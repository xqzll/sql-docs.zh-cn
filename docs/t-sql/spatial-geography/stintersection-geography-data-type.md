---
title: STIntersection（geography 数据类型）| Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STIntersection_TSQL
- STIntersection (geography Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- STIntersection method
ms.assetid: 7e09468f-499f-4a38-ba4b-bb30b8821e3b
author: MladjoA
ms.author: mlandzic
manager: craigg
ms.openlocfilehash: e1ee84ab21082193c50486f775a22caec4e0dbb4
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "65936818"
---
# <a name="stintersection-geography-data-type"></a>STIntersection（geography 数据类型）
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  返回一个对象，该对象表示一个 geography 实例与另一个 geography 实例的交点   。  
  
## <a name="syntax"></a>语法  
  
```  
  
.STIntersection ( other_geography )  
```  
  
## <a name="arguments"></a>参数  
 other_geography   
 与调用 STIntersection() 的实例进行比较的另一个 geography 实例  。  
  
## <a name="return-types"></a>返回类型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 返回类型：geography   
  
 CLR 返回类型：**SqlGeography**  
  
## <a name="remarks"></a>Remarks  
 返回两个 geography 实例的交集。  
  
 如果 geography 实例的空间引用标识符 (SRID) 不匹配，则 STIntersection() 始终返回 NULL  。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 支持大于半球的空间实例。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 在服务器上返回的可能结果集中可能包含 FullGlobe 实例  。  
  
 只有在输入实例包含圆弧线段时，结果才会包含圆弧线段。  
  
## <a name="examples"></a>示例  
  
### <a name="a-computing-the-intersection-of-a-polygon-and-a-linestring"></a>A. 计算 Polygon 和 LineString 的交集  
 以下示例使用 `STIntersection()` 计算 `Polygon` 和 `LineString` 的交集。  
  
```  
DECLARE @g geography;  
DECLARE @h geography;  
SET @g = geography::STGeomFromText('POLYGON((-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653))', 4326);  
SET @h = geography::STGeomFromText('LINESTRING(-122.360 47.656, -122.343 47.656)', 4326);  
SELECT @g.STIntersection(@h).ToString();  
```  
  
### <a name="b-computing-the-intersection-of-a-polygon-and-a-curvepolygon"></a>B. 计算 Polygon 和 CurvePolygon 的交集  
 以下示例返回一个包含圆弧线段的实例。  
  
```  
DECLARE @g geography;  
DECLARE @h geography;  
SET @g = geography::STGeomFromText('POLYGON((-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653))', 4326);  
SET @h = geography::STGeomFromText('CURVEPOLYGON(CIRCULARSTRING(-122.351 47.656, -122.341 47.656, -122.341 47.661, -122.351 47.661, -122.351 47.656))', 4326);  
SELECT @g.STIntersection(@h).ToString();  
```  
  
### <a name="c-computing-the-symmetric-difference-with-fullglobe"></a>C. 计算与 FullGlobe 的余集  
 以下示例计算 `Polygon` 与 `FullGlobe` 的余集。  
  
```  
DECLARE @g geography = 'POLYGON((-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653))';  
SELECT @g.STIntersection('FULLGLOBE').ToString();  
```  
  
## <a name="see-also"></a>另请参阅  
 [地理实例上的 OGC 方法](../../t-sql/spatial-geography/ogc-methods-on-geography-instances.md)  
  
  
