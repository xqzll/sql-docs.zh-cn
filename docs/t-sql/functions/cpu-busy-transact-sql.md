---
title: '@@CPU_BUSY (Transact-SQL) | Microsoft Docs'
ms.custom: ''
ms.date: 09/18/2017
ms.prod: sql
ms.prod_service: sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- '@@CPU_BUSY_TSQL'
- '@@CPU_BUSY'
dev_langs:
- TSQL
helpviewer_keywords:
- CPU [SQL Server]
- status information [SQL Server], CPU
- ticks [SQL Server]
- time [SQL Server], CPU activity
- '@@CPU_BUSY function'
- statistical information [SQL Server], CPU
- CPU [SQL Server], activity
ms.assetid: 81ae0e64-79fa-4a74-9aa5-37045c4cd211
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 4c80b0d801f290407115f297978c34bdcf19ee38
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "65944586"
---
# <a name="x40x40cpubusy-transact-sql"></a>&#x40;&#x40;CPU_BUSY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

此函数返回自最近一次开始以来，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 在活动操作中所花的时间。 `@@CPU_BUSY` 返回一个以 CPU 时间增量或“滴答数”计算的结果。 此值为所有 CPU 时间的累积，因此，可能会超出实际占用的时间。 若要转换为微秒，请乘以 [@@TIMETICKS](./timeticks-transact-sql.md)。
  
> [!NOTE]  
>  如果 @@CPU_BUSY 或 @@IO_BUSY 中返回的时间超过 49 天（大约）的累积 CPU 时间，则会收到算术溢出警告。 在这种情况下，`@@CPU_BUSY``@@IO_BUSY` 和 `@@IDLE` 变量值并不精确。  
  
![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "主题链接图标") [TRANSACT-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>语法  
  
```
@@CPU_BUSY  
```  
  
## <a name="return-types"></a>返回类型
**integer**
  
## <a name="remarks"></a>Remarks  
若要查看包含若干个 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 统计信息（包括 CPU 活动）的报表，请运行 [sp_monitor](../../relational-databases/system-stored-procedures/sp-monitor-transact-sql.md)。
  
## <a name="examples"></a>示例  
此示例显示了返回当前日期和时间之前的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] CPU 活动。 此示例将其中一个值转换为 `float` 数据类型。 这样就避免了计算以微秒为单位的值时的算术溢出问题。
  
```sql
SELECT @@CPU_BUSY * CAST(@@TIMETICKS AS float) AS 'CPU microseconds',   
   GETDATE() AS 'As of' ;  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```
CPU microseconds As of
---------------- -----------------------
18406250         2006-12-05 17:00:50.600
```
  
## <a name="see-also"></a>另请参阅
[sys.dm_os_sys_info (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-os-sys-info-transact-sql.md)  
[@@IDLE (Transact-SQL)](../../t-sql/functions/idle-transact-sql.md)  
[@@IO_BUSY (Transact-SQL)](../../t-sql/functions/io-busy-transact-sql.md)  
[sp_monitor (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-monitor-transact-sql.md)  
[系统统计函数 (Transact-SQL)](../../t-sql/functions/system-statistical-functions-transact-sql.md)
  
  
