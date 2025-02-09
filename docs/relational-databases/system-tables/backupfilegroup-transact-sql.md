---
title: backupfilegroup (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- backupfilegroup_TSQL
- backupfilegroup
dev_langs:
- TSQL
helpviewer_keywords:
- filegroups [SQL Server], backupfilegroup system table
- backupfilegroup system table
ms.assetid: d26e8fbe-f5c5-4e10-b2bd-0d8e16ea21f9
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: b1d7cc485899a7f8173552788471ef6ec45ce49c
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "62645187"
---
# <a name="backupfilegroup-transact-sql"></a>backupfilegroup (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  备份时数据库中的每个文件组在表中占一行。 **backupfilegroup**存储在**msdb**数据库。  
  
> [!NOTE]  
>  **Backupfilegroup**表显示了文件组配置的数据库，而不是备份集。 若要确定是否将文件包括在备份集中，使用**is_present**的列[backupfile](../../relational-databases/system-tables/backupfile-transact-sql.md)表。  
  
|列名|数据类型|Description|  
|-----------------|---------------|-----------------|  
|**backup_set_id**|**int**|包含该文件组的备份集。|  
|**名称**|**sysname**|文件组的名称。|  
|**filegroup_id**|**int**|文件组的 ID；在数据库中唯一。 对应于**data_space_id**中**sys.filegroups**。|  
|**filegroup_guid**|**uniqueidentifier**|文件组的全局唯一标识符。 可以为 NULL。|  
|**type**|**char(2)**|内容类型，可为下列类型之一：<br /><br /> FG =“行”文件组<br /><br /> SL = [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 日志文件组|  
|**type_desc**|**nvarchar(60)**|函数类型的说明，可为下列值之一：<br /><br /> ROWS_FILEGROUP<br /><br /> SQL_LOG_FILEGROUP|  
|**is_default**|**bit**|默认文件组，在 CREATE TABLE 或 CREATE INDEX 中未指定文件组时使用。|  
|**is_readonly**|**bit**|1 = 文件组为只读文件组。|  
|**log_filegroup_guid**|**uniqueidentifier**|可以为 NULL。|  
  
## <a name="remarks"></a>备注  
  
> [!IMPORTANT]  
>  相同的文件组名称可以出现在不同数据库中；但是，每个文件组都有自己的 GUID。 因此， **(backup_set_id，filegroup_guid)** 是一个用于标识的文件组中的唯一键**backupfilegroup**。  
  
 RESTORE VERIFYONLY FROM*备份设备*WITH LOADHISTORY 使用的列来填充**backupmediaset**介质集标头中的相应值的表。  
  
 若要减少此表中和其他备份和历史记录表中的行数，请执行[sp_delete_backuphistory](../../relational-databases/system-stored-procedures/sp-delete-backuphistory-transact-sql.md)存储过程。  
  
## <a name="see-also"></a>请参阅  
 [备份和还原表&#40;Transact SQL&#41;](../../relational-databases/system-tables/backup-and-restore-tables-transact-sql.md)   
 [backupfile (Transact-SQL)](../../relational-databases/system-tables/backupfile-transact-sql.md)   
 [backupmediafamily (Transact-SQL)](../../relational-databases/system-tables/backupmediafamily-transact-sql.md)   
 [backupmediaset (Transact-SQL)](../../relational-databases/system-tables/backupmediaset-transact-sql.md)   
 [backupset (Transact-SQL)](../../relational-databases/system-tables/backupset-transact-sql.md)   
 [系统表 (Transact-SQL)](../../relational-databases/system-tables/system-tables-transact-sql.md)  
  
  
