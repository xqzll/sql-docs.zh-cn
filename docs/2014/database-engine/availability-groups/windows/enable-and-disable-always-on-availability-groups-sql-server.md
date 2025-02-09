---
title: 启用和禁用 AlwaysOn 可用性组 (SQL Server) |Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], server instance
- Availability Groups [SQL Server], deploying
- Availability Groups [SQL Server], disabling
- Availability Groups [SQL Server], enabling
ms.assetid: 7c326958-5ae9-4761-9c57-905972276a8f
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 9fc5fc211d0f0c843ad16fb377fad2082bcf02c1
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "62791933"
---
# <a name="enable-and-disable-alwayson-availability-groups-sql-server"></a>启用和禁用 AlwaysOn 可用性组 (SQL Server)
  启用 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 是服务器实例使用可用性组的先决条件。 在创建和配置任何可用性组之前，必须在将承载一个或多个可用性组的可用性副本的每个 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 实例上启用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 功能。  
  
> [!IMPORTANT]  
>  如果您删除后重新创建了 WSFC 群集，则必须在其原始 WSFC 群集上承载可用性副本的每个 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 实例上都禁用然后重新启用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 功能。  
  
-   **开始之前：**  
  
     [先决条件](#Prerequisites)  
  
     [安全性](#Security)  
  
-   **如何：**  
  
    -   [确定是否 AlwaysOn 可用性组已启用](#IsEnabled)  
  
    -   [启用 AlwaysOn 可用性组](#EnableAOAG)  
  
    -   [禁用 AlwaysOn 可用性组](#DisableAOAG)  
  
##  <a name="BeforeYouBegin"></a> 开始之前  
  
###  <a name="Prerequisites"></a> 启用 AlwaysOn 可用性组的先决条件  
  
-   该服务器实例必须驻留在 Windows Server 故障转移群集 (WSFC) 节点上。  
  
-   该服务器实例必须正在运行支持 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]的 SQL Server 版本。 有关详细信息，请参阅 [Features Supported by the Editions of SQL Server 2014](../../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)。  
  
-   一次仅为一个服务器实例启用 AlwaysOn 可用性组。 在启用 AlwaysOn 可用性组之后，一直等待直到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 服务已重新启动，然后才继续在另一个服务器实例上操作。  
  
 有关创建和配置可用性组的其他先决条件的信息，请参阅[的先决条件、 限制和建议为 AlwaysOn 可用性组&#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md)。  
  
###  <a name="Security"></a> 安全性  
 在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]实例上启用 AlwaysOn 可用性组时，服务器实例具有对 WSFC 群集的完全控制权限。  
  
####  <a name="Permissions"></a> Permissions  
 要求本地计算机上 **Administrator** 组中的成员身份以及对 WSFC 群集的完全控制。 使用 PowerShell 启用 AlwaysOn 时，使用 **“以管理员身份运行”** 选项打开命令提示符窗口。  
  
 要求 Active Directory 创建对象和管理对象权限。  
  
##  <a name="IsEnabled"></a> 确定是否 AlwaysOn 可用性组已启用  
  
-   [SQL Server Management Studio](#SSMS1Procedure)  
  
-   [Transact-SQL](#Tsql1Procedure)  
  
-   [PowerShell](#PowerShell1Procedure)  
  
###  <a name="SSMS1Procedure"></a> 使用 SQL Server Management Studio  
 **若要确定是否已启用 AlwaysOn 可用性组**  
  
1.  在“对象资源管理器”中，右键单击服务器实例，再单击“属性”  。  
  
2.  在 **“服务器属性”** 对话框中，单击 **“常规”** 页。 **“启用 HADR”** 属性显示以下值之一：  
  
    -   **True**（如果启用 AlwaysOn 可用性组）  
  
    -   **False**（如果禁用 AlwaysOn 可用性组）。  
  
###  <a name="Tsql1Procedure"></a> 使用 Transact-SQL  
 **若要确定是否已启用 AlwaysOn 可用性组**  
  
1.  使用以下 [SERVERPROPERTY](/sql/t-sql/functions/serverproperty-transact-sql) 语句：  
  
    ```  
    SELECT SERVERPROPERTY ('IsHadrEnabled');  
    ```  
  
     `IsHadrEnabled` 服务器属性的设置指示是否为 AlwaysOn 可用性组启用了 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 实例，如下所示：  
  
    -   如果 `IsHadrEnabled` = 1，则启用 AlwaysOn 可用性组。  
  
    -   如果 `IsHadrEnabled` = 0，则禁用 AlwaysOn 可用性组。  
  
    > [!NOTE]  
    >  有关详细信息`IsHadrEnabled`服务器属性，请参阅[SERVERPROPERTY &#40;TRANSACT-SQL&#41;](/sql/t-sql/functions/serverproperty-transact-sql)。  
  
###  <a name="PowerShell1Procedure"></a> 使用 PowerShell  
 **若要确定是否已启用 AlwaysOn 可用性组**  
  
1.  将默认值设置 (`cd`) 为要确定是否启用 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 的服务器实例。  
  
2.  输入以下 PowerShell `Get-Item` 命令：  
  
    ```  
    PS SQLSERVER:\SQL\NODE1\DEFAULT> get-item . | select IsHadrEnabled  
    ```  
  
    > [!NOTE]  
    >  若要查看 cmdlet 的语法，请在 `Get-Help` PowerShell 环境中使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] cmdlet。 有关详细信息，请参阅 [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md)。  
  
 **设置和使用 SQL Server PowerShell 提供程序**  
  
-   [SQL Server PowerShell 提供程序](../../../powershell/sql-server-powershell-provider.md)  
  
##  <a name="EnableAOAG"></a> 启用 AlwaysOn 可用性组  
 **若要启用 AlwaysOn，使用：**  
  
-   [SQL Server 配置管理器](#SQLCM2Procedure)  
  
-   [PowerShell](#PScmd2Procedure)  
  
###  <a name="SQLCM2Procedure"></a> 使用 SQL Server 配置管理器  
 **若要启用 AlwaysOn 可用性组**  
  
1.  连接到承载要启用 AlwaysOn 可用性组的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 实例的 Windows Server 故障转移群集 (WSFC) 节点。  
  
2.  在“开始”  菜单上，依次指向“所有程序”  、 [!INCLUDE[ssCurrentUI](../../../includes/sscurrentui-md.md)]、“配置工具”  ，然后单击“SQL Server 配置管理器”  。  
  
3.  在中**SQL Server 配置管理器**，单击**SQL Server Services**，右键单击 SQL Server ( **< *`instance name`* >)** ，其中 **< *`instance name`* >** 是你想要启用 AlwaysOn 可用性组的本地服务器实例的名称和单击**属性。**  
  
4.  选择 **“AlwaysOn 高可用性”** 选项卡。  
  
5.  验证 **Windows 故障转移群集名称**字段包含本地故障转移群集的名称。 如果此字段为空，则此服务器实例当前不支持 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]。 原因包括本地计算机不是群集节点、WSFC 群集已关闭或此版本的 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 不支持 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]。  
  
6.  选中 **“启用 AlwaysOn 可用性组”** 复选框，然后单击 **“确定”** 。  
  
     [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 配置管理器保存您的更改。 然后，必须手动重新启动 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 服务。 这使您可以选择最适合您的业务要求的重新启动时间。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 服务重新启动时，将启用 AlwaysOn 且 `IsHadrEnabled` 服务器属性将设置为 1。  
  
###  <a name="PScmd2Procedure"></a> 使用 SQL Server PowerShell  
 **若要启用 AlwaysOn**  
  
1.  将目录切换 (`cd`) 到您要启用 AlwaysOn 可用性组的服务器实例。  
  
2.  使用 `Enable-SqlAlwaysOn` cmdlet 启用 AlwaysOn 可用性组。  
  
     若要查看 cmdlet 的语法，请在 `Get-Help` PowerShell 环境中使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] cmdlet。 有关详细信息，请参阅 [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md)。  
  
    > [!NOTE]  
    >  有关如何控制信息是否`Enable-SqlAlwaysOn`cmdlet 可重新启动[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]服务，请参阅[何时 Cmdlet 重新启动 SQL Server 服务？](#WhenCmdletRestartsSQL)，本主题中更高版本。  
  
 **设置和使用 SQL Server PowerShell 提供程序**  
  
-   [SQL Server PowerShell 提供程序](../../../powershell/sql-server-powershell-provider.md)  
  
####  <a name="ExmplEnable-SqlHadrServic"></a>示例：Enable-SqlAlwaysOn  
 以下 PowerShell 命令在 SQL Server 实例上启用 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] （*计算机*\\*实例*）。  
  
```  
Enable-SqlAlwaysOn -Path SQLSERVER:\SQL\Computer\Instance  
```  
  
##  <a name="DisableAOAG"></a> 禁用 AlwaysOn 可用性组  
  
-   **禁用 AlwaysOn 之前：**  
  
     [建议](#Recommendations)  
  
-   **若要禁用 AlwaysOn，使用：**  
  
    -   [SQL Server 配置管理器](#SQLCM3Procedure)  
  
    -   [PowerShell](#PScmd3Procedure)  
  
-   **跟进：** [在禁用 AlwaysOn 之后](#FollowUp)  
  
> [!IMPORTANT]  
>  一次只能在一个服务器实例上禁用 AlwaysOn。 在禁用 AlwaysOn 可用性组之后，一直等待直到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 服务已重新启动，然后才继续在另一个服务器实例上操作。  
  
###  <a name="Recommendations"></a> 建议  
 在服务器实例上禁用 AlwaysOn 之前，我们建议您执行以下操作：  
  
1.  如果该服务器实例当前正在承载您要保留的可用性组的主副本，我们建议您尽可能手动将该可用性组故障转移到一个同步的辅助副本。 有关详细信息，请参阅[执行可用性组的计划手动故障转移 (SQL Server)](perform-a-planned-manual-failover-of-an-availability-group-sql-server.md)。  
  
2.  删除所有本地辅助副本。 有关详细信息，请参阅[从可用性组中删除次要副本 (SQL Server)](remove-a-secondary-replica-from-an-availability-group-sql-server.md)。  
  
###  <a name="SQLCM3Procedure"></a> 使用 SQL Server 配置管理器  
 **若要禁用 AlwaysOn**  
  
1.  连接到承载要禁用 AlwaysOn 可用性组的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 实例的 Windows Server 故障转移群集 (WSFC) 节点。  
  
2.  在 **“开始”** 菜单中，依次指向 **“所有程序”** 、 [!INCLUDE[ssCurrentUI](../../../includes/sscurrentui-md.md)]、 **“配置工具”** ，然后单击 **“SQL Server 配置管理器”** 。  
  
3.  在中**SQL Server 配置管理器**，单击**SQL Server Services**，右键单击 SQL Server ( **< *`instance name`* >)** ，其中 **< *`instance name`* >** 是你想要禁用 AlwaysOn 可用性组的本地服务器实例的名称和单击**属性**。  
  
4.  在“AlwaysOn 高可用性”  选项卡上，取消选中“启用 AlwaysOn 可用性组”  复选框，然后单击“确定”  。  
  
     [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 配置管理器保存您的更改并重新启动 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 服务。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 服务重新启动时，将禁用 AlwaysOn 且 `IsHadrEnabled` 服务器属性将设置为 0 以指示禁用 AlwaysOn 可用性组。  
  
5.  建议阅读本主题后面的[跟进：在禁用 AlwaysOn 之后](#FollowUp)，本主题中更高版本。  
  
###  <a name="PScmd3Procedure"></a> 使用 SQL Server PowerShell  
 **若要禁用 AlwaysOn**  
  
1.  将目录更改 (`cd`) 到你想要禁用 AlwaysOn 可用性组的当前已启用的服务器实例。  
  
2.  使用 `Disable-SqlAlwaysOn` cmdlet 启用 AlwaysOn 可用性组。  
  
     例如，以下命令禁用 SQL Server 实例上的 AlwaysOn 可用性组 (*计算机*\\*实例*)。  此命令需要重新启动实例，并将提示您确认此重新启动。  
  
    ```  
    Disable-SqlAlwaysOn -Path SQLSERVER:\SQL\Computer\Instance  
    ```  
  
    > [!IMPORTANT]  
    >  有关如何控制信息是否`Disable-SqlAlwaysOn`cmdlet 可重新启动[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]服务，请参阅[何时 Cmdlet 重新启动 SQL Server 服务？](#WhenCmdletRestartsSQL)，本主题中更高版本。  
  
     若要查看 cmdlet 的语法，请在 `Get-Help` PowerShell 环境中使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] cmdlet。 有关详细信息，请参阅 [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md)。  
  
 **设置和使用 SQL Server PowerShell 提供程序**  
  
-   [SQL Server PowerShell 提供程序](../../../powershell/sql-server-powershell-provider.md)  
  
###  <a name="FollowUp"></a> 跟进：在禁用 AlwaysOn 之后  
 禁用 AlwaysOn 可用性组后，必须重新启动 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 实例。 SQL 配置管理器将自动重新启动该服务器实例。 但是，如果您使用了 `Disable-SqlAlwaysOn`cmdlet，将需要手动重新启动该服务器实例。 有关详细信息，请参阅 [sqlservr Application](../../../tools/sqlservr-application.md)。  
  
 在重新启动的服务器实例上：  
  
-   可用性数据库在 SQL Server 启动时不启动，因此无法访问它们。  
  
-   唯一支持的 AlwaysOn [!INCLUDE[tsql](../../../includes/tsql-md.md)] 语句是 [DROP AVAILABILITY GROUP](/sql/t-sql/statements/drop-availability-group-transact-sql)。 不支持 CREATE AVAILABILITY GROUP、ALTER AVAILABILITY GROUP 和 ALTER DATABASE 的 SET HADR 选项。  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 元数据和 WSFC 中的 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 配置数据不受禁用 AlwaysOn 可用性组的影响。  
  
 如果您在为承载一个或多个可用性组的辅助副本的每个服务器实例上都永久禁用了 AlwaysOn 可用性组，则我们建议您完成以下步骤：  
  
1.  如果您在禁用 AlwaysOn 前未删除本地可用性组副本，则删除服务器实例正为其承载可用性组副本的每个可用性组。 有关删除可用性组的信息，请参阅[删除可用性组 (SQL Server)](remove-an-availability-group-sql-server.md)。  
  
2.  若要删除留在原地的元数据，请删除服务器实例上作为原始 WSFC 群集一部分的受影响的可用性组。  
  
3.  所有连接仍可以访问任何主数据库，但是主数据库和辅助数据库之间的数据同步将停止。  
  
4.  辅助数据库将进入 RESTORING 状态。 您可以删除这些数据库，或者可通过使用 RESTORE WITH RECOVERY 还原它们。 但是，还原的数据库不再参与可用性组数据同步。  
  
##  <a name="WhenCmdletRestartsSQL"></a> Cmdlet 何时重新启动 SQL Server 服务？  
 在当前正在运行的服务器实例上，使用 `Enable-SqlAlwaysOn` 或 `Disable-SqlAlwaysOn` 更改当前 AlwaysOn 设置可能导致 SQL Server 服务重新启动。 重新启动行为取决于以下条件：  
  
|指定了 -NoServiceRestart 参数|指定了 -Force 参数|重新启动 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 服务？|  
|--------------------------------------------|---------------------------------|---------------------------------------------------------|  
|否|否|默认情况。 但是 cmdlet 提示您以下信息：<br /><br /> **若要完成此操作，必须重新启动服务器实例“<instance_name>”的 SQL Server 服务。是否继续？**<br /><br /> **[Y] 是 [N] 否 [S] 挂起 [?] 帮助（默认值为“Y”）：**<br /><br /> 如果指定 **N** 或 **S**，则不重新启动该服务。|  
|否|是|重新启动服务。|  
|是|否|不重新启动服务。|  
|是|是|不重新启动服务。|  
  
## <a name="see-also"></a>请参阅  
 [AlwaysOn 可用性组概述&#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)   
 [SERVERPROPERTY (Transact-SQL)](/sql/t-sql/functions/serverproperty-transact-sql)  
  
  
