---
title: sys.dm_fts_active_catalogs (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/29/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_fts_active_catalogs_TSQL
- dm_fts_active_catalogs
- dm_fts_active_catalogs_TSQL
- sys.dm_fts_active_catalogs
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_fts_active_catalogs dynamic management view
ms.assetid: 40ab5453-040c-4d2e-bb49-e340cf90c3ee
author: pmasl
ms.author: pelopes
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 3157284e23c2ec2ccee6df89b24c557403ecc5a8
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "65944396"
---
# <a name="sysdmftsactivecatalogs-transact-sql"></a>sys.dm_fts_active_catalogs (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  返回在服务器上正在进行某些填充活动的全文目录的相关信息。  
  
> [!NOTE]
>  未来版本中将删除以下列[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]: is_paused、 previous_status、 previous_status_description、 row_count_in_thousands、 状态、 status_description 和 worker_count。 应避免在新的开发工作中使用这些列，并着手修改当前使用上述任意列的应用程序。  
  
 
|列名|数据类型|Description|  
|-----------------|---------------|-----------------|  
|**database_id**|**int**|包含活动全文目录的数据库的 ID。|  
|**catalog_id**|**int**|活动的全文目录的 ID。|  
|**memory_address**|**varbinary(8)**|为与此全文目录相关的填充活动所分配的内存缓冲区的地址。|  
|**名称**|**nvarchar(128)**|活动的全文目录的名称。|  
|**is_paused**|**bit**|指示活动全文目录的填充是否已暂停。|  
|**status**|**int**|全文目录的当前状态。 可以是以下类型之一：<br /><br /> 0 = 正在初始化<br /><br /> 1 = 就绪<br /><br /> 2 = 已暂停<br /><br /> 3 = 暂时错误<br /><br /> 4 = 需要重新装入<br /><br /> 5 = 关闭<br /><br /> 6 = 停止以备份<br /><br /> 7 = 已完成目录备份<br /><br /> 8 = 目录已损坏|  
|**status_description**|**nvarchar(120)**|对活动全文目录的当前状态的说明。|  
|**previous_status**|**int**|全文目录的前面状态。 可以是以下类型之一：<br /><br /> 0 = 正在初始化<br /><br /> 1 = 就绪<br /><br /> 2 = 已暂停<br /><br /> 3 = 暂时错误<br /><br /> 4 = 需要重新装入<br /><br /> 5 = 关闭<br /><br /> 6 = 停止以备份<br /><br /> 7 = 已完成目录备份<br /><br /> 8 = 目录已损坏|  
|**previous_status_description**|**nvarchar(120)**|对活动全文目录的前面状态的说明。|  
|**worker_count**|**int**|当前正在处理此全文目录的线程数。|  
|**active_fts_index_count**|**int**|所填充的全文索引数。|  
|**auto_population_count**|**int**|正在对此全文目录进行自动填充的表数。|  
|**manual_population_count**|**int**|正在对此全文目录进行手动填充的表数。|  
|**full_incremental_population_count**|**int**|正在对此全文目录进行完整或增量填充的表数。|  
|**row_count_in_thousands**|**int**|此全文目录中的所有全文索引的估计行数（千）。|  
|**is_importing**|**bit**|指示是否正在导入全文目录：<br /><br /> 1 = 正在导入目录。<br /><br /> 2 = 没有导入目录。|  
  
## <a name="remarks"></a>备注  
 Is_importing 列是中的新增功能[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]。  
  
## <a name="permissions"></a>权限  

上[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]，需要`VIEW SERVER STATE`权限。   
上[!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]，需要`VIEW DATABASE STATE`数据库中的权限。   
   
## <a name="physical-joins"></a>物理联接  
 ![此动态管理视图的重要联接](../../relational-databases/system-dynamic-management-views/media/join-dm-fts-active-catalogs-1.gif "此动态管理视图的重要联接")  
  
## <a name="relationship-cardinalities"></a>关系基数  
  
|From|若要|关系|  
|----------|--------|------------------|  
|dm_fts_active_catalogs.database_id|dm_fts_index_population.database_id|一对一|  
|dm_fts_active_catalogs.catalog_id|dm_fts_index_population.catalog_id|一对一|  
  
## <a name="examples"></a>示例  
 以下示例返回有关当前数据库的活动全文目录的信息。  
  
```  
SELECT catalog.name, catalog.is_importing, catalog.auto_population_count,  
  OBJECT_NAME(population.table_id) AS table_name,  
  population.population_type_description, population.is_clustered_index_scan,  
  population.status_description, population.completion_type_description,  
  population.queued_population_type_description, population.start_time,  
  population.range_count   
FROM sys.dm_fts_active_catalogs catalog   
CROSS JOIN sys.dm_fts_index_population population   
WHERE catalog.database_id = population.database_id   
AND catalog.catalog_id = population.catalog_id   
AND catalog.database_id = (SELECT dbid FROM sys.sysdatabases WHERE name = DB_NAME());  
GO  
```  
  
## <a name="see-also"></a>请参阅  
 
 [全文搜索和语义搜索动态管理视图和函数&#40;Transact SQL&#41;](../../relational-databases/system-dynamic-management-views/full-text-and-semantic-search-dynamic-management-views-functions.md)  
  
  
