---
title: 同级成员 (MDX) |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: a4414e134d3b837406c3cb72566084029cf522c9
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "63149255"
---
# <a name="siblings-mdx"></a>Siblings (MDX)


  返回指定成员的同级，包括该成员本身。  
  
## <a name="syntax"></a>语法  
  
```  
  
Member_Expression.Siblings   
```  
  
## <a name="arguments"></a>参数  
 *Member_Expression*  
 返回成员的有效多维表达式 (MDX)。  
  
### <a name="example"></a>示例  
 下面的示例返回 March 2003 的同级（即 January 2003 和 February 2003，也包括 March 2003）的默认度量值。  
  
```  
SELECT [Date].[Calendar].[Month].[March 2003].Siblings ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>请参阅  
 [MDX 函数引用 (MDX)](../mdx/mdx-function-reference-mdx.md)  
  
  
