---
title: 'Issasynchstatus:: Abort (OLE DB) |Microsoft Docs'
description: ISSAsynchStatus::Abort (OLE DB)
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
apiname:
- ISSAsynchStatus::Abort (OLE DB)
apitype: COM
helpviewer_keywords:
- Abort method
author: pmasl
ms.author: pelopes
manager: jroth
ms.openlocfilehash: 36a8f97580176b4999d8429fb18c9b20da9285d1
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "66789740"
---
# <a name="issasynchstatusabort-ole-db"></a>ISSAsynchStatus::Abort (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  取消异步执行的操作。  
  
## <a name="syntax"></a>语法  
  
```  
  
HRESULT Abort(  
        HCHAPTER hChapter,  
        DBASYNCHOP eOperation);  
```  
  
## <a name="arguments"></a>参数  
 hChapter[in]   
 要中止其操作的章节的句柄。 如果所调用的对象不是行集对象或者操作不应用于章节，则调用方必须将 hChapter 设置为 DB_NULL_HCHAPTER  。  
  
 eOperation[in]   
 要中止的操作。 应使用以下值：  
  
 DBASYNCHOP_OPEN - 要取消的请求应用于行集的异步打开或填充，或应用于数据源对象的异步初始化。  
  
## <a name="return-code-values"></a>返回代码值  
 S_OK  
 已处理取消异步操作的请求。 这并不保证操作本身已取消。 若要确定操作是否已取消，使用者应当调用 [ISSAsynchStatus::GetStatus](../../oledb/ole-db-interfaces/issasynchstatus-getstatus-ole-db.md)，并检查是否有 DB_E_CANCELED；但是，它可能不会正好在下一次调用中返回。  
  
 DB_E_CANTCANCEL  
 异步操作无法取消。  
  
 DB_E_CANCELED  
 中止异步操作的请求已在通知期间取消。 操作仍然正在异步执行。  
  
 E_FAIL  
 发生了特定于访问接口的错误。  
  
 E_INVALIDARG  
 *HChapter*参数不是 DB_NULL_HCHAPTER 或者*eOperation*并不是 DBASYNCH_OPEN。  
  
 E_UNEXPECTED  
 已对尚未调用或尚未完成 IDBInitialize::Initialize 的数据源对象调用 ISSAsynchStatus::Abort   。  
  
 已对数据源对象调用 ISSAsynchStatus::Abort，此前，该对象已调用 IDBInitialize::Initialize 但随后在初始化或超时之前取消   。数据源对象仍未初始化。  
  
 已对以前调用了 ITransaction::Commit 或 ITransaction::Abort 并在提交或中止后处于僵停状态的行集调用 ISSAsynchStatus::Abort    。  
  
 已对在初始化阶段异步取消的行集调用 ISSAsynchStatus::Abort  。 该行集处于僵停状态。  
  
## <a name="remarks"></a>Remarks  
 中止行集或数据源对象的初始化可能使行集或数据源对象最后处于僵停状态，以至于除了 IUnknown 方法以外的所有方法都返回 E_UNEXPECTED  。 发生这种情况时，使用者的唯一可能操作是释放行集或数据源对象。  
  
 如果调用 ISSAsynchStatus::Abort 并为 eOperation 传递除了 DBASYNCHOP_OPEN 以外的值，将返回 S_OK   。 这并不意味着操作已完成或取消。  
  
## <a name="see-also"></a>另请参阅  
 [执行异步操作](../../oledb/features/performing-asynchronous-operations.md)  
  
  
