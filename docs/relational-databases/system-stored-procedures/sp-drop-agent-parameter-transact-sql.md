---
title: sp_drop_agent_parameter (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_drop_agent_parameter_TSQL
- sp_drop_agent_parameter
helpviewer_keywords:
- sp_drop_agent_parameter
ms.assetid: b99e65ff-9cca-4dce-a2ce-2968de23a76a
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 7abf2a3c2e9eebcd21a60beb72e650ad534cc80d
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/27/2019
ms.locfileid: "58528610"
---
# <a name="spdropagentparameter-transact-sql"></a>sp_drop_agent_parameter (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  从配置文件中删除一个或所有参数**MSagent_parameters**表。 此存储过程可在运行代理的分发服务器的任意数据库中执行。  
  
 ![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "主题链接图标") [TRANSACT-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>语法  
  
```  
  
sp_drop_agent_parameter [ @profile_id = ] profile_id  
    [ , [ @parameter_name = ] 'parameter_name' ]  
```  
  
## <a name="arguments"></a>参数  
`[ @profile_id = ] profile_id` 是为其参数是要删除的配置文件的 ID。 *profile_id*是**int**，无默认值。  
  
`[ @parameter_name = ] 'parameter_name'` 是要删除的名称。 *parameter_name*是**sysname**，默认值为**%**。 如果**%**，指定配置文件的所有参数将被都删除。  
  
## <a name="return-code-values"></a>返回代码值  
 **0** （成功） 或**1** （失败）  
  
## <a name="remarks"></a>备注  
 **sp_drop_agent_parameter**用于所有类型的复制。  
  
## <a name="permissions"></a>权限  
 只有的成员**sysadmin**固定的服务器角色可以执行**sp_drop_agent_parameter**。  
  
## <a name="see-also"></a>请参阅  
 [sp_add_agent_parameter &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-agent-parameter-transact-sql.md)   
 [sp_help_agent_parameter &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-agent-parameter-transact-sql.md)   
 [系统存储过程 (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
