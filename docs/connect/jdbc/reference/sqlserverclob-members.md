---
title: SQLServerClob 成员 | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apitype: Assembly
ms.assetid: 7db785ca-edd5-4833-8053-17fdbf87279a
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 0940e17ada4fb6ebf9c18667bff55a4fe4c42799
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "66803116"
---
# <a name="sqlserverclob-members"></a>SQLServerClob 成员
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  下表列出了 [SQLServerClob ](../../../connect/jdbc/reference/sqlserverclob-class.md) 类公开的成员。  
  
## <a name="constructors"></a>构造函数  
  
|“属性”|描述|  
|----------|-----------------|  
|[SQLServerClob](../../../connect/jdbc/reference/sqlserverclob-constructor-sqlserverconnection-java-lang-string.md)|初始化 SQLServerClob 类的新实例。|  
  
## <a name="fields"></a>字段  
 无。  
  
## <a name="inherited-fields"></a>继承的字段  
 无。  
  
## <a name="methods"></a>方法  
  
|“属性”|描述|  
|----------|-----------------|  
|[free](../../../connect/jdbc/reference/free-method-sqlserverclob.md)|此方法可释放 CLOB 对象以及它所持有的资源。|  
|[getAsciiStream](../../../connect/jdbc/reference/getasciistream-method-sqlserverclob.md)|将 Clob 作为 ASCII 流具体化。|  
|[getCharacterStream](../../../connect/jdbc/reference/getcharacterstream-method-sqlserverclob.md)|将 Clob 数据作为 java.io.Reader 对象或字符流返回。|  
|[getSubString](../../../connect/jdbc/reference/getsubstring-method-sqlserverclob.md)|根据指定的起始位置和要复制的字符数返回 Clob 中指定子字符串的副本。|  
|[length](../../../connect/jdbc/reference/length-method-sqlserverclob.md)|返回 Clob 中的字符数。|  
|[position](../../../connect/jdbc/reference/position-method-sqlserverclob.md)|返回指定 Clob 对象的字符位置或根据指定的起始位置返回 Clob 中的子字符串。|  
|[setAsciiStream](../../../connect/jdbc/reference/setasciistream-method-sqlserverclob.md)|返回用来将 ASCII 字符写入起始于指定位置的 Clob 的流。|  
|[setCharacterStream](../../../connect/jdbc/reference/setcharacterstream-method-sqlserverclob.md)|返回用来将 Unicode 字符流写入起始于指定位置的 Clob 的流。|  
|[setString](../../../connect/jdbc/reference/setstring-method-sqlserverclob.md)|将给定的字符串写入起始于指定位置的 Clob。|  
|[truncate](../../../connect/jdbc/reference/truncate-method-sqlserverclob.md)|将 Clob 截断为指定长度。|  
  
## <a name="inherited-methods"></a>继承的方法  
  
|类继承自|方法|  
|--------------------------|-------------|  
|java.lang.Object|clone、equals、finalize、getClass、hashCode、notify、notifyAll、toString、wait|  
  
## <a name="see-also"></a>另请参阅  
 [SQLServerClob 类](../../../connect/jdbc/reference/sqlserverclob-class.md)  
  
  
