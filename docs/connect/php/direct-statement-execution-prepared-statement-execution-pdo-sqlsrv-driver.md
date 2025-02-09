---
title: 指示语句的准备语句执行 PDO_SQLSRV 驱动程序 |Microsoft Docs
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 05544ca6-1e07-486c-bf03-e8c2c25b3024
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 96a03a678152c523cdb16b77834863ff920586c8
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 06/07/2019
ms.locfileid: "66801448"
---
# <a name="direct-statement-execution-and-prepared-statement-execution-in-the-pdosqlsrv-driver"></a>PDO_SQLSRV 驱动程序中的直接语句执行和预定语句执行
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

本主题讨论如何使用 PDO::SQLSRV_ATTR_DIRECT_QUERY 属性指定直接语句执行而非默认执行，即已准备的语句执行。 如果使用参数绑定多次执行语句，则将使用已准备的语句可以生成更好的性能。  
  
## <a name="remarks"></a>Remarks  
如果你想要发送[!INCLUDE[tsql](../../includes/tsql-md.md)]直接向服务器而无需由驱动程序的语句准备的语句，可以设置具有的 pdo:: SQLSRV_ATTR_DIRECT_QUERY 属性[pdo:: setattribute](../../connect/php/pdo-setattribute.md) （或驱动程序选项传递给[:: __Construct](../../connect/php/pdo-construct.md)) 或当您调用[pdo:: prepare](../../connect/php/pdo-prepare.md)。 默认情况下，pdo:: SQLSRV_ATTR_DIRECT_QUERY 的值为 False （准备的语句执行时使用）。  
  
如果您使用[pdo:: query](../../connect/php/pdo-query.md)，您可能希望直接执行。 然后再调用[pdo:: query](../../connect/php/pdo-query.md)，调用[pdo:: setattribute](../../connect/php/pdo-setattribute.md) ，pdo:: SQLSRV_ATTR_DIRECT_QUERY 设置为 True。  每次调用[pdo:: query](../../connect/php/pdo-query.md)可以具有不同设置为 pdo:: SQLSRV_ATTR_DIRECT_QUERY 执行。  
  
如果您使用[pdo:: prepare](../../connect/php/pdo-prepare.md)并[pdostatement:: Execute](../../connect/php/pdostatement-execute.md)多次执行一个查询使用绑定的参数，准备的语句执行优化的重复查询的执行。  在这种情况下，调用[pdo:: prepare](../../connect/php/pdo-prepare.md)使用 pdo:: SQLSRV_ATTR_DIRECT_QUERY 驱动程序选项数组参数中设置为 False。 如有必要，可以执行已准备的语句，pdo:: SQLSRV_ATTR_DIRECT_QUERY 设置为 False。  
  
调用后[pdo:: prepare](../../connect/php/pdo-prepare.md)，pdo:: SQLSRV_ATTR_DIRECT_QUERY 的值不能更改时执行已准备好的查询。  
  
如果查询需要在前面的查询中设置了上下文，则执行您的查询使用 pdo:: SQLSRV_ATTR_DIRECT_QUERY 设置为 True。 例如，如果您在查询中使用临时表，pdo:: SQLSRV_ATTR_DIRECT_QUERY 必须设置为 True。  
  
下面的示例显示了需要从上一个语句的上下文时，您需要将 pdo:: SQLSRV_ATTR_DIRECT_QUERY 设置为 True。 此示例使用临时表，直接执行查询时才可用于在程序中的后续语句。  
  
> [!NOTE]
> 如果查询是调用存储的过程，并且使用在此存储过程中，使用临时表[pdo:: exec](../../connect/php/pdo-exec.md)相反。

```  
<?php  
   $conn = new PDO('sqlsrv:Server=(local)', '', '');  
   $conn->setAttribute(constant('PDO::SQLSRV_ATTR_DIRECT_QUERY'), true);  
  
   $stmt1 = $conn->query("DROP TABLE #php_test_table");  
  
   $stmt2 = $conn->query("CREATE TABLE #php_test_table ([c1_int] int, [c2_int] int)");  
  
   $v1 = 1;  
   $v2 = 2;  
  
   $stmt3 = $conn->prepare("INSERT INTO #php_test_table (c1_int, c2_int) VALUES (:var1, :var2)");  
  
   if ($stmt3) {  
      $stmt3->bindValue(1, $v1);  
      $stmt3->bindValue(2, $v2);  
  
      if ($stmt3->execute())  
         echo "Execution succeeded\n";       
      else  
         echo "Execution failed\n";  
   }  
   else  
      var_dump($conn->errorInfo());  
  
   $stmt4 = $conn->query("DROP TABLE #php_test_table");  
?>  
```  
  
## <a name="see-also"></a>另请参阅  
[适用于 SQL Server for PHP 编程 Microsoft 驱动程序的指南](../../connect/php/programming-guide-for-php-sql-driver.md)
  
