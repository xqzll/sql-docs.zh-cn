---
title: Update 和 CancelUpdate 方法示例 (VB) |Microsoft Docs
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
- CancelUpdate method [ADO]
- Update method [ADO], Visual Basic example
ms.assetid: 55bedd08-7440-4da4-b854-4ac9ef2fdedb
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 690173882856e1b53e6f50eefc2cdd9115bd38bf
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "66710392"
---
# <a name="update-and-cancelupdate-methods-example-vb"></a>Update 和 CancelUpdate 方法示例 (VB)
此示例演示[更新](../../../ado/reference/ado-api/update-method.md)方法一起[CancelUpdate](../../../ado/reference/ado-api/cancelupdate-method-ado.md)方法。  
  
```  
'BeginUpdateVB  
Public Sub Main()  
    On Error GoTo ErrorHandler  
  
    'To integrate this code  
    'replace the data source and initial catalog values  
    'in the connection string  
  
    ' recordset and connection variables  
    Dim rstEmployees As ADODB.Recordset  
    Dim Cnxn As ADODB.Connection  
    Dim strCnxn As String  
    Dim strSQLEmployees As String  
     ' buffer variables  
    Dim strOldFirst As String  
    Dim strOldLast As String  
    Dim strMessage As String  
  
    ' Open connection  
    Set Cnxn = New ADODB.Connection  
    strCnxn = "Provider='sqloledb';Data Source='MySqlServer';" & _  
        "Initial Catalog='Pubs';Integrated Security='SSPI';"  
    Cnxn.Open strCnxn  
  
    ' Open recordset to enable changes  
    Set rstEmployees = New ADODB.Recordset  
    strSQLEmployees = "SELECT fname, lname FROM Employee ORDER BY lname"  
    rstEmployees.Open strSQLEmployees, Cnxn, adOpenKeyset, adLockOptimistic, adCmdText  
  
    ' Store original data  
    strOldFirst = rstEmployees!fname  
    strOldLast = rstEmployees!lname  
    ' Change data in edit buffer  
    rstEmployees!fname = "Linda"  
    rstEmployees!lname = "Kobara"  
  
    ' Show contents of buffer and get user input  
    strMessage = "Edit in progress:" & vbCr & _  
        "  Original data = " & strOldFirst & " " & _  
        strOldLast & vbCr & "  Data in buffer = " & _  
        rstEmployees!fname & " " & rstEmployees!lname & vbCr & vbCr & _  
        "Use Update to replace the original data with " & _  
        "the buffered data in the Recordset?"  
  
    If MsgBox(strMessage, vbYesNo) = vbYes Then  
        rstEmployees.Update  
    Else  
        rstEmployees.CancelUpdate  
    End If  
  
    ' show the resulting data  
    MsgBox "Data in recordset = " & rstEmployees!fname & " " & _  
       rstEmployees!lname  
  
    ' restore original data because this is a demonstration  
    If Not (strOldFirst = rstEmployees!fname And _  
           strOldLast = rstEmployees!lname) Then  
        rstEmployees!fname = strOldFirst  
        rstEmployees!lname = strOldLast  
        rstEmployees.Update  
    End If  
  
    ' clean up  
    rstEmployees.Close  
    Cnxn.Close  
    Set rstEmployees = Nothing  
    Set Cnxn = Nothing  
    Exit Sub  
  
ErrorHandler:  
    ' clean up  
    If Not rstEmployees Is Nothing Then  
        If rstEmployees.State = adStateOpen Then rstEmployees.Close  
    End If  
    Set rstEmployees = Nothing  
  
    If Not Cnxn Is Nothing Then  
        If Cnxn.State = adStateOpen Then Cnxn.Close  
    End If  
    Set Cnxn = Nothing  
  
    If Err <> 0 Then  
        MsgBox Err.Source & "-->" & Err.Description, , "Error"  
    End If  
End Sub  
' EndUpdateVB  
```  
  
 此示例演示**更新**方法一起[AddNew](../../../ado/reference/ado-api/addnew-method-ado.md)方法。  
  
```  
Attribute VB_Name = "Update"  
```  
  
## <a name="see-also"></a>请参阅  
 [CancelUpdate 方法 (ADO)](../../../ado/reference/ado-api/cancelupdate-method-ado.md)   
 [记录集对象 (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)   
 [Update 方法](../../../ado/reference/ado-api/update-method.md)
