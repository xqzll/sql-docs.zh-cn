---
title: 视图集合、 CommandText 属性示例 (VB) |Microsoft Docs
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
- CommandText property [ADOX]
- Views collection [ADOX], Visual Basic example
ms.assetid: a05a0190-352d-44ff-9488-0c94e9fb656e
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 01ddcb116c4253c2ab56548af2b9cf136b9e28de
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "66697217"
---
# <a name="views-collection-commandtext-property-example-vb"></a>视图集合、CommandText 属性示例 (VB)
下面的代码演示如何使用[命令](../../../ado/reference/adox-api/command-property-adox.md)属性更新视图的文本。  
  
```  
' BeginViewsCollectionVB  
Sub Main()  
    On Error GoTo ViewTextError  
  
    Dim cnn As New ADODB.Connection  
    Dim cat As New ADOX.Catalog  
    Dim cmd As New ADODB.Command  
  
    ' Open the connection.  
    cnn.Open _  
        "Provider='Microsoft.Jet.OLEDB.4.0';" & _  
        "Data Source='Northwind.mdb';"  
  
    ' Open the catalog.  
    Set cat.ActiveConnection = cnn  
  
    ' Get the command.  
    Set cmd = cat.Views("AllCustomers").Command  
  
    ' Update the CommandText of the command.  
    cmd.CommandText = _  
    "Select CustomerId, CompanyName, ContactName From Customers"  
  
    ' Update the view.  
    Set cat.Views("AllCustomers").Command = cmd  
  
    'Clean up.  
    cnn.Close  
    Set cat = Nothing  
    Set cmd = Nothing  
    Set cnn = Nothing  
    Exit Sub  
  
ViewTextError:  
  
    Set cat = Nothing  
    Set cmd = Nothing  
  
    If Not cnn Is Nothing Then  
        If cnn.State = adStateOpen Then cnn.Close  
    End If  
    Set cnn = Nothing  
  
    If Err <> 0 Then  
        MsgBox Err.Source & "-->" & Err.Description, , "Error"  
    End If  
End Sub  
' EndViewsCollectionVB  
```  
  
## <a name="see-also"></a>请参阅  
 [ActiveConnection 属性 (ADOX)](../../../ado/reference/adox-api/activeconnection-property-adox.md)   
 [目录对象 (ADOX)](../../../ado/reference/adox-api/catalog-object-adox.md)   
 [Command 属性 (ADOX)](../../../ado/reference/adox-api/command-property-adox.md)   
 [视图对象 (ADOX)](../../../ado/reference/adox-api/view-object-adox.md)   
 [视图集合 (ADOX)](../../../ado/reference/adox-api/views-collection-adox.md)
