---
title: 使用查詢通知 |Microsoft Docs
description: 使用中 OLE DB Driver for SQL Server 的查詢通知
ms.custom: ''
ms.date: 06/12/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- data access [OLE DB Driver for SQL Server], query notifications
- rowsets [SQL Server], notifications
- OLE DB Driver for SQL Server, query notifications
- notifications [OLE DB Driver for SQL Server]
- query notifications [SQL Server], OLE DB Driver for SQL Server
- canceling rowset changes
- IRowsetNotify interface
- MSOLEDBSQL, query notifications
- OLE DB Driver for SQL Server, query notifications
- consumer notification for rowset changes [OLE DB Driver for SQL Server]
author: pmasl
ms.author: pelopes
manager: jroth
ms.openlocfilehash: 20860d018e8971089ee1eb80ec0303bdc63ef211
ms.sourcegitcommit: 1bbbbb8686745a520543ac26c4d4f6abe1b167ea
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 06/18/2019
ms.locfileid: "67208350"
---
# <a name="working-with-query-notifications"></a>使用查詢通知

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

查詢通知已導入[!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]和 OLE DB Driver for SQL Server。 查詢通知是根據 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] 中引進的 Service Broker 基礎結構而建置，可讓應用程式在資料變更時收到通知。 此功能對於從資料庫中提供資訊快取的應用程式 (如 Web 應用程式)，及需要在來源資料變更時收到通知的應用程式來說非常有用。

當查詢的基礎資料變更時，查詢通知可讓您在指定的逾時期間要求通知。 通知的要求會指定通知選項，其中包含服務名稱、訊息文字和伺服器的逾時值。 通知會透過 Service Broker 佇列傳遞，應用程式會輪詢此佇列以查看是否有可用的通知。

查詢通知選項字串的語法為：

`service=<service-name>[;(local database=<database> | broker instance=<broker instance>)]`

 例如：

`service=mySSBService;local database=mydb`

通知訂閱的存留時間會超過初始化這些訂閱的程序，因為應用程式可以建立通知訂閱，然後再加以結束。 訂閱仍會保持有效，而如果資料在建立訂閱時所指定的逾時期間內變更，就會發生通知。 通知會由執行的查詢、通知選項和訊息文字來識別，並且可藉由將逾時值設定為零而加以取消。

通知只會傳送一次。 如果要持續接到資料變更的通知，必須在處理過每個通知之後重新執行查詢，以建立新的訂閱。

OLE DB Driver for SQL Server 應用程式接收通知時，一般是藉由使用 [!INCLUDE[tsql](../../../includes/tsql-md.md)] [RECEIVE](../../../t-sql/statements/receive-transact-sql.md) 命令從通知選項所指定之服務的相關佇列讀取通知。

> [!NOTE]
> 您必須在需要通知的查詢中限定資料表名稱，例如 `dbo.myTable`。 資料表名稱必須使用兩部分的名稱來加以限定。 如果使用三或四部份的名稱，則訂閱無效。

通知基礎結構是依照 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] 中引進的佇列功能而建立。 一般而言，在伺服器所產生的通知會透過這些佇列傳送，以供稍後處理。

若要使用查詢通知，伺服器上必須有佇列和服務。 這些項目可以使用類似下列的 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 來建立：

```sql
CREATE QUEUE myQueue
CREATE SERVICE myService ON QUEUE myQueue
([https://schemas.microsoft.com/SQL/Notifications/PostQueryNotification])
```

> [!NOTE]
> 服務必須使用預先定義的合約 (如上所示)。

## <a name="ole-db-driver-for-sql-server"></a>OLE DB Driver for SQL Server

OLE DB Driver for SQL Server 支援在資料列集修改時取用者通知。 使用者會在資料列集修改的每個階段以及嘗試進行任何變更時收到通知。

> [!NOTE]
> 使用 **ICommand::Execute** 將通知查詢傳遞至伺服器，是使用 OLE DB Driver for SQL Server 訂閱查詢通知的唯一有效方法。

### <a name="the-dbpropsetsqlserverrowset-property-set"></a>DBPROPSET_SQLSERVERROWSET 屬性集

為了透過 OLE DB 支援查詢通知，OLE DB Driver for SQL Server 會將下列新屬性加入至 DBPROPSET_SQLSERVERROWSET 屬性集。

|[屬性]|類型|Description|
|----------|----------|-----------------|
|SSPROP_QP_NOTIFICATION_TIMEOUT|VT_UI4|查詢通知要維持使用中的秒數。<br /><br /> 預設值為 432,000 秒 (5 天)。 最小值為 1 秒，最大值為 2^31-1 秒。|
|SSPROP_QP_NOTIFICATION_MSGTEXT|VT_BSTR|通知的訊息文字。 這是使用者定義的，而且沒有預先定義的格式。<br /><br /> 根據預設，字串是空的。 您可以使用 1-2000 個字元指定訊息。|
|SSPROP_QP_NOTIFICATION_OPTIONS|VT_BSTR|查詢通知選項。 這些是使用 *name*=*value* 語法在字串中指定。 使用者負責建立此服務以及從佇列讀取通知。<br /><br /> 預設為空字串。|

無論陳述式是以使用者交易或自動認可執行，或者陳述式在其中執行的交易是否已經認可或回復，系統閱永遠都會認可通知訂閱。 伺服器通知會在發生下列任何無效通知條件時觸發：基礎資料或結構描述變更，或達到逾時期限 (視何者為先)。 通知註冊會在觸發之後立刻刪除。 因此在接到通知後，應用程式必須再進行一次訂閱，才能接到進一步的更新。

其他的連接或執行緒可以檢查目的地佇列是否有通知。 例如：

```sql
WAITFOR (RECEIVE * FROM MyQueue); -- Where MyQueue is the queue name.
```

> [!NOTE]
> SELECT * 並不會從佇列刪除項目，但 RECEIVE \* FROM 會這麼做。 如果佇列是空的，這麼做會使伺服器延滯。 如果呼叫時有佇列項目，則這些項目會立刻傳回；否則呼叫會等到佇列項目建立後才進行。

```sql
RECEIVE * FROM MyQueue
```

如果佇列是空的，這個陳述式會立刻傳回空的結果集；否則會傳回所有的佇列通知。

如果 SSPROP_QP_NOTIFICATION_MSGTEXT 和 SSPROP_QP_NOTIFICATION_OPTIONS 非 NULL 且不是空的，則每次執行命令時，都會將包含以上定義的三個屬性的查詢通知 TDS 標頭傳送到伺服器。 如果其中任一項為 Null (或是空的)，則該標頭不會傳送且會引發 DB_E_ERRORSOCCURRED (如果這兩個屬性都標示為選擇性的，則會引發 DB_S_ERRORSOCCURRED)，而且狀態值會設定為 DBPROPSTATUS_BADVALUE。 在執行/準備時會進行驗證。 同樣地，當針對 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] 之前的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 版本連接設定查詢通知屬性時，會引發 DB_S_ERRORSOCCURED。 狀態值在這種情況下是 DBPROPSTATUS_NOTSUPPORTED。

初始化訂閱並不保證後續的訊息能成功傳遞。 此外，系統也不會對所指定服務名稱的有效性進行檢查。

> [!NOTE]
> 陳述式的準備永遠都不會初始化訂閱，只有陳述式的執行才會造成初始化，此外使用 OLE DB 核心服務也不會影響查詢通知。

如需有關 DBPROPSET_SQLSERVERROWSET 屬性集的詳細資訊，請參閱 <<c0> [ 資料列集屬性和行為](../../oledb/ole-db-rowsets/rowset-properties-and-behaviors.md)。

## <a name="see-also"></a>另請參閱

[OLE DB Driver for SQL Server 功能](../../oledb/features/oledb-driver-for-sql-server-features.md)
