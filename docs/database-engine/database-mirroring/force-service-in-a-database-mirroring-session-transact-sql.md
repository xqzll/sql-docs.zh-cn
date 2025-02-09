---
title: 在数据库镜像会话中强制服务 (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- forced service [SQL Server]
- database mirroring [SQL Server], forcing service
ms.assetid: 8b6ffe77-35f3-4e2a-a658-8a38a8e1c794
author: MikeRayMSFT
ms.author: mikeray
manager: jroth
ms.openlocfilehash: baa5a093e7ade403eb6786b771b10c72c2bb89a4
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "66795440"
---
# <a name="force-service-in-a-database-mirroring-session-transact-sql"></a>在数据库镜像会话中强制服务 (Transact-SQL)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  在高性能模式和不带自动故障转移功能的高安全性模式下，如果主体服务器失败而镜像服务器可用，则数据库所有者可以强制将服务故障转移到镜像数据库（可能造成数据丢失），从而使数据库可用。 此选项仅在以下情况中可用：  
  
-   主体服务器已关闭。  
  
-   WITNESS 设置为 OFF 或连接到镜像服务器。  
  
> [!CAUTION]  
>  严格讲来，强制服务是一种灾难恢复方法。 强制服务可能会导致一些数据丢失。 因此，只有在为了立即恢复数据库服务而不惜丢失某些数据时，才可强制执行服务。 如果强制服务面临丢失重要数据的风险，则建议您停止镜像并手动重新同步数据库。 有关强制服务所面临风险的详细信息，请参阅 [Database Mirroring Operating Modes](../../database-engine/database-mirroring/database-mirroring-operating-modes.md)。  
  
 强制服务会挂起会话并启动新的恢复分叉。 强制服务的结果相当于删除镜像并恢复以前的主体数据库。 但是，强制服务便于在恢复镜像时重新同步数据库（可能造成数据丢失）。  
  
### <a name="to-force-service-in-a-database-mirroring-session"></a>在数据库镜像会话中强制执行服务  
  
1.  连接到镜像服务器。  
  
2.  发出以下语句：  
  
     ALTER DATABASE *<database_name>* SET PARTNER FORCE_SERVICE_ALLOW_DATA_LOSS  
  
     其中， *<database_name>* 为镜像数据库。  
  
     镜像服务器将立即转换为主体服务器，并且镜像挂起。  
  
## <a name="see-also"></a>另请参阅  
 [ALTER DATABASE (Transact-SQL)](../../t-sql/statements/alter-database-transact-sql.md)   
 [Database Mirroring Operating Modes](../../database-engine/database-mirroring/database-mirroring-operating-modes.md)  
  
  
