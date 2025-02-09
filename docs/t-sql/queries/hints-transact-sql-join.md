---
title: 联接提示 (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 08/09/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- Join Hint
- Join_Hint_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- HASH join hint
- REMOTE join hint
- LOOP join hint
- join hints
- MERGE join hint
- hints [SQL Server], join
ms.assetid: 09069f4a-f2e3-4717-80e1-c0110058efc4
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: f1c99da1106f366e50d7c02bcc666a4e0c167bb6
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "66719443"
---
# <a name="hints-transact-sql---join"></a>提示 (Transact-SQL) - 联接
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  联接提示用于指定查询优化器在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 的两个表之间强制执行联接策略。 有关联接和联接语法的一般信息，请参阅 [FROM (Transact-SQL)](../../t-sql/queries/from-transact-sql.md)。  
  
> [!CAUTION]  
>  由于 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 查询优化器通常会为查询选择最佳执行计划，因此我们建议仅在最后迫不得已的情况下才可由资深的开发人员和数据库管理员使用提示。
  
 **适用范围：**  
  
 [DELETE](../../t-sql/statements/delete-transact-sql.md)  
  
 [SELECT](../../t-sql/queries/select-transact-sql.md)  
  
 [UPDATE](../../t-sql/queries/update-transact-sql.md)  
  
 ![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "主题链接图标") [TRANSACT-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>语法  
  
```  
  
<join_hint> ::=   
     { LOOP | HASH | MERGE | REMOTE }  
```  
  
## <a name="arguments"></a>参数  
 LOOP | HASH | MERGE  
 指定查询中的联接应使用循环、哈希或合并。 使用 LOOP |HASH | MERGE JOIN 在两个表之间强制执行特定联接。 不能同时将 LOOP 与 RIGHT（或 FULL）指定为联接类型。  
  
 REMOTE  
 指定联接操作在右表处执行。 这在左表是本地表而右表是远程表的情况下很有用。 只在左表的行数少于右表行数时才能使用 REMOTE。  
  
 如果右表为本地表，则联接在本地执行。 如果两个表均为远程表但来自不同的数据源，则 REMOTE 将使联接在右表处执行。 如果两个表均为远程表且来自相同数据源，则不需要使用 REMOTE。  
  
 如果使用 COLLATE 子句将联接谓词中比较的值中的一个值转换成了不同的排序规则，则不能使用 REMOTE。  
  
 REMOTE 只可用于 INNER JOIN 操作。  
  
## <a name="remarks"></a>Remarks  
 联接提示在查询的 FROM 子句中指定。 联接提示可以在两个表之间强制执行联接策略。 如果为任意两个表指定了联接提示，查询优化器会根据 ON 关键字的位置，自动为查询中所有联接的表强制确定联接顺序。 如果使用了不带 ON 子句的 CROSS JOIN，则可使用括号指示联接顺序。  
  
## <a name="examples"></a>示例  
  
### <a name="a-using-hash"></a>A. 使用 HASH  
 下面的示例指定查询中的 `JOIN` 操作由 `HASH` 联接执行。 该示例使用 [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] 数据库。  
  
```  
SELECT p.Name, pr.ProductReviewID  
FROM Production.Product AS p  
LEFT OUTER HASH JOIN Production.ProductReview AS pr  
ON p.ProductID = pr.ProductID  
ORDER BY ProductReviewID DESC;  
```  
  
### <a name="b-using-loop"></a>B. 使用 LOOP  
 下面的示例指定查询中的 `JOIN` 操作由 `LOOP` 联接执行。 该示例使用 [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] 数据库。  
  
```  
DELETE FROM Sales.SalesPersonQuotaHistory   
FROM Sales.SalesPersonQuotaHistory AS spqh  
    INNER LOOP JOIN Sales.SalesPerson AS sp  
    ON spqh.SalesPersonID = sp.SalesPersonID  
WHERE sp.SalesYTD > 2500000.00;  
GO  
```  
  
### <a name="c-using-merge"></a>C. 使用 MERGE  
 下面的示例指定查询中的 `JOIN` 操作由 `MERGE` 联接执行。 该示例使用 [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] 数据库。  
  
```  
SELECT poh.PurchaseOrderID, poh.OrderDate, pod.ProductID, pod.DueDate, poh.VendorID   
FROM Purchasing.PurchaseOrderHeader AS poh  
INNER MERGE JOIN Purchasing.PurchaseOrderDetail AS pod   
    ON poh.PurchaseOrderID = pod.PurchaseOrderID;  
GO  
```  
  
## <a name="see-also"></a>另请参阅  
 [提示 (Transact-SQL)](../../t-sql/queries/hints-transact-sql.md)  
  
  
