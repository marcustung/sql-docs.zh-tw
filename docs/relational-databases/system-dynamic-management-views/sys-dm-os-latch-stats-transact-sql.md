---
title: sys.dm_os_latch_stats & Amp;#40;transact-SQL&AMP;#41; |Microsoft Docs
ms.custom: ''
ms.date: 08/18/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_os_latch_stats_TSQL
- dm_os_latch_stats_TSQL
- dm_os_latch_stats
- sys.dm_os_latch_stats
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_os_latch_stats dynamic management view
ms.assetid: 2085d9fc-828c-453e-82ec-b54ed8347ae5
author: stevestein
ms.author: sstein
ms.openlocfilehash: 853fa815c431c720ed76f1cef693eb5ac5bf1f8c
ms.sourcegitcommit: e7d921828e9eeac78e7ab96eb90996990c2405e9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/16/2019
ms.locfileid: "68265816"
---
# <a name="sysdmoslatchstats-transact-sql"></a>sys.dm_os_latch_stats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  傳回所有以類別組織之閂鎖等候的相關資訊。  
  
> [!NOTE]  
>  若要呼叫這個屬性從[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]或是[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]，使用名稱**sys.dm_pdw_nodes_os_latch_stats**。  
  
|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|latch_class|**nvarchar(120)**|閂鎖類別的名稱。|  
|waiting_requests_count|**bigint**|這個類別中的閂鎖等候數。 這個計數器是從開始閂鎖等候時逐量遞增計算。|  
|wait_time_ms|**bigint**|這個類別的總閂鎖等候時間 (以毫秒為單位)。<br /><br /> **注意：** 每隔五分鐘期間閂鎖等候及閂鎖等候結束時，會更新此資料行。|  
|max_wait_time_ms|**bigint**|這是記憶體物件可以等候這個閂鎖的最長時間。 如果這個值超乎尋常地高，可能是發生內部死結。|  
|pdw_node_id|**int**|**適用於**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]， [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> 這個分佈是在節點的識別碼。|  
  
## <a name="permissions"></a>Permissions  

在  [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]，需要`VIEW SERVER STATE`權限。   
在  [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)] Premium 層需要`VIEW DATABASE STATE`資料庫的權限。 上[!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]標準和基本層，則需要**伺服器系統管理員**該**Azure Active Directory 管理員**帳戶。   
  
## <a name="remarks"></a>備註  
 sys.dm_os_latch_stats 可以檢查不同閂鎖類別的相對等候時間和等候次數，來識別閂鎖競爭的來源。 某些情況下，您或許可以解決或減少閂鎖競爭的狀況。 不過有些時候您可能還是必須連絡 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 客戶支援服務部門。  
  
 您可以利用 `DBCC SQLPERF` 重設 sys.dm_os_latch_stats 的內容，如下所示：  
  
```  
DBCC SQLPERF ('sys.dm_os_latch_stats', CLEAR);  
GO  
```  
  
 此舉會將所有的計數器重設為 0。  
  
> [!NOTE]  
>  如果重新啟動 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]，將無法保存這些統計資料。 所有的資料都是從上次重設統計資料之後，或是從 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 啟動之後開始累加計算。  
  
## <a name="latches"></a>閂鎖  
 閂鎖是各種 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 元件所用的一種輕量型同步處理物件。 閂鎖主要是用來同步處理資料庫頁面。 每一個閂鎖都與一個配置單位有關。  
  
 如果無法立即授與閂鎖要求，就會發生閂鎖等候，因為閂鎖是由另一個處於衝突模式的執行緒所持有。 與鎖定不同的是，閂鎖會在作業之後立即釋出，即使是進行寫入作業也一樣。  
  
 閂鎖是根據元件和使用方式，分成幾個類別。 零個或零個以上特殊類別的閂鎖，可以存在於 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體的任何一個時間點。  
  
> [!NOTE]  
>  sys.dm_os_latch_stats 不會追蹤立即授與或是尚未等候就失敗的閂鎖要求。  
  
 下表含有各種閂鎖類別的簡單描述。  
  
|閂鎖類別|描述|  
|-----------------|-----------------|  
|ALLOC_CREATE_RINGBUF|由 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 在內部使用，將建立配置環緩衝區的同步處理作業初始化。|  
|ALLOC_CREATE_FREESPACE_CACHE|用來將堆積內部可用空間快取的同步處理作業初始化。|  
|ALLOC_CACHE_MANAGER|用來同步處理內部一致性測試。|  
|ALLOC_FREESPACE_CACHE|利用堆積和二進位大型物件 (BLOB) 的可用空間，同步處理資料頁面快取的存取作業。 如果有多個連接同時將資料列插入堆積或 BLOB 中，可能就會發生這個類別的閂鎖競爭情形。 您可以對物件進行資料分割來減少競爭。 每一個資料分割都有它自己的閂鎖。 資料分割會將插入數分散到多個閂鎖上。|  
|ALLOC_EXTENT_CACHE|用來同步處理存取含有未配置資料頁的範圍快取。 如果有多個連接同時配置同一個配置單位的資料頁，就會發生這個類別的閂鎖競爭。 您可以對這個配置單位所屬的物件進行資料分割，來減少競爭。|  
|ACCESS_METHODS_DATASET_PARENT|在平行作業期間，用來同步處理子資料集對父資料集的存取作業。|  
|ACCESS_METHODS_HOBT_FACTORY|用來同步處理內部雜湊資料表的存取作業。|  
|ACCESS_METHODS_HOBT|用來同步處理 HoBt 記憶體中表示法的存取作業。|  
|ACCESS_METHODS_HOBT_COUNT|用來同步處理 HoBt 資料頁和資料列計數器的存取作業。|  
|ACCESS_METHODS_HOBT_VIRTUAL_ROOT|用來同步處理內部 B 型樹狀目錄所擷取之根頁面的存取作業。|  
|ACCESS_METHODS_CACHE_ONLY_HOBT_ALLOC|用來同步處理工作資料表的存取作業。|  
|ACCESS_METHODS_BULK_ALLOC|用來同步處理大量配置器中的存取作業。|  
|ACCESS_METHODS_SCAN_RANGE_GENERATOR|在平行掃描期間，用來同步處理對範圍產生器的存取作業。|  
|ACCESS_METHODS_KEY_RANGE_GENERATOR|在關鍵範圍平行掃描期間，用來同步處理對讀取前作業的存取作業。|  
|APPEND_ONLY_STORAGE_INSERT_POINT|用來同步處理快速附加專用儲存體單位中的插入作業。|  
|APPEND_ONLY_STORAGE_FIRST_ALLOC|用來同步處理附加專用儲存體單位的第一個配置作業。|  
|APPEND_ONLY_STORAGE_UNIT_MANAGER|用來同步處理快速附加專用儲存體單位管理員內的內部資料結構存取作業。|  
|APPEND_ONLY_STORAGE_MANAGER|用來同步處理快速附加專用儲存體單位管理員中的壓縮作業。|  
|BACKUP_RESULT_SET|用來同步處理平行備份結果集。|  
|BACKUP_TAPE_POOL|用來同步處理備份磁帶集區。|  
|BACKUP_LOG_REDO|用來同步處理備份記錄重做作業。|  
|BACKUP_INSTANCE_ID|用來同步處理備份效能監視器計數器之執行個體識別碼的產生作業。|  
|BACKUP_MANAGER|用來同步處理內部備份管理員。|  
|BACKUP_MANAGER_DIFFERENTIAL|用來同步處理差異備份作業與 DBCC。|  
|BACKUP_OPERATION|用來同步處理備份作業 (例如資料庫、記錄或檔案備份) 內的內部資料結構。|  
|BACKUP_FILE_HANDLE|在還原作業期間，用來同步處理檔案開啟作業。|  
|BUFFER|用來同步處理對資料庫頁面的短期存取作業。 在讀取或修改任何資料庫頁面之前，必須具備緩衝區閂鎖。 緩衝區閂鎖競爭會指出幾個問題，包括頁面使用頻繁和 I/O 速度緩慢。<br /><br /> 這個閂鎖類別涵蓋頁面閂鎖的所有可能用途。 sys.dm_os_wait_stats 讓頁面閂鎖等候 I/O 作業和讀所造成，頁面上的寫入作業之間的差異。|  
|BUFFER_POOL_GROW|在緩衝集區成長作業期間，用來同步處理內部緩衝區管理員。|  
|DATABASE_CHECKPOINT|用來序列化資料庫內的檢查點。|  
|CLR_PROCEDURE_HASHTABLE|僅供內部使用。|  
|CLR_UDX_STORE|僅供內部使用。|  
|CLR_DATAT_ACCESS|僅供內部使用。|  
|CLR_XVAR_PROXY_LIST|僅供內部使用。|  
|DBCC_CHECK_AGGREGATE|僅供內部使用。|  
|DBCC_CHECK_RESULTSET|僅供內部使用。|  
|DBCC_CHECK_TABLE|僅供內部使用。|  
|DBCC_CHECK_TABLE_INIT|僅供內部使用。|  
|DBCC_CHECK_TRACE_LIST|僅供內部使用。|  
|DBCC_FILE_CHECK_OBJECT|僅供內部使用。|  
|DBCC_PERF|用來同步處理內部效能監視器計數器。|  
|DBCC_PFS_STATUS|僅供內部使用。|  
|DBCC_OBJECT_METADATA|僅供內部使用。|  
|DBCC_HASH_DLL|僅供內部使用。|  
|EVENTING_CACHE|僅供內部使用。|  
|FCB|用來同步處理檔案控制區塊的存取作業。|  
|FCB_REPLICA|僅供內部使用。|  
|FGCB_ALLOC|用來同步處理對檔案群組中循環配置資訊的存取作業。|  
|FGCB_ADD_REMOVE|使用此選項，以同步處理新增的檔案群組的存取、 卸除、 成長，並壓縮檔案作業。|  
|FILEGROUP_MANAGER|僅供內部使用。|  
|FILE_MANAGER|僅供內部使用。|  
|FILESTREAM_FCB|僅供內部使用。|  
|FILESTREAM_FILE_MANAGER|僅供內部使用。|  
|FILESTREAM_GHOST_FILES|僅供內部使用。|  
|FILESTREAM_DFS_ROOT|僅供內部使用。|  
|LOG_MANAGER|僅供內部使用。|  
|FULLTEXT_DOCUMENT_ID|僅供內部使用。|  
|FULLTEXT_DOCUMENT_ID_TRANSACTION|僅供內部使用。|  
|FULLTEXT_DOCUMENT_ID_NOTIFY|僅供內部使用。|  
|FULLTEXT_LOGS|僅供內部使用。|  
|FULLTEXT_CRAWL_LOG|僅供內部使用。|  
|FULLTEXT_ADMIN|僅供內部使用。|  
|FULLTEXT_AMDIN_COMMAND_CACHE|僅供內部使用。|  
|FULLTEXT_LANGUAGE_TABLE|僅供內部使用。|  
|FULLTEXT_CRAWL_DM_LIST|僅供內部使用。|  
|FULLTEXT_CRAWL_CATALOG|僅供內部使用。|  
|FULLTEXT_FILE_MANAGER|僅供內部使用。|  
|DATABASE_MIRRORING_REDO|僅供內部使用。|  
|DATABASE_MIRRORING_SERVER|僅供內部使用。|  
|DATABASE_MIRRORING_CONNECTION|僅供內部使用。|  
|DATABASE_MIRRORING_STREAM|僅供內部使用。|  
|QUERY_OPTIMIZER_VD_MANAGER|僅供內部使用。|  
|QUERY_OPTIMIZER_ID_MANAGER|僅供內部使用。|  
|QUERY_OPTIMIZER_VIEW_REP|僅供內部使用。|  
|RECOVERY_BAD_PAGE_TABLE|僅供內部使用。|  
|RECOVERY_MANAGER|僅供內部使用。|  
|SECURITY_OPERATION_RULE_TABLE|僅供內部使用。|  
|SECURITY_OBJPERM_CACHE|僅供內部使用。|  
|SECURITY_CRYPTO|僅供內部使用。|  
|SECURITY_KEY_RING|僅供內部使用。|  
|SECURITY_KEY_LIST|僅供內部使用。|  
|SERVICE_BROKER_CONNECTION_RECEIVE|僅供內部使用。|  
|SERVICE_BROKER_TRANSMISSION|僅供內部使用。|  
|SERVICE_BROKER_TRANSMISSION_UPDATE|僅供內部使用。|  
|SERVICE_BROKER_TRANSMISSION_STATE|僅供內部使用。|  
|SERVICE_BROKER_TRANSMISSION_ERRORS|僅供內部使用。|  
|SSBXmitWork|僅供內部使用。|  
|SERVICE_BROKER_MESSAGE_TRANSMISSION|僅供內部使用。|  
|SERVICE_BROKER_MAP_MANAGER|僅供內部使用。|  
|SERVICE_BROKER_HOST_NAME|僅供內部使用。|  
|SERVICE_BROKER_READ_CACHE|僅供內部使用。|  
|SERVICE_BROKER_WAITFOR_MANAGER| 用來同步等候者佇列的執行個體層級對應。 每個資料庫的識別碼、 資料庫版本和佇列識別碼的 tuple，有一個佇列。 許多連線時，可能會發生這個類別的閂鎖爭用：在 WAITFOR(RECEIVE) 等候狀態;呼叫 WAITFOR(RECEIVE);超過的 WAITFOR 逾時;接收訊息;認可或回復交易，其中包含 WAITFOR(RECEIVE);您可以在 WAITFOR(RECEIVE) 等候狀態中的執行緒數目，從而減少爭用情況。 |  
|SERVICE_BROKER_WAITFOR_TRANSACTION_DATA|僅供內部使用。|  
|SERVICE_BROKER_TRANSMISSION_TRANSACTION_DATA|僅供內部使用。|  
|SERVICE_BROKER_TRANSPORT|僅供內部使用。|  
|SERVICE_BROKER_MIRROR_ROUTE|僅供內部使用。|  
|TRACE_ID|僅供內部使用。|  
|TRACE_AUDIT_ID|僅供內部使用。|  
|追蹤|僅供內部使用。|  
|TRACE_CONTROLLER|僅供內部使用。|  
|TRACE_EVENT_QUEUE|僅供內部使用。|  
|TRANSACTION_DISTRIBUTED_MARK|僅供內部使用。|  
|TRANSACTION_OUTCOME|僅供內部使用。|  
|NESTING_TRANSACTION_READONLY|僅供內部使用。|  
|NESTING_TRANSACTION_FULL|僅供內部使用。|  
|MSQL_TRANSACTION_MANAGER|僅供內部使用。|  
|DATABASE_AUTONAME_MANAGER|僅供內部使用。|  
|UTILITY_DYNAMIC_VECTOR|僅供內部使用。|  
|UTILITY_SPARSE_BITMAP|僅供內部使用。|  
|UTILITY_DATABASE_DROP|僅供內部使用。|  
|UTILITY_DYNAMIC_MANAGER_VIEW|僅供內部使用。|  
|UTILITY_DEBUG_FILESTREAM|僅供內部使用。|  
|UTILITY_LOCK_INFORMATION|僅供內部使用。|  
|VERSIONING_TRANSACTION|僅供內部使用。|  
|VERSIONING_TRANSACTION_LIST|僅供內部使用。|  
|VERSIONING_TRANSACTION_CHAIN|僅供內部使用。|  
|VERSIONING_STATE|僅供內部使用。|  
|VERSIONING_STATE_CHANGE|僅供內部使用。|  
|KTM_VIRTUAL_CLOCK|僅供內部使用。|  
  
## <a name="see-also"></a>另請參閱  
 
 [DBCC SQLPERF &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-sqlperf-transact-sql.md)   
 
 [SQL Server 作業系統相關的動態管理檢視&#40;Transact SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)  
  
  


