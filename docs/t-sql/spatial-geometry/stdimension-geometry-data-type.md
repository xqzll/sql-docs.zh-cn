---
title: STDimension（geometry 数据类型）| Microsoft Docs
ms.custom: ''
ms.date: 08/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STDimension_TSQL
- STDimension (geometry Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- STDimension (geometry Data Type)
ms.assetid: 4fbd27dd-317b-4916-a8ae-4df1b8a6f27c
author: MladjoA
ms.author: mlandzic
manager: craigg
ms.openlocfilehash: 1f84bd8cd53f68bd45cf91307968b45923e53280
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "65938988"
---
# <a name="stdimension-geometry-data-type"></a>STDimension（geometry 数据类型）
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

返回 **geometry** 实例的最大维度。
  
## <a name="syntax"></a>语法  
  
```  
  
.STDimension ( )  
```  
  
## <a name="return-types"></a>返回类型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 返回类型：int   
  
 CLR 返回类型：**SqlInt32**  
  
## <a name="remarks"></a>Remarks  
 如果 **geometry** 实例为空，则 `STDimension()` 返回 -1。  
  
## <a name="examples"></a>示例  
 以下示例创建一个存放 **geometry** 实例的表变量，并插入一个 `Point`、一个 `LineString` 和一个 `Polygon`。  然后，该示例使用 `STDimension()` 返回每个 **geometry** 实例的维度。  
  
```  
DECLARE @temp table ([name] varchar(10), [geom] geometry);  
INSERT INTO @temp values ('Point', geometry::STGeomFromText('POINT(3 3)', 0));  
INSERT INTO @temp values ('LineString', geometry::STGeomFromText('LINESTRING(0 0, 3 3)', 0));  
INSERT INTO @temp values ('Polygon', geometry::STGeomFromText('POLYGON((0 0, 3 0, 0 3, 0 0))', 0));  
SELECT [name], [geom].STDimension() as [dim]  
FROM @temp;  
```  
  
 然后，该示例返回每个 `geometry` 实例的维度。  
  
|NAME|dim|  
|----------|---------|  
|点|0|  
|LineString|1|  
|Polygon|2|  
  
## <a name="see-also"></a>另请参阅  
 [几何图形实例上的 OGC 方法](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  

