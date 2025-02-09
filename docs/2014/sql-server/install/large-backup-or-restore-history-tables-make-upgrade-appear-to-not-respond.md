---
title: 很大的备份或还原历史记录表会使升级显得不响应 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- backup history tables
- history tables
ms.assetid: f88d86ec-324b-4518-b6d7-1af7e7265812
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: fd0e8ad6c4230e01b689e5863b770cdd78ddfccc
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "66094129"
---
# <a name="large-backup-or-restore-history-tables-make-upgrade-appear-to-not-respond"></a>很大的备份或还原历史记录表会使升级显得不响应
  在 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 中，一些备份和还原历史记录表中添加了若干新列。 若要升级这些表，则需要对它们进行更改以便添加新列。 如果一个或多个这样的表包含很多行，则执行向表添加列的 ALTER TABLE 语句时，升级过程将停顿很长时间。  
  
## <a name="component"></a>组件  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>Description  
 如果以下备份或还原历史记录表中的任何表包含大量的行，则升级过程便可能出现挂起现象：  
  
-   **backupfile**  
  
-   **backupmediafamily**  
  
-   **backupmediaset**  
  
-   **backupset**  
  
-   **restorefile**  
  
-   **restorefilegroup**  
  
-   **restorehistory**  
  
 如果任何这样的表包含 10,000 行或更多的行，则升级顾问将报告不符合条件故障。 但是不会报告哪个表超过了允许的行数。 第一个超过 10,000 行的表是导致该故障的原因。  
  
## <a name="corrective-action"></a>纠正措施  
 升级数据库之前，如果任何这样的表超过了 10,000 行，我们建议将行数减少至 10,000 行以下。 若要减少所有这些表中的行，可以运行**sp_delete_backuphistory**存储过程。 此过程会删除所有备份和还原历史记录表中早于指定日期的备份集的条目。 有关详细信息，请参阅 [sp_delete_backuphistory (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-delete-backuphistory-transact-sql)。  
  
> [!NOTE]  
>  可以升级其备份和还原历史记录表大于 10,000 行的数据库。 但在更改很大的表时，升级可能会出现停顿。 表越大，完成安装程序所需的时间就越长。  
  
## <a name="see-also"></a>请参阅  
 [数据库引擎升级问题](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [SQL Server 2014 升级顾问&#91;新&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
