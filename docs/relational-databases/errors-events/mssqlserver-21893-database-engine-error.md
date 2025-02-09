---
title: MSSQLSERVER_21893 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 21893 (Database Engine error)
ms.assetid: 1ab1195a-fe2a-4e06-b871-b177b6bea1fe
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 100edf017c864567cd8f7046ff4a7a76796aaf41
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "62662706"
---
# <a name="mssqlserver21893"></a>MSSQLSERVER_21893
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>详细信息  
  
|||  
|-|-|  
|产品名称|SQL Server|  
|事件 ID|21893|  
|事件源|MSSQLSERVER|  
|组件|SQLEngine|  
|符号名称|SQLErrorNum21893|  
|消息正文|订阅服务器 (%s)（属于原始发布服务器“%s”）在重定向的发布服务器“%s”中不显示为远程服务器。 在重定向的发布服务器上运行 sp_addlinkedserver  ，以将这些订阅服务器添加为远程服务器。|  
  
## <a name="explanation"></a>解释  
在远程服务器上，**sp_validate_redirected_publisher** 使用发布服务器数据库的订阅元数据表来确定其关联的订阅服务器，并验证在订阅服务器的 master.dbo.sysservers 中是否存在关联的条目。 如果任何标识的订阅服务器不存在，则会返回此错误。  
  
该错误不被视为严重错误。 遇到该错误的代理将此错误记录为信息性消息，但不会终止，因为在新发布服务器上无法具有适当的订阅服务器条目对复制的影响很有限。 如果在 sysservers 中没有相应的订阅服务器条目，则在通过 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 执行时，某些订阅管理活动可能会失败。 但是，可以通过显式执行管理存储过程成功地执行这些相同的活动。  
  
## <a name="user-action"></a>用户操作  
在重定向的发布服务器上对每个标识的订阅服务器运行 **sp_addlinkedserver**，以将这些订阅服务器添加为远程服务器。 然后，运行 **sp_serveroption** 以设置该服务器的订阅服务器位。  
  
