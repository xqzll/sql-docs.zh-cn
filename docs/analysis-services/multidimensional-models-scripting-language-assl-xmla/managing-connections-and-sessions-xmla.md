---
title: 管理连接和会话 (XMLA) |Microsoft Docs
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: ad9be579d37cc8c75375b373ae8ecb624067ad50
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "63261590"
---
# <a name="managing-connections-and-sessions-xmla"></a>管理连接和会话 (XMLA)
  *有状态性*是在此期间服务器将保留标识和上下文的方法调用之间的客户端的条件。 *无状态*是在此期间服务器不会记住标识和上下文的客户端方法调用完成后一情况。  
  
 若要提供有状态，XML for Analysis (XMLA) 支持*会话*允许一系列语句一起执行。 例如，创建要在后续查询中使用的计算成员就是这样的一系列语句。  
  
 通常，XMLA 中的会话遵循 OLE DB 2.6 规范中所述的以下行为：  
  
-   会话定义事务和命令上下文范围。  
  
-   可以在一个会话的上下文中运行多个命令。  
  
-   支持 XMLA 上下文中的事务是通过使用发送的特定于提供程序的命令[Execute](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-execute)方法。  
  
 XMLA 定义了一种方法，用于在 Web 环境中以与分布式创作和版本管理 (DAV) 协议所使用的方法类似的模式支持会话，以便在松散耦合环境中实现锁定。 此实现遵循 DAV，允许访问接口由于各种原因而终止会话（例如超时或连接错误）。 支持会话时，Web 服务必须能够知道必须重新启动的已中断命令集，并准备好进行处理。  
  
 万维网联盟 (W3C) 简单对象访问协议 (SOAP) 规范建议在 SOAP 消息的最前面使用 SOAP 标头以构建新协议。 下表列出了 XMLA 定义的用于启动、维护和关闭会话的 SOAP 标头元素和属性。  
  
|SOAP 标头|Description|  
|-----------------|-----------------|  
|BeginSession|此标头请求访问接口创建新会话。 访问接口应通过以下方式进行响应：构造新会话并将会话 ID 作为 SOAP 响应中 Session 标头的一部分返回。|  
|SessionId|值区域包含会话 ID，在该会话此后的每个方法调用中都必须使用此 ID。 SOAP 响应中的访问接口会发送此标记，客户端也必须在每个 Session 标头元素中发送此属性。|  
|Session|对于会话中发生的每个方法调用，都必须使用此标头，此标头的值区域中必须包含会话 ID。|  
|EndSession|若要终止会话，请使用此标头。 值区域中必须包含会话 ID。|  
  
> [!NOTE]  
>  会话 ID 并不保证会话保持有效。 如果会话过期 （例如，如果在超时或连接已丢失），可以选择提供程序终止并回滚该会话的操作。 因此，来自客户端的对会话 ID 的所有后续方法调用都将失败，返回错误以通知会话无效。 客户端应处理此情况，并准备从头开始重新发送这些会话方法调用。  
  
## <a name="legacy-code-example"></a>旧代码示例  
 下面的示例演示如何支持会话。  
  
1.  若要开始会话，请在 SOAP 中将 BeginSession 标头添加到来自客户端的出站 XMLA 方法调用中。 值区域最初是空白的，因为会话 ID 还是未知的。  
  
    ```  
    <SOAP-ENV:Envelope  
       xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/"  
       SOAP-ENV:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/">  
       <SOAP-ENV:Header>  
          <XA:BeginSession  
             xmlns:XA="urn:schemas-microsoft-com:xml-analysis"  
             xsi:type="xsd:int"  
             mustUnderstand="1"/>  
       </SOAP-ENV:Header>  
       <SOAP-ENV:Body>  
          ...<!-- Discover or Execute call goes here.-->  
       </SOAP-ENV:Body>  
    </SOAP-ENV:Envelope>  
    ```  
  
2.  从提供程序的 SOAP 响应消息将会话 ID 包含在返回标头区域中，使用 XMLA 标头标记\<SessionId >。  
  
    ```  
    <SOAP-ENV:Header>  
       <XA:Session  
          xmlns:XA="urn:schemas-microsoft-com:xml-analysis"  
          SessionId="581"/>  
    </SOAP-ENV:Header>  
    ```  
  
3.  会话中的每个方法调用都必须添加 Session 标头，其中包含从访问接口返回的会话 ID。  
  
    ```  
    <SOAP-ENV:Header>  
       <XA:Session  
          xmlns:XA="urn:schemas-microsoft-com:xml-analysis"  
          mustUnderstand="1"  
          SessionId="581"/>  
    </SOAP-ENV:Header>  
    ```  
  
4.  在会话完成后， \<EndSession > 使用标记时，包含相关的会话 ID 值。  
  
    ```  
    <SOAP-ENV:Header>  
       <XA:EndSession  
          xmlns:XA="urn:schemas-microsoft-com:xml-analysis"  
          xsi:type="xsd:int"  
          mustUnderstand="1"  
          SessionId="581"/>  
    </SOAP-ENV:Header>  
    ```  
  
## <a name="see-also"></a>请参阅  
 [在 Analysis Services 中使用 XMLA 开发](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md)  
  
  
