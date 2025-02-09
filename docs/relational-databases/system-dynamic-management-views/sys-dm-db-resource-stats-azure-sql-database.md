---
title: sys.dm_db_resource_stats （Azure SQL 数据库） |Microsoft Docs
ms.custom: ''
ms.date: 05/21/2019
ms.service: sql-database
ms.reviewer: ''
ms.topic: language-reference
f1_keywords:
- sys.dm_db_resource_stats
- sys.dm_db_resource_stats_TSQL
- dm_db_resource_stats
- dm_db_resource_stats_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_db_resource_stats
- dm_db_resource_stats
ms.assetid: 6e76b39f-236e-4bbf-b0b5-38be190d81e8
author: julieMSFT
ms.author: jrasnick
manager: craigg
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: 1df2ac9979e99a301d416d25d143039bef3ee4ed
ms.sourcegitcommit: 93d1566b9fe0c092c9f0f8c84435b0eede07019f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/11/2019
ms.locfileid: "67833040"
---
# <a name="sysdmdbresourcestats-azure-sql-database"></a>sys.dm_db_resource_stats (Azure SQL Database)
[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

  返回 [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] 数据库的 CPU、I/O 和内存消耗量。 每隔 15 秒会显示一行，即使该数据库中没有任何活动也是如此。 历史数据将保留一小时。  
  
|“列”|数据类型|描述|  
|-------------|---------------|-----------------|  
|end_time|**datetime**|UTC 时间用于指示当前报告间隔的结束时间。|  
|avg_cpu_percent|**decimal (5,2)**|平均计算使用率（以服务层限制的百分比表示）。|  
|avg_data_io_percent|**decimal (5,2)**|平均数据 I/O 使用率服务层限制的百分比。|  
|avg_log_write_percent|**decimal (5,2)**|平均事务日志写入百分比表示的服务层限制的次数 （以 MBps)。|  
|avg_memory_usage_percent|**decimal (5,2)**|平均内存使用率（以服务层限制的百分比表示）。<br /><br /> 这包括用于缓冲池页数和存储内存中 OLTP 对象的内存。|  
|xtp_storage_percent|**decimal (5,2)**|存储内存中 OLTP 在使用率服务层限制的百分比 （报告间隔末尾）。 这包括用于存储以下内存中 OLTP 对象的内存： 内存优化表、 索引和表变量。 它还包括用于处理 ALTER TABLE 操作的内存。<br /><br /> 如果在数据库中不使用内存中 OLTP，则返回 0。|  
|max_worker_percent|**decimal (5,2)**|最大并发辅助进程 （请求） 中的数据库的服务层限制的百分比。|  
|max_session_percent|**decimal (5,2)**|数据库的服务层限制的百分比形式表示的最大并发会话。|  
|dtu_limit|**int**|当前最大数据库 DTU 设置为此数据库的在此时间间隔内。 对于使用基于 vCore 的模型数据库，此列为 NULL。|
|cpu_limit|**decimal (5,2)**|在此间隔期间此数据库的 Vcore 数。 对于使用基于 DTU 的模型数据库，此列为 NULL。|
|avg_instance_cpu_percent|**decimal (5,2)**|以百分比表示的 CPU 使用率的平均数据库。|
|avg_instance_memory_percent|**decimal (5,2)**|以百分比表示的平均数据库内存使用量。|
|avg_login_rate_percent|**decimal (5,2)**|标识为仅供参考。 不提供支持。 不保证以后的兼容性。|
|replica_role|**int**|表示当前副本包含角色为主要的 0，1 作为辅助数据库，并且 2 作为转发器 （异地辅助数据库的主数据库）。 你将看到"1"时连接到所有的可读辅助副本的只读意向。 如果未指定只读意向，连接到异地辅助数据库，您应看到"2"（连接到该转发器）。|
|||
  
> [!TIP]  
>  有关这些限制和服务层的更多上下文，请参阅主题[服务层](https://azure.microsoft.com/documentation/articles/sql-database-service-tiers/)并[服务层功能和限制](https://azure.microsoft.com/documentation/articles/sql-database-performance-guidance/)。  
  
## <a name="permissions"></a>权限  
 此视图需要拥有 VIEW DATABASE STATE 权限。  
  
## <a name="remarks"></a>备注  
 返回的数据**sys.dm_db_resource_stats**表示为百分比的最大允许运行的服务层/性能级别的限制。
 
 如果已在最后 60 分钟内将数据库故障转移到另一台服务器，该视图将仅返回主数据库故障转移后此时间段内的数据。  
  
 对于此数据的粗粒度视图，使用**sys.resource_stats**目录视图中的**master**数据库。 此视图每 5 分钟捕获一次数据，并将历史数据保留 14 天。  有关详细信息，请参阅[sys.resource_stats &#40;Azure SQL 数据库&#41;](../../relational-databases/system-catalog-views/sys-resource-stats-azure-sql-database.md)。  
  
 如果数据库是弹性池的成员，资源统计信息显示为百分比值，表示为数据库中的弹性池配置设置的最大限制的百分比。  
  
## <a name="example"></a>示例  
  
以下示例将返回当前连接的数据库按最新时间排序的资源利用率数据。  
  
```  
SELECT * FROM sys.dm_db_resource_stats ORDER BY end_time DESC;  
  
```  
  
 以下示例将根据过去几个小时内用户数据库的性能级别所允许的最大 DTU 限制百分比来标识平均 DTU 使用率。 请考虑提高性能级别，因为这些百分比将始终接近于 100%。  
  
```  
SELECT end_time,   
  (SELECT Max(v)    
   FROM (VALUES (avg_cpu_percent), (avg_data_io_percent), (avg_log_write_percent)) AS    
   value(v)) AS [avg_DTU_percent]   
FROM sys.dm_db_resource_stats;  
  
```  
  
 以下示例将返回最近一小时的 CPU 使用率、数据和日志 I/O 以及内存使用率的平均值和最大值。  
  
```  
SELECT    
    AVG(avg_cpu_percent) AS 'Average CPU Utilization In Percent',   
    MAX(avg_cpu_percent) AS 'Maximum CPU Utilization In Percent',   
    AVG(avg_data_io_percent) AS 'Average Data IO In Percent',   
    MAX(avg_data_io_percent) AS 'Maximum Data IO In Percent',   
    AVG(avg_log_write_percent) AS 'Average Log Write I/O Throughput Utilization In Percent',   
    MAX(avg_log_write_percent) AS 'Maximum Log Write I/O Throughput Utilization In Percent',   
    AVG(avg_memory_usage_percent) AS 'Average Memory Usage In Percent',   
    MAX(avg_memory_usage_percent) AS 'Maximum Memory Usage In Percent'   
FROM sys.dm_db_resource_stats;  
  
```  
  
## <a name="see-also"></a>请参阅  
 [sys.resource_stats &#40;Azure SQL 数据库&#41;](../../relational-databases/system-catalog-views/sys-resource-stats-azure-sql-database.md)   
 [服务层](https://azure.microsoft.com/documentation/articles/sql-database-service-tiers/)   
 [服务层功能和限制](https://azure.microsoft.com/documentation/articles/sql-database-performance-guidance/)  
  
  
