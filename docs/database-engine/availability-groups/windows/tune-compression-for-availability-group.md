---
title: 调整可用性组的压缩 | Microsoft Docs
ms.custom: ''
ms.date: 06/22/2016
ms.prod: sql
ms.technology: high-availability
ms.topic: conceptual
ms.assetid: 7632769c-b246-4766-886f-7c60ec540be8
author: MashaMSFT
ms.author: mathoma
manager: jroth
ms.openlocfilehash: f0676a65fbc30d58e81b4e7a56d6a78756b72040
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "66781027"
---
# <a name="tune-compression-for-availability-group"></a>调整可用性组的压缩
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
默认情况下，SQL Server 将在适用时压缩可用性组的数据流。 压缩会减少网络流量，增加 CPU 负载，还可能导致延迟。 必须是 sysadmin 固定服务器角色的成员才能启用压缩。 下表显示 SQL Server 何时对可用性组日志流使用压缩：

| 应用场景 | 压缩设置
| ---- | ----
| 同步提交副本 | 未压缩
| 异步提交副本 | Compressed
| 自动种子设定过程中 | 未压缩

## <a name="trace-flags-for-availability-group-compression"></a>可用性组压缩的跟踪标志 

在大多数情况下，Microsoft 不建议更改这些设置。 可使用全局跟踪标志来测试更改这些设置。 SQL Server 将全局跟踪标志应用到整个实例。 实例中的所有可用性组都将受这些设置的影响。  

下表显示将更改 SQL Server 的默认压缩行为的跟踪标志。 

跟踪标志 | 描述
------------- | -------------
1462          | 对包含异步副本的可用性组禁用日志流压缩。 默认情况下，对异步副本启用此功能，以优化网络带宽。
9567          | 对自动种子设定过程中的可用性组启用数据流压缩。 自动种子设定过程中，压缩可大幅缩短传输时间，并且将增加处理器上的负载。
9592          | 对包含同步副本的可用性组启用日志流压缩。 默认情况下，对同步副本禁用此功能，因为压缩为增加延迟。 默认情况下，对异步副本启用日志流压缩。


## <a name="resources"></a>Resources


[数据库引擎启动选项](../../../database-engine/configure-windows/database-engine-service-startup-options.md)

[自动种子设定](https://msdn.microsoft.com/library/mt735149(SQL.130).aspx)

[AlwaysOn 先决条件](prereqs-restrictions-recommendations-always-on-availability.md) 
