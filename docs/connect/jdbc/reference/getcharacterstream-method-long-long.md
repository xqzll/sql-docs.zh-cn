---
title: getCharacterStream 方法 (long，long) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: d70f502f-f60f-436a-83e6-797a0ed71bf3
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 2881f3a9e0d3a4179334256aa7d2917917cf97f3
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "66781325"
---
# <a name="getcharacterstream-method-long-long"></a>getCharacterStream 方法 (long, long)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  将 Clob  数据作为 Reader 对象或字符流返回且具有指定位置和长度。  
  
## <a name="syntax"></a>语法  
  
```  
  
public java.io.Reader getCharacterStream(long pos,  
                                         long length)  
```  
  
#### <a name="parameters"></a>Parameters  
 pos   
  
 指示与要检索的部分值的第一个字符之间偏移量的 long 值  。  
  
 *length*  
  
 指示要检索的部分值的字符长度的 long  。  
  
## <a name="return-value"></a>返回值  
 包含 Clob  数据的 Reader 对象。  
  
## <a name="exceptions"></a>异常  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 此 getCharacterStream 方法由 java.sql.Clob 接口中的 getCharacterStream 方法指定。  
  
## <a name="see-also"></a>另请参阅  
 [getCharacterStream 方法 &#40;SQLServerClob&#41;](../../../connect/jdbc/reference/getcharacterstream-method-sqlserverclob.md)   
 [SQLServerClob 方法](../../../connect/jdbc/reference/sqlserverclob-methods.md)   
 [SQLServerClob 成员](../../../connect/jdbc/reference/sqlserverclob-members.md)  
  
  
