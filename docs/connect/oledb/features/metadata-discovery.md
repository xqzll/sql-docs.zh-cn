---
title: 元数据发现 |Microsoft Docs
description: OLE DB 驱动程序适用于 SQL Server 中的元数据发现
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
ms.openlocfilehash: 3ed5020498dee14a34bd66076fc74a578bc09e69
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 06/07/2019
ms.locfileid: "66765967"
---
# <a name="metadata-discovery"></a>元数据发现
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] 中改进了元数据发现功能，从而使适用于 SQL Server 的 OLE DB 驱动程序应用程序能确保在执行查询后返回的列或参数元数据与执行该查询之前指定的元数据格式相同或兼容。 如果执行查询后返回的元数据与执行该查询之前指定的元数据格式不兼容，您将会收到错误。  
  
 在 bcp 以及 IBCPSession 和 IBCPSession2 接口中，现在可以指定延迟读取（延迟的元数据发现）以避免对查询输出操作执行元数据发现。 这样可以提高性能，并避免元数据发现失败。  
  
 如果开发使用适用于 SQL Server 的 OLE DB 驱动程序的应用程序，但所连接的服务器版本早于 [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)]，则元数据发现功能将对应于该服务器的版本。  
  
## <a name="remarks"></a>Remarks   
 [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] 中增强了以下 OLE DB 成员函数，以提供改进的元数据发现：  
  
-   IColumnsInfo::GetColumnInfo  
  
-   IColumnsRowset::GetColumnsRowset  
  
-   Icommandwithparameters:: Getparameterinfo (请参阅[ICommandWithParameters](../../oledb/ole-db-interfaces/icommandwithparameters.md)有关详细信息)  
  
 使用 IBCPSession::BCPSetBulkMode 指定元数据格式时，也会看到性能改进  
  
 OLE DB 驱动程序适用于 SQL Server 中的改进的元数据发现可能是因为存在两个存储过程中添加[!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)]:  
  
-   sp_describe_first_result_set  
  
-   sp_describe_undeclared_parameters  
  
## <a name="see-also"></a>另请参阅  
 [适用于 SQL Server 的 OLE DB 驱动程序功能](../../oledb/features/oledb-driver-for-sql-server-features.md)  
  
  
