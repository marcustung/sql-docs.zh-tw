---
title: 書籤類型 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- result sets [ODBC], bookmarks
- variable-length bookmarks [ODBC]
- bookmarks [ODBC]
- fixed-length bookmarks [ODBC]
ms.assetid: cb2e7443-0260-4d1a-930f-0154db447979
author: MightyPen
ms.author: genemi
ms.openlocfilehash: fb8f5848ef9fdffab8592215fdcc5406b24319c3
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "68118776"
---
# <a name="bookmark-types"></a>書籤類型
ODBC 中的所有書籤*3.x*是可變長度的書籤。 這可讓主索引鍵或唯一索引的資料表，來為書籤與相關聯。 書籤也可以是 32 位元值，是用於 ODBC *2.x*。 若要指定 ODBC 資料指標搭配使用的書籤*3.x*應用程式設定 SQL_UB_VARIABLE SQL_ATTR_USE_BOOKMARK 陳述式屬性。 系統會自動使用可變長度的書籤。  
  
 應用程式可以呼叫**SQLColAttribute**具有*FieldIdentifier*引數設定為 SQL_DESC_OCTET_LENGTH 可取得的書籤的長度。 因為可變長度的書籤可能很長的值，應用程式以資料行 0 不應該繫結，除非它會使用許多資料列集中的資料列的書籤。  
  
 僅為回溯相容性支援固定長度書籤。 如果 ODBC *2.x*應用程式使用 ODBC *3.x*驅動程式呼叫**SQLSetStmtOption** SQL_USE_BOOKMARKS 設 SQL_UB_ON，它會對應至 SQL_ 中驅動程式管理員UB_VARIABLE。 可變長度書籤，即使它只有 32 個位元會填入。 如果驅動程式支援固定長度書籤，它將支援可變長度的書籤。 如果 ODBC *3.x*應用程式使用 ODBC *2.x*驅動程式呼叫**SQLSetStmtAttr** SQL_ATTR_USE_BOOKMARKS 設 SQL_UB_VARIABLE，它會對應在驅動程式會使用管理員 SQL_UB_ON 和 32 位元固定長度書籤。 SQL_ATTR_FETCH_BOOKMARK_PTR 陳述式屬性然後必須指向 32 位元的書籤。 如果書籤使用超過 32 位元，例如主索引鍵使用時為書籤，游標必須對應的實際值為 32 位元值。 您可以比方說，建置它們的雜湊表。 當 ODBC *3.x*應用程式使用 ODBC *2.x*驅動程式繫結的書籤，緩衝區長度必須是 4。
