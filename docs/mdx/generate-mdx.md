---
title: 生成 (MDX) |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: c965300654f8cbebdf6fbd88699afdd512632488
ms.sourcegitcommit: d9c5b9ab3c282775ed61712892eeb3e150ccc808
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/05/2019
ms.locfileid: "67597437"
---
# <a name="generate-mdx"></a>Generate (MDX)


  将一个集应用于另一个集中的每个成员，然后对得到的集求并集。 另外，此函数返回通过用字符串表达式对集求值而创建的串联字符串。  
  
## <a name="syntax"></a>语法  
  
```  
  
Set expression syntax  
Generate( Set_Expression1 ,  Set_Expression2 [ , ALL ]  )  
  
String expression syntax  
Generate( Set_Expression1 ,  String_Expression [ ,Delimiter ]  )  
```  
  
## <a name="arguments"></a>参数  
 *Set_Expression1*  
 返回集的有效多维表达式 (MDX)。  
  
 *Set_Expression2*  
 返回集的有效多维表达式 (MDX)。  
  
 *String_Expression*  
 通常为指定集中每个元组当前成员名称 (CurrentMember.Name) 的有效字符串表达式。  
  
 *分隔符*  
 以字符串表达式表示的有效分隔符。  
  
## <a name="remarks"></a>备注  
 如果指定第二个集，则**生成**函数将返回一组生成的第二个集中的元组应用到第一个集中每个元组，然后对所得到的联合设置。 如果**所有**指定，则该函数将保留在结果集中的重复项。  
  
 如果指定的字符串表达式，则**生成**函数返回计算指定的字符串表达式对第一个集中每个元组和再串联得到的结果生成的字符串。 根据需要，可以分隔字符串，从而分隔得到的串联字符串中的每个结果。  
  
## <a name="examples"></a>示例  
  
### <a name="set"></a>将  
 在以下示例中，由于 [Date].[Calendar Year].[Calendar Year].MEMBERS 集中有四个成员，因此，查询四次返回包含 Measure Internet Sales Amount 的集：  
  
```  
SELECT   
GENERATE( [Date].[Calendar Year].[Calendar Year].MEMBERS  
, {[Measures].[Internet Sales Amount]}, ALL)  
ON 0  
FROM [Adventure Works]  
```  
  
 删除 ALL 将更改查询，这样仅返回一次 Internet Sales Amount：  
  
```  
SELECT   
GENERATE( [Date].[Calendar Year].[Calendar Year].MEMBERS  
, {[Measures].[Internet Sales Amount]})  
ON 0  
FROM [Adventure Works]  
```  
  
 最常见的实际用法**生成**计算复杂集表达式，如 TopCount，对一组的成员。 以下示例查询显示行上每个日历年的前 10 种产品：  
  
```  
SELECT   
{[Measures].[Internet Sales Amount]}  
ON 0,  
GENERATE(   
[Date].[Calendar Year].[Calendar Year].MEMBERS  
, TOPCOUNT(  
[Date].[Calendar Year].CURRENTMEMBER  
*  
[Product].[Product].[Product].MEMBERS  
,10, [Measures].[Internet Sales Amount]))  
ON 1  
FROM [Adventure Works]  
```  
  
 请注意，每年，并且显示不同的前 10 的使用**生成**是得到此结果的唯一方法。 将日历年和前 10 种产品的集进行简单交叉联接将显示所有时间的前 10 种产品（每年都重复），如以下示例所示：  
  
```  
SELECT   
{[Measures].[Internet Sales Amount]}  
ON 0,  
[Date].[Calendar Year].[Calendar Year].MEMBERS  
*   
TOPCOUNT(  
[Product].[Product].[Product].MEMBERS  
,10, [Measures].[Internet Sales Amount])  
ON 1  
FROM [Adventure Works]  
```  
  
### <a name="string"></a>String  
 下面的示例演示如何使用**生成**返回一个字符串：  
  
```  
WITH   
MEMBER MEASURES.GENERATESTRINGDEMO AS  
GENERATE(   
[Date].[Calendar Year].[Calendar Year].MEMBERS,  
[Date].[Calendar Year].CURRENTMEMBER.NAME)  
MEMBER MEASURES.GENERATEDELIMITEDSTRINGDEMO AS  
GENERATE(   
[Date].[Calendar Year].[Calendar Year].MEMBERS,  
[Date].[Calendar Year].CURRENTMEMBER.NAME, " AND ")  
SELECT   
{MEASURES.GENERATESTRINGDEMO, MEASURES.GENERATEDELIMITEDSTRINGDEMO}  
ON 0  
FROM [Adventure Works]  
```  
  
> [!NOTE]  
>  这种形式的**生成**函数时非常有用调试计算，因为它让你可以返回集内显示所有成员的名称的字符串。 这可能是一组的严格 MDX 表示形式更便于阅读， [SetToStr &#40;MDX&#41; ](../mdx/settostr-mdx.md)函数返回。  
  
## <a name="see-also"></a>请参阅  
 [MDX 函数引用 (MDX)](../mdx/mdx-function-reference-mdx.md)  
  
  
