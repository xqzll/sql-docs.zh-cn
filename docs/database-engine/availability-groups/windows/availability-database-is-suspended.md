---
title: 可用性组的可用性数据库挂起
description: 确定 Always On 可用性组中的数据库挂起的可能原因。
ms.custom: seodec18
ms.date: 05/17/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql13.swb.agdashboard.drp1notsuspended.issues.f1
helpviewer_keywords:
- Availability Groups [SQL Server], policies
ms.assetid: 6baee70f-848c-4e86-b20d-78875c0f82cb
author: MashaMSFT
ms.author: mathoma
manager: jroth
ms.openlocfilehash: 4760bd036c4946ee8fe0b924043ab6188c009576
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "66789414"
---
# <a name="availability-database-is-suspended-for-an-availability-group"></a>可用性组的可用性数据库挂起
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
## <a name="introduction"></a>简介  
  
|||  
|-|-|  
|**策略名称**|可用性数据库挂起状态|  
|**问题**|可用性数据库挂起。|  
|**类别**|**警告**|  
|**方面**|可用性数据库|  
  
## <a name="description"></a>描述  
 此策略检查辅助数据库（也称为“辅助数据库副本”）的数据移动状态。 数据移动挂起时，此策略处于不正常状态。 否则，该策略处于正常状态。  
  
> [!NOTE]  
>  对于此版本的 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]，与可能原因和解决方法有关的信息位于 [TechNet Wiki 上的可用性数据库挂起](https://go.microsoft.com/fwlink/p/?LinkId=220860) 中。  
  
## <a name="possible-causes"></a>可能的原因  
 由于下列原因，此可用性数据库上的数据同步可能已挂起：  
  
-   由于错误，系统可能已挂起数据同步。  
  
-   数据库管理员出于维护目的可能已挂起数据同步。  
  
## <a name="possible-solution"></a>可能的解决方法  
 继续数据同步。 如果问题仍然存在，请在事件日志中查看该可用性组，然后诊断系统挂起数据移动的原因。  
  
## <a name="see-also"></a>另请参阅  
 [AlwaysOn 可用性组概述 (SQL Server)](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)   
 [使用 AlwaysOn 面板 (SQL Server Management Studio)](../../../database-engine/availability-groups/windows/use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  
