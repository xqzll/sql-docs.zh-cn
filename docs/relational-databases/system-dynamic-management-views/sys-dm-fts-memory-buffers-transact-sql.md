---
title: sys.dm_fts_memory_buffers (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/29/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_fts_memory_buffers
- dm_fts_memory_buffers_TSQL
- dm_fts_memory_buffers
- sys.dm_fts_memory_buffers_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_fts_memory_buffers dynamic management view
ms.assetid: 56895fe5-e8df-4d75-9adc-c1f7757cdef8
author: pmasl
ms.author: pelopes
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 254ba42c828bbe719d5ddce0502d0a9063755fe3
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "65947269"
---
# <a name="sysdmftsmemorybuffers-transact-sql"></a>sys.dm_fts_memory_buffers (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  返回有关属于特定内存池的内存缓冲区（作为全文爬网或全文爬网范围的一部分使用）的信息。  
  
> [!NOTE]
> 未来版本中将删除以下列[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]: **row_count**。 应避免在新的开发工作中使用该列，并着手修改当前使用该列的应用程序。  

  
|“列”|数据类型|Description|  
|------------|---------------|-----------------|  
|**pool_id**|**int**|已分配的内存池的 ID。<br /><br /> 0 = 小型缓冲区<br /><br /> 1 = 大型缓冲区|  
|**memory_address**|**varbinary(8)**|已分配的内存缓冲区的地址。|  
|**名称**|**nvarchar(4000)**|执行该分配的共享内存缓冲区的名称。|  
|**is_free**|**bit**|内存缓冲区的当前状态。<br /><br /> 0 = 空闲<br /><br /> 1 = 繁忙|  
|**row_count**|**int**|该缓冲区当前正在处理的行数。|  
|**bytes_used**|**int**|该缓冲区中正在使用的内存量（字节）。|  
|**percent_used**|**int**|已分配内存已用的百分比。|  
  
## <a name="permissions"></a>权限  

上[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]，需要`VIEW SERVER STATE`权限。   
上[!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]，需要`VIEW DATABASE STATE`数据库中的权限。   
  
## <a name="physical-joins"></a>物理联接  
 ![此动态管理视图的重要联接](../../relational-databases/system-dynamic-management-views/media/join-dm-fts-memory-buffers-1.gif "此动态管理视图的重要联接")  
  
## <a name="relationship-cardinalities"></a>关系基数  
  
|From|若要|关系|  
|----------|--------|------------------|  
|dm_fts_memory_buffers.pool_id|dm_fts_memory_pools.pool_id|多对一|  
  
## <a name="see-also"></a>请参阅  
 [动态管理视图和函数 (Transact-SQL)](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [全文搜索和语义搜索动态管理视图和函数&#40;Transact SQL&#41;](../../relational-databases/system-dynamic-management-views/full-text-and-semantic-search-dynamic-management-views-functions.md)  
  
  

