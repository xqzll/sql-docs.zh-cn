---
title: getURL 方法 (SQLServerDatabaseMetaData) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDatabaseMetaData.getURL
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: fcb66851-db5f-4ae8-b728-d129480b6f42
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: f170e15ec0096d02fd98acb16e15a6ac05257f31
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 06/07/2019
ms.locfileid: "66779740"
---
# <a name="geturl-method-sqlserverdatabasemetadata"></a>getURL 方法 (SQLServerDatabaseMetaData)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  检索此数据库的 URL。  
  
## <a name="syntax"></a>语法  
  
```  
  
public java.lang.String getURL()  
```  
  
## <a name="return-value"></a>返回值  
 一个包含 URL 的字符串  。  
  
## <a name="exceptions"></a>异常  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 此 getURL 方法是由 java.sql.DatabaseMetaData 接口中的 getURL 方法指定的。  
  
 将 [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] 与 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 数据库一起使用时，此方法会返回包含以下信息的字符串值：   
  
-   "jdbc:sqlserver://" 的 URL 值  
  
-   可选的连接属性，如**serverName**， **instanceName**，和**端口号**  
  
-   由用户设置的其他连接属性和设为非空或非 Null 的驱动程序默认值的所有连接属性，userName、password 和 integratedSecurity 除外    。  
  
## <a name="see-also"></a>另请参阅  
 [SQLServerDatabaseMetaData 方法](../../../connect/jdbc/reference/sqlserverdatabasemetadata-methods.md)   
 [SQLServerDatabaseMetaData 成员](../../../connect/jdbc/reference/sqlserverdatabasemetadata-members.md)   
 [SQLServerDatabaseMetaData 类](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md)  
  
  
