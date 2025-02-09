---
title: sp_help_downloadlist (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_help_downloadlist_TSQL
- sp_help_downloadlist
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_downloadlist
ms.assetid: 745b265b-86e8-4399-b928-c6969ca1a2c8
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: f6bb56be8654b37eea250122068ef52e165a2d99
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "62796152"
---
# <a name="sphelpdownloadlist-transact-sql"></a>sp_help_downloadlist (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  列出了中的所有行**sysdownloadlist**所提供的作业或如果未指定作业的所有行的系统表。  
  
 ![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "主题链接图标") [TRANSACT-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>语法  
  
```  
  
sp_help_downloadlist { [ @job_id = ] job_id | [ @job_name = ] 'job_name' }   
     [ , [ @operation = ] 'operation' ]   
     [ , [ @object_type = ] 'object_type' ]   
     [ , [ @object_name = ] 'object_name' ]   
     [ , [ @target_server = ] 'target_server' ]   
     [ , [ @has_error = ] has_error ]   
     [ , [ @status = ] status ]   
     [ , [ @date_posted = ] date_posted ]  
```  
  
## <a name="arguments"></a>参数  
`[ @job_id = ] job_id` 作业标识号为其返回信息。 *job_id*是**uniqueidentifier**，默认值为 NULL。  
  
`[ @job_name = ] 'job_name'` 作业的名称。 *job_name*是**sysname**，默认值为 NULL。  
  
> [!NOTE]  
>  任一*job_id*或*job_name*必须指定，但不能同时指定两者。  
  
`[ @operation = ] 'operation'` 针对指定的作业的有效操作。 *操作*是**varchar(64)** ，默认值为 NULL，并且可以是下列值之一。  
  
|ReplTest1|Description|  
|-----------|-----------------|  
|**DEFECT**|服务器操作，请求从主目标服务器脱离**SQLServerAgent**服务。|  
|**DELETE**|作业操作，删除整个作业。|  
|**INSERT**|作业操作，插入整个作业或者刷新现有作业。 如果可用，此操作将包含所有作业步骤与作业计划。|  
|**RE-ENLIST**|服务器操作，使目标服务器再次将其登记信息（包括轮询间隔和时区）发送到多服务器域。 目标服务器还将重新下载**MSXOperator**详细信息。|  
|**SET-POLL**|服务器操作，设置目标服务器轮询多服务器域的间隔（以秒为单位）。 如果指定，*值*被解释为所需的时间间隔值，并且可以为值**10**到**28,800**。|  
|**START**|作业操作，请求开始执行作业。|  
|**停止**|作业操作，请求停止执行作业。|  
|**SYNC-TIME**|服务器作业，使目标服务器将其系统时钟与多服务器域时钟同步。 因为此操作的开销很大，所以只能有限制地偶尔执行。|  
|**UPDATE**|作业操作，只更新**sysjobs**作业，而不是作业步骤或计划的信息。 将自动调用**sp_update_job**。|  
  
`[ @object_type = ] 'object_type'` 指定作业的对象的类型。 *object_type*是**varchar(64)** ，默认值为 NULL。 *object_type*可以是 JOB 或 SERVER。 有关有效的详细信息*object_type*值，请参阅[sp_add_category &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-category-transact-sql.md)。  
  
`[ @object_name = ] 'object_name'` 对象的名称。 *object_name*是**sysname**，默认值为 NULL。 如果*object_type*是作业*object_name*是作业名称。 如果*object_type*是服务器， *object_name*是服务器名称。  
  
`[ @target_server = ] 'target_server'` 目标服务器的名称。 *target_server*是**nvarchar （128)** ，默认值为 NULL。  
  
`[ @has_error = ] has_error` 为作业是否应确认错误。 *has_error*是**tinyint**，默认值为 NULL，指示应确认没有错误。 **1**指示应确认所有错误。  
  
`[ @status = ] status` 作业的状态。 *状态*是**tinyint**，默认值为 NULL。  
  
`[ @date_posted = ] date_posted` 日期和时间上所做的所有条目，或指定的日期和时间应包含在结果中之后设置。 *date_posted*是**datetime**，默认值为 NULL。  
  
## <a name="return-code-values"></a>返回代码值  
 **0** （成功） 或**1** （失败）  
  
## <a name="result-sets"></a>结果集  
  
|列名|数据类型|Description|  
|-----------------|---------------|-----------------|  
|**instance_id**|**int**|指令的唯一整数标识号。|  
|**source_server**|**nvarchar(30)**|发出指令的服务器的计算机名。 在中[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 7.0 版中，这始终是主 (MSX) 服务器的计算机名称。|  
|**operation_code**|**nvarchar(4000)**|指令的操作代码。|  
|**object_name**|**sysname**|受指令影响的对象。|  
|**object_id**|**uniqueidentifier**|受指令影响的对象标识号 (**job_id**一个作业对象，或对服务器对象 0x00) 或特定于的数据值**operation_code**。|  
|**target_server**|**nvarchar(30)**|下载此指令的目标服务器。|  
|**error_message**|**nvarchar(1024)**|目标服务器处理此指令时，遇到问题而发出的错误消息（如果有）。<br /><br /> 注意：目标服务器下载所有任何错误消息块继续。|  
|**date_posted**|**datetime**|指令发布到表的日期。|  
|**date_downloaded**|**datetime**|目标服务器下载指令的日期。|  
|**status**|**tinyint**|作业的状态：<br /><br /> **0** = 尚未下载<br /><br /> **1** = 成功下载。|  
  
## <a name="permissions"></a>权限  
 默认情况下授予 **sysadmin** 固定服务器角色的成员执行此过程的权限。  
  
## <a name="examples"></a>示例  
 以下示例将列出 `sysdownloadlist` 作业的 `NightlyBackups` 中的行。  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_help_downloadlist  
    @job_name = N'NightlyBackups',  
    @operation = N'UPDATE',   
    @object_type = N'JOB',   
    @object_name = N'NightlyBackups',  
    @target_server = N'SEATTLE2',   
    @has_error = 1,   
    @status = NULL,   
    @date_posted = NULL ;  
GO  
```  
  
## <a name="see-also"></a>请参阅  
 [系统存储过程 (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
