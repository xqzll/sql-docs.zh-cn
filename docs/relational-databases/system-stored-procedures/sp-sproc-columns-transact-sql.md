---
title: sp_sproc_columns (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_sproc_columns
- sp_sproc_columns_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_sproc_columns
ms.assetid: 62c18c21-35c5-4772-be0d-ffdcc19c97ab
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 8fd3e7ba4880a5d908991d32faaa9c1a5275976f
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "63032740"
---
# <a name="spsproccolumns-transact-sql"></a>sp_sproc_columns (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  为当前环境中的单个存储过程或用户定义函数返回列信息。  
  
 ![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "主题链接图标") [TRANSACT-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>语法  
  
```  
-- Syntax for SQL Server, Azure SQL Database, Azure SQL Data Warehouse, Parallel Data Warehouse  
  
sp_sproc_columns [[@procedure_name = ] 'name']   
    [ , [@procedure_owner = ] 'owner']   
    [ , [@procedure_qualifier = ] 'qualifier']   
    [ , [@column_name = ] 'column_name']  
    [ , [@ODBCVer = ] 'ODBCVer']  
    [ , [@fUsePattern = ] 'fUsePattern']  
```  
  
## <a name="arguments"></a>参数  
`[ @procedure_name = ] 'name'` 是用于返回目录信息的名称。 *名称*是**nvarchar (** 390 **)** ，默认值为 %，表示当前数据库中的所有表。 支持通配符模式匹配。  
  
`[ @procedure_owner = ] 'owner'` 是该过程的名称。 *所有者*是**nvarchar (** 384 **)** ，默认值为 NULL。 支持通配符模式匹配。 如果*所有者*未指定，则遵循基础 dbms 的默认过程可见性规则将应用。  
  
 如果当前用户拥有具有指定名称的过程，则返回有关该过程的信息。 如果*所有者*未指定并且当前用户不是具有指定名称的过程**sp_sproc_columns**查找具有指定名称，由数据库所有者拥有的过程。 如果存在该过程，则返回有关该过程的列信息。  
  
`[ @procedure_qualifier = ] 'qualifier'` 过程限定符的名称。 *限定符*是**sysname**，默认值为 NULL。 多种 DBMS 产品支持表的三部分命名 (*qualifier.owner.name*)。 在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中，此参数表示数据库名称。 在某些产品中，该列表示表所在的数据库环境的服务器名。  
  
`[ @column_name = ] 'column_name'` 仅包含一列和所需的目录信息的只有一列时使用。 *column_name*是**nvarchar (** 384 **)** ，默认值为 NULL。 如果*column_name*是省略，则返回所有列。 支持通配符模式匹配。 为了达到最佳的互操作性，网关客户端应只采用 ISO 标准模式匹配（% 和 _ 通配符）。  
  
`[ @ODBCVer = ] 'ODBCVer'` 正在使用的 ODBC 版本。 *ODBCVer*是**int**，默认值为 2，指示 ODBC 2.0 版。 有关 ODBC 2.0 版和 ODBC 3.0 版之间差别的详细信息，请参阅 ODBC **SQLProcedureColumns** ODBC 3.0 版规范  
  
`[ @fUsePattern = ] 'fUsePattern'` 确定下划线 (_)、 百分号 （%） 和方括号 ([]) 字符被解释为通配符字符。 有效值为 0（模式匹配为关闭状态）和 1（模式匹配为打开状态）。 *fUsePattern*是**位**，默认值为 1。  
  
## <a name="return-code-values"></a>返回代码值  
 None  
  
## <a name="result-sets"></a>结果集  
  
|列名|数据类型|Description|  
|-----------------|---------------|-----------------|  
|**PROCEDURE_QUALIFIER**|**sysname**|过程限定符名称。 该列可以为 NULL。|  
|**PROCEDURE_OWNER**|**sysname**|过程所有者名称。 该列始终返回值。|  
|**PROCEDURE_NAME**|**nvarchar(** 134 **)**|过程名。 该列始终返回值。|  
|**COLUMN_NAME**|**sysname**|每个列的列名**TABLE_NAME**返回。 该列始终返回值。|  
|**COLUMN_TYPE**|**smallint**|该字段始终返回值：<br /><br /> 0 = SQL_PARAM_TYPE_UNKNOWN<br /><br /> 1 = SQL_PARAM_TYPE_INPUT<br /><br /> 2 = SQL_PARAM_TYPE_OUTPUT<br /><br /> 3 = SQL_RESULT_COL<br /><br /> 4 = SQL_PARAM_OUTPUT<br /><br /> 5 = SQL_RETURN_VALUE|  
|**DATA_TYPE**|**smallint**|ODBC 数据类型的整数代码。 如果此数据类型无法映射到 ISO 类型，则值为 NULL。 中返回的本机数据类型名称**TYPE_NAME**列。|  
|**TYPE_NAME**|**sysname**|数据类型的字符串表示形式。 这是由基础 DBMS 表示的数据类型名称。|  
|**PRECISION**|**int**|有效数字位数。 返回值**精度**列是以 10 为基数。|  
|**LENGTH**|**int**|数据的传输大小。|  
|**SCALE**|**smallint**|小数点右边的数字位数。|  
|**RADIX**|**smallint**|数值类型的基数。|  
|**可以为 NULL**|**smallint**|指定为空性：<br /><br /> 1 = 可创建允许空值的数据类型。<br /><br /> 0 = 不允许空值。|  
|**REMARKS**|**varchar(** 254 **)**|对过程列的说明。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 不为此列返回值。|  
|**COLUMN_DEF**|**nvarchar(** 4000 **)**|列的默认值。|  
|**SQL_DATA_TYPE**|**smallint**|显示在 SQL 数据类型的值**类型**的描述符字段。 此列与 DATA_TYPE 列相同，datetime 和 ISO interval 数据类型除外    。 该列始终返回值。|  
|**SQL_DATETIME_SUB**|**smallint**|如果 SQL_DATA_TYPE 的值为 SQL_DATETIME 或 SQL_INTERVAL，则为 datetime ISO interval 子代码      。 对于数据类型以外**datetime**和 ISO**间隔**，此字段为 NULL。|  
|**CHAR_OCTET_LENGTH**|**int**|以字节为单位的最大长度**字符**或**二进制**数据类型列。 对于所有其他数据类型，此列返回 NULL。|  
|**ORDINAL_POSITION**|**int**|列在表中的序号位置。 表中的第一列为 1。 该列始终返回值。|  
|**IS_NULLABLE**|**varchar(254)**|表中的列的为 Null 性。 根据 ISO 规则确定为 Null 性。 遵从 ISO 标准的 DBMS 不能返回空字符串。<br /><br /> 如果列可包含 NULL，则显示 YES；如果列不能包含 NULL，则显示 NO。<br /><br /> 如果为 Null 性为未知，该列将返回零长度字符串。<br /><br /> 该列返回的值与 NULLABLE 列返回的值不同。|  
|**SS_DATA_TYPE**|**tinyint**|扩展存储过程使用的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据类型。 有关详细信息，请参阅[数据类型 (Transact-SQL)](../../t-sql/data-types/data-types-transact-sql.md)。|  
  
## <a name="remarks"></a>备注  
 **sp_sproc_columns**等效于**SQLProcedureColumns** ODBC 中。 返回的结果按排序**PROCEDURE_QUALIFIER**， **PROCEDURE_OWNER**， **PROCEDURE_NAME**，以及参数在过程中出现的顺序定义。  
  
## <a name="permissions"></a>权限  
 需要对架构的 SELECT 权限。  
  
## <a name="see-also"></a>请参阅  
 [目录存储的过程&#40;Transact SQL&#41;](../../relational-databases/system-stored-procedures/catalog-stored-procedures-transact-sql.md)   
 [系统存储过程 (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
