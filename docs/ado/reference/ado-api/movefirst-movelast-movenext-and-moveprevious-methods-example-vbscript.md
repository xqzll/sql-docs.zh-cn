---
title: 将记录指针的记录集示例 (VBScript) 移动 |Microsoft Docs
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
- MoveLast method [ADO], VBScript example
- MoveNext method [ADO], VBScript example
- MovePrevious method [ADO], VBScript example
- MoveFirst method [ADO], VBScript example
ms.assetid: 911aa1dd-2786-4f34-992c-bb2fbdabcbdf
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: e33662b69d4e466cb6bdea40d051dfd32d566b8e
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "66707352"
---
# <a name="movefirst-movelast-movenext-and-moveprevious-methods-example-vbscript"></a>MoveFirst、 MoveLast、 MoveNext 和 MovePrevious 方法示例 (VBScript)
此示例使用[MoveFirst](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)， [MoveLast](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)， [MoveNext](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)，以及[MovePrevious](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)方法移动记录指针[记录集](../../../ado/reference/ado-api/recordset-object-ado.md)基于提供的命令。  
  
 剪切并将以下代码粘贴到记事本或其他文本编辑器，并将其保存为**MoveFirstVBS.asp**。 你可以在任何浏览器中查看结果。  
  
```  
<!-- BeginMoveFirstVBS -->  
<%@ Language=VBScript %>  
<%' use this meta tag instead of adovbs.inc%>  
<!--METADATA TYPE="typelib" uuid="00000205-0000-0010-8000-00AA006D2EA4" -->  
<HTML>  
<HEAD>  
<TITLE>ADO MoveNext, MovePrevious, MoveLast, MoveFirst Methods</TITLE>  
  
<SCRIPT LANGUAGE="VBScript">  
<!--  
   Sub cmdDown_OnClick  
      'Set Values in Form Input Boxes and Submit Form  
      Document.form.MoveAction.Value = "MovePrev"  
      Document.Form.Submit  
   End Sub  
  
   Sub cmdUp_OnClick  
      Document.form.MoveAction.Value = "MoveNext"  
      Document.Form.Submit  
   End Sub  
  
   Sub cmdFirst_OnClick  
      Document.form.MoveAction.Value = "MoveFirst"  
      Document.Form.Submit  
   End Sub  
  
   Sub cmdLast_OnClick  
      Document.form.MoveAction.Value = "MoveLast"  
      Document.Form.Submit  
   End Sub  
//-->  
</SCRIPT>  
</HEAD>  
  
<body bgcolor="white">   
<h1 align="center">ADO MoveNext, MovePrevious <br> MoveLast & MoveFirst Methods</h1>  
<% ' to integrate/test this code replace the   
   ' Data Source value in the Connection string%>  
<%   
   ' connection and recordset variables  
   Dim Cnxn, strCnxn  
   Dim rsEmployees, strSQLEmployees  
  
   ' open connection  
    Set Cnxn = Server.CreateObject("ADODB.Connection")  
    strCnxn = "Provider='sqloledb';Data Source=" & _  
            Request.ServerVariables("SERVER_NAME") & ";" & _  
            "Integrated Security='SSPI';Initial Catalog='Northwind';"  
    Cnxn.Open strCnxn  
  
    ' create and open Recordset using object refs  
   Set rsEmployees = Server.CreateObject("ADODB.Recordset")  
   strSQLEmployees = "Employees"  
  
   rsEmployees.ActiveConnection = Cnxn  
   rsEmployees.CursorLocation = adUseClient  
   rsEmployees.CursorType = adOpenKeyset  
   rsEmployees.LockType = adLockOptimistic  
   rsEmployees.Source = strSQLEmployees  
   rsEmployees.Open  
  
   rsEmployees.MoveFirst  
  
   If Not IsEmpty(Request.Form("MoveAction")) Then  
      strAction = Request.Form("MoveAction")  
      varPosition  = Request.Form("Position")  
  
      rsEmployees.AbsolutePosition = varPosition  
  
      Select Case strAction  
  
        Case "MoveNext"  
  
         rsEmployees.MoveNext  
         If rsEmployees.EOF Then  
            rsEmployees.MoveLast  
            strMessage = "Can't move beyond the last record."  
         End If  
  
        Case "MovePrev"  
  
         rsEmployees.MovePrevious  
         If rsEmployees.BOF Then  
            rsEmployees.MoveFirst  
            strMessage = "Can't move beyond the first record."  
         End If  
  
        Case "MoveLast"  
  
         rsEmployees.MoveLast  
  
        Case "MoveFirst"  
  
         rsEmployees.MoveFirst  
  
      End Select  
   End If  
  
%>  
  
<!-- Display Current Record Number and Recordset Size -->  
<h2>Record Number <%=rsEmployees.AbsolutePosition%> of <%=rsEmployees.RecordCount%></H2>  
<hr>  
<table cellpadding=5 border=0>  
<!-- BEGIN column header row for Customer Table-->  
<tr>  
   <th>Name</th>  
   <th>Hire Date</th>  
</tr>  
  
<!--Display ADO Data from Customer Table-->  
<tr>  
  <td><%= rsEmployees("LastName") & ", " %>   
      <%= rsEmployees("FirstName") & " " %></td>  
  <td><%= rsEmployees("HireDate")%></td>  
</tr>   
<tr>  
  <td colspan=2><%=strMessage%></td>  
</tr>  
</table>  
  
<hr>  
  
<form Name="Form" Method="Post" Action="MoveFirstVbs.asp">  
<Input Type=Button Name=cmdDown Value="<">  
<Input Type=Button Name=cmdUp Value=">">  
<BR>  
<H3>Click Direction Arrows to Use MovePrevious or MoveNext</H3>  
<Input Type=Button Name=cmdFirst Value="First Record">  
<Input Type=Button Name=cmdLast Value="Last Record">  
  
<!-- Use Hidden Form Fields to record values to send to Server -->  
  
<input Type="Hidden" Size="4" Name="MoveAction" Value="Move">  
<input Type="Hidden" Size="4" Name="Position" Value="<%= rsEmployees.AbsolutePosition%>">  
</form>  
  
<HR>  
</BODY>  
  
<%  
    ' clean up  
    If rsEmployees.State = adStateOpen then  
        rsEmployees.Close  
    End If  
    If Cnxn.State = adStateOpen then  
        Cnxn.Close  
    End If  
%>  
</HTML>  
<!-- EndMoveFirstVBS -->  
```  
  
## <a name="see-also"></a>请参阅  
 [MoveFirst、 MoveLast、 MoveNext 和 MovePrevious 方法 (ADO)](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)   
 [记录集对象 (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)
