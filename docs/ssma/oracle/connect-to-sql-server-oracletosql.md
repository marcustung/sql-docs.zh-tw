---
title: 連接到 SQL Server (OracleToSQL) |Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 4ef384ea-5f3e-4f70-ad7c-b62d7b0da628
author: Shamikg
ms.author: Shamikg
manager: shamikg
ms.openlocfilehash: e6e06585ca99305d6825898a98a7dbab31b5b39b
ms.sourcegitcommit: e7d921828e9eeac78e7ab96eb90996990c2405e9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/16/2019
ms.locfileid: "68266166"
---
# <a name="connect-to-sql-server--oracletosql"></a>連線到 SQL Server (OracleToSQL)
使用**連接到 SQL Server**對話方塊中，連接到的執行個體[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]您想要移轉到。 若要存取**連接到 SQL Server**對話方塊的 **檔案**功能表上，按一下 **連接到 SQL Server**。  
  
## <a name="options"></a>選項。  
**伺服器名稱**  
輸入或選取 連接到 SQL Server 執行個體。 根據預設，會顯示您連線到最近的執行個體。  
  
-   如果您要連接到本機電腦上的預設執行個體，您可以輸入**localhost**或句點 ( **。** )。  
  
-   如果您要連接到另一部電腦上的預設執行個體，請輸入電腦的名稱。  
  
-   如果您要連接到另一部電腦上的具名執行個體，輸入電腦名稱、 反斜線和執行個體名稱，例如*MyServer*\\*MyInstance*。  
  
**伺服器通訊埠**  
如果您的執行個體[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]未設定成接受連線，使用預設通訊埠 (1433) 中，輸入連接埠號碼。 否則，這個值保留空白。  
  
**[資料庫備份]**  
指定要將物件和資料移轉的資料庫。 此選項時，無法提供重新連接到[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。  
  
**驗證**  
選取用來連接到的驗證方法[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。 若要使用您目前的 Windows 帳戶，選取 [Windows 驗證]。 若要指定[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]登入和密碼，選取[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]驗證。  
  
**使用者名稱**  
如果您使用[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]驗證，輸入執行個體的登入[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。 如果您使用 Windows 驗證，此選項無法使用。  
  
**密碼**  
如果您使用[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]驗證登入輸入密碼，該執行個體上[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。 如果您使用 Windows 驗證，此選項無法使用。  
  
**加密連接**  
如果您想要安全地連線到 SQL Server，請檢查使用的加密連接**加密連接**核取方塊。  
  
**信任伺服器憑證**  
如果您想要使用此選項，選取**信任伺服器憑證**核取方塊。  
  
> [!NOTE]  
> 若要啟用**信任伺服器憑證**、 [加密] 必須設定為 **，則為 True**。  
  
