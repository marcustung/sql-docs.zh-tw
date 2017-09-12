---
title: "CREATE CELL CALCULATION 陳述式 (MDX) |Microsoft 文件"
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CELL CALCULATION
- CREATE
- CALCULATION
- CELL
- CREATE_CELL_CALCULATION
- CREATE CELL
- CREATE CELL CALCULATION
dev_langs:
- kbMDX
helpviewer_keywords:
- calculations [Analysis Services], creating
- CREATE CELL CALCULATION statement
- cubes [Analysis Services], calculations
ms.assetid: 01ced1b3-ada1-4b55-b350-e4255c3cc679
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 8d371e3ca64f848cb30f54fe1f0ce4eb98a648a4
ms.contentlocale: zh-tw
ms.lasthandoff: 08/02/2017

---
# <a name="mdx-data-definition---create-cell-calculation"></a>MDX 資料定義-建立資料格計算
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  在 Cube 內指定的 Tuple 集合上，建立評估多維度運算式 (MDX) 運算式的計算。  
  
## <a name="syntax"></a>語法  
  
```  
  
[WITH <CELL CALCULATION clause> Calculation_Name  
   [,WITH <CELL CALCULATION clause> Calculation_Name...n]  
CREATE CELL CALCULATION CURRENTCUBE | Cube_Name.Calculation_Name   
  
<CELL CALCULATION clause> ::=  
   FOR Set_Expression AS 'MDX_Expression'   
      [ [ CONDITION = 'Logical_Expression' ]   
    | [ DISABLED = { TRUE | FALSE } ]   
    | [ DESCRIPTION =String ]   
    | [ CALCULATION_PASS_NUMBER = Integer]   
    | [ CALCULATION_PASS_DEPTH = Integer]   
    | [ SOLVE_ORDER = Integer]   
    | [ Calculation_Name= Scalar_Expression ], ...n]  
```  
  
## <a name="arguments"></a>引數  
 *Cube_Name*  
 提供 Cube 名稱的有效字串。  
  
 *Calculation_Name*  
 提供資料格計算名稱的有效字串。  
  
 *Set_Expression*  
 傳回集合的有效 MDX 運算式。  
  
 *字串*  
 有效的字串值。  
  
 *MDX_Expression*  
 有效的 MDX 運算式。  
  
 *Logical_Expression*  
 有效的 MDX 邏輯運算式。  
  
 *Integer*  
 有效的整數值。  
  
 *Calculation_Name*  
 提供資料格計算屬性名稱的有效字串。  
  
 *Scalar_Expression*  
 有效的 MDX 純量運算式。  
  
## <a name="remarks"></a>備註  
 在自訂積存公式或導出成員的情況下，使用導出資料格，用戶端應用程式就可以指定特定資料格集的積存值，而非整個資料格集的積存值。 例如，可以指定由 `{[Canada],[Time].[2000]}` 定義的集合內，任何資料格都可以包含由公式定義的值。 此集合以外的其他資料格，則會正常進行運算。  
  
> [!NOTE]  
>  為了回溯相容性，會將 `{*(<comment> | <whitespace> | <newline>)}` 的巴克斯格式 (Backus-Naur Form，BNF) 剖析為 `{*}`。  
  
## <a name="see-also"></a>另請參閱  
 [建立工作階段範圍導出資料格](../analysis-services/multidimensional-models/mdx/mdx-cell-calculations-session-scoped-calculated-cells.md)   
 [建立查詢範圍資料格計算 & #40;MDX & #41;](../analysis-services/multidimensional-models/mdx/mdx-cell-calculations-query-scoped-cell-calculations.md)   
 [在 MDX & #40; 建立資料格計算MDX & #41;](../analysis-services/multidimensional-models/mdx/mdx-cell-calculations-build-cell-calculations.md)   
 [使用資料格屬性 & #40;MDX & #41;](../analysis-services/multidimensional-models/mdx/mdx-cell-properties-using-cell-properties.md)   
 [FORMAT_STRING 內容 & #40;MDX & #41;](../analysis-services/multidimensional-models/mdx/mdx-cell-properties-format-string-contents.md)   
 [FORE_COLOR 及 BACK_COLOR 內容 & #40;MDX & #41;](../analysis-services/multidimensional-models/mdx/mdx-cell-properties-fore-color-and-back-color-contents.md)   
 [MDX 資料定義陳述式 & #40;MDX & #41;](../mdx/mdx-data-definition-statements-mdx.md)  
  
  
