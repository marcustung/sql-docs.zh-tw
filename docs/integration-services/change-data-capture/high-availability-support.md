---
title: 高可用性支援 | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 2e0f6d3f-0536-46d9-8630-835e199515bf
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 610da7f6b7ef6fed5e3be6cb5ae2e7be53bf31fc
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/15/2019
ms.locfileid: "65728837"
---
# <a name="high-availability-support"></a>高可用性支援

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  Oracle CDC 服務是專為高可用性所設計。 以下功能會提供部分高可用性支援：  
  
-   Oracle CDC 服務不使用任何檔案資源 (本機或其他資源)。 其完整狀態會儲存在目標 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體中。 如此一來，如果執行此服務的電腦失敗，便可在使用相同 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體的另一部電腦上輕鬆啟動此服務。 為了減少復原時間，長時間執行的 Oracle 交易會保留在目標 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的暫存資料表中，這樣就不需要在失敗之後重新掃描許多 Oracle 交易記錄 (或是重新啟動服務)。  
  
-   Oracle CDC 服務可以使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 叢集執行個體，如此一來，它就可以在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體容錯移轉到另一個叢集節點時復原。 在建立 Oracle CDC 服務時，Oracle CDC 服務電腦管理員只需要指定與 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 叢集執行個體的連接資訊。  
  
-   Oracle CDC 服務可使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]**AlwaysOn** 資料庫鏡像功能。 此支援要求 MSXDBCDC 與所有 CDC 資料庫位於相同的可用性群組中。 它也會要求 Oracle CDC 服務電腦管理員指定與 **可用性群組的適當** AlwaysOn [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 連接資訊 (例如， `Failover_Partner and Network=dbmssocn`連接屬性)。 這樣可讓 CDC 服務在容錯移轉之後，自動繼續資料庫次要複寫的處理。  
  
-   Oracle CDC 服務可設定為 Windows 容錯移轉叢集上的一般服務資源 (與 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]一起或分開)，這樣 CDC 對叢集的容錯移轉和退讓處理就會很輕鬆。 若要將 Oracle CDC 服務設定為容錯移轉叢集中的資源，系統管理員必須將 Oracle CDC 服務設定為容錯移轉叢集上每一個節點中的一般服務資源。  
  
-   Oracle CDC 服務支援 Oracle RAC，好讓它與 Oracle 資料庫通訊並處理記錄，即使當其中一個 Oracle RAC 節點關閉時也是如此。  
  
  
