---
title: 安装 SQL Server PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/05/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
ms.assetid: 854c0b2f-02d2-46a4-a8cc-6b7a5d191cf8
author: MashaMSFT
ms.author: mathoma
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions'
manager: jroth
ms.openlocfilehash: 1a2e4099350d72cbab6a91b75664ee031ee35a60
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "66794938"
---
# <a name="install-sql-server-powershell"></a>安装 SQL Server PowerShell
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]
  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安装程序会自动配置 PowerShell 组件。  

您通过使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安装程序安装为 Windows PowerShell 提供 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 支持的软件。 选择要求 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell 支持的任何功能时，安装程序将安装下列 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell 组件：  
  
- [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] PowerShell 管理单元。这些管理单元是 dll 文件，可用来实现两种类型的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Windows PowerShell 支持：  
  
  - 一组 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] cmdlet。 Cmdlet 是用来实现特定操作的命令。 例如， **Invoke-Sqlcmd** 可用于运行 [!INCLUDE[tsql](../../includes/tsql-md.md)] 或 XQuery 脚本，而这些脚本也可使用 **sqlcmd** 实用工具运行， **Invoke-PolicyEvaluation** 用于报告 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 对象是否符合基于策略的管理策略。  
  
  - 一个 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 提供程序。 通过该提供程序，可以使用类似于文件系统路径的路径，在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 对象的层次结构中导航。 每个对象都与 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 管理对象模型中的一个类关联。 您可以使用该类的方法和属性来针对对象执行工作。 例如，如果通过 cd 切换到路径中的某个数据库对象，则可以使用 Microsoft.SqlServer.Managment.SMO.Database 类的方法和属性来管理该数据库。  
 
- **sqlps** 模块，该模块将导入到 Windows PowerShell 会话中以便加载 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 管理单元。  
 
- [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 支持从对象资源管理器树启动 Windows PowerShell 会话。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理支持 Windows PowerShell 作业步骤。  
  
Windows Server 2012 及更高版本和 Windows 8 及更高版本已安装和配置了 PowerShell。 有关安装 Windows PowerShell 的信息，请参阅[安装 Windows PowerShell](https://docs.microsoft.com/powershell/scripting/setup/installing-windows-powershell)。  

有关详细信息，请参阅：   

- [SQL Server PowerShell](../../relational-databases/scripting/sql-server-powershell.md)  
  
  
