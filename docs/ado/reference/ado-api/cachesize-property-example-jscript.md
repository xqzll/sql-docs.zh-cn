---
title: CacheSize 属性示例 (JScript) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
dev_langs:
- JScript
helpviewer_keywords:
- CacheSize property [ADO], JScript example
ms.assetid: 3675f641-b4b1-48ff-ba33-8d9ea064cd04
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 980c9620348f6aaa3d96a975a686484ffe36de39
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "66718523"
---
# <a name="cachesize-property-example-jscript"></a>CacheSize 属性示例 (JScript)
此示例使用[CacheSize](../../../ado/reference/ado-api/cachesize-property-ado.md)属性显示的操作的性能差别执行具有和没有 30 记录缓存。 剪切并粘贴到记事本或其他文本编辑器，下面的代码，然后将其保存为**CacheSizeJS.asp**。  
  
```  
<!-- BeginCacheSizeJS -->  
<%@ Language="JScript" %>  
<%// use this meta tag instead of adojavas.inc%>  
<!--METADATA TYPE="typelib" uuid="00000205-0000-0010-8000-00AA006D2EA4" -->  
  
<HTML>  
<HEAD>  
<title>CacheSize Property Example (JScript)</title>  
<style>  
<!--  
body {  
   font-family: 'Verdana','Arial','Helvetica',sans-serif;  
   BACKGROUND-COLOR:white;  
   COLOR:black;  
    }  
.thead2 {  
   background-color: #800000;   
   font-family: 'Verdana','Arial','Helvetica',sans-serif;   
   font-size: x-small;  
   color: white;  
   }  
.tbody {   
   text-align: center;  
   background-color: #f7efde;  
   font-family: 'Verdana','Arial','Helvetica',sans-serif;   
   font-size: x-small;  
    }  
-->  
</style>  
</HEAD>  
<BODY>  
<h1>CacheSize Property Example (JScript)</h1>  
<%  
    // connection and recordset variables  
    var Cnxn = Server.CreateObject("ADODB.Connection")  
    var strCnxn = "Provider='sqloledb';Data Source=" + Request.ServerVariables("SERVER_NAME") + ";" +  
            "Initial Catalog='Northwind';Integrated Security='SSPI';";  
    var rsCustomer = Server.CreateObject("ADODB.Recordset");  
    // caching variables  
    var Now = new Date();  
    var Start = Now.getTime();  
    var End, Cache, NoCache  
  
    try  
    {  
        // open connection  
        Cnxn.Open(strCnxn)  
  
        // open a recordset on the Employee table using client-side cursor  
        rsCustomer.CursorLocation = adUseClient;  
        rsCustomer.Open("Customers", strCnxn);  
  
        // loop through the recordset 20 times  
        for (var i=1; i<=20; i++)  
        {  
            rsCustomer.MoveFirst();  
            while (!rsCustomer.EOF)  
            {  
                // do something with the record  
                var strTemp = new String(rsCustomer("CompanyName"));  
                rsCustomer.MoveNext();  
            }  
        }  
  
        Now = new Date();  
        End = Now.getTime();  
        NoCache = End - Start;  
  
        // cache records in groups of 30  
        rsCustomer.MoveFirst();  
        rsCustomer.CacheSize = 30;  
  
        Now = new Date();  
        Start = Now.getTime();  
  
        // loop through the recordset 20 times  
        for (var i=1; i<=20; i++)  
        {  
            rsCustomer.MoveFirst();  
            while (!rsCustomer.EOF)  
            {  
                // do something with the record  
                var strTemp = new String(rsCustomer("CompanyName"));  
                rsCustomer.MoveNext();  
            }  
        }  
  
        Now = new Date();  
        End = Now.getTime();  
        var Cache = End - Start;  
    }  
    catch (e)  
    {  
        Response.Write(e.message);  
    }  
    finally  
    {  
        // clean up  
        if (rsCustomer.State == adStateOpen)  
            rsCustomer.Close;  
        if (Cnxn.State == adStateOpen)  
            Cnxn.Close;  
        rsCustomer = null;  
        Cnxn = null;  
    }  
%>  
  
    <table border="2">  
        <tr class="thead2">  
            <th>No Cache</th>  
            <th>30 Record Cache</th>  
        </tr>  
        <tr class="tbody">  
            <td><%=NoCache%></td>  
            <td><%=Cache%></td>  
        </tr>  
    </table>  
  
</BODY>  
</HTML>  
<!-- EndCacheSizeJS -->  
```  
  
## <a name="see-also"></a>请参阅  
 [CacheSize 属性 (ADO)](../../../ado/reference/ado-api/cachesize-property-ado.md)   
 [记录集对象 (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)
