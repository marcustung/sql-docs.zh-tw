---
title: "GETUTCDATE (TRANSACT-SQL) |Microsoft 文件"
ms.custom: 
ms.date: 12/02/2015
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- GETUTCDATE
- GETUTCDATE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- time [SQL Server], UTC time
- dates [SQL Server], functions
- UTC time [SQL Server]
- date and time [SQL Server], GETUTCDATE
- Universal Time Coordinate [SQL Server]
- GETUTCDATE function [SQL Server]
- current date and time [SQL Server]
- time [SQL Server], current
- Greenwich Mean Time [SQL Server]
- functions [SQL Server], time
- system date and time [SQL Server]
- current UTC date and time [SQL Server]
- system time [SQL Server]
- functions [SQL Server], date and time
- time [SQL Server], functions
- dates [SQL Server], current date and time
- dates [SQL Server], system date and time
- time [SQL Server], system
ms.assetid: 48a5b230-102e-4a89-bb2a-fcf0cac862bb
caps.latest.revision: 37
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 316ccab8ddcaf138f05d713f41093ea7d767339a
ms.contentlocale: zh-tw
ms.lasthandoff: 09/01/2017

---
# <a name="getutcdate-transact-sql"></a>GETUTCDATE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  傳回目前資料庫系統時間戳記，當做**datetime**值。 不包含資料庫時區位移。 這個值代表目前 UTC 時間 (國際標準時間)。 這個值衍生自正在執行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體之電腦的作業系統。  
  
> [!NOTE]  
>  SYSDATETIME 和 SYSUTCDATETIME 比 GETDATE 和 GETUTCDATE 具有更多小數秒數有效位數。 SYSDATETIMEOFFSET 包含系統時區位移。 SYSDATETIME、SYSUTCDATETIME 和 SYSDATETIMEOFFSET 可指派給任何日期和時間類型的變數。  
  
 如需所有[!INCLUDE[tsql](../../includes/tsql-md.md)]日期和時間資料型別和函式，請參閱[日期和時間資料型別和函數 &#40;TRANSACT-SQL &#41;](../../t-sql/functions/date-and-time-data-types-and-functions-transact-sql.md).  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
-- Syntax for SQL Server, Azure SQL Database, Azure SQL Data Warehouse, Parallel Data Warehouse  
  
GETUTCDATE()  
```  
  
## <a name="return-types"></a>傳回類型  
 **datetime**  
  
## <a name="remarks"></a>備註  
 [!INCLUDE[tsql](../../includes/tsql-md.md)]陳述式可以參考 GETUTCDATE 任何位置，它們可以參考**datetime**運算式。  
  
 GETUTCDATE 是不具決定性的函數。 在資料行中參考這個函數的檢視表和運算式無法編製索引。  
  
## <a name="examples"></a>範例  
 下列範例會使用六個可傳回目前日期和時間的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 系統函數來傳回日期、時間或這兩者。 由於這些值會依序傳回，因此其小數秒數可能會不同。  
  
### <a name="a-getting-the-current-system-date-and-time"></a>A. 取得目前的系統日期和時間  
  
```  
SELECT 'SYSDATETIME()      ', SYSDATETIME();  
SELECT 'SYSDATETIMEOFFSET()', SYSDATETIMEOFFSET();  
SELECT 'SYSUTCDATETIME()   ', SYSUTCDATETIME();  
SELECT 'CURRENT_TIMESTAMP  ', CURRENT_TIMESTAMP;  
SELECT 'GETDATE()          ', GETDATE();  
SELECT 'GETUTCDATE()       ', GETUTCDATE();  
/* Returned:  
SYSDATETIME()            2007-05-03 18:34:11.9351421  
SYSDATETIMEOFFSET()      2007-05-03 18:34:11.9351421 -07:00  
SYSUTCDATETIME()         2007-05-04 01:34:11.9351421  
CURRENT_TIMESTAMP        2007-05-03 18:34:11.933  
GETDATE()                2007-05-03 18:34:11.933  
GETUTCDATE()             2007-05-04 01:34:11.933  
*/  
```  
  
### <a name="b-getting-the-current-system-date"></a>B. 取得目前的系統日期  
  
```  
SELECT 'SYSDATETIME()      ', CONVERT (date, SYSDATETIME());  
SELECT 'SYSDATETIMEOFFSET()', CONVERT (date, SYSDATETIMEOFFSET());  
SELECT 'SYSUTCDATETIME()   ', CONVERT (date, SYSUTCDATETIME());  
SELECT 'CURRENT_TIMESTAMP  ', CONVERT (date, CURRENT_TIMESTAMP);  
SELECT 'GETDATE()          ', CONVERT (date, GETDATE());  
SELECT 'GETUTCDATE()       ', CONVERT (date, GETUTCDATE());  
  
/* Returned:   
SYSDATETIME()            2007-05-03  
SYSDATETIMEOFFSET()      2007-05-03  
SYSUTCDATETIME()         2007-05-04  
CURRENT_TIMESTAMP        2007-05-03  
GETDATE()                2007-05-03  
GETUTCDATE()             2007-05-04  
*/  
```  
  
### <a name="c-getting-the-current-system-time"></a>C. 取得目前的系統時間  
  
```  
SELECT 'SYSDATETIME()      ', CONVERT (time, SYSDATETIME());  
SELECT 'SYSDATETIMEOFFSET()', CONVERT (time, SYSDATETIMEOFFSET());  
SELECT 'SYSUTCDATETIME()   ', CONVERT (time, SYSUTCDATETIME());  
SELECT 'CURRENT_TIMESTAMP  ', CONVERT (time, CURRENT_TIMESTAMP);  
SELECT 'GETDATE()          ', CONVERT (time, GETDATE());  
SELECT 'GETUTCDATE()       ', CONVERT (time, GETUTCDATE());  
/* Returned  
SYSDATETIME()            18:25:01.6958841  
SYSDATETIMEOFFSET()      18:25:01.6958841  
SYSUTCDATETIME()         01:25:01.6958841  
CURRENT_TIMESTAMP        18:25:01.6930000  
GETDATE()                18:25:01.6930000  
GETUTCDATE()             01:25:01.6930000  
*/  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>範例：[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]和[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 下列範例會使用六個系統函數傳回目前的日期和時間，來傳回日期、 時間或兩者。 由於這些值會依序傳回，因此其小數秒數可能會不同。  
  
### <a name="d-getting-the-current-system-date-and-time"></a>D. 取得目前的系統日期和時間  
  
```  
SELECT 'SYSDATETIME()      ', SYSDATETIME();  
SELECT 'SYSDATETIMEOFFSET()', SYSDATETIMEOFFSET();  
SELECT 'SYSUTCDATETIME()   ', SYSUTCDATETIME();  
SELECT 'CURRENT_TIMESTAMP  ', CURRENT_TIMESTAMP;  
SELECT 'GETDATE()          ', GETDATE();  
SELECT 'GETUTCDATE()       ', GETUTCDATE();  
/* Returned:  
SYSDATETIME()            2007-05-03 18:34:11.9351421  
SYSDATETIMEOFFSET()      2007-05-03 18:34:11.9351421 -07:00  
SYSUTCDATETIME()         2007-05-04 01:34:11.9351421  
CURRENT_TIMESTAMP        2007-05-03 18:34:11.933  
GETDATE()                2007-05-03 18:34:11.933  
GETUTCDATE()             2007-05-04 01:34:11.933  
*/  
```  
  
### <a name="e-getting-the-current-system-date"></a>E. 取得目前的系統日期  
  
```  
SELECT 'SYSDATETIME()      ', CONVERT (date, SYSDATETIME());  
SELECT 'SYSDATETIMEOFFSET()', CONVERT (date, SYSDATETIMEOFFSET());  
SELECT 'SYSUTCDATETIME()   ', CONVERT (date, SYSUTCDATETIME());  
SELECT 'CURRENT_TIMESTAMP  ', CONVERT (date, CURRENT_TIMESTAMP);  
SELECT 'GETDATE()          ', CONVERT (date, GETDATE());  
SELECT 'GETUTCDATE()       ', CONVERT (date, GETUTCDATE());  
  
/* Returned:   
SYSDATETIME()            2007-05-03  
SYSDATETIMEOFFSET()      2007-05-03  
SYSUTCDATETIME()         2007-05-04  
CURRENT_TIMESTAMP        2007-05-03  
GETDATE()                2007-05-03  
GETUTCDATE()             2007-05-04  
*/  
```  
  
### <a name="f-getting-the-current-system-time"></a>F. 取得目前的系統時間  
  
```  
SELECT 'SYSDATETIME()      ', CONVERT (time, SYSDATETIME());  
SELECT 'SYSDATETIMEOFFSET()', CONVERT (time, SYSDATETIMEOFFSET());  
SELECT 'SYSUTCDATETIME()   ', CONVERT (time, SYSUTCDATETIME());  
SELECT 'CURRENT_TIMESTAMP  ', CONVERT (time, CURRENT_TIMESTAMP);  
SELECT 'GETDATE()          ', CONVERT (time, GETDATE());  
SELECT 'GETUTCDATE()       ', CONVERT (time, GETUTCDATE());  
/* Returned  
SYSDATETIME()            18:25:01.6958841  
SYSDATETIMEOFFSET()      18:25:01.6958841  
SYSUTCDATETIME()         01:25:01.6958841  
CURRENT_TIMESTAMP        18:25:01.6930000  
GETDATE()                18:25:01.6930000  
GETUTCDATE()             01:25:01.6930000  
*/  
```  
  
## <a name="see-also"></a>另請參閱  
 [CAST 和 CONVERT &#40;TRANSACT-SQL &#41;](../../t-sql/functions/cast-and-convert-transact-sql.md)   
 [TIME ZONE &AMP; #40;TRANSACT-SQL &#41;](../../t-sql/queries/at-time-zone-transact-sql.md)  
  
  


