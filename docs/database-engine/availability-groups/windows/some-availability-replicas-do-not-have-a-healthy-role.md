---
title: 一些可用性副本不具有正常运行的角色 | Microsoft Docs
ms.custom: ''
ms.date: 05/17/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql13.swb.agdashboard.agp6allroleshealthy.issues.f1
helpviewer_keywords:
- Availability Groups [SQL Server], policies
ms.assetid: 7ec5b337-7201-4a66-a541-7560f8b18784
author: MashaMSFT
ms.author: mathoma
manager: jroth
ms.openlocfilehash: 13560a2f2e610b90fcce1e37b0d5cae8e1c20057
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "66803560"
---
# <a name="some-availability-replicas-do-not-have-a-healthy-role"></a>一些可用性副本不具有正常运行的角色
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
## <a name="introduction"></a>简介  
  
|||  
|-|-|  
|**策略名称**|可用性副本角色状态|  
|**问题**|一些可用性副本不具有正常运行的角色。|  
|**类别**|**警告**|  
|**方面**|可用性组 (availability group)|  
  
## <a name="description"></a>描述  
 此策略将汇总所有可用性副本的连接状态，并且检查是否存在未处于正常运行角色的任何可用性副本。 在有可用性副本既不是主副本也不是辅助副本时，此策略处于不正常状态。 否则，该策略处于正常状态。  
  
> [!NOTE]  
>  对于此版本的 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]，与可能原因和解决方法有关的信息位于 TechNet Wiki 上的 [一些可用性副本不具有正常运行的角色](https://go.microsoft.com/fwlink/p/?LinkId=220854) 中。  
  
## <a name="possible-causes"></a>可能的原因  
 在此可用性组中，至少一个可用性副本当前不具有主角色或辅助角色。  
  
## <a name="possible-solution"></a>可能的解决方法  
 使用可用性副本策略状态查找角色不是主副本或辅助副本的可用性副本，然后解决该可用性副本上的问题。  
  
## <a name="see-also"></a>另请参阅  
 [AlwaysOn 可用性组概述 (SQL Server)](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)   
 [使用 AlwaysOn 面板 (SQL Server Management Studio)](../../../database-engine/availability-groups/windows/use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  
