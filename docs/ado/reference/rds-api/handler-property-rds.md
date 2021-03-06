---
title: 處理常式屬性 (RDS) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- Handler property [ADO]
ms.assetid: fdc34362-6d47-4727-b171-8d033159408e
author: MightyPen
ms.author: genemi
ms.openlocfilehash: a7423879b8263d87575d913c4863143faf3573e5
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "67963998"
---
# <a name="handler-property-rds"></a>Handler 屬性 (RDS)
指出擴充功能的伺服器端自訂計劃 （處理常式） 的名稱[RDSServer.DataFactory](../../../ado/reference/rds-api/datafactory-object-rdsserver.md)，以及任何所使用的參數*處理常式*。  
  
 **適用於：** [DataControl 物件 (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
> [!IMPORTANT]
>  從 Windows 8 和 Windows Server 2012 開始，RDS 伺服器元件不會再包含在 Windows 作業系統中 (請參閱 Windows 8 和[Windows Server 2012 相容性操作手冊](https://www.microsoft.com/download/details.aspx?id=27416)如需詳細資訊)。 RDS 用戶端元件將會在 Windows 的未來版本中移除。 請避免在新的開發工作中使用這項功能，並規劃修改目前使用這項功能的應用程式。 使用 RDS 的應用程式應該移轉至[WCF 資料服務](https://go.microsoft.com/fwlink/?LinkId=199565)。  
  
## <a name="syntax"></a>語法  
  
```  
  
DataControl.Handler = String  
```  
  
#### <a name="parameters"></a>參數  
 *DataControl*  
 物件變數，表示[rds。DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md)物件。  
  
 *String*  
 A**字串**所有以逗號分隔值，包含這個處理常式和任何參數，名稱 (例如`"handlerName,parm1,parm2,...,parm` *N*`"`)。  
  
## <a name="remarks"></a>備註  
 此屬性支援[自訂](../../../ado/guide/remote-data-service/datafactory-customization.md)，需要設定的功能[CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md)屬性設**adUseClient**。  
  
 名稱的處理常式和其參數，如果有的話，以逗號分隔 （"，"）。 如果分號，將會造成無法預期的行為 （";"） 內任意處出現*字串*。 您可以撰寫自己的處理常式，前提是它支援**IDataFactoryHandler**介面。  
  
 預設處理常式名稱是**MSDFMAP。處理常式**，其預設參數，而且 自訂檔案，名為**MSDFMAP。INI**。 您可以使用這個屬性來叫用您的伺服器系統管理員所建立的替代自訂檔案。  
  
 設定的替代方案**處理常式**屬性會指定處理常式和中的參數[ConnectionString](../../../ado/reference/ado-api/connectionstring-property-ado.md)屬性，也就是 「**處理常式 =** _handlerName parameter1、 parameter2，...，_ ".  
  
## <a name="applies-to"></a>適用於  
 [DataControl 物件 (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)  
  
## <a name="see-also"></a>另請參閱  
 [Handler 屬性範例 (VB)](../../../ado/reference/rds-api/handler-property-example-vb.md)   
 [DataFactory 自訂](../../../ado/guide/remote-data-service/datafactory-customization.md)   
 [DataFactory 物件 (RDSServer)](../../../ado/reference/rds-api/datafactory-object-rdsserver.md)


