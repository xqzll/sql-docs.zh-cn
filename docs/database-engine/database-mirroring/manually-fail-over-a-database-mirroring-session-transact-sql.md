---
title: 手动故障转移数据库镜像会话 (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- failover [SQL Server], database mirroring
- manual failover [SQL Server]
- database mirroring [SQL Server], failover
ms.assetid: 36218d61-b5f5-4194-905a-608e0e903db4
author: MikeRayMSFT
ms.author: mikeray
manager: jroth
ms.openlocfilehash: cff69cccd05d48df6affeca17a6799f82e26e1f5
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "66795398"
---
# <a name="manually-fail-over-a-database-mirroring-session-transact-sql"></a>手动故障转移数据库镜像会话 (Transact-SQL)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  同步镜像数据库时（即数据库处于 SYNCHRONIZED 状态时），数据库所有者可以启动到镜像服务器的手动故障转移。 手动故障转移只能从主体服务器启动。  
  
### <a name="to-manually-fail-over-a-database-mirroring-session"></a>手动故障转移数据库镜像会话  
  
1.  连接到主体服务器。  
  
2.  将数据库上下文设置为 **master** 数据库：  
  
     **USE master;**  
  
3.  在主体服务器上执行下列语句：  
  
     [ALTER DATABASE](../../t-sql/statements/alter-database-transact-sql-database-mirroring.md) *database_name* SET PARTNER FAILOVER，其中 *database_name* 是镜像数据库。  
  
     此语句将立即启动从镜像服务器到主体角色的转换。  
  
 在前一主体上，客户端断开了与数据库的连接，并且未提交的事务将回滚。  
  
> [!NOTE]  
>  当发生故障转移时，使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 分布式事务处理协调器准备就绪但尚未提交的事务被认为在数据库故障转移后已中止。  
  
## <a name="see-also"></a>另请参阅  
 [ALTER DATABASE 数据库镜像 (Transact-SQL)](../../t-sql/statements/alter-database-transact-sql-database-mirroring.md)   
 [手动故障转移数据库镜像会话 (SQL Server Management Studio)](../../database-engine/database-mirroring/manually-fail-over-a-database-mirroring-session-sql-server-management-studio.md)   
 [数据库镜像会话期间的角色切换 (SQL Server)](../../database-engine/database-mirroring/role-switching-during-a-database-mirroring-session-sql-server.md)  
  
  
