---
title: SQL Server - Backup Device 对象 | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- SQLServer:Backup Device
- Backup Device object
ms.assetid: 52e7febf-d5e0-4674-945b-aacc40a9ad6e
author: julieMSFT
ms.author: jrasnick
manager: craigg
ms.openlocfilehash: 1cd5ee037eb7a513e54239ec825af7cced6c4a8f
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "62939031"
---
# <a name="sql-server-backup-device-object"></a>SQL Server Backup Device 对象
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  **Backup Device** 对象提供的计数器可监视用于备份和还原操作的 Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 备份设备。 在希望基于每个设备确定吞吐量或备份和还原操作的进度及性能时，可以监视备份设备。 若要监视整个数据库备份或还原操作的吞吐量，请使用  Databases [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Databases** object. 有关详细信息，请参阅 [SQL Server, Databases Object](../../relational-databases/performance-monitor/sql-server-databases-object.md)。  
  
 此表介绍了 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **Backup Device** 计数器。  
  
|SQL Server Backup Device 计数器|描述|  
|---------------------------------------|-----------------|  
|**Device Throughput Bytes/sec**|一个备份设备在备份或还原数据库时所用的读写操作的吞吐量（以每秒字节数表示）。 这一计数器只有在备份或还原操作执行时才存在。|  
  
## <a name="see-also"></a>另请参阅  
 [备份设备 (SQL Server)](../../relational-databases/backup-restore/backup-devices-sql-server.md)   
 [监视资源使用情况（系统监视器）](../../relational-databases/performance-monitor/monitor-resource-usage-system-monitor.md)  
  
  
