---
title: CommandType 属性 (ADO) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Command15::CommandType
helpviewer_keywords:
- CommandType property [ADO]
ms.assetid: ca44809c-8647-48b6-a7fb-0be70a02f53e
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 5fde8adfb1b3f78e8dd0d047f8b100ddada4608c
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "66698683"
---
# <a name="commandtype-property-ado"></a>CommandType 属性 (ADO)
指示的类型[命令](../../../ado/reference/ado-api/command-object-ado.md)对象。  
  
## <a name="settings-and-return-values"></a>设置和返回值  
 设置或返回一个或多个[CommandTypeEnum](../../../ado/reference/ado-api/commandtypeenum.md)值。  
  
> [!NOTE]
>  不要使用**CommandTypeEnum**的值**adCmdFile**或**adCmdTableDirect**与**CommandType**。 这些值仅用作选项与[开放](../../../ado/reference/ado-api/open-method-ado-recordset.md)并[再次查询](../../../ado/reference/ado-api/requery-method.md)方法[记录集](../../../ado/reference/ado-api/recordset-object-ado.md)。  
  
## <a name="remarks"></a>备注  
 使用**CommandType**属性来优化计算[CommandText](../../../ado/reference/ado-api/commandtext-property-ado.md)属性。  
  
 如果**CommandType**属性值设置为默认值为**adCmdUnknown**，您可能会遇到性能降低的程度，因为 ADO 必须进行到提供程序的调用，以确定如果**CommandText**属性是一个 SQL 语句、 存储的过程或表名称。 如果您知道使用哪种类型的命令，设置**CommandType**属性指示 ADO 来直接转到相关代码。 如果**CommandType**属性中的命令类型不匹配**CommandText**属性时，发生错误时调用[Execute](../../../ado/reference/ado-api/execute-method-ado-command.md)方法。  
  
## <a name="applies-to"></a>适用范围  
 [命令对象 (ADO)](../../../ado/reference/ado-api/command-object-ado.md)  
  
## <a name="see-also"></a>请参阅  
 [ActiveConnection、 CommandText、 CommandTimeout、 CommandType、 大小和方向属性示例 (VB)](../../../ado/reference/ado-api/activeconnection-commandtext-commandtimeout-commandtype-size-example-vb.md)   
 [ActiveConnection、 CommandText、 CommandTimeout、 CommandType、 大小和方向属性示例 （VC + +）](../../../ado/reference/ado-api/activeconnection-commandtext-commandtimeout-commandtype-size-example-vc.md)   
 [ActiveConnection、 CommandText、 CommandTimeout、 CommandType、 大小和方向属性示例 (JScript)](../../../ado/reference/ado-api/activeconnection-commandtext-timeout-type-size-example-jscript.md)
