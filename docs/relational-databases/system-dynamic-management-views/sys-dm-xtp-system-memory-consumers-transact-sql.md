---
title: sys.dm_xtp_system_memory_consumers (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_xtp_system_memory_consumers
- sys.dm_xtp_system_memory_consumers_TSQL
- sys.dm_xtp_system_memory_consumers
- dm_xtp_system_memory_consumers_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_xtp_system_memory_consumers dynamic management view
ms.assetid: 9eb0dd82-7920-42e0-9e50-7ce6e7ecee8b
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: ebc5947611129086952394f157c6173a3b4efcf0
ms.sourcegitcommit: e366f702c49d184df15a9b93c2c6a610e88fa0fe
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/11/2019
ms.locfileid: "67826305"
---
# <a name="sysdmxtpsystemmemoryconsumers-transact-sql"></a>sys.dm_xtp_system_memory_consumers (Transact-SQL)
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

  报告 [!INCLUDE[hek_2](../../includes/hek-2-md.md)] 的系统级内存消耗者。 用于这些消耗者的内存需要从默认池 （当分配的用户线程上下文中） 或内部池 （如果此分配是在系统线程的上下文中）。  
  
```  
-- system memory consumers @ instance  
select * from sys.dm_xtp_system_memory_consumers  
```  
  
 有关详细信息，请参阅[内存中 OLTP&#40;内存中优化&#41;](../../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)。  
  
|列名|type|描述|  
|-----------------|----------|-----------------|  
|memory_consumer_id|**bigint**|内存消耗者的内部 ID。|  
|memory_consumer_type|**int**|一个整数，表示有下列值之一的内存消耗者的类型：<br /><br /> 0-它应不会显示。 聚合两个或多个使用者的内存使用量。<br /><br /> 1-后备链：跟踪系统后备链内存占用情况。<br /><br /> 2-VARHEAP:跟踪长度可变的堆内存占用情况。<br /><br /> 4-IO 页池：跟踪用于 IO 操作的系统页池内存占用情况。|  
|memory_consumer_type_desc|**nvarchar(16)**|对内存消耗者类型的说明：<br /><br /> 0-它应不会显示。<br /><br /> 1-后备链<br /><br /> 2 - VARHEAP<br /><br /> 4 - PGPOOL|  
|memory_consumer_desc|**nvarchar(64)**|对内存消耗者实例的说明：<br /><br /> VARHEAP: <br />系统堆。 通用。 当前仅用于分配垃圾收集工作项。<br />-或-<br />后备链堆。 后备链在后备链表中包含的项目数达到预先确定的上限（通常约 5,000 项）时使用。<br /><br /> PGPOOL:IO 系统池有有三种不同的大小：系统 4k 页池、 系统 64k 页池和系统 256k 页池。|  
|lookaside_id|**bigint**|线程本地后备链内存提供程序的 ID。|  
|pagepool_id|**bigint**|线程本地页池内存提供程序的 ID。|  
|allocated_bytes|**bigint**|为此消耗者保留的字节数。|  
|used_bytes|**bigint**|此消耗者使用的字节数。 仅适用于 varheap 内存消耗者。|  
|allocation_count|**int**|分配的数量。|  
|partition_count|**int**|仅限内部使用。|  
|sizeclass_count|**int**|仅限内部使用。|  
|min_sizeclass|**int**|仅限内部使用。|  
|max_sizeclass|**int**|仅限内部使用。|  
|memory_consumer_address|**varbinary**|消耗者的内部地址。|  
  
## <a name="permissions"></a>权限  
 要求对服务器拥有 VIEW SERVER STATE 权限。  
  
## <a name="user-scenario"></a>使用方案  
  
```  
-- system memory consumers @ instance  
selectmemory_consumer_type_desc,   
allocated_bytes/1024 as allocated_bytes_kb,   
used_bytes/1024 as used_bytes_kb, allocation_count  
from sys.dm_xtp_system_memory_consumers  
```  
  
 该输出显示系统级别的所有内存消耗者。 例如，存在事务后备链的消耗者。  
  
```  
memory_consumer_type_name           memory_consumer_desc                           allocated_bytes_kb   used_bytes_kb        allocation_count  
-------------------------------          ---------------------                          -------------------  --------------        ----------------  
VARHEAP                                  Lookaside heap                                 0                    0                    0  
VARHEAP                                  System heap                                    768                  0                    2  
LOOKASIDE                                GC transaction map entry                       64                   64                   910  
LOOKASIDE                                Redo transaction map entry                     128                  128                  1260  
LOOKASIDE                                Recovery table cache entry                     448                  448                  8192  
LOOKASIDE                                Transaction recent rows                        3264                 3264                 4444  
LOOKASIDE                                Range cursor                                   0                    0                    0  
LOOKASIDE                                Hash cursor                                    3200                 3200                 11070  
LOOKASIDE                                Transaction save-point set entry               0                    0                    0  
LOOKASIDE                                Transaction partially-inserted rows set        704                  704                  1287  
LOOKASIDE                                Transaction constraint set                     576                  576                  1940  
LOOKASIDE                                Transaction save-point set                     0                    0                    0  
LOOKASIDE                                Transaction write set                          704                  704                  672  
LOOKASIDE                                Transaction scan set                           320                  320                  156  
LOOKASIDE                                Transaction read set                           704                  704                  343  
LOOKASIDE                                Transaction                                    4288                 4288                 1459  
PGPOOL                                   System 256K page pool                          5120                 5120                 20  
PGPOOL                                   System 64K page pool                           0                    0                    0  
PGPOOL                                   System 4K page pool                            24                   24                   6  
```  
  
 查看由系统分配器占用的总内存：  
  
```  
select sum(allocated_bytes)/(1024*1024) as total_allocated_MB, sum(used_bytes)/(1024*1024) as total_used_MB   
from sys.dm_xtp_system_memory_consumers  
  
total_allocated_MB   total_used_MB  
-------------------- --------------------  
2                    2  
```  
  
## <a name="see-also"></a>请参阅  
 [内存优化表动态管理视图&#40;Transact SQL&#41;](../../relational-databases/system-dynamic-management-views/memory-optimized-table-dynamic-management-views-transact-sql.md)  
  
  
