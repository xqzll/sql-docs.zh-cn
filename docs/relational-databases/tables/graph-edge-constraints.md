---
title: 图形边缘约束 | Microsoft Docs
ms.custom: ''
ms.date: 06/21/2019
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- edge constraints [SQL Server]
- CONNECTION constraints
- edge constraints [Azure SQL Database]
- graph edge constraints
- SQL Graph
author: shkale-msft
ms.author: shkale
monikerRange: '>=sql-server-2017||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current||=azuresqldb-current'
ms.openlocfilehash: aa73858e6df29c814821ee9e24923cbfc0fbd4a2
ms.sourcegitcommit: 630f7cacdc16368735ec1d955b76d6d030091097
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/24/2019
ms.locfileid: "67343884"
---
# <a name="edge-constraints"></a>边缘约束

[!INCLUDE[appliesto-ss-asdb-xxxx-xxx-md.md](../../includes/appliesto-ss-asdb-xxxx-xxx-md.md)]

边缘约束可用于对 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 图形数据库中的边缘表强制执行数据完整性和特定语义。

##  <a name="Connection"></a> 边缘约束
 在图形功能的第一个版本中，边缘表没有对边缘的终结点强制执行任何操作。 也就是说，无论何种类型，图形数据库中的边缘都可以将任何节点连接到任何其他节点。 

 此版本引入了边缘约束，使用户能够向其边缘表添加约束，从而强制执行特定语义，同时保持数据完整性。 将新的边缘添加到具有边缘约束的边缘表时，[!INCLUDE[ssDE](../../includes/ssde-md.md)] 强制使边缘尝试连接的节点存在于正确的节点表中。 如果节点仍被边缘引用，则还要确保不会删除该节点。 

 ### <a name="edge-constraint-clauses"></a>边缘约束子句
 每个边缘约束都由一个或多个边缘约束子句组成。 边缘约束子句是给定边缘可以连接的 FROM 和 TO 节点对。 

 假设图形中有 `Product` 和 `Customer` 节点，并使用 `Bought` 边缘连接这些节点。 边缘约束子句指定 FROM 和 TO 节点对以及边缘的方向。 在这种情况下，边缘约束子句将为 `Customer` TO `Product`。 也就是说，将允许插入范围从 `Customer` 到 `Product` 的 `Bought`。 尝试插入范围从 `Product` 到 `Customer` 的边缘失败。 
  
- 边缘约束子句包含对其强制执行边缘约束的 FROM 和 TO 节点对表。 
  
- 用户可以为每个边缘约束指定多个边缘约束子句，这些子句将应用为析取。

- 如果在单个边缘表上创建多个边缘约束，则边缘必须满足允许的所有约束。
  
### <a name="indexes-on-edge-constraints"></a>边缘约束的索引
 创建边缘约束不会自动在边缘表中的 `$from_id` 和 `$to_id` 列上创建相应的索引。 如果拥有点查找查询或 OLTP 工作负载，建议在“`$from_id`，`$to_id`对上手动创建索引。 

##  <a name="Tasks"></a> 相关任务  
 下表列出了与边缘约束关联的常见任务。  
  
|任务|项目|  
|----------|-----------|  
|介绍如何创建边缘约束。|[创建边缘约束](../../relational-databases/tables/create-edge-constraints.md)|  
|介绍如何删除边缘约束。|[删除边缘约束](../../relational-databases/tables/delete-edge-constraint.md)|  
|介绍如何修改边缘约束。|[修改边缘约束](../../relational-databases/tables/modify-edge-constraint.md)|  
|介绍如何查看边缘约束属性。|[查看边缘约束属性](../../relational-databases/tables/view-edge-constraint-properties.md)|  
| SQL Server 中的图形技术概述 | [SQL Server 和 Azure SQL 数据库中的图形处理](../graphs/sql-graph-overview.md) |
| &nbsp; | &nbsp; |
