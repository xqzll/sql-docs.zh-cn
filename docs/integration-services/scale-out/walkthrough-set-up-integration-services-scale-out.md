---
title: 演练：安装 SQL Server Integration Services Scale Out | Microsoft Docs
description: 本文将引导你完成 SSIS Scale Out 的设置和配置
ms.custom: performance
ms.date: 12/13/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: maghan
ms.technology: integration-services
ms.topic: conceptual
author: haoqian
ms.author: haoqian
manager: craigg
ms.openlocfilehash: e566c31f03284660456f7a96f2d19adc32bf4404
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "66012938"
---
# <a name="walkthrough-set-up-integration-services-ssis-scale-out"></a>演练：安装 Integration Services (SSIS) Scale Out

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


通过完成以下任务，设置 [!INCLUDE[ssISnoversion_md](../../includes/ssisnoversion-md.md)] (SSIS) Scale Out。 

> [!TIP]
> 如果是在一台计算机上安装 Scale Out，请同时安装 Scale Out Master 和 Scale Out Worker 功能。 同时安装这两种功能时，将自动生成端点以连接到 Scale Out Master。 

* [安装 Scale Out Master](#InstallMaster)

* [安装 Scale Out Worker](#InstallWorker)

* [安装 Scale Out Worker 客户端证书](#InstallCert)

* [打开防火墙端口](#Firewall)

* [启动 SQL Server Scale Out Master 和 Worker 服务](#Start)

* [启用 Scale Out Master](#EnableMaster)

* [启用 SQL Server 身份验证模式](#EnableAuth)

* [启用 Scale Out Worker](#EnableWorker)

## <a name="InstallMaster"></a> 安装 Scale Out Master

要设置 Scale Out Master，必须在设置 [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] 时，安装数据库引擎服务、[!INCLUDE[ssISnoversion_md](../../includes/ssisnoversion-md.md)] 及 SSIS 的 Scale Out Master 功能。 

要了解如何设置数据库引擎和 [!INCLUDE[ssISnoversion_md](../../includes/ssisnoversion-md.md)]，请参阅[安装 SQL Server 数据库引擎](../../database-engine/install-windows/install-sql-server-database-engine.md)和[安装 Integration Services](../install-windows/install-integration-services.md)。

> [!NOTE]
> 要将默认 SQL Server 身份验证帐户用于 Scale Out 日志记录，安装数据库引擎期间，请在“数据库引擎配置”页上选择“混合模式”作为身份验证模式  。 请参阅[更改 Scale Out 日志记录的帐户](change-logdb-account.md)，了解详细信息。

要安装 Scale Out Master 功能，请使用 [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] 安装向导或命令提示符。

### <a name="install-scale-out-master-with-the-sql-server-installation-wizard"></a>使用 SQL Server 安装向导安装 Scale Out Master
1.  在“功能选择”页上，选择 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 下列出的“Scale Out Master”   。   
  
    ![功能选择 Master](media/feature-select-master.PNG)
  
2.  在“服务器配置”  页上，选择要运行“SQL Server Integration Services Scale Out Master 服务”  的帐户，然后选择“启动类型”  。  
    ![服务器配置](media/server-config.PNG)

3.  在“Integration Services Scale Out Master 配置”  页上，指定 Scale Out Master 用于与 Scale Out Worker 进行通信的端口号。 默认端口号为 8391。  

    ![Master Config](media/master-config.PNG "Master Config")

4.  通过执行以下操作之一，指定用于保护 Scale Out Master 与 Scale Out Worker 之间的通信的 SSL 证书。
    * 单击“创建新的 SSL 证书”，使安装进程创建默认的自签名 SSL 证书  。  默认证书安装在本地计算机中受信任的根证书颁发机构之下。 可在此证书中指定 CN。 CN 中应包含主终结点的主机名。 默认包含主节点的计算机名称和 IP。
    * 单击“使用现有的 SSL 证书”，然后单击“浏览”，在本地计算机上选择现有的 SSL 证书   。 文本框中显示证书的指纹。 单击“浏览”  ，显示存储在本地计算机中受信任的根证书颁发机构中的证书。 必须选择存储在此处的证书。       

    ![Master Config 2](media/master-config-2.PNG "Master Config 2")
  
5.  完成 [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] 安装向导。

### <a name="install-scale-out-master-from-the-command-prompt"></a>从命令提示符安装 Scale Out Master

按照 [从命令提示符安装 SQL Server](../../database-engine/install-windows/install-sql-server-2016-from-the-command-prompt.md)中的说明操作。 执行以下操作，为 Scale Out Master 设置参数：
 
1.  将 `IS_Master` 添加到参数 `/FEATURES`

2.  通过指定下列参数及其值来配置 Scale Out Master：
    -   `/ISMASTERSVCACCOUNT`
    -   `/ISMASTERSVCPASSWORD`
    -   `/ISMASTERSVCSTARTUPTYPE`
    -   `/ISMASTERSVCPORT`
    -   `/ISMasterSVCSSLCertCN`（可选）
    -   `/ISMASTERSVCTHUMBPRINT`（可选）

    > [!NOTE]
    > 如果 Scale Out Master 未与数据库引擎一起安装，且数据库引擎实例为命名实例，则须于安装后在 Scale Out Master 服务配置文件中配置 `SqlServerName`。 有关详细信息，请参阅 [Scale Out Master](integration-services-ssis-scale-out-master.md)。

## <a name="InstallWorker"></a> 安装 Scale Out Worker
 
要设置 Scale Out Worker，必须在 [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] 安装程序中安装 [!INCLUDE[ssISnoversion_md](../../includes/ssisnoversion-md.md)] 及其 Scale Out Worker 功能。

要安装 Scale Out Worker 功能，请使用 [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] 安装向导或命令提示符。

### <a name="install-scale-out-worker-with-the-sql-server-installation-wizard"></a>使用 SQL Server 安装向导安装 Scale Out Worker

1.  在“功能选择”页上，选择 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 下列出的“Scale Out Worker”   。

    ![功能选择 Worker](media/feature-select-worker.PNG)

2.  在“服务器配置”  页上，选择要运行“SQL Server Integration Services Scale Out Worker 服务”  的帐户，然后选择“启动类型”  。

    ![Server Config 2](media/server-config-2.PNG "Server Config 2")

3.  在“Integration Services Scale Out Worker 配置”  页上，指定端点以连接到 Scale Out Master。 

    - 对于单一计算机环境，同时安装 Scale Out Master 和 Scale Out Worker 时，会自动生成终结点  。 

    - 对于多台计算机环境，终结点包括安装了 Scale Out Master 的计算机的名称或 IP 以及 Scale Out Master 安装期间指定的端口号  。
   
    ![Worker Config 1](media/worker-config.PNG "Worker Config 1")    

    > [!NOTE]
    > 此处也可跳过 Worker 配置，并在安装后使用 [Scale Out Manager](integration-services-ssis-scale-out-manager.md) 将 Scale Out Worker 与 Scale Out Master 关联起来。

4. 对于多台计算机环境，需指定用于验证 Scale Out Master 的客户端 SSL 证书  。 对于单一计算机环境，则无需指定客户端 SSL 证书  。 
  
    单击“浏览”  ，查找证书文件 (*.cer)。 要使用默认 SSL 证书，请在安装了 Scale Out Master 的计算机上找到 `\<drive\>:\Program Files\Microsoft SQL Server\140\DTS\Binn`，并在其下选择 `SSISScaleOutMaster.cer` 文件。   

    ![Worker Config 2](media/worker-config-2.PNG "Worker Config 2")

    > [!NOTE]
    > 如果 Scale Out Master 使用的 SSL 证书为自签名证书，则需要在具有 Scale Out Worker 的计算机上安装相应的客户端 SSL 证书。 如果在“Integration Services Scale Out Worker 配置”页上提供了客户端 SSL 证书的文件路径，证书将自动安装；否则，稍后必须手动安装证书  。 
     
5. 完成 [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] 安装向导。

### <a name="install-scale-out-worker-from-the-command-prompt"></a>从命令提示符安装 Scale Out Worker

按照 [从命令提示符安装 SQL Server](../../database-engine/install-windows/install-sql-server-2016-from-the-command-prompt.md)中的说明操作。 执行以下操作，为 Scale Out Worker 设置参数：

1.  将 IS_Worker 添加到参数 `/FEATURES`。

2. 通过指定下列参数及其值来配置 Scale Out Worker：
    -   `/ISWORKERSVCACCOUNT`
    -   `/ISWORKERSVCPASSWORD`
    -   `/ISWORKERSVCSTARTUPTYPE`
    -   `/ISWORKERSVCMASTER`（可选）
    -   `/ISWORKERSVCCERT`（可选）
 
## <a name="InstallCert"></a> 安装 Scale Out Worker 客户端证书

在 Scale Out Worker 安装期间，将在计算机上自动创建并安装辅助角色证书。 此外，将在 `\<drive\>:\Program Files\Microsoft SQL Server\140\DTS\Binn` 之下安装相应的客户端证书 SSISScaleOutWorker.cer。 对于用于对 Scale Out Worker 进行身份验证的 Scale Out Master，必须将此客户端证书添加到具有 Scale Out Master 的本地计算机的根存储中。
  
要将客户端证书添加到根存储，可双击 .cer 文件，然后单击“证书”对话框中的“安装证书”  。 这将打开“证书导入向导”  。  

## <a name="Firewall"></a> 打开防火墙端口

在 Scale Out Master 计算机上的 Windows 防火墙中，打开在 Scale Out Master 安装期间指定的端口和 SQL Server 端口（默认为 1433）。

> [!Note]
> 打开防火墙端口之后，还需重启 Scale Out Worker 服务。
    
## <a name="Start"></a>启动 SQL Server Scale Out Master 和 Worker 服务

如果在安装期间未将服务的启动类型设置为“自动”，请启动以下服务  ：

-   SQL Server Integration Services Scale Out Master 14.0 (SSISScaleOutMaster140)

-   SQL Server Integration Services Scale Out Worker 14.0 (SSISScaleOutWorker140)

## <a name="EnableMaster"></a> 启用 Scale Out Master

在 [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio_md](../../includes/ssmanstudio-md.md)] 中创建 SSISDB 目录时，请在“创建目录”对话框中，选择“启用此服务器作为 SSIS Scale Out Master”   。

创建目录后，可使用 [Scale Out Manager](integration-services-ssis-scale-out-manager.md) 启用 Scale Out Master。

## <a name="EnableAuth"></a> 启用 SQL Server 身份验证模式
如果在数据库引擎安装期间没有启用 [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] 身份验证，可在托管 SSISDB 目录的 [!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)] 实例上启用 SQL Server 身份验证模式。 

禁用 SQL Server 身份验证时，包执行不会受到阻止。 但是，执行日志将无法写入 SSISDB 数据库。

## <a name="EnableWorker"></a> 启用 Scale Out Worker

可通过 [Scale Out Manager](integration-services-ssis-scale-out-manager.md) 启用 Scale Out Worker，前者可提供图形用户界面；或通过存储过程启用。

要通过存储过程启用 Scale Out Worker，请执行 `[catalog].[enable_worker_agent]` 存储过程，并将 WorkerAgentId 设为参数  。 

Scale Out Worker 注册到 Scale Out Master 之后，从 SSISDB 的 `[catalog].[worker_agents]` 视图中获取 WorkerAgentId 值  。 Scale Out Master 和 Worker 服务启用之后，需要花几分钟进行注册。

#### <a name="example"></a>示例
下例将在 `computerA` 上启用 Scale Out Worker。

```sql
SELECT WorkerAgentId, MachineName FROM [catalog].[worker_agents]
GO
-- Result: --
-- WorkerAgentId                           MachineName  --
-- 6583054A-E915-4C2A-80E4-C765E79EF61D    computerA    --

EXEC [catalog].[enable_worker_agent] '6583054A-E915-4C2A-80E4-C765E79EF61D'
GO 
```

## <a name="next-steps"></a>后续步骤
-   [在 Integration Services (SSIS) Scale Out 中运行包](run-packages-in-integration-services-ssis-scale-out.md)。
