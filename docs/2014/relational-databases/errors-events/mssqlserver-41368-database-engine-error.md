---
title: MSSQLSERVER_41368 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 41368 (Database Engine error)
ms.assetid: abc71559-4c4d-4cce-a08f-3299dd167842
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: a2206980d241d3ef0aa683e4f987a4e337a86855
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/15/2019
ms.locfileid: "62913803"
---
# <a name="mssqlserver41368"></a>MSSQLSERVER_41368
    
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|事件識別碼|41368|  
|事件來源|MSSQLSERVER|  
|元件|SQLEngine|  
|符號名稱|SQL_IMPLICIT_AND_EXPLICIT_TX_NOT_SUPPORTED|  
|訊息文字|只有自動認可交易才支援使用 READ COMMITTED 隔離等級來存取記憶體最佳化的資料表。 明確或隱含交易則不支援。 為使用資料表提示例如 WITH (SNAPSHOT) 的記憶體最佳化資料表，提供支援的隔離等級。|  
  
## <a name="explanation"></a>說明  
 只有自動認可交易支援使用 READ COMMITTED 隔離等級存取記憶體最佳化資料表。 如需詳細資訊，請參閱 [Transaction Isolation Levels](../../database-engine/transaction-isolation-levels.md)。  
  
 如果您存取記憶體最佳化的資料表是透過以 BEGIN TRANSACTION 啟動的明確交易，或是透過 IMPLICIT_TRANSACTIONS 設為 ON 的隱含交易，便不支援 READ COMMITTED 隔離等級。  
  
## <a name="user-action"></a>使用者動作  
 透過明確或隱含 READ COMMITTED 交易存取記憶體最佳化的資料表時，請使用快照集 (SNAPSHOT) 存取資料表。 這可藉由使用資料表提示 WITH (SNAPSHOT) (如需詳細資訊，請參閱 <<c0> [ 指導方針與記憶體最佳化資料表的交易隔離等級](../in-memory-oltp/memory-optimized-tables.md)) 或是將資料庫設定選項 MEMORY_OPTIMIZED_ELEVATE_TO_快照集設為 ON (如需詳細資訊，請參閱 < [ALTER DATABASE SET 選項&#40;TRANSACT-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options))。</c0>  
  
## <a name="see-also"></a>另請參閱  
 [記憶體內部 OLTP &#40;記憶體內部最佳化&#41;](../in-memory-oltp/in-memory-oltp-in-memory-optimization.md)  
  
  
