---
title: MSSQLSERVER_9790 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 9790 (Database Engine error)
ms.assetid: 83fd379f-5deb-4f97-8cb4-282e3d3fed94
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: dd965940d43fdcc1e2420e8c5a43e512b45298e2
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/15/2019
ms.locfileid: "63014963"
---
# <a name="mssqlserver9790"></a>MSSQLSERVER_9790
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|SQL Server|  
|事件識別碼|9790|  
|事件來源|MSSQLSERVER|  
|元件|SQLEngine|  
|符號名稱|SB3_XMIT_ERROR_ENTRANCE_BROKER_SINGLE_USER|  
|訊息文字|無法路由內送訊息。 包含路由資訊的系統資料庫 MSDB 正處於單一使用者 (SINGLE USER) 模式。|  
  
## <a name="explanation"></a>說明  
嘗試分類離線接收的訊息時發生錯誤，因為 MSDB 資料庫處於單一使用者模式中。  
  
## <a name="user-action"></a>使用者動作  
使用 ALTER DATABASE 命令，將 MSDB 變更為 MULTI USER 模式。  
  
