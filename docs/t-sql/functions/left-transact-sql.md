---
title: LEFT (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/13/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- LEFT
- LEFT_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- character strings [SQL Server], LEFT
- characters [SQL Server], leftmost
- LEFT function
- leftmost character of expression
ms.assetid: 44a8c71b-63d8-458b-8b5d-99d570067c3c
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 07fc18f3a2540fd1316078e7e53326d36964c735
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "65948674"
---
# <a name="left-transact-sql"></a>LEFT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  返回字符串中从左边开始指定个数的字符。  
  
 ![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "主题链接图标") [TRANSACT-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>语法  
  
```  
LEFT ( character_expression , integer_expression )  
```  
  
## <a name="arguments"></a>参数  
 *character_expression*  
 字符或二进制数据的[表达式](../../t-sql/language-elements/expressions-transact-sql.md)。 character_expression 可以是常量、变量或列  。 character_expression 可以是除 text 或 ntext 外的任何数据类型，可隐式转换为 varchar 或 nvarchar      。 否则，请使用 [CAST](../../t-sql/functions/cast-and-convert-transact-sql.md) 函数显式转换 character_expression  。  
  
 *integer_expression*  
 指定要返回的 character_expression 的字符数的正整数  。 如果 integer_expression 为负，则返回错误  。 如果 integer_expression 的数据类型为 bigint，且包含较大的值，则 character_expression 必须是较大的数据类型，如 varchar(max)     。  
  
 integer_expression 参数将 UTF-16 代理项字符计为一个字符  。  
  
## <a name="return-types"></a>返回类型  
 character_expression 为非 Unicode 字符数据类型时，返回 varchar   。  
  
 character_expression 为 Unicode 字符数据类型时，返回 nvarchar   。  
  
## <a name="remarks"></a>Remarks  
 在使用 SC 排序规则时，integer_expression 参数将 UTF-16 代理项对计为一个字符  。 有关详细信息，请参阅 [Collation and Unicode Support](../../relational-databases/collations/collation-and-unicode-support.md)。  
  
## <a name="examples"></a>示例  
  
### <a name="a-using-left-with-a-column"></a>A. 带列使用 LEFT  
 以下示例返回 [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] 数据库的 `Product` 表中每个产品名称中最左边的五个字符。  
  
```  
SELECT LEFT(Name, 5)   
FROM Production.Product  
ORDER BY ProductID;  
GO  
```  
  
### <a name="b-using-left-with-a-character-string"></a>B. 带字符串使用 LEFT  
 以下示例使用 `LEFT` 函数返回字符串 `abcdefg` 中最左边的两个字符。  
  
```  
SELECT LEFT('abcdefg',2);  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
--   
ab   
  
(1 row(s) affected)  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>示例：[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] 和 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="c-using-left-with-a-column"></a>C. 带列使用 LEFT  
 以下示例返回每个产品名中最左边的五个字符。  
  
```  
-- Uses AdventureWorks  
  
SELECT LEFT(EnglishProductName, 5)   
FROM dbo.DimProduct  
ORDER BY ProductKey;  
```  
  
### <a name="d-using-left-with-a-character-string"></a>D. 带字符串使用 LEFT  
 以下示例使用 `LEFT` 函数返回字符串 `abcdefg` 中最左边的两个字符。  
  
```  
-- Uses AdventureWorks  
  
SELECT LEFT('abcdefg',2) FROM dbo.DimProduct;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
--   
ab  
```  
  
## <a name="see-also"></a>另请参阅  
 [LTRIM (Transact-SQL)](../../t-sql/functions/ltrim-transact-sql.md)  
 [RIGHT (Transact-SQL)](../../t-sql/functions/right-transact-sql.md)  
 [RTRIM (Transact-SQL)](../../t-sql/functions/rtrim-transact-sql.md)  
 [STRING_SPLIT (Transact-SQL)](../../t-sql/functions/string-split-transact-sql.md)  
 [SUBSTRING (Transact-SQL)](../../t-sql/functions/substring-transact-sql.md)  
 [TRIM (Transact-SQL)](../../t-sql/functions/trim-transact-sql.md)  
 [CAST 和 CONVERT (Transact-SQL)](../../t-sql/functions/cast-and-convert-transact-sql.md)   
 [数据类型 (Transact-SQL)](../../t-sql/data-types/data-types-transact-sql.md)   
 [字符串函数 (Transact-SQL)](../../t-sql/functions/string-functions-transact-sql.md)  
  
  

