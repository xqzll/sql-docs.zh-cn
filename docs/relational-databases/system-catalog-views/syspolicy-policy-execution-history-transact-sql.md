---
title: syspolicy_policy_execution_history (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- syspolicy_policy_execution_history_TSQL
- syspolicy_policy_execution_history
dev_langs:
- TSQL
helpviewer_keywords:
- syspolicy_policy_execution_history view
ms.assetid: b13c44a7-6d49-4d50-abe1-e657fc52bb05
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: 155c88f9e23a706fe7124893a8dd0c5ac5f03173
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "62671786"
---
# <a name="syspolicypolicyexecutionhistory-transact-sql"></a>syspolicy_policy_execution_history (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  显示策略的执行时间、每次执行的结果以及有关出现的任何错误的详细信息。 下表介绍了 syspolicy_policy_execution_history 视图中的列。  
  
|列名|数据类型|Description|  
|-----------------|---------------|-----------------|  
|history_id|**bigint**|此记录的标识符。 每个记录指示一个策略及其一次启动时间。|  
|policy_id|**int**|策略标识符。|  
|start_date|**datetime**|尝试运行此策略的日期和时间。|  
|end_date|**datetime**|运行完此策略的时间。|  
|result|**bit**|策略成功或失败。 0 = 失败，1 = 成功。|  
|exception_message|**nvarchar(max)**|发生的异常所生成的消息。|  
|exception|**nvarchar(max)**|发生的异常的说明。|  
  
## <a name="remarks"></a>备注  
 [Syspolicy_policy_execution_history_details](../../relational-databases/system-catalog-views/syspolicy-policy-execution-history-details-transact-sql.md)视图包含有关策略和测试的条件表达式的目标的相关详细信息。  
  
## <a name="permissions"></a>权限  
 要求具有 msdb 数据库中 PolicyAdministratorRole 角色的成员身份。  
  
## <a name="see-also"></a>请参阅  
 [使用基于策略的管理来管理服务器](../../relational-databases/policy-based-management/administer-servers-by-using-policy-based-management.md)   
 [基于策略的管理视图 (Transact-SQL)](../../relational-databases/system-catalog-views/policy-based-management-views-transact-sql.md)  
  
  
