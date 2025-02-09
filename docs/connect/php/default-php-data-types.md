---
title: 默认 PHP 数据类型 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- default data types
- converting data types
ms.assetid: b66c301d-3d20-45b8-a112-225d8f01c0bd
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 01f611e0c11d6a2f3671c8911d41b4c0cfeef83c
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "66801483"
---
# <a name="default-php-data-types"></a>默认 PHP 数据类型
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

在从服务器检索数据时，如果用户未指定任何 PHP 数据类型， [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] 会将数据转换为默认 PHP 数据类型。  
  
当使用 PDO_SQLSRV 驱动程序返回数据时，数据类型将是 int 或 string。  
  
本主题的其余部分讨论使用 SQLSRV 驱动程序的默认数据类型。  
  
下表列出了 SQL Server 数据类型（从服务器检索的数据类型）、默认 PHP 数据类型（数据转换到的数据类型）以及流和字符串的默认编码。 有关如何在从服务器检索数据时指定数据类型的详细信息，请参阅 [How to: Specify PHP Data Types](../../connect/php/how-to-specify-php-data-types.md)。  
  
|SQL Server 类型|默认 PHP 类型|默认编码|  
|-------------------|--------------------|--------------------|  
|BIGINT|String|8 位字符<sup>1</sup>|  
|BINARY|Stream<sup>2</sup>|Binary<sup>3</sup>|  
|bit|Integer|8 位字符<sup>1</sup>|  
|char|String|8 位字符<sup>1</sup>|  
|date<sup>4</sup>|DATETIME|不适用|  
|datetime<sup>4</sup>|DATETIME|不适用|  
|datetime2<sup>4</sup>|DATETIME|不适用|  
|datetimeoffset<sup>4</sup>|DATETIME|不适用|  
|Decimal|String|8 位字符<sup>1</sup>|  
|FLOAT|float|8 位字符<sup>1</sup>|  
|地理|Stream|Binary<sup>3</sup>|  
|geometry|Stream|Binary<sup>3</sup>|  
|image<sup>5</sup>|Stream<sup>2</sup>|Binary<sup>3</sup>|  
|ssNoversion|Integer|8 位字符<sup>1</sup>|  
|money|String|8 位字符<sup>1</sup>|  
|NCHAR|String|8 位字符<sup>1</sup>|  
|NUMERIC|String|8 位字符<sup>1</sup>|  
|NVARCHAR|String|8 位字符<sup>1</sup>|  
|nvarchar(MAX)|Stream<sup>2</sup>|8 位字符<sup>1</sup>|  
|ntext<sup>6</sup>|Stream<sup>2</sup>|8 位字符<sup>1</sup>|  
|REAL|float|8 位字符<sup>1</sup>|  
|smalldatetime|DATETIME|8 位字符<sup>1</sup>|  
|SMALLINT|Integer|8 位字符<sup>1</sup>|  
|SMALLMONEY|String|8 位字符<sup>1</sup>|  
|sql_variant<sup>7</sup>|String|8 位字符<sup>1</sup>|  
|text<sup>8</sup>|Stream<sup>2</sup>|8 位字符<sup>1</sup>|  
|time<sup>4</sup>|DATETIME|不适用|  
|TIMESTAMP|String|8 位字符<sup>1</sup>|  
|TINYINT|Integer|8 位字符<sup>1</sup>|  
|UDT|Stream<sup>2</sup>|Binary<sup>3</sup>|  
|UNIQUEIDENTIFIER|字符串<sup>9</sup>|8 位字符<sup>1</sup>|  
|varbinary|Stream<sup>2</sup>|Binary<sup>3</sup>|  
|varbinary(MAX)|Stream<sup>2</sup>|Binary<sup>3</sup>|  
|varchar|String|8 位字符<sup>1</sup>|  
|varchar(MAX)|Stream<sup>2</sup>|8 位字符<sup>1</sup>|
|xml|Stream<sup>2</sup>|8 位字符<sup>1</sup>|  
  

1.  数据以在系统上设置的 Windows 区域设置的代码页中指定的 8 位字符的形式返回。 任何多字节字符或未映射到此代码页中的字符都会替换为单字节问号 (?) 字符。  
  
2.  如果 [sqlsrv_fetch_array](../../connect/php/sqlsrv-fetch-array.md) 或 [sqlsrv_fetch_object](../../connect/php/sqlsrv-fetch-object.md) 用于检索具有默认 PHP 类型 Stream 的字符串的数据，该数据将返回为具有与流相同的编码的字符串。 例如，如果 SQL Server 二进制类型使用 sqlsrv_fetch_array进行检索，默认返回类型将是二进制字符串  。  
  
3.  数据以原始字节流的形式从服务器返回，无需执行编码或转换。  

4.  日期和时间类型可以字符串的形式检索。 有关详细信息，请参阅 [如何：使用 SQLSRV 驱动程序以字符串的形式检索日期和时间类型](../../connect/php/how-to-retrieve-date-and-time-type-as-strings-using-the-sqlsrv-driver.md)。  

5.  这是映射到 varbinary(max) 类型的旧类型。

6. 这是映射到 nvarchar(max) 类型的旧类型。

7.  双向或输出参数中不支持 sql_variant。

8.  这是映射到 varchar(max) 类型的旧类型。  
  
9.  UNIQUEIDENTIFIER 是由以下正则表达式表示的 GUID：  
  
    [0-9a-fA-F]{8}-[0-9a-fA-F]{4}-[0-9a-fA-f]{4}-[0-9a-fA-f]{4}-[0-9a-fA-F]{12}  
 
 
## <a name="other-new-sql-server-2008-data-types-and-features"></a>其他 New SQL Server 2008 数据类型和功能  
SQL Server 2008 中新增的和存在于列外（如表值参数）的数据类型在 [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)] 中不受支持。 下表总结了对新的 SQL Server 2008 功能的 PHP 支持。  
  
|功能|PHP 支持|  
|-----------|---------------|  
|表值参数|否|  
|稀疏列|Partial|  
|Null 位压缩|是|  
|大型 CLR 用户定义的类型 (UDT)|是|  
|服务主体名称|否|  
|MERGE|是|  
|FILESTREAM|Partial|  
  
部分类型支持意味着你无法以编程方式查询列的类型。  
  
## <a name="see-also"></a>另请参阅  
[常量（Microsoft Drivers for PHP for SQL Server）](../../connect/php/constants-microsoft-drivers-for-php-for-sql-server.md)

[Converting Data Types](../../connect/php/converting-data-types.md)

[PHP 类型](https://php.net/manual/en/language.types.php)

[数据类型 (Transact-SQL)](../../t-sql/data-types/data-types-transact-sql.md)

[sqlsrv_field_metadata](../../connect/php/sqlsrv-field-metadata.md)  
  
