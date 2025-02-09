---
title: 提取 (MDX) |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: a3c58799cc3e95efd7d49b3aff0bf31a1fce22b1
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "63155197"
---
# <a name="extract-mdx"></a>Extract (MDX)


  返回由提取的层次结构元素中的元组构成的集。  
  
## <a name="syntax"></a>语法  
  
```  
  
Extract(Set_Expression, Hierarchy_Expression1 [,Hierarchy_Expression2, ...n] )  
```  
  
## <a name="arguments"></a>参数  
 *Set_Expression*  
 返回集的有效多维表达式 (MDX)。  
  
 *Hierarchy_Expression1*  
 返回层次结构的有效多维表达式 (MDX)。  
  
 *Hierarchy_Expression2*  
 返回层次结构的有效多维表达式 (MDX)。  
  
## <a name="remarks"></a>备注  
 **提取**函数返回的元组从提取的层次结构元素组成的集。 对于指定集中的每个元组，将指定层次结构的成员提取到结果集中的新元组。 此函数始终删除重复元组。  
  
 **提取**函数执行相反的操作[叉积](../mdx/crossjoin-mdx.md)函数。  
  
## <a name="examples"></a>示例  
 以下查询说明如何使用**提取**上的元组返回的一组函数**NonEmpty**函数：  
  
 `SELECT [Measures].[Internet Sales Amount] ON 0,`  
  
 `//Returns the distinct combinations of Customer and Date for all purchases`  
  
 `//of Bike Racks or Bike Stands`  
  
 `EXTRACT(`  
  
 `NONEMPTY(`  
  
 `[Customer].[Customer].[Customer].MEMBERS`  
  
 `*`  
  
 `[Date].[Date].[Date].MEMBERS`  
  
 `*`  
  
 `{[Product].[Product Categories].[Subcategory].&[26],[Product].[Product Categories].[Subcategory].&[27]}`  
  
 `*`  
  
 `{[Measures].[Internet Sales Amount]}`  
  
 `)`  
  
 `,  [Customer].[Customer], [Date].[Date])`  
  
 `ON 1`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>请参阅  
 [MDX 函数引用 (MDX)](../mdx/mdx-function-reference-mdx.md)  
  
  
