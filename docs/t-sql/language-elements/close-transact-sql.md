---
title: CLOSE (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- CLOSE_TSQL
- CLOSE
dev_langs:
- TSQL
helpviewer_keywords:
- closing cursors
- cursors [SQL Server], closing
- CLOSE statement
ms.assetid: 21546874-97e3-4b93-970f-87c27f6b78c7
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 3f2d77bc9eaab5b49933b672bbb0cba27b816538
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "65983216"
---
# <a name="close-transact-sql"></a>CLOSE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  释放当前结果集，然后解除定位游标的行上的游标锁定，从而关闭一个开放的游标。 `CLOSE` 将保留数据结构以便重新打开，但在重新打开游标之前，不允许提取和定位更新。 必须对打开的游标发布 CLOSE；不允许对仅声明或已关闭的游标执行 `CLOSE`。  
  
 ![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "主题链接图标") [TRANSACT-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>语法  
  
```  
CLOSE { { [ GLOBAL ] cursor_name } | cursor_variable_name }  
```  
  
## <a name="arguments"></a>参数  
 GLOBAL  
 指定 cursor_name 是指全局游标  。  
  
 cursor_name   
 打开的游标的名称。 当同时存在以 cursor_name 作为名称的全局游标和局部游标时，如果指定 GLOBAL，则 cursor_name 是指全局游标；否则，cursor_name 是指局部游标    。  
  
 cursor_variable_name   
 与打开的游标关联的游标变量的名称。  
  
## <a name="examples"></a>示例  
 以下示例将显示 `CLOSE` 语句在基于游标的进程中的正确位置。  
  
```sql  
DECLARE Employee_Cursor CURSOR FOR  
SELECT EmployeeID, Title FROM AdventureWorks2012.HumanResources.Employee;  
OPEN Employee_Cursor;  
FETCH NEXT FROM Employee_Cursor;  
WHILE @@FETCH_STATUS = 0  
   BEGIN  
      FETCH NEXT FROM Employee_Cursor;  
   END;  
CLOSE Employee_Cursor;  
DEALLOCATE Employee_Cursor;  
GO  
```  
  
## <a name="see-also"></a>另请参阅  
 [游标](../../relational-databases/cursors.md)   
 [游标 (Transact-SQL)](../../t-sql/language-elements/cursors-transact-sql.md)   
 [DEALLOCATE (Transact-SQL)](../../t-sql/language-elements/deallocate-transact-sql.md)   
 [FETCH (Transact-SQL)](../../t-sql/language-elements/fetch-transact-sql.md)   
 [OPEN (Transact-SQL)](../../t-sql/language-elements/open-transact-sql.md)  
  
  
