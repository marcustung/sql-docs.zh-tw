---
title: 啟用維度回寫 |Microsoft Docs
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: multidimensional-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 561dc878302afe7636a2660a9e194ac14a35c7f1
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/15/2019
ms.locfileid: "68179112"
---
# <a name="bi-wizard---enable-dimension-writeback"></a>BI 精靈 - 啟用維度回寫
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  加入維度回寫增強功能至 Cube 或維度，以允許使用者手動修改維度結構和成員。 可寫入維度的更新會直接記錄在維度資料表中。 這項增強功能會變更維度的 **WriteEnabled** 屬性設定。  
  
 若要加入維度回寫，您可使用 [商業智慧精靈]，並於 [選擇增強功能]  頁面上選取 [啟用維度回寫]  選項。 然後，此精靈會引導您逐步完成選取要套用維度回寫的維度，並為選取的維度設定此選項。  
  
> [!NOTE]  
>  只有 SQL Server 關聯式資料庫和資料超市才支援回寫。  
  
## <a name="selecting-a-dimension"></a>選取維度  
 在精靈的第一個 [啟用維度回寫]  頁面上，您會指定要套用維度回寫的維度。 加入到此選取維度的維度回寫增強功能會產生維度的變更。 包含選取之維度的所有 Cube，都會繼承這些變更。  
  
## <a name="setting-dimension-writeback-capability"></a>設定維度回寫功能  
 在精靈的第二個 [啟用維度回寫]  頁面上，您可實際設定 [在維度中啟用回寫]  選項。 選取此選項會自動將維度的 **WriteEnabled** 屬性設定為 [True]  。 而清除此選項則會自動將屬性設定為 [False]  。  
  
## <a name="remarks"></a>備註  
 建立新的成員時，您必須包含維度中的每個屬性。 您不能插入成員時不指定維度之索引鍵屬性的值。 因此，建立成員時要受到維度資料表上之已定義的任何條件約束 (例如非 Null 索引鍵值)。 您也應該考慮以維度屬性選擇性指定的資料行，例如在 **CustomRollupColumn**、 **CustomRollupPropertiesColumn** 或 **UnaryOperatorColumn** 維度屬性中指定的資料行。  
  
> [!WARNING]  
>  如果您使用 SQL Azure 做為執行回寫至 Analysis Services 資料庫中的資料來源，作業會失敗。 這是設計所限，因為預設不會開啟可啟用 Multiple Active Result Sets (MARS) 的提供者選項。  
>   
>  解決方法是，在連接字串中加入下列設定，以支援 MARS 並啟用回寫：  
>   
>  `"MultipleActiveResultSets=True"`  
>   
>  如需詳細資訊，請參閱[使用 Multiple Active Result Sets &#40;MARS&#41;](../../relational-databases/native-client/features/using-multiple-active-result-sets-mars.md)。  
  
## <a name="see-also"></a>另請參閱  
 [可寫入維度](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/write-enabled-dimensions.md)  
  
  
