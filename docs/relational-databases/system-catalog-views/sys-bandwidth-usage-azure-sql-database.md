---
title: sys.bandwidth_usage （Azure SQL 数据库） |Microsoft Docs
ms.custom: ''
ms.date: 01/28/2019
ms.service: sql-database
ms.reviewer: ''
ms.topic: language-reference
f1_keywords:
- bandwidth_usage
- sys.bandwidth_usage
- bandwidth_usage_TSQL
- sys.bandwidth_usage_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.bandwidth_usage
- bandwidth_usage
ms.assetid: 43ed8435-f059-4907-b5c0-193a258b394a
author: julieMSFT
ms.author: jrasnick
manager: craigg
monikerRange: = azuresqldb-current || = sqlallproducts-allversions
ms.openlocfilehash: 4b7534a806a856dee922ead1055da6a7567a4d8c
ms.sourcegitcommit: aeb2273d779930e76b3e907ec03397eab0866494
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/10/2019
ms.locfileid: "67716603"
---
# <a name="sysbandwidthusage-azure-sql-database"></a>sys.bandwidth_usage (Azure SQL Database)

[!INCLUDE[tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-xxxxxx-asdb-xxxx-xxx-md.md)]

> [!NOTE]
> 这仅适用于[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]V11.* *  
  
 返回有关每个数据库中使用的网络带宽的信息 **[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] V11 数据库服务器**。 为给定数据库返回的每行总结在一小时内使用的单个方向和类别。  
  
 **已弃用此功能在[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]。**  
  
 **Sys.bandwidth_usage**视图包含以下各列。  
  
|Column Name|描述|  
|-----------------|-----------------|  
|**time**|占用带宽的时间（小时）。 此视图中的各行以小时为单位。 例如，2009-09-19 02:00:00.000 表示占用带宽的时间是 2009 年 9 月 19 日的凌晨 2:00 到凌晨 3:00。|  
|**database_name**|占用带宽的数据库的名称。|  
|**direction**|占用带宽的类型，为以下选项之一：<br /><br /> 入口：数据正移入[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]。<br /><br /> 出口：数据正移出[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]。|  
|class |占用带宽的类别，为以下选项之一：<br />内部：Azure 平台内移动的数据。<br />外部：移出 Azure 平台的数据。<br /><br /> 仅在数据库与区域处于连续复制关系 ([!INCLUDE[ssGeoDR](../../includes/ssgeodr-md.md)]) 时返回此类别。 如果给定的数据库不参与任何连续复制关系，则不会返回"Interlink"行。 有关详细信息，请参阅本主题后面的"备注"部分。|  
|**time_period**|峰值或非高峰期，使用情况发生的时间段。 The Peak time is based on the region in which the server was created. 例如，如果在“US_Northwest”地区创建了服务器，则高峰期时间定义为 PST 时间上午 10:00 点 到下午 6:00 太平洋标准时间。|  
|**quantity**|占用的带宽量 (KB)。|  
  
## <a name="permissions"></a>权限

 此视图选项仅适用于**主**与服务器级别主体登录名的数据库。  
  
## <a name="remarks"></a>备注  
  
### <a name="external-and-internal-classes"></a>External 和 Internal 类别

 在给定时间，使用每个数据库**sys.bandwidth_usage**视图返回显示的类和方向的带宽使用情况的行。 下例列举给定数据库可能公开的数据。 在此示例中，时间为 2012-04-21 17:00: 00，即发生在高峰时段。 数据库名称为 Db1。 在此示例中， **sys.bandwidth_usage**已返回一行，为 Ingress 和 Egress 方向以及 External 和 Internal 类别的所有四种组合，如下所示：  
  
|time|database_name|direction|class|time_period|quantity|  
|----------|--------------------|---------------|-----------|------------------|--------------|  
|2012-04-21 17:00:00|Db1|Ingress|External|Peak|66|  
|2012-04-21 17:00:00|Db1|流出量|External|Peak|741|  
|2012-04-21 17:00:00|Db1|流入量|Internal|Peak|1052|  
|2012-04-21 17:00:00|Db1|Egress|内部|Peak|3525|  
  
### <a name="interpreting-data-direction-for-includessgeodrincludesssgeodr-mdmd"></a>解释 [!INCLUDE[ssGeoDR](../../includes/ssgeodr-md.md)] 的数据方向

 对于 [!INCLUDE[ssGeoDR](../../includes/ssgeodr-md.md)]，带宽使用情况数据在连续复制关系两侧的逻辑主数据库中可见。 因此，您必须解释入口和出口方向指示器从所查询的数据库的角度来看。 例如，考虑将 1 MB 的数据从源服务器传输到目标服务器的复制流。 在这种情况下，源服务器上 1 MB 计入发送的总数据并在目标服务器上，1 MB 记录为收到的数据。  
  
> [!NOTE]  
> 这些数据按用户数据流的方向从源服务器传输到目标服务器。 但是，在另一方向也需要传输一些数据。  
