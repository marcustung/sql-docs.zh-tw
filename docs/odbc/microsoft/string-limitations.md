---
title: 字串限制 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC desktop database drivers [ODBC]
- desktop database drivers [ODBC]
ms.assetid: ec1da65f-c69d-415d-bf75-8fda8aa2b39f
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 7faab41bd52397ac0d352e04a9ec153571e93f1e
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "67948766"
---
# <a name="string-limitations"></a>字串限制
SQL 陳述式字串的長度上限為 65000 的字元。  
  
 使用 Microsoft Access 驅動程式時，會支援僅 SQL-92 字串常數 （包含單引號，不雙引號）。  
  
 直立線符號字元 (&#124;) 不能在字串中，是否指定的字元包括在後引號或不。  
  
 最大的互通性，應用程式應該傳遞字串參數，而不是傳遞加上引號的字串。
