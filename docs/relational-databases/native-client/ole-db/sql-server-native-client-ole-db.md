---
title: SQL Server Native Client (OLE DB) |Microsoft Docs
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client OLE DB provider, about SQL Server Native Client OLE DB provider
- OLE DB, SQL Server Native Client OLE DB provider
- data access [SQL Server Native Client], OLE DB
- SQLNCLI, OLE DB
- OLE DB
- SQL Server Native Client OLE DB provider
- SQL Server Native Client, OLE DB
ms.assetid: da846da4-ec19-4a4f-81fb-7d5a2b2bf80a
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 71ae84e82fff80097ab1a8e26b00c89dfec6ba56
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "65097471"
---
# <a name="sql-server-native-client-ole-db"></a>SQL Server Native Client (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB 访问接口 (SQLNCLI) 是一种低级别的 COM API，用于访问数据。 建议将 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB 访问接口用于开发需要高性能的工具、实用工具或底层组件。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB 访问接口是直接访问 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 表格格式数据流 (TDS) 协议的本机高性能访问接口。  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 对连接到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 的应用程序提供 OLE DB 支持。  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB 访问接口是 OLE DB 版本 2.0 兼容提供程序。  
 
> [!IMPORTANT]
> [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB (SQLNCLI) 保持不推荐使用，不建议用于新的开发工作。 相反，使用新[Microsoft OLE DB 驱动程序适用于 SQL Server](../../../connect/oledb/oledb-driver-for-sql-server.md) (MSOLEDBSQL) 这将使用最新的服务器功能更新。
  
## <a name="in-this-section"></a>本节内容  
  
-   [创建 SQL Server Native Client OLE DB 提供程序应用程序](../../../relational-databases/native-client-ole-db-provider/creating-a-sql-server-native-client-ole-db-provider-application.md)  
  
-   [数据源对象&#40;OLE DB&#41;](../../../relational-databases/native-client-ole-db-data-source-objects/data-source-objects-ole-db.md)  
  
-   [命令](../../../relational-databases/native-client-ole-db-commands/commands.md)  
  
-   [行集](../../../relational-databases/native-client-ole-db-rowsets/rowsets.md)  
  
-   [存储过程](../../../relational-databases/native-client/ole-db/stored-procedures.md)  
  
-   [BLOB 和 OLE 对象](../../../relational-databases/native-client-ole-db-blobs/blobs-and-ole-objects.md)  
  
-   [表和索引](../../../relational-databases/native-client-ole-db-tables-indexes/tables-and-indexes.md)  
  
-   [数据类型&#40;OLE DB&#41;](../../../relational-databases/native-client-ole-db-data-types/data-types-ole-db.md)  
  
-   [架构行集支持 (OLE DB)](../../../relational-databases/native-client/ole-db/schema-rowset-support-ole-db.md)  
  
-   [表值参数 (OLE DB)](../../../relational-databases/native-client-ole-db-table-valued-parameters/table-valued-parameters-ole-db.md)  
  
-   [日期和时间改进 (OLE DB)](../../../relational-databases/native-client-ole-db-date-time/date-and-time-improvements-ole-db.md)  
  
-   [大型 CLR 用户定义类型 (OLE DB)](../../../relational-databases/native-client/ole-db/large-clr-user-defined-types-ole-db.md)  
  
-   [FILESTREAM 支持&#40;OLE DB&#41;](../../../relational-databases/native-client/ole-db/filestream-support-ole-db.md)  
  
-   [中的](../../../relational-databases/native-client-ole-db-transactions/transactions.md)  
  
-   [错误](../../../relational-databases/native-client-ole-db-errors/errors.md)  
  
-   [客户端连接中的服务主体名称 (SPN) (OLE DB)](../../../relational-databases/native-client/ole-db/service-principal-names-spns-in-client-connections-ole-db.md)  
  
-   [稀疏列支持 (OLE DB)](../../../relational-databases/native-client/ole-db/sparse-columns-support-ole-db.md)  
  
-   [SQL Server 本机客户端&#40;OLE DB&#41;引用](../../../relational-databases/native-client-ole-db-interfaces/sql-server-native-client-ole-db-interfaces.md)  
  
-   [OLE DB 操作指南主题](../../../relational-databases/native-client-ole-db-how-to/ole-db-how-to-topics.md)  
  
## <a name="see-also"></a>请参阅  
 [SQL Server Native Client 编程](../../../relational-databases/native-client/sql-server-native-client-programming.md)  
  
  
