---
title: 日期和时间改进 |Microsoft Docs
description: 日期和时间改进的 OLE DB 驱动程序适用于 SQL Server
ms.custom: ''
ms.date: 06/12/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
author: pmasl
ms.author: pelopes
manager: jroth
ms.openlocfilehash: 488713eb92d079afe58cfd508d5d6cdeeb5b99a9
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 06/07/2019
ms.locfileid: "66777838"
---
# <a name="date-and-time-improvements"></a>日期和时间改进
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  本主题介绍中新增的日期和时间数据类型的 SQL Server 支持 OLE DB 驱动程序[!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)]。  
  
 有关日期/时间改进的详细信息，请参阅[日期和时间改进&#40;OLE DB&#41;](../../oledb/ole-db-date-time/date-and-time-improvements-ole-db.md)。  
  
 有关演示此功能的示例应用程序的信息，请参阅 [SQL Server 数据编程示例](https://msftdpprodsamples.codeplex.com/)。  
  
## <a name="usage"></a>用法  
 以下各节介绍使用新的日期和时间类型的各种方法。  
  
### <a name="use-date-as-a-distinct-data-type"></a>将日期用作非重复数据类型  
 从[!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)]，增强了对日期/时间类型支持，可以更高效，以使用 DBTYPE_DBDATE OLE DB 类型。  
  
### <a name="use-time-as-a-distinct-data-type"></a>将时间用作非重复数据类型  
 OLE DB 已具有一种只包含时间的数据类型 DBTYPE_DBTIME，它的精度为 1 秒。
  
 新的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 时间数据类型具有秒的小数形式，其准确度可达 100 纳秒。 这需要 SQL Server 的 OLE DB 驱动程序中的新类型： DBTYPE_DBTIME2。 已编写的所用时间不带秒的小数部分的现有应用程序可以使用 time(0) 列。 现有的 OLE DB DBTYPE_TIME 类型及其对应的结构应正常工作，除非应用程序依赖于元数据中返回的类型。  
  
### <a name="use-time-as-a-distinct-data-type-with-extended-fractional-seconds-precision"></a>将具有扩展的秒的小数部分精度的时间用作非重复数据类型  
 某些应用程序（如过程控制和生产应用程序）要求能够处理精度高达 100 纳秒的时间数据。 为此 OLE DB 中的新类型为 DBTYPE_DBTIME2。  
  
### <a name="use-datetime-with-extended-fractional-seconds-precision"></a>使用具有扩展的秒的小数部分精度的日期时间  
 OLE DB 已定义了一个精度高达 1 纳秒的类型。 但是，此类型已由现有的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 应用程序使用，并且此类应用程序预计只需 1/300 秒精度。 新的 datetime2(3) 类型与现有的日期时间类型不直接兼容  。 如果这一点将影响应用程序行为而导致风险，则应用程序必须使用新的 DBCOLUMN 标志以确定实际的服务器类型。    
  
### <a name="use-datetime-with-extended-fractional-seconds-precision-and-timezone"></a>使用具有扩展的秒的小数部分精度和时区的日期时间  
 一些应用程序要求带有时区信息的日期时间值。 这被支持新的 DBTYPE_DBTIMESTAMPOFFSET 类型。
  
### <a name="use-datetimedatetimedatetimeoffset-data-with-client-side-conversions-consistent-with-existing-conversions"></a>将 Date/Time/Datetime/Datetimeoffset 数据用于与现有转换一致的客户端转换  
 转换将以一致的方式进行扩展，以包括在 [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] 中引入的所有日期和时间类型之间的转换。  
  
## <a name="see-also"></a>另请参阅  
 [适用于 SQL Server 的 OLE DB 驱动程序功能](../../oledb/features/oledb-driver-for-sql-server-features.md)  
  
  
