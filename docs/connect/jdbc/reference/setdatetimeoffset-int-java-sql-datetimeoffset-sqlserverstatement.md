---
title: setDateTimeOffset(int, java.sql.DateTimeOffset) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: e8b6e380-6b53-489b-be73-73fcb5258269
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 36b23fb46e8cd909cf71e696293f2981731a86d2
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "66793917"
---
# <a name="setdatetimeoffsetint-javasqldatetimeoffset-sqlserverstatement"></a>setDateTimeOffset(int, java.sql.DateTimeOffset) (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  将指定参数设置为给定的 DateTimeOffset 值。  
  
## <a name="syntax"></a>语法  
  
```  
  
public void setDateTimeOffset(int parameterIndex, DateTimeOffset dateTime)  
```  
  
#### <a name="parameters"></a>Parameters  
 parameterIndex   
  
 要设置的列的索引。  
  
 *dateTimeOffset*  
  
 一个 DateTimeOffset 对象。  
  
## <a name="exceptions"></a>异常  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 DateTimeOffset 格式为“YYYY-MM-DD HH-MM-SS[.nnnnnnn] [+][-] HH:MM”。 请以下表作为参考。  
  
|SQL 类型|Insert|  
|--------------|------------|  
|DATETIME|只能插入：“YYYY-MM-DD hh:mm:ss[.nnn]”|  
|smalldatetime|只能插入：“YYYY-MM-DD hh:mm:ss”|  
|Time|只能插入：“hh:mm:ss[.nnnnnnn]”|  
|date|只能插入：“YYYY-MM-DD”|  
|datetime2|只能插入：“YYYY-MM-DD hh:mm:ss[.nnnnnnn]”|  
  
## <a name="see-also"></a>另请参阅  
 [getDateTimeOffset &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/getdatetimeoffset-sqlserverresultset.md)   
 [SQLServerStatement 成员](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [SQLServerStatement 类](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
