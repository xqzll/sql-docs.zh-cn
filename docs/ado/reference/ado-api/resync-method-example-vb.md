---
title: Resync 方法示例 (VB) |Microsoft Docs
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
- Resync method [ADO], Visual Basic example
ms.assetid: ab95315c-fe15-458c-9e0c-937ae5596592
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: d5886c692bd42d4d5c8021a5953de02003044175
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "66719105"
---
# <a name="resync-method-example-vb"></a>Resync 方法示例 (VB)
此示例演示如何使用[重新同步](../../../ado/reference/ado-api/resync-method.md)方法来刷新中静态记录集的数据。  
  
```  
'BeginResyncVB  
  
    'To integrate this code  
    'replace the data source and initial catalog values  
    'in the connection strings  
  
Public Sub Main()  
    On Error GoTo ErrorHandler  
  
    'connection and recordset variables  
    Dim Cnxn As ADODB.Connection  
    Dim rstTitles As ADODB.Recordset  
    Dim strCnxn As String  
    Dim strSQLTitles As String  
  
    ' Open connection  
    Set Cnxn = New ADODB.Connection  
    strCnxn = "Provider='sqloledb';Data Source='MySqlServer';" & _  
        "Initial Catalog='Pubs';Integrated Security='SSPI';"  
    Cnxn.Open strCnxn  
  
    ' Open recordset using object refs to set properties  
    ' that allow for updates to the database  
    Set rstTitles = New ADODB.Recordset  
    Set rstTitles.ActiveConnection = Cnxn  
    rstTitles.CursorType = adOpenKeyset  
    rstTitles.LockType = adLockOptimistic  
  
    strSQLTitles = "titles"  
    rstTitles.Open strSQLTitles  
  
    'rstTitles.Open strSQLTitles, Cnxn, adOpenKeyset, adLockPessimistic, adCmdTable  
    'the above line of code passes the same refs as the object refs listed above  
  
    ' Change the type of the first title in the recordset  
    rstTitles!Type = "database"  
  
    ' Display the results of the change  
    MsgBox "Before resync: " & vbCr & vbCr & _  
        "Title - " & rstTitles!Title & vbCr & _  
        "Type - " & rstTitles!Type  
  
    ' Resync with database and redisplay results  
    rstTitles.Resync  
    MsgBox "After resync: " & vbCr & vbCr & _  
        "Title - " & rstTitles!Title & vbCr & _  
        "Type - " & rstTitles!Type  
  
    ' clean up  
    rstTitles.CancelBatch  
    rstTitles.Close  
    Cnxn.Close  
    Set rstTitles = Nothing  
    Set Cnxn = Nothing  
    Exit Sub  
  
ErrorHandler:  
    ' clean up  
    If Not rstTitles Is Nothing Then  
        If rstTitles.State = adStateOpen Then  
            rstTitles.CancelBatch  
            rstTitles.Close  
        End If  
    End If  
    Set rstTitles = Nothing  
  
    If Not Cnxn Is Nothing Then  
        If Cnxn.State = adStateOpen Then Cnxn.Close  
    End If  
    Set Cnxn = Nothing  
  
    If Err <> 0 Then  
        MsgBox Err.Source & "-->" & Err.Description, , "Error"  
    End If  
End Sub  
'EndResyncVB  
```  
  
## <a name="see-also"></a>请参阅  
 [记录集对象 (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)   
 [重新同步方法](../../../ado/reference/ado-api/resync-method.md)
