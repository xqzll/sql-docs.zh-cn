---
title: 创建 SQL Server 代理主作业 | Microsoft Docs
ms.custom: ''
ms.date: 04/26/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent], master jobs
- jobs [SQL Server Agent], creating
- master SQL Server Agent job [SQL Server]
ms.assetid: c12ab23f-d7ee-43a5-8cd2-0a9121292bcd
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: e80d5790f78c83a8a1ff3059e12e0946e206c060
ms.sourcegitcommit: ceb7e1b9e29e02bb0c6ca400a36e0fa9cf010fca
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/03/2018
ms.locfileid: "52795829"
---
# <a name="create-a-sql-server-agent-master-job"></a>创建 SQL Server 代理主作业
  本主题说明如何使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 或 [!INCLUDE[tsql](../../includes/tsql-md.md)] 在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中创建主 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理作业。  
  
 
##  <a name="BeforeYouBegin"></a> 开始之前  
  
###  <a name="Restrictions"></a> 限制和局限  
 对主 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理作业所做更改必须传播到所有涉及的目标服务器。 由于在指定那些目标后，目标服务器才开始下载作业，因此 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 建议在完成特定作业的所有作业步骤和作业计划后，再指定任何目标服务器。 否则，必须通过执行 **sp_post_msx_operation** 存储过程或使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]修改作业来手动请求目标服务器重新下载修改后的作业。 有关详细信息，请参阅[sp_post_msx_operation &#40;TRANSACT-SQL&#41; ](/sql/relational-databases/system-stored-procedures/sp-post-msx-operation-transact-sql)或[修改作业](modify-a-job.md)。  
  
###  <a name="Security"></a> 安全性  
  
####  <a name="Permissions"></a> Permissions  
 如果分布式作业的步骤与某个代理相关联，则该作业将在目标服务器上该代理帐户的上下文下运行。 请确保满足以下条件，否则与代理关联的作业步骤将不会从主服务器下载到目标服务器上：  
  
-   注册表子项**\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\\<*instance_name*> \SQL Server Agent\AllowDownloadedJobsToMatchProxyName**(REG_DWORD) 设置为 1 (true)。 默认情况下，此子项设置为 0 (False)。  
  
-   目标服务器上已存在与运行作业步骤的主服务器代理帐户同名的代理帐户。  
  
 从主服务器将使用代理帐户的作业步骤下载到目标服务器时，如果作业步骤失败，可以检查 **msdb** 数据库中 **sysdownloadlist** 表的 **error_message** 列是否存在以下错误消息：  
  
-   “该作业步骤需要代理帐户，但是目标服务器上禁用了代理匹配功能。” 若要解决此错误，请将 **AllowDownloadedJobsToMatchProxyName** 注册表子项设置为 1。  
  
-   “找不到代理。” 若要解决此错误，请确保目标服务器上已存在与运行作业步骤的主服务器代理帐户同名的代理帐户。  
  
##  <a name="SSMSProcedure"></a> 使用 SQL Server Management Studio  
  
#### <a name="to-create-a-master-sql-server-agent-job"></a>创建主 SQL Server 代理作业  
  
1.  在 **“对象资源管理器”** 中，单击加号以展开要创建 SQL Server 代理作业的服务器。  
  
2.  单击加号以展开 **“SQL Server 代理”**。  
  
3.  右键单击“作业”文件夹，然后选择“新建作业…”。  
  
4.  在 **“新建作业”** 对话框的 **“常规”** 页上，修改作业的常规属性。 有关此页上的可用选项的详细信息，请参阅[作业属性和新的作业&#40;常规页&#41;](../../integration-services/general-page-of-integration-services-designers-options.md)  
  
5.  在 **“步骤”** 页上，组织作业步骤。 有关此页上的可用选项的详细信息，请参阅[作业属性： 新建作业&#40;步骤页&#41;](job-properties-new-job-steps-page.md)  
  
6.  在 **“计划”** 页上，组织作业的计划。 有关此页上的可用选项的详细信息，请参阅[作业属性：新的作业&#40;计划页&#41;](job-properties-new-job-schedules-page.md)  
  
7.  在 **“警报”** 页上，组织作业的警报。 有关此页上的可用选项的详细信息，请参阅[作业属性：新的作业&#40;警报页&#41;](job-properties-new-job-alerts-page.md)  
  
8.  在 **“通知”** 页上，设置在作业完成时 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理要执行的操作。 有关此页上的可用选项的详细信息，请参阅[作业属性：新的作业&#40;通知页&#41;](job-properties-new-job-notifications-page.md)。  
  
9. 在 **“目标”** 页上，管理作业的目标服务器。 有关此页上的可用选项的详细信息，请参阅[作业属性：新的作业&#40;以页为目标&#41;](job-properties-new-job-targets-page.md)。  
  
10. 完成后，单击 **“确定”**。  
  

  
##  <a name="TsqlProcedure"></a> 使用 Transact-SQL  
  
#### <a name="to-create-a-master-sql-server-agent-job"></a>创建主 SQL Server 代理作业  
  
1.  在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]的实例。  
  
2.  在标准菜单栏上，单击 **“新建查询”**。  
  
3.  将以下示例复制并粘贴到查询窗口中，然后单击“执行” 。  
  
    ```  
    USE msdb ;  
    GO  
    -- Adds a new job executed by the SQLServerAgent service called 'Weekly Sales Data Backup'  
    EXEC dbo.sp_add_job  
        @job_name = N'Weekly Sales Data Backup' ;  
    GO  
    -- Adds a step (operation) to the 'Weekly Sales Data Backup' job.  
    EXEC sp_add_jobstep  
        @job_name = N'Weekly Sales Data Backup',  
        @step_name = N'Set database to read only',  
        @subsystem = N'TSQL',  
        @command = N'ALTER DATABASE SALES SET READ_ONLY',   
        @retry_attempts = 5,  
        @retry_interval = 5 ;  
    GO  
    -- Creates a schedule called RunOnce  
    EXEC dbo.sp_add_schedule  
        @schedule_name = N'RunOnce',  
        @freq_type = 1,  
        @active_start_time = 233000 ;  
    USE msdb ;  
    GO  
    -- Sets the 'RunOnce' schedule to the "Weekly Sales Data Backup' Job  
    EXEC sp_attach_schedule  
       @job_name = N'Weekly Sales Data Backup',  
       @schedule_name = N'RunOnce';  
    GO  
    -- assigns the multiserver job Weekly Sales Backups to the server SEATTLE2  
    -- assumes that SEATTLE2 is registered as a target server for the current instance.  
    EXEC dbo.sp_add_jobserver  
        @job_name = N'Weekly Sales Data Backups',  
        @server_name = N'SEATTLE2' ;  
    GO  
    ```  
  
 有关详细信息，请参阅：  
  
-   [sp_add_job (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-add-job-transact-sql)  
  
-   [sp_add_jobstep (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-add-jobstep-transact-sql)  
  
-   [sp_add_schedule (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-add-schedule-transact-sql)  
  
-   [sp_attach_schedule (Transact-SQL)](/sql/relational-databases/system-stored-procedures/sp-attach-schedule-transact-sql)  
  
-   [sp_add_jobserver &#40;TRANSACT-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-add-jobserver-transact-sql)  
  

  
  
