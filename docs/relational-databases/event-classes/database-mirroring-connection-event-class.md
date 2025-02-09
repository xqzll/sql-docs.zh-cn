---
title: Database Mirroring Connection 事件类 | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
ms.assetid: b59dccc9-f40d-4c82-aa35-ac40acea86ff
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: b5e73000ec424f6880440a8aa2a23659b92582b4
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "62672157"
---
# <a name="database-mirroring-connection-event-class"></a>数据库镜像连接事件类
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 生成 **数据库镜像连接** 事件以便报告数据库镜像管理的传输连接的状态。  
  
## <a name="database-mirroringconnection-event-class-data-columns"></a>Database Mirroring:Connection 事件类的数据列  
  
|数据列|类型|描述|列号|可筛选|  
|-----------------|----------|-----------------|-------------------|----------------|  
|**ApplicationName**|**nvarchar**|客户端应用程序的名称，该客户端应用程序创建了指向 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]实例的连接。 此列由应用程序传递的值填充，而不是由所显示的程序名填充。|10|是|  
|**ClientProcessID**|**int**|由主机分配给正在运行客户端应用程序的进程的 ID。 如果客户端提供了客户端进程 ID，则填充此数据列。|9|是|  
|**DatabaseID**|**int**|由 USE *database* 语句指定的数据库的 ID；如果未对给定实例发出 USE *database*语句，则为默认数据库的 ID。 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 数据列而且服务器可用，则 **ServerName** 将显示数据库名。 可使用 **DB_ID** 函数来确定数据库的值。|3|是|  
|**错误**|**int**|事件中文本的 **sys.messages** 的消息 ID 号。 如果此事件报告错误，即是 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 错误号。|31|否|  
|**EventClass**|**int**|捕获的事件类的类型。 对于 **数据库镜像连接** 始终为 **151**。|27|否|  
|**EventSequence**|**int**|此事件的序列号。|51|否|  
|**EventSubClass**|**nvarchar**|此连接的连接状态。 对于此事件，子类是以下值之一：<br /><br /> **Connecting**。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 正在启动传输连接。<br /><br /> **Connected**。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 已建立传输连接。<br /><br /> **Connect Failed**。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 建立传输连接失败。<br /><br /> **Closing**。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 正在关闭传输连接。<br /><br /> **Closed**。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 已关闭传输连接。<br /><br /> **Accept**。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 已接受来自另一个实例的传输连接。<br /><br /> **Send IO Error**。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 在发送消息时遇到了传输错误。<br /><br /> **Receive IO Error**。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 在接收消息时遇到了传输错误。|21|是|  
|**GUID**|**uniqueidentifier**|此连接的端点 ID。|54|否|  
|**HostName**|**nvarchar**|正在运行客户端程序的计算机的名称。 如果客户端提供了主机名，则填充此数据列。 若要确定主机名，请使用 **HOST_NAME** 函数。|8|是|  
|**IntegerData**|**int**|已关闭此连接的次数。|25|是|  
|**IsSystem**|**int**|指示事件是发生在系统进程中还是发生在用户进程中。<br /><br /> 0 = 用户<br /><br /> 1 = 系统|60|否|  
|**LoginSid**|**图像**|已登录用户的安全标识号 (SID)。 服务器中的每个登录名都具有唯一的 SID。|41|是|  
|**NTDomainName**|**nvarchar**|用户所属的 Windows 域。|7|是|  
|**NTUserName**|**nvarchar**|拥有生成此事件的连接的用户的名称。|6|是|  
|**ObjectName**|**nvarchar**|对话的会话句柄。|34|否|  
|**ServerName**|**nvarchar**|所跟踪的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例的名称。|26|否|  
|**SPID**|**int**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 为客户端所关联的进程分配的服务器进程 ID。|12|是|  
|**StartTime**|**datetime**|事件（如果有）的开始时间。|14|是|  
|**TextData**|**ntext**|与事件相关的错误消息的文本。 对于不报告错误的事件，此字段为空。 错误消息可以是 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 错误消息，也可以是 Windows 错误消息。|1|是|  
|**TransactionID**|**bigint**|系统为事务分配的 ID。|4|否|  
  
  
