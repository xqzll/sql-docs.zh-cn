---
title: sp_helpmergedeleteconflictrows (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/04/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_helpmergedeleteconflictrows
- sp_helpmergedeleteconflictrows_TSQL
helpviewer_keywords:
- sp_helpmergedeleteconflictrows
ms.assetid: 222be651-5690-4341-9dfb-f9ec1d80c970
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 6c60f56980aedc29c8262089748a77f113cc0449
ms.sourcegitcommit: c44014af4d3f821e5d7923c69e8b9fb27aeb1afd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/27/2019
ms.locfileid: "58536479"
---
# <a name="sphelpmergedeleteconflictrows-transact-sql"></a>sp_helpmergedeleteconflictrows (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  返回有关丢失删除的冲突的数据行的信息。 如果使用了分散的冲突日志，则将在发布服务器上对发布数据库执行此存储过程，或在订阅服务器上对订阅数据库执行此存储过程。  
  
 ![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "主题链接图标") [TRANSACT-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>语法  
  
```  
  
sp_helpmergedeleteconflictrows [ [ @publication = ] 'publication']  
    [ , [ @source_object = ] 'source_object']  
    [ , [ @publisher = ] 'publisher'  
    [ , [ @publisher_db = ] 'publsher_db'  
```  
  
## <a name="arguments"></a>参数  
`[ @publication = ] 'publication'` 是发布的名称。 *发布*是**sysname**，默认值为**%**。 如果指定了发布，将返回由该发布限定的所有冲突。  
  
`[ @source_object = ] 'source_object'` 是源对象的名称。 *source_object*是**nvarchar(386)**，默认值为 NULL。  
  
`[ @publisher = ] 'publisher'` 是发布服务器的名称。*发布服务器*是**sysname**，默认值为 NULL。  
  
`[ @publisher_db = ] 'publisher_db'` 是发布服务器数据库的名称。*publisher_db*是**sysname**，默认值为 NULL。  
  
## <a name="result-sets"></a>结果集  
  
|列名|数据类型|Description|  
|-----------------|---------------|-----------------|  
|**source_object**|**nvarchar(386)**|删除冲突的源对象。|  
|**rowguid**|**uniqueidentifier**|删除冲突的行标识符。|  
|**conflict_type**|**int**|指示冲突类型的代码：<br /><br /> **1** = UpdateConflict:在行级别检测到冲突。<br /><br /> **2** = ColumnUpdateConflict:在列级检测到冲突。<br /><br /> **3** = UpdateDeleteWinsConflict:删除在冲突中获胜。<br /><br /> **4** = UpdateWinsDeleteConflict:冲突中落选的已删除的 rowguid 将记录在此表。<br /><br /> **5** = UploadInsertFailed:无法在发布服务器上应用插入从订阅服务器。<br /><br /> **6** = DownloadInsertFailed:无法在订阅服务器上应用插入从发布服务器。<br /><br /> **7** = UploadDeleteFailed:到发布服务器，无法上载在订阅服务器上删除。<br /><br /> **8** = DownloadDeleteFailed:删除发布服务器上的无法下载到订阅服务器。<br /><br /> **9** = UploadUpdateFailed:无法在发布服务器上应用在订阅服务器上的更新。<br /><br /> **10** = DownloadUpdateFailed:在发布服务器上的更新无法应用于订阅服务器。|  
|**reason_code**|**Int**|与上下文相关的错误代码。|  
|**reason_text**|**varchar(720)**|与上下文相关的错误说明。|  
|**origin_datasource**|**varchar(255)**|冲突的起源。|  
|**pubid**|**uniqueidentifier**|发布标识符。|  
|**MSrepl_create_time**|**datetime**|添加冲突信息的时间。|  
  
## <a name="return-code-values"></a>返回代码值  
 **0** （成功） 或**1** （失败）  
  
## <a name="remarks"></a>备注  
 **sp_helpmergedeleteconflictrows**合并复制中使用。  
  
## <a name="permissions"></a>权限  
 只有的成员**sysadmin**固定的服务器角色和**db_owner**固定的数据库角色可以执行**sp_helpmergedeleteconflictrows**。  
  
## <a name="see-also"></a>请参阅  
 [系统存储过程 (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
