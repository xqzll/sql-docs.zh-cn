---
title: registerOutParameter 方法键入 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerCallableStatement.registerOutParameter (java.lang.String, int)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 5d00242c-4d9c-42cc-86bb-b76f5ef876b8
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 6b37a9b7c4a3dbf6f386ffed6e9e6a7669ac518d
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 06/07/2019
ms.locfileid: "66802058"
---
# <a name="registeroutparameter-method-javalangstring-int"></a>registerOutParameter 方法 (java.lang.String, int)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  将具有指定名称的 OUT 参数注册为给定的 JDBC 类型。  
  
## <a name="syntax"></a>语法  
  
```  
  
public void registerOutParameter(java.lang.String s,  
                                 int n)  
```  
  
#### <a name="parameters"></a>Parameters  
 *s*  
  
 包含参数名称的字符串  。  
  
 *n*  
  
 在 java.sql.Types 中定义的 JDBC 类型代码。  
  
## <a name="exceptions"></a>异常  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 此 registerOutParameter 方法由 java.sql.CallableStatement 接口中的 registerOutParameter 方法指定。  
  
## <a name="see-also"></a>另请参阅  
 [registerOutParameter 方法 &#40;SQLServerCallableStatement&#41;](../../../connect/jdbc/reference/registeroutparameter-method-sqlservercallablestatement.md)   
 [SQLServerCallableStatement 成员](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [SQLServerCallableStatement 类](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
