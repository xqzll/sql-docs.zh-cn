---
title: sp_droprolemember (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/20/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_droprolemember_TSQL
- sp_droprolemember
dev_langs:
- TSQL
helpviewer_keywords:
- sp_droprolemember
ms.assetid: c2f19ab1-e742-4d56-ba8e-8ffd40cf4925
ms.author: vanto
author: VanMSFT
manager: jroth
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: c235c23ac0be8dcaf6dc57dae14be9732f5c09f8
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "66822439"
---
# <a name="spdroprolemember-transact-sql"></a>sp_droprolemember (Transact-SQL)

[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  从当前数据库的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 角色中删除安全帐户。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] 使用[ALTER ROLE](../../t-sql/statements/alter-role-transact-sql.md)相反。  
  
 ![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "主题链接图标") [TRANSACT-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>语法  

### <a name="syntax-for-both-sql-server-and-azure-sql-database"></a>SQL Server 和 Azure SQL 数据库的语法

```  
sp_droprolemember [ @rolename = ] 'role' ,   
     [ @membername = ] 'security_account'  
```  

### <a name="syntax-for-both-azure-sql-data-warehouse-and-parallel-data-warehouse"></a>Azure SQL 数据仓库和并行数据仓库语法

```  
sp_droprolemember 'role' ,  
     'security_account'  
```  
  
## <a name="arguments"></a>参数  
`[ @rolename = ] 'role'` 是从中删除成员的名称。 *角色*是**sysname**，无默认值。 *角色*必须存在于当前数据库。  
  
`[ @membername = ] 'security_account'` 正在删除从角色中的安全帐户的名称。 *security_account*是**sysname**，无默认值。 *security_account*可以是数据库用户、 其他数据库角色、 Windows 登录名或 Windows 组。 *security_account*必须存在于当前数据库。  
  
## <a name="return-code-values"></a>返回代码值  
 0（成功）或 1（失败）  
  
## <a name="remarks"></a>备注  
 sp_droprolemember sysmembers 表中删除行的数据库角色中删除成员。 在从角色中删除一个成员后，该成员将失去作为该角色的成员所拥有的任何权限。  
  
 若要从固定的服务器角色中删除用户，请使用 sp_dropsrvrolemember。 不能从公共角色中删除用户和 dbo 不能从任何角色中删除。  
  
 使用 sp_helpuser 若要查看的成员[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]角色，并使用 ALTER ROLE，若要向角色添加成员。  
  
## <a name="permissions"></a>权限  
 要求具有角色的 ALTER 权限。  
  
## <a name="examples"></a>示例  
 以下示例将删除角色 `JonB` 中的用户 `Sales`。  
  
```sql
EXEC sp_droprolemember 'Sales', 'Jonb';  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>示例：[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] 和 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 以下示例将删除角色 `JonB` 中的用户 `Sales`。  
  
```sql
EXEC sp_droprolemember 'Sales', 'JonB'  
```  
  
## <a name="see-also"></a>请参阅  
 [安全存储过程 (Transact-SQL)](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [sp_addrolemember (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-addrolemember-transact-sql.md)   
 [sp_droprole (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-droprole-transact-sql.md)   
 [sp_dropsrvrolemember &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropsrvrolemember-transact-sql.md)   
 [sp_helpuser &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpuser-transact-sql.md)   
 [系统存储过程 (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  

