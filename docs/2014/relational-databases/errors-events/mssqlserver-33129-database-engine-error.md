---
title: MSSQLSERVER_33129 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 33129 (Database Engine error)
ms.assetid: 83b5f368-f1a1-4a40-9bb6-c77e2dec690f
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 991757d1bfeae8ecc0dec3a69d82c3dcab6415b1
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/15/2019
ms.locfileid: "62914645"
---
# <a name="mssqlserver33129"></a>MSSQLSERVER_33129
    
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|[SQL Server]|  
|事件識別碼|33129|  
|事件來源|MSSQLSERVER|  
|元件|SQLEngine|  
|符號名稱|SEC_CANNOT_DISABLE_WIN_GROUP|  
|訊息文字|無法使用含 DISABLE 引數的 ALTER_LOGIN 來拒絕存取 Windows 群組。|  
  
## <a name="explanation"></a>說明  
 嘗試停用 Windows 群組的登入時，會出現此訊息。  
  
## <a name="user-action"></a>使用者動作  
 您無法停用 Windows 群組的登入。 若要暫時移除授予 Windows 群組的存取權限，則使用 REVOKE 撤銷對 Windows 群組之登入的 CONNECT 權限。 Windows 使用者仍然可能透過其個別登入或透過另一個 Windows 群組具有存取權。 以下的範例會撤銷 WESTCOAST 網域之 Accounting 群組的連接權限。  
  
```sql  
REVOKE CONNECT TO [WESTCOAST\Accounting];  
```  
  
  
