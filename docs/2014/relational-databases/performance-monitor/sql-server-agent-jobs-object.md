---
title: SQL Server Agent、Jobs 物件 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SQLAgent:Jobs
- Jobs object
ms.assetid: 225b5e2d-4a78-4178-b2b6-b419df83c4aa
caps.latest.revision: 20
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 85cdedd2ffb9bebb4458ef325992e56e93345628
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2018
ms.locfileid: "37305518"
---
# <a name="sql-server-agent-jobs-object"></a>SQL Server 代理程式、作業物件
  SQL Server Agent 的「 **作業** 」效能物件包含報告有關 SQL Server Agent 作業資訊的效能計數器。 下表列出這個物件包含的計數器。  
  
 下表包含 **SQLAgent:Jobs** 計數器。  
  
|名稱|描述|  
|----------|-----------------|  
|**Active Jobs**|此計數器報告目前執行中的作業數目。|  
|**Failed jobs**|此計數器報告因失敗而結束的作業數目。|  
|**Job success rate**|此計數器報告已順利完成的已執行作業百分比。|  
|**Jobs activated/minute**|此計數器報告在上一分鐘內啟動的作業數目。|  
|**Queued jobs**|此計數器報告備妥而可供 SQL Server Agent 執行，但尚未開始執行的作業數目。|  
|**Successful jobs**|此計數器報告因成功完成而結束的作業數目。|  
  
 物件中的每個計數器均包含下列執行個體：  
  
|執行個體|描述|  
|--------------|-----------------|  
|**_Total**|所有作業的資訊。|  
|**警示**|由警示啟動之作業的資訊。|  
|**其他**|不是由警示或排程啟動之作業的資訊。 一般而言，這些作業是手動使用 **sp_start_job**來啟動。|  
|**排程**|由排程啟動之作業的資訊。|  
  
## <a name="see-also"></a>另請參閱  
 [實作作業](../../ssms/agent/implement-jobs.md)   
 [使用效能物件](../../ssms/agent/use-performance-objects.md)   
 [監視資源使用狀況 &#40;系統監視器&#41;](monitor-resource-usage-system-monitor.md)  
  
  