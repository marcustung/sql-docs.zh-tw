---
title: SqlPipe 物件 |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: clr
ms.topic: reference
helpviewer_keywords:
- custom result sets [CLR integration]
- SqlPipe object
- tabular results
ms.assetid: 3e090faf-085f-4c01-a565-79e3f1c36e3b
author: rothja
ms.author: jroth
ms.openlocfilehash: 6ecc3f87313b6ddcd48b7b0e527ba4effd58e624
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "67913551"
---
# <a name="sqlpipe-object"></a>SqlPipe 物件
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  在舊版 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中，通常會撰寫將結果或輸出參數傳送至呼叫用戶端的預存程序 (或擴充的預存程序)。  
  
 在 [!INCLUDE[tsql](../../includes/tsql-md.md)]預存程序中，任何**選取**傳回零個或多個資料列的陳述式會將結果傳送至連線呼叫端的 「 管道 」。  
  
 Common language runtime (CLR) 資料庫中執行的物件[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]，您可以將結果傳送至連接的管道使用**傳送**種**SqlPipe**物件。 存取權**管道**屬性**SqlContext**物件取得**SqlPipe**物件。 **SqlPipe**類別在概念上類似**回應**在 ASP.NET 中找到的類別。 如需詳細資訊，請參閱 .NET Framework 軟體開發套件中的 SqlPipe 類別參考文件集。  
  
## <a name="returning-tabular-results-and-messages"></a>傳回表格式結果和訊息  
 **SqlPipe**已**傳送**方法，其中有三個多載。 其中包括：  
  
-   `void Send(string message)`  
  
-   `void Send(SqlDataReader reader)`  
  
-   `void Send(SqlDataRecord record)`  
  
 **傳送**方法的資料將直接傳送至用戶端或呼叫端。 它通常是用戶端取用的輸出**SqlPipe**，但在巢狀 CLR 預存程序的情況下，輸出取用者也可以是預存程序。 例如，Procedure1 會使用命令文字 "EXEC Procedure2" 呼叫 SqlCommand.ExecuteReader()。 而 Procedure2 也是 Managed 預存程序。 如果 Procedure2 此時呼叫 SqlPipe.Send( SqlDataRecord )，資料列便會傳送至 Procedure1 的讀取器 (Reader)，而非用戶端。  
  
 **傳送**方法會傳送字串訊息，會顯示在用戶端上，為資訊訊息中的 PRINT 相等[!INCLUDE[tsql](../../includes/tsql-md.md)]。 它也可以傳送單一資料列結果集使用**SqlDataRecord**，或多重資料列的結果集使用**SqlDataReader**。  
  
 **SqlPipe**物件還擁有**ExecuteAndSend**方法。 這個方法可以用來執行命令 (做為傳遞**SqlCommand**物件)，並將結果直接傳送至呼叫端。 如果已提交的命令中出現錯誤，便會將例外狀況 (Exception) 傳送至管道，但也會傳送複本給呼叫的 Managed 程式碼。 如果呼叫程式碼未攔截到例外狀況，它會將堆疊向上傳播至 [!INCLUDE[tsql](../../includes/tsql-md.md)] 程式碼，並在輸出中出現兩次。 如果呼叫程式碼攔截到例外狀況，管道取用者還是會看到錯誤，但是不會有重複的錯誤。  
  
 它只能**SqlCommand**與內容連接相關聯; 它能與非內容連接相關聯的命令。  
  
## <a name="returning-custom-result-sets"></a>傳回自訂結果集  
 Managed 預存程序可以傳送並非來自的結果集**SqlDataReader**。 **SendResultsStart**方法，連同**SendResultsRow**並**SendResultsEnd**，允許自訂結果集傳送至用戶端的預存程序。  
  
 **SendResultsStart**會採用**SqlDataRecord**做為輸入。 它會標示結果集的開頭，並使用記錄中繼資料來建構說明結果集的中繼資料。 它不會傳送具有記錄的值**SendResultsStart**。 所有後續資料列，使用傳送**SendResultsRow**，都必須符合該中繼資料定義。  
  
> [!NOTE]  
>  之後呼叫**SendResultsStart**方法只能**SendResultsRow**並**SendResultsEnd**可以呼叫。 在相同的執行個體中呼叫任何其他方法**SqlPipe**會導致**InvalidOperationException**。 **SendResultsEnd**設定**SqlPipe**回到可以在其中呼叫其他方法的初始狀態。  
  
### <a name="example"></a>範例  
 **UspGetProductLine**預存程序會傳回名稱、 產品編號、 色彩和指定的產品線內的所有產品的標價。 這個預存程序會接受完全相符項目，如*prodLine*。  
  
 C#  
  
```  
using System;  
using System.Data;  
using System.Data.SqlClient;  
using System.Data.SqlTypes;  
using Microsoft.SqlServer.Server;  
  
public partial class StoredProcedures  
{  
[Microsoft.SqlServer.Server.SqlProcedure]  
public static void uspGetProductLine(SqlString prodLine)  
{  
    // Connect through the context connection.  
    using (SqlConnection connection = new SqlConnection("context connection=true"))  
    {  
        connection.Open();  
  
        SqlCommand command = new SqlCommand(  
            "SELECT Name, ProductNumber, Color, ListPrice " +  
            "FROM Production.Product " +   
            "WHERE ProductLine = @prodLine;", connection);  
  
        command.Parameters.AddWithValue("@prodLine", prodLine);  
  
        try  
        {  
            // Execute the command and send the results to the caller.  
            SqlContext.Pipe.ExecuteAndSend(command);  
        }  
        catch (System.Data.SqlClient.SqlException ex)  
        {  
            // An error occurred executing the SQL command.  
        }  
     }  
}  
};  
```  
  
 Visual Basic  
  
```  
Imports System  
Imports System.Data  
Imports System.Data.SqlClient  
Imports System.Data.SqlTypes  
Imports Microsoft.SqlServer.Server  
  
Partial Public Class StoredProcedures  
<Microsoft.SqlServer.Server.SqlProcedure()> _  
Public Shared Sub uspGetProductLine(ByVal prodLine As SqlString)  
    Dim command As SqlCommand  
  
    ' Connect through the context connection.  
    Using connection As New SqlConnection("context connection=true")  
        connection.Open()  
  
        command = New SqlCommand( _  
        "SELECT Name, ProductNumber, Color, ListPrice " & _  
        "FROM Production.Product " & _  
        "WHERE ProductLine = @prodLine;", connection)  
        command.Parameters.AddWithValue("@prodLine", prodLine)  
  
        Try  
            ' Execute the command and send the results   
            ' directly to the caller.  
            SqlContext.Pipe.ExecuteAndSend(command)  
        Catch ex As System.Data.SqlClient.SqlException  
            ' An error occurred executing the SQL command.  
        End Try  
    End Using  
End Sub  
End Class  
```  
  
 下列[!INCLUDE[tsql](../../includes/tsql-md.md)]陳述式會執行**uspGetProduct**程序，以傳回休閒車產品的清單。  
  
```  
EXEC uspGetProductLineVB 'T';  
```  
  
## <a name="see-also"></a>另請參閱  
 [SqlDataRecord 物件](../../relational-databases/clr-integration-data-access-in-process-ado-net/sqldatarecord-object.md)   
 [CLR 預存程序](https://msdn.microsoft.com/library/bbdd51b2-a9b4-4916-ba6f-7957ac6c3f33)   
 [ADO.NET 的 SQL Server 同處理序特定延伸模組](../../relational-databases/clr-integration-data-access-in-process-ado-net/sql-server-in-process-specific-extensions-to-ado-net.md)  
  
  
