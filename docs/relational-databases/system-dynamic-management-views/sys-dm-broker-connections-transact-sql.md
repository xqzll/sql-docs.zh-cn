---
title: sys.dm_broker_connections (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 01/08/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_broker_connections
- dm_broker_connections
- sys.dm_broker_connections_TSQL
- dm_broker_connections_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_broker_connections dynamic management view
ms.assetid: d9e20433-67fe-4fcc-80e3-b94335b2daef
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 95acff9d1b80560294758045c449c1c6c6790c27
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "62759995"
---
# <a name="sysdmbrokerconnections-transact-sql"></a>sys.dm_broker_connections (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  为每个 [!INCLUDE[ssSB](../../includes/sssb-md.md)] 网络连接返回一行。 下表提供了详细信息：  
  
|列名|数据类型|Description|  
|-----------------|---------------|-----------------|  
|**connection_id**|**uniqueidentifier**|连接的标识符。 可以为 NULL。|  
|**transport_stream_id**|**uniqueidentifier**|标识符的[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]此连接用于 TCP/IP 通信的网络接口 (SNI) 连接。 可以为 NULL。|  
|State |**smallint**|连接的当前状态。 可以为 NULL。 可能的值：<br /><br /> 1 = NEW<br /><br /> 2 = CONNECTING<br /><br /> 3 = CONNECTED<br /><br /> 4 = LOGGED_IN<br /><br /> 5 = 已关闭|  
|**state_desc**|**nvarchar(60)**|连接的当前状态。 可以为 NULL。 可能的值：<br /><br /> NEW<br /><br /> CONNECTING<br /><br /> CONNECTED<br /><br /> LOGGED_IN<br /><br /> CLOSED|  
|**connect_time**|**datetime**|打开连接的日期和时间。 可以为 NULL。|  
|**login_time**|**datetime**|连接登录成功的日期和时间。 可以为 NULL。|  
|**authentication_method**|**nvarchar(128)**|Windows 身份验证方法的名称，如 NTLM 或 KERBEROS。 该值由 Windows 提供。 可以为 NULL。|  
|**principal_name**|**nvarchar(128)**|验证其连接权限的登录的名称。 对于 Windows 身份验证，此值为远程用户名。 对于证书身份验证，该值为证书所有者。 可以为 NULL。|  
|**remote_user_name**|**nvarchar(128)**|Windows 身份验证所使用的来自其他数据库的对等方用户名。 可以为 NULL。|  
|**last_activity_time**|**datetime**|上次使用连接发送或接收信息的日期和时间。 可以为 NULL。|  
|**is_accept**|**bit**|指示连接是否源自远程端。 可以为 NULL。<br /><br /> 1 = 连接是从远程实例接受的请求。<br /><br /> 0 = 连接由本地实例启动。|  
|**login_state**|**smallint**|此连接的登录进程状态。 可能的值：<br /><br /> 0 = INITIAL<br /><br /> 1 = WAIT LOGIN NEGOTIATE<br /><br /> 2 = ONE ISC<br /><br /> 3 = ONE ASC<br /><br /> 4 = TWO ISC<br /><br /> 5 = TWO ASC<br /><br /> 6 = WAIT ISC Confirm<br /><br /> 7 = WAIT ASC Confirm<br /><br /> 8 = WAIT REJECT<br /><br /> 9 = WAIT PRE-MASTER SECRET<br /><br /> 10 = WAIT VALIDATION<br /><br /> 11 = WAIT ARBITRATION<br /><br /> 12 = 联机<br /><br /> 13 = ERROR|  
|**login_state_desc**|**nvarchar(60)**|远程计算机的当前登录状态。 可能的值：<br /><br /> 连接握手正在初始化。<br /><br /> 连接握手正在等待“登录协商”消息。<br /><br /> 连接握手已初始化并发送了用于身份验证的安全上下文。<br /><br /> 连接握手已收到并接受用于身份验证的安全上下文。<br /><br /> 连接握手已初始化并发送了用于身份验证的安全上下文。 提供可用于对对等方进行身份验证的可选机制。<br /><br /> 连接握手已收到并发送了用于身份验证的已接受安全上下文。 提供可用于对对等方进行身份验证的可选机制。<br /><br /> 连接握手正在等待“初始化安全上下文确认”消息。<br /><br /> 连接握手正在等待“接受安全上下文确认”消息。<br /><br /> 连接握手正在等待失败的身份验证的 SSPI 拒绝消息。<br /><br /> 连接握手正在等待“预主密钥”消息。<br /><br /> 连接握手正在等待“验证”消息。<br /><br /> 连接握手正在等待“仲裁”消息。<br /><br /> 连接握手已完成，准备进行消息交换。<br /><br /> 连接错误。|  
|**peer_certificate_id**|**int**|远程实例用来进行身份验证的证书的本地对象 ID。 该证书的所有者必须对 [!INCLUDE[ssSB](../../includes/sssb-md.md)] 端点拥有 CONNECT 权限。 可以为 NULL。|  
|**encryption_algorithm**|**smallint**|用于此连接的加密算法。 可以为 NULL。 可能的值：<br /><br /> **值&#124;说明&#124;的相应 DDL 选项**<br /><br /> 0 &#124; none&#124;已禁用<br /><br /> 1 &#124; SIGNING ONLY<br /><br /> 2 &#124; AES、 RC4&#124;需要&#124;所需的算法 RC4}<br /><br /> 3 &#124; AES&#124;所需的算法 AES<br /><br /> **注意：** RC4 算法仅用于支持向后兼容性。 仅当数据库兼容级别为 90 或 100 时，才能使用 RC4 或 RC4_128 对新材料进行加密。 （建议不要使用。）而是使用一种较新的算法，如 AES 算法之一。 在 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 和更高版本中，可以在任何兼容性级别对使用 RC4 或 RC4_128 加密的材料进行解密。|  
|**encryption_algorithm_desc**|**nvarchar(60)**|加密算法的文本表示形式。 可以为 NULL。 可能的值：<br /><br /> **说明&#124;的相应 DDL 选项**<br /><br /> NONE &#124; Disabled<br /><br /> RC4 &#124; {所需&#124;所需算法 RC4}<br /><br /> AES&#124;所需算法 AES<br /><br /> 无、 RC4 &#124; {支持&#124;支持算法 RC4}<br /><br /> 无、 AES&#124;支持算法 RC4<br /><br /> RC4、 AES&#124;所需算法 RC4 AES<br /><br /> AES、 RC4&#124;所需算法 AES RC4<br /><br /> 无、 RC4 AES&#124;支持算法 RC4 AES<br /><br /> 无、 AES RC4&#124;支持算法 AES RC4|  
|**receives_posted**|**smallint**|尚未针对此连接完成的异步网络接收数。 可以为 NULL。|  
|**is_receive_flow_controlled**|**bit**|网络接收是否由于流控制（因为网络忙）而推迟。 可以为 NULL。<br /><br /> 1 = True|  
|**sends_posted**|**smallint**|尚未针对此连接完成的异步网络发送数。 可以为 NULL。|  
|**is_send_flow_controlled**|**bit**|网络发送是否由于网络流控制（因为网络忙）而推迟。 可以为 NULL。<br /><br /> 1 = True|  
|**total_bytes_sent**|**bigint**|此连接发送的字节总数。 可以为 NULL。|  
|**total_bytes_received**|**bigint**|此连接接收的字节总数。 可以为 NULL。|  
|**total_fragments_sent**|**bigint**|此连接发送的 [!INCLUDE[ssSB](../../includes/sssb-md.md)] 消息片段总数。 可以为 NULL。|  
|**total_fragments_received**|**bigint**|此连接接收的 [!INCLUDE[ssSB](../../includes/sssb-md.md)] 消息片段总数。 可以为 NULL。|  
|**total_sends**|**bigint**|此连接发出的网络发送请求总数。 可以为 NULL。|  
|**total_receives**|**bigint**|此连接发出的请求接收的网络的总数。 可以为 NULL。|  
|**peer_arbitration_id**|**uniqueidentifier**|端点的内部标识符。 可以为 NULL。|  
  
## <a name="permissions"></a>权限  
 要求具有服务器的 VIEW SERVER STATE 权限。  
  
## <a name="physical-joins"></a>物理联接  
 ![Sys.dm_broker_connections 的联接](../../relational-databases/system-dynamic-management-views/media/join-dm-broker-connections-1.gif "sys.dm_broker_connections 的联接")  
  
## <a name="relationship-cardinalities"></a>关系基数  
  
|From|若要|关系|  
|----------|--------|------------------|  
|**dm_broker_connections.connection_id**|**dm_exec_connections.connection_id**|一对一|  
  
## <a name="see-also"></a>请参阅  
 [动态管理视图和函数 (Transact-SQL)](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [与 Service Broker 有关的动态管理视图 (Transact-SQL)](../../relational-databases/system-dynamic-management-views/service-broker-related-dynamic-management-views-transact-sql.md)  
  
  

