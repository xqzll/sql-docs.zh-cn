---
title: PDOStatement::bindParam | Microsoft Docs
ms.custom: ''
ms.date: 05/22/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 65212058-2632-47a4-ba7d-2206883abf09
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: d8186b87e5dde50b07aa69e4dde870d8474265bd
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "66795588"
---
# <a name="pdostatementbindparam"></a>PDOStatement::bindParam
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

将某个参数绑定到 SQL 语句中的命名占位符或问号占位符。  
  
## <a name="syntax"></a>语法  
  
```  
  
bool PDOStatement::bindParam($parameter, &$variable[, $data_type[, $length[, $driver_options]]]);  
```  
  
#### <a name="parameters"></a>Parameters  
$parameter：（混合）参数标识符  。 对于使用命名占位符的语句，使用参数名 (:name)。 对于使用问号语法的已准备的语句，为基于 1 的参数索引。  
  
&$variable：要绑定到 SQL 语句参数的 PHP 变量的（混合）名称  。  
  
$datatype：可选（整数）PDO::PARAM_* 常量  。 默认值为 PDO::PARAM_STR。  
  
$length：数据类型的可选（整数）长度  。 当在 $data_type 中使用 PDO::PARAM_INT 或 PDO::PARAM_BOOL 时，可以指定 PDO::SQLSRV_PARAM_OUT_DEFAULT_SIZE 来指示默认大小  。  
  
$*driver_options*： 可选 （混合） 特定于驱动程序的选项。 例如，你可以指定 PDO::SQLSRV_ENCODING_UTF8 来将列作为使用 UTF-8 编码的字符串绑定到变量。  
  
## <a name="return-value"></a>返回值  
如果成功，则为 TRUE；否则为 FALSE。  
  
## <a name="remarks"></a>Remarks  
在将 null 数据绑定到 varbinary、binary 或 varbinary(max) 类型的服务器列时，应使用 $driver_options 指定二进制编码 (PDO::SQLSRV_ENCODING_BINARY)  。 有关编码常量的详细信息，请参阅[常量](../../connect/php/constants-microsoft-drivers-for-php-for-sql-server.md)。  
  
已在 [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]的版本 2.0 中添加了对 PDO 的支持。  

## <a name="example"></a>示例  
本代码示例演示在将 $contact 绑定到参数后，更改该值会更改在查询中传递的值。  
  
```  
<?php  
$database = "AdventureWorks";  
$server = "(local)";  
$conn = new PDO("sqlsrv:server=$server ; Database = $database", "", "");  
  
$contact = "Sales Agent";  
$stmt = $conn->prepare("select * from Person.ContactType where name = ?");  
$stmt->bindParam(1, $contact);  
$contact = "Owner";  
$stmt->execute();  
  
while ($row = $stmt->fetch(PDO::FETCH_ASSOC)) {  
   print "$row[Name]\n\n";  
}  
  
$stmt = null;  
$contact = "Sales Agent";  
$stmt = $conn->prepare("select * from Person.ContactType where name = :contact");  
$stmt->bindParam(':contact', $contact);  
$contact = "Owner";  
$stmt->execute();  
  
while ($row = $stmt->fetch(PDO::FETCH_ASSOC)) {  
   print "$row[Name]\n\n";  
}  
?>  
```  
  
## <a name="example"></a>示例  
此代码示例演示如何访问输出参数。  
  
```  
<?php  
$database = "Test";  
$server = "(local)";  
$conn = new PDO("sqlsrv:server=$server ; Database = $database", "", "");  
  
$input1 = 'bb';  
  
$stmt = $conn->prepare("select ? = count(*) from Sys.tables");  
$stmt->bindParam(1, $input1, PDO::PARAM_STR, 10);  
$stmt->execute();  
echo $input1;  
?>  
```  
  
> [!NOTE]
> 输出参数绑定到 bigint 类型，如果值的最终可能会超出范围时[整数](../../t-sql/data-types/int-bigint-smallint-and-tinyint-transact-sql.md)，pdo:: PARAM_INT 使用 pdo:: SQLSRV_PARAM_OUT_DEFAULT_SIZE 可能会导致"超出范围的值"异常。 因此，改为使用默认 pdo:: PARAM_STR 并提供生成的字符串，最多为 21 的大小。 它是最大位数，包括任何 bigint 值的负号。 

## <a name="example"></a>示例  
此代码示例演示如何使用输入/输出参数。  
  
```  
<?php  
   $database = "AdventureWorks";  
   $server = "(local)";  
   $dbh = new PDO("sqlsrv:server=$server ; Database = $database", "", "");  
  
   $dbh->query("IF OBJECT_ID('dbo.sp_ReverseString', 'P') IS NOT NULL DROP PROCEDURE dbo.sp_ReverseString");  
   $dbh->query("CREATE PROCEDURE dbo.sp_ReverseString @String as VARCHAR(2048) OUTPUT as SELECT @String = REVERSE(@String)");  
   $stmt = $dbh->prepare("EXEC dbo.sp_ReverseString ?");  
   $string = "123456789";  
   $stmt->bindParam(1, $string, PDO::PARAM_STR | PDO::PARAM_INPUT_OUTPUT, 2048);  
   $stmt->execute();  
   print $string;   // Expect 987654321  
?>  
```  

> [!NOTE]
> 当由于 PHP 的[浮点数](https://php.net/manual/en/language.types.float.php)具有有限精确度而将值绑定到[十进制或数值列](../../t-sql/data-types/decimal-and-numeric-transact-sql.md)以确保精确度和准确度时，建议将字符串用作输入。 这同样适用于 bigint 列，尤其是在值超出[整数](../../t-sql/data-types/int-bigint-smallint-and-tinyint-transact-sql.md)范围的情况下。

## <a name="example"></a>示例  
此代码示例演示如何将十进制值作为输入参数进行绑定。  

```
<?php  
$database = "Test";  
$server = "(local)";  
$conn = new PDO("sqlsrv:server=$server ; Database = $database", "", "");  

// Assume TestTable exists with a decimal field 
$input = 9223372036854.80000;
$stmt = $conn->prepare("INSERT INTO TestTable (DecimalCol) VALUES (?)");
// by default it is PDO::PARAM_STR, rounding of a large input value may
// occur if PDO::PARAM_INT is specified
$stmt->bindParam(1, $input, PDO::PARAM_STR);
$stmt->execute();
```


## <a name="see-also"></a>另请参阅  
[PDOStatement 类](../../connect/php/pdostatement-class.md)

[PDO](https://php.net/manual/book.pdo.php)  
  
