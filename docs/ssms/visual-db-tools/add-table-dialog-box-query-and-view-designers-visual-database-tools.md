---
title: “添加表”对话框（查询和视图设计器）(Visual DB tools) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdt.dlgbox.query.addtable
- vdtsql.chm:65565
ms.assetid: fce7adcc-4cf5-4a52-9203-11c13d1ecf08
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: cfbad10dd90ddc5b68e44bac88bc1ee6d437f78e
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "65099489"
---
# <a name="add-table-dialog-box-query-and-view-designers-visual-database-tools"></a>“添加表”对话框（查询和视图设计器）(Visual Database Tools)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
使用此对话框可以向查询或视图中添加表、视图、用户定义函数或同义词。  
  
> [!NOTE]  
> 如果表是为复制发布的，则必须使用 Transact-SQL 语句 [ALTER TABLE](../../t-sql/statements/alter-table-transact-sql.md) 或 SQL Server 管理对象 (SMO) 对架构进行更改。 使用表设计器或数据库关系图设计器更改架构后，会尝试删除并重新创建表。 由于您不能删除已发布的对象，因此架构更改将失败。  
  
## <a name="options"></a>选项  
**表**  
列出可以向“关系图”  窗格中添加的表。 若要添加某个表，请选择该表，再单击“添加”  。 若要同时添加多个表，请选中这些表，再单击“添加”  。  
  
**视图**  
列出可以向“关系图”  窗格中添加的视图。 若要添加某个视图，请选择该视图，再单击“添加”  。 若要同时添加多个视图，请选中这些视图，再单击“添加”  。  
  
**函数**  
列出可以向“关系图”  窗格中添加的用户定义函数。 若要添加某个函数，请选择该函数，再单击“添加”  。 若要同时添加多个函数，请选中这些函数，再单击“添加”  。  
  
**同义词**  
列出可以向“关系图”  窗格中添加的同义词。 若要添加某个同义词，请选择该同义词，再单击“添加”  。 若要同时添加多个同义词，请选中这些同义词，再单击“添加”  。  
  
**“刷新”**  
更新该列表以包含自上次检索该列表以来对数据库做出的所有更改。  
  
**“添加”**  
添加所选的一项或多项。  
  
## <a name="see-also"></a>另请参阅  
[设计查询和视图操作指南主题 (Visual Database Tools)](../../ssms/visual-db-tools/design-queries-and-views-how-to-topics-visual-database-tools.md)  
  
