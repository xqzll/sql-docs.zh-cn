---
title: SELECT @local_variable (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 09/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- variable_TSQL
- '@loca_variable'
- '@local'
- variable
- '@loca_variable_TSQL'
- '@local_TSQL'
dev_langs:
- TSQL
helpviewer_keywords:
- variables [SQL Server], assigning
- SELECT statement [SQL Server], @local_variable
- '@local_variable'
- local variables [SQL Server]
ms.assetid: 8e1a9387-2c5d-4e51-a1fd-a2a95f026d6f
author: rothja
ms.author: jroth
manager: craigg
monikerRange: = azuresqldb-current ||>= sql-server-2016 ||= azure-sqldw-latest||>= sql-server-linux-2017||= sqlallproducts-allversions
ms.openlocfilehash: 3ea8dffc7256d08788b2a3b12812cd1f6e8f9cbd
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "65981865"
---
# <a name="select-localvariable-transact-sql"></a>SELECT @local_variable (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-asdw-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-asdw-xxx-md.md)]

  将局部变量设置为表达式的值。  
  
 要分配变量，建议使用 [SET @local_variable](../../t-sql/language-elements/set-local-variable-transact-sql.md) 而不是 SELECT @local_variable  。  
  
 ![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "主题链接图标") [TRANSACT-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>语法  
  
```  
SELECT { @local_variable { = | += | -= | *= | /= | %= | &= | ^= | |= } expression } 
    [ ,...n ] [ ; ]  
```  
  
## <a name="arguments"></a>参数  
@local_variable   
 要为其赋值的声明变量。  
  
{= | += | -= | \*= | /= | %= | &= | ^= | |= }   
将右边的值赋给左边的变量。  
  
复合赋值运算符：  
  |运算符后的表达式 |action |   
  |-----|-----|  
  | = | 将后面的表达式赋给变量。 |  
  | += | 添加并赋值 |   
  | -= | 相减并赋值 |  
  | \*= | 乘并赋值 |  
  | /= | 除并赋值 |  
  | %= | 取模并赋值 |  
  | &= | “位与”并赋值 |  
  | ^= | “位异或”并赋值 |  
  | \|= | “位或”并赋值 |  
  
 *expression*  
 为任意有效的[表达式](../../t-sql/language-elements/expressions-transact-sql.md)。 此参数包含一个标量子查询。  
  
## <a name="remarks"></a>Remarks  
 SELECT @local_variable 通常用于将单个值返回到变量中  。 但是，如果 expression 是列的名称，则可返回多个值  。 如果 SELECT 语句返回多个值，则将返回的最后一个值赋给变量。  
  
 如果 SELECT 语句没有返回行，变量将保留当前值。 如果 expression 是不返回值的标量子查询，则将变量设为 NULL  。  
  
 一个 SELECT 语句可以初始化多个局部变量。  
  
> [!NOTE]  
>  包含变量赋值的 SELECT 语句不能也用于执行通常的结果集检索操作。  
  
## <a name="examples"></a>示例  
  
### <a name="a-use-select-localvariable-to-return-a-single-value"></a>A. 使用 SELECT @local_variable 返回单个值  
 在以下示例中，为变量 `@var1` 赋值 `Generic Name`。 由于 `Store` 表中不存在为 `CustomerID` 指定的值，因此对该表的查询不返回任何行。 变量的值仍为 `Generic Name`。  
  
```sql  
-- Uses AdventureWorks    
  
DECLARE @var1 varchar(30);         
SELECT @var1 = 'Generic Name';         
SELECT @var1 = Name         
FROM Sales.Store         
WHERE CustomerID = 1000 ;        
SELECT @var1 AS 'Company Name';  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```  
 Company Name  
 ------------------------------  
 Generic Name  
 ```  
  
### <a name="b-use-select-localvariable-to-return-null"></a>B. 使用 SELECT @local_variable 返回 null  
 在以下示例中，使用了一个子查询为 `@var1` 赋值。 由于为 `CustomerID` 请求的值不存在，因此子查询不返回值，并将变量设为 `NULL`。  
  
```sql  
-- Uses AdventureWorks  
  
DECLARE @var1 varchar(30)   
SELECT @var1 = 'Generic Name'   
SELECT @var1 = (SELECT Name   
FROM Sales.Store   
WHERE CustomerID = 1000)   
SELECT @var1 AS 'Company Name' ;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
Company Name  
----------------------------  
NULL  
```  
  
## <a name="see-also"></a>另请参阅  
 [DECLARE @local_variable (Transact-SQL)](../../t-sql/language-elements/declare-local-variable-transact-sql.md)   
 [表达式 (Transact-SQL)](../../t-sql/language-elements/expressions-transact-sql.md)   
 [复合运算符 (Transact-SQL)](../../t-sql/language-elements/compound-operators-transact-sql.md)   
 [SELECT (Transact-SQL)](../../t-sql/queries/select-transact-sql.md)  
  
  
