---
title: 使用 「 維度精靈 」 建立維度 |Microsoft Docs
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: multidimensional-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: ba906ab17169b2e2faf6bef54137fcc4e6210660
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/15/2019
ms.locfileid: "62866873"
---
# <a name="create-a-dimension-using-the-dimension-wizard"></a>使用維度精靈建立維度
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  您可以使用 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中的 [維度精靈] 來建立新的維度。  
  
### <a name="to-create-a-new-dimension"></a>建立新維度  
  
1.  在**方案總管**中，以滑鼠右鍵按一下 [維度]  ，再按一下 [新增維度]  。  
  
2.  在「維度精靈」的 [選取建立方法]  頁面上，選取 [使用現有的資料表]  ，然後按一下 [下一步]  。  
  
    > [!NOTE]  
    >  您可能偶爾必須在不使用現有資料表的情況下建立維度。 如需詳細資訊，請參閱[在資料來源中產生非時間資料表來建立維度](../../analysis-services/multidimensional-models/create-a-dimension-by-generating-a-non-time-table-in-the-data-source.md)和 [Create a Time Dimension by Generating a Time Table](../../analysis-services/multidimensional-models/create-a-time-dimension-by-generating-a-time-table.md) (透過產生時間資料表來建立時間維度)。  
  
3.  在 [指定來源資訊]  頁面上，執行下列程序：  
  
    1.  在 [資料來源檢視]  清單中，選取資料來源檢視。  
  
    2.  在 [主資料表]  中，選取主維度資料表。  
  
    3.  在 [索引鍵資料行]  清單中，檢閱精靈根據您在主維度資料表中定義之主索引鍵，自動選取的索引鍵資料行。 若要變更此預設值，指定連結維度資料表和事實資料表的索引鍵資料行。  
  
    4.  在 [名稱資料行]  下拉式清單中，檢閱精靈已經自動選取的名稱資料行。  
  
         當資料行包含描述性資訊時，適合使用這個預設名稱。 不過，您可能想要指定包含對於使用者更有意義之值的名稱。 例如，如果 Products 維度中的產品類別目錄屬性使用 **ProductCategoryKey** 資料行作為其索引鍵資料行，您可以指定 **ProductCategoryName** 資料行作為其名稱資料行。  
  
         如果 [索引鍵資料行]  清單包含多個索引鍵資料行，您必須可針對索引鍵屬性提供成員值的名稱資料行。 若要這樣做，您可以在資料來源檢視中，建立具名計算，並將其當做名稱資料行使用。  
  
    5.  按一下 [下一步]  。  
  
4.  在 [選取相關資料表]  頁面上，選取您要包含在維度中的相關資料表，然後按一下 [下一步]  。  
  
    > [!NOTE]  
    >  如果您指定的主維度資料表與其他維度資料表有關聯性，會出現 [選取相關資料表]  頁面。  
  
5.  在 [選取維度屬性]  頁面上，選取您要包含在維度中的屬性，然後按一下 [下一步]  。  
  
     您可以選擇性地變更屬性名稱、啟用或停用瀏覽，以及指定屬性類型。  
  
    > [!NOTE]  
    >  若要啟用屬性的 [啟用瀏覽]  和 [屬性類型]  欄位，必須選取該屬性才能包含到維度中。  
  
6.  在 [定義帳戶智慧]  頁面的 [內建帳戶類型]  資料行上，選取帳戶類型，然後按一下 [下一步]  。  
  
     帳戶類型必須對應到 [來源資料表帳戶類型]  資料行中所列之來源資料表的帳戶類型。  
  
    > [!NOTE]  
    >  如果您在精靈的 [選取維度屬性]  頁面上定義 [帳戶類型]  維度屬性，會出現 [定義帳戶智慧]  頁面。  
  
7.  在 [正在完成精靈]  頁面上，輸入新維度的名稱，然後檢閱維度的結構。 如果您要進行任何變更，按一下 [上一步]  ，否則，按一下 [完成]  。  
  
    > [!NOTE]  
    >  您可以在完成「維度精靈」之後，使用 [維度設計師] 在維度中加入、移除和設定屬性與階層。  
  
## <a name="see-also"></a>另請參閱  
 [使用現有的資料表建立維度](../../analysis-services/multidimensional-models/create-a-dimension-by-using-an-existing-table.md)  
  
  
