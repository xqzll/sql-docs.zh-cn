---
title: 项属性 (ADO) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Parameters::GetItem
- Indexes::GetItem
- Parameters::Item
- Tables::Item
- Procedures::Item
- Users::GetItem
- Tables::GetItem
- Procedures::GetItem
- Users::get_Item
- Users::Item
- Views::GetItem
- Groups::Item
- Groups::get_Item
- Columns::Item
- Indexes::Item
- Fields15::GetItem
- Columns::GetItem
- Fields::Item
- Indexes::get_Item
- Columns::get_Item
- Fields15::Item
- Views::get_Item
- Groups::GetItem
- Errors::get_Item
- Fields15::get_Item
- Tables::get_Item
- Views::Item
- Errors::GetItem
- Parameters::get_Item
- Errors::Item
- Procedures::get_Item
helpviewer_keywords:
- Item property [ADO]
ms.assetid: e11484bb-c5c7-42d8-9bb8-21572125d727
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 6be26e9c174c1911a0c2c7210552c8e8a0e44a2c
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "66697566"
---
# <a name="item-property-ado"></a>Item 属性 (ADO)
指示集合中的特定成员按名称或序号。  
  
## <a name="syntax"></a>语法  
  
```  
Set object = collection.Item ( Index )  
```  
  
## <a name="return-value"></a>返回值  
 返回的对象引用。  
  
## <a name="parameters"></a>Parameters  
 *Index*  
 一个**变体**表达式的计算结果为名称或集合中的对象的初始数字。  
  
## <a name="remarks"></a>备注  
 使用**项**属性以返回特定对象在集合中。 如果**项**对应的集合中找不到对象*索引*参数，就会出错。 另外，某些集合不支持命名的对象;对于这些集合，必须使用序号引用。  
  
 **项**属性是所有集合的默认属性; 因此，以下语法形式是可互换的：  
  
```  
collection.Item (Index)  
collection (Index)  
```  
  
## <a name="applies-to"></a>适用范围  
  
||||  
|-|-|-|  
|[轴集合 (ADO MD)](../../../ado/reference/ado-md-api/axes-collection-ado-md.md)|[列集合 (ADOX)](../../../ado/reference/adox-api/columns-collection-adox.md)|[CubeDefs 集合 (ADO MD)](../../../ado/reference/ado-md-api/cubedefs-collection-ado-md.md)|  
|[维度集合 (ADO MD)](../../../ado/reference/ado-md-api/dimensions-collection-ado-md.md)|[错误集合 (ADO)](../../../ado/reference/ado-api/errors-collection-ado.md)|[字段集合 (ADO)](../../../ado/reference/ado-api/fields-collection-ado.md)|  
|[组集合 (ADOX)](../../../ado/reference/adox-api/groups-collection-adox.md)|[层次结构集合 (ADO MD)](../../../ado/reference/ado-md-api/hierarchies-collection-ado-md.md)|[索引集合 (ADOX)](../../../ado/reference/adox-api/indexes-collection-adox.md)|  
|[项集合 (ADOX)](../../../ado/reference/adox-api/keys-collection-adox.md)|[级别集合 (ADO MD)](../../../ado/reference/ado-md-api/levels-collection-ado-md.md)|[成员集合 (ADO MD)](../../../ado/reference/ado-md-api/members-collection-ado-md.md)|  
|[参数集合 (ADO)](../../../ado/reference/ado-api/parameters-collection-ado.md)|[位置集合 (ADO MD)](../../../ado/reference/ado-md-api/positions-collection-ado-md.md)|[过程集合 (ADOX)](../../../ado/reference/adox-api/procedures-collection-adox.md)|  
|[属性集合 (ADO)](../../../ado/reference/ado-api/properties-collection-ado.md)|[表集合 (ADOX)](../../../ado/reference/adox-api/tables-collection-adox.md)|[用户集合 (ADOX)](../../../ado/reference/adox-api/users-collection-adox.md)|  
|[视图集合 (ADOX)](../../../ado/reference/adox-api/views-collection-adox.md)|||  
  
## <a name="see-also"></a>请参阅  
 [Item 属性示例 (VB)](../../../ado/reference/ado-api/item-property-example-vb.md)   
 [Item 属性示例 (VC++)](../../../ado/reference/ado-api/item-property-example-vc.md)   
