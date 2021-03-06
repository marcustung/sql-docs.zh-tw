---
title: 如何實作資料指標 |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, cursors
- ODBC cursors, about ODBC cursors
- ODBC applications, cursors
- cursors [ODBC], about ODBC cursors
ms.assetid: 2b1d7dd4-08a4-43fc-b3eb-70c183d0941f
author: MightyPen
ms.author: genemi
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 154600107c8b05079c3dd389b78dea6c4ba84944
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "68134074"
---
# <a name="how-cursors-are-implemented"></a>如何實作資料指標
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  ODBC 應用程式會在執行 SQL 陳述式之前設定一或多個陳述式屬性，藉此來控制資料指標的行為。 ODBC 有兩個不同的方法可指定資料指標的特性：  
  
-   資料指標類型  
  
     資料指標類型已設定使用的 SQL_ATTR_CURSOR_TYPE 屬性[SQLSetStmtAttr](../../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md)。 ODBC 資料指標類型為順向、靜態、索引鍵集驅動、混合式和動態。 設定資料指標類型是在 ODBC 中指定資料指標的原始方法。  
  
-   資料指標行為  
  
     使用 SQL_ATTR_CURSOR_SCROLLABLE 和 SQL_ATTR_CURSOR_SENSITIVITY 屬性的設定資料指標行為**SQLSetStmtAttr**。 這些屬性是根據 ISO 標準中針對 DECLARE CURSOR 陳述式定義的 SCROLL 和 SENSITIVE 關鍵字來模型化。 這兩個 ISO 選項是在 ODBC 3.0 版中導入。  
  
 應該使用這兩個方法的其中一個來指定 ODBC 資料指標的特性，並將喜好設定設定為 ODBC 資料指標類型。  
  
 除了設定資料指標的類型以外，ODBC 應用程式也會設定其他選項，例如每一個提取所傳回的資料列數、並行選項和交易隔離等級。 可以針對 ODBC 樣式的資料指標 (順向、靜態、索引鍵集驅動、混合式和動態) 或 ISO 樣式的資料指標 (可捲動性和敏感性) 來設定這些選項。  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC 驅動程式支援數種方式來實際實作各種類型的資料指標。 此驅動程式會使用預設 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 結果集來實作某些類型的資料指標，並使用 ODBC 資料指標程式庫將其他類型實作為伺服器資料指標。  
  
## <a name="in-this-section"></a>本節內容  
  
-   [使用 QL Server 預設結果集](../../../relational-databases/native-client-odbc-cursors/implementation/using-sql-server-default-result-sets.md)  
  
-   [使用伺服器資料指標](../../../relational-databases/native-client-odbc-cursors/implementation/using-server-cursors.md)  
  
-   [ODBC 資料指標程式庫](../../../relational-databases/native-client-odbc-cursors/implementation/odbc-cursor-library.md)  
  
## <a name="see-also"></a>另請參閱  
 [使用資料指標&#40;ODBC&#41;](../../../relational-databases/native-client-odbc-cursors/using-cursors-odbc.md)  
  
  
