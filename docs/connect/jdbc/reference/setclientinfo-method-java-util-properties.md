---
title: setClientInfo 方法 (java.util.Properties) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: b2a8ec0b-40a2-44d1-90d9-a810d4132e56
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: e09d4cba23c87bdcaaa0503dffe73e65dfaf82b3
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 06/07/2019
ms.locfileid: "66795670"
---
# <a name="setclientinfo-method-javautilproperties"></a>setClientInfo 方法 (java.util.Properties)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  设置连接的客户端信息属性的值。  
  
## <a name="syntax"></a>语法  
  
```  
  
public void setClientInfo (java.util.Properties properties)  
```  
  
#### <a name="parameters"></a>Parameters  
 *properties*  
  
 包含要设置的客户端信息属性列表的 Properties 对象。  
  
## <a name="exceptions"></a>异常  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 此 setClientInfo 方法由 java.sql.Connection 接口中的 setClientInfo 方法指定。  
  
 [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] 不支持任何客户端信息属性。 如果 properties  输入参数没有引用空属性集，则此方法会生成警告。 也就是说，此方法针对应用程序要设置的属性生成警告。 应用程序应使用 [SQLServerConnection](../../../connect/jdbc/reference/sqlserverconnection-class.md) 类的 [getWarnings](../../../connect/jdbc/reference/getwarnings-method-sqlserverconnection.md) 方法来检索每个警告。  
  
## <a name="see-also"></a>另请参阅  
 [setClientInfo 方法 &#40;SQLServerConnection&#41;](../../../connect/jdbc/reference/setclientinfo-method-sqlserverconnection.md)   
 [SQLServerConnection 成员](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection 类](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
