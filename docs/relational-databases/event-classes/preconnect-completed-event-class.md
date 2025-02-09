---
title: PreConnect:Completed 事件类 | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- PreConnect:Completed Event Class
ms.assetid: 7ed2f620-6511-4985-9961-d2927c2b1759
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 3d44fd5f6e0d2196af84f890fcbc591e10c036f6
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "62693803"
---
# <a name="preconnectcompleted-event-class"></a>PreConnect:Completed 事件类
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  PreConnect:Completed 事件类指示何时 LOGON 触发器或资源调控器分类器函数结束执行。  
  
## <a name="preconnectcompleted-event-class-data-columns"></a>PreConnect:Completed 事件类的数据列  
  
|数据列名称|数据类型|描述|列 ID|可筛选|  
|----------------------|---------------|-----------------|---------------|----------------|  
|EventClass|**int**|216|27|否|  
|SPID|**int**|激发此事件的服务器进程的 ID。|12|是|  
|EventSubClass|**int**|1 表示用户定义的分类器函数。|21|是|  
|StartTime|**datetime**|用户定义的分类器函数开始时间。|14|是|  
|EndTime|**datetime**|用户定义的分类器函数开始时间。|15|是|  
|Duration|**bigint**|分类器函数所用的时间，以微秒为单位。|13|是|  
|ObjectID|**int**|用户定义的分类器对象的 ID。|22|是|  
|CPU|**int**|CPU 使用率，以毫秒为单位。|18|是|  
|Reads|**int**|逻辑读取数。|16|是|  
|Writes|**int**|逻辑写入数。|17|是|  
|GroupID|**int**|分类工作负荷组的 ID。|66|是|  
|错误|**int**|如果用户定义的分类器函数无法执行，则为最后一个错误号。|31|是|  
|State|**int**|最后一个错误的状态。|30|是|  
|TargetUserName|**sysname**|如果系统无法找到相应的活动组，则为用户定义的分类器函数的返回值（工作负荷组名）。 否则，此列设为 NULL.|39|是|  
|ObjectName|**nvarchar(256)**|用户定义的分类器函数的两部分名称。 例如，dbo.classifier。|34|是|  
  
## <a name="see-also"></a>另请参阅  
 [扩展事件](../../relational-databases/extended-events/extended-events.md)   
 [PreConnect:Starting 事件类](../../relational-databases/event-classes/preconnect-starting-event-class.md)   
 [资源调控器](../../relational-databases/resource-governor/resource-governor.md)  
  
  
