---
title: 日期和時間改善 (OLE DB) |Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- date/time [OLE DB]
- OLE DB, date/time improvements
ms.assetid: 71614aaf-0fa4-4fe0-b522-68e2e0b66f43
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1dec9e1281d2ff61dcab9312cdf5a7ad1ecb8da3
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/15/2019
ms.locfileid: "62866830"
---
# <a name="date-and-time-improvements-ole-db"></a>日期和時間改善 (OLE DB)
  [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 導入了新的日期和時間資料類型。 本章節描述如何將這些新類型公開為 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 中的延伸模組。 如需概觀[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client 支援新的日期和時間資料類型，請參閱[日期和時間改善](../native-client/features/date-and-time-improvements.md)。 如需範例，請參閱[使用增強型日期和時間功能&#40;OLE DB&#41;](../native-client-ole-db-how-to/use-enhanced-date-and-time-features-ole-db.md)。  
  
 一般日期和時間資料類型的詳細資訊，請參閱[datetime &#40;TRANSACT-SQL&#41;](/sql/t-sql/data-types/datetime-transact-sql)。  
  
## <a name="in-this-section"></a>本節內容  
 [對 OLE DB 日期和時間改善的資料類型支援](../../relational-databases/native-client-ole-db-date-time/data-type-support-for-ole-db-date-and-time-improvements.md)  
 提供 OLE DB 的相關資訊 ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client) 類型支援[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]日期和時間資料類型。  
  
 [Metadata &#40;OLE DB&#41;](../../database-engine/dev-guide/metadata-ole-db.md)  
 包含有關 DBBINDING 結構、 資訊`ICommandWithParameters::GetParameterInfo`， `ICommandWithParameters::SetParameterInfo`， `IColumnsRowset::GetColumnsRowset`，接著`ColumnsInfo::GetColumnInfo`。同時提供有關 OLE DB 結構描述資料列集更新的資訊。  
  
 [繫結和轉換 &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-date-time/conversions-ole-db.md)  
 描述在伺服器和用戶端之間，針對現有日期類型和新日期類型進行轉換的規則。  
  
 [大量複製變更增強型的日期和時間型別&#40;OLE DB 和 ODBC&#41;](../../relational-databases/native-client-odbc-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db-and-odbc.md)  
 描述可支援大量複製作業的日期/時間增強功能。  
  
 [OLE DB API 對日期和時間增強功能的支援](ole-db-api-support-for-date-and-time-enhancements.md)  
 描述支援日期/時間增強功能的 OLE DB API。  
  
 [IRowsetFind 的相容性](../../relational-databases/native-client-ole-db-date-time/comparability-for-irowsetfind.md)  
 描述日期/時間類型和 `IRowsetFind`。  
  
 [新的日期和時間功能，舊版的 SQL Server 的&#40;OLE DB&#41;](new-date-and-time-features-with-previous-sql-server-versions-ole-db.md)  
 描述使用日期和時間增強功能的應用程式與舊版 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 進行通訊時，以及使用舊版 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 編譯的用戶端將命令傳送到支援日期和時間增強功能的伺服器時的預期行為。  
  
## <a name="see-also"></a>另請參閱  
 [SQL Server Native Client &#40;OLE DB&#41;](../../relational-databases/native-client/ole-db/sql-server-native-client-ole-db.md)  
  
  
