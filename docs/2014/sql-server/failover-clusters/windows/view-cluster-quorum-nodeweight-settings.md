---
title: 查看群集仲裁 NodeWeight 设置 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], WSFC clusters
- quorum [SQL Server], AlwaysOn and WSFC quorum
ms.assetid: b845e73a-bb01-4de2-aac2-8ac12abebc95
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: bab64e8a33baae2c87e8068a1e4d23799742b55c
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "63049374"
---
# <a name="view-cluster-quorum-nodeweight-settings"></a>查看群集仲裁 NodeWeight 设置
  本主题说明如何查看 Windows Server 故障转移群集 (WSFC) 群集中每个成员节点的 NodeWeight 设置。 在仲裁投票期间，使用 NodeWeight 设置来支持 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 和 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 故障转移群集实例的灾难恢复和多子网方案。  
  
-   **开始之前：** [先决条件](#Prerequisites)、[安全性](#Security)  
  
-   **若要查看仲裁 NodeWeight 设置，请使用：** [使用 Transact-SQL](#TsqlProcedure)、[使用 Powershell](#PowerShellProcedure)、[使用 Cluster.exe](#CommandPromptProcedure)  
  
##  <a name="BeforeYouBegin"></a> 开始之前  
  
###  <a name="Prerequisites"></a> 先决条件  
 仅在 [!INCLUDE[firstref_longhorn](../../../includes/firstref-longhorn-md.md)] 或更高版本中支持此功能。  
  
> [!IMPORTANT]  
>  为了使用 NodeWeight 设置，必须将以下修补程序应用到 WSFC 群集中的所有服务器：  
>   
>  [KB2494036](https://support.microsoft.com/kb/2494036)：修补程序可让你配置中不具有仲裁投票的群集节点[!INCLUDE[firstref_longhorn](../../../includes/firstref-longhorn-md.md)]并在 [!INCLUDE[winserver2008r2](../../../includes/winserver2008r2-md.md)]  
  
> [!TIP]  
>  如果未安装此修补程序，本主题中的示例将为 NodeWeight 返回空或 NULL 值。  
  
###  <a name="Security"></a> 安全性  
 用户必须是一个域帐户，该帐户是每个 WSFC 群集节点上本地 Administrators 组的成员。  
  
##  <a name="TsqlProcedure"></a> 使用 Transact-SQL  
  
##### <a name="to-view-nodeweight-settings"></a>查看 NodeWeight 设置  
  
1.  连接到群集中的任意 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 实例。  
  
2.  查询 [sys].[dm_hadr_cluster_members] 视图。  
  
### <a name="example-transact-sql"></a>示例 (Transact-SQL)  
 以下示例查询一个系统视图以返回该实例的群集中所有节点的值。  
  
```sql  
SELECT  member_name, member_state_desc, number_of_quorum_votes  
 FROM   sys.dm_hadr_cluster_members;  
```  
  
##  <a name="PowerShellProcedure"></a> 使用 PowerShell  
  
##### <a name="to-view-nodeweight-settings"></a>查看 NodeWeight 设置  
  
1.  通过 **“以管理员身份运行”** 启动提升的 Windows PowerShell。  
  
2.  导入 `FailoverClusters` 模块以启用群集 commandlet。  
  
3.  使用 `Get-ClusterNode` 对象以返回群集节点对象的集合。  
  
4.  以可读格式输出群集节点属性。  
  
### <a name="example-powershell"></a>示例 (PowerShell)  
 以下示例为名为“Cluster001”的群集输出一些节点属性。  
  
```powershell  
Import-Module FailoverClusters  
  
$cluster = "Cluster001"  
$nodes = Get-ClusterNode -Cluster $cluster  
  
$nodes | Format-Table -property NodeName, State, NodeWeight  
```  
  
##  <a name="CommandPromptProcedure"></a> 使用 cluster.exe  
  
> [!NOTE]  
>  在 [!INCLUDE[winserver2008r2](../../../includes/winserver2008r2-md.md)] 版本中不推荐使用 cluster.exe 实用工具。  在将来的开发工作中，请将 PowerShell 与故障转移群集结合使用。  在 Windows Server 的下一版本中，将删除 cluster.exe 实用工具。 有关详细信息，请参阅 [Mapping Cluster.exe Commands to Windows PowerShell Cmdlets for Failover Clusters](https://technet.microsoft.com/library/ee619744\(WS.10\).aspx)（为故障转移群集将 cluster.exe 命令映射到 Windows PowerShell Cmdlet）。  
  
##### <a name="to-view-nodeweight-settings"></a>查看 NodeWeight 设置  
  
1.  通过 **“以管理员身份运行”** 启动提升的命令提示符。  
  
2.  使用 **cluster.exe** 以返回节点状态和 NodeWeight 值  
  
### <a name="example-clusterexe"></a>示例 (Cluster.exe)  
 以下示例为名为“Cluster001”的群集输出一些节点属性。  
  
```ms-dos  
cluster.exe Cluster001 node /status /properties  
```  
  
## <a name="see-also"></a>请参阅  
 [WSFC 仲裁模式和投票配置 (SQL Server)](wsfc-quorum-modes-and-voting-configuration-sql-server.md)   
 [配置群集仲裁 NodeWeight 设置](configure-cluster-quorum-nodeweight-settings.md)   
 [sys.dm_hadr_cluster_members (Transact-SQL)](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-cluster-members-transact-sql)   
 [Windows PowerShell 中按任务焦点列出的故障转移群集 Cmdlet](https://technet.microsoft.com/library/ee619761\(WS.10\).aspx)  
  
  
