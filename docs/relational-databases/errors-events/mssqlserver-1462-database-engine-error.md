---
title: MSSQLSERVER_1462 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 1462 (Database Engine error)
ms.assetid: 680e9c1c-a9d6-4765-b601-956d0a83324c
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 185a7d78f10656dc932259fb1098570190941afa
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "62859341"
---
# <a name="mssqlserver1462"></a>MSSQLSERVER_1462
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>详细信息  
  
|||  
|-|-|  
|产品名称|SQL Server|  
|事件 ID|1462|  
|事件源|MSSQLSERVER|  
|组件|SQLEngine|  
|符号名称|DBM_DISABLED_DUE_TO_FAILED_REDO|  
|消息正文|由于重做操作失败，数据库镜像被禁用。 无法恢复。|  
  
## <a name="explanation"></a>解释  
数据库镜像无法对镜像重做日志记录。  
  
### <a name="possible-causes"></a>可能的原因  
最可能的原因是，添加文件操作在主体数据库上完成，但由于主体服务器和镜像服务器上的文件名和目录结构不同而使该操作在镜像数据库上失败。  
  
## <a name="user-action"></a>用户操作  
查看 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 错误日志，了解产生此错误的原因。 尝试解决此原因并恢复对数据库的镜像。  
  
## <a name="see-also"></a>另请参阅  
[数据库镜像配置故障排除 (SQL Server)](~/database-engine/database-mirroring/troubleshoot-database-mirroring-configuration-sql-server.md)  
  
