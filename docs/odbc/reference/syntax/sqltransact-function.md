---
title: SQLTransact 函式 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLTransact
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLTransact
helpviewer_keywords:
- SQLTransact function [ODBC]
ms.assetid: 496249e0-8eff-4c60-8358-5543bc3ead9c
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 6c96c903b68dee2d1d215804d318d47b4c39a7a5
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "68039503"
---
# <a name="sqltransact-function"></a>SQLTransact 函式
**合規性**  
 導入的版本：ODBC 1.0 標準的合規性：已被取代  
  
 **摘要**  
 在 ODBC *3.x*，ODBC *2.x*函式**SQLTransact**已被取代**SQLEndTran**。 如需詳細資訊，請參閱 < [SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md)。  
  
> [!NOTE]  
>  屬性 SQL_ASYNC_DBC_FUNCTION_ENABLE ODBC 3.8 中所導入，不支援**SQLTransact**。 使用連接控制代碼上的非同步作業的應用程式必須使用**SQLEndTran**。  
  
## <a name="see-also"></a>另請參閱  
 [ODBC API 參考](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC 標頭檔](../../../odbc/reference/install/odbc-header-files.md)
