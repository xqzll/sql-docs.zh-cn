---
title: 从表中删除列 | Microsoft Docs
ms.custom: ''
ms.date: 04/11/2017
ms.prod: sql
ms.prod_service: table-view-index, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- columns [SQL Server], deleting
- removing columns
- deleting columns
- dropping columns
ms.assetid: 0d8f6e4f-bc71-4fa3-8615-74249c8e072d
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 41a78443dba90f8b75fec9e3db05c9106755b865
ms.sourcegitcommit: cff8dd63959d7a45c5446cadf1f5d15ae08406d8
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/05/2019
ms.locfileid: "67580470"
---
# <a name="delete-columns-from-a-table"></a>从表中删除列
[!INCLUDE[tsql-appliesto-ss2016-all-md](../../includes/tsql-appliesto-ss2016-all-md.md)]

  本主题说明如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中删除表列。  
  
> [!CAUTION]  
>  删除表中的某一列后，该列及其包含的所有数据都将删除。
  
 **本主题内容**  
  
-   **开始之前：**  
  
     [限制和局限](#Restrictions)  
  
     [安全性](#Security)  
  
-   **使用以下工具从表中删除列：**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> 开始之前  
  
###  <a name="Restrictions"></a> 限制和局限  
 不能删除具有 CHECK 约束的列。 必须首先删除该约束。  
  
 不能删除具有 PRIMARY KEY 或 FOREIGN KEY 约束或者其他依赖关系的列，但在使用表设计器时例外。 在使用对象资源管理器或 [!INCLUDE[tsql](../../includes/tsql-md.md)]时，必须首先删除该列上的所有依赖关系。  
  
###  <a name="Security"></a> Security  
  
####  <a name="Permissions"></a> 权限  
 需要对表的 ALTER 权限。  
  
##  <a name="SSMSProcedure"></a> 使用 SQL Server Management Studio  
  
#### <a name="to-delete-columns-by-using-object-explorer"></a>通过使用对象资源管理器删除列  
  
1.  在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的实例。  
  
2.  在“对象资源管理器”中，找到要从其中删除列的表，然后将其展开以公开列名称  。 

3.  右键单击要删除的列，然后选择“删除”  。  
  
3.  在 **“删除对象”** 对话框中，单击 **“确定”** 。  

[!INCLUDE[freshInclude](../../includes/paragraph-content/fresh-note-steps-feedback.md)]

 如果该列包含约束或其他依赖关系，则在 **“删除对象”** 对话框中将显示一条错误消息。 通过删除引用的约束解决该错误。  
  
#### <a name="to-delete-columns-by-using-table-designer"></a>通过使用表设计器删除列  
  
1.  在“对象资源管理器”  中，右键单击要从其中删除列的表，然后选择“设计”  。  
  
2.  右键单击要删除的列，然后从快捷菜单上选择“删除列”  。  
  
3.  如果该列参与了关系（FOREIGN KEY 或 PRIMARY KEY），则将显示一条消息，提示您确认删除所选列及其关系。 选择 **“是”** 。  
  
##  <a name="TsqlProcedure"></a> 使用 Transact-SQL  
  
#### <a name="to-delete-columns"></a>删除列  
  
1.  在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的实例。  
  
2.  在标准菜单栏上，单击 **“新建查询”** 。  
  
3.  将以下示例复制并粘贴到查询窗口中，然后单击“执行”  。  
  
    ```  
    USE AdventureWorks2012;  
    GO  
    ALTER TABLE dbo.doc_exb DROP COLUMN column_b ;  
    ```  
  
 如果该列包含约束或其他依赖关系，将返回一条错误消息。 通过删除引用的约束解决该错误。  
  
 有关其他示例，请参阅 [ALTER TABLE (Transact-SQL)](../../t-sql/statements/alter-table-transact-sql.md)。  
  
##  <a name="FollowUp"></a>  
