---
title: sys.fn_servershareddrives (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- fn_servershareddrives
- fn_servershareddrives_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- fn_servershareddrives function
- shared drives [SQL Server]
- names [SQL Server], shared drives
- sys.fn_serversharedrives function
ms.assetid: ff01eff7-8cb6-460c-ba7a-6a52bda6d471
author: rothja
ms.author: jroth
ms.openlocfilehash: 71858ee3c57af8d94bdf4ef4addad720655942f4
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "68122547"
---
# <a name="sysfnservershareddrives-transact-sql"></a>sys.fn_servershareddrives (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  傳回叢集伺服器所用的共用磁碟機的名稱。  
  
> [!IMPORTANT]  
>  保留這個 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 系統函數的目的在於提供回溯相容性。 我們建議您改用[sys.dm_io_cluster_valid_path_names &#40;TRANSACT-SQL&#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-io-cluster-valid-path-names-transact-sql.md)改為。  
  
 ![主題連結圖示](../../database-engine/configure-windows/media/topic-link.gif "主題連結圖示") [Transact-SQL 語法慣例](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>語法  
  
```  
  
fn_servershareddrives()  
```  
  
## <a name="tables-returned"></a>傳回的資料表  
 如果目前的伺服器是叢集的伺服器， **fn_servershareddrives**傳回共用的磁碟機的磁碟機名稱。  
  
 如果目前的伺服器執行個體不是叢集的伺服器， **fn_servershareddrives**傳回空的資料列集。  
  
## <a name="remarks"></a>備註  
 `fn_servershareddrives` 會傳回這個叢集伺服器所用的共用磁碟機清單。 這些共用的磁碟機屬於相同叢集群組[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]資源。 另外，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資源會相依於這些磁碟機。  
  
 在識別使用者是否能夠使用的磁碟機時，這項功能很有用。  
  
## <a name="permissions"></a>Permissions  
 使用者必須具有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體的 VIEW SERVER STATE 權限。  
  
## <a name="examples"></a>範例  
 下列範例會利用 `fn_servershareddrives` 來查詢叢集伺服器執行個體：  
  
```  
SELECT * FROM fn_servershareddrives();  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 DriveName  
  
 -------\-  
  
 m  
  
 n  
  
## <a name="see-also"></a>另請參閱  
 [sys.dm_io_cluster_valid_path_names &#40;-SQL&AMP;#41;&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-io-cluster-valid-path-names-transact-sql.md)   
 [sys.dm_io_cluster_shared_drives &#40;-SQL&AMP;#41;&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-io-cluster-shared-drives-transact-sql.md)   
 [sys.fn_virtualservernodes &#40;-SQL&AMP;#41;&#41;](../../relational-databases/system-functions/sys-fn-virtualservernodes-transact-sql.md)  
  
  
