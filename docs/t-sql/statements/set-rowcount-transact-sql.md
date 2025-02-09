---
title: SET ROWCOUNT (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- SET_ROWCOUNT_TSQL
- ROWCOUNT_TSQL
- SET ROWCOUNT
- ROWCOUNT
dev_langs:
- TSQL
helpviewer_keywords:
- row return limitations [SQL Server]
- SET ROWCOUNT statement
- number of rows affected by statement
- ROWCOUNT option
- counting rows
- stopping queries
- limiting rows returned
- queries [SQL Server], stopping
ms.assetid: c6966fb7-6421-47ef-98f3-82351f2f6bdc
author: CarlRabeler
ms.author: carlrab
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 539cc61e73d56d4e1de8a1710294f760d109d5d6
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "62816970"
---
# <a name="set-rowcount-transact-sql"></a>SET ROWCOUNT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  使 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 在返回指定的行数之后停止处理查询。  
  
 ![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "主题链接图标") [TRANSACT-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>语法  
  
```  
SET ROWCOUNT { number | @number_var }   
```  
  
## <a name="arguments"></a>参数  
 number | @number_var    
 在停止特定查询之前要处理的行数（整数）。  
  
## <a name="remarks"></a>Remarks  
  
> [!IMPORTANT]  
>  在 SQL Server 的将来版本中，使用 SET ROWCOUNT 将不会影响 DELETE、INSERT 和 UPDATE 语句。 应避免在新的开发工作中将 SET ROWCOUNT 与 DELETE、INSERT 和 UPDATE 语句一起使用，并计划修改当前使用它的应用程序。 对于类似行为，请使用 TOP 语法。 有关详细信息，请参阅 [TOP (Transact-SQL)](../../t-sql/queries/top-transact-sql.md)。  
  
 要将此选项设置为 off 以便返回所有的行，请将 SET ROWCOUNT 指定为 0。  
  
 设置 SET ROWCOUNT 选项将使大多数 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句在受到指定数目的行影响后停止处理。 其中包括触发器。 ROWCOUNT 选项对动态游标无效，但它可以限制键集的行集和不敏感游标； 所以应慎用此选项。  
  
 如果行数值较小，则 SET ROWCOUNT 将覆盖 SELECT 语句 TOP 关键字。  
  
 SET ROWCOUNT 的设置是在执行时或运行时设置，而不是在分析时设置。  
  
## <a name="permissions"></a>权限  
 要求具有 public 角色的成员身份。  
  
## <a name="examples"></a>示例  
 SET ROWCOUNT 在达到指定的行数后停止处理。 请注意，在下面的示例中有超过 500 行满足 `Quantity` 小于 `300` 的条件。 但是，应用 SET ROWCOUNT 后，您可以看到并未返回所有行。  
  
```  
USE AdventureWorks2012;  
GO  
SELECT count(*) AS Count  
FROM Production.ProductInventory  
WHERE Quantity < 300;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
 Count 
 ----------- 
 537 
 
 (1 row(s) affected)
 ```  
  
 现在，将 `ROWCOUNT` 设置为 `4` 并返回所有行，以演示仅返回 4 行。  
  
```  
SET ROWCOUNT 4;  
SELECT *  
FROM Production.ProductInventory  
WHERE Quantity < 300;  
GO  
  
(4 row(s) affected)
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>示例：[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] 和 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 SET ROWCOUNT 在达到指定的行数后停止处理。 请注意，在下面的示例中共有 20 行满足 `AccountType = 'Assets'` 条件。 但是，应用 SET ROWCOUNT 后，您可以看到并未返回所有行。  
  
```  
-- Uses AdventureWorks  
  
SET ROWCOUNT 5;  
SELECT * FROM [dbo].[DimAccount]  
WHERE AccountType = 'Assets';  
```  
  
 若要返回所有行，请将 ROWCOUNT 设置为 0。  
  
```  
-- Uses AdventureWorks  
  
SET ROWCOUNT 0;  
SELECT * FROM [dbo].[DimAccount]  
WHERE AccountType = 'Assets';  
```  
  
## <a name="see-also"></a>另请参阅  
 [SET 语句 (Transact-SQL)](../../t-sql/statements/set-statements-transact-sql.md)  
  
  

