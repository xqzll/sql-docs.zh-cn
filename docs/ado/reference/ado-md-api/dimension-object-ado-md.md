---
title: 维度对象 (ADO MD) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Dimension
helpviewer_keywords:
- Dimension object [ADO MD]
ms.assetid: 66adbbd2-23a3-4c19-a91b-84c31309aa1b
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: f69acfa84272e73bcafb370eb85c6a14614a367c
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "66709432"
---
# <a name="dimension-object-ado-md"></a>维度对象 (ADO MD)
表示多维数据集，其中包含一个或多个层次结构的成员的维度之一。  
  
## <a name="remarks"></a>备注  
 使用集合和属性的**维度**对象，您可以执行以下操作：  
  
-   识别**维度**与[名称](../../../ado/reference/ado-md-api/name-property-ado-md.md)并[UniqueName](../../../ado/reference/ado-md-api/uniquename-property-ado-md.md)属性。  
  
-   返回一个有意义的字符串，描述**维度**与[说明](../../../ado/reference/ado-md-api/description-property-ado-md.md)属性。  
  
-   返回[层次结构](../../../ado/reference/ado-md-api/hierarchy-object-ado-md.md)构成对象**维度**与[层次结构](../../../ado/reference/ado-md-api/hierarchies-collection-ado-md.md)集合。  
  
-   使用标准的 ADO[属性](../../../ado/reference/ado-api/properties-collection-ado.md)集合，以获取有关其他信息**维度**对象。  
  
 **属性**集合包含提供程序提供的属性。 下表列出了可能可用的属性。 实际的属性列表可能不同的提供程序实现根据。 请参阅可用属性的更完整的列表为提供程序的文档。  
  
|“属性”|Description|  
|----------|-----------------|  
|CatalogName|此多维数据集所属的目录的名称。|  
|CubeName|多维数据集的名称。|  
|DefaultHierarchy|默认层次结构的唯一名称。|  
|Description|多维数据集的贴切描述。|  
|DimensionCaption|标签或标题与维度相关联。|  
|DimensionCardinality|维度中的成员数。|  
|DimensionGUID|维度的 GUID。|  
|DimensionName|维度的名称。|  
|DimensionOrdinal|在窗体中多维数据集的维度组之间的维度的序号。|  
|DimensionType|维度类型。|  
|DimensionUniqueName|明确的维度的名称。|  
|SchemaName|此多维数据集所属的架构的名称。|  
  
 本部分包含以下主题。  
  
-   [属性、 方法和事件](../../../ado/reference/ado-md-api/dimension-object-properties-methods-and-events.md)  
  
## <a name="see-also"></a>请参阅  
 [CubeDef 示例 (VBScript)](../../../ado/reference/ado-md-api/cubedef-example-vbscript.md)   
 [CubeDef 对象 (ADO MD)](../../../ado/reference/ado-md-api/cubedef-object-ado-md.md)   
 [维度集合 (ADO MD)](../../../ado/reference/ado-md-api/dimensions-collection-ado-md.md)   
 [层次结构集合 (ADO MD)](../../../ado/reference/ado-md-api/hierarchies-collection-ado-md.md)   
 [属性集合 (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)
