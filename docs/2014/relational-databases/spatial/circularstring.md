---
title: CircularString | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
ms.assetid: 9fe06b03-d98c-4337-9f89-54da98f49f9f
author: MladjoA
ms.author: mlandzic
manager: craigg
ms.openlocfilehash: efe15f6eea386522fc6139601af66ce736e980f3
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "66014414"
---
# <a name="circularstring"></a>CircularString
  `CircularString` 是零个或多个连续圆弧线段的集合。 圆弧线段是二维平面中由三个点定义的曲线段；第一个点不能与第三个点相同。 如果圆弧线段的所有三个点共线，则将该圆弧线段视为一条直线段。  
  
> [!IMPORTANT]  
>  有关详细的说明和中引入的新空间功能的示例[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]，其中包括`CircularString`子类型，请下载白皮书[SQL Server 2012 中的新空间功能](https://go.microsoft.com/fwlink/?LinkId=226407)。  
  
## <a name="circularstring-instances"></a>CircularString 实例  
 下面的图形显示了有效的 `CircularString` 实例：  
  
 ![](../../database-engine/media/5ff17e34-b578-4873-9d33-79500940d0bc.png "5ff17e34-b578-4873-9d33-79500940d0bc")  
  
### <a name="accepted-instances"></a>接受的实例  
 一个`CircularString`实例接受如果它为空或包含奇数个点 n，其中 n > 1。 下面的 `CircularString` 实例均为已接受实例。  
  
```  
DECLARE @g1 geometry = 'CIRCULARSTRING EMPTY';  
DECLARE @g2 geometry = 'CIRCULARSTRING(1 1, 2 0, -1 1)';  
DECLARE @g3 geometry = 'CIRCULARSTRING(1 1, 2 0, 2 0, 2 0, 1 1)';  
```  
  
 `@g3` 显示 `CircularString` 实例可能被接受，但无效。 下面的 CircularString 实例声明未被接受。 此声明引发 `System.FormatException`。  
  
```  
DECLARE @g geometry = 'CIRCULARSTRING(1 1, 2 0, 2 0, 1 1)';  
```  
  
### <a name="valid-instances"></a>有效实例  
 有效 `CircularString` 实例必须为空或具有以下属性：  
  
-   必须至少包含一条圆弧线段（也就是至少有三个点）。  
  
-   序列中的每条圆弧线段（最后一条线段除外）的最后一个端点必须是序列中后一条线段的第一个端点。  
  
-   必须有奇数个点。  
  
-   不能有一段与自身重合。  
  
-   虽然 `CircularString` 实例可能包含直线段，但这些直线段必须由三个共线点定义。  
  
 下面的示例显示有效的 `CircularString` 实例。  
  
```  
DECLARE @g1 geometry = 'CIRCULARSTRING EMPTY';  
DECLARE @g2 geometry = 'CIRCULARSTRING(1 1, 2 0, -1 1)';  
DECLARE @g3 geometry = 'CIRCULARSTRING(1 1, 2 0, 2 0, 1 1, 0 1)';  
DECLARE @g4 geometry = 'CIRCULARSTRING(1 1, 2 2, 2 2)';  
SELECT @g1.STIsValid(), @g2.STIsValid(), @g3.STIsValid(),@g4.STIsValid();  
```  
  
 `CircularString` 实例必须至少包含两条圆弧线段以定义完整的圆。 `CircularString` 实例不能使用一条圆弧线段（例如（1 1、3 1、1 1））定义一个完整的圆。 使用（1 1、2 2、3 1、2 0、1 1）定义圆。  
  
 下面的示例显示无效的 CircularString 实例。  
  
```  
DECLARE @g1 geometry = 'CIRCULARSTRING(1 1, 2 0, 1 1)';  
DECLARE @g2 geometry = 'CIRCULARSTRING(0 0, 0 0, 0 0)';  
SELECT @g1.STIsValid(), @g2.STIsValid();  
```  
  
### <a name="instances-with-collinear-points"></a>具有共线点的实例  
 在下列情况下，圆弧线段将被视为直线段：  
  
-   当所有三个点共线时，例如（1 3、4 4、7 5）。  
  
-   当第一个点和中间的点相同但第三个点不同时，例如（1 3、1 3、7 5）。  
  
-   当中间的点和最后一个点相同但第一个点不同时，例如（1 3、4 4、4 4）。  
  
## <a name="examples"></a>示例  
  
### <a name="a-instantiating-a-geometry-instance-with-an-empty-circularstring"></a>A. 使用空的 CircularString 实例化一个几何图形实例  
 该示例说明如何创建一个空的 `CircularString` 实例：  
  
```sql  
DECLARE @g geometry;  
SET @g = geometry::Parse('CIRCULARSTRING EMPTY');  
```  
  
### <a name="b-instantiating-a-geometry-instance-using-a-circularstring-with-one-circular-arc-segment"></a>B. 使用具有一条圆弧线段的 CircularString 实例化一个几何图形实例  
 下面的示例演示如何创建一个具有一条圆弧线段（半圆）的 `CircularString` 实例：  
  
```sql  
DECLARE @g geometry;  
SET @g = geometry:: STGeomFromText('CIRCULARSTRING(2 0, 1 1, 0 0)', 0);  
SELECT @g.ToString();  
```  
  
### <a name="c-instantiating-a-geometry-instance-using-a-circularstring-with-multiple-circular-arc-segments"></a>C. 使用具有多条圆弧线段的 CircularString 实例化一个几何图形实例  
 下面的示例演示如何创建一个具有多条圆弧线段（整圆）的 `CircularString` 实例：  
  
```sql  
DECLARE @g geometry;  
SET @g = geometry::Parse('CIRCULARSTRING(2 1, 1 2, 0 1, 1 0, 2 1)');  
SELECT 'Circumference = ' + CAST(@g.STLength() AS NVARCHAR(10));    
```  
  
 此示例将产生以下输出：  
  
```  
Circumference = 6.28319  
```  
  
 在使用 `LineString` 而不使用 `CircularString` 时，比较输出结果：  
  
```sql  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('LINESTRING(2 1, 1 2, 0 1, 1 0, 2 1)', 0);  
SELECT 'Perimeter = ' + CAST(@g.STLength() AS NVARCHAR(10));  
```  
  
 此示例将产生以下输出：  
  
```  
Perimeter = 5.65685  
```  
  
 请注意，对于值`CircularString`示例是接近 2???，这是圆的实际周长。  
  
### <a name="d-declaring-and-instantiating-a-geometry-instance-with-a-circularstring-in-the-same-statement"></a>D. 在同一语句中使用 CircularString 声明和实例化一个几何图形实例  
 此代码段说明了如何在同一语句中使用 `geometry` 声明和实例化 `CircularString` 实例：  
  
```sql  
DECLARE @g geometry = 'CIRCULARSTRING(0 0, 1 2.1082, 3 6.3246, 0 7, -3 6.3246, -1 2.1082, 0 0)';  
```  
  
### <a name="e-instantiating-a-geography-instance-with-a-circularstring"></a>E. 使用 CircularString 实例化一个地域实例  
 下面的示例演示如何使用 `geography` 声明和实例化 `CircularString` 实例：  
  
```sql  
DECLARE @g geography = 'CIRCULARSTRING(-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653)';  
```  
  
### <a name="f-instantiating-a-geometry-instance-with-a-circularstring-that-is-a-straight-line"></a>F. 使用直线 CircularString 实例化一个几何图形实例  
 下面的示例演示如何创建一个直线 `CircularString` 实例：  
  
```sql  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('CIRCULARSTRING(0 0, 1 2, 2 4)', 0);  
```  
  
## <a name="see-also"></a>请参阅  
 [空间数据类型概述](spatial-data-types-overview.md)   
 [CompoundCurve](compoundcurve.md)   
 [MakeValid（geography 数据类型）](/sql/t-sql/spatial-geography/makevalid-geography-data-type)   
 [MakeValid（geometry 数据类型）](/sql/t-sql/spatial-geometry/makevalid-geometry-data-type)   
 [STIsValid（geometry 数据类型）](/sql/t-sql/spatial-geometry/stisvalid-geometry-data-type)   
 [STIsValid（geography 数据类型）](/sql/t-sql/spatial-geography/stisvalid-geography-data-type)   
 [STLength（geometry 数据类型）](/sql/t-sql/spatial-geometry/stlength-geometry-data-type)   
 [STStartPoint（geometry 数据类型）](/sql/t-sql/spatial-geometry/ststartpoint-geometry-data-type)   
 [STEndpoint（geometry 数据类型）](/sql/t-sql/spatial-geometry/stendpoint-geometry-data-type)   
 [STPointN（geometry 数据类型）](/sql/t-sql/spatial-geometry/stpointn-geometry-data-type)   
 [STNumPoints（geometry 数据类型）](/sql/t-sql/spatial-geometry/stnumpoints-geometry-data-type)   
 [STIsRing（geometry 数据类型）](/sql/t-sql/spatial-geometry/stisring-geometry-data-type)   
 [STIsClosed（geometry 数据类型）](/sql/t-sql/spatial-geometry/stisclosed-geometry-data-type)   
 [STPointOnSurface（geometry 数据类型）](/sql/t-sql/spatial-geometry/stpointonsurface-geometry-data-type)   
 [LineString](linestring.md)  
  
  
