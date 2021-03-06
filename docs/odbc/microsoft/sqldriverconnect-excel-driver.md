---
title: SQLDriverConnect （Excel 驅動程式） |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Excel driver [ODBC], SQLDriverConnect
- SQLDriverConnect function [ODBC], Excel Driver
ms.assetid: 285cb1ea-f461-4596-97f2-fc57af05dede
author: MightyPen
ms.author: genemi
ms.openlocfilehash: e38f2f513b7da2c9342470ba75e2ee11b3d7e52a
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "68053899"
---
# <a name="sqldriverconnect-excel-driver"></a>SQLDriverConnect (Excel 驅動程式)
> [!NOTE]  
>  本主題提供 Excel 驅動程式特有的資訊。 如需此函式的一般資訊，請參閱底下的適當主題[ODBC API 參考](../../odbc/reference/syntax/odbc-api-reference.md)。  
  
 **SQLDriverConnect**可讓您連接至驅動程式，而不需建立資料來源 (DSN)。  
  
 中的所有驅動程式的連接字串，可支援下列關鍵字：**DSN**， **DBQ**，以及**FIL**。  
  
 下表顯示最小的關鍵字，才能連接到每個驅動程式，並提供搭配使用的關鍵字/值組的範例**SQLDriverConnect**。 如 DRIVERID 值的完整清單，請參閱 < [SQLConfigDataSource](../../odbc/microsoft/odbc-jet-sqlconfigdatasource-excel-driver.md)。  
  
> [!NOTE]  
>  如果 Microsoft Excel 3.0 或 4.0 版的驅動程式未指定 DBQ 或 DefaultDir，驅動程式會連接到目前的目錄中。  
  
|驅動程式|所需的關鍵字|範例|  
|------------|-----------------------|--------------|  
|Microsoft Excel 3.0 或 4.0|驅動程式 DriverID|Driver={Microsoft Excel Driver (*.xls)}; DBQ=c:\temp; DriverID=278|  
|Microsoft Excel 5.0/7.0|驅動程式，DriverID DBQ|Driver={Microsoft Excel Driver (*.xls)}; DBQ=c:\temp\sample.xls; DriverID=22|  
|Microsoft Excel 97 和更新版本|驅動程式，DriverID DBQ|Driver={Microsoft Excel Driver (*.xls)}; DBQ=c:\temp\sample.xls; DriverID=790|
