---
title: getSendStringParametersAsUnicode 方法 (SQLServerDataSource) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDataSource.getSendStringParametersAsUnicode
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 3836d0ab-c3fb-41ff-bb89-10389594ae51
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 88f5d294e46ddc6dc4da92e437fc4513f9a50a47
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 06/07/2019
ms.locfileid: "66792008"
---
# <a name="getsendstringparametersasunicode-method-sqlserverdatasource"></a>getSendStringParametersAsUnicode 方法 (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  返回指示是否启用以 UNICODE 格式将字符串参数发送到服务器的 boolean  值。  
  
## <a name="syntax"></a>语法  
  
```  
  
public boolean getSendStringParametersAsUnicode()  
```  
  
## <a name="return-value"></a>返回值  
 如果以 UNICODE 格式将字符串参数发送到服务器，则为 true  。 否则为 **false**。  
  
## <a name="remarks"></a>Remarks  
 如果 sendStringParametersAsUnicode 属性设置为 true  （默认值），字符串参数便会以 UNICODE 格式发送到服务器。 如果 sendStringParametersAsUnicode 设置为 false  ，字符串参数便会以 ASCII/MBCS 格式（而非 UNICODE 格式）发送到服务器。 如果 sendStringParametersAsUnicode 属性未设置，getSendStringParametersAsUnicode 返回默认值 true  。  
  
 有关 sendStringParametersAsUnicode 连接属性的详细信息，请参阅[连接属性设置](../../../connect/jdbc/setting-the-connection-properties.md)。  
  
## <a name="see-also"></a>另请参阅  
 [SQLServerDataSource 成员](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource 类](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
