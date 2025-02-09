---
title: GeomFromGml（geometry 数据类型）| Microsoft Docs
ms.custom: ''
ms.date: 08/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- GeomFromGML_TSQL
- GeomFromGML
dev_langs:
- TSQL
helpviewer_keywords:
- GeomFromGML (geometry Data Type)
ms.assetid: a3f2c84b-a49f-4ce3-ba25-b903fb0c99b4
author: MladjoA
ms.author: mlandzic
manager: craigg
ms.openlocfilehash: ad5704a913ff5d8d24eeeb360f3309dfea0a2555
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "65938031"
---
# <a name="geomfromgml-geometry-data-type"></a>GeomFromGml（geometry 数据类型）
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

根据地理标记语言 (GML) 的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 子集中的给定表示形式构建 geometry 实例  。
  
有关地理标记语言的详细信息，请参阅以下开放地理空间信息联盟规范：
  
[OGC 规范：地理标记语言](https://go.microsoft.com/fwlink/?LinkId=93629)
  
## <a name="syntax"></a>语法  
  
```  
  
GeomFromGml ( GML_input, SRID )  
```  
  
## <a name="arguments"></a>参数  
 GML_input   
 XML 输入，GML 将从该输入返回值。  
  
 SRID   
 一个 int 表达式，表示希望返回的 geometry 实例的空间引用 ID (SRID)   。  
  
## <a name="return-types"></a>返回类型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 返回类型：geometry   
  
 CLR 返回类型：**SqlGeometry**  
  
## <a name="remarks"></a>Remarks  
 如果输入的格式不正确，此方法将引发 FormatException  。  
  
## <a name="examples"></a>示例  
 下面的示例使用 `GeomFromGml()` 创建 `geometry` 实例。  
  
```  
DECLARE @g geometry;  
DECLARE @x xml;  
SET @x = '<LineString xmlns="https://www.opengis.net/gml"> <posList>100 100 20 180 180 180</posList> </LineString>';  
SET @g = geometry::GeomFromGml(@x, 0);  
SELECT @g.ToString();  
```  
  
## <a name="see-also"></a>另请参阅  
 [扩展静态几何图形方法](../../t-sql/spatial-geometry/extended-static-geometry-methods.md)  
  
  

