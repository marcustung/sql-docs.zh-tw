---
title: "建立變數值檔案 (AccessToSQL) |Microsoft 文件"
ms.prod: sql-non-specified
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 808595c3-8ef1-40bd-a93e-5cf237950e08
caps.latest.revision: 15
author: sabotta
ms.author: carlasab
manager: lonnyb
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 2ebc00ea1b5fc7eb9ca2383d8887b522f59428d1
ms.contentlocale: zh-tw
ms.lasthandoff: 08/02/2017

---
# <a name="creating-variable-value-files-accesstosql"></a>建立變數值檔案 (AccessToSQL)
變數值的檔案是 XML 檔案中所包含的參數值經常變更從一部伺服器移轉到另一個來源或目的地伺服器名稱類似命令。 大量的資料庫移轉發生時，多個變數的檔案，以儲存每個來源伺服器的值時會建立及參考的主版的指令碼檔案中**– v**在命令列參數。 這有助於維護幾個指令碼檔案中的多個變數的檔案中的變數值的靜態值。  
  
> [!NOTE]  
> 1.  變數名稱會做為前置詞和後置字元為 $ （美元） 符號。 如果變數不會指派變數值檔案中的值，您會導致一主控台執行程序的指令碼檔剖析期間發生錯誤。  
> 2.  The escape character for **$** is **$$**. 如果變數或靜態值的參數值包含 **$**  （美元） 符號，然後 **$$** 必須指定以將其視為一個字元，而不是變數。  
> 3.  為了可維護性，變數可以宣告內`‘variable-group’`元素的邏輯隔離的使用者定義變數。  使用這個項目不是強制性。  
  
**範例:**  
  
**範例 1:**  
  
```xml  
<!--Sample of variable value file commands-->  
  
<variables>  
  
  <variable-group name="ProjectSpecs">  
  
    <variable name="$type$" value="MyProject"/>  
  
    <variable name="$project_folder$" value=".\$project_name$"/>  
  
    <variable name="$project_name$" value="$type$ConsoleProject"/>  
  
    <variable name="$project_overwrite$" value="true"/>  
  
    <variable name="$project_type$" value="sql-server-2008"/>  
  
  </variable-group>  
  
</variables>  
```  
**範例 2:**  
  
```xml  
<!--Sample of variable value file commands-->  
  
<variables>  
  
  <variable-group name="SQLServerParams">  
  
    <variable-group name="SqlServerConnectionParams">  
  
      <variable name="$TargetServerName$" value="xxx"/>  
  
      <variable name="$TargetDB$" value="xxx"/>  
  
      <variable name="$TargetUserName$" value="xxx"/>  
  
      <variable name="$TargetPassword$" value="xxx"/>  
  
      <variable name="$TargetIsTrusted$" value="xxx"/>  
  
      <variable name="$TrustedConnection$" value="xxx"/>  
  
    </variable-group>  
  
    <variable-group name="SqlServerObjectParams">  
  
      <variable name="$ObjectName1$" value="TestTable1"/>  
  
      <variable name="$ObjectName2$" value="TestProc1"/>  
  
    </variable-group>  
  
  </variable-group>  
  
</variables>  
```  
  
## <a name="variable-value-file-validation"></a>變數值的檔案驗證  
使用者可以輕鬆地驗證其變數值檔案對結構描述定義檔**ConsoleScriptVariablesSchema.xsd**可用 '結構描述' 資料夾中。  
  
## <a name="next-step"></a>下一個步驟  
在操作主控台的下一個步驟是[建立伺服器連接檔案 &#40;AccessToSQL &#41;](../../ssma/access/creating-the-server-connection-files-accesstosql.md)  
  
## <a name="see-also"></a>另請參閱  
[建立伺服器連接檔案 (Access)](http://msdn.microsoft.com/en-us/829153be-aa8e-4162-87e8-69882feecf19)  
  
