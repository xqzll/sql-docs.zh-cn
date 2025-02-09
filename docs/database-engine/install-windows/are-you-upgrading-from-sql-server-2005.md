---
title: 是否从 SQL Server 2005、2008 或 2008R2 进行升级？ | Microsoft Docs
ms.custom: ''
ms.date: 07/18/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
ms.assetid: ad40e66f-71fe-4ee6-9ce3-17127e7b1d7a
author: MashaMSFT
ms.author: mathoma
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions'
manager: jroth
ms.openlocfilehash: 4813ca33bca9f03d94fe6f926a7af612b217fd90
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "66795024"
---
# <a name="are-you-upgrading-from-sql-server-2005-2008-or-2008r2"></a>是否从 SQL Server 2005、2008 或 2008R2 进行升级？

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]
 
 对 SQL Server 的扩展支持已结束，这是需立即升级到较新版本的 SQL Server 和 Azure SQL 数据库的原因之一。 通过升级，你不仅可以维护安全性和合规性、获取突破性的性能，还可以优化你的数据平台基础结构。  
  
 有关计划和自动化升级或迁移的详细信息、指南和工具，请参阅 [SQL Server 2005 终止支持](https://www.microsoft.com/sql-server/sql-server-2005)和 [SQL Server 2008 终止支持](https://www.microsoft.com/cloud-platform/windows-sql-server-2008)。  
  
## <a name="why-upgrade"></a>升级理由  
  
> [!IMPORTANT]  
>  对 SQL Server 2005 的延长支持已于 2016 年 4 月 12 日结束。 如果 2016 年 4 月 12 日后仍在运行 SQL Server 2005，将不会再收到安全更新。  

> [!IMPORTANT]  
>  对于 SQL Server 2008 和 2008r2 的扩展支持将于 2019 年 7 月 9 日结束。 如果 2019 年 7 月 9 日后仍在运行 SQL Server 2008 或 2008R2，将不会再收到安全更新。 有关详细信息，请查看博客[宣布推出适用于 SQL Server 2008 的新选项](https://azure.microsoft.com/blog/announcing-new-options-for-sql-server-2008-and-windows-server-2008-end-of-support/)。  
  
## <a name="choose-your-upgrade-option"></a>选择升级选项  
如果要从较旧版本的 SQL Server 升级关系数据库，下面是用于 Microsoft 平台上关系存储的选项。  
  
若要查看有关这些选项的更全面分析，请 [单击此处](https://sql05upgrade.azurewebsites.net/)。  
  
|关系存储选项|优势|要考虑的其他因素|  
|-------------------------------|--------------|-------------------------------|  
|**本地 SQL Server**<br /><br /> 对于任何类型的数据库应用程序（从交易系统到数据仓库），请考虑此选项。|因为你管理硬件和软件，因此你对功能和可伸缩性具有最大控制权。<br /><br /> 如果从 SQL Server 的旧实例升级，这是最相似的环境。|你必须做出最大的前期投资并进行日常管理，因为你需要购买、维护和管理你自己的硬件和软件。<br /><br /> 有关详细信息，请参阅 [SQL Server](https://www.microsoft.com/evalcenter/evaluate-sql-server-2017-rtm)。|  
|**Azure 虚拟机上托管的 SQL Server**<br /><br /> 如果你需要以下内容，请考虑此选项：<br /><br /> 迁移到托管环境的好处。<br /><br /> 对操作环境的控制。<br /><br /> SQL Server 的熟悉功能集。|可以从虚拟机映像库快速进行部署。<br /><br /> 获得完整的 SQL Server 功能集。<br /><br /> 节约硬件和服务器软件的成本。 只需支付每小时的使用费用。|必须配置并管理 SQL Server 和操作系统软件。<br /><br /> <br /><br /> 有关详细信息，请参阅 [Azure 虚拟机上的 SQL Server 概述](https://azure.microsoft.com/documentation/articles/virtual-machines-sql-server-infrastructure-services/)。<br /><br /> 有关迁移的详细信息，请参阅 [将数据库迁移到 Azure VM 上的 SQL Server](https://azure.microsoft.com/documentation/articles/virtual-machines-migrate-onpremises-database/)。|  
|**Azure SQL Database 托管的数据库服务**<br /><br /> 如果想要实现较少维护的低成本解决方案，请考虑此选项。<br /><br /> 此选项非常适用于不要求一直需要相同容量的应用，或必须提供外部访问的应用。|可以快速部署并轻松纵向扩展。<br /><br /> 只需支付每小时的使用费用。<br /><br /> 该服务的成本不仅包括存储，还包括高可用性和自动执行的备份。|Azure SQL Database 缺少某些在托管的云环境中不适用的 SQL Server 功能。 有关详细信息，请参阅 [Azure SQL 数据库 Transact-SQL 信息](https://azure.microsoft.com/documentation/articles/sql-database-transact-sql-information/)。<br /><br /> 相较于 SQL Server 的 524 PB，Azure SQL Database 还具有 4 TB 的最大数据库大小。 有关详细信息，请参阅[适用于单一数据库的资源限制](https://docs.microsoft.com/azure/sql-database/sql-database-vcore-resource-limits-single-databases)<br /><br /> 有关 SQL 数据库的详细信息，请参阅 [Azure SQL 数据库概述](https://azure.microsoft.com/services/sql-database/)和 [Azure SQL 数据库文档](https://docs.microsoft.com/azure/sql-database/)。<br /><br /> 有关迁移的详细信息，请参阅 [将 SQL Server 数据库迁移到 Azure SQL 数据库](https://azure.microsoft.com/documentation/articles/sql-database-cloud-migrate/)。|  
  
 你还可能想要针对某些数据和应用程序考虑使用非关系或 NoSQL 解决方案。  
  
|非关系解决方案|优势|  
|------------------------------|--------------|  
|**Azure Cosmos DB**<br /><br /> 对于新式、可伸缩、移动和 Web 应用程序（使用 JSON 数据并要求结合使用功能强大的查询和事务数据处理），请考虑此选项。<br /><br /> 有关详细信息，请参阅 [Cosmos DB](https://azure.microsoft.com/services/cosmos-db/)。<br /><br /> 有关导入数据的信息，请参阅[将数据导入到 Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/import-data/)。|已为你的文档编制索引，你可以使用熟悉的 SQL 语法来查询它们。<br /><br /> 该数据库未设计架构。<br /><br /> 无需重新生成索引即可向文档添加属性。<br /><br /> 直接在数据库引擎内获取 JSON 和 JavaScript 支持。<br /><br /> 获取对地理空间数据和集成其他 Azure 服务（包括 Azure Search、HDInsight 和 Data Factory）的本机支持。<br /><br /> 获得低延迟、高性能存储并保留吞吐量级别。|  
|**Azure 表存储**<br /><br /> 请考虑此选项以使用经济高效的解决方案存储数千兆半结构化数据。<br /><br /> 有关详细信息，请参阅 [表存储](https://azure.microsoft.com/services/storage/tables/)。|无需使数据离线即可扩展你的应用和表架构。<br /><br /> 无需分片数据集即可纵向扩展。<br /><br /> 获取跨多个区域复制数据的异地冗余存储。|  
  
## <a name="plan-your-upgrade"></a>规划升级  
  
-   阅读以下 SQL Server 团队博客文章系列中有关如何规划升级 SQL Server 2005 实例的内容。 
    - 规划从 SQL Server 2005 进行有效的升级：[步骤 1/3](https://blogs.technet.com/b/dataplatforminsider/archive/2015/12/10/planning-an-efficient-upgrade-from-sql-server-2005-step-1-of-3.aspx)、[步骤 2/3](https://blogs.technet.com/b/dataplatforminsider/archive/2015/12/15/planning-an-efficient-upgrade-from-sql-server-2005-step-2-of-3.aspx)、[步骤 3/3](https://blogs.technet.com/b/dataplatforminsider/archive/2015/12/17/planning-an-efficient-upgrade-from-sql-server-2005-step-3-of-3.aspx)
- 做好应对 [SQL Server 2008 终止支持](https://www.microsoft.com/sql-server/sql-server-2008)的准备。
  
-   查看[规划 SQL Server 安装](../../sql-server/install/planning-a-sql-server-installation.md)中的要求和注意事项，包括[安装 SQL Server 的硬件和软件要求](../../sql-server/install/hardware-and-software-requirements-for-installing-sql-server.md)。  
  
-   阅读有关如何升级的内容。  
  
    -   查看[升级数据库引擎](../../database-engine/install-windows/upgrade-database-engine.md)一文中的可用升级方法并了解计划和测试方法。  
  
        > [!IMPORTANT]  
        >- 不能就地将 SQL Server 2005 实例升级到 SQL Server 2017 服务器。 必须先安装 SQL Server 2017 的实例，然后再将 SQL Server 2005 数据库迁移到新安装。 有关详细信息，请参阅[选择数据库引擎升级方法](../../database-engine/install-windows/choose-a-database-engine-upgrade-method.md)一文中的“新安装升级”部分。  
        >- 可以将现有的 SQL 2008 和 SQL 2008r2 升级到 SQL 2017。 有关详细信息，请参阅[支持的版本及版本升级](supported-version-and-edition-upgrades-2017.md)。 


-    有关计划和自动化升级或迁移的详细信息、指南和工具，请参阅 [SQL Server 2005 终止支持](https://www.microsoft.com/sql-server/sql-server-2005)和 [SQL Server 2008 终止支持](https://www.microsoft.com/cloud-platform/windows-sql-server-2008)。  
  
## <a name="get-sql-server"></a>获取 SQL Server  
 若要下载评估版 SQL Server，请单击 [SQL Server 下载](https://www.microsoft.com/sql-server/sql-server-downloads)。  
  
## <a name="next-steps"></a>Next Steps  
 [SQL Server 2017](https://www.microsoft.com/sql-server/sql-server-2017)   
 [SQL Server 2005 终止支持](https://www.microsoft.com/sql-server/sql-server-2005)   
 [SQL Server 2008 终止支持](https://www.microsoft.com/cloud-platform/windows-sql-server-2008)
  
  
