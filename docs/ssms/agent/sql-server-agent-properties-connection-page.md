---
title: SQL Server 代理属性（“连接”页）| Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql13.ag.agent.connection.f1
ms.assetid: d6a677ff-60ad-47ba-a0cb-df4193b165e0
author: markingmyname
ms.author: maghan
manager: craigg
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: e6cdb4cc45876377a34e75fbdaffa8bd726d8e64
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "65089416"
---
# <a name="sql-server-agent-properties-connection-page"></a>SQL Server 代理属性（“连接”页）
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> [Azure SQL 数据库托管实例](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance)目前支持大多数但并非所有 SQL Server 代理功能。 有关详细信息，请参阅 [Azure SQL 数据库托管实例与 SQL Server 之间的 T-SQL 差异](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent)。

使用此页可查看和修改 [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理服务与 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 之间的连接设置。  
  
## <a name="options"></a>选项  
**本地主机服务器别名**  
指定用来连接 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的本地实例的别名。 如果无法使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理的默认连接选项，请为相应的实例定义一个别名，并在此处指定该别名。  
  
**使用 Windows 身份验证**  
将 [!INCLUDE[msCoName](../../includes/msconame_md.md)] Windows 身份验证设置为连接 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例时使用的身份验证方法。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理按运行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理服务的帐户的身份进行连接。  
  
**Use SQL Server Authentication**  
将 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 身份验证设置为连接 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例时使用的身份验证方法。  
  
> [!IMPORTANT]  
> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 提供身份验证是为了向后兼容。 为了增强安全性，请使用 Windows 身份验证（如果可能的话）。  
  
**登录**  
指定用于连接 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的登录名。  
  
**密码**  
指定用于连接 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的密码。  
  
