---
title: 结合使用 ADO 和适用于 SQL Server 的 OLE DB 驱动程序 | Microsoft Docs
description: 结合使用 ADO 和适用于 SQL Server 的 OLE DB 驱动程序
ms.custom: ''
ms.date: 06/12/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- OLE DB Driver for SQL Server, ADO
- data access [OLE DB Driver for SQL Server], ADO
- ADO [OLE DB Driver for SQL Server]
- MSOLEDBSQL, ADO
author: pmasl
ms.author: pelopes
manager: jroth
ms.openlocfilehash: 1906ad25e9bb170b8979f44757ec5742ad9ec6c4
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "66778052"
---
# <a name="using-ado-with-ole-db-driver-for-sql-server"></a>结合使用 ADO 和适用于 SQL Server 的 OLE DB 驱动程序
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  要利用 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] 中引入的新功能，例如多个活动结果集 (MARS)、查询通知、用户定义类型 (UDT) 或新的 xml 数据类型，使用 ActiveX Data Objects (ADO) 的现有应用程序应使用适用于 SQL Server 的 OLE DB 驱动程序作为数据访问提供程序  。  
  
 要让 ADO 能够使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 最新版的新功能，适用于 SQL Server 的 OLE DB 驱动程序进行了一些增强，扩展了 OLE DB 的核心功能。 借助这些增强功能，ADO 应用程序可使用更新的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 功能，还可使用 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] 中引入的两个数据类型（xml 和 udt）   。 通过这些增强功能，还可探索对 varchar、nvarchar 和 varbinary 数据类型的强化    。 适用于 SQL Server 的 OLE DB 驱动程序将 SSPROP_INIT_DATATYPECOMPATIBILITY 初始化属性添加到 DBPROPSET_SQLSERVERDBINIT 属性集供 ADO 应用程序使用，从而通过与 ADO 兼容的方式公开新的数据类型。 此外，SQL Server 的 OLE DB 驱动程序还定义了名为的新连接字符串关键字**DataTypeCompatibility** ，设置连接字符串中。  

> [!NOTE]  
>  现有 ADO 应用程序可以使用 SQLOLEDB 访问接口来访问和更新 XML、UDT 以及大型值文本和二进制字段值。 新的更大型的 varchar(max)、nvarchar(max) 和 varbinary(max) 数据类型分别作为 ADO 类型 adLongVarChar、adLongVarWChar 和 adLongVarBinary 返回       。 XML 列作为 adLongVarChar 返回，而 UDT 列作为 adVarBinary 返回   。 但是，如果使用 OLE DB 驱动程序的 SQL Server (MSOLEDBSQL) 而不是 SQLOLEDB，您需要确保设置**DataTypeCompatibility**关键字为"80"，以便新的数据类型能正确映射到 ADO 数据类型。  

## <a name="enabling-ole-db-driver-for-sql-server-from-ado"></a>通过 ADO 启用适用于 SQL Server 的 OLE DB 驱动程序  
 ADO 应用程序需要在其连接字符串中实现下列关键字，才能使用适用于 SQL Server 的 OLE DB 驱动程序：  

-   `Provider=MSOLEDBSQL`  

-   `DataTypeCompatibility=80`  

 若要详细了解 OLE DB Driver for SQL Server 支持的 ADO 连接字符串关键字，请参阅[结合使用连接字符串关键字与 OLE DB Driver for SQL Server](../../oledb/applications/using-connection-string-keywords-with-oledb-driver-for-sql-server.md)。  

 下例创建了一个 ADO 连接字符串，它完全启用以结合适用于 SQL Server 的 OLE DB 驱动程序一起使用，包括启用 MARS 功能：  

```  
Dim con As New ADODB.Connection  

con.ConnectionString = "Provider=MSOLEDBSQL;" _  
         & "Server=(local);" _  
         & "Database=AdventureWorks;" _   
         & "Integrated Security=SSPI;" _  
         & "DataTypeCompatibility=80;" _  
         & "MARS Connection=True;"  
con.Open  
```  

## <a name="examples"></a>示例  
 以下部分提供如何使用 ADO 与 OLE DB 驱动程序适用于 SQL Server 的示例。  

### <a name="retrieving-xml-column-data"></a>检索 XML 列数据  
 本例中，使用记录集从 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] AdventureWorks 示例数据库中的 XML 列检索并显示数据  。  

```  
Dim con As New ADODB.Connection  
Dim rst As New ADODB.Recordset  
Dim sXMLResult As String  

con.ConnectionString = "Provider=MSOLEDBSQL;" _  
         & "Server=(local);" _  
         & "Database=AdventureWorks;" _   
         & "Integrated Security=SSPI;" _   
         & "DataTypeCompatibility=80;"  

con.Open  

' Get the xml data as a recordset.  
Set rst.ActiveConnection = con  
rst.Source = "SELECT AdditionalContactInfo FROM Person.Contact " _  
   & "WHERE AdditionalContactInfo IS NOT NULL"  
rst.Open  

' Display the data in the recordset.  
While (Not rst.EOF)  
   sXMLResult = rst.Fields("AdditionalContactInfo").Value  
   Debug.Print (sXMLResult)  
   rst.MoveNext  
End While  

con.Close  
Set con = Nothing  
```  

> [!NOTE]  
>  XML 列不支持记录集筛选。 如果使用，将返回错误。  

### <a name="retrieving-udt-column-data"></a>检索 UDT 列数据  
 在该示例中，使用 Command 对象执行返回 UDT 的 SQL 查询，并更新 UDT 数据，然后将新数据插入数据库中  。 该示例假定已在数据库中注册 Point UDT  。  

```  
Dim con As New ADODB.Connection  
Dim cmd As New ADODB.Command  
Dim rst As New ADODB.Recordset  
Dim strOldUDT As String  
Dim strNewUDT As String  
Dim aryTempUDT() As String  
Dim strTempID As String  
Dim i As Integer  

con.ConnectionString = "Provider=MSOLEDBSQL;" _  
         & "Server=(local);" _  
         & "Database=AdventureWorks;" _   
         & "Integrated Security=SSPI;" _  
         & "DataTypeCompatibility=80;"  

con.Open  

' Get the UDT value.  
Set cmd.ActiveConnection = con  
cmd.CommandText = "SELECT ID, Pnt FROM dbo.Points.ToString()"  
Set rst = cmd.Execute  
strTempID = rst.Fields(0).Value  
strOldUDT = rst.Fields(1).Value  

' Do something with the UDT by adding i to each point.  
arytempUDT = Split(strOldUDT, ",")  
i = 3  
strNewUDT = LTrim(Str(Int(aryTempUDT(0)) + i)) + "," + _  
   LTrim(Str(Int(aryTempUDT(1)) + i))  

' Insert the new value back into the database.  
cmd.CommandText = "UPDATE dbo.Points SET Pnt = '" + strNewUDT + _  
   "' WHERE ID = '" + strTempID + "'"  
cmd.Execute  

con.Close  
Set con = Nothing  
```  

### <a name="enabling-and-using-mars"></a>启用和使用 MARS  
 在本例中，构造连接字符串，从而通过适用于 SQL Server 的 OLE DB 驱动程序启用 MARS，然后创建两个要通过同一连接执行的记录集对象。  

```  
Dim con As New ADODB.Connection  

con.ConnectionString = "Provider=MSOLEDBSQL;" _  
         & "Server=(local);" _  
         & "Database=AdventureWorks;" _   
         & "Integrated Security=SSPI;" _  
         & "DataTypeCompatibility=80;" _  
         & "MARS Connection=True;"  
con.Open  

Dim recordset1 As New ADODB.Recordset  
Dim recordset2 As New ADODB.Recordset  

Dim recordsaffected As Integer  
Set recordset1 =  con.Execute("SELECT * FROM Table1", recordsaffected, adCmdText)  
Set recordset2 =  con.Execute("SELECT * FROM Table2", recordsaffected, adCmdText)  

con.Close  
Set con = Nothing  
```  

 在以前的 OLE DB 访问接口版本中，该代码会导致在第二次执行时创建隐式的连接，因为每个单独的连接只能打开一个活动的结果集。 由于该隐式连接未加入 OLE DB 连接池，因此这会导致额外的开销。 借助适用于 SQL Server 的 OLE DB 驱动程序提供的 MARS 功能，可在一个连接上获取多个活动结果。  

## <a name="see-also"></a>另请参阅  
 [使用适用于 SQL Server 的 OLE DB 驱动程序生成应用程序](../../oledb/applications/building-applications-with-oledb-driver-for-sql-server.md)  
