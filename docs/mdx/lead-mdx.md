---
title: 导致 (MDX) |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: d72af1bf0b671eeb2bd4b84c194f129ed1ce6bfe
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "63205442"
---
# <a name="lead-mdx"></a>Lead (MDX)


  返回在成员级别中比指定成员位置靠后且靠后位数为指定位数的成员。  
  
## <a name="syntax"></a>语法  
  
```  
  
Member_Expression.Lead( Index )  
```  
  
## <a name="arguments"></a>参数  
 *Member_Expression*  
 返回成员的有效多维表达式 (MDX)。  
  
 *Index*  
 指定成员位置位数的有效数值表达式。  
  
## <a name="remarks"></a>备注  
 级别内的成员位置由属性层次结构的自然顺序决定。 位置的编号从零开始。  
  
 如果指定的前置位数为零 (0)，**会导致**函数返回指定的成员。  
  
 如果指定的前置位数为负，**会导致**函数返回前面的成员。  
  
 `Lead(1)` 等效于[NextMember](../mdx/nextmember-mdx.md)函数。 `Lead(-1)` 等效于[PrevMember](../mdx/prevmember-mdx.md)函数。  
  
 **会导致**函数是类似于[延隔](../mdx/lag-mdx.md)函数，不同之处在于**延隔**函数查找成员的方向相反**导致**函数。 也就是说，`Lead(n)` 等效于 `Lag(-n)`。  
  
## <a name="example"></a>示例  
 下例将返回 2001 年 12 月的值：  
  
```  
SELECT [Date].[Fiscal].[Month].[February 2002].Lead(-2) ON 0  
FROM [Adventure Works]  
  
```  
  
 下例将返回 2002 年 3 月的值：  
  
```  
SELECT [Date].[Fiscal].[Month].[February 2002].Lead(1) ON 0  
FROM [Adventure Works]  
  
```  
  
## <a name="see-also"></a>请参阅  
 [MDX 函数引用 (MDX)](../mdx/mdx-function-reference-mdx.md)  
  
  
