---
title: MSsnapshotdeliveryprogress (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- MSsnapshotdeliveryprogress_TSQL
- MSsnapshotdeliveryprogress
dev_langs:
- TSQL
helpviewer_keywords:
- MSsnapshotdeliveryprogress system table
ms.assetid: 9164bfe2-6fc4-4b52-946a-09ea3cf67041
author: stevestein
ms.author: sstein
ms.openlocfilehash: 638bea3db68712300ad2284e50676bf1df67c9ae
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "68139805"
---
# <a name="mssnapshotdeliveryprogress-transact-sql"></a>MSsnapshotdeliveryprogress (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  **MSsnapshotdeliveryprogress**資料表用來追蹤已經順利傳遞給訂閱者在套用快照集時的檔案。 這項資料用來繼續傳遞檔案，萬一合併代理程式在工作階段無法傳遞所有的檔案，那麼下次再執行合併代理程式時，不會再重複傳遞相同的檔案。 這份資料表儲存在訂閱資料庫的訂閱者端。  
  
|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|**session_token**|**nvarchar(260)**|識別通往順利傳遞檔案之快照集資料夾的路徑。 使用參數化的篩選，字串之發行集**dynsnap**會附加至值。|  
|**progress_token_hash**|**int**|產生的雜湊值的值為基礎*progress_token*用來改善的查閱效率給定*progress_token*值。|  
|**progress_token**|**nvarchar(500)**|識別已經順利傳遞的檔案，該值是檔案名稱和路徑的組合。|  
|**progress_timestamp**|**datetime**|**Datetime**指出快照集檔案已成功傳遞的值。|  
  
## <a name="see-also"></a>另請參閱  
 [複寫資料表&#40;Transact SQL&#41;](../../relational-databases/system-tables/replication-tables-transact-sql.md)   
 [複寫檢視 &#40;Transact-SQL&#41;](../../relational-databases/system-views/replication-views-transact-sql.md)  
  
  
