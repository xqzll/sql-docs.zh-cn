---
title: 广播关闭消息（命令提示符）| Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- SQL Server, stopping
- named instances [SQL Server], broadcasting shutdown messages
- shutdown message broadcast
- broadcasting shutdown message
- command prompt [SQL Server], broadcasting shutdown messages
- default instances [SQL Server], broadcasting shutdown messages
- stopping SQL Server
ms.assetid: 9f20ccd5-d952-431d-ba12-339911af9430
author: MikeRayMSFT
ms.author: mikeray
manager: jroth
ms.openlocfilehash: 7517264d6ebc7baef2f066654f0309219f31b34d
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "66786898"
---
# <a name="broadcast-a-shutdown-message-command-prompt"></a>广播关闭消息（命令提示符）
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  本主题介绍了如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] net send **命令在** 中广播关闭消息。 在消息中，包括 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例将停止的时间，以便用户可以及时完成任务。  
  
##  <a name="SSMSProcedure"></a>  
  
#### <a name="to-broadcast-a-shutdown-message"></a>广播关闭消息  
  
1.  从命令提示符输入以下命令：  
  
     **net send /users "message"**  
  
     **/users** 选项指定将消息发送给已连接到服务器的所有用户  
  
> [!NOTE]  
>  **net send** 命令要求在发送和接收计算机上同时运行信使服务。 该 Messenger 服务默认情况下在 Windows Server 2003 上被禁用。 有关 **net send**的信息，请参阅 Windows 文档。  
  
 在网络上，可能更适合通过电子邮件或电话与用户联系。 若要确定当前哪些用户连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]，请使用活动监视器。 有关活动监视器的信息，请参阅[活动监视器](../../relational-databases/performance-monitor/activity-monitor.md) 和[打开活动监视器 (SQL Server Management Studio)](../../relational-databases/performance-monitor/open-activity-monitor-sql-server-management-studio.md)。  
  
## <a name="see-also"></a>另请参阅  
 [启动、停止、暂停、继续、重新启动数据库引擎、SQL Server 代理或 SQL Server Browser 服务](../../database-engine/configure-windows/start-stop-pause-resume-restart-sql-server-services.md)  
  
  
