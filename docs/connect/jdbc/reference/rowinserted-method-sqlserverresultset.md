---
title: rowInserted 方法 (SQLServerResultSet) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.rowInserted
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: e7c10372-0be8-4baa-87f7-ed6b66003357
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: da746533231983d67bbfe3689d0df63086d678bc
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "66765381"
---
# <a name="rowinserted-method-sqlserverresultset"></a>rowInserted 方法 (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  检索当前行是否曾插入内容。  
  
## <a name="syntax"></a>语法  
  
```  
  
public boolean rowInserted()  
```  
  
## <a name="return-value"></a>返回值  
 如果行中曾进行过插入并且检测到了插入操作，则为“true”  。 否则为 **false**。  
  
## <a name="exceptions"></a>异常  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 此 rowUpdated 方法由 java.sql.ResultSet 接口中的 rowUpdated 方法指定。  
  
 返回的值取决于此 [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) 对象是否可以检测可见的插入。  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 不会检测任何游标类型的插入行。  
  
## <a name="see-also"></a>另请参阅  
 [SQLServerResultSet 成员](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet 类](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
