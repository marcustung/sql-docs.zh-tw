---
title: sp_registercustomresolver & Amp;#40;transact-SQL&AMP;#41; |Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_registercustomresolver
- sp_registercustomresolver_TSQL
helpviewer_keywords:
- sp_registercustomresolver
ms.assetid: 6d2b0472-0e1f-4005-833c-735d1940fe93
author: stevestein
ms.author: sstein
ms.openlocfilehash: 0d003cccfa6fdedd0610ea34f15acb6ee1833e5a
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "68075730"
---
# <a name="spregistercustomresolver-transact-sql"></a>sp_registercustomresolver (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  登錄在合併式複寫同步處理期間所能叫用的商務邏輯處理常式或 COM 型自訂解析程式。 這個預存程序執行於散發者端。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
sp_registercustomresolver [ @article_resolver = ] 'article_resolver'   
    [ , [ @resolver_clsid = ] 'resolver_clsid' ]  
    [ , [ @is_dotnet_assembly = ] 'is_dotnet_assembly' ]  
    [ , [ @dotnet_assembly_name = ] 'dotnet_assembly_name' ]  
    [ , [ @dotnet_class_name = ] 'dotnet_class_name' ]  
```  
  
## <a name="arguments"></a>引數  
`[ @article_resolver = ] 'article_resolver'` 指定要登錄的自訂商務邏輯的易記名稱。 *article_resolver*已**nvarchar(255)** ，沒有預設值。  
  
`[ @resolver_clsid = ] 'resolver_clsid'` 指定所登錄的 COM 物件的 CLSID 值。 自訂商務邏輯*resolver_clsid*是**nvarchar(50)** ，預設值是 NULL。 當登錄商務邏輯處理常式組件時，這個參數必須設為有效的 CLSID 或設為 NULL。  
  
`[ @is_dotnet_assembly = ] 'is_dotnet_assembly'` 指定要登錄的自訂商務邏輯的類型。 *is_dotnet_assembly*已**nvarchar(50)** ，預設值是 FALSE。 **true**表示要登錄的自訂商務邏輯是商務邏輯處理常式組件。**false**表示它是 COM 元件。  
  
`[ @dotnet_assembly_name = ] 'dotnet_assembly_name'` 是實作商務邏輯處理常式的組件名稱。 *dotnet_assembly_name*已**nvarchar(255)** ，預設值是 NULL。 如果組件未部署在合併代理程式可執行檔的相同目錄、同步啟動合併代理程式之應用程式的相同目錄，或全域組件快取 (GAC) 中，您就必須指定組件的完整路徑。  
  
`[ @dotnet_class_name = ] 'dotnet_class_name'` 覆寫的類別名稱<xref:Microsoft.SqlServer.Replication.BusinessLogicSupport.BusinessLogicModule>實作商務邏輯處理常式。 應在表單中指定的名稱**Namespace.Classname**。 *dotnet_class_name*已**nvarchar(255)** ，預設值是 NULL。  
  
## <a name="return-code-values"></a>傳回碼值  
 **0** （成功） 或**1** （失敗）  
  
## <a name="remarks"></a>備註  
 **sp_registercustomresolver**用於合併式複寫中。  
  
## <a name="permissions"></a>Permissions  
 只有成員**sysadmin**固定的伺服器角色或**db_owner**固定的資料庫角色可以執行**sp_registercustomresolver**。  
  
## <a name="see-also"></a>另請參閱  
 [為合併發行項實作商務邏輯處理常式](../../relational-databases/replication/implement-a-business-logic-handler-for-a-merge-article.md)   
 [針對合併發行項實作自訂衝突解析程式](../../relational-databases/replication/implement-a-custom-conflict-resolver-for-a-merge-article.md)   
 [sp_lookupcustomresolver &#40;-SQL&AMP;#41;&#41;](../../relational-databases/system-stored-procedures/sp-lookupcustomresolver-transact-sql.md)   
 [sp_unregistercustomresolver &#40;-SQL&AMP;#41;&#41;](../../relational-databases/system-stored-procedures/sp-unregistercustomresolver-transact-sql.md)   
 [系統預存程序 &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
