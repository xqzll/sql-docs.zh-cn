---
title: 保留关键字 (DMX) |Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 7af060203d044435e364803ace67d35711eb63ea
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "62658791"
---
# <a name="reserved-keywords-dmx"></a>保留关键字 (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssASversion2005](../includes/ssasversion2005-md.md)] 保留供其独占使用的某些关键字。 除了 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 在数据挖掘扩展插件 (DMX) 语言参考中定义的位置以外，这些关键字不能用于 DMX 语句的任何其他位置。 这些受限制的 DMX 关键字包括下列成员：  
  
-   主题中列出的所有数据定义语句[DMX 数据定义语句](../dmx/dmx-statements-data-definition.md)。  
  
-   所有数据挖掘查询函数的主题中列出[DMX 函数参考](../dmx/data-mining-extensions-dmx-function-reference.md)。  
  
-   主题中列出的所有运算符[DMX 运算符参考](../dmx/data-mining-extensions-dmx-operator-reference.md)。  
  
-   在多维表达式 (MDX) 查询语言中定义并作为 DMX 语句的一部分包括在内的关键字。  
  
-   在 OLE DB for Data Mining 规范中定义并作为 DMX 语句的一部分包括在内的关键字。  
  
 在数据库中命名对象时，建议您使用命名约定以避免使用保留关键字。  
  
 如果数据库中确实包含与保留关键字匹配的名称，则在引用这些对象时必须使用分隔符。 有关详细信息，请参阅[标识符&#40;DMX&#41;](../dmx/identifiers-dmx.md)。  
  
## <a name="see-also"></a>请参阅  
 [数据挖掘扩展插件 (DMX) 参考](../dmx/data-mining-extensions-dmx-reference.md)   
 [数据挖掘扩展插件&#40;DMX&#41;语句引用](../dmx/data-mining-extensions-dmx-statements.md)   
 [数据挖掘扩展插件&#40;DMX&#41;语法约定](../dmx/data-mining-extensions-dmx-syntax-conventions.md)   
 [数据挖掘扩展插件&#40;DMX&#41;语法元素](../dmx/data-mining-extensions-dmx-syntax-elements.md)   
 [了解 DMX Select 语句](../dmx/understanding-the-dmx-select-statement.md)  
  
  
