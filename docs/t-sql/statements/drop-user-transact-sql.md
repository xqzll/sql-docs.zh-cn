---
title: DROP USER (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 05/12/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- DROP_USER_TSQL
- DROP USER
dev_langs:
- TSQL
helpviewer_keywords:
- dropping users
- DROP USER statement
- deleting users
- database user removal [SQL Server]
- removing users
- users [SQL Server], removing
ms.assetid: d6e0e21a-7568-4321-b6d6-bcfba183a719
author: VanMSFT
ms.author: vanto
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: c12a499dbca9bfe4aac952fb8257acba67cf4c5d
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "62683660"
---
# <a name="drop-user-transact-sql"></a>DROP USER (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  从当前数据库中删除用户。  
  
 ![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "主题链接图标") [TRANSACT-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>语法  
  
```  
-- Syntax for SQL Server and Azure SQL Database  
  
DROP USER [ IF EXISTS ] user_name  
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
DROP USER user_name  
```  
  
## <a name="arguments"></a>参数  
 IF EXISTS   
 **适用范围**：[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]（[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] 到[当前版本](https://go.microsoft.com/fwlink/p/?LinkId=299658)、[!INCLUDE[sssds](../../includes/sssds-md.md)]）。  
  
 有条件地删除用户（仅当其已存在时）。  
  
 user_name   
 指定在此数据库中用于识别该用户的名称。  
  
## <a name="remarks"></a>Remarks  
 不能从数据库中删除拥有安全对象的用户。 必须先删除或转移安全对象的所有权，才能删除拥有这些安全对象的数据库用户。  
  
 不能删除 guest 用户，但可在除 master 或 tempdb 之外的任何数据库中执行 REVOKE CONNECT FROM GUEST 来撤消它的 CONNECT 权限，从而禁用 guest 用户。  
  
> [!CAUTION]  
>  [!INCLUDE[ssCautionUserSchema](../../includes/sscautionuserschema-md.md)]  
  
## <a name="permissions"></a>权限  
 需要对数据库具有 ALTER ANY USER 权限。  
  
## <a name="examples"></a>示例  
 以下示例将从 `AbolrousHazem` 数据库中删除数据库用户 `AdventureWorks2012`。  
  
```  
DROP USER AbolrousHazem;  
GO  
```  
  
## <a name="see-also"></a>另请参阅  
 [CREATE USER (Transact-SQL)](../../t-sql/statements/create-user-transact-sql.md)   
 [ALTER USER (Transact-SQL)](../../t-sql/statements/alter-user-transact-sql.md)   
 [EVENTDATA (Transact-SQL)](../../t-sql/functions/eventdata-transact-sql.md)  
  
