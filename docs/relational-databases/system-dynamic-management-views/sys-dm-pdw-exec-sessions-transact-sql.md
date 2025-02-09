---
title: sys.dm_pdw_exec_sessions (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/22/2019
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 31c262b3-7e4d-44c4-af71-aaef0fd1a980
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: 331bb44faa2938241de98a6bff08f1e660583c4e
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "62689840"
---
# <a name="sysdmpdwexecsessions-transact-sql"></a>sys.dm_pdw_exec_sessions (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  保存有关所有会话信息当前或最近打开在设备上使用。 它列出了每个会话对应一行。  
  
|列名|数据类型|Description|范围|  
|-----------------|---------------|-----------------|-----------|  
|session_id|**nvarchar(32)**|当前查询或运行 （如果终止该会话，并在终止时执行查询） 的最后一个查询的 id。 此视图的键。|在不同的系统中的所有会话是唯一的。|  
|status|**nvarchar(10)**|对于当前会话，标识该会话当前处于活动状态还是空闲。 对于以前的会话状态可能会显示在会话关闭或终止 （如果已强行关闭会话）。|'ACTIVE'、 已关闭，空闲、 已终止|  
|request_id|**nvarchar(32)**|当前查询或运行的最后一个查询的 id。|在系统中的所有请求之间是唯一的。 如果运行任何为 null。|  
|security_id|**varbinary(85)**|运行会话的主体的安全 ID。||  
|login_name|**nvarchar(128)**|运行会话的主体的登录名。|符合用户命名约定的任何字符串。|  
|login_time|**datetime**|日期和时间，用户登录并创建此会话。|有效**datetime**当前时间之前。|  
|query_count|**int**|捕获自创建以来已运行的查询/请求此会话数。|大于或等于 0。|  
|is_transactional|**bit**|捕获会话是否为当前事务中或不。|自动提交为 0，1 表示事务。|  
|client_id|**nvarchar(255)**|捕获会话的客户端信息。|任何有效的字符串。|  
|app_name|**nvarchar(255)**|捕获应用程序名称信息 （可选） 设置作为连接过程的一部分。|任何有效的字符串。|  
|sql_spid|**int**|SPID id 号。 使用`session_id`此会话。 使用`sql_spid`列联接到**sys.dm_pdw_nodes_exec_sessions**。<br /><br /> **\*\* 警告\* \*** 此列包含已关闭的 Spid。||  
  
 此视图按保留的最大行有关的信息，请参阅中的元数据部分[容量限制](/azure/sql-data-warehouse/sql-data-warehouse-service-capacity-limits#metadata)主题。  
  
## <a name="permissions"></a>权限  
 需要 `VIEW SERVER STATE` 权限。  
  
## <a name="see-also"></a>请参阅  
 [SQL 数据仓库和并行数据仓库动态管理视图&#40;Transact SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  
