---
title: GeomFromGML（geography 数据类型）| Microsoft Docs
ms.custom: ''
ms.date: 07/30/2017
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
- GeomFromGML (geography Data Type)
- GeomFromGML method
ms.assetid: 470d0997-3cb0-4d34-9a45-b332fe432b14
author: MladjoA
ms.author: mlandzic
manager: craigg
ms.openlocfilehash: 1d5542501325fb84b31c0133aaa04aa0097c077b
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "65937830"
---
# <a name="geomfromgml-geography-data-type"></a>GeomFromGML（geography 数据类型）
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

根据地理标记语言 (GML) 的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 子集中的给定表示形式构造 geography 实例  。
  
有关 GML 的详细信息，请参阅下面的开放地理空间信息联盟规范：[OGC 规范：地理标记语言](https://go.microsoft.com/fwlink/?LinkId=93629)
  
这种 geography 数据类型方法支持大于半球的 FullGlobe 实例或空间实例   。
  
## <a name="syntax"></a>语法  
  
```  
  
GeomFromGml ( GML_input, SRID )  
```  
  
## <a name="arguments"></a>参数  
 GML_input   
 XML 输入，GML 将从该输入返回值。  
  
 SRID   
 一个 int 表达式，表示要返回的 geography 实例的空间引用 ID (SRID)   。  
  
## <a name="return-types"></a>返回类型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 返回类型：geography   
  
 CLR 返回类型：**SqlGeography**  
  
## <a name="remarks"></a>Remarks  
 如果输入的格式不正确，此方法将引发 FormatException  。  
  
 如果输入包含对跖边缘，此方法将引发 ArgumentException  。  
  
## <a name="examples"></a>示例  
 下面的示例使用 `GeomFromGml()` 创建 `geography` 实例。  
  
```  
DECLARE @g geography;  
DECLARE @x xml;  
SET @x = '<LineString xmlns="https://www.opengis.net/gml"><posList>47.656 -122.36 47.656 -122.343</posList></LineString>';  
SET @g = geography::GeomFromGml(@x, 4326);  
SELECT @g.ToString();  
```  
  
 下面的示例使用 `GeomFromGml()` 创建 `FullGlobe``geography` 实例。  
  
```  
DECLARE @g geography;  
DECLARE @x xml;  
SET @x = '<FullGlobe xmlns="https://schemas.microsoft.com/sqlserver/2011/geography" />';  
SET @g = geography::GeomFromGml(@x, 4326);  
SELECT @g.ToString();  
```  
  
## <a name="see-also"></a>另请参阅  
 [扩展静态地理方法](../../t-sql/spatial-geography/extended-static-geography-methods.md)  
  
  
