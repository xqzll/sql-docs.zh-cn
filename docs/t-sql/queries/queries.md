---
title: 查询 | Microsoft Docs
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
dev_langs:
- TSQL
ms.assetid: 5ff02a32-e8d3-479c-ae8b-07581e41f5f8
author: VanMSFT
ms.author: vanto
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 97c7a7f45408fa4e6ea314bd04a0d35d127af660
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "66822463"
---
# <a name="queries"></a>查询

[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  数据操作语言 (DML) 是用于检索和使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 和 SQL 数据库中的数据的词汇。 大部分也可在 SQL 数据仓库和 PDW 中使用（请查看各语句了解详细信息）。 使用这些语句可以从 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库添加、修改、查询或删除数据。  
  
## <a name="in-this-section"></a>本节内容  
 下表列出了 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 使用的 DML 语句。  
  
|||  
|-|-|  
|[BULK INSERT (Transact-SQL)](../../t-sql/statements/bulk-insert-transact-sql.md)|[SELECT (Transact-SQL)](../../t-sql/queries/select-transact-sql.md)|  
|[DELETE (Transact-SQL)](../../t-sql/statements/delete-transact-sql.md)|[UPDATE (Transact-SQL)](../../t-sql/queries/update-transact-sql.md)|  
|[INSERT (Transact-SQL)](../../t-sql/statements/insert-transact-sql.md)|[UPDATETEXT (Transact-SQL)](../../t-sql/queries/updatetext-transact-sql.md)|  
|[MERGE (Transact-SQL)](../../t-sql/statements/merge-transact-sql.md)|[WRITETEXT (Transact-SQL)](../../t-sql/queries/writetext-transact-sql.md)|  
|[READTEXT (Transact-SQL)](../../t-sql/queries/readtext-transact-sql.md)| &nbsp; |  
| &nbsp; | &nbsp; |

 下表列出了在多个 DML 语句或子句中使用的子句。  
  
|子句|可用于的语句|  
|------------|-------------------------------------|  
|[FROM (Transact-SQL)](../../t-sql/queries/from-transact-sql.md)|DELETE、SELECT、UPDATE|  
|[提示 (Transact-SQL)](../../t-sql/queries/hints-transact-sql.md)|DELETE、INSERT、SELECT、UPDATE|  
|[OPTION 子句 (Transact-SQL)](../../t-sql/queries/option-clause-transact-sql.md)|DELETE、SELECT、UPDATE|  
|[OUTPUT 子句 (Transact-SQL)](../../t-sql/queries/output-clause-transact-sql.md)|DELETE、INSERT、MERGE、UPDATE|  
|[搜索条件 (Transact-SQL)](../../t-sql/queries/search-condition-transact-sql.md)|DELETE、MERGE、SELECT、UPDATE|  
|[表值构造函数 (Transact-SQL)](../../t-sql/queries/table-value-constructor-transact-sql.md)|FROM、INSERT、MERGE|  
|[TOP (Transact-SQL)](../../t-sql/queries/top-transact-sql.md)|DELETE、INSERT、MERGE、SELECT、UPDATE|  
|[WHERE (Transact-SQL)](../../t-sql/queries/where-transact-sql.md)|DELETE、SELECT、UPDATE、MATCH|  
|[WITH common_table_expression (Transact-SQL)](../../t-sql/queries/with-common-table-expression-transact-sql.md)|DELETE、INSERT、MERGE、SELECT、UPDATE|  
| &nbsp; | &nbsp; |
