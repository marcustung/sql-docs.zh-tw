---
title: sys.spatial_index_tessellations (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- spatial_index_tessellations
- sys.spatial_index_tessellations_TSQL
- spatial_index_tessellations_TSQL
- sys.spatial_index_tessellations
dev_langs:
- TSQL
helpviewer_keywords:
- sys.spatial_index_tessellations catalog view
ms.assetid: 8b17a9a4-b57f-4220-8138-fc73581b1670
author: stevestein
ms.author: sstein
ms.openlocfilehash: c4f2f4b8ea0184d063a6423f27fdf2cf9c450a05
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "68078653"
---
# <a name="sysspatialindextessellations-transact-sql"></a>sys.spatial_index_tessellations (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

 表示有關鑲嵌式配置和每一個空間索引之參數的資訊。  
  
> [!NOTE]  
>  如需鑲嵌的資訊，請參閱[空間索引概觀](../../relational-databases/spatial/spatial-indexes-overview.md)。  
  

|資料行名稱|資料類型|描述|  
|-----------------|---------------|-----------------|  
|object_id|**int**|索引定義所在的物件識別碼。 每個 （object_id、 index_id） 配對具有對應的項目[sys.spatial_indexes](../../relational-databases/system-catalog-views/sys-spatial-indexes-transact-sql.md)。|  
|index_id|**int**|索引資料行定義所在的空間索引識別碼。|  
|tessellation_scheme|**sysname**|鑲嵌式配置，其中的名稱：GEOMETRY_GRID、 GEOGRAPHY_GRID|  
|bounding_box_xmin|**float(53)**|其中一個週框方塊左下角的 X 座標：NULL = 不適用於給定的鑲嵌式配置 （例如 GEOGRAPHY_GRID) *n* = 如果 tessellation_scheme 為 GEOMETRY_GRID，為 x-min 座標值。                     **注意：** 週框方塊參數所定義的座標會解譯為每個物件根據其[空間參考識別碼 (SRID)](../../relational-databases/spatial/spatial-reference-identifiers-srids.md)。|  
|bounding_box_ymin|**float(53)**|週框方塊的其中一個的左下角的 Y 座標：NULL = 不適用於給定的鑲嵌式配置 （例如 GEOGRAPHY_GRID) *n* = 如果 tessellation_scheme 為 GEOMETRY_GRID，為 y-min 座標值|  
|bounding_box_xmax|**float(53)**|週框方塊的其中一個的右上角的 X 座標：NULL = 不適用於給定的鑲嵌式配置 （例如 GEOGRAPHY_GRID) *n* = 如果 tessellation_scheme 為 GEOMETRY_GRID，為 x-max 座標值|  
|bounding_box_ymax|**float(53)**|其中一個週框方塊右上角的 Y 座標：NULL = 不適用於給定的鑲嵌式配置 （例如 GEOGRAPHY_GRID) *n* = 如果 tessellation_scheme 為 GEOMETRY_GRID，為 y-max 座標值|  
|level_1_grid|**smallint**|上層方格的方格密度。 如果 tessellation_scheme 為 GEOMETRY_GRID 或 GEOGRAPHY_GRID，其中一個：        16 = 4 x 4 方格 (LOW) 64 = 8 x 8 方格 (MEDIUM) 256 = 16 x 16 方格 （高） 的 NULL = 不適用於給定的空間索引類型或鑲嵌式配置。  使用新的 SQL Server 11 鑲嵌時，則傳回 NULL。|  
|level_1_grid_desc|**nvarchar(60)**|其中一個最上層方格的方格密度：低中型高 NULL = 不適用於給定的空間索引類型或鑲嵌式配置。  使用新的 SQL Server 11 鑲嵌時，則傳回 NULL。|  
|level_2_grid|**smallint**|第二層方格的方格密度。 如果 tessellation_scheme 為 GEOMETRY_GRID 或 GEOGRAPHY_GRID，其中一個：16 = 4 x 4 方格 (LOW) 64 = 8 x 8 方格 (MEDIUM) 256 = 16 x 16 方格 （高） 的 NULL = 不適用於給定的空間索引類型或鑲嵌式配置。  使用新的 SQL Server 11 鑲嵌時，則傳回 NULL。|  
|level_2_grid_desc|**nvarchar(60)**|第 2 個層級的方格，其中的方格密度：低中型高 NULL = 不適用於給定的空間索引類型或鑲嵌式配置。  使用新的 SQL Server 11 鑲嵌時，則傳回 NULL。|  
|level_3_grid|**smallint**|第三層方格的方格密度。   如果 tessellation_scheme 為 GEOMETRY_GRID 或 GEOGRAPHY_GRID，其中一個：16 = 4 x 4 方格 (LOW) 64 = 8 x 8 方格 (MEDIUM) 256 = 16 x 16 方格 （高） 的 NULL = 不適用於給定的空間索引類型或鑲嵌式配置。  使用新的 SQL Server 11 鑲嵌時，則傳回 NULL。|  
|level_3_grid_desc|**nvarchar(60)**|第 3 層級的方格，其中的方格密度： 低中型高 NULL = 不適用於給定的空間索引類型或鑲嵌式配置。  使用新的 SQL Server 11 鑲嵌時，則傳回 NULL。|  
|level_4_grid|**smallint**|第四層方格的方格密度。 如果 tessellation_scheme 為 GEOMETRY_GRID 或 GEOGRAPHY_GRID，其中一個：16 = 4 x 4 方格 (LOW) 64 = 8 x 8 方格 (MEDIUM) 256 = 16 x 16 方格 （高） 的 NULL = 不適用於給定的空間索引類型或鑲嵌式配置。  使用新的 SQL Server 11 鑲嵌時，則傳回 NULL。|  
|level_4_grid_desc|**nvarchar(60)**|4th 層級的方格，其中的方格密度： < 低中型高 NULL = 不適用於給定的空間索引類型或鑲嵌式配置。  使用新的 SQL Server 11 鑲嵌時，則傳回 NULL。|  
|cells_per_object|**int**|每個空間物件，其中的資料格數目：如果 tessellation_scheme 為 GEOMETRY_GRID 或 GEOGRAPHY_GRID， *n* = 每個物件為 NULL 的資料格數目 = 不適用於給定的空間索引類型或鑲嵌式配置|  
  
## <a name="permissions"></a>Permissions  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [物件目錄檢視 &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/object-catalog-views-transact-sql.md)   
 [空間索引概觀](../../relational-databases/spatial/spatial-indexes-overview.md)   
 [sys.objects &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)   
 [sys.spatial_indexes &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-spatial-indexes-transact-sql.md)   
 [sys.indexes &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md)   
 [sys.index_columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-index-columns-transact-sql.md)  
  
  
