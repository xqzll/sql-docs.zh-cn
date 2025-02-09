---
title: ActualSize 和 DefinedSize 属性示例 (JScript) |Microsoft Docs
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
- ActualSize property [ADO], JScript example
- DefinedSize property [ADO], JScript example
ms.assetid: 23575e70-2304-43b4-b8be-99d9a6842589
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: eba72bf4ddf9a67b85435cec924897b0d0fbc17c
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "66704012"
---
# <a name="actualsize-and-definedsize-properties-example-jscript"></a>ActualSize 和 DefinedSize 属性示例 (JScript)
此示例使用[ActualSize](../../../ado/reference/ado-api/actualsize-property-ado.md)并[DefinedSize](../../../ado/reference/ado-api/definedsize-property.md)要显示的定义的大小和实际大小字段的属性。 剪切并粘贴到记事本或其他文本编辑器，下面的代码，然后将其保存为**ActualSizeJS.asp**。  
  
```  
<!-- BeginActualSizeJS -->  
<%@LANGUAGE="JScript" %>  
<%// use this meta tag instead of adojavas.inc%>  
<!--METADATA TYPE="typelib" uuid="00000205-0000-0010-8000-00AA006D2EA4" -->  
<html>  
  
<head>  
    <title>ActualSize and DefinedSize Properties Example (JScript)</title>  
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
</head>  
  
<body bgcolor="White">  
  
<h1>ADO ActualSize and DefinedSize Properties (JScript)</h1>  
<%  
    // connection and recordset variables  
    var Cnxn = Server.CreateObject("ADODB.Connection")  
    var strCnxn = "Provider='sqloledb';Data Source=" + Request.ServerVariables("SERVER_NAME") + ";" +  
            "Initial Catalog='Northwind';Integrated Security='SSPI';";  
    var rsSuppliers = Server.CreateObject("ADODB.Recordset");  
    // display variables  
    var fld, strMessage;          
  
    try  
    {  
        // open connection  
        Cnxn.Open(strCnxn);  
  
        // Open a recordset on the stores table      
        rsSuppliers.Open("Suppliers", strCnxn);  
  
        // build table headers  
        Response.Write("<table>");  
        Response.Write('<tr class="thead2"><th>Field Value</th>');  
        Response.Write("<th>Defined Size</th>");  
        Response.Write("<th>Actual Size</th></tr>");  
  
        while (!rsSuppliers.EOF)  
        {  
            // start a new line  
            strMessage = '<tr class="tbody">';  
  
            // Display the contents of the chosen field with  
            // its defined size and actual size  
            fld = rsSuppliers("CompanyName");  
            strMessage += '<td align="left">' + fld.Value + "</td>"   
            strMessage += "<td>" + fld.DefinedSize + "</td>";  
            strMessage += "<td>" + fld.ActualSize + "</td>";  
  
            // end the line  
            strMessage += "</tr>";  
  
            // display data  
            Response.Write(strMessage);  
  
            // get next record  
            rsSuppliers.MoveNext;  
  
        }  
         // close the table  
        Response.Write("</table>");  
    }  
    catch (e)  
    {  
        Response.Write(e.message);  
    }  
    finally  
    {  
        // clean up  
        if (rsSuppliers.State == adStateOpen)  
            rsSuppliers.Close;  
        if (Cnxn.State == adStateOpen)  
            Cnxn.Close;  
        rsSuppliers = null;  
        Cnxn = null;  
    }  
%>  
  
</body>  
  
</html>  
<!-- EndActualSizeJS -->  
```  
  
## <a name="see-also"></a>请参阅  
 [ActualSize 属性 (ADO)](../../../ado/reference/ado-api/actualsize-property-ado.md)   
 [DefinedSize 属性](../../../ado/reference/ado-api/definedsize-property.md)   
 [字段对象](../../../ado/reference/ado-api/field-object.md)
