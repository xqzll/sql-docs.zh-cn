---
title: 元数据函数 (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- metadata [SQL Server], functions
- functions [SQL Server], metadata
ms.assetid: a18c12a9-59ad-4711-a862-39d8f28476b0
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 912067d715a36df3a2eede260d9e0fdbdfad8523
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "65948273"
---
# <a name="metadata-functions-transact-sql"></a>元数据函数 (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  以下标量函数返回有关数据库和数据库对象的信息：  
  
|||  
|-|-|  
|[@@PROCID](../../t-sql/functions/procid-transact-sql.md)|[INDEX_COL](../../t-sql/functions/index-col-transact-sql.md)|  
|[APP_NAME](../../t-sql/functions/app-name-transact-sql.md)|[INDEXKEY_PROPERTY](../../t-sql/functions/indexkey-property-transact-sql.md)|  
|[APPLOCK_MODE](../../t-sql/functions/applock-mode-transact-sql.md)|[INDEXPROPERTY](../../t-sql/functions/indexproperty-transact-sql.md)|  
|[APPLOCK_TEST](../../t-sql/functions/applock-test-transact-sql.md)|[NEXT VALUE FOR](../../t-sql/functions/next-value-for-transact-sql.md)|  
|[ASSEMBLYPROPERTY](../../t-sql/functions/assemblyproperty-transact-sql.md)|[OBJECT_DEFINITION](../../t-sql/functions/object-definition-transact-sql.md)|  
|[COL_LENGTH](../../t-sql/functions/col-length-transact-sql.md)|[OBJECT_ID](../../t-sql/functions/object-id-transact-sql.md)|  
|[COL_NAME](../../t-sql/functions/col-name-transact-sql.md)|[OBJECT_NAME](../../t-sql/functions/object-name-transact-sql.md)|  
|[COLUMNPROPERTY](../../t-sql/functions/columnproperty-transact-sql.md)|[OBJECT_SCHEMA_NAME](../../t-sql/functions/object-schema-name-transact-sql.md)|  
|[DATABASE_PRINCIPAL_ID](../../t-sql/functions/database-principal-id-transact-sql.md)|[OBJECTPROPERTY](../../t-sql/functions/objectproperty-transact-sql.md)|  
|[DATABASEPROPERTYEX](../../t-sql/functions/databasepropertyex-transact-sql.md)|[OBJECTPROPERTYEX](../../t-sql/functions/objectpropertyex-transact-sql.md)|  
|[DB_ID](../../t-sql/functions/db-id-transact-sql.md)|[ORIGINAL_DB_NAME](../../t-sql/functions/original-db-name-transact-sql.md)|  
|[DB_NAME](../../t-sql/functions/db-name-transact-sql.md)|[PARSENAME](../../t-sql/functions/parsename-transact-sql.md)|  
|[FILE_ID](../../t-sql/functions/file-id-transact-sql.md)|[SCHEMA_ID](../../t-sql/functions/schema-id-transact-sql.md)|  
|[FILE_IDEX](../../t-sql/functions/file-idex-transact-sql.md)|[SCHEMA_NAME](../../t-sql/functions/schema-name-transact-sql.md)|  
|[FILE_NAME](../../t-sql/functions/file-name-transact-sql.md)|[SCOPE_IDENTITY](../../t-sql/functions/scope-identity-transact-sql.md)|  
|[FILEGROUP_ID](../../t-sql/functions/filegroup-id-transact-sql.md)|[SERVERPROPERTY](../../t-sql/functions/serverproperty-transact-sql.md)|  
|[FILEGROUP_NAME](../../t-sql/functions/filegroup-name-transact-sql.md)|[STATS_DATE](../../t-sql/functions/stats-date-transact-sql.md)|  
|[FILEGROUPPROPERTY](../../t-sql/functions/filegroupproperty-transact-sql.md)|[TYPE_ID](../../t-sql/functions/type-id-transact-sql.md)|  
|[FILEPROPERTY](../../t-sql/functions/fileproperty-transact-sql.md)|[TYPE_NAME](../../t-sql/functions/type-name-transact-sql.md)|  
|[FULLTEXTCATALOGPROPERTY](../../t-sql/functions/fulltextcatalogproperty-transact-sql.md)|[TYPEPROPERTY](../../t-sql/functions/typeproperty-transact-sql.md)|  
|[FULLTEXTSERVICEPROPERTY](../../t-sql/functions/fulltextserviceproperty-transact-sql.md)|[VERSION](../../t-sql/functions/version-transact-sql-metadata-functions.md)|  
  
 所有元数据函数都具有不确定性。 这意味着即使同一组输入值，也不一定在每次调用这些函数时都返回相同的结果。  
  
## <a name="see-also"></a>另请参阅  
 [内置函数 (Transact-SQL)](~/t-sql/functions/functions.md)  
  
  

