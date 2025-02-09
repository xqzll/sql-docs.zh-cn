---
title: LastPeriods (MDX) |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 58e94b5128760dfd1d179ecad3cae7bbf065ee10
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "63205295"
---
# <a name="lastperiods-mdx"></a>LastPeriods (MDX)


  返回指定成员之前（包含该成员）的成员集。  
  
## <a name="syntax"></a>语法  
  
```  
  
LastPeriods(Index [ ,Member_Expression ] )  
```  
  
## <a name="arguments"></a>参数  
 *Index*  
 指定期间数的有效数值表达式。  
  
 *Member_Expression*  
 返回成员的有效多维表达式 (MDX)。  
  
## <a name="remarks"></a>备注  
 如果指定的期间数是正数， **LastPeriods**函数将返回一组的成员滞后的成员开始*索引*-1 从指定的成员表达式，且结尾为指定的成员。 函数返回的成员数等于*索引*。  
  
 如果指定的期间数为负， **LastPeriods**函数返回一组的成员的指定成员开始和结束的潜在顾客的成员 (-*索引*-1) 从指定成员。 函数返回的成员数等于值的绝对值*索引*。  
  
 如果指定的期间数为零， **LastPeriods**函数将返回空集。 这是与不同**延隔**函数，如果指定 0，则返回指定的成员。  
  
 如果未指定成员，则**LastPeriods**函数使用**Time.CurrentMember**。 如果没有任何一个维度标记为 Time 维度，该函数将在不发生错误的情况下分析并执行，但将导致客户端应用程序出现单元错误。  
  
## <a name="examples"></a>示例  
 下面的示例返回 2002 会计年度第二、第三和第四会计季度的默认度量值。  
  
```  
SELECT LastPeriods(3,[Date].[Fiscal].[Fiscal Quarter].[Q4 FY 2002]) ON 0  
FROM [Adventure Works]  
```  
  
> [!NOTE]  
>  此示例还可以用 :（冒号）运算符编写：  
>   
>  `[Date].[Fiscal].[Fiscal Quarter].[Q4 FY 2002]: [Date].[Fiscal].[Fiscal Quarter].[Q2 FY 2002]`  
  
 下面的示例返回 2002 会计年度第一会计季度的默认度量值。 虽然指定的期间数为三个，但是只能返回一个，因为该会计年度中没有更早的期间。  
  
```  
SELECT LastPeriods  
   (3,[Date].[Fiscal].[Fiscal Quarter].[Q1 FY 2002]  
   ) ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>请参阅  
 [MDX 函数引用 (MDX)](../mdx/mdx-function-reference-mdx.md)  
  
  
