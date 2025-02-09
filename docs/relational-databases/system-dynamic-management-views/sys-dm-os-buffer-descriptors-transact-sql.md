---
title: sys.dm_os_buffer_descriptors (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 08/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_os_buffer_descriptors_TSQL
- dm_os_buffer_descriptors_TSQL
- sys.dm_os_buffer_descriptors
- dm_os_buffer_descriptors
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_os_buffer_descriptors dynamic management view
ms.assetid: 012aab95-8888-4f35-9ea3-b5dff6e3f60f
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 29449905da888d0f7c85b66d3731eed381dc582c
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "62506057"
---
# <a name="sysdmosbufferdescriptors-transact-sql"></a>sys.dm_os_buffer_descriptors (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  返回有关 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 缓冲池中当前所有数据页的信息。 可以使用该视图的输出，根据数据库、对象或类型来确定缓冲池内数据库页的分布。 在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]中，此动态管理视图还返回有关缓冲池扩展文件中的数据页的信息。 有关详细信息，请参阅[缓冲池扩展](../../database-engine/configure-windows/buffer-pool-extension.md)。  
  
 当从磁盘读取数据页时，该数据页被复制到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 缓冲池并被缓存以供重复使用。 每个缓存的数据页都有一个缓冲描述符。 缓冲描述符唯一地标识 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例中当前缓存的每个数据页。 sys.dm_os_buffer_descriptors 返回所有用户数据库和系统数据库的缓存页。 这包括与 Resource 数据库相关联的页。  
  
> **注意**：若要调用此项从[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]或[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]，使用名称**sys.dm_pdw_nodes_os_buffer_descriptors**。  

|列名|数据类型|Description|  
|-----------------|---------------|-----------------|  
|database_id|**int**|与缓冲池中的页关联的数据库 ID。 可以为 Null。|  
|file_id|**int**|存储页的持久化图像的文件 ID。 可以为 Null。|  
|page_id|**int**|在文件中的页 ID。 可以为 Null。|  
|page_level|**int**|页的索引级别。 可以为 Null。|  
|allocation_unit_id|**bigint**|页的分配单元的 ID。 可使用此值联接 sys.allocation_units。 可以为 Null。|  
|page_type|**nvarchar(60)**|键入的页上，如：数据页或索引页。 可以为 Null。|  
|row_count|**int**|页中的行数。 可以为 Null。|  
|free_space_in_bytes|**int**|页中的可用空间（字节）。 可以为 Null。|  
|is_modified|**bit**|1 = 从磁盘读取页后已对其进行修改。 可以为 Null。|  
|numa_node|**int**|缓冲区的非一致性内存访问节点。 可以为 Null。|  
|read_microsec|**bigint**|将此页读入缓冲区所需的实际时间（微秒）。 重用缓冲区时重置该数值。 可以为 Null。|  
|is_in_bpool_extension|**bit**|1 = 页位于缓冲池扩展。 可以为 Null。|  
|pdw_node_id|**int**|**适用于**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]， [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> 对于此分布的节点标识符。|  
  
## <a name="permissions"></a>权限  

上[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]，需要`VIEW SERVER STATE`权限。   
上[!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]，需要`VIEW DATABASE STATE`数据库中的权限。   
   
## <a name="remarks"></a>备注  
 sys.dm_os_buffer_descriptors 返回 Resource 数据库正在使用的页。 sys.dm_os_buffer_descriptors 不返回有关可用页、 被盗页或在读取时出现的错误的页的信息。  
  
|From|若要|On|关系|  
|----------|--------|--------|------------------|  
|sys.dm_os_buffer_descriptors|sys.databases|database_id|多对一|  
|sys.dm_os_buffer_descriptors|\<userdb>.sys.allocation_units|allocation_unit_id|多对一|  
|sys.dm_os_buffer_descriptors|\<userdb>.sys.database_files|file_id|多对一|  
|sys.dm_os_buffer_descriptors|sys.dm_os_buffer_pool_extension_configuration|file_id|多对一|  
  
## <a name="examples"></a>示例  
  
### <a name="a-returning-cached-page-count-for-each-database"></a>A. 返回每个数据库的缓存页计数  
 以下示例返回为每个数据库加载的页的计数。  
  
```  
SELECT COUNT(*)AS cached_pages_count  
    ,CASE database_id   
        WHEN 32767 THEN 'ResourceDb'   
        ELSE db_name(database_id)   
        END AS database_name  
FROM sys.dm_os_buffer_descriptors  
GROUP BY DB_NAME(database_id) ,database_id  
ORDER BY cached_pages_count DESC;  
```  
  
### <a name="b-returning-cached-page-count-for-each-object-in-the-current-database"></a>B. 返回当前数据库中每个对象的缓存页计数  
 以下示例返回为当前数据库中每个对象加载的页的计数。  
  
```  
SELECT COUNT(*)AS cached_pages_count   
    ,name ,index_id   
FROM sys.dm_os_buffer_descriptors AS bd   
    INNER JOIN   
    (  
        SELECT object_name(object_id) AS name   
            ,index_id ,allocation_unit_id  
        FROM sys.allocation_units AS au  
            INNER JOIN sys.partitions AS p   
                ON au.container_id = p.hobt_id   
                    AND (au.type = 1 OR au.type = 3)  
        UNION ALL  
        SELECT object_name(object_id) AS name     
            ,index_id, allocation_unit_id  
        FROM sys.allocation_units AS au  
            INNER JOIN sys.partitions AS p   
                ON au.container_id = p.partition_id   
                    AND au.type = 2  
    ) AS obj   
        ON bd.allocation_unit_id = obj.allocation_unit_id  
WHERE database_id = DB_ID()  
GROUP BY name, index_id   
ORDER BY cached_pages_count DESC;  
```  
  
## <a name="see-also"></a>请参阅  
 [sys.allocation_units (Transact-SQL)](../../relational-databases/system-catalog-views/sys-allocation-units-transact-sql.md)   
 
 [与 SQL Server 操作系统相关的动态管理视图&#40;Transact SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-server-operating-system-related-dynamic-management-views-transact-sql.md)   
 [Resource 数据库](../../relational-databases/databases/resource-database.md)   
 [sys.dm_os_buffer_pool_extension_configuration (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-os-buffer-pool-extension-configuration-transact-sql.md)  
  
  


