---
title: 'RecordsetEvents (VisualC++使用 #import 语法索引) |Microsoft Docs'
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
dev_langs:
- C++
helpviewer_keywords:
- RecordsetEvents collection [ADO]
ms.assetid: b7021f11-8242-4e9f-92e9-1a4472673fb1
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: f5b8da9f851e6171b2149d57da200d093d98d0ee
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "66711710"
---
# <a name="recordsetevents-visual-c-syntax-index-with-import"></a>RecordsetEvents (VisualC++使用 #import 语法索引)
## <a name="events"></a>事件  
  
```  
HRESULT WillChangeField( long cFields, const  
    _variant_t & Fields, enum     EventStatusEnum * adStatus, struct  
    _Recordset * pRecordset );  
  
HRESULT FieldChangeComplete( long cFields, const  
    _variant_t & Fields,     struct Error * pError, enum EventStatusEnum  
    * adStatus, struct     _Recordset * pRecordset );  
  
HRESULT WillChangeRecord( enum EventReasonEnum  
    adReason, long cRecords,     enum EventStatusEnum * adStatus, struct  
    _Recordset * pRecordset );  
  
HRESULT RecordChangeComplete( enum EventReasonEnum  
    adReason, long     cRecords, struct Error * pError, enum  
    EventStatusEnum * adStatus,     struct _Recordset * pRecordset );  
  
HRESULT WillChangeRecordset( enum EventReasonEnum  
    adReason, enum     EventStatusEnum * adStatus, struct _Recordset *  
    pRecordset );  
  
HRESULT RecordsetChangeComplete( enum  
    EventReasonEnum adReason, struct     Error * pError, enum  
    EventStatusEnum * adStatus, struct _Recordset *     pRecordset );  
  
HRESULT WillMove( enum EventReasonEnum adReason, enum  
    EventStatusEnum *     adStatus, struct _Recordset * pRecordset );  
  
HRESULT MoveComplete( enum EventReasonEnum adReason, struct  
    Error *     pError, enum EventStatusEnum * adStatus, struct  
    _Recordset * pRecordset );  
  
HRESULT EndOfRecordset( VARIANT_BOOL * fMoreData, enum  
    EventStatusEnum *     adStatus, struct _Recordset * pRecordset );  
  
HRESULT FetchProgress( long Progress, long MaxProgress,  
    enum     EventStatusEnum * adStatus, struct _Recordset * pRecordset );  
  
HRESULT FetchComplete( struct Error * pError, enum  
    EventStatusEnum *     adStatus, struct _Recordset * pRecordset );  
```
