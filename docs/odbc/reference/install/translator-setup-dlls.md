---
title: 轉譯程式安裝程式 Dll |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- translator setup DLL [ODBC]
ms.assetid: b3ca79e9-01b9-4541-81de-bbbad24ca736
author: MightyPen
ms.author: genemi
ms.openlocfilehash: b6c99dffc94f2675efdbbc3d5c1d142a5ae9b7e5
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "68093843"
---
# <a name="translator-setup-dlls"></a>轉譯程式安裝程式 DLL
> [!NOTE]  
>  從 Windows XP 和 Windows Server 2003 開始，ODBC 會包含在 Windows 作業系統。 您只明確應該安裝在舊版 Windows 上的 ODBC。  
  
 轉譯程式安裝程式 DLL 包含**ConfigTranslator**函式，它會傳回轉換程式的預設選項。 如有必要，它會提示使用者提供這項資訊。 如需此函式的完整說明，請參閱[安裝程式 DLL API 參考](../../../odbc/reference/syntax/setup-dll-api-reference.md)。  
  
 轉譯程式安裝程式 DLL 是由轉譯程式開發人員撰寫。 它可以是轉譯程式組件 DLL 或不同的 DLL。
