---
title: 資料採礦延伸模組 (DMX) 參考 |Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 29454fefde7850e5e45ca6a916540e7d38e2b286
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "68070903"
---
# <a name="data-mining-extensions-dmx-reference"></a>資料採礦延伸模組 (DMX) 參考
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  資料採礦延伸模組 (DMX) 是一種語言，可用來建立和使用中的資料採礦模型[!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]。 您可以使用 DMX 建立新資料採礦模型的結構、培訓這些模型，以及瀏覽、管理與預測模型。 DMX 是由資料定義語言 (DDL) 陳述式、資料操作語言 (DML) 陳述式及函數和運算子所組成。  
  
## <a name="microsoft-ole-db-for-data-mining-specification"></a>Microsoft OLE DB for Data Mining 規格  
 中的資料採礦功能[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]符合內建[!INCLUDE[msCoName](../includes/msconame-md.md)]OLE DB for Data Mining 規格。  
  
 [!INCLUDE[msCoName](../includes/msconame-md.md)] OLE DB for Data Mining 規格會定義下列：  
  
-   保存定義資料採礦模型之資訊的結構。  
  
-   建立及處理資料採礦模型的語言。  
  
 規格會將資料採礦的基準定義為資料採礦模型虛擬物件。 資料採礦模型物件會封裝特定採礦模型的所有已知內容。 資料採礦模型物件的結構就像 SQL 資料表，有描述模型的資料行、資料類型與中繼資訊。 這種結構可以讓您使用 DMX 語言 (SQL 的延伸模組) 來建立及處理模型。  
  
 **如需詳細資訊：** [採礦結構 &#40;Analysis Services-資料採礦 &#41;](../analysis-services/data-mining/mining-structures-analysis-services-data-mining.md)  
  
##  <a name="BKMK_DMXStatements"></a> DMX 陳述式  
 您可以使用 DMX 陳述式建立、處理、刪除、複製、瀏覽與預測資料採礦模型。 DMX 中有兩種陳述式類型：資料定義陳述式與資料操作陳述式。 您可以使用每一種陳述式執行不同種類的工作。  
  
 下列各區段提供有關使用 DMX 陳述式的詳細資訊：  
  
-   [資料定義陳述式](#BKMK_DDL)  
  
-   [資料操作陳述式](#BKMK_DML)  
  
-   [查詢基礎觀念](#BKMK_Queries)  
  
###  <a name="BKMK_DDL"></a> 資料定義陳述式  
 使用 DMX 中的資料定義陳述式建立及定義新的採礦結構與模型，以匯入與匯出採礦模型與採礦結構，以及從資料庫卸除現有的模型。 DMX 中的資料定義陳述式是資料定義語言 (DDL) 的一部份。  
  
 您可以使用 DMX 中的資料定義陳述式執行下列工作：  
  
-   使用建立採礦結構[CREATE MINING STRUCTURE](../dmx/create-mining-structure-dmx.md)陳述式，並將採礦模型加入採礦結構使用[ALTER MINING STRUCTURE](../dmx/alter-mining-structure-dmx.md)陳述式。  
  
-   藉由同時建立採礦模型和相關聯的採礦結構[CREATE MINING MODEL](../dmx/create-mining-model-dmx.md)陳述式，以建立空的資料採礦模型物件。  
  
-   採礦模型和相關聯的採礦結構使用匯出至檔案[匯出](../dmx/export-dmx.md)陳述式。 從所使用的 EXPORT 陳述式建立的檔案匯入採礦模型和相關聯的採礦結構[匯入](../dmx/import-dmx.md)陳述式。  
  
-   將現有的採礦模型的結構複製到新的模型，以及它使用相同的資料，使用定型[SELECT INTO](../dmx/select-into-dmx.md)陳述式。  
  
-   使用從資料庫完全移除採礦模型[DROP MINING MODEL](../dmx/drop-mining-model-dmx.md)陳述式。 從完全移除採礦結構及其所有相關聯的採礦模型的資料庫使用[DROP MINING STRUCTURE](../dmx/drop-mining-structure-dmx.md)陳述式。  
  
 若要深入了解您可以使用 DMX 陳述式執行資料採礦工作，請參閱[資料採礦延伸模組&#40;DMX&#41;陳述式參考](../dmx/data-mining-extensions-dmx-statements.md)。  
  
 [回到 DMX 陳述式](#BKMK_DMXStatements)  
  
###  <a name="BKMK_DML"></a> 資料操作陳述式  
 使用 DMX 中的資料操作陳述式處理現有的採礦模型、瀏覽模型，以及針對模型建立預測。 DMX 中的資料操作陳述式是資料管理語言 (DML) 的一部份。  
  
 您可以使用 DMX 中的資料操作陳述式執行下列工作：  
  
-   使用定型的採礦模型[INSERT INTO](../dmx/insert-into-dmx.md)陳述式。 這不會將實際的來源資料插入資料採礦模型物件，而是會建立描述演算法建立之採礦模型的摘要。 INSERT INTO 陳述式的來源查詢所述[\<來源資料查詢 >](../dmx/source-data-query.md)。  
  
-   擴充選取的陳述式，來瀏覽在模型定型期間計算並儲存在資料採礦模型中，例如來源資料的統計資料的資訊。 以下是您可以用以擴充能力的 SELECT 陳述式的子句：  
  
    -   [SELECT DISTINCT FROM &#60;model &#62; &#40;DMX&#41;](../dmx/select-distinct-from-model-dmx.md)  
  
    -   [SELECT FROM&#60;模型&#62;。內容&#40;DMX&#41;](../dmx/select-from-model-content-dmx.md)  
  
    -   [SELECT FROM&#60;模型&#62;。案例&#40;DMX&#41;](../dmx/select-from-model-cases-dmx.md)  
  
    -   [SELECT FROM &#60;model&#62;.SAMPLE_CASES &#40;DMX&#41;](../dmx/select-from-model-sample-cases-dmx.md)  
  
    -   [SELECT FROM&#60;模型&#62;。DIMENSION_CONTENT &#40;DMX&#41;](../dmx/select-from-model-dimension-content-dmx.md)  
  
-   建立根據使用現有的採礦模型的預測[PREDICTION JOIN](../dmx/select-from-model-prediction-join-dmx.md)子句的 SELECT 陳述式。 PREDICTION JOIN 陳述式的來源查詢所述[\<來源資料查詢 >](../dmx/source-data-query.md)。  
  
-   從模型或結構中移除所有已培訓的資料，使用[刪除&#40;DMX&#41; ](../dmx/delete-dmx.md)陳述式。  
  
 若要深入了解您可以使用 DMX 陳述式執行資料採礦工作，請參閱[資料採礦延伸模組&#40;DMX&#41;陳述式參考](../dmx/data-mining-extensions-dmx-statements.md)。  
  
 [回到 DMX 陳述式](#BKMK_DMXStatements)  
  
###  <a name="BKMK_Queries"></a> DMX 查詢基礎觀念  
 SELECT 陳述式是大多數 DMX 查詢的基礎。 根據搭配這些陳述式使用的子句，您可以針對採礦模型瀏覽、複製或預測。 預測查詢會使用選取的表單來根據現有的採礦模型建立預測。 函數會將您瀏覽與查詢採礦模型的能力擴充到資料採礦模型的內建功能之外。  
  
 您可以使用 DMX 函數，取得在培訓模型過程中探索到的資訊，以及計算新資訊。 這些函數可以用於許多用途，包括傳回描述基礎資料或預測精確度的統計資料，以及傳回預測的擴充說明。  
  
 **如需詳細** **資訊：** [了解 DMX Select 陳述式](../dmx/understanding-the-dmx-select-statement.md)，[一般預測函數&#40;DMX&#41;](../dmx/general-prediction-functions-dmx.md)，[結構和使用方式的 DMX 預測查詢](../dmx/structure-and-usage-of-dmx-prediction-queries.md)，[資料採礦擴充功能&#40;DMX&#41;函式參考](../dmx/data-mining-extensions-dmx-function-reference.md)  
  
 [回到 DMX 陳述式](#BKMK_DMXStatements)  
  
## <a name="see-also"></a>另請參閱  
 [資料採礦延伸模組&#40;DMX&#41;函式參考](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [資料採礦延伸模組&#40;DMX&#41;運算子參考](../dmx/data-mining-extensions-dmx-operator-reference.md)   
 [資料採礦延伸模組&#40;DMX&#41;陳述式參考](../dmx/data-mining-extensions-dmx-statements.md)   
 [資料採礦延伸模組&#40;DMX&#41;語法慣例](../dmx/data-mining-extensions-dmx-syntax-conventions.md)   
 [資料採礦延伸模組&#40;DMX&#41;語法元素](../dmx/data-mining-extensions-dmx-syntax-elements.md)   
 [一般預測函數&#40;DMX&#41;](../dmx/general-prediction-functions-dmx.md)   
 [DMX 預測查詢的結構和使用方式](../dmx/structure-and-usage-of-dmx-prediction-queries.md)   
 [了解 DMX Select 陳述式](../dmx/understanding-the-dmx-select-statement.md)  
  
  
