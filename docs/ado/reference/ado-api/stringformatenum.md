---
title: StringFormatEnum | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- StringFormatEnum
helpviewer_keywords:
- StringFormatEnum enumeration [ADO]
ms.assetid: 28f7d1ec-092b-4323-a39d-d3f882c6c81a
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 85bef64902f014e7b5269d6df328128bc8fe8d6e
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "67937886"
---
# <a name="stringformatenum"></a>StringFormatEnum
擷取時指定的格式[資料錄集](../../../ado/reference/ado-api/recordset-object-ado.md)做為字串。  
  
|常數|值|描述|  
|--------------|-----------|-----------------|  
|**adClipString**|2|依資料列會分隔*RowDelimiter*，資料行*ColumnDelimiter*，和 null 值*NullExpr*。 這三個參數的[GetString](../../../ado/reference/ado-api/getstring-method-ado.md)方法會只使用有效*StringFormat*的**adClipString**。|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC 對等項目  
 封裝： **com.ms.wfc.data**  
  
|常數|  
|--------------|  
|AdoEnums.StringFormat.CLIPSTRING|  
  
## <a name="applies-to"></a>適用於  
 [GetString 方法 (ADO)](../../../ado/reference/ado-api/getstring-method-ado.md)
