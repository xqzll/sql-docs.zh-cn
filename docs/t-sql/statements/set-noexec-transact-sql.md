---
title: SET NOEXEC (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- NOEXEC_TSQL
- SET_NOEXEC_TSQL
- SET NOEXEC
- NOEXEC
dev_langs:
- TSQL
helpviewer_keywords:
- queries [SQL Server], compiling
- SET NOEXEC statement
- compiling queries [SQL Server]
- NOEXEC option
ms.assetid: ba56fba1-af9b-4459-b6e4-5d7e71a7630b
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 4c131cfa111b31f857d3403ed23f2836da237fd8
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "62939887"
---
# <a name="set-noexec-transact-sql"></a>SET NOEXEC (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  编译每个查询但不执行。  
  
 ![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "主题链接图标") [TRANSACT-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>语法  
  
```  
  
SET NOEXEC { ON | OFF }  
```  
  
## <a name="remarks"></a>Remarks  
 当 SET NOEXEC 为 ON 时，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 将编译每一批 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句但并不执行它们。 当 SET NOEXEC 设置为 OFF 时，所有批处理将在编译后执行。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中的语句执行包含两个阶段：编译和执行。 该设置可用于让 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 在执行 [!INCLUDE[tsql](../../includes/tsql-md.md)] 代码时，验证代码中的语法和对象名。 它也可以用于调试通常是较大的批处理中的部分语句。  
  
 SET NOEXEC 设置是在执行或运行时设置的，而不是在分析时设置的。  
  
## <a name="permissions"></a>权限  
 要求具有 public 角色的成员身份。  
  
## <a name="examples"></a>示例  
 以下示例在有效查询、包含无效对象名称的查询以及包含不正确语法的查询中使用 `NOEXEC`。  
  
```  
USE AdventureWorks2012;  
GO  
PRINT 'Valid query';  
GO  
-- SET NOEXEC to ON.  
SET NOEXEC ON;  
GO  
-- Inner join.  
SELECT e.BusinessEntityID, e.JobTitle, v.Name  
FROM HumanResources.Employee AS e   
   INNER JOIN Purchasing.PurchaseOrderHeader AS poh  
   ON e.BusinessEntityID = poh.EmployeeID  
   INNER JOIN Purchasing.Vendor AS v  
   ON poh.VendorID = v.BusinessEntityID;  
GO  
-- SET NOEXEC to OFF.  
SET NOEXEC OFF;  
GO  
  
PRINT 'Invalid object name';  
GO  
-- SET NOEXEC to ON.  
SET NOEXEC ON;  
GO  
-- Function name uses is a reserved keyword.  
USE AdventureWorks2012;  
GO  
CREATE FUNCTION dbo.Values(@BusinessEntityID int)  
RETURNS TABLE  
AS  
RETURN (SELECT PurchaseOrderID, TotalDue  
   FROM dbo.PurchaseOrderHeader  
   WHERE VendorID = @BusinessEntityID);  
  
-- SET NOEXEC to OFF.  
SET NOEXEC OFF;  
GO  
  
PRINT 'Invalid syntax';  
GO  
-- SET NOEXEC to ON.  
SET NOEXEC ON;  
GO  
-- Built-in function incorrectly invoked.  
SELECT *  
FROM fn_helpcollations;  
-- Reset SET NOEXEC to OFF.  
SET NOEXEC OFF;  
GO  
```  
  
## <a name="see-also"></a>另请参阅  
 [SET 语句 (Transact-SQL)](../../t-sql/statements/set-statements-transact-sql.md)   
 [SET SHOWPLAN_ALL (Transact-SQL)](../../t-sql/statements/set-showplan-all-transact-sql.md)   
 [SET SHOWPLAN_TEXT (Transact-SQL)](../../t-sql/statements/set-showplan-text-transact-sql.md)  
  
  
