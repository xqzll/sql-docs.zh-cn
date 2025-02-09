---
title: 为可用性组手动准备辅助数据库 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.availabilitygroup.configsecondarydbs.f1
- sql12.swb.availabilitygroup.preparedbs.f1
helpviewer_keywords:
- secondary databases [SQL Server], in availability group
- secondary databases [SQL Server]
- Availability Groups [SQL Server], configuring
- Availability Groups [SQL Server], databases
ms.assetid: 9f2feb3c-ea9b-4992-8202-2aeed4f9a6dd
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: f2fd8058518d59e5eb3fcf8a8514425c69339dfb
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "62792077"
---
# <a name="manually-prepare-a-secondary-database-for-an-availability-group-sql-server"></a>为可用性组手动准备辅助数据库 (SQL Server)
  本主题介绍如何通过使用 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 、 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]或 PowerShell 在 [!INCLUDE[tsql](../../../includes/tsql-md.md)]中为 AlwaysOn 可用性组准备辅助数据库。 准备辅助数据库需要两个步骤：（1） 还原主数据库的最近数据库备份和后续日志备份应用到每个承载辅助副本的服务器实例、 使用 RESTORE WITH NORECOVERY，和 （2） 将还原的数据库联接到可用性组。  
  
> [!TIP]  
>  如果您具有现有的日志传送配置，则可能能够将日志传送主数据库与其一个或多个辅助数据库一起转换为 AlwaysOn 主数据库和一个或多个 AlwaysOn 辅助数据库。 有关详细信息，请参阅[到 AlwaysOn 可用性组从日志传送先决条件迁移&#40;SQL Server&#41;](prereqs-migrating-log-shipping-to-always-on-availability-groups.md)。  
  
-   **开始之前：**  
  
     [先决条件和限制](#Prerequisites)  
  
     [建议](#Recommendations)  
  
     [安全性](#Security)  
  
-   **若要准备辅助数据库，请使用：**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [PowerShell](#PowerShellProcedure)  
  
-   [相关备份和还原任务](#RelatedTasks)  
  
-   **跟进：**[准备辅助数据库之后](#FollowUp)  
  
##  <a name="BeforeYouBegin"></a> 开始之前  
  
###  <a name="Prerequisites"></a> 先决条件和限制  
  
-   确保计划放置数据库的系统的磁盘驱动器空间足以存储辅助数据库。  
  
-   辅助数据库的名称必须与主数据库的名称相同。  
  
-   使用 RESTORE WITH NORECOVERY 执行每个还原操作。  
  
-   如果辅助数据库需要位于与主数据库不同的文件路径中（包括驱动器号），还原命令还必须对每个数据库文件使用 WITH MOVE 选项，将这些文件指定到辅助数据库的路径。  
  
-   如果要逐个文件组地还原数据库，则要确保还原整个数据库。  
  
-   还原数据库后，必须还原 (WITH NORECOVERY) 自上次还原的数据备份之后创建的各个日志备份。  
  
###  <a name="Recommendations"></a> 建议  
  
-   在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]独立实例上，我们建议，如有可能，给定辅助数据库的文件路径（包括驱动器号）应该与相应的主数据库的路径相同。 这是因为，如果在创建辅助数据库时移动了数据库文件，则随后在辅助数据库上执行的添加文件操作可能会失败，并导致该辅助数据库挂起。  
  
-   准备辅助数据库之前，我们强烈建议您挂起针对可用性组中数据库的计划日志备份，直到完成辅助副本的初始化。  
  
###  <a name="Security"></a> 安全性  
 备份数据库时， [TRUSTWORTHY 数据库属性](../../../relational-databases/security/trustworthy-database-property.md) 设置为 OFF。 因此，在新还原的数据库中，TRUSTWORTHY 始终为 OFF。  
  
####  <a name="Permissions"></a> Permissions  
 默认情况下，为 **sysadmin** 固定服务器角色以及 **db_owner** 和 **db_backupoperator** 固定数据库角色的成员授予 BACKUP DATABASE 和 BACKUP LOG 权限。 有关详细信息，请参阅 [BACKUP (Transact-SQL)](/sql/t-sql/statements/backup-transact-sql)。  
  
 如果服务器实例上不存在要还原的数据库，则 RESTORE 语句要求 CREATE DATABASE 权限。 有关详细信息，请参阅 [RESTORE (Transact-SQL)](/sql/t-sql/statements/restore-statements-transact-sql)。  
  
##  <a name="SSMSProcedure"></a> 使用 SQL Server Management Studio  
  
> [!NOTE]  
>  如果备份和还原文件路径在承载主要副本的服务器实例和承载次要副本的每个实例之间完全相同，则应该能够通过使用 [新建可用性组向导](use-the-availability-group-wizard-sql-server-management-studio.md)、 [将副本添加到可用性组向导](use-the-add-replica-to-availability-group-wizard-sql-server-management-studio.md)或 [将数据库添加到可用性组向导](availability-group-add-database-to-group-wizard.md)创建辅助数据库。  
  
 **准备辅助数据库**  
  
1.  除非您已经有了主数据库的最近数据库备份，否则需要创建新的完全或差异数据库备份。 最好将此备份和任何后续的日志备份放到推荐的网络共享上。  
  
2.  至少为主数据库创建一个新日志备份。  
  
3.  在承载辅助副本的服务器实例上，依次还原主数据库的完整数据库备份（还可以选择还原差异备份）以及所有后续的日志备份。  
  
     在“RESTORE DATABASEOptions”页上，选择 **“不对数据库执行任何操作，不回退未提交的事务”。可以还原其他事务日志。(RESTORE WITH NORECOVERY)**。  
  
     如果主数据库与辅助数据库的文件路径不同，例如，如果主数据库位于驱动器“F:”，但承载辅助副本的服务器实例缺少 F: 驱动器，请在 WITH 语句中包括 MOVE 选项。  
  
4.  若要完成辅助数据库的配置，您需要将辅助数据库联接到可用性组。 有关详细信息，请参阅[将辅助数据库联接到可用性组 (SQL Server)](join-a-secondary-database-to-an-availability-group-sql-server.md)。  
  
> [!NOTE]  
>  有关如何执行这些备份和还原操作的信息，请参阅本节后面的 [相关备份和还原任务](#RelatedTasks)。  
  
###  <a name="RelatedTasks"></a> 相关备份和还原任务  
 **创建数据库备份**  
  
-   [创建完整数据库备份 (SQL Server)](../../../relational-databases/backup-restore/create-a-full-database-backup-sql-server.md)  
  
-   [创建差异数据库备份 (SQL Server)](../../../relational-databases/backup-restore/create-a-differential-database-backup-sql-server.md)  
  
 **创建日志备份**  
  
-   [备份事务日志 (SQL Server)](../../../relational-databases/backup-restore/back-up-a-transaction-log-sql-server.md)  
  
 **还原备份**  
  
-   [还原数据库备份&#40;SQL Server Management Studio&#41;](../../../relational-databases/backup-restore/restore-a-database-backup-using-ssms.md)  
  
-   [还原差异数据库备份 (SQL Server)](../../../relational-databases/backup-restore/restore-a-differential-database-backup-sql-server.md)  
  
-   [还原事务日志备份 (SQL Server)](../../../relational-databases/backup-restore/restore-a-transaction-log-backup-sql-server.md)  
  
-   [将数据库还原到新位置 (SQL Server)](../../../relational-databases/backup-restore/restore-a-database-to-a-new-location-sql-server.md)  
  
##  <a name="TsqlProcedure"></a> 使用 Transact-SQL  
 **准备辅助数据库**  
  
> [!NOTE]  
>  有关此过程的示例，请参阅本主题前面的 [示例 (Transact-SQL)](#ExampleTsql)。  
  
1.  除非您已经有了主数据库的最近完整备份，否则请连接到承载主副本的服务器实例并创建完整数据库备份。 最好将此备份和任何后续的日志备份放到推荐的网络共享上。  
  
2.  在承载辅助副本的服务器实例上，依次还原主数据库的完整数据库备份（还可以选择还原差异备份）以及所有后续的日志备份。 使用 WITH NORECOVERY 执行每个还原操作。  
  
     如果主数据库与辅助数据库的文件路径不同，例如，如果主数据库位于驱动器“F:”，但承载辅助副本的服务器实例缺少 F: 驱动器，请在 WITH 语句中包括 MOVE 选项。  
  
3.  在执行完必要的日志备份之后，如果对主数据库进行了任何日志备份，还必须将这些备份复制到承载辅助副本的服务器实例上并将每个日志备份都应用到辅助数据库，以最早的备份开始进行，并始终使用 RESTORE WITH NORECOVERY。  
  
    > [!NOTE]  
    >  如果主数据库刚刚创建，则不会存在日志备份；或者如果恢复模式刚刚从“简单”更改为“完整”，则尚未进行任何日志备份。  
  
4.  若要完成辅助数据库的配置，您需要将辅助数据库联接到可用性组。 有关详细信息，请参阅[将辅助数据库联接到可用性组 (SQL Server)](join-a-secondary-database-to-an-availability-group-sql-server.md)。  
  
> [!NOTE]  
>  有关如何执行这些备份和还原操作的信息，请参阅本主题后面的 [相关备份和还原任务](#RelatedTasks)。  
  
###  <a name="ExampleTsql"></a> Transact-SQL 示例  
 下面的示例准备一个辅助数据库。 此示例使用了 [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] 示例数据库，默认情况下，该数据库使用简单恢复模式。  
  
1.  若要使用 [!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)] 数据库，请改用完整恢复模式：  
  
    ```  
    USE master;  
    GO  
    ALTER DATABASE MyDB1   
    SET RECOVERY FULL;  
    GO  
    ```  
  
2.  将数据库的恢复模式从 SIMPLE 更改为 FULL 之后，创建一个完整备份，以用于创建辅助数据库。 由于恢复模式已更改，因此指定了 WITH FORMAT 选项来创建新的介质集。 这对区分完整恢复模式下的备份与以前在简单恢复模式下创建的备份非常有用。 为了实现此示例的目的，在数据库所在的驱动器上创建备份文件 (C:\\[!INCLUDE[ssSampleDBobject](../../../includes/sssampledbobject-md.md)].bak)。  
  
    > [!NOTE]  
    >  对于生产数据库，应始终备份到单独的设备。  
  
     在承载主副本的服务器实例 (`INSTANCE01`) 上，按如下方式创建主数据库的完整备份：  
  
    ```  
    BACKUP DATABASE MyDB1   
        TO DISK = 'C:\MyDB1.bak'   
        WITH FORMAT  
    GO  
    ```  
  
3.  将完整备份复制到承载辅助副本的服务器实例上。  
  
4.  使用 RESTORE WITH NORECOVERY 在承载辅助副本的服务器实例上还原完整备份。 还原命令取决于主数据库与辅助数据库的路径是否相同。  
  
    -   **如果路径相同：**  
  
         在承载辅助副本的计算机上，按如下方式还原完整备份：  
  
        ```  
        RESTORE DATABASE MyDB1   
            FROM DISK = 'C:\MyDB1.bak'   
            WITH NORECOVERY  
        GO  
        ```  
  
    -   **如果路径不同：**  
  
         如果辅助数据库的路径与主数据库的路径不同（例如，它们所在的驱动器号不同），则创建辅助数据库要求还原操作包含 MOVE 子句。  
  
        > [!IMPORTANT]  
        >  如果主数据库与辅助数据库的路径名称不同，则无法添加文件。 原因是在接收添加文件操作所需的日志时，承载辅助副本的服务器实例会尝试将新文件放在主数据库所用的路径中。  
  
         例如，下面的命令可还原主数据库的备份，主数据库位于 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]默认实例的数据目录 C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\DATA 中。 还原数据库操作必须将数据库移动到的远程实例的数据目录[!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]名为 (*AlwaysOn1*)，另一个群集节点上的辅助副本。 该处，数据和日志文件还原到*C:\Program Files\Microsoft SQL Server\MSSQL12。ALWAYSON1\MSSQL\DATA*目录。 该还原操作使用 WITH NORECOVERY 令辅助数据库保持还原状态。  
  
        ```  
        RESTORE DATABASE MyDB1  
          FROM DISK='C:\MyDB1.bak'  
         WITH NORECOVERY,   
            MOVE 'MyDB1_Data' TO   
             'C:\Program Files\Microsoft SQL Server\MSSQL12.ALWAYSON1\MSSQL\DATA\MyDB1_Data.mdf',   
            MOVE 'MyDB1_Log' TO  
             'C:\Program Files\Microsoft SQL Server\MSSQL12.ALWAYSON1\MSSQL\DATA\MyDB1_Data.ldf';  
        GO  
        ```  
  
5.  还原完整备份之后，必须在主数据库中创建日志备份。 例如，以下 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 语句将日志备份到名为 *E:\MyDB1_log.bak*的备份文件：  
  
    ```  
    BACKUP LOG MyDB1   
      TO DISK = 'E:\MyDB1_log.bak'   
    GO  
    ```  
  
6.  在将数据库联接到辅助副本之前，必须应用必要的日志备份（以及所有后续日志备份）。  
  
     例如，以下 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 语句还原 *C:\MyDB1.bak*中的第一个日志：  
  
    ```  
    RESTORE LOG MyDB1   
      FROM DISK = 'E:\MyDB1_log.bak'   
        WITH FILE=1, NORECOVERY  
    GO  
    ```  
  
7.  如果在数据库联接到辅助副本之前进行了任何其他日志备份，则还必须使用 RESTORE WITH NORECOVERY 按顺序将所有这些日志备份还原到承载辅助副本的服务器实例上。  
  
     例如，以下 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 语句还原 *E:\MyDB1_log.bak*中的其他两个日志：  
  
    ```  
    RESTORE LOG MyDB1   
      FROM DISK = 'E:\MyDB1_log.bak'   
        WITH FILE=2, NORECOVERY  
    GO  
    RESTORE LOG MyDB1   
      FROM DISK = 'E:\MyDB1_log.bak'   
        WITH FILE=3, NORECOVERY  
    GO  
    ```  
  
##  <a name="PowerShellProcedure"></a> 使用 PowerShell  
 **准备辅助数据库**  
  
1.  如果您需要创建主数据库的最近备份，请将目录 (`cd`) 改为承载主副本的服务器实例。  
  
2.  使用 `Backup-SqlDatabase` cmdlet 创建每个备份。  
  
3.  切换目录 (`cd`) 到承载辅助副本的服务器实例。  
  
4.  若要还原数据库以及每个主数据库的日志备份，请使用 `restore-SqlDatabase` cmdlet 并指定 `NoRecovery` 还原参数。 如果文件路径在承载主副本和目标辅助副本的计算机之间存在差异，还要使用 `RelocateFile` 还原参数。  
  
    > [!NOTE]  
    >  若要查看 cmdlet 的语法，请在 `Get-Help` PowerShell 环境中使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] cmdlet。 有关详细信息，请参阅 [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md)。  
  
5.  若要完成辅助数据库的配置，您需要将其联接到可用性组。 有关详细信息，请参阅[将辅助数据库联接到可用性组 (SQL Server)](join-a-secondary-database-to-an-availability-group-sql-server.md)。  
  
 **设置和使用 SQL Server PowerShell 提供程序**  
  
-   [SQL Server PowerShell 提供程序](../../../powershell/sql-server-powershell-provider.md)  
  
###  <a name="ExamplePSscript"></a> 备份和还原脚本和命令的示例  
 下面的 PowerShell 命令将完整的数据库备份和事务日志备份到网络共享，并自该共享位置还原这些备份。 此示例假定数据库还原到的文件路径与数据库备份到的文件路径相同。  
  
```  
# Create database backup  
Backup-SqlDatabase -Database "MyDB1" -BackupFile "\\share\backups\MyDB1.bak" -ServerInstance "SourceMachine\Instance"  
# Create log backup  
Backup-SqlDatabase -Database "MyDB1" -BackupAction "Log" -BackupFile "\\share\backups\MyDB1.trn" -ServerInstance "SourceMachine\Instance"  
# Restore database backup   
Restore-SqlDatabase -Database "MyDB1" -BackupFile "\\share\backups\MyDB1.bak" -NoRecovery -ServerInstance "DestinationMachine\Instance"  
# Restore log backup   
Restore-SqlDatabase -Database "MyDB1" -BackupFile "\\share\backups\MyDB1.trn" -RestoreAction "Log" -NoRecovery -ServerInstance "DestinationMachine\Instance"  
  
```  
  
##  <a name="FollowUp"></a> 跟进：准备辅助数据库之后  
 若要完成辅助数据库的配置，您需要将新还原的数据库联接到可用性组。 有关详细信息，请参阅 [将辅助数据库联接到可用性组 (SQL Server)](join-a-secondary-database-to-an-availability-group-sql-server.md)。  
  
## <a name="see-also"></a>请参阅  
 [AlwaysOn 可用性组概述&#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [BACKUP (Transact-SQL)](/sql/t-sql/statements/backup-transact-sql)   
 [RESTORE 参数 (Transact-SQL)](/sql/t-sql/statements/restore-statements-arguments-transact-sql)   
 [RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql)   
 [解决失败的添加文件操作问题&#40;AlwaysOn 可用性组&#41;](troubleshoot-a-failed-add-file-operation-always-on-availability-groups.md)  
  
  
