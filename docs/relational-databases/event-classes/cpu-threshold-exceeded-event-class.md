---
title: CPU Threshold Exceeded 事件类 | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- CPU Threshold Exceeded Event Class
ms.assetid: eb106f7d-baa3-4a2b-96b2-f9fe0844057d
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 569b085d28a0339927049fca0d758286dd1b6e8d
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "62686098"
---
# <a name="cpu-threshold-exceeded-event-class"></a>CPU Threshold Exceeded 事件类
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  CPU Threshold Exceeded 事件类指示资源调控器检测到超出为 REQUEST_MAX_CPU_TIME_SEC 指定的 CPU 阈值的查询。  
  
> [!NOTE]  
>  此事件的检测时间间隔为五秒。 这就保证如果查询超出指定的限制至少五秒，将生成事件。 然而，如果查询超出指定的阈值少于五秒，则其检测可能会丢失，具体取决于查询计时和上次检测清扫的时间。  
  
## <a name="cpu-threshold-exceeded-data-columns"></a>CPU Threshold Exceeded 数据列  
  
|数据列名称|数据类型|描述|列 ID|可筛选|  
|----------------------|---------------|-----------------|---------------|----------------|  
|CPU|**int**|CPU 使用率，以毫秒为单位。|18|是|  
|EventClass|**int**|214|27|否|  
|EventSubClass|**int**|CPU 限制冲突。|21|是|  
|GroupID|**int**|发生冲突的组 ID。|66|是|  
|OwnerID|**int**|导致冲突的进程的 SPID。|58|是|  
|SPID|**int**|激发此事件的服务器进程的 ID。<br /><br /> 注意：如果系统线程将验证 CPU 使用率作为后台任务，则此 ID 可能与实际用户的 SPID 不同。|12|是|  
|StartTime|**datetime**|此事件的激发时间。|14|是|  
  
## <a name="see-also"></a>另请参阅  
 [sp_trace_setevent (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql.md)  
  
  
