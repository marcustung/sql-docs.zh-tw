---
title: "核心 SQLXML 安全性考量 |Microsoft 文件"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: sqlxml
ms.reviewer: 
ms.suite: sql
ms.technology: dbe-xml
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: security [SQLXML], about security
ms.assetid: 330cd2ff-d5d5-4c8e-8f93-0869c977be94
caps.latest.revision: "12"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 185fd7894bf179bcc43df4c5b6ce9c31e702143f
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/17/2017
---
# <a name="core-sqlxml-security-considerations"></a>SQLXML 的核心安全性考量
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]以下是使用 SQLXML 進行資料存取安全性指導方針。  
  
-   SQLXMLOLEDB 提供者會公開**StreamFlags**屬性可讓您設定旗標，指出應該啟用或停用每個特定執行個體什麼 SQLXML 功能。 您可以使用這個屬性來自訂 SQLXML 的使用，並確定只有您所要的元件啟用。 如需詳細資訊，請參閱[SQLXMLOLEDB 提供者 &#40;SQLXML 4.0 &#41;](http://msdn.microsoft.com/library/fc489682-690a-4bb0-b5ac-237d376dc110).  
  
-   當 SQLXML 錯誤發生且傳回時，可能會包含有關資料表名稱、資料行名稱或類型資訊之類的資料庫結構描述的資訊。 在處理這些錯誤時應該要小心，以免有關您的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 安裝的資訊在非預期或不必要的情況下被使用者輕易地找到。  
  
-   當用來查詢或傳送 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 的更新時，SQLXML 不會對可交換的資料量設定限制，也不會在嘗試處理 SQLXML 裝載之前，對該裝載中的資料大小進行任何檢查。 使用 SQLXML 開發應用程式時，您有責任確保系統上有足夠的記憶體可以處理資料。 例如，從伺服器查詢資料時，應該確認用戶端上的記憶體中有足夠的空間可以接收該資料。 同樣地，如果要將資料上傳到伺服器，則需要確認伺服器上有足夠的記憶體可以處理該資料，也有足夠的可用磁碟儲存空間來儲存該資料。  
  
-   SQLXML 會動態地產生 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 查詢和更新命令，並將其傳送至 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 進行執行。 這是 SQLXML 查詢和更新伺服器的唯一方法。 結果會以 XML 資料流或資料列集的方式接收。  
  
-   在接收查詢結果時，SQLXML 不會根據它接收的資料內容採取任何動作。 系統不會根據資料的類型或內容而進行任何其他處理。 資料絕不會被視為用來執行動作的程式碼。  
  
-   在執行 XML 範本時，SQLXML 會將包含在所提交範本內的 XPath 和 DBObject 查詢轉譯為 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 命令，之後這些命令會針對 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行。 這些命令只會影響現有的資料。 SQLXML 所產生的命令絕不會改變資料庫的結構。 使用者必須發出明確的命令才能改變資料庫結構。 例如，藉由在**sql:query**區塊的範本。  
  
-   在對應檔案上執行 DBObject 查詢和 XPath 陳述式時，SQLXML 不會對資料庫中的資料進行任何改變。  
  
-   SQLXML 可能會根據 XML 和 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 資料模型之間的差異，對給定資料進行格式上的變更。 例如，指定時間的格式是不同的。 SQLXML 會嘗試解決這些差異。 結果是某些精確度的資訊可能會遺失。  
  
-   SQLXML 不會對其用來處理資料的時間量設定限制。 在發生錯誤或處理完成之前，都會繼續進行處理。  
  
-   SQLXML 不會寫入至檔案系統。 如果使用者想要儲存從資料庫所擷取的資料，則必須在其程式碼中進行這項作業。  
  
-   SQLXML 可以讓使用者針對資料庫執行任何所要的 SQL 查詢。 絕對不要將這項功能公開至不安全或未受控制的來源，因為這樣基本上是在未規定任何使用者的情況下，讓 SQL 資料庫門戶洞開。  
  
-   執行 Updategrams 時，SQLXML 會將轉譯**updg:sync**區塊為 DELETE、 UPDATE 和 INSERT 命令，針對[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]執行個體。 這些命令只會影響現有的資料。 SQLXML 所產生的命令絕不會改變資料庫。 使用者必須發出明確的命令才能改變資料庫結構。 例如，藉由在**sql:query**區塊的範本。  
  
-   執行 DiffGrams 時，SQLXML 會將 DiffGram 針對 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體轉譯為 DELETE、UPDATE 和 INSERT 命令。 這些命令只會影響現有的資料。 SQLXML 所產生的命令絕不會改變資料庫。 使用者必須發出明確的命令才能改變資料庫結構。 例如，藉由在**sql:query**區塊的範本。  
  
## <a name="see-also"></a>請參閱＜  
 [SQLXML 4.0 安全性考量](../../../relational-databases/sqlxml-annotated-xsd-schemas-xpath-queries/security/sqlxml-4-0-security-considerations.md)  
  
  