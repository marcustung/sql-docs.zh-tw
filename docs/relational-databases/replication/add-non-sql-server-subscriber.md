---
title: 新增非 SQL Server 訂閱者 | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql13.rep.newsubwizard.addnonsqlsubscriber.f1
ms.assetid: 21beeaa0-4b9e-48da-be63-1b9ff14e03d2
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 64a0cf8fb19bd9e89efce96f2e9705eb6b2b9ae1
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/15/2019
ms.locfileid: "62665574"
---
# <a name="add-non-sql-server-subscriber"></a>加入非 SQL Server 訂閱者
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  複寫可以支援為 Oracle 和 IBM DB2 訂閱者建立快照式和交易式發行集的發送訂閱。  
  
## <a name="options"></a>選項。  
 **要加入的訂閱者類型**  
 選取 Oracle 訂閱者或 IBM DB2 訂閱者。 如需這些訂閱者支援的詳細資訊，請參閱[非 SQL Server 訂閱者](../../relational-databases/replication/non-sql/non-sql-server-subscribers.md)。  
  
 **資料來源名稱**  
 在用來尋找網路上之資料庫的名稱。 複寫會使用資料來源名稱，結合登入、密碼及您在此精靈的 **[散發代理程式安全性]** 頁面中指定的任何連接選項，來產生資料庫的連接字串。  
  
> [!NOTE]
>  The data source name and connection string are not validated by [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] until the Distribution Agent attempts to initialize the subscription.  
  
## <a name="see-also"></a>另請參閱  
 [為非 SQL Server 訂閱者建立訂閱](../../relational-databases/replication/create-a-subscription-for-a-non-sql-server-subscriber.md)   
 [Non-SQL Server Subscribers](../../relational-databases/replication/non-sql/non-sql-server-subscribers.md)   
 [訂閱發行集](../../relational-databases/replication/subscribe-to-publications.md)  
  
  
