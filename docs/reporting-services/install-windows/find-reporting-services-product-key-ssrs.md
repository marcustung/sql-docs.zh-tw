---
title: 尋找 SQL Server 2017 Reporting Services (SSRS) 的產品金鑰 | Microsoft Docs
ms.date: 12/20/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.topic: conceptual
author: maggiesMSFT
ms.author: maggies
monikerRange: '>= sql-server-2017 || = sqlallproducts-allversions'
ms.openlocfilehash: 36460943b233f02e4d029b7865c7d7fa3844b488
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 06/15/2019
ms.locfileid: "65502917"
---
# <a name="how-to-find-the-product-key-for-sql-server-2017-reporting-services"></a>如何尋找 SQL Server 2017 Reporting Services 的產品金鑰

[!INCLUDE[ssrs-appliesto](../../includes/ssrs-appliesto.md)] [!INCLUDE[ssrs-appliesto-2017-and-later](../../includes/ssrs-appliesto-2017-and-later.md)] [!INCLUDE[ssrs-appliesto-not-pbirsi](../../includes/ssrs-appliesto-not-pbirs.md)]

了解如何尋找 SQL Server 2017 Reporting Services (SSRS) 產品金鑰，以在生產環境中安裝伺服器。

若要尋找您的產品金鑰，請從下載並執行 SQL Server 2017 安裝程式開始。

1. 從下列其中一個來源下載 SQL Server 2017：

    - 大量授權服務中心
    - MSDN 訂用帳戶
    - 零售 (從 Microsoft Store 下載)

1. 執行 SQL Server 2017 安裝程式，然後複製預先填入的金鑰：

    ![複製 SQL Server 2017 產品金鑰](media/find-reporting-services-product-key-ssrs/ssrs-ss2017-copy-product-key.png)

1. [執行 Reporting Services 設定](install-reporting-services.md)，並貼上金鑰：

     ![貼上產品金鑰](media/find-reporting-services-product-key-ssrs/ssrs-ssrs2017-paste-product-key.png)

第一次安裝 SSRS 2017 時，您應該只需要執行此步驟。 提供更新應該不需要您輸入金鑰。

## <a name="related-information"></a>相關資訊

- 如需安裝 SQL Server Reporting Services 原生模式的資訊，請參閱[安裝 Reporting Services 原生模式報表伺服器](install-reporting-services-native-mode-report-server.md)。 

::: moniker range="=sql-server-2016||=sqlallproducts-allversions"

- 如需以 SharePoint 整合模式安裝 SQL Server 2016 Reporting Services (和更早版本) 的資訊，請參閱[在 SharePoint 模式中安裝第一部報表伺服器](install-the-first-report-server-in-sharepoint-mode.md)。

::: moniker-end

## <a name="next-steps"></a>後續步驟

- [安裝 SQL Server 2017 Reporting Services](install-reporting-services.md)
- 更多問題嗎？ [請嘗試詢問 Reporting Services 論壇](https://go.microsoft.com/fwlink/?LinkId=620231)
