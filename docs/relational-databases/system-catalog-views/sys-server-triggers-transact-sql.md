---
title: sys.server_triggers (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- server_triggers
- sys.server_triggers_TSQL
- server_triggers_TSQL
- sys.server_triggers
dev_langs:
- TSQL
helpviewer_keywords:
- sys.server_triggers catalog view
ms.assetid: 25926ff4-9271-45bf-bc32-d5d3344bd47a
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 9b13aeed62a84258fcfbf5820c17dca59f4b5852
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "62660748"
---
# <a name="sysservertriggers-transact-sql"></a>sys.server_triggers (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  包含 object_type 为 TR 或 TA 的所有服务器级别 DDL 触发器的集合。 如果是 CLR 触发器的程序集必须加载到**主**数据库。 所有服务器级别 DDL 触发器名称存在于单个全局范围内。  
  
|列名|数据类型|描述|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|触发器的名称。|  
|**object_id**|**int**|对象的 ID。|  
|**parent_class**|**tinyint**|父级的类。 始终为：<br /><br /> 100 = 服务器|  
|**parent_class_desc**|**nvarchar(60)**|父类的说明。 始终为：<br /><br /> SERVER。|  
|**parent_id**|**int**|对 SERVER 上的触发器，此值始终为 0。|  
|**type**|**char(2)**|对象类型：<br /><br /> TA = 程序集 (CLR) 触发器<br /><br /> TR = SQL 触发器|  
|**type_desc**|**nvarchar(60)**|对象类型的类的说明。<br /><br /> CLR_TRIGGER<br /><br /> SQL_TRIGGER|  
|**create_date**|**datetime**|触发器的创建日期。|  
|**modify_date**|**datetime**|上一次使用 ALTER 语句修改触发器的日期。|  
|**is_ms_shipped**|**bit**|由内部 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 组件代表用户创建的触发器。|  
|**is_disabled**|**bit**|1 = 触发器被禁用。|  
  
## <a name="permissions"></a>权限  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 有关详细信息，请参阅 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)。  
  
## <a name="see-also"></a>请参阅  
 [目录视图 (Transact-SQL)](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)  
  
  
