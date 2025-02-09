---
title: sys.dm_exec_query_plan (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 08/02/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_exec_query_plan_TSQL
- sys.dm_exec_query_plan
- dm_exec_query_plan
- sys.dm_exec_query_plan_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_exec_query_plan dynamic management function
ms.assetid: e26f0867-9be3-4b2e-969e-7f2840230770
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: c879af413bd8b3cf4b90e8112f10e5f756201148
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "63013277"
---
# <a name="sysdmexecqueryplan-transact-sql"></a>sys.dm_exec_query_plan (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

以 XML 格式返回计划句柄指定的批查询的显示计划。 计划句柄指定的计划可以处于缓存或正在执行状态。  
  
显示计划 XML 架构已发布并可在[此 Microsoft 网站上](https://go.microsoft.com/fwlink/?linkid=43100&clcid=0x409)。 也可在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安装目录中找到该架构。  
  
 ![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "主题链接图标") [TRANSACT-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>语法  
  
```  
sys.dm_exec_query_plan(plan_handle)  
```  
  
## <a name="arguments"></a>参数  
*plan_handle*  
是一个标记，用于唯一标识已执行的批次查询执行计划，其计划驻留在计划缓存中，或当前正在执行。 *plan_handle*是**varbinary(64)** 。   

*Plan_handle*可以从以下动态管理对象中获得：
  
-   [sys.dm_exec_cached_plans &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-cached-plans-transact-sql.md)  
  
-   [sys.dm_exec_query_stats (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-stats-transact-sql.md)  
  
-   [sys.dm_exec_requests &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md)  

-   [sys.dm_exec_procedure_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-procedure-stats-transact-sql.md)  

-   [sys.dm_exec_trigger_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-trigger-stats-transact-sql.md)  
  
## <a name="table-returned"></a>返回的表  
  
|列名|数据类型|Description|  
|-----------------|---------------|-----------------|  
|**dbid**|**smallint**|在编译对应于此计划的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句时有效的上下文数据库的 ID。 对于临时和预定义 SQL 语句，指编译这些语句时所在的数据库的 ID。<br /><br /> 此列可为空值。|  
|**objectid**|**int**|此查询计划的对象（如存储过程或用户定义函数）的 ID。 对于临时和预定义的批处理，则此列为**null**。<br /><br /> 此列可为空值。|  
|**number**|**smallint**|为存储过程编号的整数。 例如，一组的过程**订单**可能名为应用程序**orderproc; 1**， **orderproc; 2**，依次类推。 对于临时和预定义的批处理，则此列为**null**。<br /><br /> 此列可为空值。|  
|**encrypted**|**bit**|指示对应的存储过程是否已加密。<br /><br /> 0 = 未加密<br /><br /> 1 = 已加密<br /><br /> 此列不可为空值。|  
|**query_plan**|**xml**|包含与指定的查询执行计划的编译时显示计划表示形式*plan_handle*。 显示计划的格式为 XML。 为包含即席 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句、存储过程调用以及用户定义函数调用等内容的每个批查询生成一个计划。<br /><br /> 此列可为空值。|  
  
## <a name="remarks"></a>备注  
 在以下情况下不显示计划输出中返回**query_plan**返回的表的列**sys.dm_exec_query_plan**:  
  
-   通过使用指定的查询计划，如果*plan_handle*已从计划缓存中逐出**query_plan**列返回的表为 null。 例如，可能会发生此问题，如果没有捕获计划句柄的和已使用与时间之间的时间延迟**sys.dm_exec_query_plan**。  
  
-   有些 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句未放入缓存，如大容量操作语句或包含大于 8 KB 的字符串文字的语句。 不能使用检索此类语句的 XML 显示计划**sys.dm_exec_query_plan**除非当前正在执行批处理，因为它们在缓存中不存在。  
  
-   如果[!INCLUDE[tsql](../../includes/tsql-md.md)]批处理或存储的过程包含对用户定义函数的调用或对动态 SQL，例如使用 EXEC (*字符串*)，则不在表中会包含用户定义函数已编译 XML 显示计划返回的**sys.dm_exec_query_plan**为批处理或存储的过程。 相反，必须进行单独调用**sys.dm_exec_query_plan**对应于用户定义函数的计划句柄。  
  
 当即席查询使用简单或强制参数化**query_plan**列将包含仅语句文本，而不是实际查询计划。 若要返回查询计划，请调用**sys.dm_exec_query_plan**准备参数化查询的计划句柄。 您可以确定查询是否已参数化通过引用**sql**的列[sys.syscacheobjects](../../relational-databases/system-compatibility-views/sys-syscacheobjects-transact-sql.md)视图或文本列[sys.dm_exec_sql_text](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sql-text-transact-sql.md)动态管理视图。  
  
> [!NOTE] 
> 由于在允许的嵌套级别数的限制造成**xml**数据类型**sys.dm_exec_query_plan**不能返回达到或超过 128 级的嵌套元素的查询计划。 在早期版本的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中，这种情况将导致无法返回查询计划，并生成错误 6335。 在中[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]Service Pack 2 和更高版本**query_plan**列返回 NULL。   
> 可以使用[sys.dm_exec_text_query_plan &#40;TRANSACT-SQL&#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-exec-text-query-plan-transact-sql.md)动态管理函数以文本格式返回查询计划的输出。  
  
## <a name="permissions"></a>权限  
 若要执行**sys.dm_exec_query_plan**，用户必须是属于**sysadmin**固定服务器角色或具有`VIEW SERVER STATE`服务器上的权限。  
  
## <a name="examples"></a>示例  
 下面的示例演示如何使用**sys.dm_exec_query_plan**动态管理视图。  
  
 若要查看 XML 显示计划，请执行以下查询中的查询编辑器[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]，然后单击**ShowPlanXML**中**query_plan**返回的表的列**sys.dm_exec_query_plan**。 XML 显示计划显示在 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 摘要窗格中。 若要将 XML 显示计划保存到文件中，右键单击**ShowPlanXML**中**query_plan**列中，单击**结果另存为**，采用格式将文件命名\< *file_name*>.sqlplan; 例如，MyXMLShowplan.sqlplan。  
  
### <a name="a-retrieve-the-cached-query-plan-for-a-slow-running-transact-sql-query-or-batch"></a>A. 检索运行速度缓慢的 Transact-SQL 查询或批查询的缓存查询计划  
 不同类型的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 批查询（如即席批查询、存储过程和用户定义函数）的查询计划缓存在称作计划缓存的内存区域中。 每个缓存查询计划均由称作计划句柄的唯一标识符进行标识。 您可以指定与此计划句柄**sys.dm_exec_query_plan**动态管理视图来检索特定的执行计划[!INCLUDE[tsql](../../includes/tsql-md.md)]查询或批处理。  
  
 如果 [!INCLUDE[tsql](../../includes/tsql-md.md)] 查询或批查询在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的特定连接上运行的时间很长，请检索该查询或批查询的执行计划，以查找导致延迟的原因。 以下示例显示如何检索运行速度缓慢的查询或批查询的 XML 显示计划。  
  
> [!NOTE]  
>  若要运行此示例中，替换的值*session_id*并*plan_handle*与特定于你的服务器的值。  
  
 首先，使用 `sp_who` 存储过程检索正在执行查询或批查询的进程的服务器进程 ID (SPID)。  
  
```sql  
USE master;  
GO  
exec sp_who;  
GO  
```  
  
 由 `sp_who` 返回的结果集指示 SPID 为 `54`。 可以在 `sys.dm_exec_requests` 动态管理视图中使用该 SPID，以便使用以下查询来检索计划句柄：  
  
```sql  
USE master;  
GO  
SELECT * FROM sys.dm_exec_requests  
WHERE session_id = 54;  
GO  
```  
  
 通过返回的表**sys.dm_exec_requests**指示运行速度缓慢的查询或批处理的计划句柄`0x06000100A27E7C1FA821B10600`，你可以指定*plan_handle* 参数`sys.dm_exec_query_plan`来检索 XML 格式的执行计划，如下所示。 中包含的执行计划中运行速度缓慢的查询或批处理的 XML 格式**query_plan**返回的表的列`sys.dm_exec_query_plan`。  
  
```sql  
USE master;  
GO  
SELECT * 
FROM sys.dm_exec_query_plan (0x06000100A27E7C1FA821B10600);  
GO  
```  
  
### <a name="b-retrieve-every-query-plan-from-the-plan-cache"></a>B. 从计划缓存中检索每个查询计划  
 若要检索驻留在计划缓存中的所有查询计划的快照，请通过查询 `sys.dm_exec_cached_plans` 动态管理视图来检索缓存中所有查询计划的计划句柄。 计划句柄存储在 `plan_handle` 的 `sys.dm_exec_cached_plans` 列中。 然后，使用 CROSS APPLY 运算符将计划句柄传递给 `sys.dm_exec_query_plan`，如下所示。 当前在计划缓存中的每个计划的 XML 显示计划输出位于返回的表的 `query_plan` 列中。  
  
```sql  
USE master;  
GO  
SELECT * 
FROM sys.dm_exec_cached_plans AS cp 
CROSS APPLY sys.dm_exec_query_plan(cp.plan_handle);  
GO  
```  
  
### <a name="c-retrieve-every-query-plan-for-which-the-server-has-gathered-query-statistics-from-the-plan-cache"></a>C. 检索服务器已从计划缓存中收集了其查询统计信息的每个查询计划  
 若要检索服务器已收集了其当前驻留在计划缓存中的统计信息的所有查询计划的快照，请通过查询 `sys.dm_exec_query_stats` 动态管理视图来检索缓存中这些计划的计划句柄。 计划句柄存储在 `plan_handle` 的 `sys.dm_exec_query_stats` 列中。 然后，使用 CROSS APPLY 运算符将计划句柄传递给 `sys.dm_exec_query_plan`，如下所示。 服务器已收集了其驻留在计划缓存中的统计信息的每个计划的 XML 显示计划输出在返回的表的 `query_plan` 列中。  
  
```sql  
USE master;  
GO  
SELECT * 
FROM sys.dm_exec_query_stats AS qs 
CROSS APPLY sys.dm_exec_query_plan(qs.plan_handle);  
GO  
```  
  
### <a name="d-retrieve-information-about-the-top-five-queries-by-average-cpu-time"></a>D. 按平均 CPU 时间检索有关前五个查询的信息  
 以下示例为前五个查询返回查询计划和平均 CPU 时间。  
  
```sql  
SELECT TOP 5 total_worker_time/execution_count AS [Avg CPU Time],  
   plan_handle, query_plan   
FROM sys.dm_exec_query_stats AS qs  
CROSS APPLY sys.dm_exec_query_plan(qs.plan_handle)  
ORDER BY total_worker_time/execution_count DESC;  
GO  
```  
  
## <a name="see-also"></a>请参阅  
 [动态管理视图和函数 (Transact-SQL)](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [sys.dm_exec_cached_plans &#40;Transact SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-cached-plans-transact-sql.md)   
 [sys.dm_exec_query_stats &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-query-stats-transact-sql.md)   
 [sys.dm_exec_requests &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md)   
 [sp_who (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-who-transact-sql.md)   
 [Showplan 逻辑运算符和物理运算符参考](../../relational-databases/showplan-logical-and-physical-operators-reference.md)   
 [sys.dm_exec_text_query_plan &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-text-query-plan-transact-sql.md)  
  
  
