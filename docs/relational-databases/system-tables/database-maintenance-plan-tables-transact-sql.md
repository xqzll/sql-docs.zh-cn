---
title: 数据库维护计划表 (Transact SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- database maintenance plans [SQL Server]
- maintenance plans [SQL Server], system tables
- system tables [SQL Server], database maintenance plans
ms.assetid: f264554c-5514-4df2-aadb-6dcdc2dfcfea
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 01e151f65c6decc7582a3c38413b180c6a51cb92
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "62471008"
---
# <a name="database-maintenance-plan-tables-transact-sql"></a>数据库维护计划表 (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  本节的主题说明用于存储数据库维护计划所用信息的系统表。 这些表保留已从早期版本的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 升级的实例的信息。  
  
> [!NOTE]  
>  [!INCLUDE[ssNoteDepNextAvoid](../../includes/ssnotedepnextavoid-md.md)]  
  
## <a name="in-this-section"></a>本节内容  
 [sysdbmaintplan_databases](../../relational-databases/system-tables/sysdbmaintplan-databases-transact-sql.md)  
 每个具有已升级的关联数据库维护计划的数据库在表中占一行。  
  
 [sysdbmaintplan_history](../../relational-databases/system-tables/sysdbmaintplan-history-transact-sql.md)  
 每个已执行的已升级数据库维护计划操作在表中占一行。  
  
 [sysdbmaintplan_jobs](../../relational-databases/system-tables/sysdbmaintplan-jobs-transact-sql.md)  
 每个已升级的数据库维护计划作业在表中占一行。  
  
 [sysdbmaintplans](../../relational-databases/system-tables/sysdbmaintplans-transact-sql.md)  
 每个已升级数据库维护计划在表中占一行。  
  
## <a name="see-also"></a>请参阅  
 [中对象资源管理器的](../../relational-databases/maintenance-plans/maintenance-plans.md)  
  
  
