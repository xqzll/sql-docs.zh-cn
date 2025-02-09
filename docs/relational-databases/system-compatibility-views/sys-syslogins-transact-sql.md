---
title: sys.syslogins (Transact SQL) |Microsoft Docs
ms.custom: ''
ms.date: 09/08/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- syslogins_TSQL
- syslogins
- sys.syslogins
- sys.syslogins_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.syslogins compatibility view
- syslogins system table
ms.assetid: 4cb34f17-a4bb-469f-a218-71f074e6308f
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 54372511cab4cbcc3ecd7d2afe875325e105163d
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "62671926"
---
# <a name="syssyslogins-transact-sql"></a>sys.syslogins (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  每个登录帐户在表中对应一行。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssnoteCompView](../../includes/ssnotecompview-md.md)]  
  
适用范围：[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]（[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 到[当前版本](https://go.microsoft.com/fwlink/p/?LinkId=299658)）  。  
  
|列名|数据类型|Description|  
|-----------------|---------------|-----------------|  
|**sid**|**varbinary(85)**|安全标识符。|  
|**status**|**smallint**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**createdate**|**datetime**|添加登录的日期。|  
|**updatedate**|**datetime**|更新登录的日期。|  
|**accdate**|**datetime**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**totcpu**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**totio**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**spacelimit**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**timelimit**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**resultlimit**|**int**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**名称**|**sysname**|用户的登录名。|  
|**dbname**|**sysname**|建立连接时，用户的默认数据库名。|  
|**password**|**nvarchar(128)**|返回 NULL。|  
|**language**|**sysname**|默认的用户语言。|  
|**denylogin**|**int**|1 = 登录名是 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 用户或组且已被拒绝访问。|  
|**hasaccess**|**int**|1 = 已授权登录名访问服务器。|  
|**isntname**|**int**|1 = 登录名是 Windows 用户或组。<br /><br /> 0 = 登录名是 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登录名。|  
|**isntgroup**|**int**|1 = 登录名是 Windows 组。|  
|**isntuser**|**int**|1 = 登录名是 Windows 用户。|  
|**sysadmin**|**int**|1 = 登录名是的成员**sysadmin**服务器角色。|  
|**securityadmin**|**int**|1 = 登录名是的成员**securityadmin**服务器角色。|  
|**serveradmin**|**int**|1 = 登录名是的成员**serveradmin**固定的服务器角色。|  
|**setupadmin**|**int**|1 = 登录名是的成员**setupadmin**固定的服务器角色。|  
|**processadmin**|**int**|1 = 登录名是的成员**processadmin**固定的服务器角色。|  
|**diskadmin**|**int**|1 = 登录名是的成员**diskadmin**固定的服务器角色。|  
|**dbcreator**|**int**|1 = 登录名是的成员**dbcreator**固定的服务器角色。|  
|**bulkadmin**|**int**|1 = 登录名是的成员**bulkadmin**固定的服务器角色。|  
|**loginname**|**nvarchar(128)**|用户的登录名。 提供该列是为了向后兼容。|  
  
## <a name="see-also"></a>请参阅  
 [系统表映射到系统视图&#40;Transact SQL&#41;](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)   
 [兼容性视图 (Transact SQL)](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)  
  
  
