---
title: getFailoverPartner 方法 (SQLServerDataSource) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDataSource.getFailoverPartner
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 885f927f-9c48-42e0-a7fb-fd936d2b8130
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 61d86ecbab10fc1a2fc1f05034f5af00525becdc
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 06/07/2019
ms.locfileid: "66767102"
---
# <a name="getfailoverpartner-method-sqlserverdatasource"></a>getFailoverPartner 方法 (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  返回在数据库镜像配置中使用的故障转移服务器的名称。  
  
## <a name="syntax"></a>语法  
  
```  
  
public string getFailoverPartner()  
```  
  
## <a name="return-value"></a>返回值  
 包含故障转移伙伴名称的字符串  ，如果未设置值，则为 Null。  
  
## <a name="remarks"></a>Remarks  
 此方法返回的值将反映使用 [setFailoverPartner](../../../connect/jdbc/reference/setfailoverpartner-method-sqlserverdatasource.md) 方法设置的故障转移伙伴名称。  
  
## <a name="see-also"></a>另请参阅  
 [SQLServerDataSource 成员](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource 类](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
