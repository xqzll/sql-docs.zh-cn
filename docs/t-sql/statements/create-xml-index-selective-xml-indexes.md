---
title: CREATE XML INDEX（选择性 XML 索引）| Microsoft Docs
ms.custom: ''
ms.date: 08/10/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 1f510151-41d5-45c2-9cd0-b1ca0246fffe
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 14e48f3e8af059b0055f9747c5fb1b2e2a53ca6a
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "65502811"
---
# <a name="create-xml-index-selective-xml-indexes"></a>CREATE XML INDEX（选择性 XML 索引）
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  在已通过现有选择性 XML 索引建立索引的单个路径上创建新的辅助选择性 XML 索引。 您还可以创建主要选择性 XML 索引。 有关详细信息，请参阅[创建、更改和删除选择性 XML 索引](../../relational-databases/xml/create-alter-and-drop-selective-xml-indexes.md)。  
  
 ![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "主题链接图标") [TRANSACT-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>语法  
  
```  
  
CREATE XML INDEX index_name  
    ON <table_object> ( xml_column_name )  
    USING XML INDEX sxi_index_name  
    FOR ( <xquery_or_sql_values_path> )  
    [WITH ( <index_options> )]  
  
<table_object> ::=   
{ database_name.schema_name.table_name | schema_name.table_name | table_name }  
  
<xquery_or_sql_values_path>::=   
<path_name>   
  
<path_name> ::=   
character string literal  
  
<xmlnamespace_list> ::=   
<xmlnamespace_item> [, <xmlnamespace_list>]  
  
<xmlnamespace_item> ::=   
xmlnamespace_uri AS xmlnamespace_prefix  
  
<index_options> ::=   
(    
  | PAD_INDEX  = { ON | OFF }  
  | FILLFACTOR = fillfactor  
  | SORT_IN_TEMPDB = { ON | OFF }  
  | IGNORE_DUP_KEY = OFF  
  | DROP_EXISTING = { ON | OFF }  
  | ONLINE = OFF  
  | ALLOW_ROW_LOCKS = { ON | OFF }  
  | ALLOW_PAGE_LOCKS = { ON | OFF }  
  | MAXDOP = max_degree_of_parallelism  
)  
```  
  
##  <a name="Arguments"></a> 参数  
 index_name   
 要创建的新索引的名称。 索引名称在表中必须唯一，但在数据库中不必唯一。 索引名称必须符合[标识符](../../relational-databases/databases/database-identifiers.md)的规则。  
  
  \<table_object> 是包含要建立索引的 XML 列的表。 您可以使用下列格式：  
  
-   `database_name.schema_name.table_name`  
  
-   `database_name..table_name`  
  
-   `schema_name.table_name`  
  
 xml_column_name   
 包含要建立索引的路径的 XML 列的名称。  
  
 USING XML INDEX sxi_index_name   
 现有选择性 XML 索引的名称。  
  
 FOR ( \<xquery_or_sql_values_path> ) 是要在其上创建辅助选择性 XML 索引的已建立索引的路径名称   。 要建立索引的路径是从 CREATE SELECTIVE XML INDEX 语句分配的名称。 有关详细信息，请参阅 [CREATE SELECTIVE XML INDEX (Transact-SQL)](../../t-sql/statements/create-selective-xml-index-transact-sql.md)。  
  
 有关通过 \<index_options> 获取索引选项的信息，请参阅 [CREATE XML INDEX](../../t-sql/statements/create-xml-index-selective-xml-indexes.md)。  
  
## <a name="remarks"></a>Remarks  
 对于基表中的每个 XML 列，可能有多个辅助选择性 XML 索引。  
  
## <a name="limitations-and-restrictions"></a>限制和局限  
 XML 列中必须存在选择性 XML 索引，然后才能对该列创建辅助选择性 XML 索引。  
  
## <a name="security"></a>Security  
  
### <a name="permissions"></a>权限  
 要求对表或视图具有 ALTER 权限。 用户必须是 **sysadmin** 固定服务器角色的成员，或者是 **db_ddladmin** 和 **db_owner** 固定数据库角色的成员。  
  
## <a name="examples"></a>示例  
 下面的示例对路径 `pathabc`创建辅助选择性 XML 索引。 建立索引的路径是从 [CREATE SELECTIVE XML INDEX (Transact-SQL)](../../t-sql/statements/create-selective-xml-index-transact-sql.md) 语句分配的名称。  
  
```  
CREATE XML INDEX filt_sxi_index_c  
ON Tbl(xmlcol)  
USING XML INDEX sxi_index  
FOR ( pathabc );  
```  
  
## <a name="see-also"></a>另请参阅  
 [选择性 XML 索引 (SXI)](../../relational-databases/xml/selective-xml-indexes-sxi.md)   
 [创建、更改和删除辅助选择性 XML 索引](../../relational-databases/xml/create-alter-and-drop-secondary-selective-xml-indexes.md)  
  
  

