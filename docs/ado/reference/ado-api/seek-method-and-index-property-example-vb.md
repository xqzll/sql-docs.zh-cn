---
title: Seek 方法和 Index 属性示例 (VB) |Microsoft Docs
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
- Seek method [ADO], Visual Basic example
- index property [ADO]
ms.assetid: 337c9eda-9ddf-49ac-94d3-b33114ba6224
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: db5be65f007a667d23f7d94b3a7ae17eb6d2f36c
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "66719098"
---
# <a name="seek-method-and-index-property-example-vb"></a>Seek 方法和 Index 属性示例 (VB)
此示例使用[记录集](../../../ado/reference/ado-api/recordset-object-ado.md)对象的[Seek](../../../ado/reference/ado-api/seek-method.md)方法和[索引](../../../ado/reference/ado-api/index-property.md)属性结合使用与给定***员工 ID***、 查找中的员工姓名***员工***Nwind.mdb 数据库表。  
  
```  
'BeginSeekVB  
Public Sub SeekX()  
    On Error GoTo ErrorHandler  
  
    ' To integrate this code replace the data source  
    ' in the connection string  
  
     'recordset and connection variables  
    Dim rstEmployees As ADODB.Recordset  
    Dim Cnxn As ADODB.Connection  
    Dim strCnxn As String  
    Dim strSQLEmployees As String  
  
    Dim strID As String  
    Dim strPrompt As String  
    strPrompt = "Enter an EmployeeID (e.g., 1 to 9)"  
  
    ' Open connection  
    Set Cnxn = New ADODB.Connection  
    strCnxn = "Provider='Microsoft.Jet.OLEDB.4.0';" & _  
                "Data Source='C:\Program Files\Microsoft Office XP\Office10\Samples\northwind.mdb';"  
    Cnxn.Open strCnxn  
  
     ' open recordset server-side for indexing  
    Set rstEmployees = New ADODB.Recordset  
    rstEmployees.CursorLocation = adUseServer  
    strSQLEmployees = "employees"  
    rstEmployees.Open strSQLEmployees, strCnxn, adOpenKeyset, adLockReadOnly, adCmdTableDirect  
  
    ' Does this provider support Seek and Index?  
    If rstEmployees.Supports(adIndex) And rstEmployees.Supports(adSeek) Then  
        rstEmployees.Index = "PrimaryKey"  
        ' Display all the employees  
            rstEmployees.MoveFirst  
            Do While rstEmployees.EOF = False  
                Debug.Print rstEmployees!EmployeeId; ": "; rstEmployees!FirstName; " "; _  
                    rstEmployees!LastName  
                rstEmployees.MoveNext  
            Loop  
  
    ' Prompt the user for an EmployeeID between 1 and 9  
          rstEmployees.MoveFirst  
          Do  
             strID = LCase(Trim(InputBox(strPrompt, "Seek Example")))  
             ' Quit if strID is a zero-length string (CANCEL, null, etc.)  
             If Len(strID) = 0 Then Exit Do  
             If Len(strID) = 1 And strID >= "1" And strID <= "9" Then  
                rstEmployees.Seek Array(strID), adSeekFirstEQ  
                If rstEmployees.EOF Then  
                   Debug.Print "Employee not found.", , "Seek Example"  
                   MsgBox "Employee not found."  
                Else  
                   Debug.Print strID; ": Employee='"; rstEmployees!FirstName; " "; _  
                      rstEmployees!LastName; "'"  
                   MsgBox "EmployeeID is: " + strID + "; Employee Name is: '" + rstEmployees!FirstName + " " + _  
                      rstEmployees!LastName + "'", , "Seek Example"  
                End If  
             Else  
                MsgBox "You entered a wrong EmployeeID, please enter a new ID."  
             End If  
          Loop  
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
'EndSeekVB  
```  
  
## <a name="see-also"></a>请参阅  
 [索引属性](../../../ado/reference/ado-api/index-property.md)   
 [记录集对象 (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)   
 [Seek 方法](../../../ado/reference/ado-api/seek-method.md)
