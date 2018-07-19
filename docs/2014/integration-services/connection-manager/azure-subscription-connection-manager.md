---
title: Azure 訂用帳戶連線管理員 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.afpsubscrconn.f1
- sql11.dts.designer.afpsubscrconn.f1
ms.assetid: e1225327-c308-4c50-8f44-c411f52ef378
caps.latest.revision: 9
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 1fa0589e7ac68f3662929c6316cdd0ddf427911d
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2018
ms.locfileid: "37306108"
---
# <a name="azure-subscription-connection-manager"></a>Azure 訂用帳戶連線管理員
  Azure HDInsight 連線管理員可讓 SSIS 封裝連接到 Azure 訂用帳戶所使用的屬性所指定的值： Azure 訂用帳戶 ID 和管理憑證。  
  
1.  在上方顯示的 [加入 SSIS 連線管理員] 對話方塊中，選取 [Azure 訂用帳戶]，然後按一下 [加入]。  [Azure Subscription Connection Manager Editor (Azure 訂用帳戶連線管理員編輯器)] 對話方塊應會隨即出現。  
  
     ![SSIS AzureSubscriptionManager](../media/ssis-azuresubscriptionmanager.png "SSIS AzureSubscriptionManager")  
  
2.  在 [Azure 訂用帳戶識別碼] 輸入可唯一識別 Azure 訂用帳戶的 Azure 訂用帳戶識別碼。  可以在 [設定] 頁面下的 [Azure 管理入口網站](https://manage.windowsazure.com)找到此值：  
  
     ![SSIS-AzureSettings-SubscriptionID](../media/ssis-azuresettings-subscriptionid.png "SSIS-AzureSettings-SubscriptionID")  
  
3.  從下拉式清單中選擇 [Management certificate store location (管理憑證存放區位置)] 和 [Management certificate store name (管理憑證存放區名稱)]。  
  
4.  輸入 [管理憑證指紋]，或按一下 [瀏覽] 可從選取的存放區選擇憑證 以從選取的存放區中選擇憑證。 憑證必須上傳為訂用帳戶的管理憑證。 若要這樣做，請按一下 Azure 入口網站下一個頁面上的 [上傳] (如需詳細資訊，請參閱此 [MSDN 文章](https://msdn.microsoft.com/library/azure/gg551722.aspx))。  
  
     ![SSIS-AzureSettings-ManagementCertificate](../media/ssis-azuresettings-managementcertificate.png "SSIS-AzureSettings-ManagementCertificate")  
  
5.  按一下 [測試連接] 來測試連接。  
  
6.  按一下 **[確定]** ，關閉對話方塊。  
  
  