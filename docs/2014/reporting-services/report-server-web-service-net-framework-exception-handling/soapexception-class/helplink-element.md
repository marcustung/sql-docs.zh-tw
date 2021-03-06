---
title: HelpLink 項目 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- HelpLink element
- SoapException class
ms.assetid: a4489103-a874-44c2-8f75-95cb238928ed
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 7bdd18641663003a1878fe0af0ac1d39a16eda1f
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/15/2019
ms.locfileid: "63046020"
---
# <a name="helplink-element"></a>HelpLink 元素
  **Detail** 屬性的 **HelpLink** 項目是報表伺服器所產生的 URL 字串。 URL 會以 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] 說明及支援所管理的網頁為目標，並提供有關 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 中發生的特定錯誤之其他說明與知識庫文章。 URL 具有下列語法：  
  
 **http://** www.microsoft.com **/** 產品 **/** ee **/** transform.aspx**嗎？EvtSrc**=_值_ **& EvtID**=_值_ **& ProdName** =_值_ **& ProdVer**=_值_  
  
 下表列出 **HelpLink** URL 的引數。  
  
|引數|值|  
|--------------|-----------|  
|**EvtSrc**|"Microsoft.ReportingServices.Diagnostics.ErrorStrings.resources.Strings"|  
|**EvtID**|例如，報表伺服器錯誤碼，rsReservedItem。|  
|**ProdName**|"Microsoft SQL%20Server%20Reporting%20Services"。 產品名稱值是編碼的 URL。|  
|**ProdVer**|[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 的版本號碼。 "8.00" 的值表示 [!INCLUDE[ssVersion2000](../../../includes/ssversion2000-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]。|  
  
 下列範例說明**HelpLink**會傳回錯誤的程式碼的 URL `rsReservedItem`。 當使用者嘗試修改或刪除在 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 中的保留項目時，就會發生這個錯誤。  
  
```  
https://www.microsoft.com/products/ee/transform.aspx?  
EvtSrc=Microsoft.ReportingServices.Diagnostics.ErrorStrings.resources.Strings  
&EvtID=rsReservedItem&ProdName=Microsoft%20SQL%20Server%20Reporting%20Services&ProdVer=8.00  
```  
  
 您可以使用 **SoapException** 類別來存取程式碼中的 **HelpLink** 項目。  
  
```vb  
Try  
   rs.DeleteItem("/Report1")  
  
Catch e As SoapException  
   Console.WriteLine(e.Detail("HelpLink").InnerXml)  
End Try  
```  
  
```csharp  
try  
{  
   rs.DeleteItem("/Report1");  
}  
  
catch (SoapException e)  
{  
   Console.WriteLine(e.Detail["HelpLink"].InnerXml);  
}  
```  
  
## <a name="see-also"></a>另請參閱  
 [Reporting Services 中的例外狀況處理簡介](../introducing-exception-handling-in-reporting-services.md)   
 [Reporting Services SoapException 類別](reporting-services-soapexception-class.md)   
 [使用 Detail 屬性來處理特定的錯誤](../best-practices/using-the-detail-property-to-handle-specific-errors.md)  
  
  
