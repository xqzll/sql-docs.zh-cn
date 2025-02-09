---
title: LinRegVariance (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: b3ae56238623c41d29ccb388a5aaa178352af196
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "63208741"
---
# <a name="linregvariance-mdx"></a>LinRegVariance (MDX)


  对集进行线性回归计算，并返回与回归线，相关的方差 y = ax + b。  
  
## <a name="syntax"></a>语法  
  
```  
  
LinRegVariance(Set_Expression, Numeric_Expression_y [ ,Numeric_Expression_x ] ] )  
```  
  
## <a name="arguments"></a>参数  
 *Set_Expression*  
 返回集的有效多维表达式 (MDX)。  
  
 *Numeric_Expression_y*  
 返回表示 Y 轴值的数字的有效数值表达式，通常是单元坐标的多维表达式 (MDX)。  
  
 *Numeric_Expression_x*  
 通常是单元坐标（返回代表 X 轴的值的数字）的多维表达式 (MDX) 的有效数值表达式。  
  
## <a name="remarks"></a>备注  
 线性回归使用最小二乘法，可以计算出回归线（即一系列点的最佳拟合线）的公式。 回归线具有如下公式，其中是增量的斜率，b 是截距：  
  
 y = ax+b  
  
 **LinRegVariance**函数计算指定的 setagainst 的第一个数值表达式以获得 y 轴的值。 该函数然后计算指定的 setagainst 第二个数值表达式，如果指定，以获得 x 轴的值。 如果未指定第二个数值 expressionis，该函数使用指定集中单元的当前上下文作为值在 x 轴。 不指定 x 轴参数通常不对时间维度。  
  
 获取点集后**LinRegVariance**函数将返回描述线性方程与点的拟合度统计方差。  
  
> [!NOTE]  
>  **LinRegVariance**函数将忽略空单元或单元格包含文本或逻辑值。 但是，该函数将包含值为零的单元。  
  
## <a name="example"></a>示例  
 下例返回一个方差，该方差描述了单位销售额和商店销售额度量值的线性方程与点的拟合程度。  
  
```  
LinRegVariance(LastPeriods(10),[Measures].[Unit Sales],[Measures].[Store Sales])  
```  
  
## <a name="see-also"></a>请参阅  
 [MDX 函数引用 (MDX)](../mdx/mdx-function-reference-mdx.md)  
  
  
