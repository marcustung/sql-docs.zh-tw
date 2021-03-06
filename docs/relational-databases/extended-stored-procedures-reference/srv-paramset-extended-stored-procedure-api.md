---
title: srv_paramset (擴充預存程序 API) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
apiname:
- srv_paramset
apilocation:
- opends60.dll
apitype: DLLExport
dev_langs:
- C++
helpviewer_keywords:
- srv_paramset
ms.assetid: 2a509206-a1b8-4b20-b0a2-ef680cef7bd8
author: rothja
ms.author: jroth
ms.openlocfilehash: f2b4864ac13d431c3507930abc1e774b4ac6adaa
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "68119716"
---
# <a name="srvparamset-extended-stored-procedure-api"></a>srv_paramset (擴充預存程序 API)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] 請改用 CLR 整合。  
  
 設定遠端預存程序呼叫傳回參數的值。 此函式已被 **srv_paramsetoutput** 函式取代。  
  
## <a name="syntax"></a>語法  
  
```  
  
int srv_paramset (  
SRV_PROC *  
srvproc  
,  
int  
n  
,   
void *  
data  
,  
int  
len   
);  
```  
  
## <a name="arguments"></a>引數  
 *srvproc*  
 這是 SRV_PROC 結構的指標，也是特定用戶端連接的控制代碼 (在這個狀況之下，該控制代碼會收到遠端預存程序呼叫)。 擴充預存程序 API 程式庫會使用該結構所包含的資訊來管理應用程式與用戶端之間的通訊和資料。  
  
 *n*  
 表示要設定的參數數目。 第一個參數是 1。  
  
 *data*  
 這是指向要當做遠端預存程序傳回參數傳回給用戶端之資料值的指標。  
  
 *len*  
 指定要傳回之資料的實際長度。 如果參數的資料類型具有固定長度，而且不允許 null 值 (例如 *srvbit* 或 *srvint1*)，則會忽略 *len*。  
  
## <a name="returns"></a>傳回值  
 如果參數值設定成功則會傳回 SUCCEED，否則會傳回 FAIL。 目前沒有任何遠端預存程序、沒有第 *n* 個遠端預存程序參數、此參數並非傳回參數，以及 *len* 引數不合法時，會傳回 FAIL。  
  
 如果 *len* 是 0，它會傳回 NULL。 將 *len* 設定為 0 是將 NULL 傳回給用戶端的唯一方法。  
  
 如果參數是 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 資料類型的一種，則此函式會傳回下列值。  
  
|新的資料類型|傳回資料長度|  
|--------------------|------------------------|  
|**BITN**|**NULL：** _len_ = 0、data = IG、RET = 0<br /><br /> **ZERO：** 不適用<br /><br /> **>=255：** 不適用<br /><br /> **<255：** 不適用|  
|**BIGVARCHAR**|**NULL：** _len_ = 0、data = IG、RET = 1<br /><br /> **ZERO：** _len_ = IG、data = IG、RET = 0<br /><br /> **>=255：** _len_ = max8k、data = valid、RET = 0<br /><br /> **<255：** _len_ = <8k、data = valid、RET = 1|  
|**BIGCHAR**|**NULL：** _len_ = 0、data = IG、RET = 1<br /><br /> **ZERO：** _len_ = IG、data = IG、RET = 0<br /><br /> **>=255：** _len_ = max8k、data = valid、RET = 0<br /><br /> **<255：** _len_ = <8k、data = valid、RET = 1|  
|**BIGBINARY**|**NULL：** _len_ = 0、data = IG、RET = 1<br /><br /> **ZERO：** _len_ = IG、data = IG、RET = 0<br /><br /> **>=255：** _len_ = max8k、data = valid、RET = 0<br /><br /> **<255：** _len_ = <8k、data = valid、RET = 1|  
|**BIGVARBINARY**|**NULL：** _len_ = 0、data = IG、RET = 1<br /><br /> **ZERO：** _len_ = IG、data = IG、RET = 0<br /><br /> **>=255：** _len_ = max8k、data = valid、RET = 0<br /><br /> **<255：** _len_ = <8k、data = valid、RET = 1|  
|NCHAR|**NULL：** _len_ = 0、data = IG、RET = 1<br /><br /> **ZERO：** _len_ = IG、data = IG、RET = 0<br /><br /> **>=255：** _len_ = max8k、data = valid、RET = 0<br /><br /> **<255：** _len_ = <8k、data = valid、RET = 1|  
|NVARCHAR|**NULL：** _len_ = 0、data = IG、RET = 1<br /><br /> **ZERO：** _len_ = IG、data = IG、RET = 0<br /><br /> **>=255：** _len_ = max8k、data = valid、RET = 0<br /><br /> **<255：** _len_ = <8k、data = valid、RET = 1|  
|**NTEXT**|**NULL：** _len_ = IG、data = IG、RET = 0<br /><br /> **ZERO：** _len_ = IG、data = IG、RET = 0<br /><br /> **>=255：** _len_ = IG、data = IG、RET = 0<br /><br /> **\<255：** _len_ = IG、data = IG、RET = 0|  
|RET = srv_paramset 的傳回值||  
|IG = 值將會被略過||  
|valid = 資料的任何有效指標||  
  
## <a name="remarks"></a>Remarks  
 參數包含了在用戶端和應用程式之間傳遞的資料，其中包含遠端預存程序。 用戶端可以將某些參數指定為傳回參數。 這些傳回參數可包含「開放式資料服務」伺服器應用程式傳回給用戶端的值。 使用傳回參數類似於依參考方式傳遞參數。  
  
 您不能針對未當做傳回參數叫用的參數來設定傳回值。 您可以使用 **srv_paramstatus** 來決定要如何叫用此參數。  
  
 這個函數會設定參數的傳回值，但是實際上並不會將傳回值傳給用戶端。 當呼叫 **srv_senddone** 並有設定狀態旗標 SRV_DONE_FINAL 時，所有傳回參數 (不論是否已經使用 **srv_paramset** 來設定其傳回值) 都會自動傳給用戶端。  
  
 當遠端預存程序呼叫是用參數產生時，該參數可以依名稱或位置 (未命名) 傳遞。 如果遠端預存程序呼叫是藉由一些依名稱傳遞的參數和一些依位置傳遞的參數來進行時，就會發生錯誤。 雖然仍會呼叫 SRV_RPC 處理常式，但是看起來好像沒有參數，而且 **srv_rpcparams** 會傳回 0。  
  
> [!IMPORTANT]  
>  您應該徹底檢閱擴充預存程序的原始程式碼，您也應該先測試編譯過的 DLL，才能將它們安裝在實際執行伺服器上。 如需安全性檢閱和測試的資訊，請參閱此 [Microsoft 網站](https://www.microsoft.com/en-us/msrc?rtc=1)。  
  
## <a name="see-also"></a>另請參閱  
 [srv_paramsetoutput &#40;擴充預存程序 API&#41;](../../relational-databases/extended-stored-procedures-reference/srv-paramsetoutput-extended-stored-procedure-api.md)  
  
  
