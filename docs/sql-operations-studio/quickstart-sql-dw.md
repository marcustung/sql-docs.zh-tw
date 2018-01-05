---
title: "快速入門： 連接並查詢 Azure SQL 資料倉儲，使用 SQL 作業 Studio （預覽） |Microsoft 文件"
description: "本快速入門示範如何使用連接到 SQL 資料庫並執行查詢的 SQL 作業 Studio （預覽）"
ms.custom: tools|sos
ms.date: 11/15/2017
ms.prod: sql-non-specified
ms.reviewer: alayu; erickang; sstein
ms.suite: sql
ms.prod_service: sql-tools
ms.component: sos
ms.tgt_pltfrm: 
ms.topic: quickstart
author: yualan
ms.author: alayu
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 4c00912cadb94abccf14779fc6969c3a70b02a7d
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="quickstart-use-includename-sosincludesname-sos-shortmd-to-connect-and-query-data-in-azure-sql-data-warehouse"></a>快速入門： 使用[!INCLUDE[name-sos](../includes/name-sos-short.md)]連接並查詢 Azure SQL 資料倉儲中的資料

本快速入門示範如何使用[!INCLUDE[name-sos](../includes/name-sos-short.md)]連接到 Azure SQL 資料倉儲，並再使用 TRANSACT-SQL 陳述式來建立、 插入和選取的資料。 

## <a name="prerequisites"></a>Prerequisites
若要完成本快速入門，您需要[!INCLUDE[name-sos](../includes/name-sos-short.md)]，和 Azure SQL 資料倉儲。

- [安裝[!INCLUDE[name-sos](../includes/name-sos-short.md)] ](download.md)。

如果您還沒有 SQL 資料倉儲，請參閱[建立 SQL 資料倉儲](https://docs.microsoft.com/en-us/azure/sql-data-warehouse/sql-data-warehouse-get-started-provision)。

請記住伺服器名稱和登入認證 ！


## <a name="connect-to-your-data-warehouse"></a>連接到資料倉儲

使用[!INCLUDE[name-sos](../includes/name-sos-short.md)]來連接到 Azure SQL 資料倉儲伺服器。

1. 第一次執行[!INCLUDE[name-sos](../includes/name-sos-short.md)]**連接**頁面應該會開啟。 如果**連接**頁面未開啟，請按一下**新連線**中的圖示**伺服器**資訊看板：
   
   ![新的連線圖示](media/quickstart-sql-dw/new-connection-icon.png)

2. 本文使用*SQL 登入*，但*Windows 驗證*也支援。 填妥欄位，如下所示：

   | 設定       | 建議值 | 描述 |
   | ------------ | ------------------ | ------------------------------------------------- | 
   | **伺服器名稱** | 完整伺服器名稱 | 此名稱應該像下面這樣： **sqldwsample.database.windows.net** |
   | **驗證** | SQL 登入| 本教學課程中，使用 SQL 驗證。 |
   | **User name** | 伺服器系統管理員帳戶 | 這是您在建立伺服器時指定的帳戶。 |
   | **密碼 (SQL 登入)** | 伺服器系統管理員帳戶的密碼 | 這是您在建立伺服器時指定的密碼。 |
   | **儲存密碼嗎？** | [是] 或 [否] | 如果您不想每次輸入密碼，請選取 [是]。 |
   | **資料庫名稱** | *保留空白* | 要連線之資料庫的名稱。 |
   | **伺服器群組** | 選取<Default> | 如果您建立伺服器群組，您可以設定為特定的伺服器群組。 | 

   ![新的連線圖示](media/quickstart-sql-dw/new-connection-screen.png) 

3. 如果您收到有關防火牆的錯誤，您需要建立防火牆規則。 若要建立防火牆規則，請參閱[防火牆規則](https://docs.microsoft.com/azure/sql-database/sql-database-firewall-configure)。

4. 順利連接伺服器之後會出現在 [物件總管] 中。

## <a name="create-the-tutorial-data-warehouse"></a>建立教學課程資料倉儲
1. 以滑鼠右鍵按一下您的伺服器，請在 [物件總管]，然後選取**新查詢。**

1. 將下列程式碼片段貼到查詢編輯器：

   ```sql
    IF NOT EXISTS (
       SELECT name
       FROM sys.databases
       WHERE name = N'TutorialDB'
    )
    CREATE DATABASE [TutorialDB] (EDITION = 'datawarehouse', SERVICE_OBJECTIVE='DW100');
    GO  
    
    ALTER DATABASE [TutorialDB] SET QUERY_STORE=ON
    GO
   ```

1. 若要執行查詢時，按一下**執行**。

## <a name="create-a-table"></a>建立資料表

查詢編輯器仍然會連線到*主要*資料庫，但我們想要建立的資料表中*TutorialDB*資料庫。 

1. 變更的連接內容**TutorialDB**:

   ![變更內容](media/quickstart-sql-database/change-context.png)


1. 將下列程式碼片段貼到查詢編輯器：

   ```sql
   -- Create a new table called 'Customers' in schema 'dbo'
   -- Drop the table if it already exists
   IF OBJECT_ID('dbo.Customers', 'U') IS NOT NULL
   DROP TABLE dbo.Customers
   GO
   -- Create the table in the specified schema
   CREATE TABLE dbo.Customers
   (
      CustomerId        INT     NOT NULL,
      Name      [NVARCHAR](50)  NOT NULL,
      Location  [NVARCHAR](50)  NOT NULL,
      Email     [NVARCHAR](50)  NOT NULL
   );
   GO
   ```

1. 若要執行查詢時，按一下**執行**。

## <a name="insert-rows"></a>插入資料列

1. 將下列程式碼片段貼到查詢編輯器：

   ```sql
   -- Insert rows into table 'Customers'
   INSERT INTO dbo.Customers
      ([CustomerId],[Name],[Location],[Email])
      SELECT 1, N'Orlando',N'Australia', N'' UNION ALL
      SELECT 2, N'Keith', N'India', N'keith0@adventure-works.com' UNION ALL
      SELECT 3, N'Donna', N'Germany', N'donna0@adventure-works.com' UNION ALL
      SELECT 4, N'Janet', N'United States', N'janet1@adventure-works.com'
   ```

1. 若要執行查詢時，按一下**執行**。

## <a name="view-the-result"></a>檢視結果
1. 將下列程式碼片段貼到查詢編輯器：

   ```sql
   -- Select rows from table 'Customers'
   SELECT * FROM dbo.Customers;
   ```

1. 若要執行查詢時，按一下**執行**。

   ![選取 [結果]](media/quickstart-sql-dw/select-results.png)


## <a name="clean-up-resources"></a>清除資源

在此集合中的其他文章是根據本快速入門。 如果您打算在繼續處理後續的快速入門，請勿清除本快速入門中建立的資源。 如果您不打算繼續，請使用下列步驟刪除本快速入門在 Azure 入口網站所建立的資源。
刪除您不再需要的資源群組來清除資源。 如需詳細資訊，請參閱[清除資源](https://docs.microsoft.com/en-us/azure/sql-database/sql-database-get-started-portal#clean-up-resources)。


## <a name="next-steps"></a>後續步驟

現在您已成功連接到 Azure SQL 資料倉儲，並執行查詢，試試[教學課程中的程式碼編輯器](tutorial-sql-editor.md)。