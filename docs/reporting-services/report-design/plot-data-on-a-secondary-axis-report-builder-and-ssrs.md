---
title: 繪製次要座標軸上的資料 (報表產生器及 SSRS) | Microsoft Docs
ms.date: 05/30/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-design
ms.topic: conceptual
ms.assetid: 094f39bf-3634-4852-9fc3-3adec4b266e5
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 86d73f2ab16bdb7ee801e333f3a75c96a2a1c360
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 06/15/2019
ms.locfileid: "65578183"
---
# <a name="plot-data-on-a-secondary-axis-report-builder-and-ssrs"></a>繪製次要座標軸上的資料 (報表產生器及 SSRS)

圖表有兩種軸類型：主要及次要。 在比較共用相同類別目錄，但具有不同資料範圍的值組時，次要軸很有用。  
  
 例如，假設您有一張圖表計算 2008 年年度營收與稅額的比較。 在此例中，兩個值組都共用 2008 時間週期。 不過，如果在同一 Y 軸上繪製這兩個數列，我們將無法進行有效的比較，因為 Y 軸的刻度會針對資料組中最大的值進行最佳化。 如果在主要軸上顯示「營收」，而在次要軸上顯示「稅額」，就可以在 Y 軸上以每個數列本身的值刻度來顯示數列。 數列仍會共用相同的 X 軸。  
  
 如果比較的數列超過兩個，請考慮不同的方法來在圖表中比較及顯示多個數列。 如需詳細資訊，請參閱[圖表上的多個數列](../../reporting-services/report-design/multiple-series-on-a-chart-report-builder-and-ssrs.md)。  
  
 此圖表的範例可從範例報表取得。 如需有關下載這個範例報表及其他項目的詳細資訊，請參閱 [報表產生器與報表設計師範例報表](https://go.microsoft.com/fwlink/?LinkId=198283)。  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-plot-a-series-on-the-secondary-axis"></a>若要在次要座標軸上繪製數列  
  
1.  以滑鼠右鍵按一下圖表中的數列，或以滑鼠右鍵按一下要在次要軸上顯示之 **[值]** 區域中的欄位，然後按一下 **[數列屬性]** 。 **[數列屬性]** 對話方塊便會出現。  
  
2.  按一下 **[軸和圖表區域]** ，然後選取要啟用的次要軸、值軸或類別目錄軸。  

## <a name="next-steps"></a>後續步驟

[格式化圖表上的軸標籤](../../reporting-services/report-design/formatting-axis-labels-on-a-chart-report-builder-and-ssrs.md)   
[指定軸間隔](../../reporting-services/report-design/specify-an-axis-interval-report-builder-and-ssrs.md)  

更多問題嗎？ [請嘗試詢問 Reporting Services 論壇](https://go.microsoft.com/fwlink/?LinkId=620231)
