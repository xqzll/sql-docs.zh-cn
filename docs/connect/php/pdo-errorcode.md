---
title: PDO::errorCode | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 5864b1d8-6814-41cd-a88d-415124484c13
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: bd430e026d29d0637e3b9a1543b8a89bed556bd9
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "66798368"
---
# <a name="pdoerrorcode"></a>PDO::errorCode
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

PDO::errorCode 检索数据库句柄上最近操作的 SQLSTATE。  
  
## <a name="syntax"></a>语法  
  
```  
  
mixed PDO::errorCode();  
```  
  
## <a name="return-value"></a>返回值  
如果数据库句柄上没有任何操作，PDO::errorCode 将以字符串或 NULL 形式返回五个字符的 SQLSTATE。  
  
## <a name="remarks"></a>Remarks  
PDO_SQLSRV 驱动程序中的 PDO::errorCode 会针对某些成功操作返回警告。 例如，成功连接时，PDO::errorCode 会返回“01000”，该值指示 SQL_SUCCESS_WITH_INFO。  
  
PDO::errorCode 仅检索直接在数据库连接上执行的操作的错误代码。 如果通过 PDO::prepare 或 PDO::query 创建 PDOStatement 实例，并生成与语句对象有关的错误，PDO::errorCode 不会检索该错误。 必须调用 PDOStatement::errorCode 才可以返回在特定语句对象上执行的操作的错误代码。  
  
已在 [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]的版本 2.0 中添加了对 PDO 的支持。  
  
## <a name="example"></a>示例  
在此示例中，列名拼写不正确（是 `Cityx` 而不是 `City`）导致了错误，随后报告了该错误。  
  
```  
<?php  
$conn = new PDO( "sqlsrv:server=(local) ; Database = AdventureWorks ", "", "");  
$query = "SELECT * FROM Person.Address where Cityx = 'Essen'";  
  
$conn->query($query);  
print $conn->errorCode();  
?>  
```  
  
## <a name="see-also"></a>另请参阅  
[PDO 类](../../connect/php/pdo-class.md)

[PDO](https://php.net/manual/book.pdo.php)  
  
