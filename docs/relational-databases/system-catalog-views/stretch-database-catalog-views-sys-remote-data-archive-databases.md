---
title: sys.remote_data_archive_databases (Transact SQL) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.technology: stored-procedures
ms.topic: language-reference
f1_keywords:
- sys.remote_data_archive_databases
- sys.remote_data_archive_databases_TSQL
- remote_data_archive_databases
- remote_data_archive_databases_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.remote_data_archive_databases catalog view
ms.assetid: 25bffb0c-9821-40b4-88cf-75f854891a09
author: pmasl
ms.author: pelopes
ms.reviewer: mikeray
manager: craigg
ms.openlocfilehash: 74a44e8c3e6b0be026ac716d43b539869345b3b9
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "64945614"
---
# <a name="stretch-database-catalog-views---sysremotedataarchivedatabases"></a>Stretch Database 目录视图的 sys.remote_data_archive_databases
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  包含每个远程数据库用于存储从已启用延伸的本地数据库的数据行。  
  
|列名|数据类型|Description|  
|-----------------|---------------|-----------------|  
|**remote_database_id**|**int**|自动生成本地标识符的远程数据库。|  
|**remote_database_name**|**sysname**|远程数据库的名称。|  
|**data_source_id**|**int**|用于连接到远程服务器的数据源|  
  
## <a name="see-also"></a>请参阅  
 [Stretch 数据库](../../sql-server/stretch-database/stretch-database.md)  
  
  
