---
title: 连接选项 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- connection options [ODBC]
- ODBC driver for Oracle [ODBC], connection options
- custom connection options [ODBC]
ms.assetid: abfdc133-cb33-435f-a467-fbe15444f687
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 06695bf1770c9e362decac5702dcd924d47c23bb
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "63301764"
---
# <a name="connect-options"></a>连接选项
> [!IMPORTANT]  
>  此功能将 Windows 的未来版本中删除。 请避免在新的开发工作中使用该功能，并着手修改当前还在使用该功能的应用程序。 相反，使用提供的 Oracle 的 ODBC 驱动程序。  
  
 这些选项允许自定义应用程序中的数据库连接。  
  
|连接选项|说明|  
|--------------------|-----------|  
|SQL_AUTOCOMMIT|如果您选择 SQL_AUTOCOMMIT_OFF，你的应用程序必须显式提交或回滚的事务[SQLTransact](../../odbc/microsoft/core-level-api-functions-odbc-driver-for-oracle.md)。|  
|SQL_ODBC_CURSORS|此连接属性实现驱动程序管理器中。|  
|SQL_OPT_TRACE|此连接属性实现驱动程序管理器中。|  
|SQL_OPT_TRACEFILE|此连接属性实现驱动程序管理器中。|  
|SQL_TRANSLATE_DLL|将返回错误："驱动程序不可用。"|  
|SQL_TRANSLATE_OPTION|一个 32 位值传递给转换.dll。|  
|SQL_TXN_ISOLATION|驱动程序允许仅 SQL_TXN_READ_COMMITTED。<br /><br /> 不支持以下 vParams:<br /><br /> SQL_TXN_READ_UNCOMMITTED<br /><br /> SQL_TXN_REAPEATABLE_READ<br /><br /> SQL_TXN_SERIALIZABLE|  
|SQL_ATTR_ENLIST_IN_DTC|此 ODBC 3.0 连接属性，可在由 Microsoft 组件服务 （或 MTS，如果您使用的 Windows NT） 协调的分布式事务中使用用于 Oracle 的 ODBC 驱动程序。 它提供的接口指针*pITransaction*为作为事务*vParam*参数。|  
|SQL_ATTR_CONNECTION_DEAD|此只读 ODBC 3.5 连接属性，可确定是否有失败的 Oracle 服务器的连接。 仅限; 获取不能设置。|
