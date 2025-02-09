---
title: PDO::quote | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: ab9ddc48-42f8-4edf-aa8b-b0fc66706161
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: b08ead32ba3c31f8f928c6e6dda051df1204073c
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "66762022"
---
# <a name="pdoquote"></a>PDO::quote
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

根据基础 SQL Server 数据库的需要，通过用引号将输入字符串括起来处理字符串，以供在查询中使用。 PDO::quote 将使用适用于 SQL Server 的引号样式对输入字符串内的特殊字符进行转义。  
  
## <a name="syntax"></a>语法  
  
```  
  
string PDO::quote( $string[, $parameter_type ] )  
```  
  
#### <a name="parameters"></a>Parameters  
$*string*：要用引号括起来的字符串。  
  
$parameter_type：指示数据类型的可选（整数）符号  。  默认值为 PDO::PARAM_STR。  
  
## <a name="return-value"></a>返回值  
可传递到 SQL 语句的用引号括起来的字符串，或 False（如果失败）。  
  
## <a name="remarks"></a>Remarks  
已在 [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]的版本 2.0 中添加了对 PDO 的支持。  
  
## <a name="example"></a>示例  
  
```  
<?php  
$database = "test";  
$server = "(local)";  
$conn = new PDO( "sqlsrv:server=$server ; Database = $database", "", "");  
  
$param = 'a \' g';  
$param2 = $conn->quote( $param );  
  
$query = "INSERT INTO Table1 VALUES( ?, '1' )";  
$stmt = $conn->prepare( $query );  
$stmt->execute(array($param));  
  
$query = "INSERT INTO Table1 VALUES( ?, ? )";  
$stmt = $conn->prepare( $query );  
$stmt->execute(array($param, $param2));  
?>  
```  
  
## <a name="see-also"></a>另请参阅  
[PDO 类](../../connect/php/pdo-class.md)

[PDO](https://php.net/manual/book.pdo.php)  
  
