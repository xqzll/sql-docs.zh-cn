---
title: dbo.sysjobschedules (Transact SQL) |Microsoft Docs
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sysjobschedules
- dbo.sysjobschedules
- dbo.sysjobschedules_TSQL
- sysjobschedules_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sysjobschedules system table
ms.assetid: ccdafec7-2a9b-4356-bffb-1caa3a12db59
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: d055e9b76d248319bddb37241b1b79428ee5f3b5
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "62470805"
---
# <a name="dbosysjobschedules-transact-sql"></a>dbo.sysjobschedules (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  包含将由 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理执行的作业的计划信息。 此表存储中**msdb**数据库。  
  
> **注意**：**Sysjobschedules**表刷新可能会影响返回的值每隔 20 分钟**sp_help_jobschedule**存储过程。  
  
|列名|数据类型|Description|  
|-----------------|---------------|-----------------|  
|**schedule_id**|**int**|计划的 ID。|  
|**job_id**|**uniqueidentifier**|作业的 ID。|  
|**next_run_date**|**int**|计划运行作业的下一个日期。 日期格式为 YYYYMMDD。|  
|**next_run_time**|**int**|计划运行作业的时间。 时间格式为 HHMMSS，并使用 24 小时制。|  
  
## <a name="see-also"></a>请参阅  
 [dbo.sysschedules &#40;Transact-SQL&#41;](../../relational-databases/system-tables/dbo-sysschedules-transact-sql.md)  
  
  
