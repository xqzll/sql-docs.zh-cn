---
title: CONNECTIONPROPERTY (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/24/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- CONNECTIONPROPERTY_TSQL
- CONNECTIONPROPERTY
dev_langs:
- TSQL
helpviewer_keywords:
- CONNECTIONPROPERTY statement
ms.assetid: 6bd9ccae-af77-4a05-b97f-f8ab41cfde42
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 35d066a88955d3d47bb8e9e552dde689bee3ae47
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "65948131"
---
# <a name="connectionproperty-transact-sql"></a>CONNECTIONPROPERTY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

对于进入服务器的请求，此函数会返回有关支持该请求的唯一连接的连接属性的信息。
  
![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "主题链接图标") [TRANSACT-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>语法  
  
```sql
CONNECTIONPROPERTY ( property )  
```  
  
## <a name="arguments"></a>参数  
property   
连接的属性。 property 可以为下列值之一  ：
  
|ReplTest1|数据类型|描述|  
|---|---|---|
|net_transport|**nvarchar(40)**|返回该连接使用的物理传输协议。 此值不可以为 null。 可能的返回值为：<br /><br /> **HTTP**<br /> **命名管道**<br /> **会话**<br /> **共享内存**<br /> **SSL**<br /> **TCP**<br /><br /> 和<br /><br /> **VIA**<br /><br /> 注意：如果连接启用了多个活动结果集 (MARS)，并且启用了连接池，则始终返回 Session  。|  
|protocol_type|**nvarchar(40)**|返回负载协议类型。 此参数当前可区分 TDS (TSQL) 和 SOAP。 可以为 Null。|  
|auth_scheme|**nvarchar(40)**|返回连接 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 身份验证方案。 身份验证方案为 Windows 身份验证（NTLM、KERBEROS、DIGEST、BASIC、NEGOTIATE）或 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 身份验证。 不可为 null。|  
|local_net_address|**varchar(48)**|返回作为该特定连接的目标的服务器的 IP 地址。 仅适用于使用 TCP 传输提供程序的连接。 可以为 Null。|  
|local_tcp_port|**int**|如果连接是使用 TCP 传输的连接，则返回作为该连接的目标的服务器 TCP 端口。 可以为 Null。|  
|client_net_address|**varchar(48)**|请求尝试连接到该服务器的客户端的地址。 可以为 Null。|  
|physical_net_transport|**nvarchar(40)**|返回该连接使用的物理传输协议。 如果连接启用了多个活动结果集 (MARS)，则返回准确结果。|  
|\<任何其他字符串>||对无效输入返回 NULL。|  
  
## <a name="remarks"></a>Remarks  
local_net_address 和 local_tcp_port 在 [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)] 中返回 NULL   。
  
返回的值匹配为 [sys.dm_exec_connections](../../relational-databases/system-dynamic-management-views/sys-dm-exec-connections-transact-sql.md) 动态管理视图中的相应列显示的选项。 例如：
  
```sql
SELECT   
ConnectionProperty('net_transport') AS 'Net transport',   
ConnectionProperty('protocol_type') AS 'Protocol type';  
```  
  
## <a name="see-also"></a>另请参阅
[sys.dm_exec_sessions (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sessions-transact-sql.md)  
[sys.dm_exec_requests (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md)
  
  
