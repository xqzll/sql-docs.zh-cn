---
title: CURRENT_TRANSACTION_ID (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/24/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- CURRENT_TRANSACTION_ID
- CURRENT_TRANSACTION_ID_TSQL
- sys.CURRENT_TRANSACTION_ID
- sys.CURRENT_TRANSACTION_ID_TSQL
helpviewer_keywords:
- CURRENT_TRANSACTION_ID function
ms.assetid: 82cd9f92-d935-45a0-a433-620d6e15b467
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: d81571dbde882d1ec6b91e2a05933aeb178e19d4
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "65947916"
---
# <a name="currenttransactionid-transact-sql"></a>CURRENT_TRANSACTION_ID (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-xxxx-xxx-md.md)]

此函数返回当前会话中当前事务的事务 ID。
  
![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "主题链接图标") [TRANSACT-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>语法  
  
```sql
CURRENT_TRANSACTION_ID( )  
  
```  
  
## <a name="return-types"></a>返回类型
**bigint**
  
## <a name="return-value"></a>返回值  
当前会话中当前事务的事务 ID，取自 [sys.dm_tran_current_transaction (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-tran-current-transaction-transact-sql.md)。
  
## <a name="permissions"></a>权限  
任何用户都可返回当前会话的事务 ID。
  
## <a name="examples"></a>示例  
此示例返回当前会话的事务 ID：
  
```sql
SELECT CURRENT_TRANSACTION_ID();  
```  
  
## <a name="see-also"></a>另请参阅
[sp_set_session_context (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-set-session-context-transact-sql.md)  
[SESSION_CONTEXT (Transact-SQL)](../../t-sql/functions/session-context-transact-sql.md)  
[行级安全性](../../relational-databases/security/row-level-security.md)  
[CONTEXT_INFO (Transact-SQL)](../../t-sql/functions/context-info-transact-sql.md)  
[SET CONTEXT_INFO (Transact-SQL)](../../t-sql/statements/set-context-info-transact-sql.md)
  
  
