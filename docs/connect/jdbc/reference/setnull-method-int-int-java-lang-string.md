---
title: setNull 方法 （int，int，java.lang.String） |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerPreparedStatement.setNull (int, int, java.lang.String)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 43c74e06-2858-49ba-bae7-b88808e5fff4
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 62f91e694ea655fe29c7306aeea9471ba432072d
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "66800336"
---
# <a name="setnull-method-int-int-javalangstring"></a>setNull 方法 (int, int, java.lang.String)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  根据要设置的参数的类型和名称，将指定参数设置为 Null 值。  
  
## <a name="syntax"></a>语法  
  
```  
  
public final void setNull(int paramIndex,  
                          int sqlType,  
                          java.lang.String typeName)  
```  
  
#### <a name="parameters"></a>Parameters  
 paramIndex   
  
 指示参数编号的 int  。  
  
 *sqlType*  
  
 java.sql.Types 定义的 JDBC 类型代码。  
  
 *typeName*  
  
 一个指示要设置的参数完全限定名称的 String  。  
  
## <a name="exceptions"></a>异常  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 此 setNull 方法是由 java.sql.PreparedStatement 接口中的 setNull 方法指定的。  
  
## <a name="see-also"></a>另请参阅  
 [setNull 方法 &#40;SQLServerPreparedStatement&#41;](../../../connect/jdbc/reference/setnull-method-sqlserverpreparedstatement.md)   
 [SQLServerPreparedStatement 成员](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)   
 [SQLServerPreparedStatement 类](../../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)  
  
  
