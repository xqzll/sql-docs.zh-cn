---
title: setString 方法 (long, java.lang.String, int, int) - NClob | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 2d5e9f50-15b2-4c76-8bfc-3b5be49c2781
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: ad49b4a5e675d4ff6635583e0b64a1e57434ff22
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "66762269"
---
# <a name="setstring-method-long-javalangstring-int-int-sqlservernclob"></a>setString 方法 (long, java.lang.String, int, int) (SQLServerNClob)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  基于指定的偏移量和长度，将指定的字符串写入到始于指定位置的 NCLOB。  
  
## <a name="syntax"></a>语法  
  
```  
  
int setString(long pos,  
              java.lang.String str,  
              int offset,  
              int len)  
```  
  
#### <a name="parameters"></a>Parameters  
 pos   
  
 写入 NCLOB  的起始位置；第一个位置为 1。  
  
 *str*  
  
 要写入 NCLOB  的 String。  
  
 offset   
  
 *str* 中的偏移量，从这个位置开始读取将要写入的字符。  
  
 len   
  
 将要写入的字符数。  
  
## <a name="exceptions"></a>异常  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 此 setString 方法是由 java.sql.NClob 接口中的 setString 方法指定的。  
  
## <a name="see-also"></a>另请参阅  
 [SQLServerNClob 方法](../../../connect/jdbc/reference/sqlservernclob-methods.md)   
 [SQLServerNClob 成员](../../../connect/jdbc/reference/sqlservernclob-members.md)   
 [SQLServerNClob 类](../../../connect/jdbc/reference/sqlservernclob-class.md)  
  
  
