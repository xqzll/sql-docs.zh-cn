---
title: STNumCurves（geometry 数据类型）| Microsoft Docs
ms.custom: ''
ms.date: 08/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- STNumCurves method (geometry)
ms.assetid: 20c2fa0b-656b-4519-b34c-cc8f094290d4
author: MladjoA
ms.author: mlandzic
manager: craigg
ms.openlocfilehash: 6447c64b18b690f6bcdcd0f2ffca7e6b674e3200
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "65938545"
---
# <a name="stnumcurves-geometry-data-type"></a>STNumCurves（geometry 数据类型）
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

当 **geometry** 实例是一维空间数据类型时，此方法返回该实例中的曲线数。 一维空间数据类型包括 LineString、CircularString 和 CompoundCurve    。 `STNumCurves`() 仅适用于简单类型；它不适用于 **MultiLineString** 之类的 **geometry** 集合。
  
## <a name="syntax"></a>语法  
  
```  
  
.STNumCurves()  
```  
  
## <a name="return-types"></a>返回类型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 返回类型：geometry   
  
 CLR 返回类型：**SqlGeometry**  
  
## <a name="remarks"></a>Remarks  
 空的一维 **geometry** 实例返回 0。 当 **geometry** 实例不是一维实例或为未初始化的实例时，将返回 **NULL**。  
  
## <a name="examples"></a>示例  
  
### <a name="a-using-stnumcurves-on-a-circularstring-instance"></a>A. 对 CircularString 实例使用 STNumCurves()  
 下面的示例演示如何获取 `CircularString` 实例中的曲线数量：  
  
```
 DECLARE @g geometry;  
 SET @g = geometry::Parse('CIRCULARSTRING(10 0, 0 10, -10 0, 0 -10, 10 0)');  
 SELECT @g.STNumCurves();
 ```  
  
### <a name="b-using-stnumcurves-on-a-compoundcurve-instance"></a>B. 对 CompoundCurve 实例使用 STNumCurves()  
 下面的示例使用 `STNumCurves()` 返回 `CompoundCurve` 实例中的曲线数量。  
  
```
 DECLARE @g geometry;  
 SET @g = geometry::Parse('COMPOUNDCURVE(CIRCULARSTRING(10 0, 0 10, -10 0, 0 -10, 10 0))');  
 SELECT @g.STNumCurves();
 ```  
  
## <a name="see-also"></a>另请参阅  
 [空间数据类型概述](../../relational-databases/spatial/spatial-data-types-overview.md)   
 [几何图形实例上的 OGC 方法](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  

