---
title: TRANSLATE (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 02/01/2019
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: conceptual
f1_keywords:
- TRANSLATE
- TRANSLATE_TSQL
helpviewer_keywords:
- TRANSLATE function
ms.assetid: 0426fa90-ef6d-4d19-8207-02ee59f74aec
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
monikerRange: '>=sql-server-2017||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: f2f278b257b1e14f88743a03098949712fa7a873
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "65946671"
---
# <a name="translate-transact-sql"></a>TRANSLATE (Transact-SQL)

[!INCLUDE[tsql-appliesto-ss2017-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2017-asdb-xxxx-xxx-md.md)]

在第二个参数中指定的某些字符转换为第三个参数中指定的字符目标集后，返回作为第一个参数提供的字符串。

## <a name="syntax"></a>语法

```sql
TRANSLATE ( inputString, characters, translations)
```

## <a name="arguments"></a>参数

 inputString  是要搜索的字符串[表达式](../../t-sql/language-elements/expressions-transact-sql.md)。 inputString 可以是任何字符数据类型（nvarchar、varchar、nchar、char）  。

  characters 是一个包含应替换字符的字符串[表达式](../../t-sql/language-elements/expressions-transact-sql.md)。 字符可以是任何字符数据类型  。

 translations 是一个包含替换字符的字符串[表达式](../../t-sql/language-elements/expressions-transact-sql.md)。 转换必须与字符的数据类型和长度相同   。

## <a name="return-types"></a>返回类型

返回与 `inputString`（第二个参数中的字符被替换为第三个参数中的匹配字符）具有相同数据类型的字符表达式。

## <a name="remarks"></a>Remarks

如果字符和转换表达式长度不同，则 `TRANSLATE` 将返回错误   。 如果任何参数为 NULL，`TRANSLATE` 将返回 NULL。  

`TRANSLATE` 函数行为类似于使用多个 [REPLACE](../../t-sql/functions/replace-transact-sql.md) 函数。 但是，`TRANSLATE` 不会多次替换字符。 这不同于多个 `REPLACE` 函数，因为每次使用都会替换所有相关字符。 

`TRANSLATE` 始终可以感知 SC 排序规则。

## <a name="examples"></a>示例

### <a name="a-replace-square-and-curly-braces-with-regular-braces"></a>A. 将方括号和大括号替换为圆括号

以下查询将输入字符串中的方括号和大括号替换为圆括号：

```sql
SELECT TRANSLATE('2*[3+4]/{7-2}', '[]{}', '()()');
```

[!INCLUDE[ssResult_md](../../includes/ssresult-md.md)]

```plain_text
2*(3+4)/(7-2)
```

#### <a name="equivalent-calls-to-replace"></a>与 REPLACE 等效的调用

在以下 SELECT 语句中，有一组对 REPLACE 函数的四个嵌套调用。 此组相当于上述 SELECT 中对 TRANSLATE 函数的一次调用：

```sql
SELECT
REPLACE
(
      REPLACE
      (
            REPLACE
            (
                  REPLACE
                  (
                        '2*[3+4]/{7-2}',
                        '[',
                        '('
                  ),
                  ']',
                  ')'
            ),
            '{',
            '('
      ),
      '}',
      ')'
);
```

### <a name="b-convert-geojson-points-into-wkt"></a>B. 将 GeoJSON 点转换为 WKT

GeoJSON 格式可用于对各种地理数据结构进行编码。 通过 `TRANSLATE` 函数，开发人员可以轻松地将 GeoJSON 点转换为 WKT 格式，反之亦然。 以下查询将输入中的方括号和大括号替换为圆括号：

```sql
SELECT TRANSLATE('[137.4, 72.3]' , '[,]', '( )') AS Point,
    TRANSLATE('(137.4 72.3)' , '( )', '[,]') AS Coordinates;
```

[!INCLUDE[ssResult_md](../../includes/ssresult-md.md)]

|点  |坐标 |  
|---------|--------- |
|(137.4  72.3) |[137.4,72.3] |

### <a name="c-use-the-translate-function"></a>C. 使用 TRANSLATE 函数

```sql
SELECT TRANSLATE('abcdef','abc','bcd') AS Translated,
       REPLACE(REPLACE(REPLACE('abcdef','a','b'),'b','c'),'c','d') AS Replaced;
```

结果有：

| 已转换 | 已替换 |  
| ---------|--------- |
| bcddef | ddddef |


## <a name="see-also"></a>另请参阅

 [CONCAT (Transact-SQL)](../../t-sql/functions/concat-transact-sql.md)  
 [CONCAT_WS (Transact-SQL)](../../t-sql/functions/concat-ws-transact-sql.md)  
 [FORMATMESSAGE (Transact-SQL)](../../t-sql/functions/formatmessage-transact-sql.md)  
 [QUOTENAME (Transact-SQL)](../../t-sql/functions/quotename-transact-sql.md)  
 [REPLACE (Transact-SQL)](../../t-sql/functions/replace-transact-sql.md)  
 [REVERSE (Transact-SQL)](../../t-sql/functions/reverse-transact-sql.md)  
 [STRING_AGG (Transact-SQL)](../../t-sql/functions/string-agg-transact-sql.md)  
 [STRING_ESCAPE (Transact-SQL)](../../t-sql/functions/string-escape-transact-sql.md)  
 [STUFF (Transact-SQL)](../../t-sql/functions/stuff-transact-sql.md)  
 [字符串函数 (Transact-SQL)](../../t-sql/functions/string-functions-transact-sql.md)
