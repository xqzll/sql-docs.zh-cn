---
title: 值属性示例 (VB) |Microsoft Docs
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
- Value property [ADO], Visual Basic example
ms.assetid: 2d4fe651-ef09-461b-8884-a70b6af4362e
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: db0fd5dca7768e5e75664c1247d916d27766bb9b
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "66710291"
---
# <a name="value-property-example-vb"></a>Value 属性示例 (VB)
此示例演示[值](../../../ado/reference/ado-api/value-property-ado.md)具有属性[字段](../../../ado/reference/ado-api/field-object.md)并[属性](../../../ado/reference/ado-api/property-object-ado.md)按显示字段和属性值的对象的***员工***表。  
  
```  
'BeginValueVB  
Public Sub Main()  
    On Error GoTo ErrorHandler  
  
    'To integrate this code  
    'replace the data source and initial catalog values  
    'in the connection string  
  
    ' connection and recordset variables  
    Dim rstEmployees As ADODB.Recordset  
    Dim Cnxn As ADODB.Connection  
    Dim strCnxn As String  
    Dim strSQLEmployees As String  
     ' field property variables  
    Dim fld As ADODB.Field  
    Dim prp As ADODB.Property  
  
     ' Open connection  
    Set Cnxn = New ADODB.Connection  
    strCnxn = "Provider='sqloledb';Data Source='MySqlServer';" & _  
        "Initial Catalog='Pubs';Integrated Security='SSPI';"  
    Cnxn.Open strCnxn  
  
    ' Open recordset with data from Employees table  
    Set rstEmployees = New ADODB.Recordset  
    strSQLEmployees = "employee"  
    rstEmployees.Open strSQLEmployees, Cnxn, , , adCmdTable  
    'rstEmployees.Open strSQLEmployees, Cnxn, adOpenStatic, adLockReadOnly, adCmdTable  
    ' the above two lines of code are identical  
  
    Debug.Print "Field values in rstEmployees"  
  
    ' Enumerate the Fields collection of the Employees table  
    For Each fld In rstEmployees.Fields  
        ' Because Value is the default property of a  
        ' Field object, the use of the actual keyword  
        ' here is optional.  
        Debug.Print "   " & fld.Name & " = " & fld.Value  
    Next fld  
  
    Debug.Print "Property values in rstEmployees"  
  
    ' Enumerate the Properties collection of the Recordset object  
    For Each prp In rstEmployees.Properties  
        Debug.Print "   " & prp.Name & " = " & prp.Value  
        ' because Value is the default property of a Property object  
        ' use of the actual Value keyword is optional  
    Next prp  
  
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
'EndValueVB  
```  
  
## <a name="see-also"></a>请参阅  
 [字段对象](../../../ado/reference/ado-api/field-object.md)   
 [属性对象 (ADO)](../../../ado/reference/ado-api/property-object-ado.md)   
 [Value 属性 (ADO)](../../../ado/reference/ado-api/value-property-ado.md)
