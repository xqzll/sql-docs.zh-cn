---
title: 可用性组未准备好进行自动故障转移
description: 确定 Always On 可用性组未准备好进行故障转移的可能原因。
ms.custom: seodec18
ms.date: 05/17/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql13.swb.agdashboard.agp3autofailover.issues.f1
helpviewer_keywords:
- Availability Groups [SQL Server], policies
ms.assetid: 28261014-342c-442a-bd89-6d04b8d4e8b7
author: MashaMSFT
ms.author: mathoma
manager: jroth
ms.openlocfilehash: 2107137f9b50a289e056042446c2d763f0b7cd23
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "66800127"
---
# <a name="always-on-availability-group-is-not-ready-for-automatic-failover"></a>Always On 可用性组未准备好进行自动故障转移
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
## <a name="introduction"></a>简介  
  
|||  
|-|-|  
|**策略名称**|可用性组自动故障转移就绪|  
|**问题**|可用性组未准备好进行自动故障转移。|  
|**类别**|**严重**|  
|**方面**|可用性组 (availability group)|  
  
## <a name="description"></a>描述  
 此策略检查验证可用性组是否至少具有一个故障转移就绪的辅助副本。 当主副本的故障转移模式为自动但是可用性组中没有故障转移就绪的辅助副本时，此策略处于不正常状态并引发警报。  
  
 当至少一个辅助副本的自动故障转移就绪时，此策略处于正常状态。  
  
> [!NOTE]  
>  对于此版本的 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]，与可能原因和解决方法有关的信息位于 TechNet Wiki 上的 [可用性组未准备好进行自动故障转移](https://go.microsoft.com/fwlink/p/?LinkId=220851) 中。  
  
## <a name="possible-causes"></a>可能的原因  
 可用性组未准备好进行自动故障转移。 将主副本配置为自动故障转移，但是辅助副本未准备好进行自动故障转移。 为自动故障转移配置的辅助副本可能不可用或其数据同步状态当前不是 SYNCHRONIZED。  
  
## <a name="possible-solutions"></a>可能的解决方法  
 以下是此问题的可能解决方法：  
  
-   验证至少将一个辅助副本配置为自动故障转移。 如果没有一个辅助副本被配置为自动故障转移，请将辅助副本的配置更新为具有异步提交功能的自动故障转移目标。  
  
-   使用此策略验证数据是否处于同步状态以及自动故障转移目标是否 SYNCHRONIZED，然后解决可用性副本的问题。  
  
## <a name="see-also"></a>另请参阅  
 [AlwaysOn 可用性组概述 (SQL Server)](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)   
 [使用 AlwaysOn 面板 (SQL Server Management Studio)](../../../database-engine/availability-groups/windows/use-the-always-on-dashboard-sql-server-management-studio.md)  
  
  
