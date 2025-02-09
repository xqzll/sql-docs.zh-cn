---
title: TopPercent (MDX) |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 0093da0a4f69d8a1e4cf178959d28509eef15b75
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "63208401"
---
# <a name="toppercent-mdx"></a>TopPercent (MDX)


  按降序对集进行排序，并返回一个最大值元组集，该元组集的累积合计等于或大于指定的百分比。  
  
## <a name="syntax"></a>语法  
  
```  
  
TopPercent(Set_Expression, Percentage, Numeric_Expression)   
```  
  
## <a name="arguments"></a>参数  
 *Set_Expression*  
 返回集的有效多维表达式 (MDX)。  
  
 *百分比*  
 有效的数值表达式，指定要返回的元组的百分比。  
  
> [!IMPORTANT]  
>  *百分比*必须是正数值; 负值将生成错误。  
  
 *Numeric_Expression*  
 返回数字的有效数值表达式，通常为单元坐标的多维表达式 (MDX)。  
  
## <a name="remarks"></a>备注  
 **TopPercent**函数计算指定数值表达式对指定集，对该集按降序顺序求值的总和。 然后，该函数返回具有最高值的元素，其总合计值的累积百分比至少是指定的百分比。 该函数返回累积合计至少达到指定百分比的最小子集。 返回的元素按从大到小的顺序排序。  
  
> [!WARNING]  
>  如果*Numeric_Expression*然后返回任何负值**TopPercent**返回仅一 （1） 行。  
>   
>  请参阅针对此行为的详细演示的第二个示例。  
  
> [!IMPORTANT]  
>  像[BottomPercent](../mdx/bottompercent-mdx.md)函数， **TopPercent**函数总是会在层次结构。  
  
## <a name="example"></a>示例  
 下面的示例返回对于“自行车”类别，帮助实现前 10% 的分销商销售额的最佳城市。 结果将按降序排序，并且从具有最高销售额的城市开始。  
  
```  
SELECT [Measures].[Reseller Sales Amount] ON 0,  
TopPercent  
   ({[Geography].[Geography].[City].Members}  
   , 10  
   , [Measures].[Reseller Sales Amount]  
   ) ON 1  
FROM [Adventure Works]  
WHERE([Product].[Product Categories].[Bikes])  
```  
  
 上面的表达式生成以下结果：  
  
||Reseller Sales Amount|  
|-|---------------------------|  
|Toronto|$3,508,904.84|  
|London|$1,521,530.09|  
|Seattle|$1,209,418.16|  
|Paris|$1,170,425.18|  
  
 使用下面的查询可以获取原始数据集，并返回 588 行：  
  
```  
SELECT [Measures].[Reseller Sales Amount] ON 0,  
Order  
   ({[Geography].[Geography].[City].Members}  
   , [Measures].[Reseller Sales Amount]  
   , BDESC  
   ) ON 1  
FROM [Adventure Works]  
WHERE([Product].[Product Categories].[Bikes])  
  
```  
  
## <a name="example"></a>示例  
 下面的演练将帮助您理解中负值的影响*Numeric_Expression*。 首先，将生成一些可展示该行为的上下文。  
  
 下面的查询将返回一个表，由分销商的“Sales Amount”、“Total Product Cost”和“Gross Profit”构成，并且按利润的降序排序。 请注意，对于利润仅存在负值；因此，最小的利润损失将出现在最顶部。  
  
```  
SELECT { [Measures].[Reseller Sales Amount], [Measures].[Reseller Total Product Cost], [Measures].[Reseller Gross Profit] } ON columns  
     ,  ORDER( [Product].[Product Categories].[Bikes].[Touring Bikes].children, [Measures].[Reseller Gross Profit], BDESC )   ON rows  
FROM [Adventure Works]  
  
```  
  
 上述查询会返回以下结果；为便于阅读，中间部分的行已删除。  
  
||Reseller Sales Amount|Reseller Total Product Cost|Reseller Gross Profit|  
|-|---------------------------|---------------------------------|---------------------------|  
|Touring-2000 Blue, 50|$157,444.56|$163,112.57|($5,668.01)|  
|旅行车 2000年蓝色，46|$321,027.03|$333,021.50|($11,994.47)|  
|Touring-3000 Blue, 62|$87,773.61|$100,133.52|($12,359.91)|  
|...|...|...|...|  
|Touring-1000年黄色，46|$1,016,312.83|$1,234,454.27|($218,141.44)|  
|Touring-1000 Yellow, 60|$1,184,363.30|$1,443,407.51|($259,044.21)|  
  
 现在，如果要求您按利润展示前 100% 的自行车，则编写如下查询：  
  
```  
SELECT { [Measures].[Reseller Sales Amount], [Measures].[Reseller Total Product Cost], [Measures].[Reseller Gross Profit] } ON columns  
     ,  TOPPERCENT( [Product].[Product Categories].[Bikes].[Touring Bikes].children, 100,[Measures].[Reseller Gross Profit] )   ON rows  
FROM [Adventure Works]  
  
```  
  
 请注意，查询要求百分之百 (100%)；这意味着应返回所有行。 但是，因为在负值*Numeric_Expression* ，只返回一行。  
  
||Reseller Sales Amount|Reseller Total Product Cost|Reseller Gross Profit|  
|-|---------------------------|---------------------------------|---------------------------|  
|Touring-2000 Blue, 50|$157,444.56|$163,112.57|($5,668.01)|  
  
## <a name="see-also"></a>请参阅  
 [MDX 函数引用 (MDX)](../mdx/mdx-function-reference-mdx.md)  
  
  
