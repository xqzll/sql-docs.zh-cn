---
title: 使用 Windows 身份验证访问数据存储和文件共享 | Microsoft Docs
description: 了解如何配置 Azure SQL 数据库中的 SSIS 目录和 Azure 数据工厂中的 Azure-SSIS Integration Runtime，以运行使用 Windows 身份验证访问数据存储和文件共享的包。
ms.date: 3/22/2018
ms.topic: conceptual
ms.prod: sql
ms.prod_service: integration-services
ms.custom: ''
ms.technology: integration-services
author: swinarko
ms.author: sawinark
ms.reviewer: maghan
manager: craigg
ms.openlocfilehash: 218b6930e05319a4e5a1096536cf1dc31a0a94b5
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "66010519"
---
# <a name="access-data-stores-and-file-shares-with-windows-authentication-from-ssis-packages-in-azure"></a>从 Azure 的 SSIS 包中使用 Windows 身份验证访问数据存储和文件共享

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


可以从 Azure 数据工厂 (ADF) 的 Azure-SSIS Integration Runtime (IR) 上运行的 SSIS 包中使用 Windows 身份验证访问数据存储（如 SQL Server、文件共享、Azure 文件存储等）。 数据存储可以位于本地环境，可以托管在 Azure 虚拟机 (VM) 上，也可以作为托管服务在 Azure 中运行。 如果它们位于本地环境，则需要将 Azure SSIS IR 加入连接到本地网络的虚拟网络 (VNet)，请参阅[将 Azure-SSIS IR 加入 VNet](https://docs.microsoft.com/azure/data-factory/join-azure-ssis-integration-runtime-virtual-network)。 以下四种方法可从 Azure-SSIS IR 上运行的 SSIS 包中使用 Windows 身份验证访问数据存储：

| 连接方法 | 有效范围 | 安装步骤 | 在包中访问方法 | 凭据集和连接资源的数量 | 连接资源的类型 | 
|---|---|---|---|---|---|
| 设置活动级别执行上下文 | 每个执行 SSIS 包活动 | 将 SSIS 包作为 ADF 管道中的执行 SSIS 包活动运行时，配置“Windows 身份验证”  属性以设置“执行/运行方式”上下文。<br/><br/> 有关详细信息，请参阅[配置执行 SSIS 包活动](https://docs.microsoft.com/azure/data-factory/how-to-invoke-ssis-package-ssis-activity)。 | 通过 UNC 路径直接访问包资源（例如，如果使用文件共享或 Azure 文件存储：`\\YourFileShareServerName\YourFolderName` 或 `\\YourAzureStorageAccountName.file.core.windows.net\YourFolderName`） | 仅支持适用于所有连接资源的一个凭据集 | - 本地/Azure VM 上的文件共享<br/><br/> - Azure 文件，请参阅[使用 Azure 文件共享](https://docs.microsoft.com/azure/storage/files/storage-how-to-use-files-windows) <br/><br/> - 使用 Windows 身份验证的本地/Azure VM 上的 SQL Server<br/><br/> - 使用 Windows 身份验证的其他资源 |
| 设置目录级别执行上下文 | 每个 Azure-SSIS IR，但是，如果同时还设置活动级别执行上下文，则会被替代（见上文） | 执行 SSISDB `catalog.set_execution_credential` 存储过程来设置“执行/运行方式”上下文。<br/><br/> 有关详细信息，请参阅本文下面的其余部分。 | 通过 UNC 路径直接访问包资源（例如，如果使用文件共享或 Azure 文件存储：`\\YourFileShareServerName\YourFolderName` 或 `\\YourAzureStorageAccountName.file.core.windows.net\YourFolderName`） | 仅支持适用于所有连接资源的一个凭据集 | - 本地/Azure VM 上的文件共享<br/><br/> - Azure 文件，请参阅[使用 Azure 文件共享](https://docs.microsoft.com/azure/storage/files/storage-how-to-use-files-windows) <br/><br/> - 使用 Windows 身份验证的本地/Azure VM 上的 SQL Server<br/><br/> - 使用 Windows 身份验证的其他资源 |
| 通过 `cmdkey` 命令持久保留凭据 | 每个 Azure-SSIS IR，但是，如果同时还设置活动/目录级别执行上下文，则会被替代（见上文） | 在预配/重新配置 Azure-SSIS IR 时，在自定义安装脚本 (`main.cmd`) 中执行 `cmdkey` 命令，例如，如果使用文件共享或 Azure 文件存储 `cmdkey /add:YourFileShareServerName /user:YourDomainName\YourUsername /pass:YourPassword` 或 `cmdkey /add:YourAzureStorageAccountName.file.core.windows.net /user:azure\YourAzureStorageAccountName /pass:YourAccessKey`。<br/><br/> 有关详细信息，请参阅[为 Azure-SSIS IR 自定义安装程序](https://docs.microsoft.com/azure/data-factory/how-to-configure-azure-ssis-ir-custom-setup)。 | 通过 UNC 路径直接访问包资源（例如，如果使用文件共享或 Azure 文件存储：`\\YourFileShareServerName\YourFolderName` 或 `\\YourAzureStorageAccountName.file.core.windows.net\YourFolderName`） | 支持不同连接资源的多个凭据集 | - 本地/Azure VM 上的文件共享<br/><br/> - Azure 文件，请参阅[使用 Azure 文件共享](https://docs.microsoft.com/azure/storage/files/storage-how-to-use-files-windows) <br/><br/> - 使用 Windows 身份验证的本地/Azure VM 上的 SQL Server<br/><br/> - 使用 Windows 身份验证的其他资源 |
| 在包执行时装载驱动器（非永久） | 每个包 | 在包的控制流开头添加的执行过程任务中（例如，`net use D: \\YourFileShareServerName\YourFolderName`）执行 `net use` 命令 | 通过映射驱动器访问文件共享 | 支持不同文件共享的多个驱动器 | - 本地/Azure VM 上的文件共享<br/><br/> - Azure 文件，请参阅[使用 Azure 文件共享](https://docs.microsoft.com/azure/storage/files/storage-how-to-use-files-windows) |
|||||||

> [!WARNING]
> 如果不使用任何上述方法通过 Windows 身份验证访问数据存储，依赖于 Windows 身份验证的包将无法访问它们，并在运行时失败。 

本文的其余部分介绍如何配置托管在 Azure SQL 数据库服务器/托管实例上的 SSIS 目录 (SSISDB)，以便在使用 Windows 身份验证的 Azure-SSIS IR 上运行包来访问数据存储。 

## <a name="you-can-only-use-one-set-of-credentials"></a>仅可使用一组凭据
在 SSIS 包中使用 Windows 身份验证时，只能使用一组凭据。 按照本文中的步骤操作时提供的域凭据适用于 Azure-SSIS IR 上的所有包执行（交互式或按预定），直至更改或删除这些凭据。 如果必须使用多组不同的凭据将包连接到不同的数据存储，应考虑上述替代方法。

## <a name="provide-domain-credentials-for-windows-authentication"></a>提供 Windows 身份验证的域凭据
若要提供域凭据，让包使用 Windows 身份验证访问本地数据存储，请执行以下操作：

1.  使用 SQL Server Management Studio (SSMS) 或其他工具连接到托管 SSISDB 的 Azure SQL 数据库服务器/托管实例。 有关详细信息，请参阅[连接到 Azure 中的 SSISDB](ssis-azure-connect-to-catalog-database.md)。

2.  将 SSISDB 设置为当前数据库后，打开一个查询窗口。

3.  运行以下存储过程，并提供相应的域凭据：

    ```sql
    catalog.set_execution_credential @user='<your user name>', @domain='<your domain name>', @password='<your password>'
    ```

4.  运行 SSIS 包。 这些包将使用所提供的凭据通过 Windows 身份验证访问本地数据存储。

### <a name="view-domain-credentials"></a>查看域凭据
若要查看可用的域凭据，请执行以下操作：

1.  使用 SSMS 或其他工具连接到托管 SSISDB 的 Azure SQL 数据库服务器/托管实例。 有关详细信息，请参阅[连接到 Azure 中的 SSISDB](ssis-azure-connect-to-catalog-database.md)。

2.  将 SSISDB 设置为当前数据库后，打开一个查询窗口。

3.  运行以下存储过程，并检查输出：

    ```sql
    SELECT * 
    FROM catalog.master_properties
    WHERE property_name = 'EXECUTION_DOMAIN' OR property_name = 'EXECUTION_USER'
    ```

### <a name="clear-domain-credentials"></a>清除域凭据
若要清除和删除按本文所述提供的凭据，请执行以下操作：

1.  使用 SSMS 或其他工具连接到托管 SSISDB 的 Azure SQL 数据库服务器/托管实例。 有关详细信息，请参阅[连接到 Azure 中的 SSISDB](ssis-azure-connect-to-catalog-database.md)。

2.  将 SSISDB 设置为当前数据库后，打开一个查询窗口。

3.  运行以下存储过程：

    ```sql
    catalog.set_execution_credential @user='', @domain='', @password=''
    ```

## <a name="connect-to-a-sql-server-on-premises"></a>连接到本地 SQL Server 
若要检查能否连接到本地 SQL Server，请执行以下操作：

1.  若要运行此测试，请找一台未加入域的计算机。

2.  在未加入域的计算机上，运行以下命令，以便通过要使用的域凭据启动 SSMS：

    ```cmd
    runas.exe /netonly /user:<domain>\<username> SSMS.exe
    ```

3.  通过 SSMS 检查能否连接到本地 SQL Server。

### <a name="prerequisites"></a>必备条件
若要从 Azure 中运行的包中访问本地 SQL Server，请执行以下操作：

1.  在 SQL Server 配置管理器中，启用 TCP/IP 协议。
2.  允许通过 Windows 防火墙进行访问。 有关详细信息，请参阅[配置 Windows 防火墙以访问 SQL Server](https://docs.microsoft.com/sql/sql-server/install/configure-the-windows-firewall-to-allow-sql-server-access)。
3.  将 Azure-SSIS IR 加入连接到本地 SQL Server 的 VNet。  有关详细信息，请参阅[将 Azure-SSIS IR 加入 VNet](https://docs.microsoft.com/azure/data-factory/join-azure-ssis-integration-runtime-virtual-network)。
4.  使用 SSISDB `catalog.set_execution_credential` 存储过程提供凭据，如本文中所述。

## <a name="connect-to-a-file-share-on-premises"></a>连接到本地文件共享 
若要检查能否连接到本地文件共享，请执行以下操作：

1.  若要运行此测试，请找一台未加入域的计算机。

2.  在未加入域的计算机上运行以下命令。 这些命令会打开一个命令提示符窗口，其中包含要使用的域凭据，然后通过获取目录列表测试与本地文件共享的连接性。

    ```cmd
    runas.exe /netonly /user:<domain>\<username> cmd.exe
    dir \\fileshare
    ```

3.  检查是否返回本地文件共享的目录列表。

### <a name="prerequisites"></a>必备条件
若要从 Azure 中运行的包中访问本地文件共享，请执行以下操作：

1.  允许通过 Windows 防火墙进行访问。
2.  将 Azure-SSIS IR 加入连接到本地文件共享的 VNet。  有关详细信息，请参阅[将 Azure-SSIS IR 加入 VNet](https://docs.microsoft.com/azure/data-factory/join-azure-ssis-integration-runtime-virtual-network)。
3.  使用 SSISDB `catalog.set_execution_credential` 存储过程提供凭据，如本文中所述。

## <a name="connect-to-a-file-share-on-azure-vm"></a>连接到 Azure VM 上的文件共享
若要从 Azure 中运行的包中访问 Azure VM 上的文件共享，请执行以下操作：

1.  使用 SSMS 或其他工具连接到托管 SSISDB 的 Azure SQL 数据库服务器/托管实例。 有关详细信息，请参阅[连接到 Azure 中的 SSISDB](ssis-azure-connect-to-catalog-database.md)。

2.  将 SSISDB 设置为当前数据库后，打开一个查询窗口。

3.  运行以下存储过程，并提供相应的域凭据：

    ```sql
    catalog.set_execution_credential @domain = N'.', @user = N'username of local account on Azure virtual machine', @password = N'password'
    ```

## <a name="connect-to-a-file-share-in-azure-files"></a>连接到 Azure 文件中的文件共享
有关 Azure 文件的详细信息，请参阅 [Azure 文件](https://azure.microsoft.com/services/storage/files/)。

若要从 Azure 中运行的包中访问 Azure 文件存储中的文件共享，请执行以下操作：

1.  使用 SSMS 或其他工具连接到托管 SSISDB 的 Azure SQL 数据库服务器/托管实例。 有关详细信息，请参阅[连接到 Azure 中的 SSISDB](ssis-azure-connect-to-catalog-database.md)。

2.  将 SSISDB 设置为当前数据库后，打开一个查询窗口。

3.  运行以下存储过程，并提供相应的域凭据：

    ```sql
    catalog.set_execution_credential @domain = N'Azure', @user = N'<storage-account-name>', @password = N'<storage-account-key>'
    ```

## <a name="next-steps"></a>后续步骤
- 部署包。 有关详细信息，请参阅[使用 SSMS 将 SSIS 项目部署到 Azure](../ssis-quickstart-deploy-ssms.md)。
- 运行包。 有关详细信息，请参阅[使用 SSMS 运行 Azure 中的 SSIS 包](../ssis-quickstart-run-ssms.md)。
- 计划包。 有关详细信息，请参阅[计划 Azure 中的 SSIS 包](ssis-azure-schedule-packages.md)。
