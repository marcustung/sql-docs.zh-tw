---
title: 建立變更集 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: cfad6f1c-9125-4896-b5f5-a4b9f9593cc4
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: e3e15590e2d8f8e3317c8d116ebbeac7049fb1ea
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "68079756"
---
# <a name="create-a-changeset-master-data-services"></a>建立變更集 (Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  變更集是對主要資料所做的暫止變更集合。 如果實體需要核准變更，則必須將暫止變更儲存至變更集，然後提交由系統管理員核准。  
  
## <a name="prerequisites"></a>先決條件  
  
-   您必須擁有存取 [總管] 功能區域的權限。 如需詳細資訊，請參閱[功能區域權限 &#40;Master Data Services&#41;](../master-data-services/functional-area-permissions-master-data-services.md)  
  
-   您必須至少具有實體或其中一個屬性的讀取存取權。  
  
## <a name="to-create-a-local-changeset"></a>建立本機變更集  
  
1.  在 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 首頁上，選取模型和版本，然後按一下總管  。  
  
2.  按一下 [實體]  功能表中的實體。  
  
3.  在右窗格中，選取 [變更集]  ，然後按一下 [建立]  。  
  
4.  輸入變更集的名稱，然後按一下 [儲存]  。  
  
     在模型內的變更集名稱必須是唯一的。  
  
## <a name="to-create-a-changeset-for-approval"></a>建立變更集以進行核准  
  
1.  在 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 首頁上，選取模型和版本，然後按一下總管  。  
  
2.  按一下 [實體]  功能表中的實體。  
  
3.  對實體進行變更，然後按一下 [確定]  。  
  
4.  [選擇變更集]  對話方塊隨即顯示。  
  
5.  按一下 [新增]  ，並輸入變更集的名稱，然後按一下 [儲存]  。 在模型內的變更集名稱必須是唯一的。  
  
6.  若要使用現有的變更集，請按一下 [現有]  ，並從清單中選擇變更集。 只能使用已開啟或已拒絕狀態的變更集。  
  
## <a name="next-steps"></a>後續步驟  
 [套用及更新變更集 &#40;Master Data Services&#41;](../master-data-services/apply-and-update-a-changeset-master-data-services.md)  
  
## <a name="see-also"></a>另請參閱  
 [認可或提交變更集 &#40;Master Data Services&#41;](../master-data-services/commit-or-submit-a-changeset-master-data-services.md)   
 [核准或拒絕變更集 &#40;Master Data Services&#41;](../master-data-services/approve-or-reject-a-changeset-master-data-services.md)  
  
  
