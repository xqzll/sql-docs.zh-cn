---
title: 向表中添加列（数据库引擎）| Microsoft Docs
ms.custom: ''
ms.date: 10/27/2016
ms.prod: sql
ms.prod_service: table-view-index, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- inserting columns
- columns [SQL Server], adding
- adding columns
ms.assetid: abeb8d52-d562-4e29-9e1e-2923ae874859
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 231590b5b1d15e85bc6fb3ca062253dfc3fba9b9
ms.sourcegitcommit: cff8dd63959d7a45c5446cadf1f5d15ae08406d8
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/05/2019
ms.locfileid: "67585083"
---
# <a name="add-columns-to-a-table-database-engine"></a>向表中添加列（数据库引擎）
[!INCLUDE[tsql-appliesto-ss2016-all-md](../../includes/tsql-appliesto-ss2016-all-md.md)]

  本主题说明如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中向表添加新列。  

  ##  <a name="BeforeYouBegin"></a> 开始之前  
  
###  <a name="Restrictions"></a> 限制和局限  
 使用 ALTER TABLE 语句向表添加列会自动将这些列添加到该表的末尾。 如果您希望该表中的列采用特定顺序，请使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]。 但请注意，这并非数据库设计的最佳做法。 最佳做法是指定在应用程序级别和查询级别返回列的顺序。 您不应依赖于使用 SELECT * 基于在表中定义列的顺序以预期顺序返回所有列。 请始终按照您希望它们出现的顺序在您的查询和应用程序中按名称指定列。  
  
###  <a name="Security"></a> Security  
  
####  <a name="Permissions"></a> 权限  
 需要对表的 ALTER 权限。  
  
##  <a name="SSMSProcedure"></a> 使用 SQL Server Management Studio  
  
#### <a name="to-insert-columns-into-a-table-with-table-designer"></a>用表设计器向表中插入列  
  
1.  在“对象资源管理器”  中，右键单击要为其添加列的表，再选择“设计”  。  
  
2.  单击 **“列名”** 列中的第一个空单元。  
  
3.  在该单元中键入列名。 列名是必需设置的值。  
  
4.  按 Tab 键转到 **“数据类型”** 单元格，再从下拉列表中选择数据类型。 它是必需设置的值，如果你没有作出选择，它将被赋以默认值。  
  
    > [!NOTE]  
    >  可以在“选项”  对话框中的“数据库工具”  之下更改默认值。  
  
5.  在 **“列属性”** 选项卡上继续定义任何其他列属性。  
  
    > [!NOTE]  
    >  列属性的默认值在你创建新列时添加，但你可以在“列属性”  选项卡中更改这些值。  
  
6.  在你添加完列后，从“文件”  菜单中，选择“保存”  _table name_。  

[!INCLUDE[freshInclude](../../includes/paragraph-content/fresh-note-steps-feedback.md)]

##  <a name="TsqlProcedure"></a> 使用 Transact-SQL  
  
#### <a name="to-insert-columns-into-a-table"></a>向表中插入列  
  
1.  连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。  
  
2.  在标准菜单栏上，单击 **“新建查询”** 。  
  
3.  下面的示例将两列添加到表 `dbo.doc_exa`中。 将以下示例复制并粘贴到查询窗口中，然后单击“执行”  。  
  
```  
ALTER TABLE dbo.doc_exa ADD column_b VARCHAR(20) NULL, column_c INT NULL ;  
```  
  
####  <a name="FollowUp"></a> 有关详细信息，请参阅 [ALTER TABLE (Transact-SQL)](../../t-sql/statements/alter-table-transact-sql.md)  
  
  
