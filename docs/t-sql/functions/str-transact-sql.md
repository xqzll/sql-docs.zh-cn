---
title: STR (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STR
- STR_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- converting numbers to characters
- characters [SQL Server], converting
- character data [SQL Server]
- STR function
ms.assetid: de03531b-d9e7-4c3c-9604-14e582ac20c6
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: c52996b890529504c304aae2bf1dc41c3a3f4b4b
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "65947571"
---
# <a name="str-transact-sql"></a>STR (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  返回由数字数据转换来的字符数据。  
  
 ![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "主题链接图标") [TRANSACT-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>语法  
  
```  
STR ( float_expression [ , length [ , decimal ] ] )  
```  
  
## <a name="arguments"></a>参数  
 *float_expression*  
 带小数点的近似数字 (float) 数据类型的表达式  。  
  
 *length*  
 总长度。 它包括小数点、符号、数字以及空格。 默认值为 10。  
  
 *decimal*  
 小数点后的位数。 decimal 必须小于或等于 16  。 如果 decimal 大于 16，则将结果截断为小数点右边的 16 位  。  
  
## <a name="return-types"></a>返回类型  
 **varchar**  
  
## <a name="remarks"></a>Remarks  
 如果提供，则 STR 的 length 和 decimal 参数值应该是正数   。 在默认情况下或小数参数为 0 时，数字舍入为整数。 指定的长度应大于或等于小数点前面的部分加上数字符号（如果有）的长度。 短的 float_expression 在指定长度内右对齐，长的 float_expression 则截断为指定的小数位数   。 例如，STR(12,10) 生成结果 12  。 这在结果集中右对齐。 而 STR(1223,2) 则将结果集截断为 **  。 可以嵌套字符串函数。  
  
> [!NOTE]  
>  若要转换为 Unicode 数据，请在 CONVERT 或 [CAST](../../t-sql/functions/cast-and-convert-transact-sql.md) 转换函数内使用 STR。  
  
## <a name="examples"></a>示例  
 以下示例将由五个数字和一个小数点组成的表达式转换为有六个位置的字符串。 数字的小数部分舍入为一个小数位。  
  
```  
SELECT STR(123.45, 6, 1);  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
------  
 123.5  
  
(1 row(s) affected)  
```  
  
 当表达式超出指定长度时，字符串为指定长度返回 `**`。  
  
```  
SELECT STR(123.45, 2, 2);  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
--  
**  
  
(1 row(s) affected)  
```  
  
 即使数字数据嵌套在 `STR` 内，结果也是带指定格式的字符数据。  
  
```  
SELECT STR (FLOOR (123.45), 8, 3);
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
--------  
 123.000  
  
(1 row(s) affected)  
```  
  
## <a name="see-also"></a>另请参阅  
 [CAST 和 CONVERT (Transact-SQL)](../../t-sql/functions/cast-and-convert-transact-sql.md)  
 [FORMAT (Transact-SQL)](../../t-sql/functions/format-transact-sql.md)  
 [字符串函数 (Transact-SQL)](../../t-sql/functions/string-functions-transact-sql.md)  
  
  

