---
title: Linux 版 SQL Server 2017 的发行说明
description: 本文包含的发行说明，并在 Linux 上运行的 SQL Server 2017 的支持的功能。 包含最新版本和多个以前版本的发行说明。
author: VanMSFT
ms.author: vanto
manager: jroth
ms.date: 06/25/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: linux
ms.assetid: 1314744f-fcaf-46db-800e-2918fa7e1b6c
ms.openlocfilehash: 06c46a54f21c0397f4ee801349acbebafeedf7a1
ms.sourcegitcommit: 93d1566b9fe0c092c9f0f8c84435b0eede07019f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/11/2019
ms.locfileid: "67834816"
---
# <a name="release-notes-for-sql-server-2017-on-linux"></a>Linux 版 SQL Server 2017 的发行说明

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

以下发行说明适用于[!INCLUDE[ssSQL17](../includes/sssql17-md.md)]在 Linux 上运行。 本文将划分成的部分，了解每个版本。 GA 版具有详细可支持性和已知问题列表。 每个累积更新 (CU) 或常规分发版本 (GDR) 有描述 CU 更改以及链接到包下载的 Linux 支持文章的链接。

> [!TIP]
> 这些发行说明适用于专门[!INCLUDE[ssSQL17](../includes/sssql17-md.md)]释放。 有关新的详细信息[!INCLUDE[sql-server-2019](../includes/sssqlv15-md.md)]，请参阅[发行说明以在 Linux 上的 SQL Server 2019 预览](sql-server-linux-release-notes-2019.md?view=sql-server-ver15)。

## <a name="supported-platforms"></a>受支持的平台

| 平台 | 文件系统 | 安装指南 |
|-----|-----|-----|
| Red Hat Enterprise Linux 7.3、 7.4、 7.5 或 7.6 Server | XFS 或 EXT4 | [安装指南](quickstart-install-connect-red-hat.md) | 
| SUSE Enterprise Linux Server v12 SP2 | XFS 或 EXT4 | [安装指南](quickstart-install-connect-suse.md) |
| Ubuntu 16.04LTS | XFS 或 EXT4 | [安装指南](quickstart-install-connect-ubuntu.md) | 
| Windows、Mac 或 Linux 上的 Docker 引擎 1.8 及更高版本 | 不可用 | [安装指南](quickstart-install-connect-docker.md) | 

> [!TIP]
> 详细信息，请查看[系统要求](sql-server-linux-setup.md#system)为[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]Linux 上。 有关最新支持策略[!INCLUDE[ssSQL17](../includes/sssql17-md.md)]，请参阅[Microsoft SQL Server 的技术支持策略](https://support.microsoft.com/help/4047326/support-policy-for-microsoft-sql-server)。

## <a name="tools"></a>工具

大多数现有的客户端工具面向[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]可以无缝地面向[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]在 Linux 上运行。 一些工具可能会有很好地配合 Linux 特定版本要求。 有关完整列表[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]工具，请参阅[SQL 工具和适用于 SQL Server 实用工具](../tools/overview-sql-tools.md)。

## <a name="release-history"></a>发布历史记录

下表列出了版本历史记录[!INCLUDE[ssSQL17](../includes/sssql17-md.md)]。

| 发行版本               | Version       | 发布日期 |
|-----------------------|---------------|--------------|
| [CU15](#CU15)         | 14.0.3162.1   | 2019-05-23   |
| [CU14](#CU14)         | 14.0.3076.1   | 2019-03-25   |
| [CU13](#CU13)         | 14.0.3048.4   | 2018-12-18   |
| [CU12](#CU12)         | 14.0.3045.24  | 2018-10-24   |
| [CU11](#CU11)         | 14.0.3038.14  | 2018-09-20   |
| [CU10](#CU10)         | 14.0.3037.1   | 2018-08-27   |
| [CU9-GDR2](#CU9-GDR2) | 14.0.3035.2   | 2018-08-18   |
| [GDR2](#GDR2)         | 14.0.2002.14  | 2018-08-18   |
| [CU9](#CU9)           | 14.0.3030.27  | 2018-07-18   |
| [CU8](#CU8)           | 14.0.3029.16  | 2018-06-21   |
| [CU7](#CU7)           | 14.0.3026.27  | 2018-05-24   |
| [CU6](#CU6)           | 14.0.3025.34  | 2018-04-19   |
| [CU5](#CU5)           | 14.0.3023.8   | 2018-03-20   |
| [CU4](#CU4)           | 14.0.3022.28  | 2018-02-20   |
| [CU3](#CU3)           | 14.0.3015.40  | 2018-01-03   |
| [GDR1](#GDR1)         | 14.0.2000.63  | 2018-01-03   |
| [CU2](#CU2)           | 14.0.3008.27  | 2017-11-28   |
| [CU1](#CU1)           | 14.0.3006.16  | 2017-10-24   |
| [GA](#GA)             | 14.0.1000.169 | 2017-10-02   |

## <a id="cuinstall"></a> 如何安装更新

如果已配置的 CU 的存储库 (**mssql server 2017**)，则会收到的最新 CU[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]包时执行全新安装。 CU 的存储库是默认值的所有包安装文章，了解[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]Linux 上。 如果已配置的 GDR 存储库 (**mssql server 2017 gdr**)，才会出现关键安全更新发布后提供 ga 版。 如果需要使用 Docker 容器 CU 或 GDR 更新，请参阅官方的映像[Docker 引擎的 Linux 上的 Microsoft SQL Server](https://hub.docker.com/r/microsoft/mssql-server)。 有关存储库配置的详细信息，请参阅[Linux 上的 SQL Server 配置存储库](sql-server-linux-change-repo.md)。

如果要更新现有[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]包，运行每个包，以获取最新 CU 的相应更新命令。 有关特定更新的每个包的说明，请参阅以下安装指南：

- [安装 SQL Server 包](sql-server-linux-setup.md#upgrade)
- [安装全文搜索包](sql-server-linux-setup-full-text-search.md)
- [安装 SQL Server Integration Services](sql-server-linux-setup-ssis.md)
- [启用 SQL Server 代理](sql-server-linux-setup-sql-agent.md)

## <a id="CU15"></a> Cu15 的所有更新 (2018 年 5 月)

这是累积更新 15 （cu15 的所有更新） 版本的[!INCLUDE[ssSQL17](../includes/sssql17-md.md)]。 [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)]此发布版本是 14.0.3162.1。 有关修补程序和此版本中的改进的信息，请参阅[ https://support.microsoft.com/en-us/help/4498951 ](https://support.microsoft.com/en-us/help/4498951)。

### <a name="package-details"></a>包详细信息

对于手动或脱机包安装，您可以下载与下表中的信息的 RPM 和 Debian 包：

| package | 包版本 | 下载 |
|-----|-----|-----|
| Red Hat RPM 包 | 14.0.3162.1-1 | [引擎 RPM 包](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3162.1-1.x86_64.rpm)</br>[高可用性 RPM 包](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3162.1-1.x86_64.rpm)</br>[全文搜索 RPM 包](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3162.1-1.x86_64.rpm)</br>[SSIS 包](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| SLES RPM 包 | 14.0.3162.1-1 | [mssql-server 引擎 RPM 包](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3162.1-1.x86_64.rpm)</br>[高可用性 RPM 包](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3162.1-1.x86_64.rpm)</br>[全文搜索 RPM 包](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3162.1-1.x86_64.rpm) | 
| Ubuntu 16.04 Debian 包 | 14.0.3162.1-1 | [引擎 Debian 包](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3162.1-1_amd64.deb)</br>[高可用性 Debian 包](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3162.1-1_amd64.deb)</br>[全文搜索 Debian 包](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3162.1-1_amd64.deb)<br/>[SSIS 包](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a id="CU14"></a> CU14 (2018 年 3 月)

这是累积更新 14 (CU14) 版本的[!INCLUDE[ssSQL17](../includes/sssql17-md.md)]。 [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)]此发布版本是 14.0.3076.1。 有关修补程序和此版本中的改进的信息，请参阅[ https://support.microsoft.com/help/4484710 ](https://support.microsoft.com/help/4484710)。

### <a name="package-details"></a>包详细信息

对于手动或脱机包安装，您可以下载与下表中的信息的 RPM 和 Debian 包：

| package | 包版本 | 下载 |
|-----|-----|-----|
| Red Hat RPM 包 | 14.0.3076.1-2 | [引擎 RPM 包](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3076.1-2.x86_64.rpm)</br>[高可用性 RPM 包](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3076.1-2.x86_64.rpm)</br>[全文搜索 RPM 包](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3076.1-2.x86_64.rpm)</br>[SSIS 包](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| SLES RPM 包 | 14.0.3076.1-2 | [mssql-server 引擎 RPM 包](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3076.1-2.x86_64.rpm)</br>[高可用性 RPM 包](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3076.1-2.x86_64.rpm)</br>[全文搜索 RPM 包](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3076.1-2.x86_64.rpm) | 
| Ubuntu 16.04 Debian 包 | 14.0.3076.1-2 | [引擎 Debian 包](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3076.1-2_amd64.deb)</br>[高可用性 Debian 包](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3076.1-2_amd64.deb)</br>[全文搜索 Debian 包](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3076.1-2_amd64.deb)<br/>[SSIS 包](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a id="CU13"></a> CU13 (2018 年 12 月)

这是累积更新 13 (CU13) 版本的[!INCLUDE[ssSQL17](../includes/sssql17-md.md)]。 [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)]此发布版本是 14.0.3048.4。 有关修补程序和此版本中的改进的信息，请参阅[ https://support.microsoft.com/help/4466404 ](https://support.microsoft.com/help/4466404)。

### <a name="package-details"></a>包详细信息

对于手动或脱机包安装，您可以下载与下表中的信息的 RPM 和 Debian 包：

| package | 包版本 | 下载 |
|-----|-----|-----|
| Red Hat RPM 包 | 14.0.3048.4-1 | [引擎 RPM 包](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3048.4-1.x86_64.rpm)</br>[高可用性 RPM 包](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3048.4-1.x86_64.rpm)</br>[全文搜索 RPM 包](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3048.4-1.x86_64.rpm)</br>[SSIS 包](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| SLES RPM 包 | 14.0.3048.4-1 | [mssql-server 引擎 RPM 包](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3048.4-1.x86_64.rpm)</br>[高可用性 RPM 包](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3048.4-1.x86_64.rpm)</br>[全文搜索 RPM 包](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3048.4-1.x86_64.rpm) | 
| Ubuntu 16.04 Debian 包 | 14.0.3048.4-1 | [引擎 Debian 包](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3048.4-1_amd64.deb)</br>[高可用性 Debian 包](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3048.4-1_amd64.deb)</br>[全文搜索 Debian 包](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3048.4-1_amd64.deb)<br/>[SSIS 包](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a id="CU12"></a> CU12 (2018 年 10 月)

这是累积更新 12 (CU12) 版本的[!INCLUDE[ssSQL17](../includes/sssql17-md.md)]。 [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)]此发布版本是 14.0.3045.24。 有关修补程序和此版本中的改进的信息，请参阅[ https://support.microsoft.com/help/4464082 ](https://support.microsoft.com/help/4464082)。

### <a name="package-details"></a>包详细信息

对于手动或脱机包安装，您可以下载与下表中的信息的 RPM 和 Debian 包：

| package | 包版本 | 下载 |
|-----|-----|-----|
| Red Hat RPM 包 | 14.0.3045.24-1 | [引擎 RPM 包](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3045.24-1.x86_64.rpm)</br>[高可用性 RPM 包](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3045.24-1.x86_64.rpm)</br>[全文搜索 RPM 包](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3045.24-1.x86_64.rpm)</br>[SSIS 包](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| SLES RPM 包 | 14.0.3045.24-1 | [mssql-server 引擎 RPM 包](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3045.24-1.x86_64.rpm)</br>[高可用性 RPM 包](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3045.24-1.x86_64.rpm)</br>[全文搜索 RPM 包](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3045.24-1.x86_64.rpm) | 
| Ubuntu 16.04 Debian 包 | 14.0.3045.24-1 | [引擎 Debian 包](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3045.24-1_amd64.deb)</br>[高可用性 Debian 包](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3045.24-1_amd64.deb)</br>[全文搜索 Debian 包](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3045.24-1_amd64.deb)<br/>[SSIS 包](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a id="CU11"></a> CU11 (2018 年 9 月)

这是累积更新 11 (CU11) 版本的[!INCLUDE[ssSQL17](../includes/sssql17-md.md)]。 [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)]此发布版本是 14.0.3038.14。 有关修补程序和此版本中的改进的信息，请参阅[ https://support.microsoft.com/help/4462262 ](https://support.microsoft.com/help/4462262)。

### <a name="package-details"></a>包详细信息

对于手动或脱机包安装，您可以下载与下表中的信息的 RPM 和 Debian 包：

| package | 包版本 | 下载 |
|-----|-----|-----|
| Red Hat RPM 包 | 14.0.3038.14-2 | [引擎 RPM 包](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3038.14-2.x86_64.rpm)</br>[高可用性 RPM 包](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3038.14-2.x86_64.rpm)</br>[全文搜索 RPM 包](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3038.14-2.x86_64.rpm)</br>[SSIS 包](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| SLES RPM 包 | 14.0.3038.14-2 | [mssql-server 引擎 RPM 包](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3038.14-2.x86_64.rpm)</br>[高可用性 RPM 包](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3038.14-2.x86_64.rpm)</br>[全文搜索 RPM 包](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3038.14-2.x86_64.rpm) | 
| Ubuntu 16.04 Debian 包 | 14.0.3038.14-2 | [引擎 Debian 包](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3038.14-2_amd64.deb)</br>[高可用性 Debian 包](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3038.14-2_amd64.deb)</br>[全文搜索 Debian 包](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3038.14-2_amd64.deb)<br/>[SSIS 包](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a id="CU10"></a> CU10 (2018 年 8 月)

这是累积更新 10 (CU10) 版本的[!INCLUDE[ssSQL17](../includes/sssql17-md.md)]。 [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)]此发布版本是 14.0.3037.1。 有关修补程序和此版本中的改进的信息，请参阅[ https://support.microsoft.com/help/4342123 ](https://support.microsoft.com/help/4342123)。

### <a name="package-details"></a>包详细信息

对于手动或脱机包安装，您可以下载与下表中的信息的 RPM 和 Debian 包：

| package | 包版本 | 下载 |
|-----|-----|-----|
| Red Hat RPM 包 | 14.0.3037.1-2 | [引擎 RPM 包](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3037.1-2.x86_64.rpm)</br>[高可用性 RPM 包](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3037.1-2.x86_64.rpm)</br>[全文搜索 RPM 包](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3037.1-2.x86_64.rpm)</br>[SSIS 包](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| SLES RPM 包 | 14.0.3037.1-2 | [mssql-server 引擎 RPM 包](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3037.1-2.x86_64.rpm)</br>[高可用性 RPM 包](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3037.1-2.x86_64.rpm)</br>[全文搜索 RPM 包](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3037.1-2.x86_64.rpm) | 
| Ubuntu 16.04 Debian 包 | 14.0.3037.1-2 | [引擎 Debian 包](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3037.1-2_amd64.deb)</br>[高可用性 Debian 包](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3037.1-2_amd64.deb)</br>[全文搜索 Debian 包](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3037.1-2_amd64.deb)<br/>[SSIS 包](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a id="CU9-GDR2"></a> CU9 GDR2 (2018 年 8 月)

这是用于安全更新，它还包括以前发布的 CU (CU9) [!INCLUDE[ssSQL17](../includes/sssql17-md.md)]。 [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)]此发布版本是 14.0.3035.2。 有关修补程序和此版本中的改进的信息，请参阅[ https://support.microsoft.com/help/4293805 ](https://support.microsoft.com/help/4293805)。

### <a name="package-details"></a>包详细信息

对于手动或脱机包安装，您可以下载与下表中的信息的 RPM 和 Debian 包：

| package | 包版本 | 下载 |
|-----|-----|-----|
| Red Hat RPM 包 | 14.0.3035.2-1 | [引擎 RPM 包](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3035.2-1.x86_64.rpm)</br>[高可用性 RPM 包](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3035.2-1.x86_64.rpm)</br>[全文搜索 RPM 包](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3035.2-1.x86_64.rpm)| 
| SLES RPM 包 | 14.0.3035.2-1 | [mssql-server 引擎 RPM 包](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3035.2-1.x86_64.rpm)</br>[高可用性 RPM 包](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3035.2-1.x86_64.rpm)</br>[全文搜索 RPM 包](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3035.2-1.x86_64.rpm) | 
| Ubuntu 16.04 Debian 包 | 14.0.3035.2-1 | [引擎 Debian 包](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3035.2-1_amd64.deb)</br>[高可用性 Debian 包](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3035.2-1_amd64.deb)</br>[全文搜索 Debian 包](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3035.2-1_amd64.deb)<br/> |

## <a id="GDR2"></a> GDR2 (2018 年 8 月)

这是仅包含有关 GDR2 （和 GDR1） 安全修补程序的安全更新[!INCLUDE[ssSQL17](../includes/sssql17-md.md)]。  [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)]此发布版本是 14.0.2002.14。 有关修补程序和此版本中的改进的信息，请参阅[ https://support.microsoft.com/help/4293803 ](https://support.microsoft.com/help/4293803)。

### <a name="package-details"></a>包详细信息

对于手动或脱机包安装，您可以下载与下表中的信息的 RPM 和 Debian 包：

| package | 包版本 | 下载 |
|-----|-----|-----|
| Red Hat RPM 包 | 14.0.2002.14-1 | [引擎 RPM 包](https://packages.microsoft.com/rhel/7/mssql-server-2017-gdr/mssql-server-14.0.2002.14-1.x86_64.rpm)</br>[高可用性 RPM 包](https://packages.microsoft.com/rhel/7/mssql-server-2017-gdr/mssql-server-ha-14.0.2002.14-1.x86_64.rpm)</br>[全文搜索 RPM 包](https://packages.microsoft.com/rhel/7/mssql-server-2017-gdr/mssql-server-fts-14.0.2002.14-1.x86_64.rpm) | 
| SLES RPM 包 | 14.0.2002.14-1 | [mssql-server 引擎 RPM 包](https://packages.microsoft.com/sles/12/mssql-server-2017-gdr/mssql-server-14.0.2002.14-1.x86_64.rpm)</br>[高可用性 RPM 包](https://packages.microsoft.com/sles/12/mssql-server-2017-gdr/mssql-server-ha-14.0.2002.14-1.x86_64.rpm)</br>[全文搜索 RPM 包](https://packages.microsoft.com/sles/12/mssql-server-2017-gdr/mssql-server-fts-14.0.2002.14-1.x86_64.rpm) | 
| Ubuntu 16.04 Debian 包 | 14.0.2002.14-1 | [引擎 Debian 包](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017-gdr/pool/main/m/mssql-server/mssql-server_14.0.2002.14-1_amd64.deb)</br>[高可用性 Debian 包](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017-gdr/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.2002.14-1_amd64.deb)</br>[全文搜索 Debian 包](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017-gdr/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.2002.14-1_amd64.deb) |

## <a id="CU9"></a> Cu9 的所有更新 (2018 7)

这是累积更新 9 (CU9) 版本的[!INCLUDE[ssSQL17](../includes/sssql17-md.md)]。 [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)]此发布版本是 14.0.3030.27。 有关修补程序和此版本中的改进的信息，请参阅[ https://support.microsoft.com/help/4341265 ](https://support.microsoft.com/help/4341265)。

### <a name="package-details"></a>包详细信息

对于手动或脱机包安装，您可以下载与下表中的信息的 RPM 和 Debian 包：

| package | 包版本 | 下载 |
|-----|-----|-----|
| Red Hat RPM 包 | 14.0.3030.27-1 | [引擎 RPM 包](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3030.27-1.x86_64.rpm)</br>[高可用性 RPM 包](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3030.27-1.x86_64.rpm)</br>[全文搜索 RPM 包](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3030.27-1.x86_64.rpm)</br>[SSIS 包](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| SLES RPM 包 | 14.0.3030.27-1 | [mssql-server 引擎 RPM 包](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3030.27-1.x86_64.rpm)</br>[高可用性 RPM 包](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3030.27-1.x86_64.rpm)</br>[全文搜索 RPM 包](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3030.27-1.x86_64.rpm) | 
| Ubuntu 16.04 Debian 包 | 14.0.3030.27-1 | [引擎 Debian 包](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3030.27-1_amd64.deb)</br>[高可用性 Debian 包](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3030.27-1_amd64.deb)</br>[全文搜索 Debian 包](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3030.27-1_amd64.deb)<br/>[SSIS 包](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a id="CU8"></a> CU8 (2018 年 6 月)

这是累积更新 8 (CU8) 发布的[!INCLUDE[ssSQL17](../includes/sssql17-md.md)]。 [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)]此发布版本是 14.0.3029.16。 有关修补程序和此版本中的改进的信息，请参阅[ https://support.microsoft.com/help/4338363 ](https://support.microsoft.com/help/4338363)。

### <a name="package-details"></a>包详细信息

对于手动或脱机包安装，您可以下载与下表中的信息的 RPM 和 Debian 包：

| package | 包版本 | 下载 |
|-----|-----|-----|
| Red Hat RPM 包 | 14.0.3029.16-1 | [引擎 RPM 包](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3029.16-1.x86_64.rpm)</br>[高可用性 RPM 包](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3029.16-1.x86_64.rpm)</br>[全文搜索 RPM 包](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3029.16-1.x86_64.rpm)</br>[SSIS 包](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| SLES RPM 包 | 14.0.3029.16-1 | [mssql-server 引擎 RPM 包](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3029.16-1.x86_64.rpm)</br>[高可用性 RPM 包](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3029.16-1.x86_64.rpm)</br>[全文搜索 RPM 包](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3029.16-1.x86_64.rpm) | 
| Ubuntu 16.04 Debian 包 | 14.0.3029.16-1 | [引擎 Debian 包](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3029.16-1_amd64.deb)</br>[高可用性 Debian 包](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3029.16-1_amd64.deb)</br>[全文搜索 Debian 包](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3029.16-1_amd64.deb)<br/>[SSIS 包](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a id="CU7"></a> CU7 (2018 年 5 月)

这是累积更新 7 (CU7) 版本的[!INCLUDE[ssSQL17](../includes/sssql17-md.md)]。 [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)]此发布版本是 14.0.3026.27。 有关修补程序和此版本中的改进的信息，请参阅[ https://support.microsoft.com/help/4229789 ](https://support.microsoft.com/help/4229789)。

### <a name="package-details"></a>包详细信息

对于手动或脱机包安装，您可以下载与下表中的信息的 RPM 和 Debian 包：

| package | 包版本 | 下载 |
|-----|-----|-----|
| Red Hat RPM 包 | 14.0.3026.27-2 | [引擎 RPM 包](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3026.27-2.x86_64.rpm)</br>[高可用性 RPM 包](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3026.27-2.x86_64.rpm)</br>[全文搜索 RPM 包](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3026.27-2.x86_64.rpm)</br>[SSIS 包](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| SLES RPM 包 | 14.0.3026.27-2 | [mssql-server 引擎 RPM 包](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3026.27-2.x86_64.rpm)</br>[高可用性 RPM 包](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3026.27-2.x86_64.rpm)</br>[全文搜索 RPM 包](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3026.27-2.x86_64.rpm) | 
| Ubuntu 16.04 Debian 包 | 14.0.3026.27-2 | [引擎 Debian 包](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3026.27-2_amd64.deb)</br>[高可用性 Debian 包](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3026.27-2_amd64.deb)</br>[全文搜索 Debian 包](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3026.27-2_amd64.deb)<br/>[SSIS 包](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a id="CU6"></a> CU6 (2018 年 4 月)

这是累积更新 6 (CU6) 版本的[!INCLUDE[ssSQL17](../includes/sssql17-md.md)]。 [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)]此发布版本是 14.0.3025.34。 有关修补程序和此版本中的改进的信息，请参阅[ https://support.microsoft.com/help/4101464 ](https://support.microsoft.com/help/4101464)。

### <a name="package-details"></a>包详细信息

对于手动或脱机包安装，您可以下载与下表中的信息的 RPM 和 Debian 包：

| package | 包版本 | 下载 |
|-----|-----|-----|
| Red Hat RPM 包 | 14.0.3025.34-3 | [引擎 RPM 包](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3025.34-3.x86_64.rpm)</br>[高可用性 RPM 包](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3025.34-3.x86_64.rpm)</br>[全文搜索 RPM 包](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3025.34-3.x86_64.rpm)</br>[SSIS 包](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| SLES RPM 包 | 14.0.3025.34-3 | [mssql-server 引擎 RPM 包](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3025.34-3.x86_64.rpm)</br>[高可用性 RPM 包](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3025.34-3.x86_64.rpm)</br>[全文搜索 RPM 包](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3025.34-3.x86_64.rpm) | 
| Ubuntu 16.04 Debian 包 | 14.0.3025.34-3 | [引擎 Debian 包](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3025.34-3_amd64.deb)</br>[高可用性 Debian 包](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3025.34-3_amd64.deb)</br>[全文搜索 Debian 包](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3025.34-3_amd64.deb)<br/>[SSIS 包](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a id="CU5"></a> CU5 (2018 年 3 月)

这是累积更新 5 （cu5） 及其之前版本的[!INCLUDE[ssSQL17](../includes/sssql17-md.md)]。 [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)]此发布版本是 14.0.3023.8。 有关修补程序和此版本中的改进的信息，请参阅[ https://support.microsoft.com/help/4092643 ](https://support.microsoft.com/help/4092643)。

### <a name="known-upgrade-issue"></a>已知升级问题

当您从以前的版本升级到 CU5，[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]可能无法启动并出现以下错误：

```
Error: 4860, Severity: 16, State: 1.
Cannot bulk load. The file "C:\Install\SqlTraceCollect.dtsx" does not exist or you don't have file access rights.
Error: 912, Severity: 21, State: 2.
Script level upgrade for database 'master' failed because upgrade step 'msdb110_upgrade.sql' encountered error 200, state
```

若要解决此错误，请启用 SQL Server 代理，并重新启动[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]使用以下命令：

```bash
sudo /opt/mssql/bin/mssql-conf set sqlagent.enabled true
sudo systemctl start mssql-server
```

### <a name="package-details"></a>包详细信息

对于手动或脱机包安装，您可以下载与下表中的信息的 RPM 和 Debian 包：

| package | 包版本 | 下载 |
|-----|-----|-----|
| Red Hat RPM 包 | 14.0.3023.8-5 | [引擎 RPM 包](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3023.8-5.x86_64.rpm)</br>[高可用性 RPM 包](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3023.8-5.x86_64.rpm)</br>[全文搜索 RPM 包](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3023.8-5.x86_64.rpm)</br>[SSIS 包](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| SLES RPM 包 | 14.0.3023.8-5 | [mssql-server 引擎 RPM 包](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3023.8-5.x86_64.rpm)</br>[高可用性 RPM 包](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3023.8-5.x86_64.rpm)</br>[全文搜索 RPM 包](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3023.8-5.x86_64.rpm) | 
| Ubuntu 16.04 Debian 包 | 14.0.3023.8-5 | [引擎 Debian 包](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3023.8-5_amd64.deb)</br>[高可用性 Debian 包](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3023.8-5_amd64.deb)</br>[全文搜索 Debian 包](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3023.8-5_amd64.deb)<br/>[SSIS 包](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a id="CU4"></a> CU4 (2018 年 2 月)

这是累积更新 4 (CU4) 版本的[!INCLUDE[ssSQL17](../includes/sssql17-md.md)]。 [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)]此发布版本是 14.0.3022.28。 有关修补程序和此版本中的改进的信息，请参阅[ https://support.microsoft.com/help/4056498 ](https://support.microsoft.com/help/4056498)。

### <a name="package-details"></a>包详细信息

对于手动或脱机包安装，您可以下载与下表中的信息的 RPM 和 Debian 包：

> [!NOTE]
> 截至 CU4，作为单独的包不能再安装 SQL Server 代理。 它在安装与引擎包，必须启用才能使用。

| package | 包版本 | 下载 |
|-----|-----|-----|
| Red Hat RPM 包 | 14.0.3022.28-2 | [引擎 RPM 包](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3022.28-2.x86_64.rpm)</br>[高可用性 RPM 包](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3022.28-2.x86_64.rpm)</br>[全文搜索 RPM 包](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3022.28-2.x86_64.rpm)</br>[SSIS 包](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| SLES RPM 包 | 14.0.3022.28-2 | [mssql-server 引擎 RPM 包](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3022.28-2.x86_64.rpm)</br>[高可用性 RPM 包](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3022.28-2.x86_64.rpm)</br>[全文搜索 RPM 包](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3022.28-2.x86_64.rpm) | 
| Ubuntu 16.04 Debian 包 | 14.0.3022.28-2 | [引擎 Debian 包](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3022.28-2_amd64.deb)</br>[高可用性 Debian 包](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3022.28-2_amd64.deb)</br>[全文搜索 Debian 包](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3022.28-2_amd64.deb)<br/>[SSIS 包](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a id="GDR1"></a> GDR1 (2018 年 1 月)

这是仅包括安全修补程序的 GDR1 的安全更新[!INCLUDE[ssSQL17](../includes/sssql17-md.md)]。 [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)]此发布版本是 14.0.2000.63。 有关修补程序和此版本中的改进的信息，请参阅[ https://support.microsoft.com/help/4057122 ](https://support.microsoft.com/help/4057122)。

### <a name="package-details"></a>包详细信息

对于手动或脱机包安装，您可以下载与下表中的信息的 RPM 和 Debian 包：

| package | 包版本 | 下载 |
|-----|-----|-----|
| Red Hat RPM 包 | 14.0.2000.63-3 | [引擎 RPM 包](https://packages.microsoft.com/rhel/7/mssql-server-2017-gdr/mssql-server-14.0.2000.63-3.x86_64.rpm)</br>[高可用性 RPM 包](https://packages.microsoft.com/rhel/7/mssql-server-2017-gdr/mssql-server-ha-14.0.2000.63-3.x86_64.rpm)</br>[全文搜索 RPM 包](https://packages.microsoft.com/rhel/7/mssql-server-2017-gdr/mssql-server-fts-14.0.2000.63-3.x86_64.rpm) | 
| SLES RPM 包 | 14.0.2000.63-3 | [mssql-server 引擎 RPM 包](https://packages.microsoft.com/sles/12/mssql-server-2017-gdr/mssql-server-14.0.2000.63-3.x86_64.rpm)</br>[高可用性 RPM 包](https://packages.microsoft.com/sles/12/mssql-server-2017-gdr/mssql-server-ha-14.0.2000.63-3.x86_64.rpm)</br>[全文搜索 RPM 包](https://packages.microsoft.com/sles/12/mssql-server-2017-gdr/mssql-server-fts-14.0.2000.63-3.x86_64.rpm) | 
| Ubuntu 16.04 Debian 包 | 14.0.2000.63-3 | [引擎 Debian 包](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017-gdr/pool/main/m/mssql-server/mssql-server_14.0.2000.63-3_amd64.deb)</br>[高可用性 Debian 包](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017-gdr/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.2000.63-3_amd64.deb)</br>[全文搜索 Debian 包](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017-gdr/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.2000.63-3_amd64.deb) |

## <a id="CU3"></a> CU3 (2018 年 1 月)

这是累积更新 3 (CU3) 版本的[!INCLUDE[ssSQL17](../includes/sssql17-md.md)]。 [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)]此发布版本是 14.0.3015.40。 有关修补程序和此版本中的改进的信息，请参阅[ https://support.microsoft.com/help/4052987 ](https://support.microsoft.com/help/4052987)。

### <a name="package-details"></a>包详细信息

对于手动或脱机包安装，您可以下载与下表中的信息的 RPM 和 Debian 包：

| package | 包版本 | 下载 |
|-----|-----|-----|
| Red Hat RPM 包 | 14.0.3015.40-1 | [引擎 RPM 包](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3015.40-1.x86_64.rpm)</br>[高可用性 RPM 包](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3015.40-1.x86_64.rpm)</br>[全文搜索 RPM 包](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3015.40-1.x86_64.rpm)</br>[SQL Server 代理 RPM 包](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-agent-14.0.3015.40-1.x86_64.rpm)</br>[SSIS 包](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| SLES RPM 包 | 14.0.3015.40-1 | [mssql-server 引擎 RPM 包](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3015.40-1.x86_64.rpm)</br>[高可用性 RPM 包](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3015.40-1.x86_64.rpm)</br>[全文搜索 RPM 包](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3015.40-1.x86_64.rpm)</br>[SQL Server 代理 RPM 包](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-agent-14.0.3015.40-1.x86_64.rpm) | 
| Ubuntu 16.04 Debian 包 | 14.0.3015.40-1 | [引擎 Debian 包](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3015.40-1_amd64.deb)</br>[高可用性 Debian 包](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3015.40-1_amd64.deb)</br>[全文搜索 Debian 包](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3015.40-1_amd64.deb)</br>[SQL Server 代理 Debian 包](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-agent/mssql-server-agent_14.0.3015.40-1_amd64.deb)<br/>[SSIS 包](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a id="CU2"></a> CU2 (2017 年 11 月)

这是累积更新 2 (CU2) 版本的[!INCLUDE[ssSQL17](../includes/sssql17-md.md)]。 [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)]此发布版本是 14.0.3008.27。 有关修补程序和此版本中的改进的信息，请参阅[ https://support.microsoft.com/help/4052574 ](https://support.microsoft.com/help/4052574)。

### <a name="package-details"></a>包详细信息

对于手动或脱机包安装，您可以下载与下表中的信息的 RPM 和 Debian 包：

| package | 包版本 | 下载 |
|-----|-----|-----|
| Red Hat RPM 包 | 14.0.3008.27-1 | [引擎 RPM 包](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3008.27-1.x86_64.rpm)</br>[高可用性 RPM 包](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3008.27-1.x86_64.rpm)</br>[全文搜索 RPM 包](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3008.27-1.x86_64.rpm)</br>[SQL Server 代理 RPM 包](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-agent-14.0.3008.27-1.x86_64.rpm)</br>[SSIS 包](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| SLES RPM 包 | 14.0.3008.27-1 | [mssql-server 引擎 RPM 包](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3008.27-1.x86_64.rpm)</br>[高可用性 RPM 包](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3008.27-1.x86_64.rpm)</br>[全文搜索 RPM 包](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3008.27-1.x86_64.rpm)</br>[SQL Server 代理 RPM 包](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-agent-14.0.3008.27-1.x86_64.rpm) | 
| Ubuntu 16.04 Debian 包 | 14.0.3008.27-1 | [引擎 Debian 包](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3008.27-1_amd64.deb)</br>[高可用性 Debian 包](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3008.27-1_amd64.deb)</br>[全文搜索 Debian 包](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3008.27-1_amd64.deb)</br>[SQL Server 代理 Debian 包](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-agent/mssql-server-agent_14.0.3008.27-1_amd64.deb)<br/>[SSIS 包](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a id="CU1"></a> CU1 (2017 年 10 月)

这是累积更新 1 (CU1) 版本的[!INCLUDE[ssSQL17](../includes/sssql17-md.md)]。 [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)]此发布版本是 14.0.3006.16。 有关修补程序和此版本中的改进的信息，请参阅[ https://support.microsoft.com/help/KB4053439 ](https://support.microsoft.com/help/4038634)。

### <a name="package-details"></a>包详细信息

对于手动或脱机包安装，您可以下载与下表中的信息的 RPM 和 Debian 包：

| package | 包版本 | 下载 |
|-----|-----|-----|
| Red Hat RPM 包 | 14.0.3006.16-3 | [引擎 RPM 包](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.3006.16-3.x86_64.rpm)</br>[高可用性 RPM 包](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.3006.16-3.x86_64.rpm)</br>[全文搜索 RPM 包](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.3006.16-3.x86_64.rpm)</br>[SQL Server 代理 RPM 包](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-agent-14.0.3006.16-3.x86_64.rpm)</br>[SSIS 包](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| SLES RPM 包 | 14.0.3006.16-3 | [mssql-server 引擎 RPM 包](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.3006.16-3.x86_64.rpm)</br>[高可用性 RPM 包](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.3006.16-3.x86_64.rpm)</br>[全文搜索 RPM 包](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.3006.16-3.x86_64.rpm)</br>[SQL Server 代理 RPM 包](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-agent-14.0.3006.16-3.x86_64.rpm) | 
| Ubuntu 16.04 Debian 包 | 14.0.3006.16-3 | [引擎 Debian 包](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.3006.16-3_amd64.deb)</br>[高可用性 Debian 包](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.3006.16-3_amd64.deb)</br>[全文搜索 Debian 包](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.3006.16-3_amd64.deb)</br>[SQL Server 代理 Debian 包](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-agent/mssql-server-agent_14.0.3006.16-3_amd64.deb)<br/>[SSIS 包](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a id="GA"></a> GA (2017 年 10 月)

这是正式版 (GA) 版本的[!INCLUDE[ssSQL17](../includes/sssql17-md.md)]。 [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)]此发布版本是 14.0.1000.169。

### <a name="package-details"></a>包详细信息

下表列出了包的详细信息以及 RPM 和 Debian 包的下载位置。 请注意，如果使用以下安装指南中的步骤，则无需直接下载这些包：

- [安装 SQL Server 包](sql-server-linux-setup.md)
- [安装全文搜索包](sql-server-linux-setup-full-text-search.md)
- [安装 SQL Server 代理包](sql-server-linux-setup-sql-agent.md)
- [安装 SQL Server Integration Services](sql-server-linux-setup-ssis.md)

| package | 包版本 | 下载 |
|-----|-----|-----|
| Red Hat RPM 包 | 14.0.1000.169-2 | [引擎 RPM 包](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-14.0.1000.169-2.x86_64.rpm)</br>[高可用性 RPM 包](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-ha-14.0.1000.169-2.x86_64.rpm)</br>[全文搜索 RPM 包](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-fts-14.0.1000.169-2.x86_64.rpm)</br>[SQL Server 代理 RPM 包](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-agent-14.0.1000.169-2.x86_64.rpm)</br>[SSIS 包](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-is-14.0.1000.169-1.x86_64.rpm) | 
| SLES RPM 包 | 14.0.1000.169-2 | [mssql-server 引擎 RPM 包](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-14.0.1000.169-2.x86_64.rpm)</br>[高可用性 RPM 包](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-ha-14.0.1000.169-2.x86_64.rpm)</br>[全文搜索 RPM 包](https://packages.microsoft.com/sles/12/mssql-server-2017/mssql-server-fts-14.0.1000.169-2.x86_64.rpm)</br>[SQL Server 代理 RPM 包](https://packages.microsoft.com/rhel/7/mssql-server-2017/mssql-server-agent-14.0.1000.169-2.x86_64.rpm) | 
| Ubuntu 16.04 Debian 包 | 14.0.1000.169-2 | [引擎 Debian 包](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server/mssql-server_14.0.1000.169-2_amd64.deb)</br>[高可用性 Debian 包](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-ha/mssql-server-ha_14.0.1000.169-2_amd64.deb)</br>[全文搜索 Debian 包](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-fts/mssql-server-fts_14.0.1000.169-2_amd64.deb)</br>[SQL Server 代理 Debian 包](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-agent/mssql-server-agent_14.0.1000.169-2_amd64.deb)<br/>[SSIS 包](https://packages.microsoft.com/ubuntu/16.04/mssql-server-2017/pool/main/m/mssql-server-is/mssql-server-is_14.0.1000.169-1_amd64.deb) |

## <a name="Unsupported"></a> 不支持的功能和服务

以下功能和服务在 GA 发行时不可用在 Linux 上。 随着时间的推移将越来越多地启用这些功能的支持。

| 区域 | 不支持的功能或服务 |
|-----|-----|
| **数据库引擎** | 事务复制 |
| &nbsp; | 合并复制 |
| &nbsp; | 更改数据捕获 （请参阅 SQL Server 代理） |
| &nbsp; | Stretch DB |
| &nbsp; | PolyBase |
| &nbsp; | 使用第三方连接的分布式的查询 |
| &nbsp; | 以外的其他数据源的链接的服务器 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]  |
| &nbsp; | 系统扩展的存储过程（XP_CMDSHELL 等） |
| &nbsp; | Filetable，FILESTREAM |
| &nbsp; | 带有 EXTERNAL_ACCESS 或 UNSAFE 权限集的 CLR 程序集 |
| &nbsp; | 缓冲池扩展 |
| **SQL Server 代理** |  子系统：CmdExec、 PowerShell、 队列读取器、 SSIS、 SSAS、 SSRS |
| &nbsp; | 警报 |
| &nbsp; | 日志读取器代理 |
| &nbsp; | 变更数据捕获 (CDC) |
| &nbsp; | 托管备份 |
| **高可用性** | 数据库镜像  |
| **安全性** | 可扩展的密钥管理 |
| &nbsp; | 链接服务器的 AD 身份验证 | 
| &nbsp; | 可用性组 (Ag) 的 AD 身份验证 | 
| &nbsp; | 第三方 AD 工具 (Centrify，Vintela，Powerbroker) | 
| **服务** | SQL Server Browser |
| &nbsp; | SQL Server R Services |
| &nbsp; | StreamInsight |
| &nbsp; | Analysis Services |
| &nbsp; | Reporting Services |
| &nbsp; | “数据库引擎服务” |
| &nbsp; | Master Data Services |
| &nbsp; | 分布式的事务处理协调器 (DTC) |

## <a name="known-issues"></a>已知问题

以下各节介绍了正式版 (GA) 版本的已知的问题[!INCLUDE[ssSQL17](../includes/sssql17-md.md)]Linux 上。

#### <a name="general"></a>常规

- 主机名的长度其中[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]已安装，需要为 15 个字符或更少。 

    - **解析**:将 /etc/hostname 中的名称更改为不超过 15 个字符。

- 手动将系统时间向后设置的时间将导致[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]停止更新中的内部系统时间[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]。

    - **解析**:重新启动 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]。

- 仅支持单个实例安装。

    - **解析**:如果你想要在给定主机上安装多个实例，请考虑使用 Vm 或 Docker 容器。 

- [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 配置管理器无法连接到[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]Linux 上。

- 默认语言**sa**登录名是英语。

    - **解析**:更改语言**sa**具有登录名**ALTER LOGIN**语句。

#### <a name="databases"></a>数据库

- 不能使用 mssql-conf 实用工具移动 master 数据库。 可以使用 mssql-conf 移动其他系统数据库

- 还原备份数据库时[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]在 Windows 中，必须使用**WITH MOVE** Transact SQL 语句中的子句。

- 需要 Microsoft 分布式事务处理协调器服务的分布式事务不支持在[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]在 Linux 上运行。 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 到[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]除非它们涉及 DTC 支持链接的服务器。 有关详细信息，请参阅[在 Linux 上运行的 SQL Server 不支持需要 Microsoft 分布式事务处理协调器服务的分布式事务](https://blogs.msdn.microsoft.com/bobsql/2017/12/11/sql-server-linux-distributed-transactions-requiring-the-microsoft-distributed-transaction-coordinator-service-are-not-supported-on-sql-server-running-on-linux-sql-server-to-sql-server-distributed-tr/)。

- 某些算法 （密码套件） 的传输层安全性 (TLS) 与工作不正常[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]Linux 上。 这会导致连接失败时尝试连接到[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]，以及建立高可用性组副本之间的连接问题。

   - **解析**:修改**mssql.conf**配置脚本[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]上 Linux 禁用有问题的密码套件，执行以下操作：

      1. 将以下代码添加到 /var/opt/mssql/mssql.conf。

      ```
      [network]
      tlsciphers= AES256-GCM-SHA384:AES128-GCM-SHA256:AES256-SHA256:AES128-SHA256:AES256-SHA:AES128-SHA:!ECDHE-RSA-AES128-GCM-SHA256:!ECDHE-RSA-AES256-GCM-SHA384:!ECDHE-ECDSA-AES256-GCM-SHA384:!ECDHE-ECDSA-AES128-GCM-SHA256:!ECDHE-ECDSA-AES256-SHA384:!ECDHE-ECDSA-AES128-SHA256:!ECDHE-ECDSA-AES256-SHA:!ECDHE-ECDSA-AES128-SHA:!ECDHE-RSA-AES256-SHA384:!ECDHE-RSA-AES128-SHA256:!ECDHE-RSA-AES256-SHA:!ECDHE-RSA-AES128-SHA:!DHE-RSA-AES256-GCM-SHA384:!DHE-RSA-AES128-GCM-SHA256:!DHE-RSA-AES256-SHA:!DHE-RSA-AES128-SHA:!DHE-DSS-AES256-SHA256:!DHE-DSS-AES128-SHA256:!DHE-DSS-AES256-SHA:!DHE-DSS-AES128-SHA:!DHE-DSS-DES-CBC3-SHA:!NULL-SHA256:!NULL-SHA
      ```

         >[!NOTE]
         >In the preceding code, `!` negates the expression. This tells OpenSSL to not use the following cipher suite.  

      1. 重新启动[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]使用以下命令。

      ```bash
      sudo systemctl restart mssql-server
      ```

- [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] 使用内存中 OLTP 的 Windows 上的数据库不能还原上[!INCLUDE[ssSQL17](../includes/sssql17-md.md)]Linux 上。 若要还原[!INCLUDE[ssSQL14](../includes/sssql14-md.md)]使用内存中 OLTP 数据库，首先升级到的数据库[!INCLUDE[ssSQL15](../includes/sssql15-md.md)]或[!INCLUDE[ssSQL17](../includes/sssql17-md.md)]移动到之前的 Windows 上[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]通过备份/还原或分离/附加在 Linux 上。

- 用户权限**ADMINISTER BULK OPERATIONS**不支持在 Linux 上这一次。

#### <a name="networking"></a>网络

如果满足以下条件时，可能无法工作涉及从 sqlservr 进程，如链接的服务器或可用性组的出站 TCP 连接的功能：

1. 目标服务器指定为主机名而不是 IP 地址。

1. 源实例已在内核中禁用 IPv6。 若要验证您的系统是否在内核中启用 IPv6，必须通过所有以下测试：

   - `cat /proc/cmdline` 将打印在当前内核启动命令行。 不能包含输出`ipv6.disable=1`。
   - / Proc/sys/net/ipv6/目录必须存在。
   - C 程序中调用`socket(AF_INET6, SOCK_STREAM, IPPROTO_IP)`应该会成功-syscall 必须返回 fd ！ =-1 而不会失败并 EAFNOSUPPORT。

具体错误取决于该功能。 对于链接服务器，这表示为登录超时错误。 对于可用性组，`ALTER AVAILABILITY GROUP JOIN`下载配置超时错误的 5 分钟后在次要副本上的 DDL 将失败。

若要解决此问题，请执行以下操作：

1. 使用而不是主机名的 Ip 指定 TCP 连接的目标。

1. 通过删除启用内核中的 IPv6`ipv6.disable=1`从启动命令行。 若要执行此操作的方式取决于 Linux 分发版和引导加载程序，如 grub。 如果确实想要禁用 IPv6，你仍然可以禁用它通过设置`net.ipv6.conf.all.disable_ipv6 = 1`中`sysctl`配置 (例如`/etc/sysctl.conf`)。 这仍将防止系统的网络适配器 IPv6 地址，但允许 sqlservr 功能工作。

#### <a name="network-file-system-nfs"></a>网络文件系统 (NFS)
如果您使用**网络文件系统 (NFS)** 在生产中，远程共享，请注意以下支持要求：

- 使用 NFS 版本**4.2 或更高版本**。 较旧版本的 NFS 不支持所需的功能，例如 fallocate 和稀疏文件创建，普遍适用于现代文件系统。
- 仅定位 **/var/opt/mssql**上 NFS 装入的目录。 其他文件，如[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]系统二进制文件不受支持。
- 请确保装载的远程共享时，NFS 客户端，使用 nolock 选项。

#### <a name="localization"></a>本地化

- 如果您的区域设置不是在安装过程英语 (en_us)，则必须使用 utf-8 编码在 bash 会话/终端。 如果您使用 ASCII 编码，可能会看到如下错误：

   ```
   UnicodeEncodeError: 'ascii' codec can't encode character u'\xf1' in position 8: ordinal not in range(128)
   ```

   如果您不能使用 utf-8 编码，运行安装程序使用 MSSQL_LCID 环境变量来指定语言选择。

   ```bash
   sudo MSSQL_LCID=<LcidValue> /opt/mssql/bin/mssql-conf setup
   ```

- 运行 mssql conf 安装程序时执行的非英语安装和[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]，本地化文本，"配置 SQL Server..."之后显示不正确的扩展的字符。 或者，对于非拉丁基于安装，可能会丢失句子完全。 缺少句子应显示以下已本地化的字符串："已成功处理授权 PID。 新版本是 [\<名称\>版本]"。 此字符串是输出信息为目的，以及接下来的[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]累积更新将解决此问题的所有语言。 这不会影响成功安装的[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]以任何方式。 

#### <a name="full-text-search"></a>全文搜索

- 并非所有筛选器是适用于此版本，包括 Office 文档筛选器。 有关支持的筛选器列表，请参阅[安装在 Linux 上 SQL Server 全文搜索](sql-server-linux-setup-full-text-search.md#filters)。

#### <a id="ssis"></a> SQL Server Integration Services (SSIS)

- **Mssql server 是**包在此版本中不支持在 SUSE 上。 目前支持 Ubuntu 和 Red Hat Enterprise Linux (RHEL) 上。

- 与[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]刷新 Linux CTP 2.1 及更高版本，[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]包可以在 Linux 上使用 ODBC 连接。 此功能经过了[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]和 MySQL ODBC 驱动程序，但也应使用 ODBC 规范将观察任何 Unicode ODBC 驱动程序。 在设计时，你可以提供 DSN 或连接字符串连接到 ODBC 数据;此外可以使用 Windows 身份验证。 有关详细信息，请参阅[博客文章在 Linux 上宣布推出的 ODBC 支持](https://blogs.msdn.microsoft.com/ssis/2017/06/16/odbc-is-supported-in-ssis-on-linux-ssis-helsinki-ctp2-1-refresh/)。

- Linux 上运行 SSIS 包时，在此版本中不支持以下功能：
  - [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 目录数据库
  - 由 SQL 代理计划的包执行
  - Windows 身份验证
  - 第三方组件
  - 变更数据捕获 (CDC)
  - [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 横向扩展
  - 适用于 SSIS 的 azure 功能包
  - Hadoop 和 HDFS 支持
  - Microsoft Connector for SAP BW

内置 SSIS 组件的当前不支持，或支持有限制的列表，请参阅[限制和已知的问题为 Linux 上的 SSIS](sql-server-linux-ssis-known-issues.md#components)。

有关在 Linux 上的 SSIS 的详细信息，请参阅以下文章：
-   [博客文章宣布推出适用于 Linux 的 SSIS 支持](https://blogs.msdn.microsoft.com/ssis/2017/05/17/ssis-helsinki-is-available-in-sql-server-vnext-ctp2-1/)。
-   [在 Linux 上安装 SQL Server Integration Services (SSIS)](sql-server-linux-setup-ssis.md)
-   [提取、 转换和加载使用 SSIS 的 Linux 上的数据](sql-server-linux-migrate-ssis.md)

#### <a id="ssms"></a> SQL Server Management Studio (SSMS)

以下限制适用于[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]连接到的 Windows 上[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]Linux 上。

- 不支持维护计划。

- 管理数据仓库 (MDW) 和中的数据收集器[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]不受支持。 

- [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 具有 Windows 身份验证或 Windows 事件日志选项的 UI 组件不适用于 Linux。 仍可通过其它选项（如 SQL 登录名）使用这些功能。 

- 不能修改的日志文件，以保留数。

## <a name="next-steps"></a>后续步骤

若要开始，请参阅以下快速入门：

- [在 Red Hat Enterprise Linux 上安装](quickstart-install-connect-red-hat.md)
- [在 SUSE Linux Enterprise Server 上安装](quickstart-install-connect-suse.md)
- [在 Ubuntu 上安装](quickstart-install-connect-ubuntu.md)
- [在 Docker 上运行](quickstart-install-connect-ubuntu.md)
- [在 Azure 中预配 SQL VM](/azure/virtual-machines/linux/sql/provision-sql-server-linux-virtual-machine?toc=/sql/toc/toc.json)
- [运行和连接 - 云](quickstart-install-connect-clouds.md)

有关常见问题的解答，请参阅[SQL Server Linux 常见问题](sql-server-linux-faq.md)。
