---
title: STIsSimple（geometry 数据类型）| Microsoft Docs
ms.custom: ''
ms.date: 08/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STIsSimple_TSQL
- STIsSimple (geometry Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- STIsSimple (geometry Data Type)
ms.assetid: da8f45d4-4f9c-405d-b883-760eb5344a71
author: MladjoA
ms.author: mlandzic
manager: craigg
ms.openlocfilehash: 662ead77fe7af659718266ab3518a13536c77e7f
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "65938760"
---
# <a name="stissimple-geometry-data-type"></a>STIsSimple（geometry 数据类型）
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

如果 **geometry** 实例是开放地理空间信息联盟 (OGC) 所定义的简单实例，则返回 1。 如果 **geometry** 实例不是简单实例，则返回 0。
  
## <a name="syntax"></a>语法  
  
```  
  
.STIsSimple ( )  
```  
  
## <a name="return-types"></a>返回类型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 返回类型：bit   
  
 CLR 返回类型：**SqlBoolean**  
  
## <a name="remarks"></a>Remarks  
 简单的 **geometry** 实例必须符合以下所有要求：  
  
-   实例的每个图形不能与自身相交，但其终点除外。  
  
-   实例的任何两个图形可在某个点上相交，但两个边界上的点除外。  
  
## <a name="examples"></a>示例  
 下面的示例创建一个非简单 `LineString` 实例，该实例与自身相交并使用 `STIsSimple()` 来测试 `LineString` 是否为简单类型。  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('LINESTRING(0 0, 2 2, 0 2, 2 0)', 0);  
SELECT @g.STIsSimple();  
```  
  
## <a name="see-also"></a>另请参阅  
 [几何图形实例上的 OGC 方法](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  

