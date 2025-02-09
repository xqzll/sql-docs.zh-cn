---
title: Parse（geography 数据类型）| Microsoft Docs
ms.custom: ''
ms.date: 07/30/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- Parse method
- Parse (geography Data Type)
ms.assetid: 21c402fa-fd0f-4d09-a097-49cee0316d4e
author: MladjoA
ms.author: mlandzic
manager: craigg
ms.openlocfilehash: 023af0279bdb848e299ec1dbe31ff82305ad109a
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "65935915"
---
# <a name="parse-geography-data-type"></a>Parse（geography 数据类型）
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

从开放地理空间信息联盟 (OGC) 熟知文本 (WKT) 表示形式返回 geography 实例  。 Parse() 与 [STGeomFromText](../../t-sql/spatial-geography/stgeomfromtext-geography-data-type.md) 等效，不同的是，前者将值为 4326 的空间引用 ID (SRID) 作为参数。 输入值可以根据需要包含 Z（标高）和 M（度量）值。
  
这种 geography 数据类型方法支持大于半球的 FullGlobe 实例或空间实例   。
  
## <a name="syntax"></a>语法  
  
```  
  
Parse ( 'geography_tagged_text' )  
```  
  
## <a name="arguments"></a>参数  
 geography_tagged_text   
 要返回的 geography 实例的 WKT 表示形式  。 geography_tagged_text 是一个 nvarchar 表达式   。  
  
## <a name="return-types"></a>返回类型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 返回类型：geography   
  
 CLR 返回类型：**SqlGeography**  
  
## <a name="remarks"></a>Remarks  
 `Parse()` 返回的 geography  实例的 OGC 类型设置为相应的 WKT 输入。  
  
 字符串“Null”将被解释为空 geography 实例  。  
  
 如果输入包含对跖边缘，此方法将引发 ArgumentException  。  
  
## <a name="examples"></a>示例  
 下面的示例使用 `Parse()` 创建 `geography` 实例。  
  
```  
DECLARE @g geography;   
SET @g = geography::Parse('LINESTRING(-122.360 47.656, -122.343 47.656)');  
SELECT @g.ToString();  
```  
  
## <a name="see-also"></a>另请参阅  
 [扩展静态地理方法](../../t-sql/spatial-geography/extended-static-geography-methods.md)   
 [STGeomFromText（geography 数据类型）](../../t-sql/spatial-geography/stgeomfromtext-geography-data-type.md)  
  
  
