---
title: STDistance（geography 数据类型）| Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STDistance_TSQL
- STDistance (geography Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- STDistance method
ms.assetid: 063d8722-e019-4d3d-8fcf-dbf5325823e7
author: MladjoA
ms.author: mlandzic
manager: craigg
ms.openlocfilehash: 2ae6354623f67003c56c99783e1916b71a80ea3f
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "65937056"
---
# <a name="stdistance-geography-data-type"></a>STDistance（geography 数据类型）
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  返回一个 **geography** 实例中的点与另一个 **geography** 实例中的点之间的最短距离。  
  
> [!NOTE]  
>  `STDistance()` 返回两个 geography 类型之间的最短 **LineString**。 这与测地距离十分相似。 普通地球模型上 `STDistance()` 与精确测地距离之间的偏差不超过 .25%。 这将避免混淆测地类型中长度和距离之间的细微差别。  
  
## <a name="syntax"></a>语法  
  
```  
  
.STDistance ( other_geography )  
```  
  
## <a name="arguments"></a>参数  
 other_geography   
 另一个 geography 实例，将度量该实例与调用 STDistance() 的实例之间的距离  。 如果 other_geography 是一个空集，则 STDistance() 返回 null  。  
  
## <a name="return-types"></a>返回类型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 返回类型：float   
  
 CLR 返回类型：**SqlDouble**  
  
## <a name="remarks"></a>Remarks  
 如果 geography 实例的空间引用 ID (SRID) 不匹配，则 STDistance() 始终返回 null  。  
  
> [!NOTE]  
>  geography 数据类型上用于计算面积或距离的方法将根据在该方法中使用的实例的 SRID 返回不同结果  。   有关 SRID 的详细信息，请参阅[空间引用标识符 (SRID)](../../relational-databases/spatial/spatial-reference-identifiers-srids.md)。  
  
## <a name="examples"></a>示例  
 以下示例查找两个 **geography** 实例之间的距离。  
  
```  
DECLARE @g geography;  
DECLARE @h geography;  
SET @g = geography::STGeomFromText('LINESTRING(-122.360 47.656, -122.343 47.656)', 4326);  
SET @h = geography::STGeomFromText('POINT(-122.34900 47.65100)', 4326);  
SELECT @g.STDistance(@h);  
```  
  
## <a name="see-also"></a>另请参阅  
 [地理实例上的 OGC 方法](../../t-sql/spatial-geography/ogc-methods-on-geography-instances.md)  
  
  
