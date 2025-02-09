---
title: InternetTimeout 属性 (RDS) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- InternetTimeout property [ADO]
ms.assetid: 4d1c8892-4bbc-4e71-bf4b-ba52c0ea9549
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 6a5886ae206f3b16f30da406a8ccc42cc8cba7a0
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "66712461"
---
# <a name="internettimeout-property-rds"></a>InternetTimeout 属性 (RDS)
指示要请求超时之前等待毫秒的数。  
  
> [!IMPORTANT]
>  从 Windows 8 和 Windows Server 2012 开始，不再在 Windows 操作系统中包含 RDS 服务器组件 (请参阅 Windows 8 和[Windows Server 2012 兼容性指南](https://www.microsoft.com/download/details.aspx?id=27416)以了解详细信息)。 将 Windows 的未来版本中删除 RDS 客户端组件。 请避免在新的开发工作中使用该功能，并着手修改当前还在使用该功能的应用程序。 使用 RDS 的应用程序应迁移到[WCF 数据服务](https://go.microsoft.com/fwlink/?LinkId=199565)。  
  
## <a name="settings-and-return-values"></a>设置和返回值  
 设置或返回**长**超时值，该值表示一个请求之前的毫秒数。  
  
## <a name="remarks"></a>备注  
 此属性仅适用于使用 HTTP 或 HTTPS 协议发送的请求。  
  
 在三层环境中的请求可能需要几分钟才能执行。 此属性用于指定为长时间运行的请求的更多时间。  
  
## <a name="applies-to"></a>适用范围  
  
|||  
|-|-|  
|[DataControl 对象 (RDS)](../../../ado/reference/rds-api/datacontrol-object-rds.md)|[DataSpace 对象 (RDS)](../../../ado/reference/rds-api/dataspace-object-rds.md)|  
  
## <a name="see-also"></a>请参阅  
 [InternetTimeout 属性示例 (VB)](../../../ado/reference/rds-api/internettimeout-property-example-vb.md)   
 [InternetTimeout 属性示例 (VC++)](../../../ado/reference/rds-api/internettimeout-property-example-vc.md)   
 

