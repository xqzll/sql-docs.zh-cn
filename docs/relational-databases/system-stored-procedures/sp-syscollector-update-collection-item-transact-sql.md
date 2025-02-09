---
title: sp_syscollector_update_collection_item (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 08/09/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_syscollector_update_collection_item
- sp_syscollector_update_collection_item_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- data collector [SQL Server], stored procedures
- sp_syscollector_update_collection_item
ms.assetid: 7a0d36c8-c6e9-431d-a5a4-6c1802bce846
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: e1eb288a7bb99f5f24f05e4369836d21031f7e68
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "63001389"
---
# <a name="spsyscollectorupdatecollectionitem-transact-sql"></a>sp_syscollector_update_collection_item (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  用于修改用户定义的收集项的属性，或重命名用户定义的收集项。  
  
 
 ![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "主题链接图标") [TRANSACT-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>语法  
  
```  
  
sp_syscollector_update_collection_item   
      [ [ @collection_item_id = ] collection_item_id ]  
    , [ [ @name = ] 'name' ]  
    , [ [ @new_name = ] 'new_name' ]  
    , [ [ @frequency = ] frequency ]  
    , [ [ @parameters = ] 'parameters' ]  
```  
  
## <a name="arguments"></a>参数  
 [ @collection_item_id = ] *collection_item_id*  
 标识收集项的唯一标识符。 *collection_item_id*是**int**默认值为 NULL。 *collection_item_id*时，必须具有值*名称*为 NULL。  
  
 [ @name = ] '*name*'  
 收集项的名称。 *名称*是**sysname**默认值为 NULL。 *名称*时，必须具有值*collection_item_id*为 NULL。  
  
 [ @new_name = ] '*new_name*'  
 收集项的新名称。 *new_name*是**sysname**，并且如果使用，不能为空字符串。  
  
 *new_name*必须是唯一的。 有关当前收集项名称的列表，请查询 syscollector_collection_items 系统视图。  
  
 [ @frequency = ] *frequency*  
 此收集项收集数据的频率（以秒为单位）。 *频率*是**int**，默认值为 5，可以指定的最小值。  
  
 [ @parameters = ] '*parameters*'  
 收集项的输入参数。 *参数*是**xml**默认值为 NULL。 *参数*架构必须与收集器类型的参数架构匹配。  
  
## <a name="return-code-values"></a>返回代码值  
 **0** （成功） 或 1 （失败）  
  
## <a name="remarks"></a>备注  
 如果将收集组设置为非缓存模式，则忽略更改频率，这是因为此模式将导致数据收集和上载按为收集组指定的计划执行。 若要查看收集组的状态，请运行下面的查询。 将 `<collection_item_id>` 替换为要更新的收集项的 ID。  
  
```  
USE msdb;  
GO  
SELECT cs.collection_set_id, collection_set_uid, cs.name   
    ,'is running' = CASE WHEN is_running =  0 THEN 'No' ELSE 'Yes' END  
    ,'cache mode' = CASE WHEN collection_mode = 0 THEN 'Cached mode' ELSE 'Non-cached mode' END  
FROM syscollector_collection_sets AS cs  
JOIN syscollector_collection_items AS ci   
ON ci.collection_set_id = cs.collection_set_id  
WHERE collection_item_id = <collection_item_id>;  
```  
  
## <a name="permissions"></a>权限  
 要求具有 dc_admin 或 dc_operator（拥有 EXECUTE 权限）固定数据库角色的成员身份才能执行此过程。 尽管 dc_operator 可以运行此存储过程，但是此角色的成员在其属性更改权限方面受到限制。 下列属性只能由 dc_admin 更改：  
  
-   @new_name  
  
-   @parameters  
  
## <a name="examples"></a>示例  
 以下示例基于在中定义的示例中创建的集合项[sp_syscollector_create_collection_item &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-syscollector-create-collection-item-transact-sql.md)。  
  
### <a name="a-changing-the-collection-frequency"></a>A. 更改收集频率  
 以下示例更改指定收集项的收集频率。  
  
```  
USE msdb;  
GO  
EXEC sp_syscollector_update_collection_item   
@name = N'My custom TSQL query collector item',  
@frequency = 3000;  
GO  
```  
  
### <a name="b-renaming-a-collection-item"></a>B. 重命名收集项  
 以下示例重命名收集项。  
  
```  
USE msdb;  
GO  
EXEC sp_syscollector_update_collection_item   
@name = N'My custom TSQL query collector item',  
@new_name = N'My modified TSQL item';  
GO  
```  
  
### <a name="c-changing-the-parameters-of-a-collection-item"></a>C. 更改收集项的参数  
 以下示例更改与收集项关联的参数。 已更改 `<Value>` 属性中定义的语句，并将 `UseSystemDatabases` 属性设置为 False。 若要查看此项的当前参数，请查询 syscollector_collection_items 系统视图中的参数列。 您可能需要修改 `@collection_item_id` 的值。  
  
```  
USE msdb;  
GO  
EXEC sp_syscollector_update_collection_item   
@collection_item_id = 9,   
@parameters = '  
    \<ns:TSQLQueryCollector xmlns:ns="DataCollectorType">  
        <Query>  
            <Value>SELECT * FROM sys.dm_db_index_usage_stats</Value>  
            <OutputTable>MyOutputTable</OutputTable>  
        </Query>  
        <Databases>  
            <Database> UseSystemDatabases = "false"   
                       UseUserDatabases = "true"</Database>  
        </Databases>  
    \</ns:TSQLQueryCollector>';  
GO  
```  
  
## <a name="see-also"></a>请参阅  
 [系统存储过程 (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [数据收集](../../relational-databases/data-collection/data-collection.md)   
 [sp_syscollector_create_collection_item &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-syscollector-create-collection-item-transact-sql.md)   
 [syscollector_collection_items (Transact-SQL)](../../relational-databases/system-catalog-views/syscollector-collection-items-transact-sql.md)  
  
  
