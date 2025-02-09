---
title: AddNew 方法 (ADO) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::AddNew
- Recordset15::raw_AddNew
helpviewer_keywords:
- AddNew method [ADO]
ms.assetid: a9f54be9-5763-45d0-a6eb-09981b03bc08
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: da8ef8208ae3edd1219eb81ec93e77ba5a275f87
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "66704226"
---
# <a name="addnew-method-ado"></a>AddNew 方法 (ADO)
创建可更新的新记录[记录集](../../../ado/reference/ado-api/recordset-object-ado.md)对象。  
  
## <a name="syntax"></a>语法  
  
```  
  
recordset.AddNew FieldList, Values  
```  
  
#### <a name="parameters"></a>Parameters  
 *recordset*  
 一个**记录集**对象。  
  
 *字段列表*  
 可选。 单个名称或名称的数组或新记录中字段的序号位置。  
  
 *值*  
 可选。 单个值，则新记录中字段的值为数组。 如果*Fieldlist*是一个数组*值*必须也是一个数组具有相同成员的数目; 否则为就会出错。 字段名称的顺序必须与匹配的每个数组中的字段值的顺序。  
  
## <a name="remarks"></a>备注  
 使用**AddNew**方法来创建和初始化一个新的记录。 使用[支持](../../../ado/reference/ado-api/supports-method.md)方法替换**adAddNew** ( [CursorOptionEnum](../../../ado/reference/ado-api/cursoroptionenum.md)值) 以验证是否可以将记录添加到当前**记录集**对象。  
  
 调用后**AddNew**方法，新的记录将成为当前记录，并保持最新调用后[更新](../../../ado/reference/ado-api/update-method.md)方法。 由于新记录追加到**记录集**，调用**MoveNext**以下更新将移至末尾**记录集**，这会让**EOF** ，则返回 true。 如果**记录集**对象不支持书签，您可能不能访问新记录后，移动到另一条记录。 具体取决于游标类型，您可能需要调用[再次查询](../../../ado/reference/ado-api/requery-method.md)方法，以便可以访问新的记录。  
  
 如果您调用**AddNew** ADO 编辑当前记录或添加新记录时，调用**更新**方法以保存任何更改，然后创建新记录。  
  
 行为**AddNew**上的更新模式的方法取决于**记录集**对象和是否传递*Fieldlist*和*值*自变量。  
  
 在中*立即更新模式*(在其中提供程序将更改写入到基础数据源后，调用**更新**方法)，则调用**AddNew**没有方法参数集[EditMode](../../../ado/reference/ado-api/editmode-property.md)属性设置为**adEditAdd** ( [EditModeEnum](../../../ado/reference/ado-api/editmodeenum.md)值)。 提供程序将任何字段值更改在本地缓存。 调用**更新**方法将发布到数据库的新记录，并将重置**EditMode**属性设置为**adEditNone** ( **EditModeEnum**值)。 如果传递*Fieldlist*并*值*自变量，ADO 立即发布到数据库的新记录 (没有**更新**才需要调用); **EditMode**属性值不会更改 (**adEditNone**)。  
  
 在中*批更新模式*(提供程序将多个更改缓存并将其写入到基础数据源仅在调用[UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md)方法)，则调用**AddNew**方法，而参数集**EditMode**属性设置为**adEditAdd**。 提供程序将任何字段值更改在本地缓存。 调用**更新**方法将新记录添加到当前**记录集**，但该提供程序不会将更改发布到基础数据库，或重置**EditMode**向**adEditNone**，直到您调用**UpdateBatch**方法。 如果传递*Fieldlist*并*值*参数，则 ADO 会将新记录发送到缓存和集中存储的提供程序**EditMode**到**adEditAdd**; 你需要调用**UpdateBatch**方法以发布到基础数据库的新记录。  
  
## <a name="example"></a>示例  
 下面的示例演示如何使用 AddNew 方法与字段列表和值列表中包括，若要了解如何为数组中包括的字段列表和值列表。  
  
```  
create table aa1 (intf int, charf char(10))  
insert into aa1 values (2, 'aa')  
  
Dim cn As New adodb.Connection  
Dim rs As New adodb.Recordset  
Dim cmd As New adodb.Command  
  
cn.ConnectionString = "Provider=SQLOLEDB;Data Source=alexverb2;uid=sa;pwd=foo$bar00;"  
  
cn.Open  
rs.Open "select * from xxx..aa1", cn, adOpenKeyset, adLockOptimistic  
  
Dim fieldsArray(1) As Variant  
fieldsArray(0) = "intf"  
fieldsArray(1) = "charf"  
Dim values(1) As Variant  
values(0) = 4  
values(1) = "as"  
rs.AddNew fieldsArray, values  
rs.Update  
```  
  
## <a name="applies-to"></a>适用范围  
 [记录集对象 (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>请参阅  
 [AddNew 方法示例 (VB)](../../../ado/reference/ado-api/addnew-method-example-vb.md)   
 [AddNew 方法示例 (VBScript)](../../../ado/reference/ado-api/addnew-method-example-vbscript.md)   
 [AddNew 方法示例 （VC + +）](../../../ado/reference/ado-api/addnew-method-example-vc.md)   
 [CancelUpdate 方法 (ADO)](../../../ado/reference/ado-api/cancelupdate-method-ado.md)   
 [EditMode 属性](../../../ado/reference/ado-api/editmode-property.md)   
 [Requery 方法](../../../ado/reference/ado-api/requery-method.md)   
 [支持方法](../../../ado/reference/ado-api/supports-method.md)   
 [更新方法](../../../ado/reference/ado-api/update-method.md)   
 [UpdateBatch 方法](../../../ado/reference/ado-api/updatebatch-method.md)
