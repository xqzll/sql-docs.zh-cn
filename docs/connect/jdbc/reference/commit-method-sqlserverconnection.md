---
title: commit 方法 (SQLServerConnection) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerConnection.commit
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: c7346165-51bf-4844-b64c-29833c147236
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: dafb8b3c5016d0be191e06eefb5b5ca80b9ec0de
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 06/07/2019
ms.locfileid: "66777390"
---
# <a name="commit-method-sqlserverconnection"></a>commit 方法 (SQLServerConnection)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  让自上次提交或回滚后的所有更改都成为永久性更改，并释放当前由此 [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) 对象保留的任何数据库锁。  
  
## <a name="syntax"></a>语法  
  
```  
  
public void commit()  
```  
  
## <a name="exceptions"></a>异常  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 此 commit 方法是由 java.sql.Connection 接口中的 commit 方法指定的。  
  
 仅当已禁用自动提交模式时才应使用此方法。  
  
 请注意，如果客户端启动了手动事务，随后出于某种原因 SQL Server 回滚了该手动事务，此时此方法将失败并引发异常。 例如，如果客户端先调用显式调用 ROLLBACK TRANSACTION 的存储过程，再调用 commit 方法，便会导致异常。 此外，如果 SQL Server 引发了足够严重（16 或更高级别）的错误导致回滚客户端启动的手动事务，随后调用 commit 方法也会抛出异常。  
  
## <a name="see-also"></a>另请参阅  
 [SQLServerConnection 成员](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection 类](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
