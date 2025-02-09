---
title: 字段对象 |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Field
helpviewer_keywords:
- Field object [ADO]
ms.assetid: b10a72fc-3c4b-4186-a70b-993dc9f7a092
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 9b57ce165337dc2cef87daf8c2a835bde0c5f85b
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "66697853"
---
# <a name="field-object"></a>字段对象
表示与常见的数据类型的数据的列。  
  
## <a name="remarks"></a>备注  
 每个**字段**对象中的列对应[记录集](../../../ado/reference/ado-api/recordset-object-ado.md)。 您使用[值](../../../ado/reference/ado-api/value-property-ado.md)的属性**字段**对象设置或返回当前记录的数据。 根据的功能提供程序用于公开，一些集合、 方法或属性的**字段**对象可能不可用。  
  
 使用集合、 方法和属性的**字段**对象，您可以执行以下操作：  
  
-   返回与字段的名称[名称](../../../ado/reference/ado-api/name-property-ado.md)属性。  
  
-   查看或更改与字段中的数据**值**属性。 **值**是默认属性**字段**对象。  
  
-   返回的字段的基本特征[类型](../../../ado/reference/ado-api/type-property-ado.md)，[精度](../../../ado/reference/ado-api/precision-property-ado.md)，并[NumericScale](../../../ado/reference/ado-api/numericscale-property-ado.md)属性。  
  
-   返回具有字段的声明的大小[DefinedSize](../../../ado/reference/ado-api/definedsize-property.md)属性。  
  
-   返回与给定字段中的数据的实际大小[ActualSize](../../../ado/reference/ado-api/actualsize-property-ado.md)属性。  
  
-   确定与给定字段的支持哪些类型的功能[特性](../../../ado/reference/ado-api/attributes-property-ado.md)属性和[属性](../../../ado/reference/ado-api/properties-collection-ado.md)集合。  
  
-   操作包含使用长度的二进制或长字符数据字段的值[AppendChunk](../../../ado/reference/ado-api/appendchunk-method-ado.md)并[GetChunk](../../../ado/reference/ado-api/getchunk-method-ado.md)方法。  
  
-   如果提供程序支持批量更新，解决字段值中的差异在批更新与期间[OriginalValue](../../../ado/reference/ado-api/originalvalue-property-ado.md)并[UnderlyingValue](../../../ado/reference/ado-api/underlyingvalue-property.md)属性。  
  
 所有元数据属性 (**名称**，**类型**， **DefinedSize**，**精度**，和**NumericScale**) 可打开之前**字段**对象的**记录集**。 将它们设置在该时间可用于动态构建窗体。  
  
 本部分包含以下主题。  
  
-   [字段对象属性、 方法和事件](../../../ado/reference/ado-api/field-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>请参阅  
 [字段集合 (ADO)](../../../ado/reference/ado-api/fields-collection-ado.md)   
 [属性集合 (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)   
 [记录集对象 (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)
