---
title: '@@IO_BUSY (Transact-SQL) | Microsoft Docs'
ms.custom: ''
ms.date: 09/18/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- '@@IO_BUSY'
- '@@IO_BUSY_TSQL'
dev_langs:
- TSQL
helpviewer_keywords:
- ticks [SQL Server]
- I/O [SQL Server], time spent performing operations
- '@@IO_BUSY function'
- output operations [SQL Server]
- input operations [SQL Server]
- time [SQL Server], I/O operations
ms.assetid: 3c26770c-41ae-4e34-8c82-7bef920ffbca
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: b874feb143f72b6cc65a59b8f08eab889ad1927b
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "65944445"
---
# <a name="x40x40iobusy-transact-sql"></a>&#x40;&#x40;IO_BUSY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  返回自从 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 最近一次启动以来，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 已经用于执行输入和输出操作的时间。 其结果是 CPU 时间增量（时钟周期），并且是所有 CPU 的累积值，所以，它可能超过实际消逝的时间。 乘以 @@TIMETICKS 可转换为微秒。  
  
> [!NOTE]  
>  如果 @@CPU_BUSY 或 @@IO_BUSY 中返回的时间超过累积的 CPU 时间约 49 天，则会收到算术溢出警告。 在这种情况下，@@CPU_BUSY、@@IO_BUSY 和 @@IDLE 变量值并不精确。  
  
 ![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "主题链接图标") [TRANSACT-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>语法  
  
```  
@@IO_BUSY  
```  
  
## <a name="return-types"></a>返回类型  
 **integer**  
  
## <a name="remarks"></a>Remarks  
 若要显示包含几种 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 统计信息的报告，请运行 sp_monitor。  
  
## <a name="examples"></a>示例  
 下面的示例返回在开始时间和当前时间之间 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 已经用于执行输入/输出操作的毫秒数。 为了避免将值转换为微秒时出现算术溢出，此示例将其中一个值转换为 float 数据类型  。  
  
```  
SELECT @@IO_BUSY*@@TIMETICKS AS 'IO microseconds',   
   GETDATE() AS 'as of';  
```  
  
 下面是典型的结果集：  
  
```  
  
IO microseconds as of                   
--------------- ----------------------  
4552312500      12/5/2006 10:23:00 AM   
```  
  
## <a name="see-also"></a>另请参阅  
 [sys.dm_os_sys_info (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-os-sys-info-transact-sql.md)   
 [@@CPU_BUSY (Transact-SQL)](../../t-sql/functions/cpu-busy-transact-sql.md)   
 [sp_monitor (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-monitor-transact-sql.md)   
 [系统统计函数 (Transact-SQL)](../../t-sql/functions/system-statistical-functions-transact-sql.md)  
  
  
