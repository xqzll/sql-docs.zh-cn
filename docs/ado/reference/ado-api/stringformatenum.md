---
title: StringFormatEnum | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- StringFormatEnum
helpviewer_keywords:
- StringFormatEnum enumeration [ADO]
ms.assetid: 28f7d1ec-092b-4323-a39d-d3f882c6c81a
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 7225f8a7612f08947720eb2912722dc92b7a2a96
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "66710805"
---
# <a name="stringformatenum"></a>StringFormatEnum
检索时指定的格式[记录集](../../../ado/reference/ado-api/recordset-object-ado.md)作为字符串。  
  
|常量|ReplTest1|Description|  
|--------------|-----------|-----------------|  
|**adClipString**|2|分隔行乘以*RowDelimiter*，按列*ColumnDelimiter*，和 null 值*NullExpr*。 这三个参数的[GetString](../../../ado/reference/ado-api/getstring-method-ado.md)方法是仅对于有效*StringFormat*的**adClipString**。|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC 等效项  
 包： **com.ms.wfc.data**  
  
|常量|  
|--------------|  
|AdoEnums.StringFormat.CLIPSTRING|  
  
## <a name="applies-to"></a>适用范围  
 [GetString 方法 (ADO)](../../../ado/reference/ado-api/getstring-method-ado.md)
