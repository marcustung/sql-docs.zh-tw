---
title: LIKE 述詞限制 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- LIKE predicate limitations [ODBC]
- ODBC SQL grammar, LIKE predicate limitations
ms.assetid: dbd39099-caf6-4c4c-9ad8-f6c63c1bd5e4
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 8cd3cebfcf20df2f8a3a786ea66fd28dd76307c0
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "68119713"
---
# <a name="like-predicate-limitations"></a>LIKE 述詞限制
如果資料行中的長度超過 255 個字元，LIKE 比較將只會依前 255 個字元。  
  
 在中使用類似的程序只支援常數模式。 桌面資料庫驅動程式支援 SQL-92 例如模式比對。  
  
 不支援使用 LIKE 述詞中的逸出子句。  
  
 LIKE 比較不應該對資料行包含數值或浮點資料類型的資料。 您可能無法預期的結果。 如需詳細資訊，請參閱 < *Microsoft Jet Database Engine 程式設計人員指南*。
