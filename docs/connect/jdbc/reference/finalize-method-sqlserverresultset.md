---
title: finalize 方法 (SQLServerResultSet) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.finalize
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 49bc879d-822b-42da-bc20-2394865f1f0f
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 854da2b16cf680ac6ce54ae44a4bf1296cdbfd2c
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "66796862"
---
# <a name="finalize-method-sqlserverresultset"></a>finalize 方法 (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  显式关闭此 [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) 对象。  
  
## <a name="syntax"></a>语法  
  
```  
  
public void finalize()  
```  
  
## <a name="remarks"></a>Remarks  
 如果应用程序未关闭结果集，则关闭它。 提供此方法只是为了符合 JDBC 规范。 由于 Java 虚拟机 (JVM) 不保证何时可以运行终结器，因此忽略显式关闭其结果集的应用程序对于正在使用同一连接并因为公共服务器资源（如行锁）而阻塞的另一语句可能造成死锁。  
  
## <a name="see-also"></a>另请参阅  
 [SQLServerResultSet 成员](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet 类](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
