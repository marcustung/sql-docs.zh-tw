---
title: 狀態屬性 (ADO) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Command25::State
helpviewer_keywords:
- State property [ADO]
ms.assetid: 0b993bac-2653-40b1-bcbb-5b57b6aae2bf
author: MightyPen
ms.author: genemi
ms.openlocfilehash: c45b9331ddd538cdf23a57eaf39b6efb71bccc4a
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "67930856"
---
# <a name="state-property-ado"></a>State 屬性 (ADO)
物件的狀態是否已開啟或關閉，則表示所有適用的物件。 如果物件執行非同步方法，指出是否連接、 執行，或擷取物件的目前狀態。  
  
## <a name="return-value"></a>傳回值  
 傳回**長**值，可以是[ObjectStateEnum](../../../ado/reference/ado-api/objectstateenum.md)值。 預設值是**adStateClosed**。  
  
## <a name="remarks"></a>備註  
 您可以使用**狀態**屬性來判斷在任何時間的指定物件的目前狀態。  
  
 物件的**狀態**屬性可以有值的組合。 例如，如果執行陳述式時，此屬性會有的組合的值**adStateOpen**並**adStateExecuting**。  
  
 **狀態**屬性是唯讀的。  
  
## <a name="applies-to"></a>適用於  
  
||||  
|-|-|-|  
|[Command 物件 (ADO)](../../../ado/reference/ado-api/command-object-ado.md)|[Connection 物件 (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)|[Record 物件 (ADO)](../../../ado/reference/ado-api/record-object-ado.md)|  
|[Recordset 物件 (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)|[Stream 物件 (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)||  
  
## <a name="see-also"></a>另請參閱  
 [ConnectionString、 ConnectionTimeout 和 State 屬性範例 (VB)](../../../ado/reference/ado-api/connectionstring-connectiontimeout-and-state-properties-example-vb.md)   
 [ConnectionString、 ConnectionTimeout 和狀態的屬性範例 （VC + +）](../../../ado/reference/ado-api/connectionstring-connectiontimeout-and-state-properties-example-vc.md)   
