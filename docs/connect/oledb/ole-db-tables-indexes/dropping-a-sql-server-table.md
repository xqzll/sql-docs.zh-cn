---
title: 删除 SQL Server 表 |Microsoft Docs
description: 删除 SQL Server 表使用的 SQL Server OLE DB 驱动程序
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- tables [OLE DB]
- deleting tables
- OLE DB Driver for SQL Server, tables
- removing tables
- dropping tables
author: pmasl
ms.author: pelopes
manager: jroth
ms.openlocfilehash: f743194d0036d338ad39594d7c7f00665d83a224
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 06/07/2019
ms.locfileid: "66766241"
---
# <a name="dropping-a-sql-server-table"></a>删除 SQL Server 表
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  SQL Server 的 OLE DB 驱动程序公开**itabledefinition:: Droptable**函数来删除[!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]从数据库表。  
  
 在 pTableID 参数的 uName 联合的 pwszName 成员中，将表名指定为 Unicode 字符串    。 pTableID 的 eKind 成员必须是 DBKIND_NAME   。  
  
## <a name="see-also"></a>另请参阅  
 [表和索引](../../oledb/ole-db-tables-indexes/tables-and-indexes.md)  
  
  
