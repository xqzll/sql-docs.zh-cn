---
title: CalculationPassValue (MDX) | Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: ca5966492ac83599cd4a053ea526e2ce366e4b0e
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "63181623"
---
# <a name="calculationpassvalue-mdx"></a>CalculationPassValue (MDX)


  返回用多维表达式 (MDX) 对多维数据集的指定计算传递求得的数值或字符串值。  
  
## <a name="syntax"></a>语法  
  
```  
  
      Numeric syntax  
CalculationPassValue(Numeric_Expression,Pass_Value [, ABSOLUTE | RELATIVE [,ALL]])  
String syntax  
CalculationPassValue(String_Expression ,Pass_Value [, ABSOLUTE | RELATIVE [,ALL]])  
```  
  
## <a name="arguments"></a>参数  
 *Numeric_Expression*  
 返回数字的有效数值表达式，通常为单元坐标的多维表达式 (MDX)。  
  
 *String_Expression*  
 通常是单元坐标（返回以字符串表示的数字）的有效多维表达式 (MDX) 的有效字符串表达式。  
  
 *Pass_Value*  
 指定计算传递数的有效数值表达式。  
  
 ABSOLUTE  
 一个访问标志值，指定*Pass_Value*参数包含计算传递的从零开始的索引。 如果未指定访问标志值，则 ABSOLUTE 将作为默认访问标志值。  
  
 RELATIVE  
 一个访问标志值，指定*Pass_Value*参数包含从触发计算的计算传递的相对偏移量。 如果偏移量解析为某个小于 0 的计算传递索引，则使用计算传递 0，并且不会出错。  
  
 ALL  
 如果设置此标志，则除了存储引擎加载的值外，其余值均为空值。 如果未设置此标志，则聚合这些值而不进行任何计算。  
  
## <a name="remarks"></a>备注  
 如果提供了数值表达式，则函数通过计算指定计算传递中的指定 MDX 数值表达式来返回一个数值，或者通过访问标志以及访问标志修饰符对其进行修改。  
  
 如果提供的字符串表达式，该函数通过计算指定的计算传递中的指定的 MDX 字符串表达式来返回一个字符串值和修改 （可选） 通过访问标志以及访问标志修饰符 *。*  
  
 中的自动递归解决方法[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]，此函数的用处。  
  
> [!NOTE]  
>  只有管理员才能使用**CalculationPassValue** MDX 脚本中的函数。 如果在不具有管理员特权的角色上下文中运行包含此函数的 MDX 脚本，则会发生错误。  
  
## <a name="see-also"></a>请参阅  
 [CalculationCurrentPass (MDX)](../mdx/calculationcurrentpass-mdx.md)   
 [IIf &#40;MDX&#41;](../mdx/iif-mdx.md)   
 [MDX 函数引用 (MDX)](../mdx/mdx-function-reference-mdx.md)  
  
  
