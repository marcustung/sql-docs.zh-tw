---
title: 替代方案：使用 SQL 陳述式 |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- SQL statements [ADO]
- editing data [ADO], sql statements
- ADO, SQL statements
ms.assetid: 8b528b23-063d-45ea-8dea-6a90d4060b20
author: MightyPen
ms.author: genemi
ms.openlocfilehash: f41ef7f0641877056a6e2f3d85fd6a40ff7826db
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "67925994"
---
# <a name="alternatives-using-sql-statements"></a>替代方案：使用 SQL 陳述式
ADO 也可讓使用命令作為其內建的屬性和方法，來編輯資料的替代方案。 視您的提供者而定，這一節所述的所有作業也都可藉由將命令傳遞至您的資料來源。 例如，SQL UPDATE 陳述式可用來修改資料，而不使用**值**屬性**欄位**。 SQL INSERT 陳述式可用來將新記錄新增至資料來源，而不是 ADO 方法**AddNew**。 如需 SQL 或您的提供者的資料操作語言的詳細資訊，請參閱您的資料來源的文件。  
  
 例如，您可以傳遞 SQL 字串，包含資料庫，DELETE 陳述式，如下列程式碼所示：  
  
```  
'BeginSQLDelete  
strSQL = "DELETE FROM Shippers WHERE ShipperID = " & intId  
objConn1.Execute strSQL, , adCmdText + adExecuteNoRecords  
'EndSQLDelete  
```
