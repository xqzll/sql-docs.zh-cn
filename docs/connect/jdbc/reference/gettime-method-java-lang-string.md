---
title: getTime 方法 (java.lang.String) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerCallableStatement.getTime (java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: ca0a3b29-30d1-4d20-bc8d-d3d9ed19ff50
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 6fe0152d23bcf71e371ad778a961dedb9c6ee739
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "66778813"
---
# <a name="gettime-method-javalangstring"></a>getTime 方法 (java.lang.String)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  根据给定的参数名称，检索指定参数的值作为 Java 编程语言中的 java.sql.Time 对象。  
  
## <a name="syntax"></a>语法  
  
```  
  
public java.sql.Time getTime(java.lang.String sCol)  
```  
  
#### <a name="parameters"></a>Parameters  
 sCol   
  
 包含参数名称的字符串  。  
  
## <a name="return-value"></a>返回值  
 Time 对象。  
  
## <a name="exceptions"></a>异常  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 此 getTime 方法是由 java.sql.CallableStatement 接口中的 getTime 方法指定的。  
  
 在查看标题为"Getter 方法转换"的图表[了解数据类型转换](../../../connect/jdbc/understanding-data-type-conversions.md)以查看哪个[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]可通过此方法检索的数据类型。  
  
## <a name="see-also"></a>另请参阅  
 [getTime 方法 &#40;SQLServerCallableStatement&#41;](../../../connect/jdbc/reference/gettime-method-sqlservercallablestatement.md)   
 [SQLServerCallableStatement 成员](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [SQLServerCallableStatement 类](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
