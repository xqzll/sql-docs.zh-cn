---
title: getObject 方法 (int) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerCallableStatement.getObject (jnt)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: c4b8366b-c065-48e1-b712-19e2d9834228
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 01bca4d9cb7eea385cb1c9cc1f4cb4a1447c1caf
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 06/07/2019
ms.locfileid: "66787545"
---
# <a name="getobject-method-int"></a>getObject 方法 (int)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  根据给定的参数索引，检索指定参数的值作为 Java 编程语言中的一个对象。  
  
## <a name="syntax"></a>语法  
  
```  
  
public java.lang.Object getObject(int index)  
```  
  
#### <a name="parameters"></a>Parameters  
 索引   
  
 指示参数索引的 int  。  
  
## <a name="return-value"></a>返回值  
 Object 值  。  
  
## <a name="exceptions"></a>异常  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 此 getObject 方法是由 java.sql.CallableStatement 接口中的 getObject 方法指定的。  
  
 此方法将返回给定列的值作为一个 Java 对象。 根据 JDBC 规范中指定的内置类型映射，Java 对象的类型将为对应于此列 SQL 类型的默认 Java 对象类型。 如果此值为 SQL NULL，则驱动程序会返回 Java null。  
  
 也可使用此方法来读取数据库特定的抽象数据类型。 在 JDBC 2.0 中，getObject 方法的行为已扩展为具体化 SQL 用户定义类型的数据。 当列包含结构化或非重复值时，此方法的行为则类似于对 `getObject(columnIndex, this.getStatement().getConnection().getTypeMap())` 进行调用。  
  
 从 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] JDBC Driver 3.0 开始：  
  
-   date 类型的值将作为 java.sql.Date 对象返回  。  
  
-   time 类型的值将作为 java.sql.Time 对象返回  。  
  
-   datetime2 类型的值将作为 java.sql.Timestamp 对象返回  。  
  
-   datetimeoffset 类型的值将作为 microsoft.sql.DateTimeOffset 对象返回  。  
  
## <a name="see-also"></a>另请参阅  
 [getObject 方法 &#40;SQLServerCallableStatement&#41;](../../../connect/jdbc/reference/getobject-method-sqlservercallablestatement.md)   
 [SQLServerCallableStatement 成员](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [SQLServerCallableStatement 类](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
