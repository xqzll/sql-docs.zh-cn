---
title: lightweight pooling 服务器配置选项 | Microsoft Docs
ms.custom: ''
ms.date: 03/02/2017
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- default lightweight pooling
- decreasing overhead
- lightweight pooling option
- system overhead [SQL Server]
- performance [SQL Server], lightweight pooling
- context switching [SQL Server], lightweight pooling option
- excessive context switching [SQL Server]
- reducing overhead
- overhead [SQL Server]
ms.assetid: 2dc11b61-d065-4126-8e00-acf40390f9fb
author: MikeRayMSFT
ms.author: mikeray
manager: jroth
ms.openlocfilehash: ea3ef8aa6e667935ea65c619221bfbbd10199e99
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "66785170"
---
# <a name="lightweight-pooling-server-configuration-option"></a>lightweight pooling 服务器配置选项
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  使用“轻型池”  选项可以减少有时在对称多处理 (SMP) 环境下遇到的、与过多的上下文切换有关的系统开销。 如果出现过多的上下文切换，轻型池可以通过上下文切换内联化，从而降低用户/内核环的转换频率，达到提高吞吐量的目的。  
  
 纤程模式专用于 UMS 工作线程的上下文切换是性能的关键瓶颈的某些情况。 因为这种情况很少出现，所以纤程模式很少增强典型系统上的性能或可扩展性。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)] 中改进的上下文切换也减少了对纤程模式的需求。 我们建议您不要使用纤程模式计划日常操作。 这是因为它会抑制上下文切换优点的正常发挥，并且使用线程本地存储区 (TLS) 或线程所有的对象（如互斥体，一种 Win32 内核对象）的某些 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 组件在纤程模式下无法正常工作。  
  
 将 **lightweight pooling** 设置为 1 将使 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 切换到纤程模式计划。 该选项的默认值为 0。  
  
 **lightweight pooling** 选项是一个高级选项。 如果使用 **sp_configure** 系统存储过程来更改该设置，则仅当“显示高级选项”  设置为 1 时才可以更改“轻型池”  。 该设置在服务器重新启动后生效。  
  
> [!NOTE]  
>  [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 2000 和 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows XP 不支持轻型池。 [!INCLUDE[winxpsvr](../../includes/winxpsvr-md.md)] 完全支持轻型池。  
  
> [!NOTE]  
>  轻型池不支持执行公共语言运行时 (CLR)。 禁用以下两个选项之一：“clr enabled”或“lightweight pooling”。 依赖于 CLR 并且在纤程模式下无法正常工作的功能包括：hierarchy 数据类型、复制和基于策略的管理。  
  
## <a name="see-also"></a>另请参阅  
 [clr enabled 服务器配置选项](../../database-engine/configure-windows/clr-enabled-server-configuration-option.md)   
 [服务器配置选项 (SQL Server)](../../database-engine/configure-windows/server-configuration-options-sql-server.md)   
 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)   
 [clr enabled 服务器配置选项](../../database-engine/configure-windows/clr-enabled-server-configuration-option.md)  
  
  
