---
title: Optimize 動態屬性 (ADO) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- Optimize property [ADO]
ms.assetid: a491c4ce-2b04-4c84-be83-3846bde8d16b
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 3e8bb3c3787effe8418db735a72425a793b73e35
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "67931856"
---
# <a name="optimize-property-dynamic-ado"></a>Optimize 動態屬性 (ADO)
指定是否應該在建立索引[欄位](../../../ado/reference/ado-api/field-object.md)。  
  
## <a name="settings-and-return-values"></a>設定和傳回值  
 設定或傳回**布林**值，指出是否應該建立索引。  
  
## <a name="remarks"></a>備註  
 索引可改善效能的尋找或排序中的值的作業[資料錄集](../../../ado/reference/ado-api/recordset-object-ado.md)。 索引是以內部 ado;您明確地無法存取，或在您的應用程式中使用它。  
  
 若要在欄位上建立索引，設定**最佳化**屬性設 **，則為 True**。 若要刪除索引，請將此屬性設定為**False**。  
  
 **最佳化**動態屬性附加至[欄位](../../../ado/reference/ado-api/field-object.md)物件[屬性](../../../ado/reference/ado-api/properties-collection-ado.md)集合時[CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md)屬性設定為**adUseClient**。  
  
## <a name="usage"></a>使用量  
  
```  
Dim rs As New Recordset  
Dim fld As Field  
rs.CursorLocation = adUseClient      'Enable index creation  
rs.Fields.Append "Field1", adChar, 35, adFldIsNullable  
rs.Open  
Set fld = rs.Fields(0)  
fld.Properties("Optimize") = True    'Create an index  
fld.Properties("Optimize") = False   'Delete an index  
```  
  
## <a name="applies-to"></a>適用於  
 [Field 物件](../../../ado/reference/ado-api/field-object.md)  
  
## <a name="see-also"></a>另請參閱  
 [Optimize 屬性範例 (VB)](../../../ado/reference/ado-api/optimize-property-example-vb.md)   
 [Optimize 屬性範例 （VC + +）](../../../ado/reference/ado-api/optimize-property-example-vc.md)   
 [篩選屬性](../../../ado/reference/ado-api/filter-property.md)   
 [Find 方法 (ADO)](../../../ado/reference/ado-api/find-method-ado.md)   
 [Sort 屬性](../../../ado/reference/ado-api/sort-property.md)
