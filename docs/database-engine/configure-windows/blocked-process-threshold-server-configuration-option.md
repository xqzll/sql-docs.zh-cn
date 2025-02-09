---
title: blocked process threshold 服务器配置选项 | Microsoft Docs
ms.custom: ''
ms.date: 03/02/2017
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- thresholds [SQL Server]
- blocked process threshold option
ms.assetid: 3d46d143-bc6a-4220-8b55-6baa37547c25
author: MikeRayMSFT
ms.author: mikeray
manager: jroth
ms.openlocfilehash: 7b0ec5d159a333b65ae2a67fd5737c17771792a9
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "66786818"
---
# <a name="blocked-process-threshold-server-configuration-option"></a>blocked process threshold 服务器配置选项
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  **blocked process threshold** 选项用于指定阈值（以秒为单位），超过该阈值将生成阻塞的进程报告。 该阈值可介于 0 到 86,400 之间。 默认情况下，不生成阻塞的进程报告。 对于系统任务或正在等待未生成可检测死锁的资源的任务，不生成该事件。  
  
 可以定义一个生成该事件时执行的 [警报](../../ssms/agent/alerts.md) 。 例如，可以选择通知管理员采取相应的操作来处理阻塞情况。  
  
 阻塞的进程阈值使用死锁监视器后台线程监视等待时间大于（或数倍于）配置的阈值的任务列表。 每个报告间隔中，为每个阻塞的任务生成一次事件。  
  
 已通过最大努力完成了阻塞的进程报告。 不保证报表的数据始终为实时数据，也不保证报表数据接近实时。  
  
 该设置立即生效，无需停止并重新启动服务器。  
  
## <a name="examples"></a>示例  
 下面的示例将 `blocked process threshold` 设置为 `20` 秒，超过该阈值将为阻塞的每个任务生成阻塞的进程报告。  
  
```  
sp_configure 'show advanced options', 1 ;  
GO  
RECONFIGURE ;  
GO  
sp_configure 'blocked process threshold', 20 ;  
GO  
RECONFIGURE ;  
GO  
```  
  
## <a name="see-also"></a>另请参阅  
 [sp_trace_setevent (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql.md)   
 [Blocked Process Report 事件类](../../relational-databases/event-classes/blocked-process-report-event-class.md)  
  
  
