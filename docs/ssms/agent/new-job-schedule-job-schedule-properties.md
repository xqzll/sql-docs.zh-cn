---
title: 新建作业计划 - 作业计划属性 | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql13.ag.job.scheduleproperties.f1
- sql13.swb.maint.editrecurringjobsched.f1
ms.assetid: 5c0b1bc9-dd87-49cc-b0dd-75d0d922b177
author: markingmyname
ms.author: maghan
manager: craigg
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: cedcba1f41921a0e364a3e5419bec82cfa273920
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "65105513"
---
# <a name="new-job-schedule---job-schedule-properties"></a>新建作业计划 - 作业计划属性
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> [Azure SQL 数据库托管实例](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance)目前支持大多数但并非所有 SQL Server 代理功能。 有关详细信息，请参阅 [Azure SQL 数据库托管实例与 SQL Server 之间的 T-SQL 差异](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent)。

使用此页可以查看和更改计划的属性。  
  
## <a name="options"></a>选项  
**名称**  
为计划键入一个新名称。  
  
**计划中的作业**  
查看使用该计划的作业。  
  
**计划类型**  
选择计划的类型。  
  
**已启用**  
选中此项可以启用或禁用该计划。  
  
## <a name="recurring-schedule-types-options"></a>重复执行计划类型选项  
**执行**  
选择重复执行计划的间隔。  
  
**执行间隔**  
选择重复执行计划的间隔天数或星期数。 此选项对于每月重复执行计划不可用。  
  
**星期一**  
设置作业在特定的星期一发生。 只用于每周重复执行计划。  
  
**星期二**  
设置作业在特定的星期二发生。 只用于每周重复执行计划。  
  
**星期三**  
设置作业在特定的星期三发生。 只用于每周重复执行计划。  
  
**星期四**  
设置作业在特定的星期四发生。 只用于每周重复执行计划。  
  
**星期五**  
设置作业在特定的星期五发生。 只用于每周重复执行计划。  
  
**星期六**  
设置作业在特定的星期六发生。 只用于每周重复执行计划。  
  
**星期日**  
设置作业在特定的星期日发生。 只用于每周重复执行计划。  
  
**Day**  
选择每月中执行此计划的日期。 只用于每月重复执行计划。  
  
**每**  
选择两次计划间隔的月数。 只用于每月重复执行计划。  
  
**“应用程序池:”**  
为某月内特定一周的特定一天指定计划。 只用于每月重复执行计划。  
  
**执行一次，时间为**  
设置每天执行作业的时间。  
  
**执行间隔**  
设置作业两次发生之间的时间间隔（小时、分钟或秒钟）。  
  
**开始日期**  
设置此计划开始生效的日期。  
  
**结束日期**  
设置计划的失效日期。  
  
**无结束日期**  
指定计划将无限期地保持有效。  
  
## <a name="one-time-schedule-types-options"></a>一次性计划类型选项  
**Date**  
选择作业的计划运行日期。  
  
**Time**  
选择作业的计划运行时间。  
  
## <a name="see-also"></a>另请参阅  
[创建计划并将计划附加到作业](../../ssms/agent/create-and-attach-schedules-to-jobs.md)  
[安排作业计划](../../ssms/agent/schedule-a-job.md)  
  
