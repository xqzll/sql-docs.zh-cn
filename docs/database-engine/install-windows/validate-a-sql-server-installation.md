---
title: 验证 SQL Server 安装 | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
helpviewer_keywords:
- validating installations [SQL Server]
ms.assetid: 1689af50-d2b8-4aa6-8f27-cc7127157fc8
author: MashaMSFT
ms.author: mathoma
monikerRange: '>=sql-server-2016||=sqlallproducts-allversions'
manager: jroth
ms.openlocfilehash: 7597997f55e6b070013b32a1d36f0a16f8fe5111
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "66794676"
---
# <a name="validate-a-sql-server-installation"></a>验证 SQL Server 安装

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]
  
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 发现报告可用于验证 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的版本和在计算机上安装的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 功能。 “已安装的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 功能发现报告”显示了在本地服务器上安装的所有  [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)]、[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]、[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]、[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]、[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]、[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]、[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] 和 [!INCLUDE[ssSQL15](../../includes/sssqlv14-md.md)] 产品和功能的报告。 在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安装中心的 **“工具”** 页上提供 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 功能发现报告。  
  
 ## <a name="run-includessnoversionincludesssnoversion-mdmd-features-discovery-report"></a>运行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 功能发现报告  
  
 启动 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安装中心，使用“开始”菜单，依次指向“所有程序”、“[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \<Version Name>”、“配置工具”，然后单击“[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安装中心”      。 若要运行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 功能发现报告，请在“[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 安装中心”  的左侧导航区域中单击“工具”  ，然后单击“已安装的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 功能发现报告”  。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 发现报告将保存到 %ProgramFiles%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\\nnn\Setup Bootstrap\Log\\<last Setup Session\>  。  
  
 您还可以通过命令行生成发现报告。 从命令提示符运行“Setup.exe /Action=RunDiscovery”。如果将“/q”添加到上述命令行，将不显示 UI，但是仍将在 %ProgramFiles%\\[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]\\nnn\Setup Bootstrap\Log\\<last Setup Session\> 中创建报告  。  
  
## <a name="see-also"></a>另请参阅  
 [查看和读取 SQL Server 安装程序日志文件](../../database-engine/install-windows/view-and-read-sql-server-setup-log-files.md)  
  
  
