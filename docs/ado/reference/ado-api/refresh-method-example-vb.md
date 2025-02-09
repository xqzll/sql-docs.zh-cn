---
title: Refresh 方法示例 (VB) |Microsoft Docs
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
- Refresh method [ADO], Visual Basic example
ms.assetid: f5375fa1-4711-4f7e-9ba4-54c427f71325
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: c44797b663007600b66db3d40d910d7f2459ad89
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "66711701"
---
# <a name="refresh-method-example-vb"></a>Refresh 方法示例 (VB)
此示例演示如何使用[刷新](../../../ado/reference/ado-api/refresh-method-ado.md)方法来刷新[参数](../../../ado/reference/ado-api/parameters-collection-ado.md)存储过程的集合[命令](../../../ado/reference/ado-api/command-object-ado.md)对象。  
  
```vb
'BeginRefreshVB  
Public Sub Main()  
    On Error GoTo ErrorHandler  
  
    'To integrate this code  
    'replace the data source and initial catalog values  
    'in the connection strings  
  
    ' connection and recordset variables  
    Dim Cnxn As ADODB.Connection  
    Dim cmdByRoyalty As ADODB.Command  
    Dim rstByRoyalty As ADODB.Recordset  
    Dim rstAuthors As ADODB.Recordset  
    Dim strCnxn As String  
    Dim strSQLAuthors As String  
     ' record variables  
    Dim intRoyalty As Integer  
    Dim strAuthorID As String  
    Dim strRoyalty As String  
  
    ' Open connection  
    Set Cnxn = New ADODB.Connection  
    strCnxn = "Provider='sqloledb';Data Source='MySqlServer';" & _  
        "Initial Catalog='Pubs';Integrated Security='SSPI';"  
    Cnxn.Open strCnxn  
  
    ' Open a command object for a stored procedure  
    ' with one parameter  
    Set cmdByRoyalty = New ADODB.Command  
    Set cmdByRoyalty.ActiveConnection = Cnxn  
    cmdByRoyalty.CommandText = "byroyalty"  
    cmdByRoyalty.CommandType = adCmdStoredProc  
    cmdByRoyalty.Parameters.Refresh  
  
    ' Get parameter value, execute the command  
    ' and store the results in a recordset  
    strRoyalty = InputBox("Enter royalty:")  
    If strRoyalty = "" Then  
        Err.Raise 1, , "You either didn't enter royalty or canceled the input box. Exit the application"  
    End If  
  
    intRoyalty = Trim(strRoyalty)  
    cmdByRoyalty.Parameters(1) = intRoyalty  
    Set rstByRoyalty = cmdByRoyalty.Execute()  
  
    ' Open the Authors table to get author names for display  
    Set rstAuthors = New ADODB.Recordset  
    strSQLAuthors = "Authors"  
    rstAuthors.Open strSQLAuthors, Cnxn, adOpenForwardOnly, adLockPessimistic, adCmdTable  
  
    ' Print current data in the recordset  
    ' and add author names  
    Debug.Print "Authors with " & intRoyalty & " percent royalty"  
  
    Do Until rstByRoyalty.EOF  
        strAuthorID = rstByRoyalty!au_id  
        Debug.Print "   " & rstByRoyalty!au_id & ", ";  
        rstAuthors.Filter = "au_id = '" & strAuthorID & "'"  
        Debug.Print rstAuthors!au_fname & " "; rstAuthors!au_lname  
        rstByRoyalty.MoveNext  
    Loop  
  
    ' clean up  
    rstByRoyalty.Close  
    rstAuthors.Close  
    Cnxn.Close  
    Set rstByRoyalty = Nothing  
    Set rstAuthors = Nothing  
    Set Cnxn = Nothing  
    Exit Sub  
  
ErrorHandler:  
    ' clean up  
    If Not rstByRoyalty Is Nothing Then  
        If rstByRoyalty.State = adStateOpen Then rstByRoyalty.Close  
    End If  
    Set rstByRoyalty = Nothing  
  
    If Not rstAuthors Is Nothing Then  
        If rstAuthors.State = adStateOpen Then rstAuthors.Close  
    End If  
    Set rstAuthors = Nothing  
  
    If Not Cnxn Is Nothing Then  
        If Cnxn.State = adStateOpen Then Cnxn.Close  
    End If  
    Set Cnxn = Nothing  
  
    If Err <> 0 Then  
        MsgBox Err.Source & "-->" & Err.Description, , "Error"  
    End If  
End Sub  
'EndRefreshVB  
```  
  
## <a name="see-also"></a>请参阅  
 [命令对象 (ADO)](../../../ado/reference/ado-api/command-object-ado.md)   
 [参数集合 (ADO)](../../../ado/reference/ado-api/parameters-collection-ado.md)   
 [Refresh 方法 (ADO)](../../../ado/reference/ado-api/refresh-method-ado.md)
