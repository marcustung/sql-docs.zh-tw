---
title: 資料庫檢查點 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 10/13/2015
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- automatic checkpoints
- transaction logs [SQL Server], checkpoints
- logs [SQL Server], active
- pages [SQL Server], dirty
- MinLSN
- checkpoints [SQL Server]
- pages [SQL Server], flushing
- dirty pages
- transaction logs [SQL Server], active logs
- recovery interval option [SQL Server]
- buffer cache [SQL Server]
- logs [SQL Server], checkpoints
- Minimum Recovery LSN
- flushing pages
- active logs
ms.assetid: 98a80238-7409-4708-8a7d-5defd9957185
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 33f85b2f1cd8b259e46851aab818b258a6d78291
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/15/2019
ms.locfileid: "68206107"
---
# <a name="database-checkpoints-sql-server"></a>資料庫檢查點 (SQL Server)
  本主題提供 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫檢查點的概觀。 *「檢查點」* (Checkpoint) 會建立一個已知的恰當起點， [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 可以從這個點開始套用發生非預期的關機或損毀之後，於復原期間包含在記錄檔中的變更。  
  
  
##  <a name="Overview"></a> 檢查點概觀  
 基於效能的考量，[!INCLUDE[ssDE](../../includes/ssde-md.md)]會在緩衝區快取的記憶體內修改資料庫頁面，但並不會在每次變更之後都將這些頁面寫入磁碟中。 而是由 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 定期在每一個資料庫上發出檢查點。 *「檢查點」* (Checkpoint) 會將目前記憶體中已修改的頁面 (稱為 *「中途分頁」* (Dirty Page)) 和交易記錄資訊從記憶體寫入磁碟上，也會記錄有關交易記錄的資訊。  
  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 支援幾種類型的檢查點：自動、間接、手動和內部。 下表彙總檢查點的類型。  
  
|名稱|[!INCLUDE[tsql](../../includes/tsql-md.md)] 介面|描述|  
|----------|----------------------------------|-----------------|  
|Automatic|EXEC sp_configure **'`recovery interval`'、' *`seconds`* '**|在以符合所建議的時間限制上限背景自動發出`recovery interval`伺服器組態選項。 自動檢查點會執行到完成為止。  自動檢查點的調節是根據未完成的寫入數目以及 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 是否偵測到超過 20 毫秒的寫入延遲有增加。<br /><br /> 如需詳細資訊，請參閱 [Configure the recovery interval Server Configuration Option](../../database-engine/configure-windows/configure-the-recovery-interval-server-configuration-option.md)。|  
|間接|ALTER DATABASE ...SET TARGET_RECOVERY_TIME **=** _target_recovery_time_ { SECONDS &#124; MINUTES }|在背景發出，以符合使用者對給定資料庫所指定的目標復原時間。 預設目標復原時間為 0，這會導致自動檢查點啟發學習法在資料庫上使用。 如果您已使用 ALTER DATABASE 將 TARGET_RECOVERY_TIME 設定為 >0，則會使用這個值，而不是針對伺服器執行個體指定的復原間隔。<br /><br /> 如需詳細資訊，請參閱 [變更資料庫的目標復原時間 &#40;SQL Server&#41;](change-the-target-recovery-time-of-a-database-sql-server.md)伺服器組態選項。|  
|手動|CHECKPOINT [ *checkpoint_duration* ]|當您執行 [!INCLUDE[tsql](../../includes/tsql-md.md)] CHECKPOINT 命令時發出。 手動檢查點會發生在連接的目前資料庫中。 根據預設，手動檢查點會執行到完成為止。 調節的運作方式與自動檢查點相同。  *checkpoint_duration* 參數可選擇性地指定要求的時間量 (以秒為單位)，好讓檢查點得以完成。<br /><br /> 如需詳細資訊，請參閱 [CHECKPOINT &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/checkpoint-transact-sql)。|  
|內部|無。|由各種伺服器作業 (例如備份和資料庫快照集建立) 發出，以保證磁碟映像符合目前的記錄檔狀態。|  
  
> [!NOTE]  
>  資料庫管理員可利用 `-k`[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 進階設定選項，根據某些類型的檢查點之 I/O 子系統輸送量，來調節檢查點 I/O 行為。 `-k`安裝選項會套用到自動檢查點以及任何未調節的手動與內部檢查點。  
  
 如果是自動、手動和內部檢查點，只有在最新檢查點之後所做的修改才需要在資料庫復原期間向前復原。 這會減少復原資料庫所需的時間。  
  
> [!IMPORTANT]  
>  長時間執行且未認可的交易會讓所有檢查點類型的復原時間增加。  
  
  
  
###  <a name="InteractionBwnSettings"></a> TARGET_RECOVERY_TIME 和 'recovery interval' 選項的互動  
 下表摘要說明伺服器端之間的互動**sp_configure'`recovery interval`'** 設定與資料庫特有 ALTER DATABASE...TARGET_RECOVERY_TIME 設定之間的互動。  
  
|target_recovery_time|'recovery interval'|使用的檢查點類型|  
|----------------------------|-------------------------|-----------------------------|  
|0|0|目標復原間隔為 1 分鐘的自動檢查點。|  
|0|>0|由使用者定義的 **sp_configurerecovery interval** 選項設定，所指定的目標復原間隔之自動檢查點。|  
|>0|不適用。|由 TARGET_RECOVERY_TIME 設定決定目標復原時間 (以秒鐘表示) 的間接檢查點。|  
  
###  <a name="AutomaticChkpt"></a> 自動檢查點  
 自動檢查點會在每次的記錄檔記錄數目到達數目[!INCLUDE[ssDE](../../includes/ssde-md.md)]估計可在指定的時間內處理`recovery interval`伺服器組態選項。 在沒有使用者定義之目標復原時間的每個資料庫中， [!INCLUDE[ssDE](../../includes/ssde-md.md)] 都會產生自動檢查點。 自動檢查點的頻率取決於`recovery interval`進階伺服器組態選項，指定給定的伺服器執行個體應該用來將資料庫復原期間重新啟動系統的時間上限。 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 會預估它在復原間隔內可以處理的記錄檔記錄數目上限。 當使用自動檢查點的資料庫到達這個記錄檔數目上限時， [!INCLUDE[ssDE](../../includes/ssde-md.md)] 會發出資料庫的檢查點。 自動檢查點之間的時間間隔可能會有很大的變化。 具有大量交易工作負載的資料庫所擁有的檢查點會比主要用於唯讀作業的資料庫更頻繁。  
  
 此外，在簡單復原模式下，如果記錄檔已填滿百分之 70，則自動檢查點也會排入佇列。  
  
 在簡單復原模式下，除非某些因素延遲了記錄截斷，否則自動檢查點會截斷交易記錄的未使用區段。 相反地，在完整復原模式和大量記錄復原模式下，一旦建立了記錄備份鏈，自動檢查點就不會導致記錄截斷。 如需詳細資訊，請參閱[交易記錄 &#40;SQL Server&#41;](the-transaction-log-sql-server.md)。  
  
 當系統損壞時，復原給定資料庫所需的時間長度大部分取決於重做損壞時已變更之頁面所需的隨機 I/O 數量。 這表示`recovery interval`設定不可靠。 它無法判斷精確的復原持續時間。 此外，當自動檢查點正在進行時，資料的一般 I/O 活動會大幅增加而且無法預測。  
  
  
####  <a name="PerformanceImpact"></a> 復原間隔對復原效能的影響  
 對於線上交易處理 (OLTP) 系統，使用簡短交易，`recovery interval`是決定復原時間的主要因素。 不過，`recovery interval`選項不會將長時間執行的交易復原所需的時間。 將長時間執行的交易在資料庫的復原可以花更長的時間比指定在`recovery interval`選項。 比方說，如果長時間執行交易花了兩個小時執行更新的伺服器執行個體變成停用之前，實際的復原花很長的時間比`recovery interval`復原長交易的值。 如需長時間執行的交易對復原時間之影響的詳細資訊，請參閱 [交易記錄 &#40;SQL Server&#41;](the-transaction-log-sql-server.md)。  
  
 一般來說，預設值會提供最佳復原效能。 但是在以下情況下，變更復原間隔可能會提升效能：  
  
-   如果未回復長時間執行的交易，復原通常花的時間大幅多於 1 分鐘時。  
  
-   如果您注意到頻繁的檢查點損害了資料庫的效能。  
  
 如果您決定增加 `recovery interval` 設定，我們建議您逐漸少量增加此設定，並評估每次累加對於復原效能的影響。 這個方法非常重要因為為`recovery interval`設定增加時，資料庫復原就要同樣多倍的時間才能完成。 例如，如果您變更`recovery interval`10，復原所花大約 10 倍的時間才能完成比`recovery interval`設為零。  
  
  
###  <a name="IndirectChkpt"></a> 間接檢查點  
 間接檢查點是 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]中的新功能，它會提供替代自動檢查點的可設定資料庫層級。 萬一系統損壞，間接檢查點可能會提供比自動檢查點更快而且更可以預測的復原時間。 間接檢查點會提供以下優點：  
  
-   設定間接檢查點的資料庫線上交易式工作負載可能會導致效能降低。 間接檢查點可確定中途分頁的數目，低於特定臨界值，如此即可在目標復原時間內完成資料庫的復原。 復原間隔組態選項會使用異動數目來判斷復原時間，而間接檢查點則是會利用中途分頁數目來判斷復原時間。 在收到大量 DML 作業的資料庫上啟用間接檢查點時，背景寫入器可開始積極排清磁碟的中途緩衝區，以確保執行復原所需的時間，落在資料庫所設的目標復原時間內。 如此會在某些系統上造成額外的 I/O 活動，而若磁碟子系統的運作超過或接近 I/O 臨界值，就會形成效能瓶頸。  
  
-   間接檢查點可讓您考量 REDO 期間的隨機 I/O 成本來可靠控制資料庫復原時間。 如此可讓伺服器執行個體維持在給定資料庫的復原時間上限內 (除非長時間執行的交易造成過多的復原次數)。  
  
-   間接檢查點會持續在背景中將中途分頁寫入磁碟，以減少與檢查點相關的 I/O 峰值。  
  
 但是，設定間接檢查點的資料庫線上交易式工作負載可能會導致效能降低。 這是因為，間接檢查點使用的背景寫入器有時會讓伺服器執行個體的寫入負載總量增加。  
  
  
###  <a name="EventsCausingChkpt"></a> 內部檢查點  
 內部檢查點是由各種伺服器元件產生，可保證磁碟映像符合目前的記錄檔狀態。 產生內部檢查點是為了回應以下事件：  
  
-   使用 ALTER DATABASE 加入或移除資料庫檔案。  
  
-   取得資料庫備份。  
  
-   針對 DBCC CHECK 建立資料庫快照集，不論是明確或內部方式。  
  
-   執行需要關閉資料庫的活動。 例如，AUTO_CLOSE 為 ON，且上次使用者與資料庫的連接已經關閉，或是已變更資料庫選項，因此需要重新啟動資料庫。  
  
-   經由停止 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (MSSQLSERVER) 服務，來停止 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的執行個體。 任何一項動作都會導致在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]執行個體的每個資料庫中產生檢查點。  
  
-   讓 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 容錯移轉叢集執行個體 (FCI) 離線。  
  
  
##  <a name="RelatedTasks"></a> 相關工作  
 **若要變更伺服器執行個體的復原間隔**  
  
-   [Configure the recovery interval Server Configuration Option](../../database-engine/configure-windows/configure-the-recovery-interval-server-configuration-option.md)  
  
 **若要設定資料庫的間接檢查點**  
  
-   [變更資料庫的目標復原時間 &#40;SQL Server&#41;](change-the-target-recovery-time-of-a-database-sql-server.md)  
  
 **若要發出資料庫的手動檢查點**  
  
-   [CHECKPOINT &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/checkpoint-transact-sql)  
  
  
##  <a name="RelatedContent"></a> 相關內容  
  
-   [交易記錄檔實體架構](https://technet.microsoft.com/library/ms179355.aspx) (在《 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] 線上叢書》中)  
  
  
## <a name="see-also"></a>另請參閱  
 [交易記錄 &#40;SQL Server&#41;](the-transaction-log-sql-server.md)  
  
  
