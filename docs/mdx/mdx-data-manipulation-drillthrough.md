---
title: DRILLTHROUGH 陳述式 (MDX) |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 0149898e44476233eafcb226a221fc5cc48ae1d5
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "68006261"
---
# <a name="mdx-data-manipulation---drillthrough"></a>MDX 資料操作 - DRILLTHROUGH


  擷取在 Cube 中用來建立指定資料格的基礎資料表資料列。  
  
## <a name="syntax"></a>語法  
  
```  
  
DRILLTHROUGH[MAXROWSUnsigned_Integer]   
      <MDX SELECT statement>   
      [RETURNSet_of_Attributes_and_Measures   
            [,Set_of_Attributes_and_Measures ...]  
      ]  
```  
  
## <a name="arguments"></a>引數  
 *Unsigned_Integer*  
 正整數值。  
  
 *MDX SELECT 陳述式*  
 任何有效的多維度運算式 (MDX) 運算式 SELECT 陳述式。  
  
 *Set_of_Attributes_and_Measures*  
 以逗號分隔的維度屬性和量值清單。  
  
## <a name="remarks"></a>備註  
 在鑽研作業中，使用者會從 Cube 選取單一資料格，並且從該資料格的來源資料中擷取結果集，以便取得更詳細的資訊。 依預設，鑽研結果集是從評估以計算所選 Cube 資料格之值的資料表資料列衍生而來。 若要讓使用者能執行鑽研，用戶端應用程式必須支援此功能。 在  [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]，直接從 MOLAP 儲存所擷取的結果，除非查詢 ROLAP 資料分割或維度。  
  
> [!IMPORTANT]  
>  鑽研安全性是以定義於 Cube 的一般安全性選項為基礎。 如果使用者無法透過 MDX 取得某些資料，鑽研也會以完全相同的方式限制使用者。  
  
 MDX 陳述式可指定主旨資料格。 所指定的值**MAXROWS**引數指出應該傳回結果的資料列集的資料列的數目上限。  
  
 根據預設，傳回的資料列數上限為 10,000 個資料列。 這表示，如果您離開**MAXROWS**未指定，您將得到 10,000 個資料列或更少。 如果此值為對您的案例而言太低，您可以設定**MAXROWS**更高的數字，例如`MAXROWS 20000`。 如果是過低整體來說，您還可以增加預設值，藉由變更**OLAP\Query\DefaultDrillthroughMaxRows**伺服器屬性。 如需變更此屬性的詳細資訊，請參閱[Server Properties in Analysis Services](../analysis-services/server-properties/server-properties-in-analysis-services.md)。  
  
 除非另有指定，否則所傳回的資料行會包含與指定量值之量值群組相關的所有維度 (多對多維度除外) 之全部資料粒度屬性。 Cube 維度前面有 $，以區分維度和量值群組。 **傳回**子句來指定鑽研查詢所傳回的資料行。 下列函數可套用至單一屬性，或藉由測量**傳回**子句。  
  
 Name(attribute_name)  
 傳回指定屬性成員的名稱。  
  
 UniqueName(attribute_name)  
 傳回指定屬性成員的唯一名稱。  
  
 Key(attribute_name[, N])  
 傳回指定屬性成員的索引鍵，其中 N 指定複合索引鍵 (如果有的話) 的資料行。 N 的預設值是 1。  
  
 Caption(attribute_name)  
 傳回指定之屬性成員的標題。  
  
 MemberValue(attribute_name)  
 傳回指定之屬性成員的成員值。  
  
 CustomRollup(attribute_name)  
 傳回所指定屬性成員的自訂積存運算式。  
  
 CustomRollupProperties(attribute_name)  
 傳回所指定屬性 (Attribute) 成員的自訂積存屬性 (Property)。  
  
 UnaryOperator(attribute_name)  
 傳回所指定屬性成員的一元運算子。  
  
## <a name="example"></a>範例  
 下列範例會指定 2007 年 7 月澳大利亞轉售商銷售數量量值 (預設量值) 的資料格。 RETURN 子句會指定所傳回之資料格的基礎：每個銷售日期、產品型號名稱、員工名稱、銷售額、稅額及產品成本值。  
  
```  
DRILLTHROUGH  
SELECT  
   ([Date].[Calendar].[Month].[July 2007])  
ON 0   
FROM [Adventure Works]  
WHERE [Geography].[Country].[Australia]  
RETURN   
  [$Date].[Date]  
  ,KEY([$Product].[Model Name])  
  ,NAME([$Employee].[Employee])  
  ,[Reseller Sales].[Reseller Sales Amount]  
  ,[Reseller Sales].[Reseller Tax Amount]  
  ,[Reseller Sales].[Reseller Standard Product Cost]  
```  
  
## <a name="see-also"></a>另請參閱  
 [MDX 資料操作陳述式&#40;MDX&#41;](../mdx/mdx-data-manipulation-statements-mdx.md)  
  
  
