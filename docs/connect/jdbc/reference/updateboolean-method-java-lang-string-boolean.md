---
title: updateBoolean 方法 (java.lang.String, boolean) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.updateBoolean (java.lang.String, boolean)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 5fed9ebb-d9a3-4d1a-9212-1057a603c4e5
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 488d79e4b3d82bc20d7046efd09621fb0d08e707
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 06/07/2019
ms.locfileid: "66787055"
---
# <a name="updateboolean-method-javalangstring-boolean"></a>updateBoolean 方法 (java.lang.String, boolean)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  根据给定的列名称使用 boolean  值更新指定的列。  
  
## <a name="syntax"></a>语法  
  
```  
  
public void updateBoolean(java.lang.String columnName,  
                          boolean x)  
```  
  
#### <a name="parameters"></a>Parameters  
 *columnName*  
  
 一个包含列名的字符串  。  
  
 *x*  
  
 一个布尔值  。  
  
## <a name="exceptions"></a>异常  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 此 updateBoolean 方法由 java.sql.ResultSet 接口中的 updateBoolean 方法指定。  
  
## <a name="see-also"></a>另请参阅  
 [updateBoolean 方法 &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/updateboolean-method-sqlserverresultset.md)   
 [SQLServerResultSet 成员](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet 类](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
