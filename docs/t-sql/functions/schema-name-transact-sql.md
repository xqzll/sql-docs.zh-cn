---
title: SCHEMA_NAME (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- SCHEMA_NAME
- SCHEMA_NAME_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- SCHEMA_NAME function
- schemas [SQL Server], names
ms.assetid: 20071b77-2b6e-4ce7-a8e3-fa71480baf73
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: b3692f3c0bc1c09a5841fcff146ceb9f4489548c
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "65945426"
---
# <a name="schemaname-transact-sql"></a>SCHEMA_NAME (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  返回与架构 ID 关联的架构名称。  
  
 ![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "主题链接图标") [TRANSACT-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>语法  
  
```  
SCHEMA_NAME ( [ schema_id ] )  
```  
  
## <a name="arguments"></a>参数  
  
|术语|定义|  
|----------|----------------|  
|schema_id |架构的 ID。 schema_id 是 int   。如果没有定义 schema_id，则 SCHEMA_NAME 将返回调用方的默认架构的名称  。|  
  
## <a name="return-types"></a>返回类型  
 **sysname**  
  
 schema_id 不是有效 ID 时，返回 NULL  。  
  
## <a name="remarks"></a>Remarks  
 SCHEMA_NAME 返回系统架构和用户定义架构的名称。 可以在选择列表、WHERE 子句和任何允许使用表达式的地方调用 SCHEMA_NAME。  
  
## <a name="examples"></a>示例  
  
### <a name="a-returning-the-name-of-the-default-schema-of-the-caller"></a>A. 返回调用方的默认架构的名称  
  
```  
SELECT SCHEMA_NAME();  
```  
  
### <a name="b-returning-the-name-of-a-schema-by-using-an-id"></a>B. 使用 ID 返回架构的名称  
  
```  
SELECT SCHEMA_NAME(1);  
```  
  
## <a name="see-also"></a>另请参阅  
 [表达式 (Transact-SQL)](../../t-sql/language-elements/expressions-transact-sql.md)   
 [SCHEMA_ID (Transact-SQL)](../../t-sql/functions/schema-id-transact-sql.md)   
 [sys.schemas (Transact-SQL)](../../relational-databases/system-catalog-views/schemas-catalog-views-sys-schemas.md)   
 [sys.database_principals (Transact-SQL)](../../relational-databases/system-catalog-views/sys-database-principals-transact-sql.md)   
 [元数据函数 (Transact-SQL)](../../t-sql/functions/metadata-functions-transact-sql.md)   
 [WHERE (Transact-SQL)](../../t-sql/queries/where-transact-sql.md)  
  
  

