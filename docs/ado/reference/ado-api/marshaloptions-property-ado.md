---
title: MarshalOptions 属性 (ADO) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::MarshalOptions
helpviewer_keywords:
- MarshalOptions property [ADO]
ms.assetid: 390c8abf-133e-40da-8b99-8f748a983e4f
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 69b9b44fc20fe832bffdd4c03536117a626916ac
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "66697292"
---
# <a name="marshaloptions-property-ado"></a>MarshalOptions 属性 (ADO)
指示的哪些记录[记录集](../../../ado/reference/ado-api/recordset-object-ado.md)要封送回服务器。  
  
## <a name="settings-and-return-values"></a>设置和返回值  
 设置或返回[MarshalOptionsEnum](../../../ado/reference/ado-api/marshaloptionsenum.md)值。 默认值是**adMarshalAll**。  
  
## <a name="remarks"></a>备注  
 使用客户端时[记录集](../../../ado/reference/ado-api/recordset-object-ado.md)，到中间层或通过调用封送处理打包并发送接口方法的过程的技术的 Web 服务器的客户端修改的记录写回跨线程或进程边界的参数。 设置**MarshalOptions**修改后的远程数据封送回给中间层或 Web 服务器更新时，属性可以提高性能。  
  
> [!NOTE]
>  **远程数据服务使用情况**仅在客户端上使用此属性**记录集**。  
  
## <a name="applies-to"></a>适用范围  
 [记录集对象 (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>请参阅  
 [MarshalOptions 属性示例 (VB)](../../../ado/reference/ado-api/marshaloptions-property-example-vb.md)   
 [MarshalOptions 属性示例 (VC++)](../../../ado/reference/ado-api/marshaloptions-property-example-vc.md)   
