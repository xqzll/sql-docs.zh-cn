---
title: 从 SSMS 连接到任何 SQL Server 组件 | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- connections [SQL Server], SQL Server Management Studio
- saving connections
- components [SQL Server], connections
- SQL Server Management Studio [SQL Server], connections
ms.assetid: 5eeb41bd-b25b-4d3b-a005-a7d9e4b5978e
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 8ce85a190288adeb02f19d71a76cc5a0d6c8605b
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "65102703"
---
# <a name="connect-to-any-sql-server-component-from-sql-server-management-studio"></a>从 SQL Server Management Studio 连接到任何 SQL Server 组件
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 提供了管理每个 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]组件的功能。 使用 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 可以连接到：  
  
-   [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion_md.md)]实例。  
  
-   [!INCLUDE[ssASnoversion](../../includes/ssasnoversion_md.md)]组件的功能。  
  
-   [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]组件的功能。  
  
-   [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]组件的功能。  
  
虽然 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 允许您在使用查询时无需先建立与数据源的连接，但其他多数任务需要一个连接。 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 提供了“连接到服务器”  对话框，可用于配置到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 组件的连接属性。 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 启动时，将打开“连接到服务器”  对话框，并提示你连接到服务器。 “连接到服务器”  对话框会保留上次使用的连接设置。  
  
> [!NOTE]  
> 可以关闭此功能，以免自动启动某个连接。 有关详细信息，请参阅 [Database Engine Service Startup Options](../../database-engine/configure-windows/database-engine-service-startup-options.md)。  
  
## <a name="saving-connections"></a>保存连接  
可以在已注册的服务器中将连接保存到特定服务器，也可以在解决方案资源管理器中将连接保存到项目中。  
  
### <a name="saving-connections-in-registered-servers"></a>在已注册的服务器中保存连接  
注册服务器时， [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 会在已注册的服务器中保存连接信息。 若要连接到某个已注册的服务器，可在已注册的服务器中双击该服务器名称。 对象资源管理器随即会打开一个到该服务器的连接。  
  
### <a name="saving-connections-in-solution-explorer"></a>在解决方案资源管理器中保存连接  
使用解决方案资源管理器，可以在项目中存储相关的查询、脚本、连接和其他关联的信息。 每个脚本项目都包含一个名为“连接”  的节点，可以在其中保存一个或多个连接。 若要添加连接，可右键单击“连接”  ，再单击“新建连接”  。 若要访问已保存的连接，可展开“连接”  ，然后双击该连接。 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 随即会打开一个与该连接关联的查询窗口。 保存后，脚本会保留其与特定连接的关联。  
  
## <a name="see-also"></a>另请参阅  
[使用 SQL Server Management Studio](../../ssms/use-sql-server-management-studio.md)  
[对象资源管理器](../../ssms/object/object-explorer.md)  
  
