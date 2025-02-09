---
title: dbo.sysoperators (Transact SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysoperators
- dbo.sysoperators
- dbo.sysoperators_TSQL
- sysoperators_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysoperators system table
ms.assetid: c2afa20c-b15f-46ca-ae74-2eb65909409e
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 3796714cbdfb55900447bf23904136ac5abefa9c
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "62470651"
---
# <a name="dbosysoperators-transact-sql"></a>dbo.sysoperators (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  对每个 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理操作员包含一行。  
  
|列名|数据类型|Description|  
|-----------------|---------------|-----------------|  
|**id**|**int**|操作员 ID。|  
|**名称**|**sysname**|操作员名称。|  
|**enabled**|**tinyint**|警报通知的状态 (Boolean)。 如果**1**，发生警报时，此运算符可接收通知。|  
|**email_address**|**nvarchar(100)**|该操作员的电子邮件地址。|  
|**last_email_date**|**int**|该操作员上次接收电子邮件警报通知的日期。|  
|**last_email_time**|**int**|该操作员上次接收电子邮件警报通知的时间。|  
|**pager_address**|**nvarchar(100)**|该操作员的寻呼地址。|  
|**last_pager_date**|**int**|该操作员上次接收寻呼警报通知的日期。|  
|**last_pager_time**|**int**|该操作员上次接收寻呼警报通知的时间。|  
|**weekday_pager_start_time**|**int**|工作日（从星期一到星期五）中的某一时间，该操作员在该时间后可以接收寻呼警报通知。|  
|**weekday_pager_end_time**|**int**|工作日（从星期一到星期五）中的某一时间，该操作员在该时间后不能接收寻呼警报通知。|  
|**saturday_pager_start_time**|**int**|星期六当天的某一时间，该操作员在该时间后可以接收寻呼警报通知。|  
|**saturday_pager_end_time**|**int**|星期六当天的某一时间，该操作员在该时间后不能接收寻呼警报通知。|  
|**sunday_pager_start_time**|**int**|星期日当天的某一时间，该操作员在该时间后可以接收寻呼警报通知。|  
|**sunday_pager_end_time**|**int**|星期日当天的某一时间，该操作员在该时间后不能接收寻呼警报通知。|  
|**pager_days**|**tinyint**|表示一周中某几天的位掩码，该操作员在这几天内可以接收寻呼警报通知。|  
|**netsend_address**|**nvarchar(100)**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**last_netsend_date**|**int**|上次将最近网络消息发送到指定操作员 ID 的日期。|  
|**last_netsend_time**|**int**|上次将最新网络消息发送到指定操作员 ID 的时间。|  
|**category_id**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
  
## <a name="see-also"></a>请参阅  
 [SQL Server 代理表&#40;Transact SQL&#41;](../../relational-databases/system-tables/sql-server-agent-tables-transact-sql.md)  
  
  
