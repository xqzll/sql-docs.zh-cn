---
title: setNClob 方法 （int，java.io.Reader） |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 9fc9938c-b821-41c7-8df7-e21cb83a46d4
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 34888d11cfdf88936b65aedc210d49e1a049bbc6
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "66800433"
---
# <a name="setnclob-method-int-javaioreader"></a>setNClob 方法 (int, java.io.Reader)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  将指定参数设置为指定的 Reader 对象。  
  
## <a name="syntax"></a>语法  
  
```  
  
public final void setNClob(int parameterIndex,  
                    java.io.Reader reader)  
```  
  
#### <a name="parameters"></a>Parameters  
 parameterIndex   
  
 指示参数索引的 int  。  
  
 reader   
  
 指示参数值的 Reader 对象。  
  
## <a name="exceptions"></a>异常  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 此 setNClob 方法是由 java.sql.PreparedStatement 接口中的 setNClob 方法指定的。  
  
## <a name="see-also"></a>另请参阅  
 [setNClob 方法 &#40;SQLServerPreparedStatement&#41;](../../../connect/jdbc/reference/setnclob-method-sqlserverpreparedstatement.md)   
 [SQLServerPreparedStatement 成员](../../../connect/jdbc/reference/sqlserverpreparedstatement-members.md)  
  
  
