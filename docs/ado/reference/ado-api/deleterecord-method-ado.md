---
title: DeleteRecord 方法 (ADO) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Record::raw_DeleteRecord
- _Record::DeleteRecord
helpviewer_keywords:
- DeleteRecord method [ADO]
ms.assetid: 2726498c-dbd8-4266-983b-ae7d62c39142
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: f67f074596bfcf93eb7017a7afe273285f721aae
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "66695333"
---
# <a name="deleterecord-method-ado"></a>DeleteRecord 方法 (ADO)
删除所表示的实体[记录](../../../ado/reference/ado-api/record-object-ado.md)。  
  
## <a name="syntax"></a>语法  
  
```  
  
Record.DeleteRecord Source, Async  
```  
  
#### <a name="parameters"></a>Parameters  
 *数据源*  
 可选。 一个**字符串**值，该值包含要删除的 URL 标识的实体 （例如，文件或目录）。 如果*源*省略或指定了空字符串，表示由当前的实体[记录](../../../ado/reference/ado-api/record-object-ado.md)被删除。 如果记录是集合记录 ([RecordType](../../../ado/reference/ado-api/recordtype-property-ado.md)的**adCollectionRecord**，例如目录) 也将删除所有子项 （例如，子目录）。  
  
 *Async*  
 可选。 一个**布尔**值，当**True**，指定删除操作是异步。  
  
## <a name="remarks"></a>备注  
 表示此对象上的操作**记录**此方法完成后可能会失败。 在调用**DeleteRecord**，则**记录**应关闭，因为的行为**记录**可能会变得不可预知根据提供程序的更新时**记录**与数据源。  
  
 如果此**记录**来自[记录集](../../../ado/reference/ado-api/recordset-object-ado.md)，则此操作的结果将不会立即反映到**记录集**。 刷新**记录集**通过关闭并重新打开它，或通过执行**记录集**[再次查询](../../../ado/reference/ado-api/requery-method.md)方法，[更新](../../../ado/reference/ado-api/update-method.md)方法，或[重新同步](../../../ado/reference/ado-api/resync-method.md)方法。  
  
> [!NOTE]
>  Url 使用 http 方案将自动调用[Microsoft OLE DB 访问接口用于 Internet 发布](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md)。 有关详细信息，请参阅[绝对和相对 Url](../../../ado/guide/data/absolute-and-relative-urls.md)。  
  
## <a name="applies-to"></a>适用范围  
 [记录对象 (ADO)](../../../ado/reference/ado-api/record-object-ado.md)  
  
## <a name="see-also"></a>请参阅  
 [Delete 方法 （ADO 字段集合）](../../../ado/reference/ado-api/delete-method-ado-fields-collection.md)   
 [Delete 方法 （ADO 参数集合）](../../../ado/reference/ado-api/delete-method-ado-parameters-collection.md)   
 [Delete 方法（ADO 记录集）](../../../ado/reference/ado-api/delete-method-ado-recordset.md)
