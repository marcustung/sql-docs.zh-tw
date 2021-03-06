---
title: sp_update_operator (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_update_operator_TSQL
- sp_update_operator
dev_langs:
- TSQL
helpviewer_keywords:
- sp_update_operator
ms.assetid: 231750a6-4828-4d03-afe6-b91d38c42ed3
author: stevestein
ms.author: sstein
ms.openlocfilehash: 2a766ad74f42336612859c63cf42df654846ff96
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "68084845"
---
# <a name="spupdateoperator-transact-sql"></a>sp_update_operator (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  更新操作員 (通知收件者) 的相關資訊，以搭配警示和作業使用。  
  
   ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
sp_update_operator   
     [ @name =] 'name'   
     [ , [ @new_name = ] 'new_name' ]   
     [ , [ @enabled = ] enabled]   
     [ , [ @email_address = ] 'email_address' ]  
     [ , [ @pager_address = ] 'pager_number']   
     [ , [ @weekday_pager_start_time = ] weekday_pager_start_time ]  
     [ , [ @weekday_pager_end_time = ] weekday_pager_end_time ]   
     [ , [ @saturday_pager_start_time = ] saturday_pager_start_time ]  
     [ , [ @saturday_pager_end_time = ] saturday_pager_end_time ]   
     [ , [ @sunday_pager_start_time = ] sunday_pager_start_time ]  
     [ , [ @sunday_pager_end_time = ] sunday_pager_end_time ]   
     [ , [ @pager_days = ] pager_days ]   
     [ , [ @netsend_address = ] 'netsend_address' ]   
     [ , [ @category_name = ] 'category' ]  
```  
  
## <a name="arguments"></a>引數  
 [ @name=] '*名稱*'  
 要修改的操作員名稱。 *名稱*已**sysname**，沒有預設值。  
  
 [ @new_name=] '*new_name*'  
 操作員的新名稱。 這個名稱必須是唯一的。 *new_name*已**sysname**，預設值是 NULL。  
  
 [ @enabled=]*啟用*  
 數字，指出操作員目前狀態 (**1**目前已啟用，如果**0**如果不是)。 *已啟用*已**tinyint**，預設值是 NULL。 如果未啟用，操作員不會收到警示通知。  
  
 [ @email_address=] '*email_address*'  
 操作員的電子郵件地址。 這個字串會直接傳遞至電子郵件系統。 *email_address*已**nvarchar(100)** ，預設值是 NULL。  
  
 [ @pager_address=] '*pager_number*'  
 操作員的呼叫器號碼。 這個字串會直接傳遞至電子郵件系統。 *pager_number*已**nvarchar(100)** ，預設值是 NULL。  
  
 [ @weekday_pager_start_time=] *weekday_pager_start_time*  
 指定從星期一到星期五，在什麼時間之後，可以將呼叫器通知傳給這位操作員。 *weekday_pager_start_time*已**int**，預設值是 NULL，而且必須使用 HHMMSS 格式輸入 24 小時制。  
  
 [ @weekday_pager_end_time=] *weekday_pager_end_time*  
 指定從星期一到星期五，在什麼時間之後，不能將呼叫器通知傳給指定的操作員。 *weekday_pager_end_time*已**int**，預設值是 NULL，而且必須使用 HHMMSS 格式輸入 24 小時制。  
  
 [ @saturday_pager_start_time=] *saturday_pager_start_time*  
 指定在星期六的什麼時間之後，可以將呼叫器通知傳給指定的操作員。 *saturday_pager_start_time*已**int**，預設值是 NULL，而且必須使用 HHMMSS 格式輸入 24 小時制。  
  
 [ @saturday_pager_end_time=] *saturday_pager_end_time*  
 指定在星期六的什麼時間之後，不能將呼叫器通知傳給指定的操作員。 *saturday_pager_end_time*已**int**，預設值是 NULL，而且必須使用 HHMMSS 格式輸入 24 小時制。  
  
 [ @sunday_pager_start_time=] *sunday_pager_start_time*  
 指定在星期日的什麼時間之後，可以將呼叫器通知傳給指定的操作員。 *sunday_pager_start_time*已**int**，預設值是 NULL，而且必須使用 HHMMSS 格式輸入 24 小時制。  
  
 [ @sunday_pager_end_time=] *sunday_pager_end_time*  
 指定在星期日的什麼時間之後，不能將呼叫器通知傳給指定的操作員。 *sunday_pager_end_time*已**int**，預設值是 NULL，而且必須使用 HHMMSS 格式輸入 24 小時制。  
  
 [ @pager_days=] *pager_days*  
 指定操作員能夠接收呼叫的日子 (遵照指定的開始/結束時間)。 *pager_days*已**tinyint**，預設值是 NULL，而且必須是介於**0**透過**127**。 *pager_days*的計算方式是加入必要天數的個別值。 例如，從星期一到星期五是**2**+**4**+**8**+**16** + **32** = **64**。  
  
|值|描述|  
|-----------|-----------------|  
|**1**|星期日|  
|**2**|星期一|  
|**4**|星期二|  
|**8**|星期三|  
|**16**|星期四|  
|**32**|星期五|  
|**64**|星期六|  
  
 [ @netsend_address=] '*netsend_address*'  
 要傳送網路訊息的目標操作員網路位址。 *netsend_address&lt*已**nvarchar(100)** ，預設值是 NULL。  
  
 [ @category_name=] '*分類*'  
 這個警示的類別目錄名稱。 *類別目錄*已**sysname**，預設值是 NULL。  
  
## <a name="return-code-values"></a>傳回碼值  
 **0** （成功） 或**1** （失敗）  
  
## <a name="remarks"></a>備註  
 sp_update_operator 必須從 msdb 資料庫中執行。  
  
## <a name="permissions"></a>Permissions  
 這個程序的執行權限預設會授與系統管理員 (sysadmin) 固定伺服器角色的成員。  
  
## <a name="examples"></a>範例  
 下列範例會將操作員狀態更新為已啟用，並設定能夠呼叫操作員的日子 (星期一至星期五，上午 8 點至下午 5 點)。  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_update_operator   
    @name = N'François Ajenstat',  
    @enabled = 1,  
    @email_address = N'françoisa',  
    @pager_address = N'5551290AW@pager.Adventure-Works.com',  
    @weekday_pager_start_time = 080000,  
    @weekday_pager_end_time = 170000,  
    @pager_days = 64 ;  
GO  
```  
  
## <a name="see-also"></a>另請參閱  
 [sp_add_operator &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-operator-transact-sql.md)   
 [sp_delete_operator &#40;-SQL&AMP;#41;&#41;](../../relational-databases/system-stored-procedures/sp-delete-operator-transact-sql.md)   
 [sp_help_operator &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-operator-transact-sql.md)   
 [系統預存程序 &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
