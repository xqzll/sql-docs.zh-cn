---
title: 重命名视图 | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: table-view-index, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- views [SQL Server], renaming
- renaming views
ms.assetid: 5eed0488-81d2-40e8-8fdf-b0a640a591d0
author: stevestein
ms.author: sstein
ms.manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: bc4d31360e86fa0ec60c482034ce1678801cf5f3
ms.sourcegitcommit: cff8dd63959d7a45c5446cadf1f5d15ae08406d8
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/05/2019
ms.locfileid: "67582332"
---
# <a name="rename-views"></a>重命名视图
[!INCLUDE[tsql-appliesto-ss2008-asdb-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-all-md.md)]
  您可以使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中重命名视图。  
  
> [!WARNING]  
>  如果重命名视图，则依赖于该视图的代码和应用程序可能会出错。 这些代码和应用程序包括其他视图、查询、存储过程、用户定义函数和客户端应用程序。 注意，这些错误会级联发生。  
  
 **本主题内容**  
  
-   **开始之前：**  
  
     [先决条件](#Prerequisites)  
  
     [安全性](#Security)  
  
-   **重命名视图，使用：**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
-   **跟进：** [在重命名视图之后](#FollowUp)  
  
##  <a name="BeforeYouBegin"></a> 开始之前  
  
###  <a name="Prerequisites"></a> 先决条件  
 获取视图的所有依赖关系的列表。 必须修改引用视图的任何对象、脚本或应用程序，以反映新的视图名称。 有关详细信息，请参阅 [Get Information About a View](../../relational-databases/views/get-information-about-a-view.md)。 我们建议您删除视图，然后使用新名称重新创建它，而不是重命名视图。 通过重新创建视图，您可以更新视图中引用的对象的依赖关系信息。  
  
###  <a name="Security"></a> Security  
  
####  <a name="Permissions"></a> 权限  
 需要对 SCHEMA 的 ALTER 权限或对 OBJECT 的 CONTROL 权限，以及数据库中的 CREATE VIEW 权限。  
  
##  <a name="SSMSProcedure"></a> 使用 SQL Server Management Studio  
  
#### <a name="to-rename-a-view"></a>重命名视图  
  
1.  在 **“对象资源管理器”** 中，展开包含要重命名的视图的数据库，然后展开 **“视图”** 文件夹。  
  
2.  右键单击要重命名的视图，然后选择 **“重命名”** 。  
  
3.  输入视图的新名称。  

[!INCLUDE[freshInclude](../../includes/paragraph-content/fresh-note-steps-feedback.md)]

##  <a name="TsqlProcedure"></a> 使用 Transact-SQL  
 **重命名视图**  
  
 尽管可以使用 **sp_rename** 更改视图的名称，但是我们建议你删除现有视图，然后使用新名称重新创建它。  
  
 有关详细信息，请参阅 [CREATE VIEW (Transact-SQL)](../../t-sql/statements/create-view-transact-sql.md) 和 [DROP VIEW (Transact-SQL)](../../t-sql/statements/drop-view-transact-sql.md)。  
  
##  <a name="FollowUp"></a> 跟进：在重命名视图之后  
 确保引用视图的旧名称的所有对象、脚本和应用程序现在都使用新名称。  
  
  
