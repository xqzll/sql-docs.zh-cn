---
title: InstanceOf（geometry 数据类型）| Microsoft Docs
ms.custom: ''
ms.date: 08/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- InstanceOf
- InstanceOf_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- InstanceOf (geometry Data Type)
ms.assetid: fdea1248-29a4-4bab-a60d-a1b359b5e109
author: MladjoA
ms.author: mlandzic
manager: craigg
ms.openlocfilehash: 82cc52338771862b580c193353db0bb98453b458
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "65939107"
---
# <a name="instanceof-geometry-data-type"></a>InstanceOf（geometry 数据类型）
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

一个方法，用于测试 **geometry** 实例是否与指定的类型相同。 如果 **geometry** 实例的类型与指定类型相同，则返回 1。 如果指定的类型是该实例类型的上级，此方法也返回 1。 否则，此方法返回 0。
  
## <a name="syntax"></a>语法  
  
```  
  
.InstanceOf (geometry_type )  
```  
  
## <a name="arguments"></a>参数  
*geometry_type*  
**nvarchar(4000)** 字符串，用于指定 **geometry** 类型层次结构中公开的 15 个类型之一。  
  
## <a name="return-types"></a>返回类型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 返回类型：bit   
  
 CLR 返回类型：**SqlBoolean**  
  
## <a name="remarks"></a>Remarks  
 方法的输入必须为以下类型之一：**Geometry**、**Point**、**Curve**、**LineString**、**CircularString**、**CompoundCurve**、**Surface**、**Polygon**、**CurvePolygon**、**GeometryCollection**、**MultiSurface**、**MultiPolygon**、**MultiCurve**、**MultiLineString** 和 **MultiPoint**。 如果将任何其他字符串用于输入，此方法会引发 **ArgumentException**。  
  
## <a name="examples"></a>示例  
 下面的示例创建一个 `MultiPoint` 实例，并使用 `InstanceOf()` 查看该实例是否为 `GeometryCollection`。  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('MULTIPOINT(0 0, 13.5 2, 7 19)', 0);  
SELECT @g.InstanceOf('GEOMETRYCOLLECTION');  
```  
  
## <a name="see-also"></a>另请参阅  
 [几何图形实例上的扩展方法](../../t-sql/spatial-geometry/extended-methods-on-geometry-instances.md)  
  
  

