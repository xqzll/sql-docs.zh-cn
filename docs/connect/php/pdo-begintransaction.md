---
title: PDO::beginTransaction | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 4d5db438-9df7-4d22-9907-3ddc63bd2220
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 9399e903db0806778dffc192b3bd512514d71b07
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "66768114"
---
# <a name="pdobegintransaction"></a>PDO::beginTransaction
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

关闭自动提交模式，然后开始某个事务。  
  
## <a name="syntax"></a>语法  
  
```  
  
bool PDO::beginTransaction();  
```  
  
## <a name="return-value"></a>返回值  
如果方法调用成功，则为 True；否则为 False。  
  
## <a name="remarks"></a>Remarks  
调用 [PDO::commit](../../connect/php/pdo-commit.md) 或 [PDO::rollback](../../connect/php/pdo-rollback.md) 时，将结束使用 PDO::beginTransaction 开始的事务。  
  
PDO::beginTransaction 不受 PDO::ATTR_AUTOCOMMIT 的值影响（也不影响该值）。  
  
除非先使用 PDO::rollback 或 PDO::commit 结束之前的 PDO::beginTransaction，否则不允许调用 PDO::beginTransaction。  
  
如果此方法失败，该连接会返回到自动提交模式。  
  
已在 [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]的版本 2.0 中添加了对 PDO 的支持。  
  
## <a name="example"></a>示例  
以下示例使用名为 Test 的数据库和名为 Table1 的表。 它将启动某个事务，然后发出命令，以便添加两行并随后删除一行。 将这些命令发送到该数据库，并且使用 `PDO::commit`显式结束该事务。  
  
```  
<?php  
   $conn = new PDO( "sqlsrv:server=(local); Database = Test", "", "");  
   $conn->beginTransaction();  
   $ret = $conn->exec("insert into Table1(col1, col2) values('a', 'b') ");  
   $ret = $conn->exec("insert into Table1(col1, col2) values('a', 'c') ");  
   $ret = $conn->exec("delete from Table1 where col1 = 'a' and col2 = 'b'");  
   $conn->commit();  
   // $conn->rollback();  
   echo $ret;  
?>  
```  
  
## <a name="see-also"></a>另请参阅  
[PDO 类](../../connect/php/pdo-class.md)

[PDO](https://php.net/manual/book.pdo.php)  
  
