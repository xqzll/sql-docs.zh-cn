---
title: 连接到 SQL Server (DB2ToSQL) |Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: bc14a072-8949-4ee0-a4b4-ada55fe8df5c
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 0bc3c92067d1fd8240cc17db03de7dac409a0123
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "63298981"
---
# <a name="connect-to-sql-server-db2tosql"></a>连接到 SQL Server (DB2ToSQL)
使用**连接到 SQL Server**对话框以连接到的实例[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]想要迁移到。 访问**连接到 SQL Server**对话框中，在**文件**菜单中，单击**连接到 SQL Server**。  
  
## <a name="options"></a>选项  
**服务器名称**  
输入或选择要连接到的 SQL Server 实例。 默认情况下，显示最近连接到的实例。  
  
-   如果要连接到本地计算机上的默认实例，可以输入**localhost**或句点 (**。**)。  
  
-   如果要连接到另一台计算机上的默认实例，输入的计算机的名称。  
  
-   如果要连接到另一台计算机上的命名实例，输入计算机名称、 一个反斜杠和实例名称，例如*MyServer*\\*MyInstance*。  
  
**服务器端口**  
如果你的实例[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]未配置为接受连接在默认端口 (1433)，输入端口号。 否则，将此值留空。  
  
**“数据库”**  
指定要将对象和数据迁移的数据库。 此选项不可用时重新连接到[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。  
  
**身份验证**  
选择用于连接到的身份验证方法[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。 若要使用当前 Windows 帐户，选择 Windows 身份验证。 若要指定[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]登录名和密码，选择[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]身份验证。  
  
**用户名**  
如果使用的[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]身份验证，该实例的输入的登录名[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。 如果使用 Windows 身份验证，则此选项不可用。  
  
**密码**  
如果使用的[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]身份验证，该实例上的登录名输入的密码[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。 如果使用 Windows 身份验证，则此选项不可用。  
  
**加密连接**  
如果你想要安全地连接到 SQL Server，请通过检查使用的加密连接**对连接进行加密**复选框。  
  
**信任服务器证书**  
如果你想要使用此选项，选择**信任服务器证书**复选框。  
  
> [!NOTE]  
> 若要启用**信任服务器证书**，必须将"加密"设置为**True**。  
  
