---
title: MSSQLSERVER_2577 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 2577 (Database Engine error)
ms.assetid: f53256a2-2fb0-47fd-9ed9-c45389104145
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 73dc506732b84f9fc6478d455f84393acdd99b15
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "63045869"
---
# <a name="mssqlserver2577"></a>MSSQLSERVER_2577
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
## <a name="details"></a>详细信息  
  
|||  
|-|-|  
|产品名称|SQL Server|  
|事件 ID|2577|  
|事件源|MSSQLSERVER|  
|组件|SQLEngine|  
|符号名称|DBCC_IAM_CHAIN_SEQUENCE_OUT_OF_ORDER|  
|消息正文|在对象 ID O_ID，索引 ID I_ID，分区 ID PN_ID，分配单元 ID A_ID（类型为 TYPE）的索引分配映射 (IAM) 链中，链序列号顺序不对。 序列号为 SEQUENCE1 的页 P_ID1 指向了序列号为 SEQUENCE2 的页 P_ID2。|  
  
## <a name="explanation"></a>解释  
每个索引分配映射 (IAM) 页都有一个序列号。 该序列号指示 IAM 页在 IAM 链内的位置。 规则是用该序列号加一来表示每个 IAM 页。 IAM 页 *P_ID2* 具有的序列号未遵循此规则。  
  
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
运行 REPAIR 将重新生成 IAM 链。 REPAIR 首先将现有的 IAM 链拆分为两半。 链的第一半将以 IAM 页 *P_ID1* 结束。 *P_ID1* 页的下一页指针将设置为 (0:0)。 链的第二半将从 IAM 页 *P_ID2* 开始。 *P_ID2* 页的上一页指针将设置为 (0:0)。  
  
然后，REPAIR 将链的两半连接在一起，并重新生成 IAM 链的序列号。 将释放无法修复的任何 IAM 页。  
  
> [!CAUTION]  
> 此修复可能会导致数据丢失。  
  
