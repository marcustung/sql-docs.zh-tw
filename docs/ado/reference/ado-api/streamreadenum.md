---
title: StreamReadEnum |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- StreamReadEnum
helpviewer_keywords:
- StreamReadEnum enumeration [ADO]
ms.assetid: cfa1b416-003a-436f-a21b-bd2397e54db3
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 7700fc1ddc3cc619db224ac46006370898af1d62
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "67928666"
---
# <a name="streamreadenum"></a>StreamReadEnum
指定的整個資料流] 或 [下一列是否應該從讀取[Stream](../../../ado/reference/ado-api/stream-object-ado.md)物件。  
  
|常數|值|描述|  
|--------------|-----------|-----------------|  
|**adReadAll**|-1|預設值。 及更新版本為從資料流，從目前位置讀取所有位元組[EOS](../../../ado/reference/ado-api/eos-property.md)標記。 這是唯一有效**StreamReadEnum**二進位資料流的值 ([型別](../../../ado/reference/ado-api/type-property-ado-stream.md)會**adTypeBinary**)。|  
|**adReadLine**|-2|從資料流讀取下一行 (所指定[LineSeparator](../../../ado/reference/ado-api/lineseparator-property-ado.md)屬性)。|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC 對等項目  
 這些常數不需要 ADO/WFC 對等項目。  
  
## <a name="applies-to"></a>適用於  
  
|||  
|-|-|  
|[Read 方法](../../../ado/reference/ado-api/read-method.md)|[ReadText 方法](../../../ado/reference/ado-api/readtext-method.md)|
