---
title: STDistance（geometry 数据类型）| Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STDistance_TSQL
- STDistance (geometry Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- STDistance (geometry Data Type)
ms.assetid: ac815bc7-5342-4cc4-af40-c80a1c4c8b68
author: MladjoA
ms.author: mlandzic
manager: craigg
ms.openlocfilehash: 47caf3acbbdfd663dcfc507279a4b41ce134ad01
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "65938969"
---
# <a name="stdistance-geometry-data-type"></a>STDistance（geometry 数据类型）
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  返回一个 **geometry** 实例中的点与另一个 **geometry** 实例中的点之间的最短距离。  
  
## <a name="syntax"></a>语法  
  
```  
  
.STDistance ( other_geometry )  
```  
  
## <a name="arguments"></a>参数  
 *other_geometry*  
 另一个 **geometry** 实例，将度量该实例与调用 `STDistance()` 的实例之间的距离。 如果 *other_geometry* 为空集，则 `STDistance()` 返回 null。  
  
## <a name="return-types"></a>返回类型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 返回类型：float   
  
 CLR 返回类型：**SqlDouble**  
  
## <a name="remarks"></a>Remarks  
 如果 **geometry** 实例的空间引用 ID (SRID) 不匹配，则 `STDistance()` 始终返回 null。  
  
## <a name="examples"></a>示例  
  
```  
DECLARE @g geometry;  
DECLARE @h geometry;  
SET @g = geometry::STGeomFromText('POLYGON((0 0, 2 0, 2 2, 0 2, 0 0))', 0);  
SET @h = geometry::STGeomFromText('POINT(10 10)', 0);  
SELECT @g.STDistance(@h);  
```  
  
## <a name="see-also"></a>另请参阅  
 [空间索引概述](../../relational-databases/spatial/spatial-indexes-overview.md)   
 [几何图形实例上的 OGC 方法](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  
