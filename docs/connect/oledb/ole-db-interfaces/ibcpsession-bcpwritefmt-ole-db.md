---
title: 'Ibcpsession:: Bcpwritefmt (OLE DB) |Microsoft Docs'
description: '使用 ibcpsession:: Bcpwritefmt 将格式文件保存为 xml 或文本格式 (OLE DB)'
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
apiname:
- IBCPSession::BCPWriteFmt (OLE DB)
apitype: COM
helpviewer_keywords:
- BCPWriteFmt method
author: pmasl
ms.author: pelopes
manager: jroth
ms.openlocfilehash: 5d93d2114ff462eddd45fb5520a976d148cc96ac
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "66790838"
---
# <a name="ibcpsessionbcpwritefmt-ole-db"></a>IBCPSession::BCPWriteFmt (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  将每一列的格式信息写入格式化文件。  
  
## <a name="syntax"></a>语法  
  
```  
  
HRESULT BCPWriteFmt(   
      const wchar_t *pwszFormatFile);  
```  
  
## <a name="remarks"></a>Remarks  
 格式化文件指定大容量复制所创建的数据文件的数据格式。 调用 [IBCPSession::BCPColumns](../../oledb/ole-db-interfaces/ibcpsession-bcpcolumns-ole-db.md) 和 [IBCPSession::BCPColFmt](../../oledb/ole-db-interfaces/ibcpsession-bcpcolfmt-ole-db.md) 方法将定义数据文件的格式。 BCPWriteFmt 方法将此定义保存在 pwszFormatFile 参数引用的文件中  。  
  
 BCPWriteFmt 方法可以通过 xml 或文本格式保存格式化文件  。 这必须通过将 BCP_OPTION_XML 控制选项用于 [IBCPSession::BCPControl](../../oledb/ole-db-interfaces/ibcpsession-bcpcontrol-ole-db.md) 方法来指示。  
  
 若要加载已保存的格式化文件，请使用 [IBCPSession::BCPReadFmt](../../oledb/ole-db-interfaces/ibcpsession-bcpreadfmt-ole-db.md) 方法。  
  
## <a name="arguments"></a>参数  
 pwszFormatFile  [in]  
 包含数据文件格式值的文件的路径和文件名。  
  
## <a name="return-code-values"></a>返回代码值  
 S_OK  
 方法成功。  
  
 E_FAIL  
 出现访问接口特定的错误；若要获取详细信息，请使用 [ISQLServerErrorInfo](https://msdn.microsoft.com/library/a8323b5c-686a-4235-a8d2-bda43617b3a1) 接口。  
  
 E_OUTOFMEMORY  
 内存不足错误。  
  
 E_UNEXPECTED  
 意外调用了该方法。 例如，在调用该方法之前，未调用 [IBCPSession::BCPInit](../../oledb/ole-db-interfaces/ibcpsession-bcpinit-ole-db.md) 方法。  
  
## <a name="see-also"></a>另请参阅  
 [IBCPSession &#40;OLE DB&#41;](../../oledb/ole-db-interfaces/ibcpsession-ole-db.md)   
 [执行大容量复制操作](../../oledb/features/performing-bulk-copy-operations.md) 
  
  
