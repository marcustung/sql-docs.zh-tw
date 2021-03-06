---
title: 交叉驗證公式 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: fd1ea582-29a1-4154-8de2-47bab3539b4d
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ccdf0285dc110cde89e08778f6badf56f586a5ab
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/15/2019
ms.locfileid: "66085153"
---
# <a name="cross-validation-formulas"></a>交叉驗證公式
  當您產生交叉驗證報表時，報表會根據採礦模型類型包含每一個模型的精確度量值 (也就是之前用來建立模型的演算法)、可預測屬性的資料類型，以及可預測的屬性值 (如果有的話)。  
  
 本節列出交叉驗證報表中所使用的量值，並描述計算的方法。  
  
 如需依模型類型的精確度量值分解，請參閱 [交叉驗證報表中的量值](measures-in-the-cross-validation-report.md)。  
  
## <a name="formulas-used-for-cross-validation-measures"></a>交叉驗證量值所使用的公式  
  
> [!NOTE]  
>  **重要：** 每一個目標屬性計算這些精確度量值。 您可以針對每一個屬性指定或省略目標值。 如果資料集內的案例沒有任何目標屬性值，此案例會視為擁有特殊值，稱為 *「遺漏值」* (Missing Value)。 計算特定目標屬性的精確度量值時，不會計算有遺漏值的資料列。 請注意，由於分數是分別針對每一個屬性計算而得，因此如果目標屬性的值存在，而其他屬性有遺漏值，這樣並不會影響目標屬性的分數。  
  
|[量值]|適用於|實作|  
|-------------|----------------|--------------------|  
|**真肯定**|離散屬性，已指定值|符合這些條件的案例計數：<br /><br /> 案例包含目標值。<br /><br /> 模型預測出案例包含目標值。|  
|**真否定**|離散屬性，已指定值|符合這些條件的案例計數：<br /><br /> 案例不包含目標值。<br /><br /> 模型預測出案例不包含目標值。|  
|**誤判**|離散屬性，已指定值|符合這些條件的案例計數：<br /><br /> 實際的值等於目標值。<br /><br /> 模型預測出案例包含目標值。|  
|**誤否定**|離散屬性，已指定值|符合這些條件的案例計數：<br /><br /> 實際的值不等於目標值。<br /><br /> 模型預測出案例不包含目標值。|  
|**通過/失敗**|離散屬性，沒有指定的目標|符合這些條件的案例計數：<br /><br /> 如果具有最高機率的預測狀態與輸入狀態相同，且機率大於 [狀態臨界值]  的值，則通過。<br /><br /> 否則為失敗。|  
|**增益**|離散屬性。 您可以指定目標值，但並非必要條件。|包含目標屬性值之所有資料列的平均對數可能性，其中每一個案例的對數可能性會計算為 Log(ActualProbability/MarginalProbability)。 若要計算平均值，會將對數概似值的總和除以輸入資料集中的資料列數，不包括目標屬性擁有遺漏值的資料列。<br /><br /> 增益可以是負值或正值。 正值代表優於隨機猜測的有效模型。|  
|**對數分數**|離散屬性。 您可以指定目標值，但並非必要條件。|每一個案例之實際機率的對數，經過加總，然後除以輸入資料集中的資料列數目，不包括目標屬性擁有遺漏值的資料列。<br /><br /> 由於機率會以小數表示，因此對數分數永遠為負數。 分數越接近 0，表示得分越高。|  
|**案例概似值**|叢集|所有案例的叢集概似值分數總和，除以資料分割中的案例數目，不包括目標屬性擁有遺漏值的資料列。|  
|**平均絕對誤差**|連續屬性|資料分割中所有案例的絕對錯誤總和，除以資料分割中的案例數目。|  
|**均方根誤差**|連續屬性|資料分割之均方誤差的平方根。|  
|**均方根誤差**|離散屬性。 您可以指定目標值，但並非必要條件。|機率分數補數平方之平均數的平方根，除以資料分割中的案例數目，不包括目標屬性擁有遺漏值的資料列。|  
|**均方根誤差**|離散屬性，沒有指定的目標。|機率分數補數平方之平均數的平方根，除以資料分割中的案例數目，不包括目標屬性擁有遺漏值的案例。|  
  
## <a name="see-also"></a>另請參閱  
 [測試和驗證 &#40;資料採礦&#41;](testing-and-validation-data-mining.md)   
 [交叉驗證 &#40;Analysis Services - 資料採礦&#41;](cross-validation-analysis-services-data-mining.md)  
  
  
