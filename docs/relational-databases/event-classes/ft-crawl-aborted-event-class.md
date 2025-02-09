---
title: FT:Crawl Aborted 事件类 | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- Crawl Aborted event class
ms.assetid: eead8ea6-5051-4689-ab30-4dfbfda01fb9
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 8b8455ffcd3cc3274ae6e7fffd104826263cb730
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "62724560"
---
# <a name="ftcrawl-aborted-event-class"></a>FT:Crawl Aborted 事件类
[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]
  **FT:Crawl Aborted** 事件类指示全文爬网过程中遇到异常。 该错误通常导致全文爬网停止。 有关更多详细的错误信息，请查看 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 事件日志或爬网日志。  
  
## <a name="ftcrawl-aborted-event-class-data-columns"></a>FT:Crawl Aborted 事件类的数据列  
  
|数据列名称|数据类型|描述|列 ID|可筛选|  
|----------------------|---------------|-----------------|---------------|----------------|  
|**DatabaseID**|**int**|正在运行全文爬网的数据库的 ID。 可使用 DB_ID 函数来确定数据库的值。|3|是|  
|**错误**|**int**|给定事件的错误号。 通常是 **sysmessages** 表中存储的错误号。|31|是|  
|**EventClass**|**int**|事件类型 = 157。|27|否|  
|**EventSequence**|**int**|给定事件在请求中的顺序。|51|否|  
|**IsSystem**|**int**|指示事件是发生在系统进程中还是发生在用户进程中。 1 = 系统，0 = 用户。|60|是|  
|**Exchange Spill**|**int**|发生错误时系统分配给正在运行全文爬网的对象的 ID。|22|是|  
|**SessionLoginName**|**nvarchar**|发起会话的用户的登录名。 例如，如果您使用 Login1 连接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，再以 Login2 的身份执行语句，则 **SessionLoginName** 将显示 Login1，而 **LoginName** 将显示 Login2。 此列将同时显示 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 登录名和 Windows 登录名。|64|是|  
|**SPID**|**int**|发生该事件的会话的 ID。|12|是|  
|**StartTime**|**datetime**|该事件（如果存在）的启动时间。|14|是|  
|**State**|**int**|等同于错误状态代码。|30|是|  
|**TransactionID**|**bigint**|系统分配的事务 ID。|4|是|  
  
## <a name="see-also"></a>另请参阅  
 [sp_trace_setevent (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql.md)  
  
  
