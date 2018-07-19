---
title: 全文檢索索引屬性 （一般頁面） |Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: search
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.fulltextsearch.fulltextindexproperties.general.f1
ms.assetid: f4dff61c-8c2f-4ff9-abe4-70a34421448f
caps.latest.revision: 27
author: craigg-msft
ms.author: craigg
manager: craigg
ms.openlocfilehash: 825b7e357d5904108b9dd4cbdec9533e89313c83
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2018
ms.locfileid: "37149929"
---
# <a name="full-text-index-properties-general-page"></a>全文檢索索引屬性 (一般頁面)
  **若要檢視或變更全文檢索索引的可修改的屬性**  
  
-   [管理全文檢索索引](../relational-databases/indexes/indexes.md)  
  
## <a name="uielement-list"></a>UIElement 清單  
 **全文檢索目錄**  
 顯示與全文檢索索引相關聯之全文檢索目錄的名稱。  
  
 **[資料庫備份]**  
 顯示全文檢索索引所在之資料庫的名稱。  
  
 **Table**  
 顯示定義全文檢索索引之資料表的名稱。  
  
 **全文檢索索引鍵**  
 顯示全文檢索索引鍵的名稱，它是資料表之單一資料行的唯一索引。  
  
 **資料表全文檢索擴展狀態**  
 顯示全文檢索索引資料表的母體擴展狀態。  
  
 可能的值如下：  
  
 0 = 閒置。  
  
 1 = 完整母體擴展在進行中。  
  
 2 = 累加母體擴展在進行中。  
  
 3 = 追蹤變更的傳播在進行中。  
  
 4 = 背景更新索引在進行中，例如自動變更追蹤。  
  
 5 = 全文檢索索引在調整執行速度或暫停。  
  
 **作用中的全文檢索索引**  
 指出資料表是否具有使用中全文檢索索引。  
  
 1 = True  
  
 0 = False  
  
 **全文檢索索引檔案群組**  
 全文檢索索引所屬的檔案群組。  
  
 **全文檢索索引停用字詞表**  
 目前與全文檢索索引產生關聯的停用字詞表。 停用字詞表是一份[停用字詞](../relational-databases/search/full-text-search.md)。 與全文檢索索引相關聯的停用字詞表 (如果有的話) 會套用至該索引上的全文檢索查詢。 您也可以選取從索引移除停用字詞表 **\<OFF >** 從清單中，或者您可以選取不同停用字詞表; **\<SYSTEM >** 表示系統停用字詞表。  
  
 **若要建立停用字詞表**  
  
-   [設定及管理全文檢索搜尋的停用字詞與停用字詞表](../relational-databases/search/full-text-search.md)  
  
 **搜尋屬性清單**  
 目前與此全文檢索索引相關聯的搜尋屬性清單 (如果有的話)。 搜尋屬性清單會指定關聯全文檢索索引擴展時所包含的一組文件屬性。 如需詳細資訊，請參閱 [使用搜索屬性清單搜索文件屬性](../relational-databases/search/search-document-properties-with-search-property-lists.md)。  
  
 **\<關閉 >** 表示目前沒有與索引相關聯的搜尋屬性清單。 您也可以選取從索引移除目前的搜尋屬性清單**\<關閉 >** 從清單中，或從清單中選取不同的搜尋屬性清單。 這裡只會列出目前資料庫中的搜尋屬性清單。  
  
> [!NOTE]  
>  您可以將特定的搜尋屬性清單與相同資料庫中的多個全文檢索索引相關聯。  
  
 **若要建立搜尋屬性清單**  
  
-   [使用搜索屬性清單搜索文件屬性](../relational-databases/search/search-document-properties-with-search-property-lists.md)  
  
 **資料表全文檢索項目計數**  
 表示已順利建立全文檢索索引的資料列數。  
  
 此屬性會對應至`TableFulltextItemCount`屬性傳回的 OBJECTPROPERTYEX[!INCLUDE[tsql](../includes/tsql-md.md)]函式。  
  
 **已處理的資料表全文檢索文件**  
 顯示全文檢索索引啟動之後已經處理的資料列數。 在建立全文檢索搜尋索引的資料表中，單一資料列的所有資料行都會被視為單一文件的一部分來建立索引。 不會計算已刪除的資料列。  
  
|||  
|-|-|  
|0|表示全文檢索索引已完成，而且沒有任何作用中母體擴展。|  
|> 0|若為作用中母體擴展，表示自從下列任何一項作業以來，插入或更新作業所處理的文件數目：母體擴展、啟用含背景更新索引母體擴展的變更追蹤 (例如自動變更追蹤)、變更全文檢索索引結構描述、重建全文檢索目錄，或重新啟動 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 執行個體等等。|  
  
 **資料表全文檢索暫止的變更**  
 要處理的暫止變更追蹤項目數。  
  
 0 = 未啟用變更追蹤。  
  
 NULL = 資料表沒有全文檢索索引。  
  
 **資料表全文檢索失敗計數**  
 全文檢索搜尋功能尚未建立索引的資料列數。  
  
 0 = 母體擴展已完成。  
  
 \>0 = 下列其中之一：  
  
-   啟動完整、累加或手動更新變更追蹤母體擴展之後，尚未建立索引的文件數目。  
  
-   對於背景更新索引的變更追蹤，在開始母體擴展或重新開始母體擴展之後，尚未建立索引的資料列數。 這可能是結構描述變更、重建目錄、伺服器重新啟動等所造成的。  
  
 **全文檢索索引已啟用**  
 指定是否已啟用全文檢索索引。  
  
|||  
|-|-|  
|**True**|已啟用|  
|**False**|已停用|  
  
 **變更追蹤**  
 指定資料表是否已啟用全文檢索變更追蹤，而且如果有，啟用的是哪種變更追蹤。 全文檢索變更追蹤會在已設定全文檢索索引的資料表或索引檢視表中，維護已經修改之資料列的記錄。 這些變更可傳播至全文檢索索引。  
  
 **[變更追蹤]** 的值如下所示：  
  
|||  
|-|-|  
|**關閉**|全文檢索索引不會使用基礎資料的變更來更新。|  
|**手動**|全文檢索索引不會在基礎資料發生變更時自動更新。 但是會維護基礎資料的變更，而且您可以使用 SQL Server Agent 來依照排程， 或是以手動方式將其傳播到全文檢索索引。|  
|**自動**|全文檢索索引會在基底資料表中的基礎資料發生變更時自動更新。|  
  
 **重新擴展索引**  
 按一下即可在結束對話方塊時，針對全文檢索索引啟動母體擴展。 請選取下列其中一種母體擴展類型：  
  
|||  
|-|-|  
|**Full**|在資料表的完整母體擴展期間，系統會針對所有資料列建立索引項目。|  
|**增量**|累加母體擴展會針對在上一次母體擴展之後或進行時加入、刪除或修改的資料列，更新全文檢索索引。 執行累加母體擴展，基底資料表必須包含的資料行`timestamp`資料型別。|  
|**Update**|每當修改基底資料表中的資料時，就會更新全文檢索索引。|  
  
## <a name="see-also"></a>另請參閱  
 [全文檢索搜尋使用者入門](../relational-databases/search/get-started-with-full-text-search.md)  
  
  