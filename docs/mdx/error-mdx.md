---
title: 錯誤 (MDX) |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
ms.openlocfilehash: 91d07c6bbb4eb4731c9a802e47cd8f4c71aa5aeb
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "68031234"
---
# <a name="error-mdx"></a>Error (MDX)


  引發錯誤，選擇性提供指定的錯誤訊息。  
  
## <a name="syntax"></a>語法  
  
```  
  
Error( [ Error_Text ] )  
```  
  
## <a name="arguments"></a>引數  
 *Error_Text*  
 包含要傳回之錯誤訊息的有效字串運算式。  
  
## <a name="examples"></a>範例  
 下列查詢會示範如何使用**錯誤**內的導出量值函式：  
  
 `WITH MEMBER MEASURES.ERRORDEMO AS ERROR("THIS IS AN ERROR")`  
  
 `SELECT`  
  
 `MEASURES.ERRORDEMO ON 0`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>另請參閱  
 [MDX 函數參考 &#40;MDX&#41;](../mdx/mdx-function-reference-mdx.md)  
  
  
