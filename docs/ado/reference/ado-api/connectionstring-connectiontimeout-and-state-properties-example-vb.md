---
title: 连接属性示例 (VB) |Microsoft Docs
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
- ConnectionString property [ADO], Visual Basic example
- ConnectionTimeout property [ADO], Visual Basic example
- State property [ADO], Visual Basic example
ms.assetid: 4de7336a-b5ea-43f1-b750-5fa302b5b756
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: f80b2f49b31a3eb175f0f5c613bba11d67c50365
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "66695735"
---
# <a name="connectionstring-connectiontimeout-and-state-properties-example-vb"></a>ConnectionString、 ConnectionTimeout 和 State 属性示例 (VB)
此示例演示使用的不同方式[ConnectionString](../../../ado/reference/ado-api/connectionstring-property-ado.md)以打开[连接](../../../ado/reference/ado-api/connection-object-ado.md)对象。 它还使用[ConnectionTimeout](../../../ado/reference/ado-api/connectiontimeout-property-ado.md)属性来设置连接超时期限，并且[状态](../../../ado/reference/ado-api/state-property-ado.md)属性来检查连接状态。 若要运行此过程需要 GetState 函数。  
  
> [!NOTE]
>  如果您要连接到的数据源提供程序支持 Windows 身份验证，则应指定**Trusted_Connection = yes**或**Integrated Security = SSPI**而不是用户 ID 和密码在连接字符串中的信息。  
  
```  
'BeginConnectionStringVB  
  
    'To integrate this code replace  
    'the database, DSN or Data Source values  
  
Public Sub Main()  
    On Error GoTo ErrorHandler  
  
    Dim Cnxn1 As ADODB.Connection  
    Dim Cnxn2 As ADODB.Connection  
    Dim Cnxn3 As ADODB.Connection  
    Dim Cnxn4 As ADODB.Connection  
  
     ' Open a connection without using a Data Source Name (DSN)  
    Set Cnxn1 = New ADODB.Connection  
    Cnxn1.ConnectionString = "Provider='sqloledb';Data Source='MySqlServer';" & _  
        "Initial Catalog='Pubs';Integrated Security='SSPI';"  
    Cnxn1.Open  
    MsgBox "Cnxn1 state: " & GetState(Cnxn1.State)  
  
     ' Open a connection using a DSN and ODBC tags  
     ' It is assumed that you have created DSN 'Pubs' with a user name as  
     ' 'MyUserId' and password as 'MyPassword'.  
    Set Cnxn2 = New ADODB.Connection  
    Cnxn2.ConnectionString = "Data Source='Pubs';" & _  
        "User ID='MyUserId';Password='MyPassword';"  
    Cnxn2.ConnectionTimeout = 30  
    Cnxn2.Open  
    MsgBox "Cnxn2 state: " & GetState(Cnxn2.State)  
  
     ' Open a connection using a DSN and OLE DB tags  
     ' It is assumed that you have created DSN 'Pubs1' with windows authentication.  
    Set Cnxn3 = New ADODB.Connection  
    Cnxn3.ConnectionString = "Data Source='Pubs1';"  
    Cnxn3.Open  
    MsgBox "Cnxn2 state: " & GetState(Cnxn3.State)  
  
     ' Open a connection using a DSN and individual  
     ' arguments instead of a connection string  
     ' It is assumed that you have created DSN 'Pubs' with a user name as  
     ' 'MyUserId' and password as 'MyPassword'.  
    Set Cnxn4 = New ADODB.Connection  
    Cnxn4.Open "Pubs", "MyUserId", "MyPassword"  
    MsgBox "Cnxn4 state: " & GetState(Cnxn4.State)  
  
    ' clean up  
    Cnxn1.Close  
    Cnxn2.Close  
    Cnxn3.Close  
    Cnxn4.Close  
    Set Cnxn1 = Nothing  
    Set Cnxn2 = Nothing  
    Set Cnxn3 = Nothing  
    Set Cnxn4 = Nothing  
    Exit Sub  
  
ErrorHandler:  
    ' clean up  
    If Not Cnxn1 Is Nothing Then  
        If Cnxn1.State = adStateOpen Then Cnxn1.Close  
    End If  
    Set Cnxn1 = Nothing  
  
    If Not Cnxn2 Is Nothing Then  
        If Cnxn2.State = adStateOpen Then Cnxn2.Close  
    End If  
    Set Cnxn2 = Nothing  
  
    If Not Cnxn3 Is Nothing Then  
        If Cnxn3.State = adStateOpen Then Cnxn3.Close  
    End If  
    Set Cnxn3 = Nothing  
  
    If Not Cnxn4 Is Nothing Then  
        If Cnxn4.State = adStateOpen Then Cnxn4.Close  
    End If  
    Set Cnxn4 = Nothing  
  
    If Err <> 0 Then  
        MsgBox Err.Source & "-->" & Err.Description, , "Error"  
    End If  
End Sub  
  
Public Function GetState(intState As Integer) As String  
  
   Select Case intState  
      Case adStateClosed  
         GetState = "adStateClosed"  
      Case adStateOpen  
         GetState = "adStateOpen"  
   End Select  
  
End Function  
'EndConnectionStringVB  
```  
  
## <a name="see-also"></a>请参阅  
 [连接对象 (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)   
 [ConnectionString 属性 (ADO)](../../../ado/reference/ado-api/connectionstring-property-ado.md)   
 [ConnectionTimeout 属性 (ADO)](../../../ado/reference/ado-api/connectiontimeout-property-ado.md)   
 [State 属性 (ADO)](../../../ado/reference/ado-api/state-property-ado.md)
