---
title: MSSQLSERVER_2527 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 2527 (Database Engine error)
ms.assetid: 1cef90ef-9c39-44e6-bc7f-316c8f53c10c
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 26dfce968215f01ea1e3451bf879f41ecc1b9962
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "63045356"
---
# <a name="mssqlserver2527"></a>MSSQLSERVER_2527
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>详细信息  
  
|||  
|-|-|  
|产品名称|SQL Server|  
|事件 ID|2527|  
|事件源|MSSQLSERVER|  
|组件|SQLEngine|  
|符号名称|DBCC_INDEX_FILEGROUP_IS_OFFLINE|  
|消息正文|无法处理表 O_NAME 的索引 I_NAME，因为文件组 F_NAME 离线。|  
  
## <a name="explanation"></a>解释  
此信息性消息指示由于用来存储索引数据的某个文件组处于脱机状态而无法检查索引。 文件组中文件的状态决定整个文件组的可用性。 文件组中的所有文件都必须联机，文件组才可用。 如果没有其他问题，将检查同一对象的所有其他索引。  
  
## <a name="user-action"></a>用户操作  
若要查看指定文件组中文件的状态，请查询 **sys.database_files** 或 **sys.master_files** 目录视图。  
  
从备份还原离线文件。  
  
## <a name="see-also"></a>另请参阅  
[sys.database_files (Transact-SQL)](~/relational-databases/system-catalog-views/sys-database-files-transact-sql.md)  
[sys.master_files (Transact-SQL)](~/relational-databases/system-catalog-views/sys-master-files-transact-sql.md)  
[RESTORE &#40;Transact-SQL&#41;](~/t-sql/statements/restore-statements-transact-sql.md)  
  
