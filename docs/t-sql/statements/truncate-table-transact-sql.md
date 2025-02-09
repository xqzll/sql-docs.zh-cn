---
title: TRUNCATE TABLE (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 08/10/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- TRUNCATE
- TRUNCATE TABLE
- TRUNCATE_TSQL
- TRUNCATE_TABLE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- row removal [SQL Server], TRUNCATE TABLE statement
- table truncating [SQL Server]
- removing rows
- TRUNCATE TABLE statement
- deleting rows
- dropping rows
ms.assetid: 3d544eed-3993-4055-983d-ea334f8c5c58
author: CarlRabeler
ms.author: carlrab
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 82107dd0e4e5927eec1670a2a4e9fcf933ae35df
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "65503313"
---
# <a name="truncate-table-transact-sql"></a>TRUNCATE TABLE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

删除表中的所有行或表中指定的分区，不记录单个行删除操作。 TRUNCATE TABLE 与没有 WHERE 子句的 DELETE 语句类似；但是，TRUNCATE TABLE 速度更快，使用的系统资源和事务日志资源更少。  
  
 ![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "主题链接图标") [TRANSACT-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>语法  
  
```  
-- Syntax for SQL Server and Azure SQL Database  
  
TRUNCATE TABLE   
    { database_name.schema_name.table_name | schema_name.table_name | table_name }  
    [ WITH ( PARTITIONS ( { <partition_number_expression> | <range> }   
    [ , ...n ] ) ) ]  
[ ; ]  
  
<range> ::=  
<partition_number_expression> TO <partition_number_expression>  
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
TRUNCATE TABLE { database_name.schema_name.table_name | schema_name.table_name | table_name }  
[;]  
```  
  
## <a name="arguments"></a>参数  
 *database_name*  
 数据库的名称。  
  
 *schema_name*  
 表所属架构的名称。  
  
 *table_name*  
 要截断的表的名称，或要删除其全部行的表的名称。 table_name 须是文本。  table_name 不能是 OBJECT_ID() 函数或变量。    
  
 WITH ( PARTITIONS ( { \<partition_number_expression> | \<range> } [ , ...n ] ) )    
适用范围：[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]（[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] 到[当前版本](https://go.microsoft.com/fwlink/p/?LinkId=299658)） 
  
 指定要截断或删除其中所有行的分区。 如果表未分区，则 WITH PARTITIONS 参数会生成错误。  如果未提供 WITH PARTITIONS 子句，则整个表都将被截断。   
  
 可以按以下方式指定 \<partition_number_expression>：  
  
-   提供分区号，例如：`WITH (PARTITIONS (2))`  
  
-   提供若干单独分区的分区号，并用逗号分隔，例如：`WITH (PARTITIONS (1, 5))`  
  
-   同时提供范围和单独分区，例如：`WITH (PARTITIONS (2, 4, 6 TO 8))`  
  
-   \<range> 可指定为由单词 TO 隔开的分区号，例如：`WITH (PARTITIONS (6 TO 8))`    
  
 要截断一个已分区表，表和索引必须对齐（在同一个分区函数上进行分区）。  
  
## <a name="remarks"></a>Remarks  
 与 DELETE 语句相比，TRUNCATE TABLE 具有以下优点：  
  
-   所用的事务日志空间较少。  
  
     DELETE 语句每次删除一行，并在事务日志中为所删除的每行记录一个项。 TRUNCATE TABLE 通过释放用于存储表数据的数据页删除数据，且仅在事务日志中记录页释放。  
  
-   使用的锁通常较少。  
  
     当使用行锁执行 DELETE 语句时，将锁定表中各行以便删除。 TRUNCATE TABLE 始终锁定表（包含架构 (SCH-M) 锁）和页，而不是锁定各行。  
  
-   如无例外，在表中不会留有任何页。  
  
     执行 DELETE 语句后，表仍会包含空页。 例如，必须至少使用一个排他 (LCK_M_X) 表锁，才能释放堆中的空表。 如果执行删除操作时没有使用表锁，表（堆）中将包含许多空页。 对于索引，删除操作会留下一些空页，尽管这些页会通过后台清除进程迅速释放。  
  
 TRUNCATE TABLE 删除表中的所有行，但表结构及其列、约束、索引等保持不变。 若要删除表定义及其数据，请使用 DROP TABLE 语句。  
  
 如果表包含标识列，该列的计数器重置为该列定义的种子值。 如果未定义种子，则使用默认值 1。 若要保留标识计数器，请使用 DELETE。  
  
## <a name="restrictions"></a>限制  
 不能对以下表使用 TRUNCATE TABLE：  
  
-   由 FOREIGN KEY 约束引用的表。 （您可以截断具有引用自身的外键的表。）  
  
-   参与索引视图的表。  
  
-   通过使用事务复制或合并复制发布的表。  
  
 对于具有以上一个或多个特征的表，请使用 DELETE 语句。  
  
 TRUNCATE TABLE 不能激活触发器，因为该操作不记录各个行删除。 有关详细信息，请参阅 [CREATE TRIGGER (Transact-SQL)](../../t-sql/statements/create-trigger-transact-sql.md)。 
 
 在 [!INCLUDE[sssdwfull](../../includes/sssdwfull-md.md)] 和 [!INCLUDE[sspdw](../../includes/sspdw-md.md)] 中：

- TRUNCATE TABLE 不可出现在 EXPLAIN 语句中。

- TRUNCATE TABLE 不可在事务内部运行。
  
## <a name="truncating-large-tables"></a>截断大型表  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 和 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 能够删除或截断超过 128 个区的表，而无需同步锁定所有需删除的区。  
  
## <a name="permissions"></a>权限  
 所需的最低权限是 table_name 上的 ALTER 权限。  TRUNCATE TABLE 权限默认授予表所有者、sysadmin 固定服务器角色的成员、db_owner 和 db_ddladmin 固定数据库角色的成员，并且不可转移权限。 但是，可以在诸如存储过程这样的模块中加入 TRUNCATE TABLE 语句，然后为使用 EXECUTE AS 子句的模块授予适当的权限。  
  
## <a name="examples"></a>示例  
  
### <a name="a-truncate-a-table"></a>A. 截断表  
 下面的示例删除 `JobCandidate` 表中的所有数据。 在 `SELECT` 语句之前和之后使用 `TRUNCATE TABLE` 语句来比较结果。  
  
```sql  
USE AdventureWorks2012;  
GO  
SELECT COUNT(*) AS BeforeTruncateCount   
FROM HumanResources.JobCandidate;  
GO  
TRUNCATE TABLE HumanResources.JobCandidate;  
GO  
SELECT COUNT(*) AS AfterTruncateCount   
FROM HumanResources.JobCandidate;  
GO  
```  
  
### <a name="b-truncate-table-partitions"></a>B. 截断表分区  
  
适用范围：[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]（[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] 到[当前版本](https://go.microsoft.com/fwlink/p/?LinkId=299658)） 
  
 下面的示例将截断已分区表的指定分区。 `WITH (PARTITIONS (2, 4, 6 TO 8))` 语法导致分区号 2、4、6、7 和 8 被截断。  
  
```sql  
TRUNCATE TABLE PartitionTable1   
WITH (PARTITIONS (2, 4, 6 TO 8));  
GO  
```  
  
## <a name="see-also"></a>另请参阅  
 [DELETE (Transact-SQL)](../../t-sql/statements/delete-transact-sql.md)   
 [DROP TABLE (Transact-SQL)](../../t-sql/statements/drop-table-transact-sql.md)   
 [IDENTITY（属性）(Transact-SQL)](../../t-sql/statements/create-table-transact-sql-identity-property.md)  
  
  

