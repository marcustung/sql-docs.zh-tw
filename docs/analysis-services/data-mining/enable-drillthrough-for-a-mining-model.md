---
title: 針對採礦模型啟用鑽研 |Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: data-mining
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: ec6d880c6b32a092f6d4da8b85dfd6693280da7d
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/15/2019
ms.locfileid: "68210023"
---
# <a name="enable-drillthrough-for-a-mining-model"></a>針對採礦模型啟用鑽研
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  如果您已經啟用採礦模型的鑽研，當您瀏覽此模型時，可以擷取有關用來建立模型之案例的詳細資訊。 若要檢視這項資訊，您必須擁有必要的權限，而且結構必須已經經過處理。  
  
 **權限** ：若要讓使用者鑽研模型資料或結構資料，該使用者必須是針對採礦模型或採礦結構擁有 [AllowDrillThrough](https://docs.microsoft.com/bi-reference/assl/properties/allowdrillthrough-element-assl) 權限之角色的成員。 鑽研權限是在結構和模型上分別設定的。  
  
-   即使您沒有結構的權限，模型的鑽研權限還是可以讓您從模型進行鑽研。  
  
-   結構的鑽研權限可以使用 [StructureColumn &#40;DMX&#41;](../../dmx/structurecolumn-dmx.md) 函數，提供將結構資料行從模型加入到鑽研查詢的額外功能。 您也可以查詢的定型和測試案例，在結構中，方法是使用 SELECT...從\<結構 >。案例的語法。  
  
 **快取定型案例** ：鑽研藉由擷取採礦結構中定型案例的相關資訊來運作。 這項資訊會在處理結構時快取。 因此，如果您選擇將 <xref:Microsoft.AnalysisServices.MiningStructureCacheMode> 屬性變更為 **ClearAfterProcessing**來清除所有快取的資料，鑽研將不會運作。  
  
> [!NOTE]  
>  如果尚未快取定型案例，您必須將 <xref:Microsoft.AnalysisServices.MiningStructureCacheMode> 屬性變更為 **KeepTrainingCases** ，然後在可以檢視案例資料之前，重新處理模型。  
  
 如需詳細資訊，請參閱 [鑽研查詢 &#40;資料採礦&#41;](../../analysis-services/data-mining/drillthrough-queries-data-mining.md)。  
  
### <a name="to-enable-drillthrough-on-a-mining-model"></a>針對採礦模型啟用鑽研  
  
1.  在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 中，於資料採礦設計師的 [採礦模型]  索引標籤上，以滑鼠右鍵按一下您想要啟用鑽研之採礦模型的名稱，然後選取 [屬性]  。  
  
2.  在 [屬性]  視窗中，按一下 [AllowDrillThrough]  ，然後選取 [True]  。  
  
3.  在 [採礦模型]  索引標籤中，以滑鼠右鍵按一下模型，然後選取 [處理模型]  。  
  
### <a name="to-enable-caching-for-a-mining-structure"></a>針對採礦結構啟用快取  
  
1.  在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 中，於資料採礦設計師的 [採礦結構]  索引標籤上，以滑鼠右鍵按一下採礦結構的名稱。  
  
2.  開啟 [屬性]  視窗。  
  
3.  在 [屬性]  視窗中，找出 **CacheMode** 屬性，然後從清單中選取 [KeepTrainingCases]  。  
  
4.  在 [資料庫]  功能表中，選取 [處理]  。  
  
## <a name="see-also"></a>另請參閱  
 [鑽研查詢 &#40;資料採礦&#41;](../../analysis-services/data-mining/drillthrough-queries-data-mining.md)  
  
  
