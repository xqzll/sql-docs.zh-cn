---
title: Recordset 和 SourceRecordset 属性示例 (VBScript) |Microsoft Docs
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.prod: sql
ms.prod_service: connectivity
ms.topic: conceptual
dev_langs:
- VB
helpviewer_keywords:
- Source property [ADO], VBScript example
- Recordset property [ADO], VBScript example
ms.assetid: 95175316-cd10-4cf7-96ba-2a226fd97701
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 9cff6233f73cf2e49ff90b7e888d6f85155187b9
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "66718764"
---
# <a name="recordset-and-sourcerecordset-properties-example-vbscript"></a>Recordset 和 SourceRecordset 属性示例 (VBScript)
> [!IMPORTANT]
>  从 Windows 8 和 Windows Server 2012 开始，不再在 Windows 操作系统中包含 RDS 服务器组件 (请参阅 Windows 8 和[Windows Server 2012 兼容性指南](https://www.microsoft.com/download/details.aspx?id=27416)以了解详细信息)。 将 Windows 的未来版本中删除 RDS 客户端组件。 请避免在新的开发工作中使用该功能，并着手修改当前还在使用该功能的应用程序。 使用 RDS 的应用程序应迁移到[WCF 数据服务](https://go.microsoft.com/fwlink/?LinkId=199565)。  
  
 下面的示例演示如何设置的所需的参数[提高](../../../ado/reference/rds-api/datafactory-object-rdsserver.md)在运行时的默认业务对象。  
  
 若要测试此示例中，代码剪切并粘贴此之间\<正文 > 和\</b o d > 标记中普通的 HTML 文档并将其命名**RecordsetVBS.asp**。 ASP 脚本将识别您的服务器。  
  
```  
<!-- BeginRecordSetVBS -->  
<%@ Language=VBScript %>  
<html>  
<head>  
    <meta name="VI60_DefaultClientScript"  content=VBScript>  
    <meta name="GENERATOR" content="Microsoft Visual Studio 6.0">  
    <title>Recordset and SourceRecordset Properties Example (VBScript)</title>  
<style>  
<!--  
body {  
   font-family: 'Verdana','Arial','Helvetica',sans-serif;  
   BACKGROUND-COLOR:white;  
   COLOR:black;  
    }  
.thead {  
   background-color: #008080;   
   font-family: 'Verdana','Arial','Helvetica',sans-serif;   
   font-size: x-small;  
   color: white;  
   }  
.thead2 {  
   background-color: #800000;   
   font-family: 'Verdana','Arial','Helvetica',sans-serif;   
   font-size: x-small;  
   color: white;  
   }  
.tbody {   
   text-align: center;  
   background-color: #f7efde;  
   font-family: 'Verdana','Arial','Helvetica',sans-serif;   
   font-size: x-small;  
    }  
-->  
</style>  
</head>  
  
<body>  
<h1>Recordset and SourceRecordset Properties Example (VBScript)</h1>  
  
<Center>  
<H2>RDS API Code Examples</H2>  
<HR>  
<H3>Using SourceRecordset and Recordset with RDSServer.DataFactory</H3>  
<!-- RDS.DataSpace ID RDS1 -->  
<OBJECT ID="RDS1" WIDTH=1 HEIGHT=1   
CLASSID="CLSID:BD96C556-65A3-11D0-983A-00C04FC29E36">  
</OBJECT>  
  
<!-- RDS.DataControl with parameters set at Run Time -->  
<OBJECT classid="clsid:BD96C556-65A3-11D0-983A-00C04FC29E33"  
   ID=RDC WIDTH=1 HEIGHT=1>  
</OBJECT>  
  
<TABLE DATASRC=#RDC>  
   <TR>  
      <TD> <INPUT DATAFLD="FirstName" SIZE=15> </TD>  
      <TD> <INPUT DATAFLD="LastName" SIZE=15></TD>  
   </TR>  
</TABLE>  
<HR>  
<Input Size=70 Name="txtServer" Value="https://<%=Request.ServerVariables("SERVER_NAME")%>"><BR>  
<Input Size=70 Name="txtConnect" Value="Provider='sqloledb';Integrated Security='SSPI';Initial Catalog='Northwind'"><BR>  
<Input Size=70 Name="txtSQL" Value="SELECT FirstName, LastName FROM Employees">  
<HR>  
<INPUT TYPE=BUTTON NAME="Run" VALUE="Run"><BR>  
  
</Center>  
<Script Language="VBScript">  
  
   Dim rdsDF  
   Dim strServer  
   strServer = "https://<%=Request.ServerVariables("SERVER_NAME")%>"  
  
   Sub Run_OnClick()  
  
      Dim rs           
      ' Create RDSServer.DataFactory Object  
      Set rdsDF = RDS1.CreateObject("RDSServer.DataFactory", strServer)                 
      ' Get Recordset  
      Set rs = rdsDF.Query(txtConnect.Value,txtSQL.Value)  
  
      ' Set parameters of RDS.DataControl at run time  
      RDC.Server = txtServer.Value  
      RDC.SQL = txtSQL.Value  
      RDC.Connect = txtConnect.Value  
      RDC.Refresh  
  
   End Sub  
  
</Script>  
  
</body>  
</html>  
<!-- EndRecordsetVBS -->  
```  
  
## <a name="see-also"></a>请参阅  
 [DataFactory 对象 (RDSServer)](../../../ado/reference/rds-api/datafactory-object-rdsserver.md)   
 [Recordset、SourceRecordset 属性 (RDS)](../../../ado/reference/rds-api/recordset-sourcerecordset-properties-rds.md)



