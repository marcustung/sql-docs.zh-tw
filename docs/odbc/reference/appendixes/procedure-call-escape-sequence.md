---
title: 程序呼叫逸出序列 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- escape sequences [ODBC], procedure call
- procedure call escape sequence [ODBC]
- ODBC escape sequences [ODBC], procedure call
ms.assetid: 269fbab0-e5f2-4a98-86c0-2d7b647acaae
author: MightyPen
ms.author: genemi
ms.openlocfilehash: aa936eb9f8ef3328945d4ece63fb36432a5fd618
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "68100596"
---
# <a name="procedure-call-escape-sequence"></a>程序呼叫逸出序列
ODBC 會將逸出序列用於程序呼叫。 此逸出序列的語法如下所示：  
  
 **{** [？ =]**呼叫** *程序名稱*[ **(** [*參數*] [，[*參數*]]... **)** ] **}**  
  
 在 backus-naur form，BNF 標記法中，語法如下所示：  
  
 *ODBC 程序逸出*:: =  
  
 &#124;*ODBC-esc-啟動器*[？ =] 呼叫*程序 ODBC esc 鍵結束字元*  
  
 *procedure* ::= *procedure-name* &#124; *procedure-name* (*procedure-parameter-list*)  
  
 *程序識別項*:: =*使用者定義名稱*  
  
 *程序名稱*:: =*程序識別項*  
  
 &#124;*擁有者名稱*。*程序識別項*  
  
 &#124;*目錄名稱的目錄分隔符號* *程序識別項*  
  
 &#124;*目錄名稱的目錄分隔符號* [*擁有者名稱*]。*程序識別項*  
  
 （第三個的語法是資料來源不支援擁有者時，才有效）。  
  
 *owner-name* ::= *user-defined-name*  
  
 *catalog-name* ::= *user-defined-name*  
  
 *catalog-separator* ::= {*implementation-defined*}  
  
 (經由傳回的目錄分隔符號**SQLGetInfo** SQL_CATALOG_NAME_SEPARATOR 資訊選項。)  
  
 *procedure-parameter-list* ::= *procedure-parameter*  
  
 &#124;*程序參數*，*程序參數清單*  
  
 *procedure-parameter* ::= *dynamic-parameter* &#124; *literal* &#124; *empty-string*  
  
 *空字串*:: =  
  
 *起始 esc ODBC 端*:: = {  
  
 *ODBC esc 鍵結束字元*:: =}  
  
 （程序參數是否為空字串，此程序使用的預設值為該參數。）  
  
 若要判斷資料來源支援程序及驅動程式支援 ODBC 的程序引動過程語法，應用程式可以呼叫**SQLGetInfo** SQL_PROCEDURES 資訊類型。
