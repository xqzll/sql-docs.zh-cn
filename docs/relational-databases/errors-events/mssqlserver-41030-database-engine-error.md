---
title: MSSQLSERVER_41030 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 41030 (Database Engine error)
ms.assetid: c85341ae-0fbf-42ae-9275-4cfe678238f0
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 29b328581b1a7c8e9bfc0bbcc3cb73b945ffccd8
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "63028926"
---
# <a name="mssqlserver41030"></a>MSSQLSERVER_41030
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>详细信息  
  
|||  
|-|-|  
|产品名称|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|事件 ID|41030|  
|事件源|MSSQLSERVER|  
|组件|SQLEngine|  
|符号名称|OPEN_CLUSTER_SUB_KEY|  
|消息正文|无法打开 Windows Server 故障转移群集注册表子项“%.*ls”（错误代码 %d）。  父键为群集根键。  WSFC 服务可能未在运行或是在其当前状态下无法访问，或指定的参数无效。 如果已删除对应的可用性组，则会出现此错误。 有关此错误代码的信息，请参阅 Windows 开发文档中的“系统错误代码”。|  
  
## <a name="explanation"></a>解释  
如果 WSFC 群集损坏，则将删除与 [!INCLUDE[ssHADR](../../includes/sshadr-md.md)]相关的所有注册表项。  
  
## <a name="user-action"></a>用户操作  
重新创建 WSFC 群集之后，请在其中 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的实例启用了 AlwaysOn 的每个群集节点上禁用后重新启用 AlwaysOn。 您可使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 配置管理器执行此任务。  
  
## <a name="see-also"></a>另请参阅  
[启用和禁用 AlwaysOn 可用性组 (SQL Server)](~/database-engine/availability-groups/windows/enable-and-disable-always-on-availability-groups-sql-server.md)  
[Windows Server 故障转移群集 (WSFC) 与 SQL Server](~/sql-server/failover-clusters/windows/windows-server-failover-clustering-wsfc-with-sql-server.md)  
  
