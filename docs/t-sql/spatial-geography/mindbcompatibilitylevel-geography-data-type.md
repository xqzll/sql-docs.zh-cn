---
title: MinDbCompatibilityLevel（geography 数据类型）| Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- MinDbCompatibilityLevel
- MinDbCompatibilityLevel_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- MinDbCompatibilityLevel method (geography)
ms.assetid: a9e44748-4a9e-4179-abc4-7631597be5a7
author: MladjoA
ms.author: mlandzic
manager: craigg
ms.openlocfilehash: 32d7df746e51612dd39360ff6702e9489111ce04
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "65937253"
---
# <a name="mindbcompatibilitylevel-geography-data-type"></a>MinDbCompatibilityLevel（geography 数据类型）
[!INCLUDE[tsql-appliesto-ss2012-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-asdb-xxxx-xxx-md.md)]

  返回识别 geography 数据类型的最基本的数据库兼容级别  。  
  
## <a name="syntax"></a>语法  
  
```  
  
. MinDbCompatibilityLevel ( )  
```  
  
## <a name="return-types"></a>返回类型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 返回类型：int   
  
 CLR 返回类型：int   
  
## <a name="remarks"></a>Remarks  
 在更改数据库的兼容级别之前应使用 `MinDbCompatibilityLevel()` 测试空间对象的兼容性。 无效的 geography 类型返回 110  。  
  
## <a name="examples"></a>示例  
  
### <a name="a-testing-circularstring-type-for-compatibility-with-compatibility-level-110"></a>A. 在兼容级别为 110 的情况下测试 CircularString 类型是否兼容  
 下面的示例测试 `CircularString` 实例是否与较早版本的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 兼容：  
  
```  
DECLARE @g geometry = 'CIRCULARSTRING(-120.533 46.566, -118.283 46.1, -122.3 47.45)';  
IF @g.MinDbCompatibilityLevel() <= 110  
BEGIN  
    SELECT @g.ToString();  
END  
  
```  
  
### <a name="b-testing-linestring-type-for-compatibility-with-compatibility-level-100"></a>B. 在兼容级别为 100 的情况下测试 LineString 类型是否兼容  
 下面的示例测试 `LineString` 实例是否与 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 兼容：  
  
```  
DECLARE @g geometry = 'LINESTRING(-120.533 46.566, -118.283 46.1, -122.3 47.45)';  
IF @g.MinDbCompatibilityLevel() <= 100  
BEGIN  
    SELECT @g.ToString();  
END  
  
```  
  
### <a name="c-testing-the-value-of-a-geography-instance-for-compatibility"></a>C. 测试 Geography 实例的值是否兼容  
 下面的示例说明两个 `geography` 实例的兼容级别。 一个小于半球，另一个大于半球：  
  
```  
DECLARE @g geography = geography::Parse('POLYGON((0 -10, 120 -10, 240 -10, 0 -10))');  
DECLARE @h geography = geography::Parse('POLYGON((0 10, 120 10, 240 10, 0 10))');  
IF (@g.EnvelopeAngle() >= 90)  
BEGIN  
SELECT @g.MinDbCompatibilityLevel();  
END     
IF (@h.EnvelopeAngle() < 90)  
BEGIN  
SELECT @h.MinDbCompatibilityLevel();  
END  
  
```  
  
 第一个 SELECT 语句返回 110，第二个 SELECT 语句返回 100。  
  
## <a name="see-also"></a>另请参阅  
 [ALTER DATABASE 兼容级别 (Transact-SQL)](../../t-sql/statements/alter-database-transact-sql-compatibility-level.md)   
 [SQL Server 数据库引擎的后向兼容性](../../database-engine/sql-server-database-engine-backward-compatibility.md)  
  
  
