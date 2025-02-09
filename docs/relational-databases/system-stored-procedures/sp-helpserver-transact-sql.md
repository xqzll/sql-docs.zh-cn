---
title: sp_helpserver (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_helpserver
- sp_helpserver_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_helpserver
ms.assetid: e8f42de7-c738-41c3-8bf5-dbd559dc7184
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 31caafde6ea3cdd93355910f244ed5872b6990ff
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "62635884"
---
# <a name="sphelpserver-transact-sql"></a>sp_helpserver (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  报告某个特定远程服务器或复制服务器的信息，或者报告两种类型的所有服务器的信息。 提供服务器名称、服务器的网络名称、服务器的复制状态、服务器的标识号以及排序规则名称。 还提供连接到链接服务器的超时值，或对链接服务器进行查询的超时值。  
  
 ![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "主题链接图标") [TRANSACT-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>语法  
  
```  
  
sp_helpserver [ [ @server = ] 'server' ]   
  [ , [ @optname = ] 'option' ]   
  [ , [ @show_topology = ] 'show_topology' ]  
```  
  
## <a name="arguments"></a>参数  
`[ @server = ] 'server'` 是哪些报告信息的服务器。 当*服务器*未指定，则有关中的所有服务器的报表**master.sys.servers**。 *服务器*是**sysname**，默认值为 NULL。  
  
`[ @optname = ] 'option'` 说明服务器的选项。 *选项*是**varchar (** 35 **)** ，默认值为 NULL，并且必须是下列值之一。  
  
|ReplTest1|Description|  
|-----------|-----------------|  
|**排序规则兼容**|影响分布式查询在链接服务器上的执行。 如果此选项设置为 True，|  
|**数据访问**|启用和禁用链接服务器以进行分布式查询访问。|  
|**dist**|分发服务器。|  
|**dpub**|到该分发服务器的远程发布服务器。|  
|**惰性架构验证**|在查询开始跳过远程表的架构检查。|  
|**pub**|发布服务器。|  
|**rpc**|从指定的服务器启用 RPC。|  
|**rpc out**|对指定的服务器启用 RPC。|  
|**sub**|订阅服务器。|  
|**system**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**使用远程排序规则**|使用远程列的排序规则而不使用本地服务器的排序规则。|  
  
`[ @show_topology = ] 'show_topology'` 是指定服务器与其他服务器的关系。 *show_topology*是**varchar (** 1 **)** ，默认值为 NULL。 如果*show_topology*不等于**t**或为 NULL， **sp_helpserver**返回结果集部分中列出的列。 如果*show_topology*等于**t**，除了列出的结果集中的列**sp_helpserver**也会返回**topx**和**topy**信息。  
  
## <a name="return-code-values"></a>返回代码值  
 0（成功）或 1（失败）。  
  
## <a name="result-sets"></a>结果集  
  
|列名|数据类型|Description|  
|-----------------|---------------|-----------------|  
|**名称**|**sysname**|服务器名称。|  
|**network_name**|**sysname**|服务器的网络名称。|  
|**status**|**varchar(** 70 **)**|服务器状态。|  
|**id**|**char(** 4 **)**|服务器的标识号。|  
|**collation_name**|**sysname**|服务器的排序规则。|  
|**connect_timeout**|**int**|连接到链接服务器的超时值。|  
|**query_timeout**|**int**|查询链接服务器的超时值。|  
  
## <a name="remarks"></a>备注  
 一个服务器可以有多种状态。  
  
## <a name="permissions"></a>权限  
 不检查权限。  
  
## <a name="examples"></a>示例  
  
### <a name="a-displaying-information-about-all-servers"></a>A. 显示所有服务器的信息  
 以下示例通过使用不带参数的 `sp_helpserver` 来显示所有服务器的信息。  
  
```  
USE master;  
GO  
EXEC sp_helpserver;  
```  
  
### <a name="b-displaying-information-about-a-specific-server"></a>B. 显示某个特定服务器的信息  
 以下示例显示服务器 `SEATTLE2` 的所有信息。  
  
```  
USE master;  
GO  
EXEC sp_helpserver 'SEATTLE2';  
```  
  
## <a name="see-also"></a>请参阅  
 [数据库引擎存储过程&#40;Transact SQL&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [sp_adddistpublisher &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-adddistpublisher-transact-sql.md)   
 [sp_addserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addserver-transact-sql.md)   
 [sp_addsubscriber &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addsubscriber-transact-sql.md)   
 [sp_changesubscriber &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changesubscriber-transact-sql.md)   
 [sp_dropserver &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropserver-transact-sql.md)   
 [sp_dropsubscriber &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropsubscriber-transact-sql.md)   
 [sp_helpdistributor (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-helpdistributor-transact-sql.md)   
 [sp_helpremotelogin &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpremotelogin-transact-sql.md)   
 [sp_helpsubscriberinfo (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-helpsubscriberinfo-transact-sql.md)   
 [sp_serveroption (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-serveroption-transact-sql.md)   
 [系统存储过程 (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
