---
title: MSSQLSERVER_1204 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 1204 (Database Engine error)
ms.assetid: de6ece78-79de-484d-9224-ca0f7645815f
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: b334eda517f7f4a2283f3ac24f0dd0bb1a84b846
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "63048362"
---
# <a name="mssqlserver1204"></a>MSSQLSERVER_1204
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>详细信息  
  
|||  
|-|-|  
|产品名称|SQL Server|  
|事件 ID|1204|  
|事件源|MSSQLSERVER|  
|组件|SQLEngine|  
|符号名称|LK_OUTOF|  
|消息正文|SQL Server 数据库引擎的实例此时无法获得 LOCK 资源。 请在活动用户较少时重新运行该语句。 请询问数据库管理员，检查此实例的锁定和内存配置，或检查是否有长时间运行的事务。|  
  
## <a name="explanation"></a>解释  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 无法获得锁资源。 这可能是由以下任一原因导致的：  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 无法从操作系统分配更多的内存，因为其他进程正在使用它，或者因为服务器在配置了“最大服务器内存”  选项的情况下运行。  
  
-   锁管理器使用的内存不会超过可供 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 使用的内存的 60%。  
  
## <a name="user-action"></a>用户操作  
如果您怀疑 SQL Server 无法分配足够的内存，请尝试执行以下操作：  
  
-   如果除 SQL Server 外的应用程序正在占用资源，请尝试停止这些应用程序，或者考虑在单独的服务器上运行它们。 这样其他进程将释放并删除内存供 SQL Server 使用。  
  
-   如果已配置 max server memory，请增大其设置。  
  
如果您怀疑锁管理器使用了最大可用内存，请识别持有最多锁的事务并终止它。 以下脚本将识别持有最多锁的事务：  
  
```  
SELECT request_session_id, COUNT (*) num_locks  
FROM sys.dm_tran_locks  
GROUP BY request_session_id   
ORDER BY count (*) DESC  
```  
  
采用最大会话 id，并使用 KILL 命令终止它。  
  
