---
title: ParentRow 属性 (ADO) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- ADORecordConstruction::put_ParentRow
- ADORecordConstruction::ParentRow
- ADORecordConstruction::putParentRow
helpviewer_keywords:
- ParentRow property [ADO]
ms.assetid: 5ea8029b-eda4-490b-ae84-2ad036fb582f
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 180ab01d28cb5c6f7715480459eeb12ab6ea81be
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "66703289"
---
# <a name="parentrow-property-ado"></a>ParentRow 属性 (ADO)
设置容器的 OLE DB**行**对象上**ADORecordConstruction**对象，以便行的父变成 ADO**记录**对象。  
  
 只写。  
  
## <a name="syntax"></a>语法  
  
```  
HRESULT put_ParentRow([in] IUnknown* pParent);  
```  
  
## <a name="parameters"></a>Parameters  
 *pParent*  
 行的容器。  
  
## <a name="return-values"></a>返回值  
 此属性方法返回的标准的 HRESULT 值，包括，则为 S_OK 和 E_FAIL。  
  
## <a name="applies-to"></a>适用范围  
 [ADORecordConstruction 接口](../../../ado/reference/ado-api/adorecordconstruction-interface.md)
