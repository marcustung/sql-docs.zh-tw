---
title: SQLAllocEnv 對應 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLAllocEnv function [ODBC], mapping
- mapping deprecated functions [ODBC], SQLAllocEnv
ms.assetid: 4bb51845-ee91-4b97-9dd4-2fab977f2aec
author: MightyPen
ms.author: genemi
ms.openlocfilehash: afbd1404cb40408166ecfc59993db7b183ae5ed2
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "68065010"
---
# <a name="sqlallocenv-mapping"></a>SQLAllocEnv 對應
當應用程式呼叫**SQLAllocEnv**透過 ODBC *3.x*驅動程式，會呼叫**SQLAllocEnv**(*phenv*) 會對應到**SQLAllocHandle** ，如下所示：  
  
1.  驅動程式管理員配置環境控制代碼，並傳回應用程式。 此驅動程式管理員會呼叫**SQLSetEnvAttr**設 SQL_OV_ODBC2 SQL_ATTR_ODBC_VERSION 環境屬性。  
  
2.  當應用程式建立與驅動程式的第一個連接時，驅動程式管理員會呼叫  
  
    ```  
    SQLAllocHandle(SQL_HANDLE_ENV, SQL_NULL_HANDLE, OutputHandlePtr)  
    ```  
  
     在 將驅動程式與*OutputHandlePtr*設為*phenv*。
