---
title: MSSQLSERVER_2546 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 2546 (Database Engine error)
ms.assetid: c8f0e1b4-c7c4-45f2-9221-746714172313
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 983c5536d08d9701fd301ace4ca8d2b5d7e76f71
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "63046398"
---
# <a name="mssqlserver2546"></a>MSSQLSERVER_2546
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>详细信息  
  
|||  
|-|-|  
|产品名称|SQL Server|  
|事件 ID|2546|  
|事件源|MSSQLSERVER|  
|组件|SQLEngine|  
|符号名称|DBCC_INDEX_MARKED_DISABLED|  
|消息正文|表 'OBJECT_NAME' 的索引 'INDEX_NAME' 已标记为禁用。 请重新生成该索引，以使之联机。|  
  
## <a name="explanation"></a>解释  
指定的索引已标记为离线或禁用。 因此，不能检查该索引。  
  
## <a name="user-action"></a>用户操作  
请使用 ALTER INDEX 重新生成索引。  
  
## <a name="see-also"></a>另请参阅  
[ALTER INDEX (Transact-SQL)](~/t-sql/statements/alter-index-transact-sql.md)  
[重新组织和重新生成索引](~/relational-databases/indexes/reorganize-and-rebuild-indexes.md)  
  
