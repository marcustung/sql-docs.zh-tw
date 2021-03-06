---
title: sys.resource_governor_resource_pools (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.resource_governor_resource_pools
- resource_governor_resource_pools
- sys.resource_governor_resource_pools_TSQL
- resource_governor_resource_pools_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.resource_governor_resource_pools catalog view
ms.assetid: 56793e9c-aa90-452e-88c6-d9b799239888
author: stevestein
ms.author: sstein
ms.openlocfilehash: 06ed4b4820ce7a6e6483df6efd1de2e8fbadf954
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "67904460"
---
# <a name="sysresourcegovernorresourcepools-transact-sql"></a>sys.resource_governor_resource_pools (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  傳回 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中儲存的資源集區組態。 檢視的每個資料列都會決定集區的組態。  
  
|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|pool_id|**int**|資源集區的唯一識別碼。 不可為 Null。|  
|name|**sysname**|資源集區的名稱。 不可為 Null。|  
|min_cpu_percent|**int**|當 CPU 出現瓶頸時，為資源集區中的所有要求保證的平均 CPU 頻寬。 不可為 Null。|  
|max_cpu_percent|**int**|當 CPU 出現瓶頸時，針對資源集區中的所有要求所允許的最大平均 CPU 頻寬。 不可為 Null。|  
|min_memory_percent|**int**|為資源集區中的所有要求保證的記憶體數量。 這不會與其他資源集區共用。 不可為 Null。|  
|max_memory_percent|**int**|在此資源集區中，可供要求所用的伺服器記憶體總量百分比。 不可為 Null。 有效的最大值取決於集區最小值。 例如，max_memory_percent 可以設定為 100，但有效的最大值比較低。|  
|cap_cpu_percent|**int**|**適用於**： [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 至 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]。<br /><br /> 資源集區中所有要求都將接收的 CPU 頻寬硬體上限。 將最大 CPU 頻寬限制為指定的層級。 允許的值範圍從 1 至 100。|  
|min_iops_per_volume|**int**|**適用於**： [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 至 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]。<br /><br /> 這個集區之每個磁碟區設定的每秒 I/O 作業數最小值 (IOPS)。 0 = 無保留項目。 不可為 null。|  
|max_iops_per_volume|**int**|**適用於**： [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 至 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]。<br /><br /> 這個集區之每個磁碟區設定的每秒 I/O 作業數最大值 (IOPS)。 0 = 無限制。 不可為 null。|  
  
## <a name="remarks"></a>備註  
 目錄檢視會顯示儲存的中繼資料。 若要查看記憶體中組態，請使用對應的動態管理檢視[sys.dm_resource_governor_resource_pools &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-resource-pools-transact-sql.md)。  
  
## <a name="permissions"></a>Permissions  
 需要 VIEW ANY DEFINITION 權限檢視內容；需要 CONTROL SERVER 權限變更內容。  
  
## <a name="see-also"></a>另請參閱  
 [Resource Governor 目錄檢視&#40;Transact SQL&#41;](../../relational-databases/system-catalog-views/resource-governor-catalog-views-transact-sql.md)   
 [sys.dm_resource_governor_resource_pools &#40;-SQL&AMP;#41;&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-resource-governor-resource-pools-transact-sql.md)   
 [資源管理員](../../relational-databases/resource-governor/resource-governor.md)   
 [sys.resource_governor_external_resource_pools &#40;-SQL&AMP;#41;&#41;](../../relational-databases/system-catalog-views/sys-resource-governor-external-resource-pools-transact-sql.md)  
  
  
