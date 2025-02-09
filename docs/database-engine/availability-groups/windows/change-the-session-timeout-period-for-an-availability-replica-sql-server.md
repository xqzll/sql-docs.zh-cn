---
title: 更改可用性组中副本的会话超时期限
description: 介绍如何配置 AlwaysOn 可用性组中的副本的会话超时期限。
ms.custom: seodec18
ms.date: 05/17/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], configuring
- Availability Groups [SQL Server], session timeout
- session timeout [SQL Server]
ms.assetid: e23c6e06-1cd1-4d4a-9bc2-e3e06ab2933d
author: MashaMSFT
ms.author: mathoma
manager: jroth
ms.openlocfilehash: d1cb8408c01dd02528f80cf44b0516e0d12000b2
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "66796610"
---
# <a name="change-the-session-timeout-period-for-a-replica-within-an-always-on-availability-group"></a>更改 AlwaysOn 可用性组中副本的会话超时期限
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  本主题介绍如何通过在 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]中使用 [!INCLUDE[tsql](../../../includes/tsql-md.md)]、 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]或 PowerShell 来配置 AlwaysOn 可用性副本的会话超时期限。 会话超时期限是一个副本属性，用来控制可用性副本等待已连接副本的 ping 响应的时间（秒数），超过该期限则认为连接已失败。 默认情况下，副本等待 ping 响应的时长为 10 秒钟。 此副本属性仅适用于可用性组的给定辅助副本与主副本之间的连接。 有关会话超时期限的详细信息，请参阅 [AlwaysOn 可用性组概述 (SQL Server)](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)。  
   
##  <a name="Prerequisites"></a> 先决条件  
  
-   您必须连接到承载主副本的服务器实例。  
  
##  <a name="Recommendations"></a> 建议  
 我们建议您将超时期限保持为 10 秒或更长。 如果将值设置为低于 10 秒，则可能使高负荷系统丢失 PING 并声明错误故障。  
  
  
## <a name="Permissions"></a> 权限  
 对可用性组要求 ALTER AVAILABILITY GROUP 权限、CONTROL AVAILABILITY GROUP 权限、ALTER ANY AVAILABILITY GROUP 权限或 CONTROL SERVER 权限。  
  
##  <a name="SSMSProcedure"></a> 使用 SQL Server Management Studio  
 **更改可用性副本的会话超时期限**  
  
1.  在对象资源管理器中，连接到承载主副本的服务器实例，然后展开服务器树。  
  
2.  依次展开“Always On 高可用性”  节点和“可用性组”  节点。  
  
3.  单击要配置其可用性副本的可用性组。  
  
4.  右键单击要配置的副本，然后单击 **“属性”** 。  
  
5.  在 **“可用性副本属性”** 对话框中，使用 **“会话超时（秒）”** 字段更改此副本的会话超时期限的秒数。  
  
##  <a name="TsqlProcedure"></a> 使用 Transact-SQL  
 **更改可用性副本的会话超时期限**  
  
1.  连接到承载主副本的服务器实例。  
  
2.  按如下所示使用 [ALTER AVAILABILITY GROUP](../../../t-sql/statements/alter-availability-group-transact-sql.md) 语句：  
  
     ALTER AVAILABILITY GROUP *group_name*  
  
     MODIFY REPLICA ON '*instance_name*' WITH ( SESSION_TIMEOUT =*seconds* )  
  
     其中， *group_name* 是可用性组的名称， *instance_name* 是承载要修改的可用性副本的服务器实例的名称， *seconds* 指定该副本在充当次要副本时将日志应用到数据库之前必须等待的最少秒数。 默认值为 0 秒，指示无应用延迟。  
  
     在 `AccountsAG` 可用性组的主副本上输入的以下示例，将 `15` 服务器实例上的副本的会话超时值更改为 `INSTANCE09` 秒。  
  
    ```  
    ALTER AVAILABILITY GROUP AccountsAG   
       MODIFY REPLICA ON 'INSTANCE09' WITH (SESSION_TIMEOUT = 15);  
    ```  
  
##  <a name="PowerShellProcedure"></a> 使用 PowerShell  
 **更改可用性副本的会话超时期限**  
  
1.  将目录 (**cd**) 更改为托管主副本的服务器实例。  
  
2.  结合使用 **Set-SqlAvailabilityReplica** cmdlet 和 **SessionTimeout** 参数，以更改指定的可用性副本上的会话超时期限的秒数。  
  
     例如，以下命令将会话超时期限设置为 15 秒。  
  
    ```  
    Set-SqlAvailabilityReplica -SessionTimeout 15 `   
    -Path SQLSERVER:\Sql\PrimaryServer\InstanceName\AvailabilityGroups\MyAg\AvailabilityReplicas\MyReplica  
    ```  
  
    > [!NOTE]  
    >  若要查看 cmdlet 的语法，请在 **PowerShell 环境中使用** Get-Help [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] cmdlet。 有关详细信息，请参阅 [Get Help SQL Server PowerShell](../../../relational-databases/scripting/get-help-sql-server-powershell.md)。  
  
 **设置和使用 SQL Server PowerShell 提供程序**  
  
-   [SQL Server PowerShell 提供程序](../../../relational-databases/scripting/sql-server-powershell-provider.md)  
  
## <a name="see-also"></a>另请参阅  
 [AlwaysOn 可用性组概述 (SQL Server)](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)  
  
  
