---
title: 註冊已連接的伺服器 (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.swb.registerserver.f1
helpviewer_keywords:
- Registered Servers [SQL Server], register connected servers
- connected server registrations [SQL Server]
ms.assetid: 77deb5f5-0f80-484f-8b8b-29afa67ec18f
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 80dbd927f0a1b008e48fda7fcbd4a7e75b7fbaf8
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/15/2019
ms.locfileid: "63191936"
---
# <a name="register-a-connected-server-sql-server-management-studio"></a>註冊連接的伺服器 (SQL Server Management Studio)
  此主題描述如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] ，在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中註冊伺服器。 透過註冊伺服器，您可以儲存經常存取之伺服器的連接資訊。 您可以在連接之前或連接時從 [物件總管] 註冊伺服器。  
  
 **本主題內容**  
  
-   **若要使用下列項目註冊伺服器：**  
  
     [Transact-SQL](#SSMSProcedure)  
  
##  <a name="SSMSProcedure"></a> 使用 SQL Server Management Studio  
  
#### <a name="to-register-a-connected-server"></a>若要註冊連接的伺服器  
  
1.  在物件總管中，以滑鼠右鍵按一下已連接的伺服器，然後按一下 [註冊]  。  
  
     **伺服器名稱**  
     輸入您要用於已註冊之伺服器的名稱。 使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 註冊本機或遠端伺服器，可以讓您儲存伺服器連接資訊供未來連接使用。 此欄位的預設值為您連接到伺服器時所輸入的伺服器名稱。 您可以保留此伺服器名稱，或輸入伺服器的另一個易用名稱。  
  
     **伺服器描述**  
     輸入伺服器的選擇性描述。 允許的最大字元數為 250。  
  
     **選取 伺服器群組**  
     選取您要儲存伺服器註冊的伺服器群組。  
  
     **新增群組**  
     按一下即可啟動 [新增群組]  對話方塊，您可以在此為已註冊的伺服器建立新的伺服器群組。  
  
     **儲存**  
     按一下即可儲存您所輸入的資訊，然後建立已註冊的伺服器。  
  
  
