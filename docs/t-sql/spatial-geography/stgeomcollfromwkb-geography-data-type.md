---
title: STGeomCollFromWKB（geography 数据类型）| Microsoft Docs
ms.custom: ''
ms.date: 07/30/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STGeomCollFromWKB (geography Data Type)
- STGeomCollFromWKB_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STMGeomCollFromWKB method
ms.assetid: bbed028c-9cd6-4236-b5e5-8e914a21f2e4
author: MladjoA
ms.author: mlandzic
manager: craigg
ms.openlocfilehash: fe164f0ca8a411f4cb9de9242e2e2df0d8043d38
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "65936939"
---
# <a name="stgeomcollfromwkb-geography-data-type"></a>STGeomCollFromWKB（geography 数据类型）
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

从开放地理空间信息联盟 (OGC) 已知二进制 (WKB) 表示形式中返回 GeometryCollection 实例  。
  
## <a name="syntax"></a>语法  
  
```  
  
STGeomCollFromWKB ( 'WKB_geometrycollection' , SRID )  
```  
  
## <a name="arguments"></a>参数  
 WKB_geometrycollection   
 希望返回的 GeometryCollection 实例的 WKB 表示形式  。 WKB_geometrycollection 是一个 varbinary(max) 表达式   。  
  
 SRID   
 一个 int 表达式，表示希望返回的 GeometryCollection 实例的空间引用 ID (SRID)   。  
  
## <a name="return-types"></a>返回类型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 返回类型：geography   
  
 CLR 返回类型：**SqlGeography**  
  
## <a name="remarks"></a>Remarks  
 STGeomCollFromWKB() 返回的 geography 实例的 OGC 类型设为 GeometryCollection、MultiPolygon、MultiLineString 或 MultiPoint，具体取决于相应的 WKB 输入      。  
  
 如果输入的格式不正确，此方法将引发 FormatException 异常  。  
  
## <a name="examples"></a>示例  
 下面的示例使用 `STGeomCollFromWKB()` 创建 `geography` 实例。  
  
```  
DECLARE @g geography;  
SET @g = geography::STGeomCollFromWKB(0x01070000000200000001010000007593180456965EC017D9CEF753D34740010200000002000000D7A3703D0A975EC08716D9CEF7D34740CBA145B6F3955EC08716D9CEF7D34740, 4326);  
SELECT @g.ToString();  
```  
  
## <a name="see-also"></a>另请参阅  
 [OGC 静态地理方法](../../t-sql/spatial-geography/ogc-static-geography-methods.md)  
  
  
