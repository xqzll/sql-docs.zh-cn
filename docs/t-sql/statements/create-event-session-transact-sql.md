---
title: CREATE EVENT SESSION (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 05/28/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- CREATE EVENT SESSION
- SESSION
- EVENT SESSION
- SESSION_TSQL
- EVENT_SESSION_TSQL
- CREATE_EVENT_SESSION_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- event sessions [SQL Server]
- CREATE EVENT SESSION statement
ms.assetid: 67683027-2b0f-47aa-b223-604731af8b4d
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 49570a5dd2c5d0e45e75a51a4835df28b63aa783
ms.sourcegitcommit: ce5770d8b91c18ba5ad031e1a96a657bde4cae55
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/25/2019
ms.locfileid: "67388122"
---
# <a name="create-event-session-transact-sql"></a>CREATE EVENT SESSION (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  创建一个标识事件源、事件会话目标和事件会话选项的扩展事件会话。  
  
 ![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "主题链接图标") [Transact-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)。  
  
## <a name="syntax"></a>语法  
  
```    
CREATE EVENT SESSION event_session_name  
ON { SERVER | DATABASE }
{  
    <event_definition> [ ,...n]  
    [ <event_target_definition> [ ,...n] ]  
    [ WITH ( <event_session_options> [ ,...n] ) ]  
}  
;  
  
<event_definition>::=  
{  
    ADD EVENT [event_module_guid].event_package_name.event_name   
         [ ( {   
                 [ SET { event_customizable_attribute = <value> [ ,...n] } ]  
                 [ ACTION ( { [event_module_guid].event_package_name.action_name [ ,...n] } ) ]  
                 [ WHERE <predicate_expression> ]  
        } ) ]  
}  
  
<predicate_expression> ::=   
{  
    [ NOT ] <predicate_factor> | {( <predicate_expression> ) }   
    [ { AND | OR } [ NOT ] { <predicate_factor> | ( <predicate_expression> ) } ]   
    [ ,...n ]  
}  
  
<predicate_factor>::=   
{  
    <predicate_leaf> | ( <predicate_expression> )  
}  
  
<predicate_leaf>::=  
{  
      <predicate_source_declaration> { = | < > | ! = | > | > = | < | < = } <value>   
    | [event_module_guid].event_package_name.predicate_compare_name ( <predicate_source_declaration>, <value> )   
}  
  
<predicate_source_declaration>::=   
{  
    event_field_name | ( [event_module_guid].event_package_name.predicate_source_name )  
}  
  
<value>::=   
{  
    number | 'string'  
}  
  
<event_target_definition>::=  
{  
    ADD TARGET [event_module_guid].event_package_name.target_name  
        [ ( SET { target_parameter_name = <value> [ ,...n] } ) ]  
}  
  
<event_session_options>::=  
{  
    [    MAX_MEMORY = size [ KB | MB ] ]  
    [ [,] EVENT_RETENTION_MODE = { ALLOW_SINGLE_EVENT_LOSS | ALLOW_MULTIPLE_EVENT_LOSS | NO_EVENT_LOSS } ]  
    [ [,] MAX_DISPATCH_LATENCY = { seconds SECONDS | INFINITE } ]  
    [ [,] MAX_EVENT_SIZE = size [ KB | MB ] ]  
    [ [,] MEMORY_PARTITION_MODE = { NONE | PER_NODE | PER_CPU } ]  
    [ [,] TRACK_CAUSALITY = { ON | OFF } ]  
    [ [,] STARTUP_STATE = { ON | OFF } ]  
}  
```  
  
## <a name="arguments"></a>参数  
 event_session_name   
 事件会话的用户定义名称。 event_session_name 由字母数字组成，最多可包含 128 个字符，在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例中必须是唯一的，并且必须符合[标识符](../../relational-databases/databases/database-identifiers.md)规则  。  
  
 ADD EVENT [ event_module_guid ].event_package_name.event_name     
 表示要与事件会话关联的事件，其中：  
  
-   event_module_guid 为包含该事件的模块的 GUID  。  
  
-   event_package_name 为包含操作对象的包  。  
  
-   event_name 为事件对象  。  
  
 事件在 sys.dm_xe_objects 视图中显示为 object_type 'event'。  
  
 SET { event_customizable_attribute= \<value> [ ,...n] }    
 允许设置事件的可自定义属性。 可自定义属性在 sys.dm_xe_object_columns 视图中显示为 column_type 'customizable' 以及 object_name = event_name  。  
  
 ACTION ( { [event_module_guid].event_package_name.action_name [ ,...n] })       
 要与事件会话关联的操作，其中：  
  
-   event_module_guid 为包含该事件的模块的 GUID  。  
  
-   event_package_name 为包含操作对象的包  。  
  
-   action_name 为操作对象  。  
  
 操作在 sys.dm_xe_objects 视图中显示为 object_type 'action'。  
  
 WHERE \<predicate_expression> 指定用于确定是否应处理事件的谓词表达式。 如果 \<predicate_expression> 为 true，则由会话的操作和目标对事件做进一步处理。 如果 \<predicate_expression> 为 false，则在会话的操作和目标处理事件之前由会话删除该事件。 谓词表达式限制在 3000 个字符，这限制了字符串参数。 
  
 event_field_name   
 表示标识谓词源的事件字段的名称。  
  
 [event_module_guid].event_package_name.predicate_source_name     
 表示全局谓词源的名称，其中：  
  
-   event_module_guid 为包含该事件的模块的 GUID  。  
  
-   event_package_name 为包含谓词对象的包  。  
  
-   predicate_source_name 在 sys.dm_xe_objects 视图中定义为 object_type 'pred_source'  。  
  
 [event_module_guid].event_package_name.predicate_compare_name     
 要与事件关联的谓词对象的名称，其中：  
  
-   event_module_guid 为包含该事件的模块的 GUID  。  
  
-   event_package_name 为包含谓词对象的包  。  
  
-   predicate_compare_name 为在 sys.dm_xe_objects 视图中定义为 object_type 'pred_compare' 的全局源  。  
  
 *number*  
 任何数值类型，包括 decimal  。 局限性在于缺少可用物理内存，或数值过大而无法用 64 位整数表示。  
  
 'string  '  
 进行谓词比较所需的 ANSI 字符串或 Unicode 字符串。 不为谓词比较函数执行隐式字符串类型转换。 传递错误类型会导致出错。  
  
 ADD TARGET [event_module_guid].event_package_name.target_name     
 表示要与事件会话关联的目标，其中：  
  
-   event_module_guid 为包含该事件的模块的 GUID  。  
  
-   event_package_name 为包含操作对象的包  。  
  
-   target_name 为目标  。 目标在 sys.dm_xe_objects 视图中显示为 object_type 'target'。  
  
 SET { target_parameter_name= \<value> [, ...n] }    
 设置目标参数。 目标参数在 sys.dm_xe_object_columns 视图中显示为 column_type 'customizable' 以及 object_name = target_name  。  
  
> [!IMPORTANT]  
>  如果您在使用环形缓冲区目标，我们建议您将 max_memory 目标参数设置为 2048 KB，以便避免在 XML 输出中可能发生数据截断。 有关何时使用不同目标类型的详细信息，请参阅 [SQL Server 扩展事件目标](https://msdn.microsoft.com/library/e281684c-40d1-4cf9-a0d4-7ea1ecffa384)。  
  
 WITH ( \<event_session_options> [ ,...n] ) 指定要与事件会话一起使用的选项  。  
  
 MAX_MEMORY =size [ KB | MB   ]  
 指定要分配给会话用来缓冲事件的最大内存量。 默认值为 4 MB。 size 是整数，并且其值可以以千字节 (KB) 或兆字节 (MB) 表示  。 最大内存量不能超过 2 GB（小于 2048 MB）。 但是，不建议使用 GB 范围内的内存值。
  
 EVENT_RETENTION_MODE = { ALLOW_SINGLE_EVENT_LOSS | ALLOW_MULTIPLE_EVENT_LOSS | NO_EVENT_LOSS }   
 指定要用于处理事件丢失的事件保留模式。  
  
 ALLOW_SINGLE_EVENT_LOSS   
 事件可能会从会话中丢失。 只有在所有事件缓冲区均已满时才删除单个事件。 通过在事件缓冲区已满时丢失单个事件，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 可实现足以满足要求的性能特征，同时还可使处理的事件流中的数据丢失降到最低。  
  
 ALLOW_MULTIPLE_EVENT_LOSS  
 包含多个事件的已满事件缓冲区可能会从会话中丢失。 丢失事件的数目取决于分配给会话的内存大小、内存的分区情况以及缓冲区中事件的大小。 在事件缓冲区迅速达到已满状态时，该选项可将对服务器性能的影响降至最低，但可能会有大量的事件从会话中丢失。  
  
 NO_EVENT_LOSS  
 不允许事件丢失。 此选项可确保所有引发的事件都将得以保留。 使用此选项可强制所有激发事件的任务一直等到事件缓冲区中有可用空间时才执行。 这可能会在事件会话处于活动状态时引发可察觉到的性能问题。 在等待从缓冲区刷新事件时，用户连接可能中断。  
  
 MAX_DISPATCH_LATENCY = { seconds SECONDS | INFINITE   }  
 指定将事件调度至事件会话目标前事件将在内存中缓冲的时间。 默认情况下，此值设置为 30 秒。  
  
 seconds SECONDS   
 在开始将缓冲区刷新到目标前等待的时间（单位为秒）。 seconds 是一个整数  。 最小滞后时间值为 1 秒。 但是，可以使用 0 来指定 INFINITE 滞后时间。  
  
 INFINITE   
 仅在缓冲区已满或事件会话关闭时才将缓冲区刷新到目标。  
  
> [!NOTE]  
>  MAX_DISPATCH_LATENCY = 0 SECONDS 等效于 MAX_DISPATCH_LATENCY = INFINITE。  
  
 MAX_EVENT_SIZE =size [ KB | MB ]    
 指定允许的最大事件大小。 MAX_EVENT_SIZE 应仅设置为允许单个事件大于 MAX_MEMORY；将其设置为小于 MAX_MEMORY 将引发错误。 size 是整数，并且其值可以以千字节 (KB) 或兆字节 (MB) 表示  。 如果以千字节为单位指定 size，则允许的最小大小为 64 KB  。 设置 MAX_EVENT_SIZE 后，除 MAX_MEMORY 之外，还创建了两个大小为 size 的缓冲区  。 也就是说，用于事件缓冲的总内存为 MAX_MEMORY + 2 * MAX_EVENT_SIZE。  
  
 MEMORY_PARTITION_MODE = { NONE | PER_NODE | PER_CPU }   
 指定事件缓冲区的创建位置。  
  
 **NONE**  
 在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例中创建一组缓冲区。  
  
 PER_NODE  
 为每个 NUMA 节点创建一组缓冲区。  
  
 PER_CPU  
 为每个 CPU 创建一组缓冲区。  
  
 TRACK_CAUSALITY = { ON | OFF }   
 指定是否跟踪因果关系。 如果已启用，因果关系将允许将不同服务器连接上的相关事件关联在一起。  
  
 STARTUP_STATE = { ON | OFF  }  
 指定在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 启动时是否自动启动此事件会话。  
  
> [!NOTE]  
> 如果 `STARTUP_STATE = ON`，则事件会话将只在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 停止并重新启动的情况下才启动。  
  
 ON  
 启动时事件会话会启动。  
  
 **OFF**  
 启动时事件会话不启动。  
  
## <a name="remarks"></a>Remarks  
逻辑运算符的优先顺序是 `NOT`（最高），然后是 `AND`，最后是 `OR`。  
  
## <a name="permissions"></a>权限  
在 SQL Server 上，需要 `ALTER ANY EVENT SESSION` 权限。 在 SQL 数据库上，需要在数据库中拥有 `ALTER ANY DATABASE EVENT SESSION` 权限。
  
## <a name="examples"></a>示例  
 以下示例说明如何创建一个名为 `test_session` 的事件会话。 此示例添加了两个事件并使用 Windows 事件跟踪目标。  
  
```sql  
IF EXISTS(SELECT * FROM sys.server_event_sessions WHERE name='test_session')  
    DROP EVENT session test_session ON SERVER;  
GO  
CREATE EVENT SESSION test_session  
ON SERVER  
    ADD EVENT sqlos.async_io_requested,  
    ADD EVENT sqlserver.lock_acquired  
    ADD TARGET package0.etw_classic_sync_target   
        (SET default_etw_session_logfile_path = N'C:\demo\traces\sqletw.etl' )  
    WITH (MAX_MEMORY=4MB, MAX_EVENT_SIZE=4MB);  
GO  
```  

### <a name="code-examples-can-differ-for-azure-sql-database"></a>Azure SQL 数据库的代码示例可能有所不同

[!INCLUDE[sql-on-premises-vs-azure-similar-sys-views-include.](../../includes/paragraph-content/sql-on-premises-vs-azure-similar-sys-views-include.md)]

## <a name="see-also"></a>另请参阅  
 [ALTER EVENT SESSION (Transact-SQL)](../../t-sql/statements/alter-event-session-transact-sql.md)   
 [DROP EVENT SESSION (Transact-SQL)](../../t-sql/statements/drop-event-session-transact-sql.md)   
 [sys.server_event_sessions (Transact-SQL)](../../relational-databases/system-catalog-views/sys-server-event-sessions-transact-sql.md)   
 [sys.dm_xe_objects (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-xe-objects-transact-sql.md)   
 [sys.dm_xe_object_columns (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-xe-object-columns-transact-sql.md)   
  

