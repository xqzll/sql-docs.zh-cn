---
title: next 方法 (SQLServerResultSet) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.next
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 60248447-6908-4036-a779-a501453cd553
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 8fcd3125f45622ddd167acf06ed91ccffb02a3b5
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "66779528"
---
# <a name="next-method-sqlserverresultset"></a>next 方法 (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  将游标从当前位置下移一行。  
  
## <a name="syntax"></a>语法  
  
```  
  
public boolean next()  
```  
  
## <a name="return-value"></a>返回值  
 **true**新的当前行是否有效。 **false**如果没有要处理的多个行。  
  
## <a name="exceptions"></a>异常  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 此 next 方法是由 java.sql.ResultSet 接口中的 next 方法指定的。  
  
 结果集游标最初位于第一行之前。 第一次调用 next 方法让第一行成为当前行，第二次调用让第二行成为当前行，以此类推。  
  
 如果输入流对当前行是打开的，调用 next 方法会隐式关闭它。 [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) 对象的警告链会在新行被读取时清除。  
  
## <a name="see-also"></a>另请参阅  
 [SQLServerResultSet 成员](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet 类](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
