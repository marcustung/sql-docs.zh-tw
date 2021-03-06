---
title: NumericScale 屬性 (ADO) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Parameter::NumericScale
- Field20::NumericScale
helpviewer_keywords:
- NumericScale property [ADO]
ms.assetid: 29a02992-64be-4fcd-be13-445cba205893
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 38d283e8fedb90ed5a99143090bc6a077efa8512
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "67932100"
---
# <a name="numericscale-property-ado"></a>NumericScale 屬性 (ADO)
中的數值，指出[參數](../../../ado/reference/ado-api/parameter-object.md)或是[欄位](../../../ado/reference/ado-api/field-object.md)物件。  
  
## <a name="settings-and-return-values"></a>設定和傳回值  
 設定或傳回**位元組**值，指出哪一個數字值的小數位數會解析。  
  
## <a name="remarks"></a>備註  
 使用**NumericScale**屬性，以判斷小數點右邊的位數數目會用來代表一個數字的值**參數**或是**欄位**物件。  
  
 針對**參數**物件， **NumericScale**屬性是讀取/寫入。  
  
 針對**欄位**物件， **NumericScale**是通常是唯讀。 不過，對於新**欄位**附加到的物件[欄位](../../../ado/reference/ado-api/fields-collection-ado.md)集合[記錄](../../../ado/reference/ado-api/record-object-ado.md)， **NumericScale**是讀取/寫入之後才[值](../../../ado/reference/ado-api/value-property-ado.md)屬性**欄位**已指定與此資料提供者已成功地加入新**欄位**藉由呼叫[更新](../../../ado/reference/ado-api/update-method.md)方法[欄位](../../../ado/reference/ado-api/fields-collection-ado.md)集合。  
  
## <a name="applies-to"></a>適用於  
  
|||  
|-|-|  
|[Parameter 物件](../../../ado/reference/ado-api/parameter-object.md)|[Field 物件](../../../ado/reference/ado-api/field-object.md)|  
  
## <a name="see-also"></a>另請參閱  
 [NumericScale 和 Precision 屬性範例 (VB)](../../../ado/reference/ado-api/numericscale-and-precision-properties-example-vb.md)   
 [NumericScale 和 Precision 屬性範例 （VC + +）](../../../ado/reference/ado-api/numericscale-and-precision-properties-example-vc.md)   
 [Precision 屬性 (ADO)](../../../ado/reference/ado-api/precision-property-ado.md)
