---
title: SQL Server 2017 的各版本和支持的功能 | Microsoft Docs
ms.custom: ''
ms.date: 03/28/2019
ms.prod: sql
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
helpviewer_keywords:
- Enterprise Edition [SQL Server]
- Developer Edition [SQL Server]
- 32-bit vs. 64-bit editions [SQL Server]
- default components
- Workgroup Edition [SQL Server]
- Internet servers [SQL Server]
- installing SQL Server, components
- Setup [SQL Server], components
- SQL Server, editions
- SQL Server, components
- client/server applications [SQL Server]
- editions [SQL Server]
- versions [SQL Server]
- Setup [SQL Server], editions
- SQL Server Installation Wizard
- components [SQL Server]
- Standard Edition [SQL Server]
- 64-bit edition [SQL Server]
- IIS [SQL Server]
- installing SQL Server, editions
- editions [SQL Server], about edition options
- Setup [SQL Server]
ms.assetid: ''
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
monikerRange: '>= sql-server-2017 || = sqlallproducts-allversions'
ms.openlocfilehash: c7e831a6c0e5a1d45c8e7ac2c921be3ef120a41f
ms.sourcegitcommit: 3a64cac1e1fc353e5a30dd7742e6d6046e2728d9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/03/2019
ms.locfileid: "67556956"
---
# <a name="editions-and-supported-features-of-sql-server-2017"></a>SQL Server 2017 的各版本和支持的功能
[!INCLUDE[tsql-appliesto-ss2017-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2017-xxxx-xxxx-xxx-md.md)]

> [!div class="nextstepaction"]
> [请分享你对 SQL Docs 中心页的反馈！](https://github.com/MicrosoftDocs/sql-docs/issues/2249)

本主题详细介绍 SQL Server 2017 的不同版本支持的功能。 

有关以前版本的信息，请参阅：

* [SQL Server 2016](editions-and-components-of-sql-server-2016.md)。  
* [SQL Server 2014](https://msdn.microsoft.com/library/cc645993(v=sql.120).aspx)。

  
根据应用程序的需要，安装要求会有所不同。 不同版本的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 能够满足单位和个人独特的性能、运行时以及价格要求。 安装哪些 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 组件还取决于您的具体需要。 下面各节将帮助您了解如何在 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]的不同版本和可用组件中做出最佳选择。  

可在 180 天的试用期内使用 SQL Server 评估版。  
  
有关最新的发布说明和新增功能的信息，请参阅以下内容：
- [SQL Server 2017 发行说明](../sql-server/sql-server-2017-release-notes.md)
- [SQL Server 2017 的新增功能](../sql-server/what-s-new-in-sql-server-2017.md)

### <a name="try-sql-server"></a>试用 SQL Server！    
    
> [![从 Evaluation Center 下载](../analysis-services/media/download.png)](https://www.microsoft.com/evalcenter/evaluate-sql-server-2017-ctp/) **[从 Evaluation Center 下载 SQL Server 2017](https://www.microsoft.com/evalcenter/evaluate-sql-server-2017-ctp/)**    

<!---    
> ![Azure Virtual Machine small](../analysis-services/media/azure-virtual-machine-small.png) **[Spin up a Virtual Machine with SQL Server 2016 already installed](https://azuremarketplace.microsoft.com/marketplace/apps/Microsoft.SQL2016SP1-WS2016?tab=Overview?wt.mc_id=sqL16_vm)**   
--->

## <a name="includessnoversionincludesssnoversion-mdmd-editions"></a>[!INCLUDE[ssNoVersion](../includes/ssNoVersion-md.md)] 版本  
 下表介绍 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]的各个版本。 
  
|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 版本|定义|  
|---------------------------------------|----------------|  
|Enterprise|作为高级产品/服务，[!INCLUDE[ssNoVersion](../includes/ssNoVersion-md.md)] Enterprise Edition 提供了全面的高端数据中心功能，性能极为快捷、无限虚拟化<sup>1</sup>，还具有端到端的商业智能，可为关键任务工作负荷提供较高服务级别并且支持最终用户访问数据见解。|  
|Standard|[!INCLUDE[ssNoVersion](../includes/ssNoVersion-md.md)] Standard 版提供了基本数据管理和商业智能数据库，使部门和小型组织能够顺利运行其应用程序并支持将常用开发工具用于内部部署和云部署，有助于以最少的 IT 资源获得高效的数据库管理。|  
|Web|对于为从小规模至大规模 Web 资产提供可伸缩性、经济性和可管理性功能的 Web 宿主和 Web VAP 来说，[!INCLUDE[ssNoVersion](../includes/ssNoVersion-md.md)] Web 版本是一项总拥有成本较低的选择。|  
|开发人员|[!INCLUDE[ssNoVersion](../includes/ssNoVersion-md.md)] Developer 版支持开发人员基于 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]构建任意类型的应用程序。 它包括 Enterprise 版的所有功能，但有许可限制，只能用作开发和测试系统，而不能用作生产服务器。 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Developer 是构建和测试应用程序的人员的理想之选。|  
|Express 版本|Express 版本是入门级的免费数据库，是学习和构建桌面及小型服务器数据驱动应用程序的理想选择。 它是独立软件供应商、开发人员和热衷于构建客户端应用程序的人员的最佳选择。 如果您需要使用更高级的数据库功能，则可以将 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Express 无缝升级到其他更高端的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]版本。 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Express LocalDB 是 Express 的一种轻型版本，该版本具备所有可编程性功能，在用户模式下运行，并且具有快速的零配置安装和必备组件要求较少的特点。|  

<sup>1</sup> Enterprise Edition 上提供有面向具有[软件保障](https://www.microsoft.com/licensing/licensing-programs/software-assurance-default)的客户的无限虚拟化。 部署必须遵守[许可指南](https://download.microsoft.com/download/7/8/C/78CDF005-97C1-4129-926B-CE4A6FE92CF5/SQL_Server_2017_Licensing_guide.pdf)。 有关详细信息，请参阅我们的[定价和许可页](https://www.microsoft.com/sql-server/sql-server-2017-pricing)。

## <a name="using-includessnoversionincludesssnoversion-mdmd-with-an-internet-server"></a>将 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 用于 Internet 服务器  
 在 Internet 服务器（如运行 Internet Information Services (IIS) 的服务器）上通常都会安装 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 客户端工具。 客户端工具包括连接到 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]实例的应用程序所使用的客户端连接组件。  
  
>[!NOTE]
>尽管可以在运行 IIS 的计算机上安装 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 实例，但这种做法通常只用于仅包含一台服务器的小型网站。 大多数网站都将其中间层 IIS 系统安装在一台服务器上或服务器群集中，将数据库安装在另外一个服务器或服务器联合体上。  
  
## <a name="using-includessnoversionincludesssnoversion-mdmd-with-clientserver-applications"></a>将 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 用于客户端/服务器应用程序  
 在运行直接连接到 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 实例的客户端/服务器应用程序的计算机上，只能安装 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]客户端组件。 如果要在数据库服务器上管理 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 实例，或者打算开发 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 应用程序，那么客户端组件安装也是一个不错的选择。  
  
 客户端工具选项安装以下 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 功能：向后兼容性组件、 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]、连接组件、管理工具、软件开发包和 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 联机丛书组件。 有关详细信息，请参阅[安装 SQL Server](../database-engine/install-windows/install-sql-server.md)。  
  
## <a name="deciding-among-includessnoversionincludesssnoversion-mdmd-components"></a>选择 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 组件  
 使用 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 安装向导的“功能选择”页面选择安装 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]时要安装的组件。 默认情况下未选中树中的任何功能。  
  
 可根据下表中给出的信息确定最能满足需要的功能集合。  
  
|服务器组件|描述|  
|-----------------------|-----------------|  
|[!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)]|[!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] 包括 [!INCLUDE[ssDE](../includes/ssde-md.md)]、部分工具和 [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) 服务器，其中引擎是用于存储、处理和保护数据、复制及全文搜索的核心服务，工具用于管理数据库分析集成中和可访问 Hadoop 及其他异类数据源的 Polybase 集成中的关系数据和 XML 数据。|  
|[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]|[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 包括一些工具，可用于创建和管理联机分析处理 (OLAP) 以及数据挖掘应用程序。|  
|[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]|[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 包括用于创建、管理和部署表格报表、矩阵报表、图形报表以及自由格式报表的服务器和客户端组件。 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 还是一个可用于开发报表应用程序的可扩展平台。|  
|[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]|[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 是一组图形工具和可编程对象，用于移动、复制和转换数据。 它还包括 [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] 的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)](DQS) 组件。|  
|[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]|[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] (MDS) 是针对主数据管理的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 解决方案。 可以配置 MDS 来管理任何领域（产品、客户、帐户）；MDS 中可包括层次结构、各种级别的安全性、事务、数据版本控制和业务规则，以及可用于管理数据的 [!INCLUDE[ssMDSXLS](../includes/ssmdsxls-md.md)] 。|  
|机器学习服务（数据库内）|机器学习服务（数据库内）支持使用企业数据源的分布式、可缩放的机器学习解决方案。 SQL Server 2016 支持 R 语言。 SQL Server 2017 支持 R 和 Python。|
|机器学习服务器（独立）|机器学习服务器（独立）支持在多个平台上部署分布式、可缩放机器学习解决方案，并可使用多个企业数据源，包括 Linux 和 Hadoop。 SQL Server 2016 支持 R 语言。 SQL Server 2017 支持 R 和 Python。|

  
|管理工具|描述|  
|----------------------|-----------------|  
|[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]|[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 是用于访问、配置、管理和开发 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]组件的集成环境。 [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] 使各种技术水平的开发人员和管理员都能使用 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]。<br /><br /> 从 <br />                [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] 下载 SQL Server Management Studio  [中下载并安装](https://msdn.microsoft.com/library/mt238290.aspx)|  
|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 配置管理器|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 配置管理器为 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 服务、服务器协议、客户端协议和客户端别名提供基本配置管理。|  
|[!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)]|[!INCLUDE[ssSqlProfiler](../includes/sssqlprofiler-md.md)] 提供了一个图形用户界面，用于监视 [!INCLUDE[ssDE](../includes/ssde-md.md)] 实例或 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]实例。|  
|[!INCLUDE[ssDE](../includes/ssde-md.md)] 优化顾问|[!INCLUDE[ssDE](../includes/ssde-md.md)] 优化顾问可以协助创建索引、索引视图和分区的最佳组合。|  
|数据质量客户端|提供了一个非常简单和直观的图形用户界面，用于连接到 DQS 数据库并执行数据清理操作。 它还允许您集中监视在数据清理操作过程中执行的各项活动。|  
|[!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]|[!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] 提供 IDE 以便为以下商业智能组件生成解决方案： [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]、 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]和 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]。<br /><br /> （以前称作 Business Intelligence Development Studio）。<br /><br /> [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] 还包含“数据库项目”，为数据库开发人员提供集成环境，以便在 Visual Studio 内为任何 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 平台（包括本地和外部）执行其所有数据库设计工作。 数据库开发人员可以使用 Visual Studio 中功能增强的服务器资源管理器，轻松创建或编辑数据库对象和数据或执行查询。|  
|连接组件|安装用于客户端和服务器之间通信的组件，以及用于 DB-Library、ODBC 和 OLE DB 的网络库。|  
  
|文档|描述|  
|-------------------|-----------------|  
|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 联机丛书|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]的核心文档。| 

**开发人员版和评估版**  
有关开发人员版和评估版支持的功能，请参阅下表中列出的 SQL Server Enterprise Edition 功能。

开发人员版仍然仅支持一个 [SQL Server Distributed Replay](../tools/distributed-replay/sql-server-distributed-replay.md) 客户端。 
  
##  <a name="Cross-BoxScaleLimits"></a>规模限制  
  
|功能|Enterprise|Standard|Web|Express with Advanced Services|Express| 
|-------------|----------------|--------------|---------|------------------------------------|------------------------|
|单个实例使用的最大计算能力 - [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)]<sup>1</sup>|操作系统支持的最大值|限制为 4 个插槽或 24 核，取二者中的较小值|限制为 4 个插槽或 16 核，取二者中的较小值|限制为 1 个插槽或 4 核，取二者中的较小值|限制为 1 个插槽或 4 核，取二者中的较小值| 
|单个实例使用的最大计算能力 - [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 或 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]|操作系统支持的最大值|限制为 4 个插槽或 24 核，取二者中的较小值|限制为 4 个插槽或 16 核，取二者中的较小值|限制为 1 个插槽或 4 核，取二者中的较小值|限制为 1 个插槽或 4 核，取二者中的较小值|  
|每个 [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)]实例的缓冲池的最大内存|操作系统支持的最大值|128 GB|64 GB|1410 MB|1410 MB|
|每个 [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)]实例的列存储段缓存的最大内存|不受限制的内存| 32 GB| 16 GB| 352 MB| 352 MB|  
|[!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)] 中每个数据库的最大内存优化数据大小|不受限制的内存| 32 GB| 16 GB| 352 MB| 352 MB|  
|每个 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]实例利用的最大内存|操作系统支持的最大值|表格：16 GB<br /><br /> MOLAP：64 GB|N/A|N/A|N/A|  
|每个 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]实例利用的最大内存|操作系统支持的最大值|64 GB|64 GB|4 GB|N/A|
|最大关系数据库大小|524 PB|524 PB|524 PB|10 GB|10 GB|  
  
<sup>1</sup> 对于 Enterprise Edition 配合基于服务器 + 客户端访问许可证 (CAL) 的许可（对新协议不可用），每个 SQL Server 实例的内核数上限为 20。 基于内核的服务器许可模型没有限制。 有关详细信息，请参阅 [Compute Capacity Limits by Edition of SQL Server](../sql-server/compute-capacity-limits-by-edition-of-sql-server.md)。  
 
##  <a name="RDBMSHA"></a>RDBMS 高可用性  
  
|功能|Enterprise|Standard|Web|Express with Advanced Services|Express|  
|-------------|----------------|--------------|---------|------------------------------------|------------------------|  
|Server Core 支持 <sup>1</sup>|是|是|是|是|是|  
|日志传送|是|是|是|否|否|  
|数据库镜像|是|是<br /><br /> 仅完全安全|仅见证服务器|仅见证服务器|仅见证服务器| 
|备份压缩|是|是|否|否|否| 
|数据库快照|是|是|是|是|是|
|AlwaysOn 故障转移群集实例<sup>2</sup>|是|是|否|否|否|  
|AlwaysOn 可用性组<sup>3</sup>|是|否|否|否|否|
|基本可用性组<sup>4</sup>|否|是|否|否|否|
|联机页面和文件还原|是|否|否|否|否|
|联机索引创建和重新生成|是|否|否|否|否|
|可恢复的联机索引重新生成|是|否|否|否|否|
|联机架构更改|是|否|否|否|否|
|快速恢复|是|否|否|否|否|
|镜像备份|是|否|否|否|否|
|热插拔内存和 CPU|是|否|否|否|否|
|数据库恢复顾问|是|是|是|是|是|
|加密备份|是|是|否|否|否|
|Microsoft Azure 的混合备份（URL 的备份）|是|是|否|否|否|
|读取缩放可用性组|是|是|否|否|否|否|
|最小副本提交可用性组|是|是|是|否|否|否|
  

<sup>1</sup> 有关如何在 Server Core 上安装 SQL Server 的详细信息，请参阅[在 Server Core 上安装 SQL Server](../database-engine/install-windows/install-sql-server-on-server-core.md)。 

<sup>2</sup> 在 Enterprise 版本中，节点数是操作系统支持的最大值。 Standard 版本中支持两个节点。 

<sup>3</sup> Enterprise 版本支持最多 8 个辅助副本，包括 2 个同步辅助副本。 

<sup>4</sup> Standard 版本支持基本可用性组。 基本可用性组支持两个副本，一个数据库。 有关基本可用性组的详细信息，请参阅 [可用性组](../database-engine/availability-groups/windows/basic-availability-groups-always-on-availability-groups.md)。  


##  <a name="RDBMSSP"></a>RDBMS 可伸缩性和性能  
  
|功能|Enterprise|Standard|Web|Express with Advanced Services|Express|  
|-------------|----------------|--------------|---------|------------------------------------|------------------------| 
|列存储 <sup>1</sup>|是|是|是|是|是|  
|聚集列存储索引中的大型对象二进制文件|是|是|是|是|是|  
|联机非聚集列存储索引重新生成|是|否|否|否|否|
|内存中 OLTP <sup>1</sup>|是|是|是|是，<sup>2</sup>|是|
|Stretch Database|是|是|是|是|是|
|永久性主内存|是|是|是|是|是|
|多实例支持|50|50|50|50|50|
|表和索引分区|是|是|是|是|是|  
|数据压缩|是|是|是|是|是|
|Resource Governor|是|否|否|否|否|  
|已分区表并行度|是|否|否|否|否|
|多个 Filestream 容器|是|是|是|是|是|
|可识别 NUMA 的大型页内存和缓冲区数组分配|是|否|否|否|否|
|缓冲池扩展|是|是|否|否|否|
|I/O 资源治理|是|否|否|否|否|  
|预读|是|否|否|否|否|
|高级扫描|是|否|否|否|否|
|延迟持续性|是|是|是|是|是|
|自动优化|是|否|否|否|否|
|批处理模式自适应联接|是|否|否|否|否|
|批处理模式内存授予反馈|是|否|否|否|否|
|多语句表值函数的交错执行|是|是|是|是|是|
|大容量插入改进|是|是|是|是|是|


<sup>1</sup> 内存中 OLTP 数据大小和列存储段缓存限制为“规模限制”部分中的版本所指定的内存量。 最大并行度是有限的。 对于 Standard Edition，索引生成的进程并行度 (DOP) 限制为 2 DOP，对于 Web 和 Express Edition，索引生成的进程并行度 (DOP) 限制为 1 DOP。 这是指在基于磁盘的表和内存优化表上创建的列存储索引。

<sup>2</sup> LocalDB 安装选项中不包括此功能。

##  <a name="RDBMSS"></a>RDBMS 安全性  
  
|功能|Enterprise|Standard|Web|Express|Express with Advanced Services|  
|-------------|----------------|--------------|---------|-------------|------------------------------------| 
|行级安全性|是|是|是|是|是|  
|始终加密|是|是|是|是|是| 
|动态数据屏蔽|是|是|是|是|是|   
|基本审核|是|是|是|是|是| 
|精细审核|是|是|是|是|是| 
|透明数据库加密|是|否|否|否|否|   
|可扩展的密钥管理|是|否|否|否|否| 
|用户定义的角色|是|是|是|是|是| 
|包含的数据库|是|是|是|是|是| 
|备份加密|是|是|否|否|否|  

##  <a name="Replication"></a> Replication  
  
|功能|Enterprise|Standard|Web|Express with Advanced Services|Express|   
|-------------|----------------|--------------|---------|------------------------------------|------------------------| 
|异类订阅服务器|是|是|否|否|否|  
|合并复制|是|是|支持（仅订阅服务器）|支持（仅订阅服务器）|支持（仅订阅服务器）|   
|Oracle 发布|是|否|否|否|否| 
|对等事务复制|是|否|否|否|否|   
|快照复制|是|是|支持（仅订阅服务器）|支持（仅订阅服务器）|支持（仅订阅服务器）|   
|SQL Server 变更跟踪|是|是|是|是|是| 
|事务复制|是|是|支持（仅订阅服务器）|支持（仅订阅服务器）|支持（仅订阅服务器）|   
|事务复制到 Azure|是|是|否|否|否|   
|事务复制可更新的订阅|是|否|否|否|否|  
  
##  <a name="SSMS"></a>管理工具  
  
|功能|Enterprise|Standard|Web|Express with Advanced Services|Express| 
|-------------|----------------|--------------|---------|------------------------------------|------------------------|  
|SQL 管理对象 (SMO)|是|是|是|是|是|  
|SQL 配置管理器|是|是|是|是|是|   
|SQL CMD（命令提示工具）|是|是|是|是|是|      
|Distributed Replay - 管理工具|是|是|是|是|否|  
|Distributed Replay - 客户端|是|是|是|否|否|  
|分布式重播 - 控制器|支持（最多 16 个客户端）|支持（1 个客户端）|支持（1 个客户端）|否|否|   
|SQL Profiler|是|是|否 <sup>1</sup>|否 <sup>1</sup>|否 <sup>1</sup>|  
|SQL Server 代理|是|是|是|否|否| 
|Microsoft System Center Operations Manager 管理包|是|是|是|否|否|  
|数据库优化顾问 (DTA)|是|是 <sup>2</sup>|是 <sup>2</sup>|否|否|      
  
 <sup>1</sup> 可以使用 SQL Server Standard 和 SQL Server Enterprise 版本探查 SQL Server Web、SQL Server Express、SQL Server Express with Tools 和 SQL Server Express with Advanced Services。  
  
 <sup>2</sup> 仅对 Standard 版本功能启用优化  
  
##  <a name="RDBMSM"></a>RDBMS 可管理性  
  
|功能|Enterprise|Standard|Web|Express with Advanced Services|Express|   
|-------------|----------------|--------------|---------|------------------------------------|------------------------|  
|用户实例|否|否|否|是|是| 
|LocalDB|否|否|否|是|否| 
|专用管理连接|是|是|是|支持（使用跟踪标志）|支持（使用跟踪标志）|   
|SysPrep 支持 <sup>1</sup>|是|是|是|是|是| 
|PowerShell 脚本支持<sup>2</sup>|是|是|是|是|是| 
|支持数据层应用程序组件操作 - 提取、部署、升级、删除|是|是|是|是|是| 
|策略自动执行（检查计划和更改）|是|是|是|否|否|   
|性能数据收集器|是|是|是|否|否| 
|能够作为多实例管理中的托管实例注册|是|是|是|否|否|   
|标准性能报表|是|是|是|否|否| 
|计划指南和计划指南的计划冻结|是|是|是|否|否|   
|使用 NOEXPAND 提示的索引视图的直接查询|是|是|是|是|是| 
|自动索引视图维护|是|是|是|否|否| 
|分布式分区视图|是|否|否|否|否| 
|并行索引操作|是|否|否|否|否|  
|查询优化器自动使用索引视图|是|否|否|否|否| 
|并行一致性检查|是|否|否|否|否| 
|SQL Server 实用工具控制点|是|否|否|否|否|    
|缓冲池扩展|是|是|否|否|否| 
  
 <sup>1</sup> 有关详细信息，请参阅 [使用 SysPrep 安装 SQL Server 的注意事项](../database-engine/install-windows/considerations-for-installing-sql-server-using-sysprep.md)。  
 
 <sup>2</sup>在 Linux 上，支持来自于 Windows 计算机、面向 Linux 上的 SQL Server 的 PowerShell 脚本。 
##  <a name="DevTools"></a>开发工具  
  
|功能|Enterprise|Standard|Web|Express with Advanced Services|Express| 
|-------------|----------------|--------------|---------|------------------------------------|------------------------| 
|Microsoft Visual Studio 集成|是|是|是|是|是| 
|Intellisense（Transact-SQL 和 MDX）|是|是|是|是|是| 
|SQL Server Data Tools (SSDT)|是|是|是|是|否|    
|MDX 编辑、调试和设计工具|是|是|否|否|否|   
  
##  <a name="Programmability"></a> Programmability  
  
|功能|Enterprise|Standard|Web|Express with Advanced Services|Express 
|-------------|----------------|--------------|---------|------------------------------------|------------------------|  
|基本 R 集成 <sup>1</sup>|是|是|是|是|否|   
|高级 R 集成 <sup>2</sup>|是|否|否|否|否| 
|基本 Python 集成|是|是|是|是|否|
|高级 Python 集成|是|否|否|否|否| 
|机器学习服务器（独立）|是|否|否|否|否|   
|PolyBase 计算节点|是|是 <sup>3</sup>|是 <sup>3</sup>|是 <sup>3</sup>|是 <sup>3</sup> | 
|PolyBase 头节点|是|否|否|否|否| 
|JSON|是|是|是|是|是|   
|查询存储|是|是|是|是|是|   
|临时|是|是|是|是|是|   
|公共语言运行时 (CLR) 集成|是|是|是|是|是|   
|本机 XML 支持|是|是|是|是|是| 
|XML 索引|是|是|是|是|是| 
|MERGE 和 UPSERT 功能|是|是|是|是|是|   
|FILESTREAM 支持|是|是|是|是|是| 
|FileTable|是|是|是|是|是| 
|日期和时间数据类型|是|是|是|是|是|  
|国际化支持|是|是|是|是|是| 
|全文和语义搜索|是|是|是|是|否| 
|查询中的语言规范|是|是|是|是|否|   
|Service Broker（消息传递）|是|是|不支持（仅客户端）|不支持（仅客户端）|不支持（仅客户端）|   
|Transact-SQL 端点|是|是|是|否|否| 
|图形|是|是|是|是|是|  


<sup>1</sup> 基本集成仅限于 2 个核心和内存中数据集。 

<sup>2</sup> 高级集成可以使用所有用于并行处理任意大小（受硬件限制）数据集的可用核心。 

<sup>3</sup> 具有多个计算节点的横向扩展需要一个头节点。


## <a name="IS"></a> Integration Services

有关 [!INCLUDE[ssNoVersion_md](../includes/ssnoversion-md.md)] 各个版本支持的 SQL Server Integration Services (SSIS) 功能的信息，请参阅 [SQL Server 各个版本支持的 Integration Services 功能](../integration-services/integration-services-features-supported-by-the-editions-of-sql-server.md)。

##  <a name="MDS"></a> Master Data Services  
 有关 [!INCLUDE[ssNoVersion_md](../includes/ssnoversion-md.md)] 各个版本支持的 [!INCLUDE[ssMDSshort_md](../includes/ssmdsshort-md.md)] 和 Data Quality Services 功能的信息，请参阅 [SQL Server 各个版本支持的 Master Data Services 和 Data Quality Services 功能](../master-data-services/master-data-services-and-data-quality-services-features-support.md)。 

  
##  <a name="DW"></a>数据仓库  
  
|功能|Enterprise|Standard|Web|Express with Advanced Services|Express|   
|-------------|----------------|--------------|---------|------------------------------------|------------------------| 
|在无需数据库的情况下创建多维数据集|是|是|否|否|否 |   
|自动生成临时和数据仓库架构|是|是|否|否|否| 
|变更数据捕获|是|是|否|否|否| 
|星型联接查询优化|是|否|否|否|否| 
|可扩展的只读 Analysis Services 配置|是|否|否|否|否| 
|针对已分区表和索引的并行查询处理|是|否|否|否|否|   
|全局批处理集成|是|否|否|否|否| 

##  <a name="SSAS"></a> Analysis Services  
  
有关 [!INCLUDE[ssNoVersion_md](../includes/ssnoversion-md.md)] 各个版本支持的 Analysis Services 功能的信息，请参阅 [SQL Server 各个版本支持的 Analysis Services 功能](../analysis-services/analysis-services-features-supported-by-the-editions-of-sql-server-2016.md)。 
  
##  <a name="BIMD"></a>BI 语义模型（多维）  
  
有关 [!INCLUDE[ssNoVersion_md](../includes/ssnoversion-md.md)] 各个版本支持的 Analysis Services 功能的信息，请参阅 [SQL Server 各个版本支持的 Analysis Services 功能](../analysis-services/analysis-services-features-supported-by-the-editions-of-sql-server-2016.md)。
   
##  <a name="BIT"></a>BI 语义模型（表格）  
  
有关 [!INCLUDE[ssNoVersion_md](../includes/ssnoversion-md.md)] 各个版本支持的 Analysis Services 功能的信息，请参阅 [SQL Server 各个版本支持的 Analysis Services 功能](../analysis-services/analysis-services-features-supported-by-the-editions-of-sql-server-2016.md)。
  
##  <a name="PPSP"></a> Power Pivot for SharePoint  
  
有关 [!INCLUDE[ssNoVersion_md](../includes/ssnoversion-md.md)] 各个版本支持的 Power Pivot for SharePoint 功能的信息，请参阅 [SQL Server 各个版本支持的 Analysis Services 功能](../analysis-services/analysis-services-features-supported-by-the-editions-of-sql-server-2016.md)。
  
##  <a name="DM"></a>数据挖掘  
  
有关 [!INCLUDE[ssNoVersion_md](../includes/ssnoversion-md.md)] 各个版本支持的数据挖掘功能的信息，请参阅 [SQL Server 各个版本支持的 Analysis Services 功能](../analysis-services/analysis-services-features-supported-by-the-editions-of-sql-server-2016.md)。
  
##  <a name="SSRS"></a> Reporting Services  
  
有关 [!INCLUDE[ssNoVersion_md](../includes/ssnoversion-md.md)] 各个版本支持的 Reporting Services 功能的信息，请参阅 [SQL Server 各个版本支持的 Reporting Services 功能](../reporting-services/reporting-services-features-supported-by-the-editions-of-sql-server-2016.md)。

##  <a name="BIC"></a>商业智能客户端  

有关 [!INCLUDE[ssNoVersion_md](../includes/ssnoversion-md.md)] 各个版本支持的商业智能客户端功能的信息，请参阅 [SQL Server 各个版本支持的 Analysis Services 功能](../analysis-services/analysis-services-features-supported-by-the-editions-of-sql-server-2016.md)或 [SQL Server 各个版本支持的 Reporting Services 功能](../reporting-services/reporting-services-features-supported-by-the-editions-of-sql-server-2016.md)。
  
##  <a name="SLS"></a>空间和位置服务  
  
|功能名称|Enterprise|Standard|Web|Express with Advanced Services|Express|  
|------------------|----------------|--------------|---------|------------------------------------|------------------------|
|空间索引|是|是|是|是|是|   
|平面和大地测量数据类型|是|是|是|是|是| 
|高级空间库|是|是|是|是|是|   
|导入/导出业界标准的空间数据格式|是|是|是|是|是|   
  
##  <a name="ADS"></a>其他数据库服务  
  
|功能名称|Enterprise|Standard|Web|Express with Advanced Services|Express|   
|------------------|----------------|--------------|---------|------------------------------------|------------------------| 
|[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 迁移助手|是|是|是|是|是|   
|数据库邮件|是|是|是|否|否| 
  
##  <a name="Other"></a>其他组件  
  
|功能名称|Enterprise|Standard|Web|Express with Advanced Services|Express|   
|------------------|----------------|--------------|---------|------------------------------------|------------------------|  
|StreamInsight|StreamInsight Premium Edition|StreamInsight Standard Edition|StreamInsight Standard Edition|否|否| 
|StreamInsight HA|StreamInsight Premium Edition|否|否|否|否|   

> [![Download SSMS](../analysis-services/media/download.png)](../ssms/download-sql-server-management-studio-ssms.md) **[Download the latest version of SQL Server Management Studio](../ssms/download-sql-server-management-studio-ssms.md)**     
  
## <a name="next-steps"></a>后续步骤 
 [SQL Server 的产品规格](https://msdn.microsoft.com/library/6445fd53-6844-4170-a86b-7fe76a9f64cb)   
 [安装 SQL Server](../database-engine/install-windows/installation-for-sql-server-2016.md)  
 
[!INCLUDE[get-help-options](../includes/paragraph-content/get-help-options.md)]

[!INCLUDE[contribute-to-content](../includes/paragraph-content/contribute-to-content.md)]
