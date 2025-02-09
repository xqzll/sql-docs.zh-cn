---
title: 用于 Internet 发布的 Microsoft OLE DB 提供程序 |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 11/08/2018
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- OLE DB provider for Internet publishing [ADO]
- providers [ADO], OLE DB provider for Internet publishing
- Internet Publishing provider [ADO]
ms.assetid: 66a208d9-b580-4655-a41e-1d36e5b5bfca
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 48c6e95a644c643721a7cb1c6f15c5eaf1e5a995
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "66701394"
---
# <a name="microsoft-ole-db-provider-for-internet-publishing-overview"></a>Microsoft OLE DB 提供程序用于 Internet 发布概述
Microsoft OLE DB 访问接口用于 Internet 发布允许 ADO 访问由 Microsoft FrontPage 或 Microsoft Internet 信息服务器提供服务的资源。 资源包括 web 源代码文件，例如 HTML 文件或 Windows 2000 web 文件夹。

## <a name="connection-string-parameters"></a>连接字符串参数
 若要连接到此提供程序，请设置*提供程序*的参数[ConnectionString](../../../ado/reference/ado-api/connectionstring-property-ado.md)属性设置为：

```vb
MSDAIPP.DSO
```

 此值还可以设置或读取使用[提供程序](../../../ado/reference/ado-api/provider-property-ado.md)属性。

## <a name="typical-connection-string"></a>典型的连接字符串
 此提供程序的典型的连接字符串是：

```vb
"Provider=MSDAIPP.DSO;Data Source=ResourceURL;User ID=MyUserID;Password=MyPassword;"
```

 -或-

```vb
"URL=ResourceURL;User ID=MyUserID;Password=MyPassword;"
```

 该字符串包含这些关键字：

|关键字|Description|
|-------------|-----------------|
|**提供程序**|指定用于 Internet 发布的 OLE DB 访问接口。|
|**数据源**-或- **URL**|指定的文件或目录已发布的 Web 文件夹中的 URL。|
|**用户 ID**|指定用户名称。|
|**密码**|指定用户密码。|

> [!NOTE]
>  如果您要连接到的数据源提供程序支持 Windows 身份验证，则应指定**Trusted_Connection = yes**或**Integrated Security = SSPI**而不是用户 ID 和密码在连接字符串中的信息。

 如果您设置*ResourceURL*值从"URL ="在连接字符串为无效值，默认情况下 Internet 发布提供程序引发一个对话框，提示输入有效的值。 这是应用程序的中间层中的组件的意外行为，因为暂停程序执行，直到清除对话框中，客户端似乎会冻结，因为它不从组件接收响应。

> [!NOTE]
>  如果 MSDAIPP。作为提供程序，使用的值显式指定 DSO*提供程序*连接字符串关键字或**提供程序**属性，不能使用"URL ="连接字符串中。 如果这样做，将会出错。 本主题中所示，只需指定的 URL[用于 Internet 发布针对 OLE DB 访问接口使用 ADO](../../../ado/guide/data/the-ole-db-provider-for-internet-publishing.md)。

## <a name="see-also"></a>请参阅
 [Internet 发布方案](../../../ado/guide/data/internet-publishing-scenario.md) [Internet 发布的 OLE DB 访问接口](../../../ado/guide/data/the-ole-db-provider-for-internet-publishing.md)
