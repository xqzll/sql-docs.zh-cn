---
title: sp_set_session_context (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 05/14/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_set_session_context
- sp_set_session_context_TSQL
- sys.sp_set_session_context
- sys.sp_set_session_context_TSQL
helpviewer_keywords:
- sp_set_session_context
ms.assetid: 7a3a3b2a-1408-4767-a376-c690e3c1fc5b
author: VanMSFT
ms.author: vanto
manager: craigg
monikerRange: =azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 25f9d67ee50f7c33391027d69c7db87aac8d7210
ms.sourcegitcommit: 869d4de6c807a37873b66e5479d2c5ceff9efb85
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/03/2019
ms.locfileid: "67559425"
---
# <a name="spsetsessioncontext-transact-sql"></a>sp_set_session_context (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-asdb-asdw-xxx-md](../../includes/tsql-appliesto-ss2016-asdb-asdw-xxx-md.md)]

会话上下文中设置键 / 值对。  
  

 ![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "主题链接图标") [TRANSACT-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>语法  
  
```  
sp_set_session_context [ @key= ] N'key', [ @value= ] 'value'  
    [ , [ @read_only = ] { 0 | 1 } ]  
[ ; ]  
```  
  
## <a name="arguments"></a>参数  
 [ @key= ] N'key'  
 正在设置的类型的键**sysname**。 最大密钥大小为 128 个字节。  
  
 [ @value= ] 'value'  
 类型的指定键的值**sql_variant**。 设置的值为 NULL 释放的内存。 最大大小为 8,000 个字节。  
  
 [ @read_only= ] { 0 | 1 }  
 类型的标志**位**。 如果为 1，然后指定键的值不能再次更改此逻辑连接。 如果可以更改 0 （默认值），则值。  
  
## <a name="permissions"></a>权限  
 任何用户可以为其会话设置会话上下文。  
  
## <a name="remarks"></a>备注  
 与其他存储过程一样可以作为参数传递唯一文本和变量 （非表达式或函数调用）。  
  
 会话上下文的总大小限于 1 MB。 如果设置一个值，导致超过此限制，该语句将失败。 你可以监视中的总体内存使用情况[sys.dm_os_memory_objects &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-memory-objects-transact-sql.md)。  
  
 可以通过查询监视总体内存使用情况[sys.dm_os_memory_cache_counters &#40;TRANSACT-SQL&#41; ](../../relational-databases/system-dynamic-management-views/sys-dm-os-memory-cache-counters-transact-sql.md) ，如下所示： `SELECT * FROM sys.dm_os_memory_cache_counters WHERE type = 'CACHESTORE_SESSION_CONTEXT';`  
  
## <a name="examples"></a>示例  
 下面的示例演示如何设置，然后返回一个名为的值为英语语言的会话上下文密钥。  
  
```  
EXEC sys.sp_set_session_context @key = N'language', @value = 'English';  
SELECT SESSION_CONTEXT(N'language');  
```  
  
 下面的示例演示如何将可选的只读标志。  
  
```  
EXEC sys.sp_set_session_context @key = N'user_id', @value = 4, @read_only = 1;  
```  
  
## <a name="see-also"></a>请参阅  
 [CURRENT_TRANSACTION_ID (Transact-SQL)](../../t-sql/functions/current-transaction-id-transact-sql.md)   
 [SESSION_CONTEXT (Transact-SQL)](../../t-sql/functions/session-context-transact-sql.md)   
 [行级安全性](../../relational-databases/security/row-level-security.md)   
 [CONTEXT_INFO (Transact-SQL)](../../t-sql/functions/context-info-transact-sql.md)   
 [SET CONTEXT_INFO (Transact-SQL)](../../t-sql/statements/set-context-info-transact-sql.md)  
  
  
