---
title: 存储过程属性示例 (VB) |Microsoft Docs
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
- Size property [ADO], Visual Basic example
- CommandTimeout property [ADO], Visual Basic example
- CommandText property [ADO], Visual Basic example
- ActiveConnection property [ADO], Visual Basic example
- Direction property [ADO], Visual Basic example
ms.assetid: dade4531-0bcc-4a52-8f86-b110ba2a3f9d
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: bf2e9677025afe00788f57129fbf37d39c6163a3
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "66704031"
---
# <a name="activeconnection-commandtext-commandtimeout-commandtype-size-and-direction-properties-example-vb"></a>ActiveConnection、 CommandText、 CommandTimeout、 CommandType、 大小和方向属性示例 (VB)
此示例使用[ActiveConnection](../../../ado/reference/ado-api/activeconnection-property-ado.md)， [CommandText](../../../ado/reference/ado-api/commandtext-property-ado.md)， [CommandTimeout](../../../ado/reference/ado-api/commandtimeout-property-ado.md)， [CommandType](../../../ado/reference/ado-api/commandtype-property-ado.md)，[大小](../../../ado/reference/ado-api/size-property-ado-parameter.md)，并[方向](../../../ado/reference/ado-api/direction-property.md)属性来执行存储的过程。  
  
```  
'BeginActiveConnectionVB  
  
    'To integrate this code  
    'replace the data source and initial catalog values  
    'in the connection string  
  
Public Sub Main()  
    On Error GoTo ErrorHandler  
  
    'recordset, command and connection variables  
    Dim Cnxn As ADODB.Connection  
    Dim cmdByRoyalty As ADODB.Command  
    Dim prmByRoyalty As ADODB.Parameter  
    Dim rstByRoyalty As ADODB.Recordset  
    Dim rstAuthors As ADODB.Recordset  
    Dim strCnxn As String  
    Dim strSQLAuthors As String  
    Dim strSQLByRoyalty As String  
     'record variables  
    Dim intRoyalty As Integer  
    Dim strAuthorID As String  
  
    ' Define a command object for a stored procedure  
    Set Cnxn = New ADODB.Connection  
    strCnxn = "Provider='sqloledb';Data Source='MySqlServer';" & _  
        "Initial Catalog='Pubs';Integrated Security='SSPI';"  
    Cnxn.Open strCnxn  
  
    Set cmdByRoyalty = New ADODB.Command  
    Set cmdByRoyalty.ActiveConnection = Cnxn  
    ' Set the criteria  
    strSQLByRoyalty = "byroyalty"  
    cmdByRoyalty.CommandText = strSQLByRoyalty  
    cmdByRoyalty.CommandType = adCmdStoredProc  
    cmdByRoyalty.CommandTimeout = 15  
  
    ' Define the stored procedure's input parameter  
    intRoyalty = Trim(InputBox("Enter royalty:"))  
    Set prmByRoyalty = New ADODB.Parameter  
    prmByRoyalty.Type = adInteger  
    prmByRoyalty.Size = 3  
    prmByRoyalty.Direction = adParamInput  
    prmByRoyalty.Value = intRoyalty  
  
    cmdByRoyalty.Parameters.Append prmByRoyalty  
  
    ' Create a recordset by executing the command.  
    Set rstByRoyalty = cmdByRoyalty.Execute()  
  
    ' Open the Authors Table to get author names for display  
    Set rstAuthors = New ADODB.Recordset  
    strSQLAuthors = "Authors"  
  
    'rstAuthors.Open strSQLAuthors, strCnxn, , , adCmdTable  
    rstAuthors.Open strSQLAuthors, strCnxn, adOpenForwardOnly, adLockReadOnly, adCmdTable  
    'the above two lines of code are identical as the default values for  
    'CursorType and LockType arguments match those shown  
  
    ' Print the recordset and add author names from Table  
    Debug.Print "Authors with " & intRoyalty & _  
       " percent royalty"  
  
    Do Until rstByRoyalty.EOF  
        strAuthorID = rstByRoyalty!au_id  
        Debug.Print , rstByRoyalty!au_id & ", ";  
        rstAuthors.Filter = "au_id = '" & strAuthorID & "'"  
        Debug.Print rstAuthors!au_fname & " " & _  
            rstAuthors!au_lname  
        rstByRoyalty.MoveNext  
    Loop  
  
    ' clean up  
    rstAuthors.Close  
    rstByRoyalty.Close  
    Cnxn.Close  
    Set rstAuthors = Nothing  
    Set rstByRoyalty = Nothing  
    Set Cnxn = Nothing  
    Exit Sub  
  
ErrorHandler:  
    ' clean up  
    If Not rstAuthors Is Nothing Then  
        If rstAuthors.State = adStateOpen Then rstAuthors.Close  
    End If  
    Set rstAuthors = Nothing  
  
    If Not rstByRoyalty Is Nothing Then  
        If rstByRoyalty.State = adStateOpen Then rstByRoyalty.Close  
    End If  
    Set rstByRoyalty = Nothing  
  
    If Not Cnxn Is Nothing Then  
        If Cnxn.State = adStateOpen Then Cnxn.Close  
    End If  
    Set Cnxn = Nothing  
  
    If Err <> 0 Then  
        MsgBox Err.Source & "-->" & Err.Description, , "Error"  
    End If  
End Sub  
'EndActiveConnectionVB  
```  
  
## <a name="see-also"></a>请参阅  
 [ActiveCommand 属性 (ADO)](../../../ado/reference/ado-api/activecommand-property-ado.md)   
 [命令对象 (ADO)](../../../ado/reference/ado-api/command-object-ado.md)   
 [CommandText 属性 (ADO)](../../../ado/reference/ado-api/commandtext-property-ado.md)   
 [CommandTimeout 属性 (ADO)](../../../ado/reference/ado-api/commandtimeout-property-ado.md)   
 [CommandType 属性 (ADO)](../../../ado/reference/ado-api/commandtype-property-ado.md)   
 [连接对象 (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)   
 [Direction 属性](../../../ado/reference/ado-api/direction-property.md)   
 [参数对象](../../../ado/reference/ado-api/parameter-object.md)   
 [记录对象 (ADO)](../../../ado/reference/ado-api/record-object-ado.md)   
 [记录集对象 (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)   
 [Size 属性（ADO 参数）](../../../ado/reference/ado-api/size-property-ado-parameter.md)
