---
title: DeleteRecord 和 MoveRecord 方法示例 (VB) |Microsoft Docs
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
- MoveRecord method [ADO], Visual Basic example
- DeleteRecord method [ADO], Visual Basic example
ms.assetid: c3937d1e-9872-47e5-a22e-b147637f2388
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 08e201db8406354662948e4da3d2047746780eba
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "66695367"
---
# <a name="deleterecord-and-moverecord-methods-example-vb"></a>DeleteRecord 和 MoveRecord 方法示例 (VB)
此示例演示如何复制、 移动、 编辑和删除文本文件发布到 Web 文件夹的内容。 其他属性和方法使用包括[GetChildren](../../../ado/reference/ado-api/getchildren-method-ado.md)， [ParentURL](../../../ado/reference/ado-api/parenturl-property-ado.md)，[源](../../../ado/reference/ado-api/source-property-ado-record.md)，以及[刷新](../../../ado/reference/ado-api/flush-method-ado.md)。  
  
```  
'BeginDeleteRecordVB  
  
'Note:  
' IIS must be running for this sample to work. To  
' use this sample you must:  
'  
' 1. create folders named "test" and "test2"  
'    in the root web folder of https://MyServer  
'  
' 2. Create a text file named "test2.txt" in the  
'    "test" folder.  
' 3. Replace "MyServer" with the appropriate web  
'    server name.  
  
Public Sub Main()  
    On Error GoTo ErrorHandler  
  
     ' connection and recordset variables  
    Dim rsDestFolder As ADODB.Recordset  
    Dim Cnxn As ADODB.Connection  
    Dim strCnxn As String  
  
     ' file as record variables  
    Dim rcFile As ADODB.Record  
    Dim rcDestFile As ADODB.Record  
    Dim rcDestFolder As ADODB.Record  
    Dim objStream As Stream  
  
     ' file variables  
    Dim strFile As String  
    Dim strDestFile As String  
    Dim strDestFolder As String  
  
     ' instantiate variables  
    Set rsDestFolder = New ADODB.Recordset  
    Set rcDestFolder = New ADODB.Record  
    Set rcFile = New ADODB.Record  
    Set rcDestFile = New ADODB.Record  
    Set objStream = New ADODB.Stream  
  
     ' open a record on a text file  
    Set Cnxn = New ADODB.Connection  
    strCnxn = "url=https://MyServer/"  
    Cnxn.Open strCnxn  
    strFile = "test/test2.txt"  
    rcFile.Open strFile, Cnxn, adModeReadWrite, adOpenIfExists Or adCreateNonCollection  
    Debug.Print Cnxn  
  
     ' edit the contents of the text file  
    objStream.Open rcFile, , adOpenStreamFromRecord  
  
    Debug.Print "Source: " & strCnxn & rcFile.Source  
    Debug.Print "Original text: " & objStream.ReadText  
  
    objStream.Position = 0  
    objStream.WriteText "Newer Text. "  
    objStream.Position = 0  
  
    Debug.Print "New text: " & objStream.ReadText  
  
     ' reset the stream object  
    objStream.Flush  
    objStream.Close  
    rcFile.Close  
  
     ' reopen record to see new contents of text file  
    rcFile.Open strFile, Cnxn, adModeReadWrite, adOpenIfExists Or adCreateNonCollection  
    objStream.Open rcFile, adModeReadWrite, adOpenStreamFromRecord  
  
    Debug.Print "Source: " & strCnxn & rcFile.Source  
    Debug.Print "Edited text: " & objStream.ReadText  
  
     ' copy the file to another folder  
    strDestFile = "test2/test1.txt"  
    rcFile.CopyRecord "", "https://MyServer/" & strDestFile, "", "", adCopyOverWrite  
  
     ' delete the original file  
    rcFile.DeleteRecord  
  
     ' move the file from the subfolder back to original location  
    strDestFolder = "test2/"  
    rcDestFolder.Open strDestFolder, Cnxn ', adOpenIfExists  'Or adCreateCollection  
    Set rsDestFolder = rcDestFolder.GetChildren  
    rsDestFolder.MoveFirst  
  
     ' position current record at on the correct file  
    Do While Not (rsDestFolder.EOF Or rsDestFolder(0) = "test1.txt")  
        rsDestFolder.MoveNext  
    Loop  
  
     ' open a record on the correct row of the recordset  
    rcDestFile.Open rsDestFolder, Cnxn  
  
     ' do the move  
    rcDestFile.MoveRecord "", "https://MyServer/" & strFile, "", "", adMoveOverWrite  
  
    ' clean up  
    rsDestFolder.Close  
    Cnxn.Close  
    Set rsDestFolder = Nothing  
    Set Cnxn = Nothing  
    Exit Sub  
  
ErrorHandler:  
    ' clean up  
    If Not rsDestFolder Is Nothing Then  
        If rsDestFolder.State = adStateOpen Then rsDestFolder.Close  
    End If  
    Set rsDestFolder = Nothing  
  
    If Not Cnxn Is Nothing Then  
        If Cnxn.State = adStateOpen Then Cnxn.Close  
    End If  
    Set Cnxn = Nothing  
  
    If Err <> 0 Then  
        MsgBox Err.Source & "-->" & Err.Description, , "Error"  
    End If  
End Sub  
'EndDeleteRecordVB  
```  
  
## <a name="see-also"></a>请参阅  
 [DeleteRecord 方法 (ADO)](../../../ado/reference/ado-api/deleterecord-method-ado.md)   
 [Flush 方法 (ADO)](../../../ado/reference/ado-api/flush-method-ado.md)   
 [GetChildren 方法 (ADO)](../../../ado/reference/ado-api/getchildren-method-ado.md)   
 [MoveRecord 方法 (ADO)](../../../ado/reference/ado-api/moverecord-method-ado.md)   
 [ParentURL 属性 (ADO)](../../../ado/reference/ado-api/parenturl-property-ado.md)   
 [Source 属性（ADO 记录）](../../../ado/reference/ado-api/source-property-ado-record.md)
