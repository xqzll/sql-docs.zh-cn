---
title: 连接的 Close 方法、 表 Type 属性示例 (VB) |Microsoft Docs
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
- Close method [ADOX], Visual Basic example
- Type property [ADOX], Visual Basic example
ms.assetid: f88e7a3b-19ed-46e2-b2ce-3b611d9b8166
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: aa4089925e5a51f5e4fa4578094634e724b8a615
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "66703380"
---
# <a name="connection-close-method-table-type-property-example-vb"></a>连接的 Close 方法、表 Type 属性示例 (VB)
设置[ActiveConnection](../../../ado/reference/adox-api/activeconnection-property-adox.md)属性设置为**Nothing**应关闭连接到目录。 关联的集合将为空。 从目录中的架构对象创建的任何对象都被孤立。 对已缓存这些对象的任何属性仍将可用，但尝试读取属性需要调用提供程序将失败。  
  
```  
' BeginCloseConnectionVB  
Sub Main()  
    On Error GoTo CloseConnectionByNothingError  
  
    Dim cnn As New ADODB.Connection  
    Dim cat As New ADOX.Catalog  
    Dim tbl As ADOX.Table  
  
    cnn.Open "Provider='Microsoft.Jet.OLEDB.4.0';" & _  
        "Data Source= 'Northwind.mdb';"  
    Set cat.ActiveConnection = cnn  
    Set tbl = cat.Tables(0)  
    Debug.Print tbl.Type    ' Cache tbl.Type info  
    Set cat.ActiveConnection = Nothing  
    Debug.Print tbl.Type    ' tbl is orphaned  
    ' Previous line will succeed if this info was cached.  
    Debug.Print tbl.Columns(0).DefinedSize  
    ' Previous line will fail if this info has not been cached.  
  
    'Clean up.  
    cnn.Close  
    Set cat = Nothing  
    Set cnn = Nothing  
    Exit Sub  
  
CloseConnectionByNothingError:  
    Set cat = Nothing  
  
    If Not cnn Is Nothing Then  
        If cnn.State = adStateOpen Then cnn.Close  
    End If  
    Set cnn = Nothing  
  
    If Err <> 0 Then  
        MsgBox Err.Source & "-->" & Err.Description, , "Error"  
    End If  
End Sub  
' EndCloseConnectionVB  
```  
  
 关闭[连接](../../../ado/reference/ado-api/connection-object-ado.md)对象，用于打开该目录应具有相同的效果与设置**ActiveConnection**属性设置为**Nothing**。  
  
```  
Attribute VB_Name = "Connection"  
```  
  
## <a name="see-also"></a>请参阅  
 [ActiveConnection 属性 (ADOX)](../../../ado/reference/adox-api/activeconnection-property-adox.md)   
 [目录对象 (ADOX)](../../../ado/reference/adox-api/catalog-object-adox.md)   
 [列对象 (ADOX)](../../../ado/reference/adox-api/column-object-adox.md)   
 [列集合 (ADOX)](../../../ado/reference/adox-api/columns-collection-adox.md)   
 [表对象 (ADOX)](../../../ado/reference/adox-api/table-object-adox.md)   
 [表集合 (ADOX)](../../../ado/reference/adox-api/tables-collection-adox.md)   
 [Type 属性（表）(ADOX)](../../../ado/reference/adox-api/type-property-table-adox.md)
