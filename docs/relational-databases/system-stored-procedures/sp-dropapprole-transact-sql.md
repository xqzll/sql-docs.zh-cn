---
title: sp_dropapprole (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_dropapprole_TSQL
- sp_dropapprole
dev_langs:
- TSQL
helpviewer_keywords:
- sp_dropapprole
ms.assetid: ea1aefe6-8f7d-46e9-a3cb-7b037b393e73
ms.author: vanto
author: VanMSFT
manager: jroth
ms.openlocfilehash: 0928137201d9a731051ab95e603744f60c3a52e1
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "66822820"
---
# <a name="spdropapprole-transact-sql"></a>sp_dropapprole (Transact-SQL)

[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  从当前数据库删除应用程序角色。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)] 使用[DROP APPLICATION ROLE](../../t-sql/statements/drop-application-role-transact-sql.md)相反。  
  
 ![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "主题链接图标") [TRANSACT-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>语法  
  
```  
sp_dropapprole [@rolename = ] 'role'  
```  
  
## <a name="arguments"></a>参数  
`[ @rolename = ] 'role'` 是要删除的应用程序角色。 *角色*是**sysname**，无默认值。 *角色*必须存在于当前数据库。  
  
## <a name="return-code-values"></a>返回代码值  
 0（成功）或 1（失败）  
  
## <a name="remarks"></a>备注  
 **sp_dropapprole**仅可用于删除应用程序角色。 如果一个角色拥有任何安全对象，则不能删除此角色。 在删除拥有安全对象的应用程序角色之前，必须首先移交安全对象的所有权或将其删除。  
  
 **sp_dropapprole**不能在用户定义的事务内执行。  
  
## <a name="permissions"></a>权限  
 需要对数据库具有 ALTER ANY APPLICATION ROLE 权限。  
  
## <a name="examples"></a>示例  
 以下示例将从当前数据库中删除 `SalesApp` 应用程序角色。  
  
```sql
EXEC sp_dropapprole 'SalesApp';  
```  
  
## <a name="see-also"></a>请参阅  
 [安全存储过程 (Transact-SQL)](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [sp_addapprole &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addapprole-transact-sql.md)   
 [DROP APPLICATION ROLE (Transact-SQL)](../../t-sql/statements/drop-application-role-transact-sql.md)   
 [sp_changeobjectowner &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changeobjectowner-transact-sql.md)   
 [sp_setapprole (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-setapprole-transact-sql.md)   
 [系统存储过程 (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
