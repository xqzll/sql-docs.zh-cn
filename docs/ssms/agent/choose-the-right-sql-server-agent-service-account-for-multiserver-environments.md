---
title: 为多服务器环境选择代理服务帐户 | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent, service accounts
- multiserver environments [SQL Server], SQL Server Agent service account behavior
ms.assetid: a07e2f38-281c-495b-965b-13fad03ba548
author: markingmyname
ms.author: maghan
manager: craigg
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 467896f654bc39abf1317287860fe59edee4060a
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "65105905"
---
# <a name="choose-the-right-sql-server-agent-service-account-for-multiserver-environments"></a>为多服务器环境选择正确的 SQL Server 代理服务帐户
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> [Azure SQL 数据库托管实例](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance)目前支持大多数但并非所有 SQL Server 代理功能。 有关详细信息，请参阅 [Azure SQL 数据库托管实例与 SQL Server 之间的 T-SQL 差异](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent)。

为 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理服务选择的 Windows 帐户可影响多服务器环境的行为，如下所示：  
  
-   如果使用非本地 Windows Administrators 组成员的帐户运行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理服务，则将目标服务器登记在主服务器中时可能会失败。 如果出现这种情况，则返回以下错误消息：  
  
    “登记操作失败。”  
  
    重新启动 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 和 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理服务以解决此问题。  
  
-   当 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理服务使用本地系统帐户运行时，仅当主服务器和目标服务器位于同一台计算机上时，才支持主服务器 - 目标服务器操作。 如果使用此配置，则在将目标服务器登记到主服务器时返回以下信息：  
  
    “请确保 <target_server_computer_name>  的代理启动帐户拥有以 targetServer 身份登录的权限”。  
  
    您可以忽略此信息性消息。 登记操作将成功完成。  
  
有关如何选择 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理服务帐户的信息，请参阅 [选择 SQL Server 代理服务帐户](../../ssms/agent/select-an-account-for-the-sql-server-agent-service.md)。  
  
