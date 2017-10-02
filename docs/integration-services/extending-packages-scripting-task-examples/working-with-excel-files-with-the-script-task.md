---
title: "使用 Excel 檔案 with the Script Task |Microsoft 文件"
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
dev_langs:
- VB
helpviewer_keywords:
- Script task [Integration Services], Excel files
- Script task [Integration Services], examples
- Excel [Integration Services]
ms.assetid: b8fa110a-2c9c-4f5a-8fe1-305555640e44
caps.latest.revision: 35
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 46bf53c35663393ad600f02600961cf0295386bf
ms.contentlocale: zh-tw
ms.lasthandoff: 09/26/2017

---
# <a name="working-with-excel-files-with-the-script-task"></a>以指令碼工作處理 Excel 檔案
  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 提供 Excel 連接管理員、Excel 來源和 Excel 目的地，以處理 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Excel 檔案格式試算表中儲存的資料。 本主題所述的技術會使用指令碼工作取得有關可用 Excel 資料庫 (活頁簿檔案) 與資料表 (工作表與具名範圍) 的相關資訊。 您可以輕鬆地修改這些範例，使其可與 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Jet OLE DB Provider 所支援的其他以檔案為基礎之資料來源搭配使用。  
  
 [設定封裝以測試範例](#configuring)  
  
 [範例 1： 檢查 Excel 檔案是否存在](#example1)  
  
 [範例 2： 檢查 Excel 資料表是否存在](#example2)  
  
 [範例 3： 取得資料夾中的 Excel 檔案的清單](#example3)  
  
 [範例 4： 取得 Excel 檔案中的資料表清單](#example4)  
  
 [顯示範例的結果](#testing)  
  
> [!NOTE]  
>  如果您想要建立可更輕鬆地在多個封裝之間重複使用的工作，請考慮使用此指令碼工作範例中的程式碼做為自訂工作的起點。 如需詳細資訊，請參閱 [開發自訂工作](../../integration-services/extending-packages-custom-objects/task/developing-a-custom-task.md)。  
  
##  <a name="configuring"></a>設定封裝以測試範例  
 您可以設定單一封裝以測試本主題中的所有範例。 範例使用許多相同的封裝變數與相同的 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 類別。  
  
#### <a name="to-configure-a-package-for-use-with-the-examples-in-this-topic"></a>設定封裝與本主題中的範例搭配使用  
  
1.  在 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 中建立新的 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 專案，並開啟預設封裝以進行編輯。  
  
2.  **變數**。 開啟**變數**視窗，並定義下列變數：  
  
    -   `ExcelFile`型別**字串**。 輸入現有 Excel 活頁簿的完整路徑與檔案名稱。  
  
    -   `ExcelTable`型別**字串**。 輸入以 `ExcelFile` 變數值命名之活頁簿中，現有工作表或具名範圍的名稱。 此值區分大小寫。  
  
    -   `ExcelFileExists`型別**布林**。  
  
    -   `ExcelTableExists`型別**布林**。  
  
    -   `ExcelFolder`型別**字串**。 輸入含有至少一個 Excel 活頁簿的資料夾完整路徑。  
  
    -   `ExcelFiles`型別**物件**。  
  
    -   `ExcelTables`型別**物件**。  
  
3.  **Imports 陳述式**。 大部分的程式碼範例都需要您在指令碼檔案最上方匯入下列一或兩個 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 命名空間：  
  
    -   **System.IO**，檔案系統作業。  
  
    -   **System.Data.OleDb**，若要開啟 Excel 檔案做為資料來源。  
  
4.  **參考**。 從 Excel 檔案讀取結構描述資訊的程式碼範例需要在將指令碼專案中的額外參考**System.Xml**命名空間。  
  
5.  設定指令碼元件的預設指令碼語言使用**指令碼語言**選項**一般**頁面**選項** 對話方塊。 如需相關資訊，請參閱 [General Page](https://msdn.microsoft.com/library/ms189436(v=sql.110).aspx)。  
  
##  <a name="example1"></a>範例 1 描述： 檢查 Excel 檔案是否存在  
 此範例會判斷 `ExcelFile` 變數中指定的 Excel 活頁簿檔案是否存在，然後將 `ExcelFileExists` 變數的布林值設定為結果。 您可以為封裝工作流程中的分支使用此布林值。  
  
#### <a name="to-configure-this-script-task-example"></a>設定此指令碼工作範例  
  
1.  將新的指令碼工作加入封裝和其名稱變更為**ExcelFileExists**。  
  
2.  在**指令碼工作編輯器**上**指令碼**索引標籤上，按一下  **readonlyvariables**和輸入屬性值，使用下列方法之一：  
  
    -   型別**ExcelFile**。  
  
         -或-  
  
    -   按一下省略符號 (**...**) 屬性欄位中，然後在下一步按鈕**選取變數**對話方塊中，選取**ExcelFile**變數。  
  
3.  按一下**[readwritevariables]**和輸入屬性值，使用下列方法之一：  
  
    -   型別**ExcelFileExists**。  
  
         -或-  
  
    -   按一下省略符號 (**...**) 屬性欄位中，然後在下一步按鈕**選取變數**對話方塊中，選取**ExcelFileExists**變數。  
  
4.  按一下**編輯指令碼**開啟指令碼編輯器。  
  
5.  新增**匯入**陳述式**System.IO**指令碼檔案頂端的命名空間。  
  
6.  加入下列程式碼。  
  
### <a name="example-1-code"></a>範例 1 的程式碼  
  
```vb  
Public Class ScriptMain  
  Public Sub Main()  
    Dim fileToTest As String  
  
    fileToTest = Dts.Variables("ExcelFile").Value.ToString  
    If File.Exists(fileToTest) Then  
      Dts.Variables("ExcelFileExists").Value = True  
    Else  
      Dts.Variables("ExcelFileExists").Value = False  
    End If  
  
    Dts.TaskResult = ScriptResults.Success  
  End Sub  
End Class  
```  
  
```csharp  
public class ScriptMain  
{  
  public void Main()  
  {  
    string fileToTest;  
  
    fileToTest = Dts.Variables["ExcelFile"].Value.ToString();  
    if (File.Exists(fileToTest))  
    {  
      Dts.Variables["ExcelFileExists"].Value = true;  
    }  
    else  
    {  
      Dts.Variables["ExcelFileExists"].Value = false;  
    }  
  
    Dts.TaskResult = (int)ScriptResults.Success;  
  }  
}  
```  
  
##  <a name="example2"></a>範例 2 描述： 檢查 Excel 資料表是否存在  
 此範例會判斷 `ExcelTable` 變數中指定的 Excel 工作表或具名範圍是否存在於 `ExcelFile` 變數中指定的 Excel 活頁簿檔案，然後將 `ExcelTableExists` 變數的布林值設定為結果。 您可以為封裝工作流程中的分支使用此布林值。  
  
#### <a name="to-configure-this-script-task-example"></a>設定此指令碼工作範例  
  
1.  將新的指令碼工作加入封裝和其名稱變更為**ExcelTableExists**。  
  
2.  在**指令碼工作編輯器**上**指令碼**索引標籤上，按一下  **readonlyvariables**和輸入屬性值，使用下列方法之一：  
  
    -   型別**ExcelTable**和**ExcelFile**以逗號分隔**。**  
  
         -或-  
  
    -   按一下省略符號 (**...**) 屬性欄位中，然後在下一步按鈕**選取變數**對話方塊中，選取**ExcelTable**和**ExcelFile**變數。  
  
3.  按一下**[readwritevariables]**和輸入屬性值，使用下列方法之一：  
  
    -   型別**ExcelTableExists**。  
  
         -或-  
  
    -   按一下省略符號 (**...**) 屬性欄位中，然後在下一步按鈕**選取變數**對話方塊中，選取**ExcelTableExists**變數。  
  
4.  按一下**編輯指令碼**開啟指令碼編輯器。  
  
5.  將參考加入**System.Xml**指令碼專案中的組件。  
  
6.  新增**匯入**陳述式**System.IO**和**System.Data.OleDb**指令碼檔案頂端的命名空間。  
  
7.  加入下列程式碼。  
  
### <a name="example-2-code"></a>程式碼範例 2  
  
```vb  
Public Class ScriptMain  
  Public Sub Main()  
    Dim fileToTest As String  
    Dim tableToTest As String  
    Dim connectionString As String  
    Dim excelConnection As OleDbConnection  
    Dim excelTables As DataTable  
    Dim excelTable As DataRow  
    Dim currentTable As String  
  
    fileToTest = Dts.Variables("ExcelFile").Value.ToString  
    tableToTest = Dts.Variables("ExcelTable").Value.ToString  
  
    Dts.Variables("ExcelTableExists").Value = False  
    If File.Exists(fileToTest) Then  
      connectionString = "Provider=Microsoft.Jet.OLEDB.4.0;" & _  
        "Data Source=" & fileToTest & _  
        ";Extended Properties=Excel 8.0"  
      excelConnection = New OleDbConnection(connectionString)  
      excelConnection.Open()  
      excelTables = excelConnection.GetSchema("Tables")  
      For Each excelTable In excelTables.Rows  
        currentTable = excelTable.Item("TABLE_NAME").ToString  
        If currentTable = tableToTest Then  
          Dts.Variables("ExcelTableExists").Value = True  
        End If  
      Next  
    End If  
  
    Dts.TaskResult = ScriptResults.Success  
  End Sub  
End Class  
```  
  
```csharp  
public class ScriptMain  
{  
    public void Main()  
        {  
            string fileToTest;  
            string tableToTest;  
            string connectionString;  
            OleDbConnection excelConnection;  
            DataTable excelTables;  
            string currentTable;  
  
            fileToTest = Dts.Variables["ExcelFile"].Value.ToString();  
            tableToTest = Dts.Variables["ExcelTable"].Value.ToString();  
  
            Dts.Variables["ExcelTableExists"].Value = false;  
            if (File.Exists(fileToTest))  
            {  
                connectionString = "Provider=Microsoft.Jet.OLEDB.4.0;" +  
                "Data Source=" + fileToTest + ";Extended Properties=Excel 8.0";  
                excelConnection = new OleDbConnection(connectionString);  
                excelConnection.Open();  
                excelTables = excelConnection.GetSchema("Tables");  
                foreach (DataRow excelTable in excelTables.Rows)  
                {  
                    currentTable = excelTable["TABLE_NAME"].ToString();  
                    if (currentTable == tableToTest)  
                    {  
                        Dts.Variables["ExcelTableExists"].Value = true;  
                    }  
                }  
            }  
  
            Dts.TaskResult = (int)ScriptResults.Success;  
  
        }  
}  
```  
  
##  <a name="example3"></a>範例 3 描述： 取得資料夾中的 Excel 檔案的清單  
 此範例會使用在 `ExcelFolder` 變數值中指定的資料夾內所找到的 Excel 檔案清單，來填滿陣列，然後將陣列複製到 `ExcelFiles` 變數中。 您可以使用 Foreach From Variable 列舉值來反覆運算陣列中的檔案。  
  
#### <a name="to-configure-this-script-task-example"></a>設定此指令碼工作範例  
  
1.  將新的指令碼工作加入封裝和其名稱變更為**GetExcelFiles**。  
  
2.  開啟**指令碼工作編輯器**上**指令碼**索引標籤上，按一下  **readonlyvariables**和輸入屬性值，使用下列方法之一：  
  
    -   型別**ExcelFolder**  
  
         -或-  
  
    -   按一下省略符號 (**...**) 屬性欄位中，然後在下一步按鈕**選取變數**對話方塊方塊中，選取 ExcelFolder 變數。  
  
3.  按一下**[readwritevariables]**和輸入屬性值，使用下列方法之一：  
  
    -   型別**ExcelFiles**。  
  
         -或-  
  
    -   按一下省略符號 (**...**) 屬性欄位中，然後在下一步按鈕**選取變數**對話方塊方塊中，選取 ExcelFiles 變數。  
  
4.  按一下**編輯指令碼**開啟指令碼編輯器。  
  
5.  新增**匯入**陳述式**System.IO**指令碼檔案頂端的命名空間。  
  
6.  加入下列程式碼。  
  
### <a name="example-3-code"></a>範例 3 程式碼  
  
```vb  
Public Class ScriptMain  
  Public Sub Main()  
    Const FILE_PATTERN As String = "*.xls"  
  
    Dim excelFolder As String  
    Dim excelFiles As String()  
  
    excelFolder = Dts.Variables("ExcelFolder").Value.ToString  
    excelFiles = Directory.GetFiles(excelFolder, FILE_PATTERN)  
  
    Dts.Variables("ExcelFiles").Value = excelFiles  
  
    Dts.TaskResult = ScriptResults.Success  
  End Sub  
End Class  
```  
  
```csharp  
public class ScriptMain  
{  
  public void Main()  
  {  
    const string FILE_PATTERN = "*.xls";  
  
    string excelFolder;  
    string[] excelFiles;  
  
    excelFolder = Dts.Variables["ExcelFolder"].Value.ToString();  
    excelFiles = Directory.GetFiles(excelFolder, FILE_PATTERN);  
  
    Dts.Variables["ExcelFiles"].Value = excelFiles;  
  
    Dts.TaskResult = (int)ScriptResults.Success;  
  }  
}  
```  
  
### <a name="alternate-solution"></a>替代方案  
 您也可以使用 ForEach 檔案列舉值反覆運算資料夾中的所有 Excel 檔案，以代替使用指令碼工作將 Excel 檔案清單蒐集到陣列中的方式。 如需詳細資訊，請參閱[Excel 檔案，並使用 「 Foreach 迴圈 」 容器的資料表執行迴圈](../../integration-services/control-flow/loop-through-excel-files-and-tables-by-using-a-foreach-loop-container.md)。  
  
##  <a name="example4"></a>範例 4 描述： 取得 Excel 檔案中的資料表清單  
 此範例會使用在 `ExcelFile` 變數值中指定的 Excel 活頁簿檔案內找到的工作表清單和具名範圍，來填滿陣列，然後將陣列複製到 `ExcelTables` 變數中。 您可以使用 Foreach From Variable 列舉值來反覆運算陣列中的資料表。  
  
> [!NOTE]  
>  Excel 活頁簿中資料表清單包含活頁簿 (具有 $ 後置詞) 及具名範圍。 如果您必須只篩選清單中的工作表或具名範圍，必須加入其他程式碼以達成此目的。  
  
#### <a name="to-configure-this-script-task-example"></a>設定此指令碼工作範例  
  
1.  將新的指令碼工作加入封裝和其名稱變更為**GetExcelTables**。  
  
2.  開啟**指令碼工作編輯器**上**指令碼**索引標籤上，按一下  **readonlyvariables**和輸入屬性值，使用下列方法之一：  
  
    -   型別**ExcelFile**。  
  
         -或-  
  
    -   按一下省略符號 (**...**) 屬性欄位中，然後在下一步按鈕**選取變數**對話方塊方塊中，選取 ExcelFile 變數。  
  
3.  按一下**[readwritevariables]**和輸入屬性值，使用下列方法之一：  
  
    -   型別**ExcelTables**。  
  
         -或-  
  
    -   按一下省略符號 (**...**) 屬性欄位中，然後在下一步按鈕**選取變數**對話方塊方塊中，選取 ExcelTablesvariable。  
  
4.  按一下**編輯指令碼**開啟指令碼編輯器。  
  
5.  將參考加入**System.Xml**指令碼專案中的命名空間。  
  
6.  新增**匯入**陳述式**System.Data.OleDb**指令碼檔案頂端的命名空間。  
  
7.  加入下列程式碼。  
  
### <a name="example-4-code"></a>範例 4 程式碼  
  
```vb  
Public Class ScriptMain  
  Public Sub Main()  
    Dim excelFile As String  
    Dim connectionString As String  
    Dim excelConnection As OleDbConnection  
    Dim tablesInFile As DataTable  
    Dim tableCount As Integer = 0  
    Dim tableInFile As DataRow  
    Dim currentTable As String  
    Dim tableIndex As Integer = 0  
  
    Dim excelTables As String()  
  
    excelFile = Dts.Variables("ExcelFile").Value.ToString  
    connectionString = "Provider=Microsoft.Jet.OLEDB.4.0;" & _  
        "Data Source=" & excelFile & _  
        ";Extended Properties=Excel 8.0"  
    excelConnection = New OleDbConnection(connectionString)  
    excelConnection.Open()  
    tablesInFile = excelConnection.GetSchema("Tables")  
    tableCount = tablesInFile.Rows.Count  
    ReDim excelTables(tableCount - 1)  
    For Each tableInFile In tablesInFile.Rows  
      currentTable = tableInFile.Item("TABLE_NAME").ToString  
      excelTables(tableIndex) = currentTable  
      tableIndex += 1  
    Next  
  
    Dts.Variables("ExcelTables").Value = excelTables  
  
    Dts.TaskResult = ScriptResults.Success  
  End Sub  
End Class  
```  
  
```csharp  
public class ScriptMain  
{  
  public void Main()  
        {  
            string excelFile;  
            string connectionString;  
            OleDbConnection excelConnection;  
            DataTable tablesInFile;  
            int tableCount = 0;  
            string currentTable;  
            int tableIndex = 0;  
  
            string[] excelTables = new string[5];  
  
            excelFile = Dts.Variables["ExcelFile"].Value.ToString();  
            connectionString = "Provider=Microsoft.Jet.OLEDB.4.0;" +  
                "Data Source=" + excelFile + ";Extended Properties=Excel 8.0";  
            excelConnection = new OleDbConnection(connectionString);  
            excelConnection.Open();  
            tablesInFile = excelConnection.GetSchema("Tables");  
            tableCount = tablesInFile.Rows.Count;  
  
            foreach (DataRow tableInFile in tablesInFile.Rows)  
            {  
                currentTable = tableInFile["TABLE_NAME"].ToString();  
                excelTables[tableIndex] = currentTable;  
                tableIndex += 1;  
            }  
  
            Dts.Variables["ExcelTables"].Value = excelTables;  
  
            Dts.TaskResult = (int)ScriptResults.Success;  
        }  
}  
```  
  
### <a name="alternate-solution"></a>替代方案  
 您也可以使用 Foreach ADO.NET 結構描述資料列集列舉值，反覆運算在 Excel 活頁簿檔案中的所有資料表 (也就是，工作表與具名範圍)，以代替使用指令碼工作將 Excel 資料表清單蒐集到陣列中的方式。 如需詳細資訊，請參閱[Excel 檔案，並使用 「 Foreach 迴圈 」 容器的資料表執行迴圈](../../integration-services/control-flow/loop-through-excel-files-and-tables-by-using-a-foreach-loop-container.md)。  
  
##  <a name="testing"></a>顯示範例的結果  
 如果您已在相同封裝中設定此主題中的每個範例，可以將所有的指令碼工作連接至其他顯示所有範例輸出的指令碼工作。  
  
#### <a name="to-configure-a-script-task-to-display-the-output-of-the-examples-in-this-topic"></a>設定指令碼工作以顯示本主題中的範例輸出  
  
1.  將新的指令碼工作加入封裝和其名稱變更為**DisplayResults**。  
  
2.  連接四個範例指令碼工作，好讓每一項工作執行前一個工作已順利完成之後，若要將第四個範例工作連接**DisplayResults**工作。  
  
3.  開啟**DisplayResults**中工作**指令碼工作編輯器**。  
  
4.  在**指令碼**索引標籤上，按一下  **[readonlyvariables]**並使用下列方法之一將中所列的所有七個變數[設定封裝以測試範例](#configuring):  
  
    -   輸入每個變數名稱，並以逗號分隔。  
  
         -或-  
  
    -   按一下省略符號 (**...**) 屬性欄位中，然後在下一步按鈕**選取變數**對話方塊中，選取變數。  
  
5.  按一下**編輯指令碼**開啟指令碼編輯器。  
  
6.  新增**匯入**陳述式**Microsoft.VisualBasic**和**System.Windows.Forms**指令碼檔案頂端的命名空間。  
  
7.  加入下列程式碼。  
  
8.  執行封裝並檢查在訊息方塊中顯示的結果。  
  
### <a name="code-to-display-the-results"></a>可顯示結果的程式碼  
  
```vb  
Public Class ScriptMain  
  Public Sub Main()  
    Const EOL As String = ControlChars.CrLf  
  
    Dim results As String  
    Dim filesInFolder As String()  
    Dim fileInFolder As String  
    Dim tablesInFile As String()  
    Dim tableInFile As String  
  
    results = _  
      "Final values of variables:" & EOL & _  
      "ExcelFile: " & Dts.Variables("ExcelFile").Value.ToString & EOL & _  
      "ExcelFileExists: " & Dts.Variables("ExcelFileExists").Value.ToString & EOL & _  
      "ExcelTable: " & Dts.Variables("ExcelTable").Value.ToString & EOL & _  
      "ExcelTableExists: " & Dts.Variables("ExcelTableExists").Value.ToString & EOL & _  
      "ExcelFolder: " & Dts.Variables("ExcelFolder").Value.ToString & EOL & _  
      EOL  
  
    results &= "Excel files in folder: " & EOL  
    filesInFolder = DirectCast(Dts.Variables("ExcelFiles").Value, String())  
    For Each fileInFolder In filesInFolder  
      results &= " " & fileInFolder & EOL  
    Next  
    results &= EOL  
  
    results &= "Excel tables in file: " & EOL  
    tablesInFile = DirectCast(Dts.Variables("ExcelTables").Value, String())  
    For Each tableInFile In tablesInFile  
      results &= " " & tableInFile & EOL  
    Next  
  
    MessageBox.Show(results, "Results", MessageBoxButtons.OK, MessageBoxIcon.Information)  
  
    Dts.TaskResult = ScriptResults.Success  
  End Sub  
End Class  
```  
  
```csharp  
public class ScriptMain  
{  
  public void Main()  
        {  
            const string EOL = "\r";  
  
            string results;  
            string[] filesInFolder;  
            //string fileInFolder;  
            string[] tablesInFile;  
            //string tableInFile;  
  
            results = "Final values of variables:" + EOL + "ExcelFile: " + Dts.Variables["ExcelFile"].Value.ToString() + EOL + "ExcelFileExists: " + Dts.Variables["ExcelFileExists"].Value.ToString() + EOL + "ExcelTable: " + Dts.Variables["ExcelTable"].Value.ToString() + EOL + "ExcelTableExists: " + Dts.Variables["ExcelTableExists"].Value.ToString() + EOL + "ExcelFolder: " + Dts.Variables["ExcelFolder"].Value.ToString() + EOL + EOL;  
  
            results += "Excel files in folder: " + EOL;  
            filesInFolder = (string[])(Dts.Variables["ExcelFiles"].Value);  
            foreach (string fileInFolder in filesInFolder)  
            {  
                results += " " + fileInFolder + EOL;  
            }  
            results += EOL;  
  
            results += "Excel tables in file: " + EOL;  
            tablesInFile = (string[])(Dts.Variables["ExcelTables"].Value);  
            foreach (string tableInFile in tablesInFile)  
            {  
                results += " " + tableInFile + EOL;  
            }  
  
            MessageBox.Show(results, "Results", MessageBoxButtons.OK, MessageBoxIcon.Information);  
  
            Dts.TaskResult = (int)ScriptResults.Success;  
        }  
}  
```  
  
## <a name="see-also"></a>另請參閱  
 [Excel 連接管理員](../../integration-services/connection-manager/excel-connection-manager.md)   
 [使用 Foreach 迴圈容器來執行 Excel 檔案和資料表迴圈](../../integration-services/control-flow/loop-through-excel-files-and-tables-by-using-a-foreach-loop-container.md)  
  
  