---
title: getBytes 方法 (SQLServerResultSet) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.getBytes
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: d16a0aea-6144-4fcb-bcbc-5d7daa36d327
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 58a0420fd28ff86ab59ac0b20acf9803058bd2b0
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 06/07/2019
ms.locfileid: "66803986"
---
# <a name="getbytes-method-sqlserverresultset"></a>getBytes 方法 (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  使用 Java 程式語言，擷取這個 [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) 物件中目前資料列中所指定資料行的值來當作 **byte** 陣列。  
  
## <a name="overload-list"></a>多載清單  
  
|[屬性]|Description|  
|----------|-----------------|  
|[getBytes (int)](../../../connect/jdbc/reference/getbytes-method-int-sqlserverresultset.md)|使用 Java 程式設計語言，從這個 [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) 物件目前資料列中擷取指定的資料行索引值來當作 **byte** 陣列。|  
|[getBytes (java.lang.String)](../../../connect/jdbc/reference/getbytes-method-java-lang-string-sqlserverresultset.md)|使用 Java 程式設計語言，擷取這個 [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) 物件中目前資料列中所指定資料行名稱的值來當作 **byte** 陣列。|  
  
## <a name="remarks"></a>Remarks  
 在舊版的 [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] 中，您可以使用 SQLServerResultSet.getBytes 來轉換位元組陣列與 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 資料類型 **date**、**time**、**datetime2** 或 **datetimeoffset** 之間的值。 現在，搭配這些資料類型使用這個方法將會引發例外狀況，指出不支援轉換。  
  
## <a name="see-also"></a>另請參閱  
 [SQLServerResultSet 成員](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet 類別](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
