---
title: 集运算符 |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: df58b5c7f6da05700f00b4ec5fd46b81926dd3bb
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "63150169"
---
# <a name="set-operators"></a>集运算符


  在多维表达式 (MDX) 中，集运算符对成员或集进行运算并返回一个集。 通常用集运算符替换 MDX 表达式中的多个集函数。  
  
 MDX 支持下表中列出的集运算符。  
  
|运算符|Description|  
|--------------|-----------------|  
|[-（排除）](../mdx/except-mdx-operator.md)|返回两个集之间的不同项，并删除重复的成员。<br /><br /> 此运算符在功能上等效于[除](../mdx/except-mdx-function.md)函数。|  
|[*（叉积）](../mdx/crossjoin-mdx-operator-reference.md)|返回两个集的叉积。<br /><br /> 此运算符在功能上等效于[叉积](../mdx/crossjoin-mdx.md)函数。|  
|[设置用户帐户 ：(Range)](../mdx/range-mdx.md)|返回自然排序的集，并将两个指定的成员作为终结点，这两个指定成员之间的所有成员都作为集的成员包括在其中。|  
|[+（并集）](../mdx/union-mdx-operator-reference.md)|返回两个集的并集，不包括重复的成员。<br /><br /> 此运算符在功能上等效于[Union &#40;MDX&#41; ](../mdx/union-mdx.md)函数。|  
  
## <a name="see-also"></a>请参阅  
 [MDX 函数引用 (MDX)](../mdx/mdx-function-reference-mdx.md)   
 [MDX 运算符参考&#40;MDX&#41;](../mdx/mdx-operator-reference-mdx.md)   
 [运算符&#40;MDX 语法&#41;](../mdx/operators-mdx-syntax.md)  
  
  
