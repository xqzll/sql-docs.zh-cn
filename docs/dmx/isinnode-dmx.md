---
title: IsInNode (DMX) | Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 21c90bea43972f1c9088c228d6810b18308f93f4
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "62503624"
---
# <a name="isinnode-dmx"></a>IsInNode (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  指示指定的节点是否包含当前事例。  
  
## <a name="syntax"></a>语法  
  
```  
  
IsInNode(<NodeID>)  
```  
  
## <a name="return-type"></a>返回类型  
 一种布尔值类型。  
  
## <a name="remarks"></a>备注  
 **IsInNode**只用于[SELECT FROM&#60;模型&#62;。用例&#40;DMX&#41; ](../dmx/select-from-model-cases-dmx.md)并[FROM&#60;模型&#62;。SAMPLE_CASES &#40;DMX&#41; ](../dmx/select-from-model-sample-cases-dmx.md)查询。  
  
## <a name="examples"></a>示例  
 以下示例返回所有用于创建与 IsInNode 函数中所指定节点关联的模型的事例。  
  
```  
Select * from [TM Decision Tree].Cases  
WHERE IsInNode('0')  
```  
  
## <a name="see-also"></a>请参阅  
 [数据挖掘扩展插件&#40;DMX&#41;函数参考](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [函数&#40;DMX&#41;](../dmx/functions-dmx.md)   
 [通用预测函数&#40;DMX&#41;](../dmx/general-prediction-functions-dmx.md)  
  
  
