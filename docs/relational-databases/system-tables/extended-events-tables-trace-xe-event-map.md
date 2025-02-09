---
title: trace_xe_event_map (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- trace_xe_event_map_TSQL
- trace_xe_event_map
dev_langs:
- TSQL
helpviewer_keywords:
- trace_xe_event_map
- extended events [SQL Server], tables
ms.assetid: 537aa292-3540-47e8-be28-56dc01abc343
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: cc823459c701bd0045e594f753a803a0a092a244
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "62817103"
---
# <a name="extended-events-tables---tracexeeventmap"></a>扩展事件表 - trace_xe_event_map
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  映射到 SQL 跟踪事件类的每个扩展事件各占一行。 此表存储在 master 数据库的 sys 架构中。  
  
|列名|数据类型|Description|  
|-----------------|---------------|-----------------|  
|trace_event_id|**smallint**|正在映射的 SQL 跟踪事件类的 ID。|  
|package_name|**nvarchar(60)**|映射事件所在的扩展事件包的名称。|  
|xe_event_name|**nvarchar(60)**|映射到 SQL 跟踪事件类的“扩展事件”事件的名称。|  
  
## <a name="remarks"></a>备注  
 您可以使用以下查询确定与 SQL 跟踪事件类等效的“扩展事件”事件：  
  
```  
SELECT te.name, xe.package_name, xe.xe_event_name  
FROM sys.trace_events AS te  
LEFT JOIN sys.trace_xe_event_map AS xe  
   ON te.trace_event_id = xe.trace_event_id  
WHERE xe.trace_event_id IS NOT NULL  
```  
  
 并非所有事件类都有等效的“扩展事件”事件。 您可以使用以下查询列出没有扩展事件等效项的事件类：  
  
```  
SELECT te.trace_event_id, te.name  
FROM sys.trace_events AS te  
LEFT JOIN sys.trace_xe_event_map AS xe  
   ON te.trace_event_id = xe.trace_event_id  
WHERE xe.trace_event_id IS NULL  
```  
  
 在前面的查询中，返回的大多数事件类都与审核相关。 建议您使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Audit 进行审核。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Audit 使用扩展事件来帮助创建审核。 有关详细信息，请参阅 [SQL Server Audit（数据库引擎）](../../relational-databases/security/auditing/sql-server-audit-database-engine.md)。  
  
## <a name="see-also"></a>请参阅  
 [trace_xe_action_map (Transact-SQL)](../../relational-databases/system-tables/extended-events-tables-trace-xe-action-map.md)  
  
  
