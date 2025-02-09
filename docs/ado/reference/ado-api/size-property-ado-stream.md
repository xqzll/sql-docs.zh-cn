---
title: Size 属性 (ADO Stream) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Stream::Size
helpviewer_keywords:
- Size property [ADO Stream]
ms.assetid: a487c241-d953-4c31-ae7e-6358d5cf6733
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 42a4725efde507112d51b4f9c41af4ba83f63da4
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "66719084"
---
# <a name="size-property-ado-stream"></a>Size 属性（ADO 流）
指示流中的字节数的大小。  
  
## <a name="return-values"></a>返回值  
 返回**长**值，该值指定流的大小中的字节数。 如果不知道的流的大小，默认值将为流，则为-1 的大小。  
  
## <a name="remarks"></a>备注  
 **大小**可以仅可用于打开[Stream](../../../ado/reference/ado-api/stream-object-ado.md)对象。  
  
> [!NOTE]
>  中可存储任意数量的位**Stream**对象，仅受系统资源限制。 如果**Stream**包含超出可表示的位数**长**值，**大小**将被截断，因此不能准确表示长度**Stream**。  
  
## <a name="applies-to"></a>适用范围  
 [流对象 (ADO)](../../../ado/reference/ado-api/stream-object-ado.md)  
  
## <a name="see-also"></a>请参阅  
 [Size 属性（ADO 参数）](../../../ado/reference/ado-api/size-property-ado-parameter.md)
