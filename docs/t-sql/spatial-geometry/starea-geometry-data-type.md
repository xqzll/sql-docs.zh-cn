---
title: STArea（geometry 数据类型）| Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STArea (geometry Data Type)
- STArea_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STArea (geometry Data Type)
ms.assetid: a7dd6083-c649-4ac3-885d-1234e0db62f1
author: MladjoA
ms.author: mlandzic
manager: craigg
ms.openlocfilehash: 24ebfb84c17b21116d5571b83adae0d942b31abd
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "65939119"
---
# <a name="starea-geometry-data-type"></a>STArea（geometry 数据类型）
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  返回 geometry 实例的总表面积  。  
  
## <a name="syntax"></a>语法  
  
```  
  
.STArea ( )  
```  
  
## <a name="return-types"></a>返回类型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 返回类型：float   
  
 CLR 返回类型：**SqlDouble**  
  
## <a name="remarks"></a>Remarks  
 如果 geometry 实例仅包含 0 维和 1 维图形，或者为空，则 `STArea()` 返回 0  。 如果 geometry 实例尚未初始化，则 `STArea()` 返回 NULL   。  
  
## <a name="examples"></a>示例  
  
### <a name="a-computing-the-area-of-a-polygon-instance"></a>A. 计算 Polygon 实例的面积  
 以下示例创建一个 `Polygon``geometry` 实例并计算多边形的面积。  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('POLYGON((0 0, 3 0, 3 3, 0 3, 0 0),(2 2, 2 1, 1 1, 1 2, 2 2))', 0);  
SELECT @g.STArea();  
```  
  
### <a name="b-computing-the-area-of-a-curvepolygon-instance"></a>B. 计算 CurvePolygon 实例的面积  
 以下示例计算 `CurvePolygon` 实例的面积。  
  
```
 DECLARE @g geometry;  
 SET @g = geometry::Parse('CURVEPOLYGON(CIRCULARSTRING(0 2, 2 0, 4 2, 4 2, 0 2))');  
 SELECT @g.STArea() AS Area;
 ```  
  
## <a name="see-also"></a>另请参阅  
 [几何图形实例上的 OGC 方法](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  
