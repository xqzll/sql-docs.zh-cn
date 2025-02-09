---
title: CHECKSUM_AGG (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/24/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- CHECKSUM_AGG
- CHECKSUM_AGG_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- checksum values
- CHECKSUM_AGG function
- groups [SQL Server], checksum values
ms.assetid: cdede70c-4eb5-4c92-98ab-b07787ab7222
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: b744bf63f2b001c0f2529d6430d2ec335202abfe
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "65946524"
---
# <a name="checksumagg-transact-sql"></a>CHECKSUM_AGG (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

此函数返回组中各值的校验和。 `CHECKSUM_AGG` 将忽略 null 值。 [OVER 子句](../../t-sql/queries/select-over-clause-transact-sql.md)可以遵循 `CHECKSUM_AGG`。
  
![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "主题链接图标") [TRANSACT-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>语法  
  
```sql
CHECKSUM_AGG ( [ ALL | DISTINCT ] expression )  
```  
  
## <a name="arguments"></a>参数  
**ALL**  
向所有值应用此聚合函数。 ALL 为默认参数。
  
DISTINCT  
指定 `CHECKSUM_AGG` 返回唯一值的校验和。
  
*expression*  
整数[表达式](../../t-sql/language-elements/expressions-transact-sql.md)。 `CHECKSUM_AGG` 不允许使用聚合函数或子查询。
  
## <a name="return-types"></a>返回类型
将所有表达式值的校验和作为 int 类型返回   。
  
## <a name="remarks"></a>Remarks  
`CHECKSUM_AGG` 可以检测表中的更改。
  
`CHECKSUM_AGG` 结果不取决于表中行的顺序。 此外，`CHECKSUM_AGG` 函数允许使用 `DISTINCT` 关键字和 `GROUP BY` 子句。
  
如果表达式列表值更改，则列表校验和值列表很可能也会更改。 但是，也存在计算校验和不会更改这一很小的可能性。
  
`CHECKSUM_AGG` 具有类似于其他聚合函数的功能。 有关详细信息，请参阅[聚合函数 (Transact-SQL)](../../t-sql/functions/aggregate-functions-transact-sql.md)。
  
## <a name="examples"></a>示例  
这些示例使用 `CHECKSUM_AGG` 检测 [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] 数据库中 `ProductInventory` 表的 `Quantity` 列中的更改。
  
```sql
--Get the checksum value before the column value is changed.  

SELECT CHECKSUM_AGG(CAST(Quantity AS int))  
FROM Production.ProductInventory;  
GO  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```
------------------------  
262  
```  
  
```sql
UPDATE Production.ProductInventory   
SET Quantity=125  
WHERE Quantity=100;  
GO  

--Get the checksum of the modified column.  
SELECT CHECKSUM_AGG(CAST(Quantity AS int))  
FROM Production.ProductInventory;  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```
------------------------  
287  
```  
  
## <a name="see-also"></a>另请参阅
[CHECKSUM (Transact-SQL)](../../t-sql/functions/checksum-transact-sql.md)  
[HASHBYTES (Transact-SQL)](../../t-sql/functions/hashbytes-transact-sql.md)  
[BINARY_CHECKSUM  &#40;Transact-SQL&#41;](../../t-sql/functions/binary-checksum-transact-sql.md)
[OVER Clause &#40;Transact-SQL&#41;](../../t-sql/queries/select-over-clause-transact-sql.md)
  
