---
title: FILE_IDEX (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- FILE_IDEX
- FILE_IDEX_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- FILE_IDEX function
- IDs [SQL Server], files
- file IDs [SQL Server]
- names [SQL Server], files
- identification numbers [SQL Server], files
- file names [SQL Server], FILE_IDEX
ms.assetid: 7532fea5-ee5e-4edd-b98b-111a7ba56c8e
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 44cb6fa7f32616f7a1616c334c438b7a752546e3
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "65946052"
---
# <a name="fileidex-transact-sql"></a>FILE_IDEX (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

此函数返回当前数据库的数据、日志或全文文件的指定逻辑名称的文件标识 (ID) 号。 
  
![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "主题链接图标") [TRANSACT-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>语法  
  
```  
FILE_IDEX ( file_name )  
```  
  
## <a name="arguments"></a>参数  
 file_name   
类型为 sysname  的表达式，它返回文件名称的文件 ID 值“FILE_IDEX”。 
  
## <a name="return-types"></a>返回类型  
**int**  
  
出现错误时，返回 NULL   
  
## <a name="remarks"></a>Remarks  
file_name  对应于 [sys.master_files](../../relational-databases/system-catalog-views/sys-master-files-transact-sql.md) 或 [sys.database_files](../../relational-databases/system-catalog-views/sys-database-files-transact-sql.md) 目录视图中的 name  列中所显示的逻辑文件名。  
  
在 SELECT 列表、WHERE 子句或支持使用表达式的任何位置使用 `FILE_IDEX`。 有关详细信息，请参阅[表达式 (Transact-SQL)](../../t-sql/language-elements/expressions-transact-sql.md)。  
  
## <a name="examples"></a>示例  
  
### <a name="a-retrieving-the-file-id-of-a-specified-file"></a>A. 检索指定文件的文件 ID  
此示例返回 `AdventureWorks_Data` 文件的文件 ID。  
  
```sql  
USE AdventureWorks2012;  
GO  
SELECT FILE_IDEX('AdventureWorks2012_Data') AS 'File ID';  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
File ID   
-------   
1  
(1 row(s) affected)  
```  
  
### <a name="b-retrieving-the-file-id-when-the-file-name-is-not-known"></a>B. 在文件名未知时检索文件 ID  
此示例返回 `AdventureWorks` 日志文件的文件 ID。 Transact-SQL (T-SQL) 代码段从 `sys.database_files` 目录视图中选择逻辑文件名称，其中文件类型等于 `1`（日志）。  
  
```sql  
USE AdventureWorks2012;  
GO  
SELECT FILE_IDEX((SELECT TOP (1) name FROM sys.database_files WHERE type = 1)) AS 'File ID';  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
File ID   
-------   
2  
```  
  
### <a name="c-retrieving-the-file-id-of-a-full-text-catalog-file"></a>C. 检索全文目录文件的文件 ID  
此示例返回全文文件的文件 ID。 T-SQL 代码段从 `sys.database_files` 目录视图中选择逻辑文件名称，其中文件类型等于 `4`（全文）。 如果全文目录不存在，则此代码将返回“NULL”。
  
```sql  
SELECT FILE_IDEX((SELECT name FROM sys.master_files WHERE type = 4))  
AS 'File_ID';  
```  
  
## <a name="see-also"></a>另请参阅  
 [元数据函数 (Transact-SQL)](../../t-sql/functions/metadata-functions-transact-sql.md)   
 [sys.database_files (Transact-SQL)](../../relational-databases/system-catalog-views/sys-database-files-transact-sql.md)   
 [sys.master_files (Transact-SQL)](../../relational-databases/system-catalog-views/sys-master-files-transact-sql.md)  
  
  
