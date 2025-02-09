---
title: ~（位非）(Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 01/10/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- ~_TSQL
- bitwise
- NOT
- "~"
- Bitwise NOT
dev_langs:
- TSQL
helpviewer_keywords:
- NOT keyword
- bitwise NOT (~)
- ~ (bitwise NOT)
ms.assetid: 02da8016-f6c0-41ae-8d59-33eaa02bfc95
author: rothja
ms.author: jroth
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 5957410faa3bcc2870712e01857216c2ef526008
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "65981320"
---
# <a name="-bitwise-not-transact-sql"></a>~（位非）(Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  对整数值执行逻辑位非运算。  
  
 ![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "主题链接图标") [TRANSACT-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>语法  
  
```  
~ expression  
```  
  
## <a name="arguments"></a>参数  
 *expression*  
 整数数据类型类别中的任何一种数据类型、bit、binary 或 varbinary 数据类型的任何有效的[表达式](../../t-sql/language-elements/expressions-transact-sql.md)    。 对于位运算，expression 被视为二进制数字  。  
  
> [!NOTE]  
>  位运算中，只有一个 expression 可以是 binary 或 varbinary 数据类型    。  
  
## <a name="result-types"></a>结果类型  
 如果输入值为 int，则结果为 int   。  
  
 如果输入值为 smallint，则结果为 smallint   。  
  
 如果输入值为 tinyint，则结果为 tinyint   。  
  
 如果输入值为 bit，则结果为 bit   。  
  
## <a name="remarks"></a>Remarks  
 ~ 位运算符对 expression 逐位执行逻辑位非运算   。 如果 expression 的值为 0，则结果集中的位将设置为 1；否则，结果中的位将清 0  。 换句话说，1 改成 0，而 0 则改成 1。  
  
> [!IMPORTANT]  
>  执行任何种类的位运算时，位运算中使用的表达式的存储长度都是很重要的。 建议您在存储值时使用该相同的字节数。 例如，如果将十进制值 5 作为 tinyint、smallint 或 int 进行存储，所生成的值将以不同字节数进行存储：tinyint 使用 1 个字节存储数据；smallint 使用 2 个字节存储数据；而 int 则使用 4 个字节存储数据       。 因此，对 int 十进制值执行位运算所生成的结果与那些使用直接二进制或十六进制转换的结果不同，尤其是使用 ~（位非）运算符时   。 位非运算可能针对长度较短的变量执行。 这种情况下，当长度较短的变量转换为较长的数据类型变量时，上 8 位中的位将不能设置为期望的值。 我们建议先将较小的数据类型变量转换为较大的数据类型，然后对结果执行非运算。  
  
## <a name="examples"></a>示例  
 以下示例将使用 int 数据类型创建一个表，用于存储值，并将两个值插入到一行中  。  
  
```  
CREATE TABLE bitwise  
(   
a_int_value int NOT NULL,  
b_int_value int NOT NULL  
);  
GO  
INSERT bitwise VALUES (170, 75);  
GO  
```  
  
 以下查询对 `a_int_value` 和 `b_int_value` 列执行位非运算。  
  
```  
SELECT ~ a_int_value, ~ b_int_value  
FROM bitwise;  
```  
  
 下面是结果集：  
  
```  
--- ---   
-171  -76   
  
(1 row(s) affected)  
```  
  
 170（`a_int_value` 或 `A`）的二进制表示形式是 `0000 0000 1010 1010`。 对这个值执行“位非”运算将产生二进制结果 `1111 1111 0101 0101`，即十进制数 -171。 75 的二进制表示形式是 `0000 0000 0100 1011`。 执行位非运算将生成 `1111 1111 1011 0100`，该结果等于十进制 -76。  
  
```  
 (~A)     
         0000 0000 1010 1010  
         -------------------  
         1111 1111 0101 0101  
(~B)     
         0000 0000 0100 1011  
         -------------------  
         1111 1111 1011 0100  
```  
  
 
## <a name="see-also"></a>另请参阅  
 [表达式 (Transact-SQL)](../../t-sql/language-elements/expressions-transact-sql.md)   
 [运算符 (Transact-SQL)](../../t-sql/language-elements/operators-transact-sql.md)   
 [位运算符 (Transact-SQL)](../../t-sql/language-elements/bitwise-operators-transact-sql.md)  
  
  


