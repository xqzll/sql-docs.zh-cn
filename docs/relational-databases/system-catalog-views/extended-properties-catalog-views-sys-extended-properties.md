---
title: sys.extended_properties (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.extended_properties
- sys.extended_properties_TSQL
- extended_properties
- extended_properties_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.extended_properties catalog view
ms.assetid: 439b7299-dce3-4d26-b1c7-61be5e0df82a
author: MashaMSFT
ms.author: mathoma
manager: craigg
monikerRange: '>=aps-pdw-2016||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 7ffac91aef6e7b761705e477a9d5b433d6e3f2fe
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "63008504"
---
# <a name="extended-properties-catalog-views---sysextendedproperties"></a>扩展属性目录视图-sys.extended_properties
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

  针对当前数据库中的每个扩展属性返回一行。  
  
|列名|数据类型|Description|  
|-----------------|---------------|-----------------|  
|class|**tinyint**|标识其上存在属性的项类。 可以为以下各项之一：<br /><br /> 0 = 数据库<br /><br /> 1 = 对象或列<br /><br /> 2 = 参数<br /><br /> 3 = 架构<br /><br /> 4 = 数据库主体<br /><br /> 5 = 程序集<br /><br /> 6 = 类型<br /><br /> 7 = 索引<br /><br /> 10 = XML 架构集合<br /><br /> 15 = 消息类型<br /><br /> 16 = 服务约定<br /><br /> 17 = 服务<br /><br /> 18 = 远程服务绑定<br /><br /> 19 = 路由<br /><br /> 20 = 数据空间（文件组或分区方案）<br /><br /> 21 = 分区函数<br /><br /> 22 = 数据库文件<br /><br /> 27 = 计划指南|  
|class_desc|**nvarchar(60)**|其上存在扩展属性的类的说明。 可以为以下各项之一：<br /><br /> DATABASE<br /><br /> OBJECT_OR_COLUMN<br /><br /> 参数<br /><br /> SCHEMA<br /><br /> DATABASE_PRINCIPAL<br /><br /> ASSEMBLY<br /><br /> TYPE<br /><br /> INDEX<br /><br /> XML_SCHEMA_COLLECTION<br /><br /> MESSAGE_TYPE<br /><br /> SERVICE_CONTRACT<br /><br /> SERVICE<br /><br /> REMOTE_SERVICE_BINDING<br /><br /> ROUTE<br /><br /> DATASPACE<br /><br /> PARTITION_FUNCTION<br /><br /> DATABASE_FILE<br /><br /> PLAN_GUIDE|  
|major_id|**int**|其上存在扩展属性的项的 ID，根据项类进行解释。 对于大多数项，该 ID 适用于类所表示的项。 下列是非标准主 ID 的解释：<br /><br /> 如果 class 为 0，则 major_id 始终为 0。<br /><br /> 如果 class 为 1、2 或 7，则 major_id 为 object_id。|  
|minor_id|**int**|其上存在扩展属性的项的辅助 ID，根据项类进行解释。 对于大多数项，ID 为 0；否则，ID 为下列值之一：<br /><br /> 如果 class = 1，则 minor_id 在项为列的情况下等于 column_id，在项为对象的情况下等于 0。<br /><br /> 如果 class = 2，则 minor_id 为 parameter_id。<br /><br /> 如果 class = 7，则 minor _id 为 index_id。|  
|name|**sysname**|属性名，其 class、major_id 和 minor_id 是唯一的。|  
|value|**sql_variant**|扩展属性的值。|  
  
## <a name="permissions"></a>权限  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 有关详细信息，请参阅 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)。  
  
## <a name="see-also"></a>请参阅  
 [目录视图 (Transact-SQL)](../../relational-databases/system-catalog-views/catalog-views-transact-sql.md)   
 [扩展属性目录视图&#40;Transact SQL&#41;](https://msdn.microsoft.com/library/f39fd324-efd4-4468-884c-bf77ed1a026f)   
 [sys.fn_listextendedproperty &#40;Transact-SQL&#41;](../../relational-databases/system-functions/sys-fn-listextendedproperty-transact-sql.md)   
 [sp_addextendedproperty &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addextendedproperty-transact-sql.md)   
 [sp_dropextendedproperty &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropextendedproperty-transact-sql.md)   
 [sp_updateextendedproperty &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-updateextendedproperty-transact-sql.md)  
  
  
