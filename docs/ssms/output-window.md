---
title: SSMS 输出窗口 | Microsoft Docs
ms.custom: ''
ms.date: 08/09/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- Output Window [SQL Server Management Studio]
- Activity Monitor [SQL Server Management Studio]
- Object Explorer [SQL Server Management Studio]
ms.assetid: a2ce1a07-b4e2-471c-87d2-b8de5e6c6864
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: a070121a50f056ad293bc4aec6af305587a9b6c3
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "65095674"
---
# <a name="output-window-in-sql-server-management-studio"></a>SQL Server Management Studio 中的输出窗口
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
可从视图菜单或使用组合键 Ctrl+Alt+O 打开输出窗口。 可用的输出通道有多个。

下表概述与各输出通道相关联的消息类型。

|Channel|描述|
|-----------|---------------|  
|遥测 |遥测是由 Microsoft 收集的[匿名功能使用情况数据](sql-server-management-studio-ssms.md)流。 对于自己的保留 SSMS 使用情况的记录，这些事件非常有用。 它能帮助标识展开的对象资源管理器节点以及输出窗口处于打开状态时在 SSMS 会话期间运行的命令。|
|**对象资源管理器**|此通道将输出在对象资源管理器中展开节点所需的 SQL 查询的查询文本和运行时间。 每个查询记录一个“开始查询”和一个“结束查询”事件。 每个事件都具有一个时间戳，以及与正在查询的实体相关联的 URN。 [URN](https://technet.microsoft.com/library/microsoft.sqlserver.management.smo.urn(v=sql.90).aspx) 即基础 SQL 管理对象，由 XPath 样式的层次结构组成。 例如，一个表位于“MyServer”服务器上的“Db”数据库中，表名为“Table1”，其 URN 则为“Server[@Name='MyServer']/Database[@Name='Db']/Table[/@Name='Table1']”。 在对象资源管理器中展开一个节点，可执行多个具有不同参数的此类查询。 “结束查询”事件将包含查询的运行时间和 TSQL 文本。 在对象资源管理器展开特定节点的速度似乎异常缓慢的情况下，可能会发现此查询数据对于服务器性能分析很有用。 注意：对象资源管理器中并非所有节点都会在展开时提供此级别的查询详细信息  。|
|**活动监视器**|为服务器[打开活动监视器](https://docs.microsoft.com/sql/relational-databases/performance-monitor/activity-monitor)时，此通道将启动。 此数据流包含的事件显示每个查询的部分查询文本和时间戳、错误消息、因连接问题而导致监视器暂停的通知。 如果活动监视器空闲或无法更新，请检查此输出通道，获取详细信息。|





