---
title: '@@CURSOR_ROWS (Transact-SQL) | Microsoft Docs'
ms.custom: ''
ms.date: 08/18/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- '@@CURSOR_ROWS'
- '@@CURSOR_ROWS_TSQL'
dev_langs:
- TSQL
helpviewer_keywords:
- '@@CURSOR_ROWS function'
- cursors [SQL Server], last-opened
- last-opened cursor
- asynchronous cursors [SQL Server]
ms.assetid: 31bd7a97-7f28-42a8-ba24-24d16d22973d
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: ad753fbdd529cbe9bc53906479aa134029fcc45e
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "65947871"
---
# <a name="x40x40cursorrows-transact-sql"></a>&#x40;&#x40;CURSOR_ROWS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

它返回在连接上打开的上一个游标中当前拥有的限定行的数目。 为了提高性能，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 可异步填充大型键集和静态游标。 可调用 `@@CURSOR_ROWS` 以确定当 @@CURSOR_ROWS 被调用时检索了游标符合条件的行数。
  
![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "主题链接图标") [TRANSACT-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>语法  
  
```
@@CURSOR_ROWS  
```  
  
## <a name="return-types"></a>返回类型
**integer**
  
## <a name="return-value"></a>返回值  
  
|返回值|描述|  
|---|---|
|-m |游标被异步填充。 返回的值 (-m) 是键集中当前的行数*m*。|  
|-1|游标为动态游标。 因为动态游标可反映所有更改，所以游标符合条件的行数不断变化。 游标不一定检索所有符合条件的行。|  
|0|没有已打开的游标，对于上一个打开的游标没有符合条件的行，或上一个打开的游标已被关闭或被释放。|  
|*n*|游标已完全填充。 返回值 (n) 是游标中的总行数  。|  
  
## <a name="remarks"></a>Remarks  
如果异步打开最后一个游标，`@@CURSOR_ROWS` 返回负数。 如果 sp_configure cursor threshold 的值超过 0，且游标结果集中的行数大于游标阈值，则异步打开键集驱动程序或静态游标。
  
## <a name="examples"></a>示例  
此示例首先声明了一个游标，然后使用 `SELECT` 显示 `@@CURSOR_ROWS` 的值。 在游标打开前，该设置的值为 `0`，之后其值为 `-1`，后者表示游标键集被异步填充。
  
```sql
USE AdventureWorks2012;  
GO  
SELECT @@CURSOR_ROWS;  
DECLARE Name_Cursor CURSOR FOR  
SELECT LastName ,@@CURSOR_ROWS FROM Person.Person;  
OPEN Name_Cursor;  
FETCH NEXT FROM Name_Cursor;  
SELECT @@CURSOR_ROWS;  
CLOSE Name_Cursor;  
DEALLOCATE Name_Cursor;  
GO             
```  
  
下面是结果集。
  
```
-----------
0  
```

```
LastName
---------------
Sanchez
```

```
-----------
-1
```  
  
## <a name="see-also"></a>另请参阅
[游标函数 (Transact-SQL)](../../t-sql/functions/cursor-functions-transact-sql.md)  
[OPEN (Transact-SQL)](../../t-sql/language-elements/open-transact-sql.md)
  
  
