---
title: Linux 上的 SQL Server 的 active Directory 驗證
titleSuffix: SQL Server
description: 這篇文章會提供在 Linux 上的 SQL Server 中的 Active Directory 驗證的概觀。
ms.date: 04/01/2019
author: Dylan-MSFT
ms.author: dygray
ms.reviewer: vanto
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
helpviewer_keywords:
- Linux, AAD authentication
ms.openlocfilehash: 14cb6a377e6aeb0fbd24f9808a794d68633f4ce6
ms.sourcegitcommit: 93d1566b9fe0c092c9f0f8c84435b0eede07019f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/11/2019
ms.locfileid: "67834417"
---
# <a name="active-directory-authentication-for-sql-server-on-linux"></a>Linux 上的 SQL Server 的 active Directory 驗證

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

這篇文章提供的 Active Directory (AD) 驗證概觀[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]Linux 上。 AD 驗證，也就是在整合式的驗證[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]。 

## <a name="ad-authentication-overview"></a>AD 驗證概觀

AD 驗證可讓已加入網域的 Windows 或 Linux 上驗證的用戶端[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]使用其網域認證和 Kerberos 通訊協定。

AD 驗證透過具有下列優點[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]驗證：

- 使用者驗證透過單一登入，而不提示輸入密碼。   
- 藉由建立 AD 群組的登入，您可以管理存取和權限在[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]使用 AD 群組成員資格。  
- 每個使用者會有組織的單一身分識別讓您不必追蹤其中的[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]登入對應到哪些人。   
- AD 可讓您強制執行組織的集中式的密碼原則。   

## <a name="configuration-steps"></a>組態步驟

若要使用 Active Directory 驗證，您必須在網路上有 AD 網域控制站 (Windows)。

如何設定 AD 驗證的詳細資料中的教學課程中，提供[教學課程：Linux 上的 SQL Server 使用 Active Directory 驗證](sql-server-linux-active-directory-authentication.md)。 下列清單提供摘要，以包含每個區段的連結，在本教學課程：

1. [加入 Active Directory 網域的 SQL Server 主機](sql-server-linux-active-directory-join-domain.md)。
1. [適用於 SQL Server 中建立 AD 使用者和設定 ServicePrincipalName](sql-server-linux-active-directory-authentication.md#createuser)。
1. [設定 SQL Server 服務 keytab](sql-server-linux-active-directory-authentication.md#configurekeytab)。
1. [安全 keytab 檔案](sql-server-linux-active-directory-authentication.md#securekeytab)。
1. [設定 SQL Server 以使用 keytab 檔案進行 Kerberos 驗證](sql-server-linux-active-directory-authentication.md#keytabkerberos)。
1. [在 TRANSACT-SQL 中建立 AD 為基礎的 SQL Server 登入](sql-server-linux-active-directory-authentication.md#createsqllogins)。
1. [連接到 SQL Server 使用 AD 驗證](sql-server-linux-active-directory-authentication.md#connect)。

## <a name="known-issues"></a>已知問題

- 此時，資料庫鏡像端點支援的唯一驗證方法是憑證。 在未來版本中，將會啟用 WINDOWS 驗證方法。

## <a name="next-steps"></a>後續步驟

如需有關如何在 Linux 上實作適用於 SQL Server 的 Active Directory 驗證的詳細資訊，請參閱[教學課程：Linux 上的 SQL Server 使用 Active Directory 驗證](sql-server-linux-active-directory-authentication.md)。
