---
title: setSavepoint 方法 （) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerConnection.setSavepoint ()
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 11013055-4fd3-45a9-b2da-28b2908dad52
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: bf2c9920545d4d17bb8df6979410d849c125e20c
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 06/07/2019
ms.locfileid: "66796734"
---
# <a name="setsavepoint-method-"></a>setSavepoint 方法 ()
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  在当前事务中创建未命名的保存点，并返回代表它的新 [SQLServerSavepoint](../../../connect/jdbc/reference/sqlserversavepoint-class.md) 对象。  
  
## <a name="syntax"></a>语法  
  
```  
  
public java.sql.Savepoint setSavepoint()  
```  
  
## <a name="return-value"></a>返回值  
 一个保存点的对象。  
  
## <a name="exceptions"></a>异常  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 此 setSavePoint 方法由 java.sql.Connection 接口中的 setSavePoint 方法指定。  
  
## <a name="see-also"></a>另请参阅  
 [setSavepoint 方法 &#40;SQLServerConnection&#41;](../../../connect/jdbc/reference/setsavepoint-method-sqlserverconnection.md)   
 [SQLServerConnection 成员](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection 类](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
