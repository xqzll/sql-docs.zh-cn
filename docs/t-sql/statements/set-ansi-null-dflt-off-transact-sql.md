---
title: SET ANSI_NULL_DFLT_OFF (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 12/04/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- ANSI_NULL_DFLT_OFF_TSQL
- ANSI_NULL_DFLT_OFF
- SET ANSI_NULL_DFLT_OFF
- SET_ANSI_NULL_DFLT_OFF_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- default nullability
- ANSI_NULL_DFLT_OFF option
- null values [SQL Server], overriding
- overriding default nullability
- SET ANSI_NULL_DFLT_OFF statement
ms.assetid: 8ed5c512-f5de-4741-a18a-de85a3041295
author: CarlRabeler
ms.author: carlrab
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 0bab88402c4a43286fd40807293a0245c85b1ac7
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "62638628"
---
# <a name="set-ansinulldfltoff-transact-sql"></a>SET ANSI_NULL_DFLT_OFF (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  数据库的 ANSI null default 选项为 true 时，更改会话行为以覆盖新列的默认为 Null 性  。 有关设置 ANSI null default 的值的详细信息，请参阅 [ALTER DATABASE (Transact-SQL)](../../t-sql/statements/alter-database-transact-sql.md)。  
  
 ![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "主题链接图标") [TRANSACT-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  

## <a name="syntax"></a>语法

```
-- Syntax for SQL Server and Azure SQL Database
  
SET ANSI_NULL_DFLT_OFF { ON | OFF }
```

```
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse

SET ANSI_NULL_DFLT_OFF OFF
```

## <a name="remarks"></a>Remarks  
 仅当在 CREATE TABLE 和 ALTER TABLE 语句中没有指定列的为空性时，该设置才能影响新列的为空性。 默认情况下，当 SET ANSI_NULL_DFLT_OFF 为 ON 时，如果没有显式指定列的为空性状态，则使用 ALTER TABLE 和 CREATE TABLE 语句创建的新列将为 NOT NULL。 SET ANSI_NULL_DFLT_OFF 对使用显示 NULL 或 NOT NULL 创建的列无效。  
  
 不能同时将 SET ANSI_NULL_DFLT_OFF 和 SET ANSI_NULL_DFLT_ON 设置为 ON。 如果将一个选项设置为 ON，则将另一个选项设置为 OFF。 因此，可以将 ANSI_NULL_DFLT_OFF 或 SET ANSI_NULL_DFLT_ON 设置为 ON，或者将二者都设置为 OFF。 如果有一个选项为 ON，则该设置（SET ANSI_NULL_DFLT_OFF 或 SET ANSI_NULL_DFLT_ON）生效。 如果将这两个选项都设置为 OFF，则 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 将使用 [sys.databases](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md) 目录视图中 is_ansi_null_default_on 列的值。  
  
 为使 [!INCLUDE[tsql](../../includes/tsql-md.md)] 脚本在包含不同为空性设置的数据库中获得更可靠的操作，最好始终在 CREATE TABLE 和 ALTER TABLE 语句中指定 NULL 或 NOT NULL。  
  
 SET ANSI_NULL_DFLT_OFF 的设置是在执行或运行时设置的，而不是在分析时设置的。  
  
 要查看此设置的当前设置，请运行以下查询。  
  
```  
DECLARE @ANSI_NULL_DFLT_OFF VARCHAR(3) = 'OFF';  
IF ( (2048 & @@OPTIONS) = 2048 ) SET @ANSI_NULL_DFLT_OFF = 'ON';  
SELECT @ANSI_NULL_DFLT_OFF AS ANSI_NULL_DFLT_OFF;  
  
```  
  
## <a name="permissions"></a>权限  
 要求具有 public 角色的成员身份。  
  
## <a name="examples"></a>示例  
 以下示例显示当 ANSI null default 数据库选项在两种设置下时，对 `SET ANSI_NULL_DFLT_OFF` 的影响。  
  
```  
USE AdventureWorks2012;  
GO  
  
-- Set the 'ANSI null default' database option to true by executing   
-- ALTER DATABASE.  
GO  
ALTER DATABASE AdventureWorks2012 SET ANSI_NULL_DEFAULT ON;  
GO  
-- Create table t1.  
CREATE TABLE t1 (a TINYINT);  
GO  
-- NULL INSERT should succeed.  
INSERT INTO t1 (a) VALUES (NULL);  
GO  
  
-- SET ANSI_NULL_DFLT_OFF to ON and create table t2.  
SET ANSI_NULL_DFLT_OFF ON;  
GO  
CREATE TABLE t2 (a TINYINT);  
GO   
-- NULL INSERT should fail.  
INSERT INTO t2 (a) VALUES (NULL);  
GO  
  
-- SET ANSI_NULL_DFLT_OFF to OFF and create table t3.  
SET ANSI_NULL_DFLT_OFF OFF;  
GO  
CREATE TABLE t3 (a TINYINT) ;  
GO   
-- NULL INSERT should succeed.  
INSERT INTO t3 (a) VALUES (NULL);  
GO  
  
-- This illustrates the effect of having both the database  
-- option and SET option disabled.  
-- Set the 'ANSI null default' database option to false.  
ALTER DATABASE AdventureWorks2012 SET ANSI_NULL_DEFAULT OFF;  
GO  
-- Create table t4.  
CREATE TABLE t4 (a tinyint) ;  
GO   
-- NULL INSERT should fail.  
INSERT INTO t4 (a) VALUES (null);  
GO  
  
-- SET ANSI_NULL_DFLT_OFF to ON and create table t5.  
SET ANSI_NULL_DFLT_OFF ON;  
GO  
CREATE TABLE t5 (a tinyint);  
GO   
-- NULL insert should fail.  
INSERT INTO t5 (a) VALUES (null);  
GO  
  
-- SET ANSI_NULL_DFLT_OFF to OFF and create table t6.  
SET ANSI_NULL_DFLT_OFF OFF;  
GO  
CREATE TABLE t6 (a tinyint);   
GO   
-- NULL insert should fail.  
INSERT INTO t6 (a) VALUES (null);  
GO  
  
-- Drop tables t1 through t6.  
DROP TABLE t1, t2, t3, t4, t5, t6;  
  
```  
  
## <a name="see-also"></a>另请参阅  
 [ALTER TABLE (Transact-SQL)](../../t-sql/statements/alter-table-transact-sql.md)   
 [CREATE TABLE (Transact-SQL)](../../t-sql/statements/create-table-transact-sql.md)   
 [SET 语句 (Transact-SQL)](../../t-sql/statements/set-statements-transact-sql.md)   
 [SET ANSI_NULL_DFLT_ON (Transact-SQL)](../../t-sql/statements/set-ansi-null-dflt-on-transact-sql.md)  
  
  
