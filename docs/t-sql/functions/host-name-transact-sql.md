---
title: HOST_NAME (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 09/21/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- HOST_NAME_TSQL
- HOST_NAME
dev_langs:
- TSQL
helpviewer_keywords:
- HOST_NAME function
- workstation names [SQL Server]
ms.assetid: 4b8b0705-c083-4b07-b954-c83ee73b2ebb
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: c781ef8b6b2b0aa883deda482c10c03fbc6f2b78
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/15/2019
ms.locfileid: "65946474"
---
# <a name="hostname-transact-sql"></a>HOST_NAME (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

  傳回工作站名稱。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
HOST_NAME ()  
```  
  
## <a name="return-types"></a>傳回類型  
 **nvarchar(128)**  
  
## <a name="remarks"></a>Remarks  
 當系統函數的參數是選擇性時，就會假設使用目前資料庫、主機電腦、伺服器使用者或資料庫使用者。 內建函數後面一律必須接著括號。  
  
 系統函數可以用於選取清單、WHERE 子句以及任何可以使用運算式的位置。  
  
> [!IMPORTANT]  
>  用戶端應用程式會提供工作站名稱，而且可提供不正確的資料。 請勿依賴 HOST_NAME 當做安全性功能。  
  
## <a name="examples"></a>範例  
 下列範例會建立一份資料表，利用 `HOST_NAME()` 定義中的 `DEFAULT` 來記錄電腦的工作站名稱，這些電腦會將資料列插入記錄訂單的資料表中。  
  
```  
CREATE TABLE Orders  
   (OrderID     int        PRIMARY KEY,  
    CustomerID  nchar(5)   REFERENCES Customers(CustomerID),  
    Workstation nchar(30)  NOT NULL DEFAULT HOST_NAME(),  
    OrderDate   datetime   NOT NULL,  
    ShipDate    datetime   NULL,  
    ShipperID   int        NULL REFERENCES Shippers(ShipperID));  
GO  
```  
  
## <a name="see-also"></a>另請參閱  
 [運算式 &#40;Transact-SQL&#41;](../../t-sql/language-elements/expressions-transact-sql.md)   
 [系統函式 &#40;Transact-SQL&#41;](../../relational-databases/system-functions/system-functions-for-transact-sql.md)  
  
  
