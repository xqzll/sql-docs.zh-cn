---
title: updateBytes 方法 (SQLServerResultSet) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.updateBytes
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 3050c836-fbb3-4475-99e5-05637a48a932
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: f63a21b69bc0650dd6d46f0b0e15708f089af537
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "66784213"
---
# <a name="updatebytes-method-sqlserverresultset"></a>updateBytes 方法 (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  使用字节值构成的数组更新指定列  。  
  
## <a name="overload-list"></a>重载列表  
  
|“属性”|描述|  
|----------|-----------------|  
|[updateBytes (int, byte[])](../../../connect/jdbc/reference/updatebytes-method-int-byte.md)|根据给定的列索引使用字节值构成的数组更新指定的列  。|  
|[updateBytes (java.lang.String, byte[])](../../../connect/jdbc/reference/updatebytes-method-java-lang-string-byte.md)|根据给定的列名称使用字节值构成的数组更新指定的列  。|  
  
## <a name="remarks"></a>Remarks  
 在之前的 [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] 版本中，可使用 SQLServerResultSet.updateBytes 将字节数组和 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 数据类型日期、时间、datetime2 或 datetimeoffset 的值相互转换     。 现在对于这些数据类型使用此方法将导致异常，指出不支持该转换。  
  
## <a name="see-also"></a>另请参阅  
 [SQLServerResultSet 成员](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet 类](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
