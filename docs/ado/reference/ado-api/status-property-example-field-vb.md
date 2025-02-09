---
title: Status 属性示例 （字段） (VB) |Microsoft Docs
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
- Status property [ADO Field], Visual Basic example
ms.assetid: fdd09b60-39c7-44be-8008-e891a031f80e
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 12ae39b965678a47053d3d312c750f7bd87bd7d1
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "66719051"
---
# <a name="status-property-example-field-vb"></a>Status 属性示例（字段）(VB)
下面的示例从读/写文件夹使用打开文档[发布的 Internet 提供商](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md)。 [状态](../../../ado/reference/ado-api/status-property-ado-field.md)的属性[字段](../../../ado/reference/ado-api/field-object.md)的对象[记录](../../../ado/reference/ado-api/record-object-ado.md)首先将设置为**adFieldPendingInsert**，则更新为**adFieldOk**。  
  
```  
'BeginStatusFieldVB  
  
 ' to integrate this code replace the values in the source string  
  
Sub Main()  
  
   Dim File As ADODB.Record  
   Dim strFile As String  
   Dim Cnxn As ADODB.Connection  
   Dim strCnxn As String  
  
   Set Cnxn = New ADODB.Connection  
   strCnxn = "url=https://MyServer/"  
   Cnxn.Open strCnxn  
  
   Set File = New ADODB.Record  
   strFile = "Folder/FileName"  
   ' Open a read/write document  
   File.Source = strFile  
   File.ActiveConnection = Cnxn  
   File.Mode = adModeReadWrite  
   File.Open  
  
   Debug.Print "Append a couple of fields"  
  
   File.Fields.Append "chektest:fld1", adWChar, 42, adFldUpdatable, "fld1"  
   File.Fields.Append "chektest:fld2", adWChar, 42, adFldUpdatable, "fld2"  
  
   Debug.Print "status for the fields"  
   Debug.Print File.Fields("chektest:fld1").Status 'adfldpendinginsert  
   Debug.Print File.Fields("chektest:fld2").Status 'adfldpendinginsert  
  
    'turn off error-handling to verify field status  
   On Error Resume Next  
  
   File.Fields.Update  
  
   Debug.Print "Update succeeds"  
   Debug.Print File.Fields("chektest:fld1").Status 'adfldpendinginsert + adFieldUnavailable  
   Debug.Print File.Fields("chektest:fld2").Status 'adfldpendinginsert + adFieldUnavailable  
  
    ' resume default error-handling  
   On Error GoTo 0  
  
     ' clean up  
    File.Close  
    Cnxn.Close  
    Set File = Nothing  
    Set Cnxn = Nothing  
  
End Sub  
'EndStatusFieldVB  
```  
  
 以下示例删除一个已知**字段**从**记录**从文档打开。 **状态**首先将属性设置为**adFieldOK**，然后**adFieldPendingUnknown**。  
  
```  
Attribute VB_Name = "StatusField"  
```  
  
 下面的代码删除**字段**从**记录**上只读的文档打开。 **状态**将设置为**adFieldPendingDelete**。 在[更新](../../../ado/reference/ado-api/update-method.md)，删除将失败并**状态**将是**adFieldPendingDelete**加上**adFieldPermissionDenied**。 [CancelUpdate](../../../ado/reference/ado-api/cancelupdate-method-ado.md)清除挂起**状态**设置。  
  
```  
Attribute VB_Name = "StatusField"  
```  
  
## <a name="see-also"></a>请参阅  
 [字段对象](../../../ado/reference/ado-api/field-object.md)   
 [记录对象 (ADO)](../../../ado/reference/ado-api/record-object-ado.md)   
 [Status 属性（ADO 字段）](../../../ado/reference/ado-api/status-property-ado-field.md)
