---
title: IsEmpty (MDX) |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: dbed0eba3fec73d7134b1ce21275c28dbd387fcd
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "63224965"
---
# <a name="isempty-mdx"></a>IsEmpty (MDX)


  返回表达式的计算结果是否为空单元值。  
  
## <a name="syntax"></a>语法  
  
```  
  
IsEmpty(Value_Expression)   
```  
  
## <a name="arguments"></a>参数  
 *Value_Expression*  
 有效 MDX（多维表达式）表达式，通常返回成员或元组的单元坐标。  
  
## <a name="remarks"></a>备注  
 **IsEmpty**函数将返回**true**如果表达式的计算结果为空单元值。 否则，此函数返回**false**。  
  
> [!NOTE]  
>  成员的默认属性为成员的值。  
  
 **IsEmpty**函数是唯一的方法可以可靠测试空单元，因为空单元值中具有特殊含义[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]。  
  
> [!IMPORTANT]  
>  如果值表达式的计算将返回错误，则该函数将返回**false**。 值表达式也可能返回错误，例如，属性引用引用了无效或不存在的属性。  
  
 有关空单元的详细信息，请参阅 OLE DB 文档。  
  
## <a name="example"></a>示例  
 如果 Date 维度的 Fiscal 层次结构上当前成员的 Internet Sales Amount 返回一个空单元，则下面的示例将返回 TRUE：  
  
 `WITH MEMBER MEASURES.ISEMPTYDEMO AS`  
  
 `IsEmpty([Measures].[Internet Sales Amount])`  
  
 `SELECT {[Measures].[Internet Sales Amount],MEASURES.ISEMPTYDEMO} ON 0,`  
  
 `[Date].[Fiscal].MEMBERS ON 1`  
  
 `FROM [Adventure Works]`  
  
## <a name="see-also"></a>请参阅  
 [使用空值](../mdx/working-with-empty-values.md)   
 [MDX 函数引用 (MDX)](../mdx/mdx-function-reference-mdx.md)  
  
  
