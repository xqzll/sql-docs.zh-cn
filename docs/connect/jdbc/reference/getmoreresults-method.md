---
title: getMoreResults 方法 （) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerStatement.getMoreResults ()
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: df89db50-0b2f-4094-820a-30be25ad72fe
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 989cb8fee55de2ec522e4517521815b467d7d946
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 06/07/2019
ms.locfileid: "66784657"
---
# <a name="getmoreresults-method-"></a>getMoreResults 方法 ()
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  移动到此 [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) 对象的下一个结果。  
  
## <a name="syntax"></a>语法  
  
```  
  
public final boolean getMoreResults()  
```  
  
## <a name="return-value"></a>返回值  
 如果返回的结果为一个结果集，则为 true  。 否则为 **false**。  
  
## <a name="exceptions"></a>异常  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 此 getMoreResults 方法由 java.sql.Statement 接口中的 getMoreResults 方法指定。  
  
 调用 getMoreResults 方法，可隐式关闭使用 [getResultSet](../../../connect/jdbc/reference/getresultset-method-sqlserverstatement.md) 方法获取的所有当前已打开的结果集对象。  
  
## <a name="see-also"></a>另请参阅  
 [getMoreResults 方法 &#40;SQLServerStatement&#41;](../../../connect/jdbc/reference/getmoreresults-method-sqlserverstatement.md)   
 [SQLServerStatement 成员](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [SQLServerStatement 类](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
