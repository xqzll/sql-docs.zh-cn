---
title: Count （元组） (MDX) |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 3775af63181489b982778d40ddd69ebc12872271
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "63285039"
---
# <a name="count-tuple-mdx"></a>Count（元组）(MDX)


  返回元组中的维度数。  
  
## <a name="syntax"></a>语法  
  
```  
  
Tuple_Expression.Count  
```  
  
## <a name="arguments"></a>参数  
 *Tuple_Expression*  
 返回元组的有效多维表达式 (MDX)。  
  
## <a name="remarks"></a>备注  
 返回元组中的维度数。  
  
## <a name="example"></a>示例  
 下面的查询中的计算度量值返回值 2，这是在元组 `([Measures].[Internet Sales Amount], [Date].[Calendar].[Calendar Year].&[2001])` 中提供的层次结构的数目：  
  
```  
WITH MEMBER MEASURES.COUNTTUPLE AS  
COUNT(([Measures].[Internet Sales Amount], [Date].[Calendar].[Calendar Year].&[2001]))  
SELECT MEASURES.COUNTTUPLE ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>请参阅  
 [计数&#40;维度&#41; &#40;MDX&#41;](../mdx/count-dimension-mdx.md)   
 [计数&#40;层次结构级别&#41; &#40;MDX&#41;](../mdx/count-hierarchy-levels-mdx.md)   
 [Count（集）(MDX)](../mdx/count-set-mdx.md)   
 [MDX 函数引用 (MDX)](../mdx/mdx-function-reference-mdx.md)  
  
  
