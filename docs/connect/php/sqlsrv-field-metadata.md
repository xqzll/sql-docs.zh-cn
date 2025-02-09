---
title: sqlsrv_field_metadata | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- sqlsrv_field_metadata
apitype: NA
helpviewer_keywords:
- API Reference, sqlsrv_field_metadata
- sqlsrv_field_metadata
ms.assetid: c02f6942-0484-4567-a78e-fe8aa2053536
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 5a582a95223fd47863a6e42b8426ccfb13fcda59
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "66796082"
---
# <a name="sqlsrvfieldmetadata"></a>sqlsrv_field_metadata
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

检索已准备语句的字段的元数据。 有关准备语句的信息，请参阅 [sqlsrv_query](../../connect/php/sqlsrv-query.md) 或 [sqlsrv_prepare](../../connect/php/sqlsrv-prepare.md)。 请注意，无论在执行前还是执行后，都可以在任何已准备的语句上调用 sqlsrv_field_metadata  。  
  
## <a name="syntax"></a>语法  
  
```  
  
sqlsrv_field_metadata( resource $stmt)  
```  
  
#### <a name="parameters"></a>Parameters  
*$stmt*：寻找字段元数据的语句资源。  
  
## <a name="return-value"></a>返回值  
数组的 **array** 或 **false**。 数组由结果集中的每个字段的一个数组组成。 每个子数组具有下表中所述的键。 如果在检索字段元数据时出现错误，则返回 **false** 。  
  
|Key|描述|  
|-------|---------------|  
|“属性”|字段对应的列的名称。|  
|类型|对应于 SQL 类型的数值。|  
|Size|字符类型（char(n)、varchar(n)、nchar(n)、nvarchar(n)、XML）的字段的字符数。 二进制类型（binary(n)、varbinary(n)、UDT）的字段的字节数。 **NULL** 用于其他 SQL Server 数据类型。|  
|精度|变量精度类型（real、numeric、decimal、datetime2、datetimeoffset 和 time）的精度。 **NULL** 用于其他 SQL Server 数据类型。|  
|小数位数|变量小数位数类型（numeric、decimal、datetime2、datetimeoffset 和 time）的小数位数。 **NULL** 用于其他 SQL Server 数据类型。|  
|可以为 Null|指示列可以为 null (SQLSRV_NULLABLE_YES)、不可为 null (SQLSRV_NULLABLE_NO) 还是未知列是否可以为 null (SQLSRV_NULLABLE_UNKNOWN) 的枚举值    。|  
  
下表提供有关每个子数组的键的详细信息（有关这些类型的详细信息，请参阅 SQL Server 文档）：  
  
|SQL Server 2008 数据类型|类型|最小/最大精度|最小/最大小数位数|Size|  
|-----------------------------|--------|----------------------|------------------|--------|  
|BIGINT|SQL_BIGINT (-5)|||8|  
|BINARY|SQL_BINARY (-2)||| 0 < n < 8000 <sup>1</sup>|  
|bit|SQL_BIT (-7)||||  
|char|SQL_CHAR (1)||| 0 < n < 8000 <sup>1</sup>|  
|日期|SQL_TYPE_DATE (91)|10/10|0/0||  
|DATETIME|SQL_TYPE_TIMESTAMP (93)|23/23|3/3||  
|datetime2|SQL_TYPE_TIMESTAMP (93)|19/27|0/7||  
|datetimeoffset|SQL_SS_TIMESTAMPOFFSET (-155)|26/34|0/7||  
|Decimal|SQL_DECIMAL (3)|1/38|0/精度值||  
|FLOAT|SQL_FLOAT (6)|4/8|||  
|图像|SQL_LONGVARBINARY (-4)|||2 GB|  
|ssNoversion|SQL_INTEGER (4)||||  
|money|SQL_DECIMAL (3)|19/19|4/4||  
|NCHAR|SQL_WCHAR (-8)||| 0 < n < 4000 <sup>1</sup>|  
|ntext|SQL_WLONGVARCHAR (-10)|||1 GB|  
|NUMERIC|SQL_NUMERIC (2)|1/38|0/精度值||  
|NVARCHAR|SQL_WVARCHAR (-9)||| 0 < n < 4000 <sup>1</sup>|  
|REAL|SQL_REAL (7)|4/4|||  
|smalldatetime|SQL_TYPE_TIMESTAMP (93)|16/16|0/0||  
|SMALLINT|SQL_SMALLINT (5)|||2 字节|  
|Smallmoney|SQL_DECIMAL (3)|10/10|4/4||  
|text|SQL_LONGVARCHAR (-1)|||2 GB|  
|time|SQL_SS_TIME2 (-154)|8/16|0/7||  
|TIMESTAMP|SQL_BINARY (-2)|||8 字节|  
|TINYINT|SQL_TINYINT (-6)|||1 字节|  
|udt|SQL_SS_UDT (-151)|||变量|  
|UNIQUEIDENTIFIER|SQL_GUID (-11)|||16|  
|varbinary|SQL_VARBINARY (-3)||| 0 < n < 8000 <sup>1</sup>|  
|varchar|SQL_VARCHAR (12)||| 0 < n < 8000 <sup>1</sup>|  
|xml|SQL_SS_XML (-152)|||0|  
  
(1) 零 (0) 指示允许最大大小。  
  
可以为 Null 的键可能为是或否。  
  
## <a name="example"></a>示例  
以下示例创建语句资源，然后检索并显示字段元数据。 该示例假定已在本地计算机上安装了 SQL Server 和 [AdventureWorks](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/adventure-works) 数据库。 从命令行运行该示例时，所有输出都将写入控制台。  
  
```  
<?php  
/* Connect to the local server using Windows Authentication and  
specify the AdventureWorks database as the database in use. */  
$serverName = "(local)";  
$connectionInfo = array( "Database"=>"AdventureWorks");  
$conn = sqlsrv_connect( $serverName, $connectionInfo);  
if( $conn === false )  
{  
     echo "Could not connect.\n";  
     die( print_r( sqlsrv_errors(), true));  
}  
  
/* Prepare the statement. */  
$tsql = "SELECT ReviewerName, Comments FROM Production.ProductReview";  
$stmt = sqlsrv_prepare( $conn, $tsql);  
  
/* Get and display field metadata. */  
foreach( sqlsrv_field_metadata( $stmt) as $fieldMetadata)  
{  
      foreach( $fieldMetadata as $name => $value)  
      {  
           echo "$name: $value\n";  
      }  
      echo "\n";  
}  
  
/* Note: sqlsrv_field_metadata can be called on any statement  
resource, pre- or post-execution. */  
  
/* Free statement and connection resources. */  
sqlsrv_free_stmt( $stmt);  
sqlsrv_close( $conn);  
?>  
```  
  
## <a name="see-also"></a>另请参阅  
[SQLSRV 驱动程序 API 参考](../../connect/php/sqlsrv-driver-api-reference.md)  

[常量（Microsoft Drivers for PHP for SQL Server）](../../connect/php/constants-microsoft-drivers-for-php-for-sql-server.md)  

[文档中相关的代码示例](../../connect/php/about-code-examples-in-the-documentation.md)  
  
