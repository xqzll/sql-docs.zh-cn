---
title: MSSQLSERVER_10538 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 10538 (Database Engine error)
ms.assetid: 284d19b4-4979-4cbe-a9be-ac1104433c69
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 163dd6e764f061e936f32fd530ca4c1b5a13421d
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "63048283"
---
# <a name="mssqlserver10538"></a>MSSQLSERVER_10538
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>详细信息  
  
|||  
|-|-|  
|产品名称|SQL Server|  
|事件 ID|10538|  
|事件源|MSSQLSERVER|  
|组件|SQLEngine|  
|符号名称|PG_INVALID_PLANGUIDE_HANDLE|  
|消息正文|因为指定的计划指南 ID 为 NULL 或无效，或者您对该计划指南引用的对象没有所需权限，所以找不到该计划指南。 请确保计划指南 ID 有效，当前会话设置为正确的数据库上下文，并且你对计划指南所引用的对象具有 ALTER DATABASE 权限或 ALTER 权限。|  
  
## <a name="explanation"></a>解释  
指定的计划指南 ID 为 NULL 或无效，或者您对该计划指南引用的对象没有所需权限。  
  
## <a name="user-action"></a>用户操作  
请确保计划指南 ID 有效，当前会话设置为正确的数据库上下文，并且你对计划指南所引用的对象具有 ALTER DATABASE 权限或 ALTER 权限。  
  
## <a name="see-also"></a>另请参阅  
[sp_create_plan_guide (Transact-SQL)](~/relational-databases/system-stored-procedures/sp-create-plan-guide-transact-sql.md)  
[计划指南](~/relational-databases/performance/plan-guides.md)  
[sp_create_plan_guide_from_handle (Transact-SQL)](~/relational-databases/system-stored-procedures/sp-create-plan-guide-from-handle-transact-sql.md)  
  
