---
title: CancelUpdate 方法示例 (VBScript) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
dev_langs:
- VB
helpviewer_keywords:
- CancelUpdate method [ADO], VBScript example
ms.assetid: c23912f0-1288-4727-8fb4-f643b8811cf7
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 620da1d2d9e63d0f9699328892b87cdd3d3cb807
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "66701764"
---
# <a name="cancelupdate-method-example-vbscript"></a>CancelUpdate 方法示例 (VBScript)
> [!IMPORTANT]
>  从 Windows 8 和 Windows Server 2012 开始，不再在 Windows 操作系统中包含 RDS 服务器组件 (请参阅 Windows 8 和[Windows Server 2012 兼容性指南](https://www.microsoft.com/download/details.aspx?id=27416)以了解详细信息)。 将 Windows 的未来版本中删除 RDS 客户端组件。 请避免在新的开发工作中使用该功能，并着手修改当前还在使用该功能的应用程序。 使用 RDS 的应用程序应迁移到[WCF 数据服务](https://go.microsoft.com/fwlink/?LinkId=199565)。  
  
 若要测试此示例中，代码剪切并粘贴此之间\<正文 > 和\</b o d > 标记中普通的 HTML 文档并将其命名**CancelUpdateVBS.asp**。 ASP 脚本将识别您的 internet 服务器。 你将需要编辑的服务器，以反映你自己的设置名称。 只需将连接字符串中的值从 MyServer 更改为 SQL Server 安装的名称。  
  
```  
<!-- BeginCancelUpdateVBS -->  
<%@Language=VBScript%>  
  
<%'Option Explicit%>  
<% 'use the following META tag instead of adovbs.inc%>  
<!--METADATA TYPE="typelib" uuid="00000205-0000-0010-8000-00AA006D2EA4" -->  
<HTML>  
<HEAD>  
<META NAME="GENERATOR" Content="Microsoft Visual Studio 6.0">  
<TITLE></TITLE>  
</HEAD>  
<BODY>  
<CENTER>  
<H1>Remote Data Service</H1>  
<H2>SubmitChanges and CancelUpdate Methods</H2>  
  
<%  ' to integrate/test this code replace the Server property value and   
    ' the Data Source value in the Connect property with appropriate values%>  
  
<HR>  
<OBJECT ID=RDS classid="clsid:BD96C556-65A3-11D0-983A-00C04FC29E33" HEIGHT=1 WIDTH=1></OBJECT>  
<SCRIPT Language="VBScript">  
  
     'set RDS properties for control just created  
  
    RDS.Server = "https://<%=Request.ServerVariables("SERVER_NAME")%>"  
    RDS.SQL = "Select * from Employees"  
    RDS.Connect = "Provider='sqloledb';Integrated Security='SSPI';Initial Catalog='Northwind';"  
    RDS.Refresh  
</SCRIPT>  
  
<TABLE DATASRC=#RDS>  
<THEAD>  
<TR ID="ColHeaders">  
   <TH>ID</TH>  
   <TH>FName</TH>  
   <TH>LName</TH>  
   <TH>Title</TH>  
   <TH>Hire Date</TH>  
   <TH>Birth Date</TH>  
   <TH>Extension</TH>  
   <TH>Home Phone</TH>  
</TR>  
</THEAD>  
<TBODY>  
<TR>  
   <TD> <INPUT DATAFLD="EmployeeID" size=4> </TD>  
   <TD> <INPUT DATAFLD="FirstName" size=10> </TD>  
   <TD> <INPUT DATAFLD="LastName" size=10> </TD>  
   <TD> <INPUT DATAFLD="Title" size=10> </TD>  
   <TD> <INPUT DATAFLD="HireDate" size=10> </TD>  
   <TD> <INPUT DATAFLD="BirthDate" size=10> </TD>  
   <TD> <INPUT DATAFLD="Extension" size=10> </TD>  
   <TD> <INPUT DATAFLD="HomePhone" size=8> </TD>  
</TR>  
</TBODY>  
</TABLE>  
<HR>  
<INPUT TYPE=button NAME="SubmitChange" VALUE="Submit Changes">  
<INPUT TYPE=button NAME="CancelChange" VALUE="Cancel Update">  
<BR>  
<H4>Alter a current entry on the grid. Move off that Row. <BR>  
Submit the Changes to your DBMS or cancel the updates. </H4>  
</CENTER>  
<SCRIPT Language="VBScript">  
  
Sub SubmitChange_OnClick  
  
    msgbox "Changes will be made"  
    RDS.SubmitChanges     
    RDS.Refresh  
  
End Sub  
  
Sub CancelChange_OnClick  
  
    msgbox "Changes will be cancelled"  
    RDS.CancelUpdate  
    RDS.Refresh  
  
End Sub  
-->  
</SCRIPT>  
  
</BODY>  
</HTML>  
<!-- EndCancelUpdateVBS -->  
```  
  
## <a name="see-also"></a>请参阅  
 [CancelUpdate 方法 (ADO)](../../../ado/reference/ado-api/cancelupdate-method-ado.md)



