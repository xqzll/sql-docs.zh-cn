---
title: AsTextZM（geography 数据类型）| Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- AsTextZM (geography Data Type)
- AsTextZM_TSQL
- AsTextZM
- AsTextZM_(geography_Data_Type)_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- AsTextZM method
ms.assetid: e9dc27f6-e945-4457-8498-7644db34008e
author: MladjoA
ms.author: mlandzic
manager: craigg
ms.openlocfilehash: 8b4d5e834faa455eeb62e67f396447d44a176f55
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "65936385"
---
# <a name="astextzm-geography-data-type"></a>AsTextZM（geography 数据类型）
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  返回 geography 实例的开放地理空间信息联盟 (OGC) 熟知文本 (WKT) 表示形式，增加了该实例传递的任何 Z（标高）和 M（度量）值    。  
  
## <a name="syntax"></a>语法  
  
```  
  
.AsTextZM ()  
```  
  
## <a name="return-types"></a>返回类型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 返回类型：nvarchar(max)   
  
 CLR 返回类型：**SqlChars**  
  
## <a name="remarks"></a>Remarks  
  
## <a name="examples"></a>示例  
 下面的示例创建一个带有 Z（标高）和 M（度量）值的 `Point` 实例   。 `STAsText()` 选择 WKT 值 (-122.34900 47.65100)；`AsTextZM()` 选择相同的 WKT 值，还返回 Z 和 M 的值，从而生成 (-122.34900 47.65100 10.3 12)   。  
  
```  
DECLARE @g geography;  
SET @g = geography::STGeomFromText('POINT(-122.34900 47.65100 10.3 12)', 4326);  
SELECT @g.STAsText();  
SELECT @g.AsTextZM();  
```  
  
## <a name="see-also"></a>另请参阅  
 [Geography 实例上的扩展方法](../../t-sql/spatial-geography/extended-methods-on-geography-instances.md)   
 [M（geography 数据类型）](../../t-sql/spatial-geography/m-geography-data-type.md)   
 [Z（geography 数据类型）](../../t-sql/spatial-geography/z-geography-data-type.md)  
  
  
