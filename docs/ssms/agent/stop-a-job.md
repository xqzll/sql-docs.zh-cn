---
title: 停止作业 | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- jobs [SQL Server Agent], stopping
- SQL Server Agent jobs, stopping
- stopping jobs
ms.assetid: 4249328a-24d8-4284-9d1d-7d04ed90e3d7
author: markingmyname
ms.author: maghan
manager: craigg
monikerRange: = azuresqldb-mi-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: daedb5dbd9bb08c0ee68e149ee70deab24426782
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "65089454"
---
# <a name="stop-a-job"></a>Stop a Job
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

> [!IMPORTANT]  
> [Azure SQL 数据库托管实例](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance)目前支持大多数但并非所有 SQL Server 代理功能。 有关详细信息，请参阅 [Azure SQL 数据库托管实例与 SQL Server 之间的 T-SQL 差异](https://docs.microsoft.com/azure/sql-database/sql-database-managed-instance-transact-sql-information#sql-server-agent)。

本主题说明如何停止 [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理作业。 作业是 SQL Server 代理执行的一系列指定操作。  
  
-   **开始之前：**  ，  
  
    [限制和局限](#Restrictions)  
  
    [安全性](#Security)  
  
-   **若要停止作业，请使用：**  
  
    [SQL Server Management Studio](#SSMS)  
  
    [Transact-SQL](#TSQL)  
  
    [SQL Server 管理对象](#SMO)  
  
## <a name="BeforeYouBegin"></a>开始之前  
  
### <a name="Restrictions"></a>限制和局限  
  
-   如果作业当前正在执行 **CmdExec** 或 **PowerShell**类型的步骤，则强制提前结束正在运行的进程（例如 MyProgram.exe）。 这可能会导致不可预知的行为，如进程正在使用的文件保持为打开状态。  
  
-   对于多服务器作业，针对该作业的 STOP 指令将发布到该作业的所有目标服务器中。  
  
### <a name="Security"></a>安全性  
有关详细信息，请参阅[实现 SQL Server 代理安全性](../../ssms/agent/implement-sql-server-agent-security.md)。  
  
## <a name="SSMS"></a>使用 SQL Server Management Studio  
  
#### <a name="to-stop-a-job"></a>停止作业  
  
1.  在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion_md.md)]的实例，然后展开该实例。  
  
2.  展开 **“SQL Server 代理”** ，再展开 **“作业”** ，右键单击要停止的作业，再单击 **“停止作业”** 。  
  
3.  若要停止多个作业，请右键单击 **“作业活动监视器”** ，然后单击 **“查看作业活动”** 。 在作业活动监视器中，选择要停止的作业，右键单击所选内容，然后单击 **“停止作业”** 。  
  
## <a name="TSQL"></a>使用 Transact-SQL  
  
#### <a name="to-stop-a-job"></a>停止作业  
  
1.  在 **“对象资源管理器”** 中，连接到 [!INCLUDE[ssDE](../../includes/ssde_md.md)]的实例。  
  
2.  在标准菜单栏上，单击 **“新建查询”** 。  
  
3.  将以下示例复制并粘贴到查询窗口中，然后单击“执行”  。  
  
    ```  
    -- stops a job named Weekly Sales Data Backup  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_stop_job  
        N'Weekly Sales Data Backup' ;  
    GO  
    ```  
  
有关详细信息，请参阅 [sp_stop_job (Transact-SQL)](https://msdn.microsoft.com/64b4cc75-99a0-421e-b418-94e37595bbb0)。  
  
## <a name="SMO"></a>使用 SQL Server 管理对象  
**停止作业**  
  
通过使用所选编程语言（如 Visual Basic、Visual C# 或 PowerShell）来调用 **Job** 类的 **Stop** 方法。 有关详细信息，请参阅 [SQL Server 管理对象 (SMO)](https://msdn.microsoft.com/library/ms162169.aspx)。  
  
