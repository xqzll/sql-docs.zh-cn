---
title: DistinctCount (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 3f0235f14366667dbce21af92cf0418bb6fa1e0e
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "63248212"
---
# <a name="distinctcount-mdx"></a>DistinctCount (MDX)


  返回集中非重复的非空元组的数目。  
  
## <a name="syntax"></a>语法  
  
```  
  
DistinctCount(Set_Expression)  
```  
  
## <a name="arguments"></a>参数  
 *Set_Expression*  
 返回集的有效多维表达式 (MDX)。  
  
## <a name="remarks"></a>备注  
 **DistinctCount**函数等同于`Count(Distinct(Set_Expression), EXCLUDEEMPTY)`。  
  
## <a name="examples"></a>示例  
 以下查询说明如何使用 DistinctCount 函数：  
  
 `WITH SET MySet AS`  
  
 `{[Customer].[Customer Geography].[Country].&[Australia],[Customer].[Customer Geography].[Country].&[Australia],`  
  
 `[Customer].[Customer Geography].[Country].&[Canada],[Customer].[Customer Geography].[Country].&[France],`  
  
 `[Customer].[Customer Geography].[Country].&[United Kingdom],[Customer].[Customer Geography].[Country].&[United Kingdom]}`  
  
 `*`  
  
 `{([Date].[Calendar].[Date].&[20010701],[Measures].[Internet Sales Amount] )}`  
  
 `//Returns the value 3 because Internet Sales Amount is null`  
  
 `//for the UK on the date specified`  
  
 `MEMBER MEASURES.SETDISTINCTCOUNT AS`  
  
 `DISTINCTCOUNT(MySet)`  
  
 `SELECT {MEASURES.SETDISTINCTCOUNT} ON 0`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>请参阅  
 [Count（集）(MDX)](../mdx/count-set-mdx.md)   
 [MDX 函数引用 (MDX)](../mdx/mdx-function-reference-mdx.md)  
  
  
