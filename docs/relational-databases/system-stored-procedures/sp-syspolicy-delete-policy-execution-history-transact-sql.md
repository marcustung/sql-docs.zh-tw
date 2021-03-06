---
title: sp_syspolicy_delete_policy_execution_history (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_syspolicy_delete_policy_execution_history
- sp_syspolicy_delete_policy_execution_history_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_syspolicy_delete_policy_execution_history
ms.assetid: fe651af9-267e-45ec-b4e7-4b0698fb1be3
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: f0cb7f631b75be4e8b2f4063b03aca1895ba6900
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "67997342"
---
# <a name="spsyspolicydeletepolicyexecutionhistory-transact-sql"></a>sp_syspolicy_delete_policy_execution_history (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  在以原則為基礎的管理中刪除原則的執行記錄。 您可以使用這個預存程序刪除特定原則或所有原則的執行記錄，並刪除特定日期之前的執行記錄。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
sp_syspolicy_delete_policy_execution_history [ @policy_id = ] policy_id ]  
    [ , [ @oldest_date = ] 'oldest_date' ]  
```  
  
## <a name="arguments"></a>引數  
`[ @policy_id = ] policy_id` 是您想要刪除執行記錄之原則的識別碼。 *policy_id&lt*已**int**，而且需要。 可以是 NULL。  
  
`[ @oldest_date = ] 'oldest_date'` 這是您要保留原則執行記錄最舊日期。 早於這個日期的執行記錄會遭到刪除。 *oldest_date*已**datetime**，而且需要。 可以是 NULL。  
  
## <a name="return-code-values"></a>傳回碼值  
 **0** （成功） 或**1** （失敗）  
  
## <a name="remarks"></a>備註  
 您必須在 msdb 系統資料庫的內容中執行 sp_syspolicy_delete_policy_execution_history。  
  
 若要取得值，如*policy_id&lt*，若要檢視執行歷程記錄日期，您可以使用下列查詢：  
  
```  
SELECT a.name AS N'policy_name', b.policy_id, b.start_date, b.end_date  
FROM msdb.dbo.syspolicy_policies AS a   
INNER JOIN msdb.dbo.syspolicy_policy_execution_history AS b  
ON a.policy_id = b.policy_id  
```  
  
 如果您針對一個或兩個值指定 NULL，將適用下列行為：  
  
-   若要刪除所有原則執行記錄，請指定兩個 NULL *policy_id&lt*至於*oldest_date*。  
  
-   若要刪除特定原則的所有原則執行記錄，指定的原則識別碼*policy_id&lt*，並指定 NULL 作為*oldest_date*。  
  
-   若要刪除特定日期之前的所有原則的原則執行記錄，請指定 NULL *policy_id&lt*，並指定的日期*oldest_date*。  
  
 若要封存原則執行記錄，您可以在 [物件總管] 中開啟「原則記錄」記錄檔，並將執行記錄匯出到某個檔案。 若要存取的原則記錄檔，依序展開**管理**，以滑鼠右鍵按一下**原則管理**，然後按一下**檢視歷程記錄**。  
  
## <a name="permissions"></a>Permissions  
 需要 PolicyAdministratorRole 固定資料庫角色中的成員資格。  
  
> [!IMPORTANT]  
>  可能會提高認證：PolicyAdministratorRole 角色中的使用者可以建立伺服器觸發程序以及排程可能會影響作業的執行個體的原則執行[!INCLUDE[ssDE](../../includes/ssde-md.md)]。 例如，PolicyAdministratorRole 角色中的使用者可以建立防止在 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 中建立大部分物件的原則。 由於可能會提高認證，因此 PolicyAdministratorRole 角色應該只授與可控制 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 組態的受信任使用者。  
  
## <a name="examples"></a>範例  
 下列範例會針對識別碼為 7 的原則刪除特定日期之前的原則執行記錄。  
  
```  
EXEC msdb.dbo.sp_syspolicy_delete_policy_execution_history @policy_id = 7  
, @oldest_date = '2009-02-16 16:00:00.000';  
  
GO  
```  
  
## <a name="see-also"></a>另請參閱  
 [以原則為基礎的管理預存程序&#40;Transact SQL&#41;](../../relational-databases/system-stored-procedures/policy-based-management-stored-procedures-transact-sql.md)   
 [sp_syspolicy_set_config_history_retention &#40;-SQL&AMP;#41;&#41;](../../relational-databases/system-stored-procedures/sp-syspolicy-set-config-history-retention-transact-sql.md)   
 [sp_syspolicy_purge_history &#40;-SQL&AMP;#41;&#41;](../../relational-databases/system-stored-procedures/sp-syspolicy-purge-history-transact-sql.md)  
  
  
