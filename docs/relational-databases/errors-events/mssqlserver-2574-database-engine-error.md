---
title: MSSQLSERVER_2574 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 2574 (Database Engine error)
ms.assetid: efba507a-b5ad-4f1d-b0c8-f73b663a0562
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 453c1a2aad80b9aa607a9d948660a78b5195c314
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "63045202"
---
# <a name="mssqlserver2574"></a>MSSQLSERVER_2574
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>详细信息  
  
|||  
|-|-|  
|产品名称|SQL Server|  
|事件 ID|2574|  
|事件源|MSSQLSERVER|  
|组件|SQLEngine|  
|符号名称|DBCC_EMPTY_INDEX_TREE_LEVEL_PAGE|  
|消息正文|表错误：对象 ID O_ID，索引 ID I_ID，分区 ID PN_ID，分配单元 ID A_ID（类型为 TYPE）中的页 P_ID 为空。 在 B 树的 LEVEL 级上，这是不允许的。|  
  
## <a name="explanation"></a>解释  
指定索引叶级上方的 B 树页为空，即它不包含行。 对于 [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)] 中的叶级页，此行为是可能的，但是在树级中决不可能。  
  
## <a name="user-action"></a>用户操作  
  
### <a name="look-for-hardware-failure"></a>查找硬件故障  
运行硬件诊断并更正任何问题。 也可以通过检查 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 系统和应用程序日志以及 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 错误日志来查看是否存在由硬件故障导致的错误。 修复日志中包含的所有与硬件相关的问题。  
  
如果持续遇到数据损坏问题，请尝试分别换下不同的硬件组件以确定问题所在。 进行检查以确保系统未启用磁盘控制器上的写缓存。 如果怀疑写入缓存是问题起因，请与硬件供应商联系。  
  
最后，您可能会发现，切换到全新的硬件系统是解决问题的极佳途径。 此切换操作可能包括重新格式化磁盘驱动器和重新安装操作系统。  
  
### <a name="restore-from-backup"></a>从备份还原  
如果出现的问题与硬件无关，并且您确信有可用的干净备份，请从备份中还原数据库。  
  
### <a name="run-dbcc-checkdb"></a>运行 DBCC CHECKDB  
如果不存在干净的可用备份，请运行不带 REPAIR 子句的 DBCC CHECKDB 以确定损坏程度。 建议使用 DBCC CHECKDB 的 REPAIR 子句。 接下来，请运行带适当 REPAIR 子句的 DBCC CHECKDB 修复损坏的数据。  
  
> [!CAUTION]  
> 如果您不确定运行带有 REPAIR 子句的 DBCC CHECKDB 会对数据造成何种影响，请在运行该语句前与您的主要支持提供商联系。  
  
如果运行具有 REPAIR 子句的 DBCC CHECKDB 无法解决存在的问题，请与主要支持提供商联系。  
  
### <a name="results-of-running-repair-options"></a>运行 REPAIR 选项的结果  
DBCC 将重新生成索引。  
  
