---
title: MSSQLSERVER_3452 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 3452 (Database Engine error)
ms.assetid: bf838f02-7186-4b33-b01e-361b0c02de1f
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: b30cd4786e278b4fa88eb4264165e0c1449eeeb7
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/15/2019
ms.locfileid: "62985951"
---
# <a name="mssqlserver3452"></a>MSSQLSERVER_3452
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>詳細資料  
  
|||  
|-|-|  
|產品名稱|SQL Server|  
|事件識別碼|3452|  
|事件來源|MSSQLSERVER|  
|元件|SQLEngine|  
|符號名稱|REC_CHECKIDENTITY|  
|訊息文字|資料庫 '%.*ls' (%d) 的復原偵測到資料表識別碼 %d 中的識別值可能不一致。 請執行 DBCC CHECKIDENT ('%.\*ls')。|  
  
## <a name="explanation"></a>說明  
升級至 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 時，復原資料庫中識別值的處理序在中繼資料中發現不一致的問題。  
  
## <a name="user-action"></a>使用者動作  
執行 DBCC CHECKIDENT。  
  
