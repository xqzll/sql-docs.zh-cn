---
title: sys.xml_schema_collections (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.xml_schema_collections_TSQL
- sys.xml_schema_collections
- xml_schema_collections
- xml_schema_collections_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.xml_schema_collections catalog view
ms.assetid: f3f7f3dc-029f-4942-ab3c-75fa9814e40f
author: pmasl
ms.author: pelopes
ms.reviewer: mikeray
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 9f7756d13f3a844d3cb8fb146a691698b69ba280
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "64945973"
---
# <a name="sysxmlschemacollections-transact-sql"></a>sys.xml_schema_collections (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  为每个 XML 架构集合返回一行。 XML 架构集合是一组命名的 XSD 定义。 XML 架构集合自身包含在关系架构中，由架构范围内的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 名称标识。 下列元组是唯一的：xml_collection_id、以及 schema_id 和 name。  
  
|列名|数据类型|Description|  
|-----------------|---------------|-----------------|  
|xml_collection_id|**int**|XML 架构集合的 ID。 在数据库中是唯一的。|  
|schema_id|**int**|包含此 XML 架构集合的关系架构的 ID。|  
|principal_id|**int**|如果不是架构所有者，则为特定所有者的 ID。 默认情况下，架构包含的对象由架构所有者拥有。 但是，可以通过使用 ALTER AUTHORIZATION 语句更改所有权指定备用所有者。<br /><br /> NULL = 没有代替的单个所有者。|  
|name|**sysname**|XML 架构集合的名称。|  
|create_date|**datetime**|创建 XML 架构集合的日期。|  
|modify_date|**datetime**|上次修改 XML 架构集合的日期。|  
  
## <a name="permissions"></a>权限  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 有关详细信息，请参阅 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)。  
  
## <a name="see-also"></a>请参阅  
 [目录视图 (Transact-SQL)](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [XML 架构&#40;XML 类型系统&#41;目录视图&#40;Transact SQL&#41;](../../relational-databases/system-catalog-views/xml-schemas-xml-type-system-catalog-views-transact-sql.md)   
 [查询 SQL Server 系统目录常见问题解答](../../relational-databases/system-catalog-views/querying-the-sql-server-system-catalog-faq.md)  
  
  
