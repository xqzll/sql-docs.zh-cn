---
title: SET ANSI_WARNINGS (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 12/04/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- SET ANSI_WARNINGS
- ANSI_WARNINGS_TSQL
- ANSI_WARNINGS
- SET_ANSI_WARNINGS_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- errors [SQL Server], ISO standard behavior
- warnings [SQL Server]
- SET ANSI_WARNINGS statement
- ANSI_WARNINGS option
ms.assetid: f82aaab0-334f-427b-89b0-de4af596b4fa
author: CarlRabeler
ms.author: carlrab
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: af30fd34d42b296e9b83bbd537dcff411cd42608
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "62639094"
---
# <a name="set-ansiwarnings-transact-sql"></a>SET ANSI_WARNINGS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  对几种错误情况指定 ISO 标准行为。  
  
 ![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "主题链接图标") [TRANSACT-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>语法
  
```
-- Syntax for SQL Server and Azure SQL Database
  
SET ANSI_WARNINGS { ON | OFF }
```

```
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse

SET ANSI_WARNINGS ON
```

## <a name="remarks"></a>Remarks  
 SET ANSI_WARNINGS 可以影响下列情况：  
  
-   设置为 ON 时，如果聚合函数（如 SUM、AVG、MAX、MIN、STDEV、STDEVP、VAR、VARP 或 COUNT）中出现空值，将生成警告消息。 设置为 OFF 时，不发出警告。  
  
-   设置为 ON 时，被零除错误和算术溢出错误将导致回滚语句，并生成错误消息。 设置为 OFF 时，被零除错误和算术溢出错误将导致返回空值。 如果尝试对 character、Unicode 或 binary 列执行 INSERT 或 UPDATE 操作，而这些列中的新值长度超出列的最大大小，那么，在发生被零除错误或算术溢出错误时，将导致返回 NULL 值   。 如果 SET ANSI_WARNINGS 为 ON，则根据 ISO 标准，将取消 INSERT 或 UPDATE。 字符列的尾随空格和二进制列的尾随零都将被忽略。 设置为 OFF 时，数据将剪裁为列的大小，并且语句执行成功。  
  
> [!NOTE]  
> 在 binary 或 varbinary 数据转换中发生截断时，不管 SET 选项如何设置，都不发出警告或错误消息   。  
  
> [!NOTE]  
> 在存储过程和用户定义函数中传递参数，或者在批处理语句中声明和设置变量时，不执行 ANSI_WARNINGS。 例如，如果将一个变量定义为 char(3)，然后将其值设置为大于三个字符，则数据会被截断为定义的大小，并且 INSERT 或 UPDATE 语句可以成功执行  。  
  
可以使用 sp_configure 的 user options 选项，为服务器的所有连接设置 ANSI_WARNINGS 的默认设置。 有关详细信息，请参阅本主题后面的 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)不熟悉的读者。  
  
创建或操作对索引视图或计算列的索引时，ANSI_WARNINGS 必须为 ON。 如果 SET ANSI_WARNINGS 为 OFF，对计算列或索引视图的索引所在的表执行 CREATE、UPDATE、INSERT 和 DELETE 语句将失败。 有关计算列的索引视图和索引需要的 SET 选项设置的详细信息，请参阅 [SET Statements (Transact-SQL)](../../t-sql/statements/set-statements-transact-sql.md) 中的“使用 SET 语句时的注意事项”。  
  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 包含 ANSI_WARNINGS 数据库选项。 此选项与 SET ANSI_WARNINGS 等效。 如果 SET ANSI_WARNINGS 为 ON，则发生被零除、字符串超出数据库列及其他类似错误时，将引发错误或警告。 如果 SET ANSI_WARNINGS 为 OFF，则不会引发这些错误和警告。 model 数据库中的 SET ANSI_WARNINGS 默认值为 OFF。 如果未指定，则应用 ANSI_WARNINGS 设置。 如果 SET ANSI_WARNINGS 为 OFF，则 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 使用 [sys.databases](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md) 目录视图中 is_ansi_warnings_on 列的值。  
  
> [!IMPORTANT]
> 执行分布式查询时，应将 ANSI_WARNINGS 设置为 ON。  
  
 进行连接时，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC 驱动程序和 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB 提供程序会自动将 ANSI_WARNINGS 设置为 ON。 这可以在 ODBC 数据源、ODBC 连接属性（它们在连接前在应用程序中设置）中进行配置。 从 DB-Library 应用程序连接时，SET ANSI_WARNINGS 的默认值为 OFF。  
  
ANSI_DEFAULTS 为 ON 时，将启用 ANSI_WARNINGS。  
  
ANSI_WARNINGS 的设置是在执行或运行时定义的，而不是在分析时定义的。  
  
如果 SET ARITHABORT 或 SET ARITHIGNORE 为 OFF，而 SET ANSI_WARNINGS 为 ON，则遇到被零除或溢出错误时，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 仍会返回错误消息。  
  
要查看此设置的当前设置，请运行以下查询。  
  
```sql  
DECLARE @ANSI_WARN VARCHAR(3) = 'OFF';  
IF ( (8 & @@OPTIONS) = 8 ) SET @ANSI_WARN = 'ON';  
SELECT @ANSI_WARN AS ANSI_WARNINGS;  
```  
  
## <a name="permissions"></a>权限  
要求 **公共** 角色具有成员身份。  
  
## <a name="examples"></a>示例  
下面的示例阐释了 SET ANSI_WARNINGS 为 ON 和 OFF 时的上述三种情况。  
  
```sql  
CREATE TABLE T1   
(  
   a int,   
   b int NULL,   
   c varchar(20)  
);  
GO  
  
SET NOCOUNT ON;  
  
INSERT INTO T1   
VALUES (1, NULL, '')   
      ,(1, 0, '')  
      ,(2, 1, '')  
      ,(2, 2, '');  
  
SET NOCOUNT OFF;  
GO  
```

现在将 ANSI_WARNINGS 设置为 ON 并测试。

```sql
PRINT '**** Setting ANSI_WARNINGS ON';  
GO  
  
SET ANSI_WARNINGS ON;  
GO  
  
PRINT 'Testing NULL in aggregate';  
GO  
SELECT a, SUM(b)   
FROM T1   
GROUP BY a;  
GO  
  
PRINT 'Testing String Overflow in INSERT';  
GO  
INSERT INTO T1   
VALUES (3, 3, 'Text string longer than 20 characters');  
GO  
  
PRINT 'Testing Divide by zero';  
GO  
SELECT a / b AS ab   
FROM T1;  
GO  
```

现在将 ANSI_WARNINGS 设置为 OFF 并测试。

```sql
PRINT '**** Setting ANSI_WARNINGS OFF';  
GO  
SET ANSI_WARNINGS OFF;  
GO  
  
PRINT 'Testing NULL in aggregate';  
GO  
SELECT a, SUM(b)   
FROM T1   
GROUP BY a;  
GO  
  
PRINT 'Testing String Overflow in INSERT';  
GO  
INSERT INTO T1   
VALUES (4, 4, 'Text string longer than 20 characters');  
GO  
SELECT a, b, c   
FROM T1  
WHERE a = 4;  
GO  
  
PRINT 'Testing Divide by zero';  
GO  
SELECT a / b AS ab   
FROM T1;  
GO  
  
DROP TABLE T1;  
```  
  
## <a name="see-also"></a>另请参阅  
 [INSERT (Transact-SQL)](../../t-sql/statements/insert-transact-sql.md)   
 [SELECT (Transact-SQL)](../../t-sql/queries/select-transact-sql.md)   
 [SET 语句 (Transact-SQL)](../../t-sql/statements/set-statements-transact-sql.md)   
 [SET ANSI_DEFAULTS (Transact-SQL)](../../t-sql/statements/set-ansi-defaults-transact-sql.md)   
 [SESSIONPROPERTY (Transact-SQL)](../../t-sql/functions/sessionproperty-transact-sql.md)  
  
  
