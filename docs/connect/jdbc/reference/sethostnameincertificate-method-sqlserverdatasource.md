---
title: setHostNameInCertificate 方法 (SQLServerDataSource) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- setHostNameInCertificate Method (SQLServerDataSource)
apilocation:
- setHostNameInCertificate Method (SQLServerDataSource)
apitype: Assembly
ms.assetid: 2bcf4f2e-a103-4374-abc4-ffad4ce8e3c0
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: cde4c07a6a611fd6cd97324c46eae1e2ddc379ce
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 06/07/2019
ms.locfileid: "66764368"
---
# <a name="sethostnameincertificate-method-sqlserverdatasource"></a>setHostNameInCertificate 方法 (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  设置要用于验证 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 安全套接字层 (SSL) 证书的主机名。  
  
## <a name="syntax"></a>语法  
  
```  
  
public void setHostNameInCertificate(java.lang.String hostNameInCertificate)  
```  
  
#### <a name="parameters"></a>Parameters  
 *hostNameInCertificate*  
  
 一个包含主机名的字符串  。  
  
## <a name="remarks"></a>Remarks  
 当使用 SSL 对通信层加密时，将使用 hostNameInCertificate 值来验证 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] SSL 证书。 默认值为 null。  
  
 如果 hostNameInCertificate 属性设置为 Null 或未指定，则 [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] 将使用 serverName 属性值来对 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] SSL 证书进行验证。 如果 hostNameInCertificate 属性被设置为字符串或空字符串 ("")，则驱动程序将使用该值验证服务器 SSL 证书。  
  
## <a name="see-also"></a>另请参阅  
 [SQLServerDataSource 成员](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource 类](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
