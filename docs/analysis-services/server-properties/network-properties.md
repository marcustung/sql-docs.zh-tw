---
title: Analysis Services 的網路屬性 |Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: ''
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 3b9bb77c5139b299a25fbd75bc30a58790ee0c30
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/15/2019
ms.locfileid: "68207951"
---
# <a name="network-properties"></a>網路屬性
[!INCLUDE[ssas-appliesto-sqlas-all-aas](../../includes/ssas-appliesto-sqlas-all-aas.md)]

  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 支援下表列出的伺服器屬性。 如需其他伺服器屬性以及如何設定伺服器屬性的詳細資訊，請參閱 [Analysis Services 中的伺服器屬性](../../analysis-services/server-properties/server-properties-in-analysis-services.md)。  
  
 **適用於：** 多維度與表格式伺服器模式  
  
## <a name="general"></a>一般  
 **ListenOnlyOnLocalConnections**  
 此為布林值屬性，識別是否僅在本機連接上接聽，例如 localhost。  
  
## <a name="listener"></a>接聽程式  
 **IPV4Support**  
 此為帶正負號的 32 位元整數屬性，定義 IPv4 通訊協定的支援。 此屬性的值為下表列出的值之一：  
  
|值|描述|  
|-----------|-----------------|  
|*0*|IPv4 已停用；用戶端無法連接。|  
|*1*|(預設值) 需要有 IPv4；如果伺服器無法接聽 IPv4 將無法啟動。|  
|*2*|IPv4 是選擇性的；伺服器會嘗試接聽 IPv4，但即使無法接聽仍會啟動。|  
  
 **IPV6Support**  
 此為帶正負號的 32 位元整數屬性，定義 IPv6 通訊協定的支援。 此屬性的值為下表列出的值之一：  
  
|值|描述|  
|-----------|-----------------|  
|*0*|IPv6 已停用；用戶端無法連接。|  
|*1*|(預設值) 需要有 IPv6；如果伺服器無法接聽 IPv6 將無法啟動。|  
|*2*|IPv6 是選擇性的；伺服器會嘗試接聽 IPv6，但即使無法接聽仍會啟動。|  
  
 **MaxAllowedRequestSize**  
 此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。  
  
 **RequestSizeThreshold**  
 此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。  
  
 **ServerReceiveTimeout**  
 此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。  
  
 **ServerSendTimeout**  
 此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。  
  
## <a name="requests"></a>要求  
 **EnableBinaryXML**  
 此為布林值屬性，指定伺服器是否會辨識要求的二進位 XML 格式。  
  
 **EnableCompression**  
 此為布林值屬性，指定是否針對要求啟用壓縮。  
  
## <a name="responses"></a>Responses  
 **CompressionLevel**  
 此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。  
  
 **EnableBinaryXML**  
 此為布林值屬性，指定伺服器是否啟用二進位 XML 回應。  
  
 **EnableCompression**  
 此為布林值屬性，指定是否針對用戶端要求的回應啟用壓縮。  
  
## <a name="tcp"></a>TCP  
 **InitialConnectTimeout**  
 此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。  
  
 **MaxCompletedReceiveCount**  
 此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。  
  
 **MaxPendingAcceptExCount**  
 此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。  
  
 **MaxPendingReceiveCount**  
 此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。  
  
 **MaxPendingSendCount**  
 此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。  
  
 **MinPendingAcceptExCount**  
 此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。  
  
 **MinPendingReceiveCount**  
 此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。  
  
 **ScatterReceiveMultiplier**  
 此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。  
  
 **SocketOptions\ DisableNonblockingMode**  
 此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。  
  
 **SocketOptions\ EnableLingerOnClose**  
 此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。  
  
 **SocketOptions\EnableNagleAlgorithm**  
 此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。  
  
 **SocketOptions\ LingerTimeout**  
 此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。  
  
 **SocketOptions\ ReceiveBufferSize**  
 此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。  
  
 **SocketOptions\ SendBufferSize**  
 此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。  
  
## <a name="see-also"></a>另請參閱  
 [Analysis Services 中的伺服器屬性](../../analysis-services/server-properties/server-properties-in-analysis-services.md)   
 [判斷 Analysis Services 執行個體的伺服器模式](../../analysis-services/instances/determine-the-server-mode-of-an-analysis-services-instance.md)  
  
  
