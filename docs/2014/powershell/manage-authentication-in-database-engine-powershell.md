---
title: 在数据库引擎 PowerShell 中管理身份验证 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: scripting
ms.topic: conceptual
ms.assetid: ab9212a6-6628-4f08-a38c-d3156e05ddea
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 0992e3a956a2b498d92186fa91c0ed4fbddf6102
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "62762046"
---
# <a name="manage-authentication-in-database-engine-powershell"></a>在数据库引擎 PowerShell 中管理身份验证
  默认情况下， [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] PowerShell 组件在连接到 [!INCLUDE[ssDE](../includes/ssde-md.md)]实例时使用 Windows 身份验证。 您可以通过定义 PowerShell 虚拟驱动器，或者通过为 `-Username` 指定 `-Password` 和 `Invoke-Sqlcmd` 参数，使用 SQL Server 身份验证。  
  
1.  **开始之前：** [权限](#Permissions)  
  
2.  **若要设置身份验证，使用：** [虚拟驱动器](#SQLAuthVirtDrv)，[调用 Sqlcmd](#SQLAuthInvSqlCmd)  
  
##  <a name="Permissions"></a> Permissions  
 您可以在 [!INCLUDE[ssDE](../includes/ssde-md.md)] 实例中执行的所有操作都受到授予用于连接到该实例的身份验证凭据的权限的控制。 默认情况下， [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] PowerShell 和 cmdlet 将使用其运行所基于的 Windows 帐户来建立与 [!INCLUDE[ssDE](../includes/ssde-md.md)]的 Windows 身份验证连接。  
  
 若要建立 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 身份验证连接，您必须提供 SQL Server 身份验证登录 ID 和密码。 使用时[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]提供程序，必须将关联[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]登录凭据与虚拟驱动器，然后使用更改目录命令 (`cd`) 以连接到该驱动器。 在 Windows PowerShell 中，安全凭据只能与虚拟驱动器关联。  
  
##  <a name="SQLAuthVirtDrv"></a> 使用虚拟驱动器进行 SQL Server 身份验证  
 **创建与 SQL Server 身份验证登录相关联的虚拟驱动器**  
  
1.  创建一个函数，该函数：  
  
    1.  具有针对为虚拟驱动器提供的名称、登录 ID 以及要与虚拟驱动器相关联的提供程序路径的参数。  
  
    2.  使用 `read-host` 来提示用户输入密码。  
  
    3.  使用 `new-object` 来创建凭据对象。  
  
    4.  使用 `new-psdrive` 来创建具有提供的凭据的虚拟驱动器。  
  
2.  调用函数来创建具有提供的凭据的虚拟驱动器。  
  
### <a name="example-virtual-drive"></a>示例（虚拟驱动器）  
 此示例创建名为 **sqldrive** 的函数，您可使用该函数来创建与指定 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 身份验证登录名和实例相关联的虚拟驱动器。  
  
 **sqldrive** 函数提示您输入登录名的密码，并在您键入密码时屏蔽密码。 然后，每当你使用更改目录命令 (`cd`) 来使用虚拟驱动器名称连接到的路径，所有操作都执行使用[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]在创建驱动器时提供的身份验证登录凭据。  
  
```  
## Create a function that specifies the login and prompts for the password.  
  
function sqldrive  
{  
    param( [string]$name, [string]$login = "MyLogin", [string]$root = "SQLSERVER:\SQL\MyComputer\MyInstance" )  
    $pwd = read-host -AsSecureString -Prompt "Password"  
    $cred = new-object System.Management.Automation.PSCredential -argumentlist $login,$pwd  
    New-PSDrive $name -PSProvider SqlServer -Root $root -Credential $cred -Scope 1  
}  
  
## Use the sqldrive function to create a SQLAuth virtual drive.  
sqldrive SQLAuth  
  
## CD to the virtual drive, which invokes the supplied authentication credentials.  
cd SQLAuth  
```  
  
##  <a name="SQLAuthInvSqlCmd"></a> 使用 Invoke-Sqlcmd 的 SQL Server 身份验证  
 **将 Invoke-Sqlcmd 用于 SQL Server 身份验证**  
  
1.  使用 `-Username` 参数可以指定一个登录 ID，以及用于指定关联密码的 `-Password` 参数。  
  
### <a name="example-invoke-sqlcmd"></a>示例 (Invoke-Sqlcmd)  
 此示例使用 read-host cmdlet 来提示用户输入密码，然后使用 SQL Server 身份验证进行连接。  
  
```  
## Prompt the user for their password.  
$pwd = read-host -AsSecureString -Prompt "Password"  
  
Invoke-Sqlcmd -Query "SELECT GETDATE() AS TimeOfQuery;" -ServerInstance "MyComputer\MyInstance" -Username "MyLogin" -Password $pwd  
```  
  
## <a name="see-also"></a>请参阅  
 [SQL Server PowerShell](sql-server-powershell.md)   
 [SQL Server PowerShell 提供程序](sql-server-powershell-provider.md)   
 [Invoke-Sqlcmd cmdlet](../database-engine/invoke-sqlcmd-cmdlet.md)  
  
  
