---
title: STMPolyFromText（geometry 数据类型）| Microsoft Docs
ms.custom: ''
ms.date: 08/03/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STMPolyFromText (geometry Data Type)
- STMPolyFromText_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STMPolyFromText (geometry Data Type)
ms.assetid: f087a61c-f063-4fb8-8f1c-251a2fed76a1
author: MladjoA
ms.author: mlandzic
manager: craigg
ms.openlocfilehash: 9f1071dafdb4f1f012aab06724cd8c3865242dbb
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "65938569"
---
# <a name="stmpolyfromtext-geometry-data-type"></a>STMPolyFromText（geometry 数据类型）
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

从开放地理空间信息联盟 (OGC) 已知文本 (WKT) 表示形式返回 **geometry** 实例以及该实例传递的任何 Z（标高）和 M（度量）值。
  
## <a name="syntax"></a>语法  
  
```  
  
STMPolyFromText ( 'multipolygon_tagged_text' , SRID )  
```  
  
## <a name="arguments"></a>参数  
 multipolygon_tagged_text   
 希望返回的 **geometryMultiPolygon** 实例的 WKT 表示形式。 multipolygon_tagged_text 是一个 nvarchar(max) 表达式   。  
  
 SRID   
 一个 int 表达式，表示希望返回的 geometryMultiPolygon 实例的空间引用 ID (SRID)   。  
  
## <a name="return-types"></a>返回类型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 返回类型：geometry   
  
 CLR 返回类型：**Sql Geometry**  
  
 OGC 类型：**MultiPolygon**  
  
## <a name="remarks"></a>Remarks  
 如果输入的格式不正确，此方法将引发 FormatException  。  
  
## <a name="examples"></a>示例  
 下面的示例使用 `STMPolyFromText()` 创建 `geometry` 实例。  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STMPolyFromText('MULTIPOLYGON (((5 5, 10 5, 10 10, 5 5)), ((10 10, 100 10, 200 200, 30 30, 10 10)))', 0);  
SELECT @g.ToString();  
```  
  
## <a name="see-also"></a>另请参阅  
 [OGC 静态几何图形方法](../../t-sql/spatial-geometry/ogc-static-geometry-methods.md)  
  
  

