---
title: PDOStatement::getColumnMeta | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: c92a21cc-8e53-43d0-a4bf-542c77c100c9
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 57bc8d1e6112a64f99864ce08f7adb81db6df781
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "66799116"
---
# <a name="pdostatementgetcolumnmeta"></a>PDOStatement::getColumnMeta
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

检索列的元数据。  
  
## <a name="syntax"></a>语法  
  
```  
  
array PDOStatement::getColumnMeta ( $column );  
```  
  
#### <a name="parameters"></a>Parameters  
 $conn：（整数）要检索其元数据的列的从零开始的数。  
  
## <a name="return-value"></a>返回值  
包含列的元数据的关联阵列（键和值）。 有关数组中的字段的说明，请参阅“备注”部分。  
  
## <a name="remarks"></a>Remarks  
下表介绍 getColumnMeta 返回的数组中的字段。  
  
|NAME|VALUES|  
|--------|----------|  
|native_type|指定列的 PHP 类型。 始终为字符串。|  
|driver:decl_type|指定用于表示数据库中的列值的 SQL 类型。 如果结果集中的列是函数的结果，则 PDOStatement::getColumnMeta 不会返回此值。|  
|flags|指定为此列设置的标志。 始终为 0。|  
|NAME|指定数据库中的列的名称。|  
|表|指定包含数据库中的列的表格名称。 始终为空白。|  
|len|指定列长度。|  
|精度|指定此列的数值精度。|  
|pdo_type|指定此列的类型，由 PDO::PARAM_* 常量表示。 Always PDO::PARAM_STR (2)。|  
  
已在 [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]的版本 2.0 中添加了对 PDO 的支持。  
  
## <a name="example"></a>示例  
  
```  
<?php  
$database = "AdventureWorks";  
$server = "(local)";  
$conn = new PDO( "sqlsrv:server=$server ; Database = $database", "", "");  
  
$stmt = $conn->query("select * from Person.ContactType");  
$metadata = $stmt->getColumnMeta(2);  
var_dump($metadata);  
  
print $metadata['sqlsrv:decl_type'] . "\n";  
print $metadata['native_type'] . "\n";  
print $metadata['name'];  
?>  
```  
  
## <a name="see-also"></a>另请参阅  
[PDOStatement 类](../../connect/php/pdostatement-class.md)

[PDO](https://php.net/manual/book.pdo.php)  
  
