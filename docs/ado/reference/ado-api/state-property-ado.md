---
title: State 属性 (ADO) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Command25::State
helpviewer_keywords:
- State property [ADO]
ms.assetid: 0b993bac-2653-40b1-bcbb-5b57b6aae2bf
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: e8a46dd9358b085fb6079f03df88474b72440068
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "66711257"
---
# <a name="state-property-ado"></a>State 属性 (ADO)
指示所有适用的对象，对象的状态是打开还是已关闭。 如果该对象正在执行的异步方法，指示该对象的当前状态是连接、 执行或检索。  
  
## <a name="return-value"></a>返回值  
 返回**长**值，该值可[ObjectStateEnum](../../../ado/reference/ado-api/objectstateenum.md)值。 默认值是**adStateClosed**。  
  
## <a name="remarks"></a>备注  
 可以使用**状态**属性，以在任何时候确定给定对象的当前状态。  
  
 对象的**状态**属性可以具有的值的组合。 例如，如果执行语句时，此属性将具有的合并的值**adStateOpen**并**adStateExecuting**。  
  
 **状态**属性是只读的。  
  
## <a name="applies-to"></a>适用范围  
  
||||  
|-|-|-|  
|[命令对象 (ADO)](../../../ado/reference/ado-api/command-object-ado.md)|[连接对象 (ADO)](../../../ado/reference/ado-api/connection-object-ado.md)|[记录对象 (ADO)](../../../ado/reference/ado-api/record-object-ado.md)|  
|[记录集对象 (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)|[流对象 (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)||  
  
## <a name="see-also"></a>请参阅  
 [ConnectionString、 ConnectionTimeout 和 State 属性示例 (VB)](../../../ado/reference/ado-api/connectionstring-connectiontimeout-and-state-properties-example-vb.md)   
 [ConnectionString、 ConnectionTimeout 和 State 属性示例 （VC + +）](../../../ado/reference/ado-api/connectionstring-connectiontimeout-and-state-properties-example-vc.md)   
