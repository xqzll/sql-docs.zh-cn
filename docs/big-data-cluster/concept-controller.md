---
title: 什么是控制器？
titleSuffix: SQL Server big data clusters
description: 本指南介绍了 SQL Server 2019 大数据群集 （预览版） 的控制器。
author: mihaelablendea
ms.author: mihaelab
ms.reviewer: mikeray
manager: jroth
ms.date: 06/26/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 076cc40c09d4b086ae7a416ac1cc5ccbcc16a20a
ms.sourcegitcommit: e0c55d919ff9cec233a7a14e72ba16799f4505b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2019
ms.locfileid: "67729173"
---
# <a name="what-is-the-controller-on-a-sql-server-big-data-cluster"></a>什么是 SQL Server 大数据群集上的控制器？

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

控制器托管用于部署和管理大数据群集的核心逻辑。 它负责与 Kubernetes，是在群集和 HDFS 和 Spark 等其他组件的一部分的 SQL Server 实例的所有交互。

控制器服务提供了以下的核心功能：

- 管理群集生命周期： 群集启动和删除、 更新配置
- 管理主 SQL Server 实例
- 管理计算、 数据和存储池
- 公开监视工具来观察群集的状态
- 公开来检测和修复意外的问题的故障排除工具
- 管理群集安全性：
  - 确保安全的群集终结点
  - 管理用户和角色
  - 配置群集内通信的凭据

## <a name="deploying-the-controller-service"></a>部署控制器服务

控制器是部署并托管在客户要构建大数据群集相同的 Kubernetes 命名空间中。 此服务安装群集启动，使用过程中由 Kubernetes 管理员**mssqlctl**命令行实用程序。 有关详细信息，请参阅[开始使用 SQL Server 大数据群集](deploy-get-started.md)。

建设工作流将基于 Kubernetes 的布局包括中所述的所有组件的完全正常运行的 SQL Server 大数据群集[概述](big-data-cluster-overview.md)一文。 启动工作流首先创建控制器服务，这部署后，控制器服务会协调安装和配置 master、 计算、 数据和存储池的服务部分的其余部分。

## <a name="managing-the-cluster-through-the-controller-service"></a>控制器服务通过群集进行管理

你可以管理通过使用控制器服务群集**mssqlctl**命令。 如果 pod 等其他 Kubernetes 对象部署到相同的命名空间时，它们是未托管或由控制器服务监视。 此外可以使用**kubectl**用于管理级别的 Kubernetes 群集的命令。 有关详细信息，请参阅[监视和故障排除 SQL Server 大数据群集](cluster-troubleshooting-commands.md)。

在控制器和大数据群集创建的 Kubernetes 对象 （有状态集，pod、 机密等） 驻留在专用的 Kubernetes 命名空间。 控制器服务将由 Kubernetes 群集管理器来管理该命名空间中的所有资源授予的权限。  初始群集部署使用的过程中自动配置此方案中的 RBAC 策略**mssqlctl**。

### <a name="mssqlctl"></a>mssqlctl

**mssqlctl**是启用群集管理员若要启动和管理控制器服务公开的 REST Api 通过大数据群集以 Python 编写的命令行实用程序。

## <a name="controller-service-security"></a>控制器服务安全性

与控制器服务的所有通信通过 HTTPS 都执行通过 REST API。 生成自签名的证书将会自动为你在启动时。 

向控制器服务终结点进行身份验证基于用户名和密码。 这些凭据都在群集启动时使用环境变量的输入预配`CONTROLLER_USERNAME`和`CONTROLLER_PASSWORD`。

> [!NOTE]
> 必须提供密码即遵守[SQL Server 密码复杂性要求](https://docs.microsoft.com/sql/relational-databases/security/password-policy?view=sql-server-2017)。

## <a name="next-steps"></a>后续步骤

若要了解有关 SQL Server 大数据群集的详细信息，请参阅以下资源：

- [什么是 SQL Server 2019 大数据群集？](big-data-cluster-overview.md)
- [研讨会：Microsoft SQL Server 大数据群集体系结构](https://github.com/Microsoft/sqlworkshops/tree/master/sqlserver2019bigdataclusters)
