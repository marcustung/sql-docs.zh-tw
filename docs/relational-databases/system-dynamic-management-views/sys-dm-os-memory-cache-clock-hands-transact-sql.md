---
title: sys.dm_os_memory_cache_clock_hands (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 12/21/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_os_memory_cache_clock_hands_TSQL
- dm_os_memory_cache_clock_hands
- dm_os_memory_cache_clock_hands_TSQL
- sys.dm_os_memory_cache_clock_hands
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_os_memory_cache_clock_hands dynamic management view
ms.assetid: 0660eddc-691c-425f-9d43-71151d644de7
author: stevestein
ms.author: sstein
ms.openlocfilehash: 783f985810b44673c6a6566caa6e89ff655670e0
ms.sourcegitcommit: e7d921828e9eeac78e7ab96eb90996990c2405e9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/16/2019
ms.locfileid: "68265795"
---
# <a name="sysdmosmemorycacheclockhands-transact-sql"></a>sys.dm_os_memory_cache_clock_hands (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  傳回特定快取時鐘的每一個指針的狀態。  
  
> [!NOTE]  
>  若要呼叫這個屬性從[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]或是[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]，使用名稱**sys.dm_pdw_nodes_os_memory_cache_clock_hands**。  
  
|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|**cache_address**|**varbinary(8)**|與時鐘相關聯的快取位址。 不可為 Null。|  
|**name**|**nvarchar(256)**|快取的名稱。 不可為 Null。|  
|**type**|**nvarchar(60)**|快取存放區的類型。 可以有相同類型的幾個快取。 不可為 Null。|  
|**clock_hand**|**nvarchar(60)**|指針的類型。 這是下列項目之一：<br /><br /> External<br /><br /> 內部<br /><br /> 不可為 Null。|  
|**clock_status**|**nvarchar(60)**|時鐘的狀態。 這是下列項目之一：<br /><br /> 已暫停<br /><br /> 執行中<br /><br /> 不可為 Null。|  
|**rounds_count**|**bigint**|透過快取移除項目的清除數目。 不可為 Null。|  
|**removed_all_rounds_count**|**bigint**|所有清除所移除的項目數。 不可為 Null。|  
|**updated_last_round_count**|**bigint**|上次清除期間更新的項目數。 不可為 Null。|  
|**removed_last_round_count**|**bigint**|上次清除期間移除的項目數。 不可為 Null。|  
|**last_tick_time**|**bigint**|時鐘指針移動的最後時間 (以毫秒為單位)。 不可為 Null。|  
|**round_start_time**|**bigint**|上次清除的時間 (以毫秒為單位)。 不可為 Null。|  
|**last_round_start_time**|**bigint**|時鐘完成上一圈所花費的總時間 (以毫秒為單位)。 不可為 Null。|  
|**pdw_node_id**|**int**|**適用於**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]， [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> 這個分佈是在節點的識別碼。|  
  
## <a name="permissions"></a>Permissions  

在  [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]，需要`VIEW SERVER STATE`權限。   
在  [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] Premium 層需要`VIEW DATABASE STATE`資料庫的權限。 上[!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]標準和基本層，則需要**伺服器系統管理員**該**Azure Active Directory 管理員**帳戶。   
  
## <a name="remarks"></a>備註  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 會以稱為記憶體快取的結構，將資訊儲存在記憶體中。 快取中的資訊可以是資料、索引項目、編譯程序計畫，以及各種其他類型的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資訊。 為了避免重建資訊，記憶體快取會盡可能長期保存，並且通常是因資訊太舊而無法使用、或是必須挪出記憶體空間供新資訊使用等情形，才從快取中移除。 移除舊資訊的處理序稱為記憶體清除。 記憶體清除屬於常執行的活動，但是非持續性活動。 時鐘演算法會控制記憶體快取的清除。 每個時鐘都會控制數個記憶體清除，即所謂的指針。 記憶體快取時鐘指針，就是指其中一個記憶體清除指針的目前位置。  

## <a name="see-also"></a>另請參閱  
 [SQL Server 作業系統相關的動態管理檢視&#40;Transact SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)    
 [sys.dm_os_memory_cache_counters &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-memory-cache-counters-transact-sql.md)
  

