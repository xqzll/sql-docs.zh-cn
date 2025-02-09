---
title: 在 Windows 2000 上配置 RDS |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/09/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- RDS configuration [ADO], Windows 2000
ms.assetid: ef37e858-c05f-4f52-a65f-3ce6037e0d03
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: a17ed52371a6c7eae057332a3e80bd215131d287
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "66704349"
---
# <a name="configuring-rds-on-windows-2000"></a>在 Windows 2000 上配置 RDS
如果您遇到获取 RDS 才能正常工作后升级到 Windows 2000 的问题，请按照下列步骤来解决此问题：  
  
1.  请确保 World Wide Web 发布服务通过使用 Internet 资源管理器导航到 https:// 服务器运行第一个。 如果不能访问 Web 服务器以这种方式，请打开命令提示符并输入以下命令，"NET 启动 W3SVC"。  
  
2.  在开始菜单中，选择运行。 键入 msdfmap.ini，然后单击确定以在记事本中打开 msdfmap.ini 文件。 检查 [连接默认值] 部分中，并访问参数设置为 NOACCESS，如果将其更改为只读。  
  
3.  使用 RegEdit 实用程序，导航到"HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DataFactory\HandlerInfo"，并确保**HandlerRequired**设置为 0 并**DefaultHandler**是""(Null 字符串)。  
  
     **请注意**如果对注册表的此部分进行任何更改，必须停止并通过输入以下命令在命令提示符下重新启动 World Wide Web 发布服务："NET STOP W3SVC"和"NET 启动 W3SVC"。  
  
4.  使用 RegEdit 实用程序，导航到"HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\W3SVC\Parameters\ADCLaunch"注册表中并验证是否有一个名为密钥**提高**。 如果没有，则创建它。  
  
5.  使用 Internet 服务管理器，找到默认的 Web 站点，并查看 MSADC 虚拟根目录的属性。 检查目录安全/IP 地址和域名限制。 如果选中"访问被拒绝"，然后选择"授予"。  
  
 务必尝试重新启动服务器，如果更改不会显示为解决在第一个问题。  
  
> [!IMPORTANT]
>  从 Windows 8 和 Windows Server 2012 开始，不再在 Windows 操作系统中包含 RDS 服务器组件 (请参阅 Windows 8 和[Windows Server 2012 兼容性指南](https://www.microsoft.com/download/details.aspx?id=27416)以了解详细信息)。 将 Windows 的未来版本中删除 RDS 客户端组件。 请避免在新的开发工作中使用该功能，并着手修改当前还在使用该功能的应用程序。 使用 RDS 的应用程序应迁移到[WCF 数据服务](https://go.microsoft.com/fwlink/?LinkId=199565)。从 Windows 8 和 Windows Server 2012 开始，RDS 服务器组件不再包含在 Windows 操作系统中。 将使用到 RDS 的应用程序迁移[WCF 数据服务](https://go.microsoft.com/fwlink/?LinkId=199565)。  
  
## <a name="see-also"></a>请参阅  
 [RDS 基础知识](../../../ado/guide/remote-data-service/rds-fundamentals.md)


