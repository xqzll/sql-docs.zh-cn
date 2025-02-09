---
title: sp_syscollector_stop_collection_set (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_syscollector_stop_collection_set_TSQL
- sp_syscollector_stop_collection_set
dev_langs:
- TSQL
helpviewer_keywords:
- sp_syscollector_stop_collection_set
- data collector [SQL Server], stored procedures
ms.assetid: 4668cfb7-462f-40d0-948c-8f740a792a4d
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: dd5c396db88a8377a46bd965b664bc2a667d51de
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "63001523"
---
# <a name="spsyscollectorstopcollectionset-transact-sql"></a>sp_syscollector_stop_collection_set (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  停止收集组。  
  
 ![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "主题链接图标") [TRANSACT-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>语法  
  
```  
  
sp_syscollector_stop_collection_set   
    [ [ @collection_set_id = ] collection_set_id ]  
    , [ [ @name = ] 'name' ]  
    , [ [ @stop_collection_job = ] stop_collection_job ]  
```  
  
## <a name="arguments"></a>参数  
 [ @collection_set_id = ] *collection_set_id*  
 收集组的唯一本地标识符。 *collection_set_id*是**int**默认值为 NULL。 *collection_set_id*时，必须具有值*名称*为 NULL。  
  
 [ @name = ] '*name*'  
 是收集组的名称。 *名称*是**sysname**默认值为 NULL。 *名称*时，必须具有值*collection_set_id*为 NULL。  
  
 [ @stop_collection_job = ] *stop_collection_job*  
 指定应停止收集组的收集作业（如果正在运行）。 *stop_collection_job*是**位**默认值为 1。  
  
 *stop_collection_job*仅适用于收集组收集模式设置为缓存。 有关详细信息，请参阅[sp_syscollector_create_collection_set &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-syscollector-create-collection-set-transact-sql.md)。  
  
## <a name="return-code-values"></a>返回代码值  
 **0** （成功） 或**1** （失败）  
  
## <a name="remarks"></a>备注  
 sp_syscollector_create_collection_set 必须在 msdb 系统数据库的上下文中运行。  
  
## <a name="permissions"></a>权限  
 必须具有 dc_operator（拥有 EXECUTE 权限）固定数据库角色的成员身份才能执行此过程。  
  
## <a name="examples"></a>示例  
 以下示例使用收集组的标识符停止此收集组。  
  
```  
USE msdb;  
GO  
EXEC sp_syscollector_stop_collection_set @collection_set_id = 1;  
```  
  
## <a name="see-also"></a>请参阅  
 [数据收集](../../relational-databases/data-collection/data-collection.md)   
 [数据收集器存储过程 (Transact-SQL)](../../relational-databases/system-stored-procedures/data-collector-stored-procedures-transact-sql.md)  
  
  
