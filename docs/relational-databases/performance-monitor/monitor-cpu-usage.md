---
title: 监视 CPU 使用率 | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- monitoring performance [SQL Server], CPU usage
- tuning databases [SQL Server], CPU usage
- processors [SQL Server], monitoring usage
- database performance [SQL Server], CPU usage
- monitoring CPU usage [SQL Server]
- server performance [SQL Server], CPU usage
- database monitoring [SQL Server], CPU usage
- monitoring [SQL Server], CPU usage
- processors [SQL Server]
- CPU [SQL Server], monitoring
- monitoring server performance [SQL Server], CPU usage
ms.assetid: 2a02a3b6-07b2-4ad0-8a24-670414d19812
author: julieMSFT
ms.author: jrasnick
manager: craigg
ms.openlocfilehash: 0f398fc02392331a64fd5514e0e8d8e2d7e6deeb
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "63047451"
---
# <a name="monitor-cpu-usage"></a>监视 CPU 使用率
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  定期监视 Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例以确定 CPU 使用率是否在正常范围内。 持续的高 CPU 使用率可能表明需要升级 CPU 或需要增加多个处理器。 或者，高 CPU 使用率也可能表明应用程序的调整或设计不良。 优化应用程序可以降低 CPU 的使用率。  
  
 一个确定 CPU 使用率的有效方法是使用系统监视器中的 **Processor:% Processor Time** 计数器。 该计数器监视 CPU 执行非闲置线程所用的时间。 持续 80% 到 90% 的状态可能表明需要升级 CPU 或需要增加更多的处理器。 对于多处理器系统，应为每个处理器监视一个该计数器的独立实例。 这一值代表了在一个特定处理器上的处理器时间之和。 若要确定所有处理器的平均时间，请改用 **System: %Total Processor Time** 计数器。  
  
 另外还可以监视下列计数器来监视处理器的使用率：  
  
-   **Processor: % Privileged Time**  
  
     对应于处理器执行 Microsoft Windows 内核命令（例如处理 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] I/O 请求）所用时间的百分比。 如果 **Physical Disk** 计数器的值很高时该计数器的值也一直很高，则考虑安装速度更快或效率更高的磁盘子系统。  
  
    > [!NOTE]  
    >  不同的磁盘控制器和驱动程序所用的内核处理时间不同。 高效的控制器和驱动程序所用的特权时间较少，可留出更多的处理器时间给用户应用程序，从而提高总体的吞吐量。  
  
-   **Processor: %User Time**  
  
     对应于处理器执行用户进程（例如 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]）所用时间的百分比。  
  
-   **系统：Processor Queue Length**  
  
     对应于等待处理器时间的线程数。 当一个进程的线程需要的处理器循环数超过可获得的循环数时，就产生了处理器瓶颈。 如果有很多进程在争用处理器时间，可能需要安装一个速度更快的处理器。 如果使用的是多处理器系统，则可以增加一个处理器。  
  
 检查处理器使用率时，需考虑 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例执行的工作类型。 如果 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 正在做大量的运算，例如包含聚合的查询，或受内存限制但不需要磁盘 I/O 的查询，此时所用的处理器时间可能是 100%。 如果这导致其他应用程序的性能降低，应尝试改变工作负荷。 例如，让计算机只运行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]实例。  
  
 若使用率为 100% 左右（表示在处理大量的客户端请求），可能表示进程正在排队，等待处理器时间，并因而导致出现瓶颈。 可以通过增加速度更快的处理器来解决这一问题。  
  
  
