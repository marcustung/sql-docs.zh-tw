---
title: 資料採礦延伸模組 (DMX) 陳述式參考 |Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 7a7a9c18599d13c4db510793a1d75c85bbb7a829
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "68070858"
---
# <a name="data-mining-extensions-dmx-statements"></a>資料採礦延伸模組 (DMX) 陳述式
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  使用資料採礦模型[!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]牽涉到下列主要工作：  
  
-   建立採礦結構與採礦模型  
  
-   處理採礦結構與採礦模型  
  
-   刪除或卸除採礦結構或採礦模型  
  
-   複製採礦模型  
  
-   瀏覽採礦模型  
  
-   針對採礦模型預測  
  
 您可以使用資料採礦延伸模組 (DMX) 陳述式，以程式來執行每一項工作。  
  
 建立採礦結構與採礦模型  
 使用[CREATE MINING STRUCTURE &#40;DMX&#41; ](../dmx/create-mining-structure-dmx.md)陳述式，以將新的採礦結構加入至資料庫。 然後您可以使用[ALTER MINING STRUCTURE &#40;DMX&#41; ](../dmx/alter-mining-structure-dmx.md)陳述式將採礦模型加入至採礦結構。  
  
 使用[CREATE MINING MODEL &#40;DMX&#41; ](../dmx/create-mining-model-dmx.md)陳述式，建立新的採礦模型與相關聯的採礦結構。  
  
 處理採礦結構與採礦模型  
 使用[插入&#40;DMX&#41; ](../dmx/insert-into-dmx.md)陳述式來處理採礦結構和採礦模型。  
  
 刪除或卸除採礦結構或採礦模型  
 使用[刪除&#40;DMX&#41; ](../dmx/delete-dmx.md)陳述式，從採礦模型或採礦結構移除所有已培訓的資料。 使用[DROP MINING STRUCTURE &#40;DMX&#41; ](../dmx/drop-mining-structure-dmx.md)或是[DROP MINING MODEL &#40;DMX&#41; ](../dmx/drop-mining-model-dmx.md)陳述式從資料庫完全移除採礦結構或採礦模型。  
  
 複製採礦模型  
 使用[SELECT INTO &#40;DMX&#41; ](../dmx/select-into-dmx.md)陳述式，將現有的採礦模型的結構複製到新的採礦模型，以及定型新的模型，使用相同的資料。  
  
 瀏覽採礦模型  
 使用[選取&#40;DMX&#41; ](../dmx/select-dmx.md)陳述式，以瀏覽資料採礦演算法計算，並在模型定型期間儲存資料採礦模型中的資訊。 非常類似於[!INCLUDE[tsql](../includes/tsql-md.md)]，您可以使用數個子句與 SELECT 陳述式中，以擴充其功能。 這些子句包括[DISTINCT FROM\<模型 >](../dmx/select-distinct-from-model-dmx.md)， [FROM\<模型 >。案例](../dmx/select-from-model-cases-dmx.md)， [FROM\<模型 >。SAMPLE_CASES](../dmx/select-from-model-sample-cases-dmx.md)， [FROM\<模型 >。內容](../dmx/select-from-model-content-dmx.md)並[FROM\<模型 >。DIMENSION_CONTENT](../dmx/select-from-model-dimension-content-dmx.md)。  
  
 針對採礦模型預測  
 使用[PREDICTION JOIN](../dmx/select-from-model-prediction-join-dmx.md)子句的 SELECT 陳述式來建立以現有的採礦模型為基礎的預測。  
  
 您也可以匯入和匯出模型，使用[匯入&#40;DMX&#41; ](../dmx/import-dmx.md)並[匯出&#40;DMX&#41; ](../dmx/export-dmx.md)陳述式。  
  
 這些工作分成兩個類別目錄：資料定義陳述式與資料操作陳述式，這會在下表中描述。  
  
|主題|描述|  
|-----------|-----------------|  
|[資料採礦延伸模組 &#40;DMX&#41; 資料定義陳述式](../dmx/dmx-statements-data-definition.md)|資料定義語言 (DDL) 的一部份。 用於定義新的採礦模型 (包括培訓)，或從資料庫卸除現有的採礦模型。|  
|[資料採礦延伸模組&#40;DMX&#41;資料操作陳述式](../dmx/dmx-statements-data-manipulation.md)|資料操作語言 (DML) 的一部份。 用於處理現有的採礦模型，包括瀏覽模型或建立預測。|  
  
## <a name="see-also"></a>另請參閱  
 [資料採礦延伸模組&#40;DMX&#41;函式參考](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [資料採礦延伸模組&#40;DMX&#41;運算子參考](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [資料採礦延伸模組&#40;DMX&#41;語法慣例](../dmx/data-mining-extensions-dmx-syntax-conventions.md)   
 [資料採礦延伸模組&#40;DMX&#41;語法元素](../dmx/data-mining-extensions-dmx-syntax-elements.md)  
  
  
