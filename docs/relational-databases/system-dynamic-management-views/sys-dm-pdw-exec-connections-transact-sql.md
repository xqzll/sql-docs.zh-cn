---
title: sys.dm_pdw_exec_connections (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.technology: data-warehouse
ms.reviewer: ''
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 2625466b-d0ef-4c71-bedc-6d13491a8351
author: ronortloff
ms.author: rortloff
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || = sqlallproducts-allversions'
ms.openlocfilehash: e93d397d10a99f844454494c4bf0d82b7fe6d660
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "62502899"
---
# <a name="sysdmpdwexecconnections-transact-sql"></a>sys.dm_pdw_exec_connections (Transact-SQL)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-asdw-pdw-md.md)]

  返回有关与此 [!INCLUDE[ssSDW](../../includes/sssdw-md.md)] 实例建立的连接的信息以及每个连接的详细信息。  
  
|列名|数据类型|Description|  
|-----------------|---------------|-----------------|  
|session_id|**int**|标识与此连接关联的会话。 使用`SESSION_ID()`以返回`session_id`的当前连接。|  
|connect_time|**datetime**|连接建立时的时间戳。 不可为 null。|  
|encrypt_option|**nvarchar(40)**|指示 TRUE （连接已加密） 或 FALSE （连接不是 enctypred）。|  
|auth_scheme|**nvarchar(40)**|指定此连接使用的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]/Windows 身份验证方案。 不可为 null。|  
|client_id|**varchar(48)**|连接到此服务器的客户端的 IP 地址。 可以为 Null。|  
|sql_spid|**int**|连接的服务器进程 ID。 使用`@@SPID`以返回`sql_spid`的当前连接。对于大多数用途，使用`session_id`相反。|  
  
## <a name="permissions"></a>权限  
 需要**VIEW SERVER STATE**服务器上的权限。  
  
## <a name="relationship-cardinalities"></a>关系基数  
  
||||  
|-|-|-|  
|dm_pdw_exec_sessions.session_id|dm_pdw_exec_connections.session_id|一对一|  
|dm_pdw_exec_requests.connection_id|dm_pdw_exec_connections.connection_id|多对一|  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>示例：[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] 和 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 收集查询自有连接有关信息的典型查询。  
  
```  
SELECT  
    c.session_id, c.encrypt_option,  
    c.auth_scheme, s.client_id, s.login_name,   
    s.status, s.query_count  
FROM sys.dm_pdw_exec_connections AS c  
JOIN sys.dm_pdw_exec_sessions AS s  
    ON c.session_id = s.session_id  
WHERE c.session_id = SESSION_ID();  
```  
  
## <a name="see-also"></a>请参阅  
 [SQL 数据仓库和并行数据仓库动态管理视图&#40;Transact SQL&#41;](../../relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views.md)  
  
  

