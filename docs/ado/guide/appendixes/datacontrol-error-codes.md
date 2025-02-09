---
title: DataControl 错误代码 |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- errors [ADO], DataControl
- DataControl errors [ADO]
ms.assetid: 293df9d5-e1a2-406d-9107-07bf7cdc6f96
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: fe2a6cc350291ac2304e2f00825bef76e37e75cf
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "66701273"
---
# <a name="datacontrol-object-error-codes"></a>DataControl 对象错误代码
下表列出了[rds。DataControl](../../../ado/reference/rds-api/datacontrol-object-rds.md)对象错误代码。 低两个字节的正十进制转换，显示了完整的错误代码和十六进制值的负十进制转换。

|RDS。DataControl 错误代码|Number|Description|
|---------------------------------|------------|-----------------|
|**IDS_AsyncPending**|4107 -2146824175 0x800A1011|异步操作挂起时，无法执行操作。|
|**IDS_BadInlineTablegram**|4105 -2146824183 0x800A1009|内嵌图表错误。|
|**IDS_CantConnect**|4099 -2146824189 0x800A1003|无法连接到服务器。|
|**IDS_CantCreateObject**|4100 -2146824188 0x800A1004|无法创建业务对象。|
|**IDS_CantFindDataspace**|4102 -2146824186 0x800A1006|数据空间属性不是有效的。|
|**IDS_CantInvokeMethod**|4101 -2146824187 0x800A1005|不能在业务对象上调用方法。|
|**IDS_CrossDomainWarning**|4112 -2146824170 0x800A1016|此页访问另一个域上的数据。 若要允许此操作吗？ 若要避免出现此消息在 Internet Explorer 中的，您可以安全网站到受信任的站点区域上添加**安全**选项卡**Internet 选项**对话框。|
|**IDS_InvalidADCClientVersion**|4106 -2146824176 0x800A1010|无效的 RDS 客户端版本的客户端是比服务器更新。|
|**IDS_INVALIDARG**|5376 -2147019520 0x80071500|一个或多个参数均无效。|
|**IDS_InvalidBindings**|4097 -2146824191 0x800A1001|绑定属性中的错误。|
|**IDS_InvalidParam**|4110 -2146824172 0x800A1014|一个或多个参数均无效。|
|**IDS_NOINTERFACE**|5377 -2147019519 0x80071501|不支持任何此类接口。|
|**IDS_NotReentrant**|4111 -2146824171 0x800A1015|无法执行请求，但继续处理的事件处理程序。|
|**IDS_ObjectNotSafe**|4103 -2146824185 0x800A1007|在此计算机上的安全设置禁止创建业务对象。|
|**IDS_RecordsetNotOpen**|4109 -2146824173 0x800A1013|**记录集**未打开。|
|**IDS_ResetInvalidField**|4108 -2146824174 0x800A1012|中指定的列**SortColumn**或**FilterColumn**不存在。|
|**IDS_RowsetNotUpdateable**|4104 -2146824184 0x800A1008|行集不可更新。|
|**IDS_UnexpectedError**|4351 -2146823937 0x800A10FF|出现意外的错误。|
|**IDS_UpdatesFailed**|4098 -2146824190 0x800A1002|无法更新数据库。|
|**IDS_URLMONNotFound**|4119 -2146824169 0x800A1017|DataControl **URL**属性所需的系统文件 Urlmon.dll，找不到。|

## <a name="see-also"></a>请参阅
 [DataControl 对象 (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)
