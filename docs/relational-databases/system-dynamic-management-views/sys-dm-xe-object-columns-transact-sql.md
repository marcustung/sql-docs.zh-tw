---
title: sys.dm_xe_object_columns (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_xe_object_columns
- sys.dm_xe_object_columns_TSQL
- dm_xe_object_columns_TSQL
- dm_xe_object_columns
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_xe_object_columns dynamic management view
- extended events [SQL Server], views
ms.assetid: d96a14f3-4284-45ff-b1fe-4858e540a013
author: stevestein
ms.author: sstein
ms.openlocfilehash: 8b44824310637b279388ea367cd4ab1d07401d1f
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "68090279"
---
# <a name="sysdmxeobjectcolumns-transact-sql"></a>sys.dm_xe_object_columns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  傳回所有物件的結構描述資訊。  
  
> [!NOTE]  
>  事件物件會公開唯讀和可讀寫資料的固定結構描述。  
  
|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|name|**nvarchar(256)**|資料行的名稱。 在物件內的唯一名稱。 不可為 Null。|  
|column_id|**int**|資料行的識別碼。 column_id 內是唯一的物件，當使用 column_type 時。 不可為 Null。|  
|object_name|**nvarchar(256)**|這個資料行所屬之物件的名稱。 沒有與 sys.dm_xe_objects.id 之間多對一關聯性。不可為 Null。|  
|object_package_guid|**uniqueidentifier**|包含物件之封裝的 GUID。 不可為 Null。|  
|type_name|**nvarchar(256)**|此資料行之類型的名稱。 不可為 Null。|  
|type_package_guid|**uniqueidentifier**|包含資料行資料類型之封裝的 GUID。 不可為 Null。|  
|column_type|**nvarchar(60)**|指示如何使用這個資料行。 不可為 Null。 column_type 可以是下列其中一項：<br /><br /> readonly。 此資料行包含無法變更的靜態值。<br /><br /> data。 此資料行包含物件所公開的執行階段資料。<br /><br /> customizable。 此資料行包含可以變更的值。<br /><br /> 注意:變更此值可以修改物件的行為。|  
|column_value|**nvarchar(256)**|會顯示與物件資料行相關聯的靜態值。 可為 Null。|  
|capabilities|**int**|描述資料行之功能的點陣圖。 可為 Null。|  
|capabilities_desc|**nvarchar(256)**|這個物件資料行之功能的描述。 這個值可以是下列其中一個值：<br /><br /> Mandatory。 將父物件繫結至事件工作階段時，必須設定此值。<br /><br /> 可為 Null。|  
|description|**nvarchar(3072)**|此物件資料行的描述。 可為 Null。|  
  
## <a name="permissions"></a>Permissions  
 需要伺服器的 VIEW SERVER STATE 權限。  
  
### <a name="relationship-cardinalities"></a>關聯性基數  
  
|來源|若要|關聯性|  
|----------|--------|------------------|  
|sys.dm_xe_object_columns.object_name、sys.dm_xe_object_columns.object_package_guid|sys.dm_xe_objects.name、<br /><br /> sys.dm_xe_objects.package_guid|多對一|  
|sys.dm_xe_object_columns.type_name<br /><br /> sys.dm_xe_object_columns.type_package_guid|sys.dm_xe_objects.name<br /><br /> sys.dm_xe_objects.package_guid|多對一|  
  
## <a name="see-also"></a>另請參閱  
 [動態管理檢視與函數 &#40;Transact-SQL&#41;](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)  
  
  

