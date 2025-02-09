---
title: sp_helpmergesubscription (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_helpmergesubscription
- sp_helpmergesubscription_TSQL
helpviewer_keywords:
- sp_helpmergesubscription
ms.assetid: da564112-f769-4e67-9251-5699823e8c86
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 4643cfc08db68e5369cfca25d2de76d314ffb347
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/27/2019
ms.locfileid: "58530669"
---
# <a name="sphelpmergesubscription-transact-sql"></a>sp_helpmergesubscription (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  返回有关对合并发布的订阅（推送订阅和请求订阅）的信息。 此存储过程用于在发布服务器上对发布数据库执行，或在正重新发布的订阅服务器上对订阅数据库执行。  
  
 ![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "主题链接图标") [TRANSACT-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>语法  
  
```  
  
sp_helpmergesubscription [ [ @publication=] 'publication']  
    [ , [ @subscriber=] 'subscriber']  
    [ , [ @subscriber_db=] 'subscriber_db']  
    [ , [ @publisher=] 'publisher']  
    [ , [ @publisher_db=] 'publisher_db']  
    [ , [ @subscription_type=] 'subscription_type']  
    [ , [ @found=] 'found' OUTPUT]  
```  
  
## <a name="arguments"></a>参数  
`[ @publication = ] 'publication'` 是发布的名称。 *发布*是**sysname**，默认值为**%**。 该发布必须已经存在，并符合标识符的相关规则。 如果为 NULL 或**%**，返回有关所有合并发布和订阅当前数据库中的信息。  
  
`[ @subscriber = ] 'subscriber'` 是订阅服务器的名称。 *订阅服务器上*是**sysname**，默认值为**%**。 如果为 NULL 或 %，则返回有关对给定发布的所有订阅信息。  
  
`[ @subscriber_db = ] 'subscriber_db'` 是订阅数据库的名称。 *subscriber_db*是**sysname**，默认值为**%**，表示返回有关所有订阅数据库的信息。  
  
`[ @publisher = ] 'publisher'` 是发布服务器的名称。 发布服务器必须为有效服务器。 *发布服务器*是**sysname**，默认值为**%**，表示返回有关所有发布服务器的信息。  
  
`[ @publisher_db = ] 'publisher_db'` 是发布服务器数据库的名称。 *publisher_db*是**sysname**，默认值为**%**，表示返回有关所有发布服务器数据库的信息。  
  
`[ @subscription_type = ] 'subscription_type'` 是订阅的类型。 *subscription_type*是**nvarchar(15)**，可以是下列值之一。  
  
|ReplTest1|Description|  
|-----------|-----------------|  
|**推送**（默认值）|推送订阅|  
|**pull**|请求订阅|  
|**两者**|推送订阅和请求订阅|  
  
`[ @found = ] 'found'OUTPUT` 是一个标志，指示返回行。 *找到*是**int**而且是 OUTPUT 参数，默认值为 NULL。 **1**指示已找到发布。 **0**指示找不到该发布。  
  
## <a name="result-sets"></a>结果集  
  
|列名|数据类型|Description|  
|-----------------|---------------|-----------------|  
|**subscription_name**|**sysname**|订阅的名称。|  
|**publication**|**sysname**|发布的名称。|  
|**publisher**|**sysname**|发布服务器的名称。|  
|**publisher_db**|**sysname**|发布服务器数据库名。|  
|**订阅服务器**|**sysname**|订阅服务器的名称。|  
|**subscriber_db**|**sysname**|订阅数据库的名称。|  
|**status**|**int**|订阅的状态：<br /><br /> **0** = 所有作业都在等待开始<br /><br /> **1** = 一个或多个作业正在启动<br /><br /> **2** = 所有作业都已成功执行<br /><br /> **3** = 至少一个作业正在执行<br /><br /> **4** = 所有作业计划和空闲<br /><br /> **5** = 至少一个作业正在尝试在上一次失败后执行<br /><br /> **6** = 至少一个作业无法成功执行|  
|**subscriber_type**|**int**|订阅服务器的类型。|  
|**subscription_type**|**int**|订阅的类型：<br /><br /> **0** = 推送<br /><br /> **1** = 请求<br /><br /> **2** = both|  
|**priority**|**float(8)**|指示订阅优先级的数字。|  
|**sync_type**|**tinyint**|订阅同步类型。|  
|**description**|**nvarchar(255)**|对该合并订阅的简短说明。|  
|**merge_jobid**|**binary(16)**|合并代理的作业 ID。|  
|**full_publication**|**tinyint**|指定订阅是完全发布还是筛选发布。|  
|**offload_enabled**|**bit**|指定复制代理的卸载执行是否设置为在订阅服务器上运行。 如果为 NULL，则执行将在发布服务器上运行。|  
|**offload_server**|**sysname**|运行代理的服务器名。|  
|**use_interactive_resolver**|**int**|返回在调节过程中是否使用交互式冲突解决程序。 如果**0**，不使用交互式冲突解决程序。|  
|**hostname**|**sysname**|订阅筛选的值时提供值[HOST_NAME](../../t-sql/functions/host-name-transact-sql.md)函数。|  
|**subscriber_security_mode**|**smallint**|安全模式在订阅服务器上，其中**1**表示 Windows 身份验证，并**0**意味着[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]身份验证。|  
|**subscriber_login**|**sysname**|在订阅服务器上的登录名。|  
|**subscriber_password**|**sysname**|永远不会返回实际的订阅服务器密码。 通过屏蔽结果"**\*\*\*\*\*\***"字符串。|  
  
## <a name="return-code-values"></a>返回代码值  
 **0** （成功） 或**1** （失败）  
  
## <a name="remarks"></a>备注  
 **sp_helpmergesubscription**合并复制用来返回存储在发布服务器或重新发布订阅服务器的订阅信息。  
  
 对于匿名订阅， *subscription_type*值始终是**1** （拉取）。 但是，必须执行[sp_helpmergepullsubscription](../../relational-databases/system-stored-procedures/sp-helpmergepullsubscription-transact-sql.md)在订阅服务器有关匿名订阅的信息。  
  
## <a name="permissions"></a>权限  
 只有的成员**sysadmin**固定服务器角色**db_owner**固定的数据库角色或订阅所属的发布的发布访问列表才能执行**sp_helpmergesubscription**。  
  
## <a name="see-also"></a>请参阅  
 [sp_addmergesubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addmergesubscription-transact-sql.md)   
 [sp_changemergesubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changemergesubscription-transact-sql.md)   
 [sp_dropmergesubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropmergesubscription-transact-sql.md)   
 [系统存储过程 (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
