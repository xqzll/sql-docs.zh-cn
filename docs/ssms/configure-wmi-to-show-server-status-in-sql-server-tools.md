---
title: 在 SQL Server 工具中将 WMI 配置为显示服务器状态 | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- WMI Provider for Server Events, setting permissions
- WMI permissions [SQL Server]
ms.assetid: 7e97197b-ed4d-40d1-9a52-9ab1d92401d7
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 16e262dbc1a89ef16fff5906e128b5f073c8bc3c
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "65102838"
---
# <a name="configure-wmi-to-show-server-status-in-sql-server-tools"></a>在 SQL Server 工具中将 WMI 配置为显示服务器状态
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
本主题介绍了如何在 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] 中配置 WMI 以便在 SQL Server 工具中显示服务器状态。 连接到服务器后，已注册的服务器和 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]的对象资源管理器组件以及 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 配置管理器均使用 Windows Management Instrumentation (WMI) 来获取 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] (MSSQLSERVER) 和 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 代理 (MSSQLSERVER) 服务的状态。 若要显示服务的状态，用户必须具有远程访问 WMI 对象的权限。 服务器必须已安装 WMI 才能配置此权限。  
  
## <a name="SSMSProcedure"></a>配置 WMI 权限  
  
1.  在远程服务器的“开始”  菜单上，单击“运行”  。  
  
2.  在“打开”  框中，键入 **wmimgmt.msc**，然后单击“确定”  。  
  
3.  在 **Windows 管理体系结构**程序中，右键单击“WMI 控制(本地)”  ，再单击“属性”  。  
  
4.  在“WMI 控制(本地) 属性”  对话框的“安全性”  选项卡中，展开“Root”  ，再单击“CIMV2”  。  
  
5.  单击“安全设置”  打开“安全设置 ROOT\CIMV2”  对话框。  
  
6.  向“组或用户名称”  框中添加一个组或用户，并将其选中。  
  
7.  在“<group or user> 权限”   框中，为希望远程检测服务状态的用户选择“远程启用”  权限的“允许”  列。  
  
## <a name="see-also"></a>另请参阅  
[启动、停止或暂停 SQL Server 代理服务](../ssms/agent/start-stop-or-pause-the-sql-server-agent-service.md)  
  
