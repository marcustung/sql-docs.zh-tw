---
title: Analysis Services 表格式模型中建立的關聯性 |Microsoft Docs
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 7e9ee96a04aa6b023be51f8e1e8d913e26a7e2a8
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/15/2019
ms.locfileid: "68207742"
---
# <a name="create-a-relationship"></a>建立關聯性 
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  如果您資料來源中的資料表並沒有關聯性存在，或如果您要新增資料表，則可以使用模型設計師中的工具來建立新的關聯性。 如需如何在表格式模型中使用關聯性的資訊，請參閱[關聯性](../../analysis-services/tabular-models/relationships-ssas-tabular.md)。  
  
## <a name="create-a-relationship-between-two-tables"></a>建立兩個資料表之間的關聯性  
  
#### <a name="to-create-a-relationship-between-two-tables-in-diagram-view-click-and-drag"></a>在圖表檢視中建立兩個資料表之間的關聯性 (按住並拖曳)  
  
1.  在 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]中，按一下 **[模型]** 功能表，然後按一下 **[模型檢視]** ，再按一下 **[圖表檢視]** 。  
  
2.  按住資料表中的資料行，再將游標拖曳至相關查閱資料表中的相關查閱資料行，然後放開。 即可以正確的順序自動建立關聯性。  
  
#### <a name="to-create-a-relationship-between-two-tables-in-diagram-view-right-click"></a>在圖表檢視中建立兩個資料表之間的關聯性 (按一下滑鼠右鍵)  
  
1.  在 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]中，按一下 **[模型]** 功能表，然後按一下 **[模型檢視]** ，再按一下 **[圖表檢視]** 。  
  
2.  以滑鼠右鍵按一下資料表標題或資料行，然後按一下 [建立關聯性]  。  
  
3.  在 **[建立關聯性]** 對話方塊的 **[資料表]** 中，按一下向下鍵，然後從下拉式清單中選取資料表。  
  
     在「一對多」關聯性中，這個資料表應該是「多」邊。  
  
4.  針對 **[資料行]** ，選取包含與 **[相關查閱資料行]** 相關之資料的資料行。 若您以滑鼠右鍵按一下資料行來建立關聯性，則會自動選取資料行。  
  
5.  針對 **[相關查閱資料表]** 選取資料表，其中至少有一個資料行與剛才針對 **[資料表]** 選取的資料表相關聯。  
  
     在「一對多」關聯性中，此資料表應該是「一」邊，也就是說，所選資料行中的值不包含重複的項目。 如果您嘗試以錯誤的順序 (一對多而非多對一) 建立關聯性，圖示將會出現在 [相關查閱資料行]  欄位的旁邊。 反轉順序來建立有效的關聯性。  
  
6.  針對 **[相關查閱資料行]** 選取資料行，其唯一值與針對 **[資料行]** 選取之資料行中的值相符。  
  
7.  按一下 [建立]  。  
  
#### <a name="to-create-a-relationship-between-two-tables-in-data-view"></a>在資料檢視中建立兩個資料表之間的關聯性  
  
1.  在 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]中，按一下 **[資料表]** 功能表，然後按一下 **[建立關聯性]** 。  
  
2.  在 **[建立關聯性]** 對話方塊的 **[資料表]** 中，按一下向下鍵，然後從下拉式清單中選取資料表。  
  
     在「一對多」關聯性中，這個資料表應該是「多」邊。  
  
3.  針對 **[資料行]** ，選取包含與 **[相關查閱資料行]** 相關之資料的資料行。  
  
4.  針對 **[相關查閱資料表]** 選取資料表，其中至少有一個資料行與剛才針對 **[資料表]** 選取的資料表相關聯。  
  
     在「一對多」關聯性中，此資料表應該是「一」邊，也就是說，所選資料行中的值不包含重複的項目。 如果您嘗試以錯誤的順序 (一對多而非多對一) 建立關聯性，圖示將會出現在 [相關查閱資料行]  欄位的旁邊。 反轉順序來建立有效的關聯性。  
  
5.  針對 **[相關查閱資料行]** 選取資料行，其唯一值與針對 **[資料行]** 選取之資料行中的值相符。  
  
6.  按一下 [建立]  。  
  
## <a name="see-also"></a>另請參閱  
 [刪除關聯性](../../analysis-services/tabular-models/delete-relationships-ssas-tabular.md)   
 [關聯性](../../analysis-services/tabular-models/relationships-ssas-tabular.md)  
  
  
