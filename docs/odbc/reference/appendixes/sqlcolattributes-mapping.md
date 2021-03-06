---
title: SQLColAttributes 對應 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- mapping deprecated functions [ODBC], SQLColAttributes
- SQLColAttribute function [ODBC], mapping
ms.assetid: 30e25719-176b-4c48-97d4-920766b22412
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 08abd0128a6fa2a478af0e9dc9c292ff973ace79
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "68064493"
---
# <a name="sqlcolattributes-mapping"></a>SQLColAttributes 對應
當應用程式呼叫**SQLColAttributes**透過 ODBC *3.x*驅動程式，會呼叫**SQLColAttributes**對應到**SQLColAttribute** ，如下所示：  
  
> [!NOTE]
>  使用中的前置詞*FieldIdentifier* ODBC 中的值*3.x*已從該使用中的 ODBC 變更*2.x*。 新的前置詞是"SQL_DESC";舊的前置詞是"SQL_COLUMN 」。  
  
1.  如果應用程式的 ODBC *2.x*應用程式*fDescType*是 SQL_COLUMN_TYPE，而傳回的型別是精簡的日期時間類型，傳回值的日期、 時間和時間戳記的驅動程式管理員對應程式碼。  
  
2.  如果*fDescType* SQL_COLUMN_NAME、 SQL_COLUMN_NULLABLE，或 SQL_COLUMN_COUNT，此驅動程式管理員會呼叫**SQLColAttribute**中使用的驅動程式*FieldIdentifier*引數對應到與 SQL_DESC_NAME、 SQL_DESC_NULLABLE 或 SQL_DESC_COUNT，適當地 *。* 所有其他的值*fDescType*會傳遞給驅動程式。  
  
 ODBC *3.x*驅動程式必須支援所有 ODBC *3.x* *FieldIdentifiers*列出**SQLColAttribute**。  
  
 ODBC *3.x* SQL_COLUMN_PRECISION 和 SQL_DESC_PRECISION，SQL_COLUMN_SCALE SQL_DESC_SCALE，和 SQL_COLUMN_LENGTH 和 SQL_DESC_LENGTH，驅動程式必須支援。 這些值都不同，因為有效位數、 小數位數和長度會以不同的方式在定義 ODBC *3.x*比起在 ODBC *2.x*。 如需詳細資訊，請參閱 <<c0> [ 資料行大小、 小數位數、 傳輸八位元長度和顯示大小](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md)附錄 d:資料類型。
