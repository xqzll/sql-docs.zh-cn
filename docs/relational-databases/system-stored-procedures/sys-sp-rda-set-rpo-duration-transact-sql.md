---
title: sys.sp_rda_set_rpo_duration (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: language-reference
f1_keywords:
- sys.sp_rda_set_rpo_duration
- sys.sp_rda_set_rpo_duration_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sp_rda_set_rpo_duration stored procedure
ms.assetid: 95c80c5b-9252-4612-9ea7-544c48834fd2
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: f46dd0bbedfebec5e21800b477a23d664446bf24
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "65982955"
---
# <a name="syssprdasetrpoduration-transact-sql"></a>sys.sp_rda_set_rpo_duration (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  在临时表以帮助确保完整还原的远程 Azure 数据库，如果时间还原点是必需的设置 SQL Server 保留的已迁移数据的小时的数。    
    
 有关详细信息，请参阅[Stretch Database 通过暂时保留已迁移的行来降低你的 Azure 数据的数据丢失的风险](../../sql-server/stretch-database/backup-stretch-enabled-databases-stretch-database.md#stretchRPO)。  
   
 ![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "主题链接图标") [TRANSACT-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)    
     
## <a name="syntax"></a>语法    
    
```    
    
sp_rda_set_rpo_duration [ @duration_hrs = ] duration_hrs    
    
```    
    
## <a name="arguments"></a>参数    
 [ @duration_hrs = ] *duration_hrs*    
 是的小时数 （非 null 的整数值） 的迁移的数据所需 SQL Server 以保留当前已启用延伸的数据库。 默认值和最小值为 8 小时。    
 
 > [!NOTE]
 > 较高的值需要 SQL Server 上的更多存储空间。
    
## <a name="permissions"></a>权限    
 需要 db_owner 权限。    
    
## <a name="remarks"></a>备注    
 通过运行获取的当前值[sys.sp_rda_get_rpo_duration &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-rda-get-rpo-duration-transact-sql.md)。    
    
## <a name="see-also"></a>请参阅    
 [sys.sp_rda_get_rpo_duration &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sys-sp-rda-get-rpo-duration-transact-sql.md)     
 [还原已启用延伸的数据库 (Stretch Database)](../../sql-server/stretch-database/restore-stretch-enabled-databases-stretch-database.md)     
 [Stretch 数据库](../../sql-server/stretch-database/stretch-database.md)    
    
  
