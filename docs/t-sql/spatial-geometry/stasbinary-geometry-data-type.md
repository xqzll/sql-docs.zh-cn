---
title: STAsBinary（geometry 数据类型）| Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STAsBinary_TSQL
- STAsBinary (geometry Data Type)
dev_langs:
- TSQL
helpviewer_keywords:
- STAsBinary (geometry Data Type)
ms.assetid: 65353777-e3e6-461c-9504-ea4d83312692
author: MladjoA
ms.author: mlandzic
manager: craigg
ms.openlocfilehash: 37c935195c740ef03b891f6fb082257422ae412a
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "65937328"
---
# <a name="stasbinary-geometry-data-type"></a>STAsBinary（geometry 数据类型）
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  返回 geometry 实例的开放地理空间信息联盟 (OGC) 熟知二进制 (WKB) 表示形式。  
 
## <a name="syntax"></a>语法  
  
```  
  
.STAsBinary ( )  
```  
  
## <a name="return-types"></a>返回类型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 返回类型：varbinary(max)   
  
 CLR 返回类型：**SqlBytes**  
  
## <a name="examples"></a>示例  
 以下示例根据文本创建一个从 (0,0) 到 (2,3) 的 `LineString` geometry 实例。 `STAsBinary()` 以 WKB 形式返回结果。  
  
```  
DECLARE @g geometry;  
SET @g = geometry::STGeomFromText('LINESTRING(0 0, 2 3)', 0);  
SELECT @g.STAsBinary();  
```  
  
## <a name="see-also"></a>另请参阅  
 [几何图形实例上的 OGC 方法](../../t-sql/spatial-geometry/ogc-methods-on-geometry-instances.md)  
  
  
