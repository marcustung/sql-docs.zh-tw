---
title: sys.dm_pdw_dms_cores (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: b3f09b15-0863-4418-9347-a4f5fd2ab7c7
author: ronortloff
ms.author: rortloff
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 76a154639a71b22bfe3f119233f3abbcd329f7c3
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "67899531"
---
# <a name="sysdmpdwdmscores-transact-sql"></a>sys.dm_pdw_dms_cores (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  保留所有設備的計算節點上執行的 DMS 服務的相關資訊。 它會列出每個服務執行個體，也就是目前的每個節點的一個資料列的一個資料列。  
  
|資料行名稱|資料類型|描述|範圍|  
|-----------------|---------------|-----------------|-----------|  
|dms_core_id|**int**|與此 DMS 核心相關聯的唯一數值識別碼。<br /><br /> 此檢視的索引鍵。|設定為 pdw_node_id 的節點上執行此 DMS 核心。|  
|pdw_node_id|**int**|此 DMS 服務執行所在節點的識別碼。|請參閱中的 node_id [sys.dm_pdw_nodes &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-nodes-transact-sql.md)。|  
|status|**nvarchar(32)**|DMS 服務的目前狀態。|[!INCLUDE[ssInfoNA](../../includes/ssinfona-md.md)]|  
  
 這份檢視所保留的最大資料列的相關資訊，請參閱中的 [中繼資料] 區段[容量限制](/azure/sql-data-warehouse/sql-data-warehouse-service-capacity-limits#metadata)主題。  
  
## <a name="see-also"></a>另請參閱  
 [SQL 資料倉儲和平行處理資料倉儲動態管理檢視&#40;Transact SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
