---
title: 使用 QL Server 預設結果集 |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQLSetStmtAttr function
- ODBC cursors, default result sets
- cursors [ODBC], default result sets
- default result sets
- result sets [ODBC], default
- ODBC applications, cursors
ms.assetid: ee1db3e5-60eb-4425-8a6b-977eeced3f98
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 23d2767b8ec4d82fe283666338501efdc67c708b
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "68134041"
---
# <a name="using-sql-server-default-result-sets"></a>使用 QL Server 預設結果集
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  預設的 ODBC 資料指標屬性為：  
  
```  
SQLSetStmtAttr(hstmt, SQL_ATTR_CURSOR_TYPE, SQL_CURSOR_FORWARD_ONLY, SQL_IS_INTEGER);  
SQLSetStmtAttr(hstmt, SQL_ATTR_CONCURRENCY, SQL_CONCUR_READ_ONLY, SQL_IS_INTEGER);  
SQLSetStmtAttr(hstmt, SQL_ATTR_ROW_ARRAY_SIZE, 1, SQL_IS_INTEGER);  
```  
  
 這些屬性會設為其預設值，每當[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client ODBC 驅動程式會使用[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]預設結果集。 預設結果集可用於任何受到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 支援的 SQL 陳述式，而且是將整個結果集傳送到用戶端的最有效率的方法。  
  
 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] 導入了的對 multiple active result set (MARS);應用程式現在可以有一個以上的使用中預設結果集針對每個連接。 預設不會啟用 MARS。  
  
 在 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] 以前，預設結果集不能在相同連接上支援多個作用中陳述式。 在連接上執行 SQL 陳述式以後，伺服器要等到結果集中的所有資料列都已經處理過後，才能在該連接上接受來自用戶端的命令 (取消其餘結果集的要求除外)。 若要取消部分處理之結果集的其餘部分，呼叫[SQLCloseCursor](../../../relational-databases/native-client-odbc-api/sqlclosecursor.md)或是[SQLFreeStmt](../../../relational-databases/native-client-odbc-api/sqlfreestmt.md)具有*fOption*參數設定為 SQL_CLOSE。 若要完成的部分處理之結果集和測試的另一個結果集是否存在，請呼叫[SQLMoreResults](../../../relational-databases/native-client-odbc-api/sqlmoreresults.md)。 如果已完全處理預設結果集之前，ODBC 應用程式會嘗試連接控制代碼上的命令，呼叫就會產生 SQL_ERROR 並呼叫**SQLGetDiagRec**傳回：  
  
```  
szSqlState: "HY000", pfNativeError: 0  
szErrorMsg: "[Microsoft][SQL Server Native Client]  
                Connection is busy with results for another hstmt."  
```  
  
## <a name="see-also"></a>另請參閱  
 [如何實作資料指標](../../../relational-databases/native-client-odbc-cursors/implementation/how-cursors-are-implemented.md)  
  
  
