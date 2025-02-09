---
title: ODBC 错误代码 （Visual FoxPro ODBC 驱动程序） |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Visual FoxPro ODBC driver [ODBC], error codes
- Visual FoxPro error codes
- error messages [ODBC], Visual FoxPro ODBC driver
- SQLSTATE [ODBC]
- FoxPro ODBC driver [ODBC], error codes
ms.assetid: 9b4251f2-6fa6-49df-8abf-7cc1cc35d1c8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: af6fb682e6179f99096a86d93e3f02c7b59cb91f
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "63244608"
---
# <a name="odbc-error-codes-visual-foxpro-odbc-driver"></a>ODBC 错误代码（Visual FoxPro ODBC 驱动程序）
下表列出了 Visual FoxPro 错误代码映射到 ODBC 错误代码 SQLSTATE 值。 映射的 SQLSTATE 值来自[SQLExecDirect](../../odbc/microsoft/sqlexecdirect-visual-foxpro-odbc-driver.md)并[SQLPrepare](../../odbc/microsoft/sqlprepare-visual-foxpro-odbc-driver.md)。 从其他 ODBC API 的其他任何 SQLSTATE 值映射，因为**SQLExecDirect**并**SQLPrepare**是访问 Visual FoxPro 引擎的唯一函数。  
  
 ODBC 错误代码的详细信息，请参阅[附录 a:ODBC 错误代码](../../odbc/reference/appendixes/appendix-a-odbc-error-codes.md)，请在*ODBC 程序员参考*。  
  
|SQLSTATE|Visual FoxPro 错误代码|  
|--------------|------------------------------|  
|S1001|149<br /><br /> 150<br /><br /> 182<br /><br /> 202<br /><br /> 308|  
|1004|159|  
|37000|132<br /><br /> 200<br /><br /> 219<br /><br /> 221<br /><br /> 222<br /><br /> 227<br /><br /> 229<br /><br /> 230<br /><br /> 498<br /><br /> 499<br /><br /> 713<br /><br /> 901|  
|22005|301<br /><br /> 302|  
|22012|307|  
|23000|581<br /><br /> 583<br /><br /> 884<br /><br /> 886<br /><br /> 988|  
|S0001|121<br /><br /> 571|  
|S0002|173<br /><br /> 120<br /><br /> 123<br /><br /> 295<br /><br /> 562<br /><br /> 563<br /><br /> 802|  
|S0012|683|  
|S0021|156<br /><br /> 712|  
|S0022|158<br /><br /> 806|  
|S1000|100<br /><br /> 101<br /><br /> 102<br /><br /> 105<br /><br /> 107<br /><br /> 109<br /><br /> 110<br /><br /> 111<br /><br /> 113<br /><br /> 114<br /><br /> 115<br /><br /> 118<br /><br /> 119<br /><br /> 125<br /><br /> 133<br /><br /> 135<br /><br /> 136<br /><br /> 137<br /><br /> 145<br /><br /> 146<br /><br /> 171<br /><br /> 173<br /><br /> 177<br /><br /> 201<br /><br /> 205<br /><br /> 239<br /><br /> 240<br /><br /> 252<br /><br /> 257<br /><br /> 296<br /><br /> 305<br /><br /> 407<br /><br /> 410<br /><br /> 462<br /><br /> 502<br /><br /> 503<br /><br /> 520<br /><br /> 538<br /><br /> 550<br /><br /> 561<br /><br /> 567<br /><br /> 570<br /><br /> 575<br /><br /> 578<br /><br /> 580<br /><br /> 585<br /><br /> 602<br /><br /> 702<br /><br /> 705<br /><br /> 707<br /><br /> 708<br /><br /> 718<br /><br /> 750<br /><br /> 872<br /><br /> 879<br /><br /> 887<br /><br /> 888<br /><br /> 912<br /><br /> 914<br /><br /> 915<br /><br /> 918<br /><br /> 922<br /><br /> 923<br /><br /> 947<br /><br /> 976<br /><br /> 999|
