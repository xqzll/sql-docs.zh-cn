---
title: FirstChild (MDX) |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: ed769da991c54b4ae7bc85091a652a27f5399a73
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "63155183"
---
# <a name="firstchild-mdx"></a>FirstChild (MDX)


  返回指定成员的第一个子成员。  
  
## <a name="syntax"></a>语法  
  
```  
  
Member_Expression.FirstChild   
```  
  
## <a name="arguments"></a>参数  
 *Member_Expression*  
 返回成员的有效多维表达式 (MDX)。  
  
### <a name="example"></a>示例  
 下面的查询返回 Fiscal 层次结构中 2003 会计年度的第一个子级，也就是 2003 会计年度的第一个半期。  
  
```  
SELECT [Date].[Fiscal].[Fiscal Year].&[2003].FirstChild ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>请参阅  
 [LastChild &#40;MDX&#41;](../mdx/lastchild-mdx.md)   
 [MDX 函数引用 (MDX)](../mdx/mdx-function-reference-mdx.md)  
  
  
