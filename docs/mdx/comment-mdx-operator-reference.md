---
title: -（注释） (MDX) |Microsoft Docs
ms.date: 06/04/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: mdx
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: dc8bf49f6d25c4e00c2d5693ff6a9cf48d5450ee
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "63208757"
---
# <a name="comment---mdx-operator-reference"></a>注释-MDX 运算符参考


  表示用户提供的注释文本。  
  
## <a name="syntax"></a>语法  
  
```  
  
-- Comment_Text      
```  
  
#### <a name="parameters"></a>Parameters  
 *Comment_Text*  
 包含注释文本的字符串。  
  
## <a name="remarks"></a>备注  
 注释可以在单独的一行插入，也可以在多维表达式 (MDX) 脚本行的结尾处嵌入，还可以嵌入在 MDX 语句中。 服务器不对注释进行计算。  
  
 该运算符用于单行或嵌套的注释。 用 -- 插入的注释由换行符分隔。  
  
 注释没有最大长度限制。  
  
## <a name="examples"></a>示例  
 下面的示例演示了此运算符的用法。  
  
```  
-- This member returns the gross profit margin for product types  
-- and reseller types crossjoined by year.  
SELECT   
    [Date].[Calendar].[Calendar Year].Members *  
      [Reseller].[Reseller Type].Children ON 0,  
    [Product].[Category].[Category].Members ON 1  
FROM -- Select from the Adventure Works cube.  
    [Adventure Works]  
WHERE  
    [Measures].[Gross Profit Margin]  
```  
  
## <a name="see-also"></a>请参阅  
 [注释 (MDX)](../mdx/comment-mdx.md)   
 [&#40;Comment&#41; &#40;MDX&#41;](../mdx/comment-mdx-double-slash.md)   
 [MDX 运算符参考&#40;MDX&#41;](../mdx/mdx-operator-reference-mdx.md)  
  
  
