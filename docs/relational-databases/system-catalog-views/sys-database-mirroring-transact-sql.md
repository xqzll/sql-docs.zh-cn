---
title: sys.database_mirroring (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.database_mirroring
- database_mirroring
- sys.database_mirroring_TSQL
- database_mirroring_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.database_mirroring catalog view
ms.assetid: 480de2b0-2c16-497d-a6a3-bf7f52a7c9a0
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: bea7712fd4efa1934117937a5168843d727d0dc6
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "62693914"
---
# <a name="sysdatabasemirroring-transact-sql"></a>sys.database_mirroring (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例中的每个数据库占一行。 如果数据库未处于联机状态或未启用数据库镜像，除 database_id 的所有列的值将为 NULL。  
  
 若要查看 master 或 tempdb 以外的数据库行，必须是数据库所有者或至少具有 ALTER ANY DATABASE 或 VIEW ANY DATABASE 服务器级权限，或者在 master 数据库中的 CREATE DATABASE 权限。 若要查看镜像数据库的非 NULL 值，您必须**sysadmin**固定的服务器角色。  
  
> [!NOTE]  
>  如果数据库不参与镜像，则所有带有"mirroring_"前缀的列将为 NULL。  
  
|列名|数据类型|Description|  
|-----------------|---------------|-----------------|  
|**database_id**|**int**|数据库 ID。 在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例中是唯一的。|  
|**mirroring_guid**|**uniqueidentifier**|镜像合作关系的 ID。<br /><br /> NULL = 数据库不可访问或未镜像。<br /><br /> 注意：如果数据库不参与镜像，则所有带有"mirroring_"前缀的列将为 NULL。|  
|**mirroring_state**|**tinyint**|镜像数据库的状态和数据库镜像会话的状态。<br /><br /> 0 = 已挂起<br /><br /> 1 = 与其他伙伴断开<br /><br /> 2 = 正在同步<br /><br /> 3 = 挂起故障转移<br /><br /> 4 = 已同步<br /><br /> 5 = 伙伴未同步。 现在无法进行故障转移。<br /><br /> 6 = 伙伴已同步。 可以进行故障转移。 了解有关故障转移，请参阅要求[Database Mirroring Operating Modes](../../database-engine/database-mirroring/database-mirroring-operating-modes.md)。<br /><br /> NULL = 数据库不可访问或未镜像。|  
|**mirroring_state_desc**|**nvarchar(60)**|镜像数据库状态和数据库镜像会话状态的说明，可以是下列值之一：<br /><br /> DISCONNECTED<br /><br /> SYNCHRONIZED<br /><br /> SYNCHRONIZING<br /><br /> PENDING_FAILOVER<br /><br /> SUSPENDED<br /><br /> UNSYNCHRONIZED<br /><br /> SYNCHRONIZED<br /><br /> NULL<br /><br /> 有关详细信息，请参阅[镜像状态 (SQL Server)](../../database-engine/database-mirroring/mirroring-states-sql-server.md)。|  
|**mirroring_role**|**tinyint**|本地数据库当前在数据库镜像会话中扮演的角色。<br /><br /> 1 = 主体<br /><br /> 2 = 镜像<br /><br /> NULL = 数据库不可访问或未镜像。|  
|**mirroring_role_desc**|**nvarchar(60)**|本地数据库在镜像中的角色说明，可以是以下值之一：<br /><br /> PRINCIPAL<br /><br /> MIRROR|  
|**mirroring_role_sequence**|**int**|由于故障转移或强制服务，导致镜像伙伴在主体数据库角色和镜像数据库角色之间进行切换的次数。<br /><br /> NULL = 数据库不可访问或未镜像。|  
|**mirroring_safety_level**|**tinyint**|镜像数据库更新的安全设置：<br /><br /> 0 = 未知状态<br /><br /> 1 = 关闭 [异步]<br /><br /> 2 = 完全 [同步]<br /><br /> NULL = 数据库不可访问或未镜像。|  
|**mirroring_safety_level_desc**|**nvarchar(60)**|镜像数据库更新的事务安全设置，可以是下列值之一：<br /><br /> UNKNOWN<br /><br /> OFF<br /><br /> FULL<br /><br /> NULL|  
|**mirroring_safety_sequence**|**int**|将更改的序列号更新为事务安全级别。<br /><br /> NULL = 数据库不可访问或未镜像。|  
|**mirroring_partner_name**|**nvarchar(128)**|数据库镜像伙伴的服务器名称。<br /><br /> NULL = 数据库不可访问或未镜像。|  
|**mirroring_partner_instance**|**nvarchar(128)**|其他伙伴的实例名和计算机名称。 如果伙伴成为主体服务器，则客户端需要此信息以连接到该伙伴服务器。<br /><br /> NULL = 数据库不可访问或未镜像。|  
|**mirroring_witness_name**|**nvarchar(128)**|数据库镜像见证服务器的服务器名称。<br /><br /> NULL = 不存在见证服务器。|  
|mirroring_witness_state|**tinyint**|数据库的数据库镜像会话中的见证服务器状态，可以是下列值之一：<br /><br /> 0 = 未知<br /><br /> 1 = 已连接<br /><br /> 2 = 已断开<br /><br /> NULL = 见证服务器不存在，数据库未联机或未镜像。|  
|**mirroring_witness_state_desc**|**nvarchar(60)**|状态说明，可以是下列值之一：<br /><br /> UNKNOWN<br /><br /> CONNECTED<br /><br /> DISCONNECTED<br /><br /> NULL|  
|**mirroring_failover_lsn**|**numeric(25,0)**|保证将被镜像到两个伙伴服务器磁盘中的最新事务日志记录的日志序列号 (LSN)。 在故障转移后**mirroring_failover_lsn**由合作伙伴将它用作新的镜像服务器开始新的镜像数据库与新的主体数据库进行同步的对帐的点。|  
|**mirroring_connection_timeout**|**int**|镜像连接超时值（秒）。 这是等待伙伴或见证服务器回复的秒数，超过该时间后，伙伴或见证服务器将被视为不可用。 默认超时值为 10 秒。<br /><br /> NULL = 数据库不可访问或未镜像。|  
|**mirroring_redo_queue**|**int**|对镜像服务器重做的最大日志量。 如果 mirroring_redo_queue_type 将设置为 UNLIMITED，这是默认设置，此列将为 NULL。 如果数据库未联机，则该列也为 NULL。<br /><br /> 否则，该列包含最大日志量 (MB)。 如果达到最大值，则当镜像服务器也达到同一值时，日志将在主体服务器上临时停止。 此功能限制故障转移时间。<br /><br /> 有关详细信息，请参阅 [估计在角色切换期间服务的中断（数据库镜像）](../../database-engine/database-mirroring/estimate-the-interruption-of-service-during-role-switching-database-mirroring.md)。|  
|**mirroring_redo_queue_type**|**nvarchar(60)**|UNLIMITED 指示镜像不会禁止重做队列。 这是默认设置。<br /><br /> 以兆字节为单位的重做队列的最大大小 (MB)。 请注意，如果队列大小以 KB 或 GB 形式指定，则[!INCLUDE[ssDE](../../includes/ssde-md.md)]会将该值转换为 MB。<br /><br /> 如果数据库未联机，则该列为 NULL。|  
|**mirroring_end_of_log_lsn**|**numeric(25,0)**|已刷新到磁盘本地日志末尾。 这相当于强制写入的 LSN 从镜像服务器 (请参阅**mirroring_failover_lsn**列)。|  
|**mirroring_replication_lsn**|**numeric(25,0)**|可以发送复制的最大 LSN。|  
  
## <a name="permissions"></a>权限  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 有关详细信息，请参阅 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)。  
  
## <a name="see-also"></a>请参阅  
 [目录视图 (Transact-SQL)](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [ALTER DATABASE (Transact-SQL)](../../t-sql/statements/alter-database-transact-sql.md)   
 [sys.database_mirroring_witnesses (Transact-SQL)](../../relational-databases/system-catalog-views/database-mirroring-witness-catalog-views-sys-database-mirroring-witnesses.md)   
 [sys.database_mirroring_endpoints (Transact-SQL)](../../relational-databases/system-catalog-views/sys-database-mirroring-endpoints-transact-sql.md)   
 [数据库和文件目录视图 (Transact-SQL)](../../relational-databases/system-catalog-views/databases-and-files-catalog-views-transact-sql.md)   
 [查询 SQL Server 系统目录常见问题解答](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)  
  
  
