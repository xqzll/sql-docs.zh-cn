---
title: setFailoverPartner 方法 (SQLServerDataSource) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDataSource.setFailoverPartner
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 5310b7c2-9d10-474f-ad3a-218fe5da694b
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 11bd963275f94fd5ab37d17ead561adbfb0bff5c
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 06/07/2019
ms.locfileid: "66802964"
---
# <a name="setfailoverpartner-method-sqlserverdatasource"></a>setFailoverPartner 方法 (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  设置在数据库镜像配置中使用的故障转移服务器的名称。  
  
## <a name="syntax"></a>语法  
  
```  
  
public void setFailoverPartner(java.lang.String serverName)  
```  
  
#### <a name="parameters"></a>Parameters  
 *serverName*  
  
 包含故障转移服务器名称的 String  。  
  
## <a name="remarks"></a>Remarks  
 如果在与主服务器进行初始连接时失败，则使用由此方法设置的值；建立初始连接后，将忽略此值。 此外，还应将此方法与 [setDatabaseName](../../../connect/jdbc/reference/setdatabasename-method-sqlserverdatasource.md) 方法结合使用，否则将引发异常。  
  
 驱动程序不支持在设置故障转移服务器名称时指定故障转移服务器的端口号。 但是，它支持在调用 [setServerName](../../../connect/jdbc/reference/setservername-method-sqlserverdatasource.md) 方法和 [setInstanceName](../../../connect/jdbc/reference/setinstancename-method-sqlserverdatasource.md) 方法时，同时调用 [setFailoverPartner](../../../connect/jdbc/reference/setfailoverpartner-method-sqlserverdatasource.md) 方法。  
  
## <a name="see-also"></a>另请参阅  
 [SQLServerDataSource 成员](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource 类](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
