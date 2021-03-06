---
title: SQL Server 登入對話方塊 (OLE DB) |Microsoft Docs
description: 使用 SQL Server 登入對話方塊
ms.custom: ''
ms.date: 01/21/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
ms.author: v-beaziz
author: bazizi
ms.openlocfilehash: 4735ead33dc7c3a6d633e3b23ff1da97eeae4962
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: zh-TW
ms.lasthandoff: 06/15/2019
ms.locfileid: "62853260"
---
# <a name="sql-server-login-dialog-box"></a>SQL Server 登入對話方塊
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

當您嘗試連線時未指定足夠的資訊時，OLE DB 驅動程式會顯示**SQL Server 登入** 對話方塊。

> [!NOTE]  
> SQL Server 登入對話方塊，提示的行為會受到`DBPROP_INIT_PROMPT`初始化屬性。 如需詳細資訊，請參閱：
> - [初始化和授權屬性](../ole-db-data-source-objects/initialization-and-authorization-properties.md)
> - [OLE DB 程式設計人員指南](https://go.microsoft.com/fwlink/?linkid=2067702)

![SQL Server 登入 對話方塊的螢幕擷取畫面](../media/sql-server-login-dialog.png)

## <a name="options"></a>選項。
|選項|Description|
|---   |---        |
|[伺服器]|您的網路上的 SQL Server 執行個體名稱。 從清單中選取伺服器或執行個體名稱，或在 [伺服器]  方塊中鍵入伺服器或執行個體名稱。 (選擇性) 您可以在用戶端電腦上使用 [SQL Server 設定管理員]  建立伺服器別名，並在 [伺服器]  方塊中鍵入該名稱。 <br/><br/>如果您使用的電腦與 SQL Server 的相同，則可輸入 "(local)"。 接著，即使執行的是非網路版的 SQL Server，您也可連接到 SQL Server 的本機執行個體。<br/><br/>如需不同類型的網路的伺服器名稱的詳細資訊，請參閱[SQL Server 安裝](https://go.microsoft.com/fwlink/?linkid=2067541)。|
|驗證模式|您可以從下拉式清單中選取下列的驗證選項：<br/><ul><li>`Windows Authentication:` 使用目前登入使用者的 Windows 帳戶認證的 SQL Server 驗證。</li><li>`SQL Server Authentication:` 使用登入識別碼和密碼的 SQL Server 驗證。</li><li>`Active Directory - Integrated:` 使用目前登入使用者的 Windows 帳戶認證的整合式的驗證。</li><li>`Active Directory - Password:` 使用登入識別碼和密碼的 active Directory 驗證。</li></ul>|
|伺服器 SPN|如果您使用了信任連接，就可以指定伺服器的服務主要名稱 (SPN)。|
|登入識別碼|指定要用於連線的登入識別碼。 登入識別碼 文字方塊中才會啟用`Authentication Mode`設定為`SQL Server Authentication`或`Active Directory - Password`。|
|[密碼]|指定用於連接的密碼。 [密碼] 文字方塊中才會啟用`Authentication Mode`設定為`SQL Server Authentication`或`Active Directory - Password`。|
|選項。|顯示或隱藏 [選項]  群組。 如果 [伺服器]  具有值，即會啟用 [選項]  按鈕。|
|變更密碼|有選取時，可讓**新的密碼**並**確認新密碼**文字方塊。|
|新密碼|指定新的密碼。|
|確認新密碼|再次指定新密碼，以進行確認。|
|[資料庫]|選取或輸入用於連線的預設資料庫。 此設定會覆寫伺服器上指定用於登入的預設資料庫。 如果未指定任何資料庫，則連接會使用伺服器上指定用於登入的預設資料庫。|
|鏡像伺服器|指定要鏡像處理之資料庫的容錯移轉夥伴名稱。|
|鏡像 SPN|(選擇性) 您可以指定鏡像伺服器的 SPN。 鏡像伺服器的 SPN 會用於用戶端與伺服器之間的相互驗證。|
|語言|指定要用於 SQL Server 系統訊息的國家/地區語言。 執行 SQL Server 的電腦必須安裝此語言。 此設定會覆寫伺服器上指定用於登入的預設語言。 如果未指定任何語言，則連接會使用伺服器上指定用於登入的預設語言。|
|Application Name|指定要針對 **sys.sysprocesses** 中的此連線，儲存在資料列上的 **program_name** 資料行中的應用程式名稱。|
|工作站 ID|指定要針對 **sys.sysprocesses** 中的此連線，儲存在資料列上的 **hostname** 資料行中的工作站識別碼。|
|使用高度加密資料|有選取時，會透過連線傳遞的資料將會加密。|
|信任伺服器憑證|有選取時，將會驗證伺服器的憑證。 伺服器的憑證必須具有伺服器的正確主機名稱，且受信任的憑證授權單位所核發。|

> [!NOTE]  
> 使用時`Windows Authentication`或`SQL Server Authentication`模式中，**信任伺服器憑證**會被視為只有當**使用強式加密資料**啟用選項。

## <a name="next-steps"></a>後續步驟
- [向 Azure Active Directory](../features/using-azure-active-directory.md)使用 OLE DB 驅動程式。
- 使用的設定連線資訊[通用資料連結 (UDL)](data-link-pages.md)。