---
title: sys.database_scoped_credentials (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/27/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse
ms.reviewer: ''
ms.technology: system-objects
ms.topic: conceptual
f1_keywords:
- sys.database_scoped_credentials
- sys.database_scoped_credentials_TSQL
- database_scoped_credentials
- database_scoped_credentials_TSQL
helpviewer_keywords:
- sys.database_scoped_credentials catalog view
ms.assetid: 68e8aa6b-bcdc-42aa-93d8-d498f724c188
author: VanMSFT
ms.author: vanto
manager: craigg
monikerRange: =azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 1deb05541e46ec1007d234dc622b14ea1e20eb3f
ms.sourcegitcommit: c0e48b643385ce19c65ca6e348ce83b2d22b6514
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/01/2019
ms.locfileid: "67492578"
---
# <a name="sysdatabasescopedcredentials-transact-sql"></a>sys.database_scoped_credentials (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-asdw-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-asdw-xxx-md.md)]

  为每个数据库返回一行作用域数据库中的凭据。  
  
|列名|数据类型|Description|  
|-----------------|---------------|-----------------|  
|name|**sysname**|数据库的名称范围的凭据。 是在数据库中唯一的。|  
|credential_id|**int**|数据库范围凭据的 ID。 是在数据库中唯一的。|  
|principal_id|**int**|拥有密钥的数据库主体的 ID。|  
|credential_identity|**nvarchar(4000)**|要使用的标识的名称。 这通常是一个 Windows 用户。 它不必是唯一的。|  
|create_date|**datetime**|在其中创建数据库范围凭据的时间。|  
|modify_date|**datetime**|数据库作用域凭据的上次修改时间。|  
|target_type|**nvarchar(100)**|类型的数据库范围凭据。 返回`NULL`数据库范围的凭据。|  
|target_id|**int**|数据库作用域凭据映射到的对象 ID。 返回 0 个数据库范围的凭据|  
  
## <a name="permissions"></a>权限  
 需要对数据库拥有 `CONTROL` 权限。  
  
## <a name="see-also"></a>请参阅  
 [凭据（数据库引擎）](../../relational-databases/security/authentication-access/credentials-database-engine.md)   
 [CREATE DATABASE SCOPED CREDENTIAL (Transact-SQL)](../../t-sql/statements/create-database-scoped-credential-transact-sql.md)   
 [ALTER DATABASE SCOPED CREDENTIAL (Transact-SQL)](../../t-sql/statements/alter-database-scoped-credential-transact-sql.md)   
 [DROP DATABASE SCOPED CREDENTIAL (Transact-SQL)](../../t-sql/statements/drop-database-scoped-credential-transact-sql.md)   
 [CREATE CREDENTIAL &#40;Transact-SQL&#41;](../../t-sql/statements/create-credential-transact-sql.md)   
 [sys.credentials (Transact-SQL)](../../relational-databases/system-catalog-views/sys-credentials-transact-sql.md)  
  
  
