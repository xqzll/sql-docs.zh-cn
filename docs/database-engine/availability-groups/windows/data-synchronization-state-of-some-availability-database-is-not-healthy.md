---
title: 一些可用性数据库的数据同步状态不正常
description: 标识 AlwaysOn 可用性组中的一些数据库的数据同步状态不正常的可能原因。
ms.custom: seodec18
ms.date: 05/17/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql13.swb.agdashboard.drp3datasynchealthy.issues.f1
helpviewer_keywords:
- Availability Groups [SQL Server], policies
ms.assetid: 89f95d15-33c6-4768-bccd-9dbf8c4f49a9
author: MashaMSFT
ms.author: mathoma
manager: jroth
ms.openlocfilehash: 1a1c768b431e1e5c50e4c100f1af23d50eb63f48
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "66793396"
---
# <a name="data-synchronization-state-of-some-availability-database-is-not-healthy"></a>一些可用性数据库的数据同步状态不正常
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
## <a name="introduction"></a>简介  
  
|||  
|-|-|  
|**策略名称**|可用性副本数据同步状态|  
|**问题**|一些可用性数据库的数据同步状态不正常。|  
|**类别**|**警告**|  
|**方面**|可用性副本|  
  
## <a name="description"></a>描述  
 此策略检查可用性数据库（也称为“数据库副本”）的数据同步状态。 当数据同步状态为 NOT SYNCHRONIZING 或同步提交数据库副本的状态不为 SYNCHRONIZED 时，此策略处于不正常状态。  
  
> [!NOTE]  
>  对于此版本的 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]，与可能原因和解决方法有关的信息位于 TechNet Wiki 上的 [可用性数据库的数据同步状态不正常](https://go.microsoft.com/fwlink/p/?LinkId=220863) 中。  
  
## <a name="possible-causes"></a>可能的原因  
 副本上至少一个可用性数据库处于不正常数据同步状态。 如果该副本是异步-提交可用性副本，则所有可用性数据库都应该处于“正在同步”状态。 如果这是同步提交可用性副本，所有可用性数据库应处于 SYNCHRONIZED 状态。 此问题可能由以下原因导致：  
  
-   可用性副本可能已断开连接。  
  
-   数据移动可能已挂起。  
  
-   数据库可能无法访问。  
  
-   可能存在由于网络滞后或主副本/辅助副本上的负载导致的临时延迟问题。  
  
## <a name="possible-solution"></a>可能的解决方法  
 解决所有连接或数据移动挂起问题。 使用 SQL Server Management Studio 查看此问题的事件，查找数据库错误。 按照特定错误的故障排除步骤操作。  
  
## <a name="see-also"></a>另请参阅  
 [AlwaysOn 可用性组概述 (SQL Server)](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)   
 [使用 AlwaysOn 面板 (SQL Server Management Studio)](../../../database-engine/availability-groups/windows/use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  
