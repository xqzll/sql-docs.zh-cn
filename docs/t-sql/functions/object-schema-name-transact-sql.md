---
title: OBJECT_SCHEMA_NAME (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/25/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- OBJECT_SCHEMA_NAME
- OBJECT_SCHEMA_NAME_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- objects [SQL Server], names
- schemas [SQL Server], names
- displaying schema names
- database objects [SQL Server], names
- OBJECT_SCHEMA_NAME function
ms.assetid: 5ba90bb9-d045-4164-963e-e9e96c0b1e8b
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 7f46e00be95d751629325a6b7c54160bf00e44be
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "65948969"
---
# <a name="objectschemaname-transact-sql"></a>OBJECT_SCHEMA_NAME (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-asdw-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-asdw-xxx-md.md)]

  返回架构范围内的对象的数据库架构名称。 有关架构范围内对象的列表，请参阅 [sys.objects (Transact-SQL)](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)。  
  
 ![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "主题链接图标") [TRANSACT-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>语法  
  
```  
  
OBJECT_SCHEMA_NAME ( object_id [, database_id ] )  
```  
  
## <a name="arguments"></a>参数  
 *object_id*  
 要使用的对象的 ID。 object_id 的数据类型为 int，并假定为指定数据库或当前数据库上下文中的架构范围内的对象   。  
  
 database_id   
 要在其中查找对象的数据库的 ID。 database_id 的数据类型为 int   。  
  
## <a name="return-types"></a>返回类型  
 **sysname**  
  
## <a name="exceptions"></a>异常  
 出现错误时或调用方没有查看对象的权限时，将返回 NULL。 如果目标数据库的 AUTO_CLOSE 选项设置为 ON，则此函数将打开此数据库。  
  
 用户只能查看符合如下条件的安全对象的元数据：该安全对象为该用户所有，或已授予该用户对该安全对象的权限。 也就是说，如果用户对该对象没有任何权限，则那些会生成元数据的内置函数（如 OBJECT_SCHEMA_NAME）则可能返回 NULL。 有关详细信息，请参阅 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)。  
  
## <a name="permissions"></a>权限  
 需要对对象拥有 ANY 权限。 若要指定数据库 ID，还需要对数据库拥有 CONNECT 权限，或者必须启用 guest 帐户。  
  
## <a name="remarks"></a>Remarks  
 系统函数可以在选择列表、WHERE 子句和任何允许使用表达式的地方使用。 有关详细信息，请参阅[表达式](../../t-sql/language-elements/expressions-transact-sql.md)和 [WHERE](../../t-sql/queries/where-transact-sql.md)。  
  
 由此系统函数返回的结果集将使用当前数据库的排序规则。  
  
 如果未指定 database_id，则 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 假定 object_id 在当前数据库上下文中   。 在其他数据库中引用 object_id 的查询将返回 NULL 或错误的结果  。 例如，以下查询中当前数据库上下文是 [!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]。 [!INCLUDE[ssDE](../../includes/ssde-md.md)]将尝试返回在该数据库（而非查询的 FROM 子句中指定的数据库）中指定的对象 ID 的对象架构名称。 因此，会返回不正确的信息。  
  
```sql
SELECT DISTINCT OBJECT_SCHEMA_NAME(object_id)  
FROM master.sys.objects;  
  
```  
  
 以下示例在 `master` 函数中指定 `OBJECT_SCHEMA_NAME` 数据库的数据库 ID，并返回正确的结果。  
  
```sql
SELECT DISTINCT OBJECT_SCHEMA_NAME(object_id, 1) AS schema_name  
FROM master.sys.objects;  
  
```  
  
## <a name="examples"></a>示例  
  
### <a name="a-returning-the-object-schema-name-and-object-name"></a>A. 返回对象架构名称和对象名称  
 以下示例返回所有缓存查询计划（为非临时语句或预定义语句）的对象架构名称、对象名称和 SQL 文本。  
  
```sql
SELECT DB_NAME(st.dbid) AS database_name,   
    OBJECT_SCHEMA_NAME(st.objectid, st.dbid) AS schema_name,  
    OBJECT_NAME(st.objectid, st.dbid) AS object_name,   
    st.text AS query_statement  
FROM sys.dm_exec_query_stats AS qs  
CROSS APPLY sys.dm_exec_sql_text(qs.sql_handle) AS st  
WHERE st.objectid IS NOT NULL;  
GO  
```  
  
### <a name="b-returning-three-part-object-names"></a>B. 返回由三部分组成的对象名称  
 以下示例返回所有数据库中所有对象的数据库名称、架构名称和对象名称，同时返回 `sys.dm_db_index_operational_stats` 动态管理视图中的其他所有列。  
  
```sql
SELECT QUOTENAME(DB_NAME(database_id))   
    + N'.'   
    + QUOTENAME(OBJECT_SCHEMA_NAME(object_id, database_id))   
    + N'.'   
    + QUOTENAME(OBJECT_NAME(object_id, database_id))  
    , *   
FROM sys.dm_db_index_operational_stats(null, null, null, null);  
GO  
```  
  
## <a name="see-also"></a>另请参阅  
 [元数据函数 (Transact-SQL)](../../t-sql/functions/metadata-functions-transact-sql.md)   
 [OBJECT_DEFINITION (Transact-SQL)](../../t-sql/functions/object-definition-transact-sql.md)   
 [OBJECT_ID (Transact-SQL)](../../t-sql/functions/object-id-transact-sql.md)   
 [OBJECT_NAME (Transact-SQL)](../../t-sql/functions/object-name-transact-sql.md)   
 [安全对象](../../relational-databases/security/securables.md)
