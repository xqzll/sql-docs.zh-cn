---
title: STArea（geography 数据类型）| Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STArea (geography Data Type)
- STArea_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STArea method
ms.assetid: cfc0b0e0-7fde-431a-863f-d13f3b1b1bef
author: MladjoA
ms.author: mlandzic
manager: craigg
ms.openlocfilehash: 49919caaf30bb425e90b286cb3c8e7877067ae6d
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "65936243"
---
# <a name="starea-geography-data-type"></a>STArea（geography 数据类型）
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

返回 geography 实例的总表面积  。 STArea() 的结果是 geography  实例的空间引用标识符使用的平方度量单位。 例如，如果实例的 SRID 是 4326，STArea() 返回以平方米为单位的结果。  
  
## <a name="syntax"></a>语法  
  
```  
  
.STArea ( )  
```  
  
## <a name="return-types"></a>返回类型  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 返回类型：float   
  
CLR 返回类型：**SqlDouble**  
  
## <a name="remarks"></a>Remarks  
如果 geography  实例仅包含零维和一维图形，或者为空，那么 STArea() 返回 0。  
  
> [!NOTE]  
>  geography 数据类型上生成标准返回值的方法将根据在该方法中使用的实例的 SRID 生成不同结果  。 有关 SRID 的详细信息，请参阅[空间引用标识符 (SRID)](../../relational-databases/spatial/spatial-reference-identifiers-srids.md)。  
  
## <a name="examples"></a>示例  
以下示例使用 `STArea()` 创建 `Polygon geography` 实例，并计算该多边形的面积。  
  
```  
DECLARE @g geography;  
SET @g = geography::STGeomFromText('POLYGON((-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653))', 4326);  
SELECT @g.STArea();  
```  
  
## <a name="see-also"></a>另请参阅  
[地理实例上的 OGC 方法](../../t-sql/spatial-geography/ogc-methods-on-geography-instances.md)  
  
