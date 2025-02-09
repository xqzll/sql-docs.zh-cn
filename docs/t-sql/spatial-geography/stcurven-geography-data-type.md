---
title: STCurveN（geography 数据类型）| Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- STCurveN
- STCurveN_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- STCurveN method (geography)
ms.assetid: 99ef7100-2c4b-4f07-8d66-b343da94b023
author: MladjoA
ms.author: mlandzic
manager: craigg
ms.openlocfilehash: 56adf5a1cfb41b3a8efb10e278109a6d10659e7d
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "65937090"
---
# <a name="stcurven-geography-data-type"></a>STCurveN（geography 数据类型）
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  返回从 geography 实例中指定的曲线，该实例的数据类型为 LineString、CircularString 或 CompoundCurve     。  
  
## <a name="syntax"></a>语法  
  
```  
  
.STCurveN( n )  
```  
  
## <a name="arguments"></a>参数  
 *n*  
 一个 int 表达式，其值介于 1 与 geography 实例中的曲线数之间   。  
  
## <a name="return-types"></a>返回类型  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 返回类型：geography   
  
 CLR 返回类型：**SqlGeography**  
  
## <a name="exceptions"></a>异常  
 如果 n < 1，则会引发 ArgumentOutOfRangeException  。  
  
## <a name="remarks"></a>Remarks  
 如果满足以下条件，则会返回 NULL  。  
  
-   已声明 geography 实例，但未将其实例化   
  
-   geography 实例为空   
  
-   n 超过 geography 实例中的曲线数目（请参阅 [STNumCurves（geography 数据类型）](../../t-sql/spatial-geography/stnumcurves-geography-data-type.md)）   
  
-   geography 实例的维度不相等（请参阅 [STDimension（geography 数据类型）](../../t-sql/spatial-geography/stdimension-geography-data-type.md)）   
  
## <a name="examples"></a>示例  
  
### <a name="a-using-stcurven-on-a-circularstring"></a>A. 在 CircularString 上使用 STCurveN()  
 以下示例返回 CircularString 实例中的第二条曲线  ：  
  
```
 DECLARE @g geography = 'CIRCULARSTRING(-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653)';  
 SELECT @g.STCurveN(2).ToString();
 ```  
  
 该示例返回：  
  
 `CIRCULARSTRING (-122.348 47.658, -122.358 47.658, -122.358 47.653)`  
  
### <a name="b-using-stcurven-on-a-compoundcurve"></a>B. 在 CompoundCurve 上使用 STCurveN()  
 以下示例返回 CompoundCurve 实例中的第二条曲线  ：  
  
```
 DECLARE @g geography = 'COMPOUNDCURVE(CIRCULARSTRING(-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653))';  
 SELECT @g.STCurveN(2).ToString();
 ```  
  
 该示例返回：  
  
 `CIRCULARSTRING (-122.348 47.658, -122.358 47.658, -122.358 47.653)`  
  
### <a name="c-using-stcurven-on-a-compoundcurve-containing-three-circularstrings"></a>C. 在包含三个 CircularString 的 CompoundCurve 实例上使用 STCurveN()  
 以下示例使用 CompoundCurve 实例，该实例将三个单独的 CircularString 实例合并为与上一示例相同的曲线序列   ：  
  
```
 DECLARE @g geography = 'COMPOUNDCURVE (CIRCULARSTRING (-122.358 47.653, -122.348 47.649, -122.348 47.658), CIRCULARSTRING(-122.348 47.658, -122.358 47.658, -122.358 47.653))';  
 SELECT @g.STCurveN(2).ToString();
 ```  
  
 该示例返回：  
  
 `CIRCULARSTRING (-122.348 47.658, -122.358 47.658, -122.358 47.653)`  
  
 `STCurveN()` 返回相同的结果，而无论使用的是哪种熟知文本 （WKT） 格式。  
  
### <a name="d-testing-for-validity-before-calling-stcurve"></a>D. 在调用 STCurve() 之前测试有效性  
 以下示例说明如何在调用 STCurveN() 方法之前确保 n 有效  ：  
  
```
 DECLARE @g geography;  
 DECLARE @n int;  
 SET @n = 2;  
 SET @g = geography::Parse('LINESTRING(-122.358 47.653, -122.348 47.649, -122.348 47.658, -122.358 47.658, -122.358 47.653)');  
 IF @n >= 1 AND @n <= @g.STNumCurves()  
 BEGIN  
 SELECT @g.STCurveN(@n).ToString();  
 END
  ```  
  
## <a name="see-also"></a>另请参阅  
 [地理实例上的 OGC 方法](../../t-sql/spatial-geography/ogc-methods-on-geography-instances.md)  
  
  
