---
title: 對使用者授與 DQS 角色 | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: data-quality-services
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: afb445b5-bdbe-4bfe-844f-344766cdc2b2
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: ab6554acd249e119c054754f5b6b6f5196071322
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "67935219"
---
# <a name="grant-dqs-roles-to-users"></a>對使用者授與 DQS 角色

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  本主題描述如何根據 Windows 主體建立 SQL 登入，並在 DQS_MAIN 資料庫上授與 [!INCLUDE[ssDQSnoversion](../../includes/ssdqsnoversion-md.md)] (DQS) 角色。  
  
## <a name="prerequisites"></a>先決條件  
  
-   您必須執行 DQSInstaller.exe 檔案，才可以完成 [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] 的安裝。 如需詳細資訊，請參閱 [執行 DQSInstaller.exe 完成 Data Quality Server 安裝](../../data-quality-services/install-windows/run-dqsinstaller-exe-to-complete-data-quality-server-installation.md)。  
  
-   您的 Windows 使用者帳戶必須是適當固定伺服器角色 (例如 securityadmin、serveradmin 或 sysadmin) 的成員，才能建立 SQL 登入並授與它們 DQS 角色。  
  
### <a name="to-create-sql-login-and-grant-dqs-roles"></a>若要建立 SQL 登入並授與 DQS 角色  
  
1.  啟動 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]。  
  
2.  在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中，展開您的 SQL Server 執行個體，然後展開 **[安全性]** 。  
  
3.  以滑鼠右鍵按一下 [安全性]  資料夾，並指向 [新增]  ，然後按一下 [登入]  。  
  
4.  在 [登入 - 新增]  對話方塊的 [登入名稱]  方塊中，指定 Windows 使用者的名稱，指定 [Windows 驗證]  做為驗證類型，然後按一下 [搜尋]  驗證使用者。  
  
5.  使用者驗證完成後，按一下左窗格中的 **[使用者對應]** 頁面。  
  
6.  在右窗格中，從 **DQS_MAIN** 資料庫的 [對應]  資料行底下選取該核取方塊，然後選取 **dqs_administrator**、**dqs_kb_editor** 或 **dqs_kb_operator** 核取方塊，這些核取方塊位於 [資料庫角色成員資格對象: DQS_MAIN]  窗格中，且根據使用者所需的存取層級來選取。 如需有關三個 DQS 角色的詳細資訊，請參閱＜ [DQS 安全](../../data-quality-services/dqs-security.md)＞。  
  
7.  在 [登入 - 新增]  對話方塊中，按一下 [確定]  套用變更。  
  
    > [!NOTE]  
    >  如果您對使用者授與 **dqs_administrator** 角色並套用了變更，然後重新檢查使用者的權限，也會同時選取另外兩個 DQS 角色核取方塊 (**dq_kb_editor** 和 **dqs_kb_operator**)。  
  
## <a name="next-steps"></a>後續步驟  
 嘗試使用您剛才為其建立 SQL 登入並授與 DQS 角色的 Windows 使用者帳戶登入 [!INCLUDE[ssDQSServer](../../includes/ssdqsserver-md.md)] 。  
  
## <a name="see-also"></a>另請參閱  
 [安裝 Data Quality Services](../../data-quality-services/install-windows/install-data-quality-services.md)   
 [建立登入](../../relational-databases/security/authentication-access/create-a-login.md)  
  
  
