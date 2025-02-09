---
title: Datetime 数据类型更改 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- time data type [ODBC]
- datetime data types [ODBC]
- date data type [ODBC]
- backward compatibility [ODBC], datetime data types
- timestamp data type [ODBC]
- compatibility [ODBC], datetime data types
ms.assetid: c38c79f9-8bb0-4633-ac86-542366c09a95
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 56e0c7d633c6e15b1958d370e8d69c08505edbb6
ms.sourcegitcommit: 56b963446965f3a4bb0fa1446f49578dbff382e0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/11/2019
ms.locfileid: "67793842"
---
# <a name="datetime-data-type-changes"></a>Datetime 数据类型更改
在 ODBC *3.x*、 的标识符的日期、 时间和时间戳 SQL 数据类型已更改从 SQL_DATE、 SQL_TIME 和 SQL_TIMESTAMP (的实例，并用 **#define** 9、 10 和 11 的标头文件中) 到 SQL_TYPE_DATE、 SQL_TYPE_TIME 和 SQL_TYPE_TIMESTAMP (的实例，并用 **#define** 91、 92 和 93 的标头文件中)，分别。 相应的 C 类型标识符都更改 SQL_C_DATE、 SQL_C_TIME 和 SQL_C_TIMESTAMP SQL_C_TYPE_DATE、 SQL_C_TYPE_TIME，和 SQL_C_TYPE_TIMESTAMP，分别。  
  
 ODBC 中的 SQL 日期时间数据类型返回的列的大小和小数位数*3.x*精度和小数位数相同在 ODBC 中为其返回的是*2.x*。 这些值是不同于 SQL_DESC_PRECISION 和 SQL_DESC_SCALE 描述符字段中的值。 (有关详细信息，请参阅[列的大小、 十进制数字、 传输八位字节长度和显示大小](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md)。)  
  
 这些更改会影响**SQLDescribeCol**， **SQLDescribeParam**，并**SQLColAttribute**;**SQLBindCol**， **SQLBindParameter**，并**SQLGetData**; 并且**SQLColumns**， **SQLGetTypeInfo**， **SQLProcedureColumns**， **SQLStatistics**，并且**SQLSpecialColumns**。  
  
 下表显示如何 ODBC *3.x*驱动程序管理器执行的输入中的日期、 时间和时间戳 C 数据类型映射*TargetType*自变量的**SQLBindCol**并**SQLGetData**中或在*ValueType*自变量**SQLBindParameter**。  
  
|数据类型<br /><br /> 输入代码|*2.x*到应用<br /><br /> *2.x* driver|*2.x*到应用<br /><br /> *3.x* driver|*3.x*到应用<br /><br /> *2.x* driver|*3.x*到应用<br /><br /> *3.x* driver|  
|--------------------------------|-----------------------------------|-----------------------------------|-----------------------------------|-----------------------------------|  
|SQL_C_DATE (9)|无映射|SQL_C_TYPE_DATE (91)|无映射 [1]|SQL_C_TYPE_DATE (91)|  
|SQL_C_TYPE_DATE (91)|错误 （从数据挖掘）|错误 （从数据挖掘）|SQL_C_DATE (9)|[2] 没有映射|  
|SQL_C_TIME (10)|无映射|SQL_C_TYPE_TIME (92)|无映射 [1]|SQL_C_TYPE_TIME (92)|  
|SQL_C_TYPE_TIME (92)|错误 （从数据挖掘）|错误 （从数据挖掘）|SQL_C_TIME (10)|[2] 没有映射|  
|SQL_C_TIMESTAMP (11)|无映射|SQL_C_TYPE_TIMESTAMP (93)|无映射 [1]|SQL_C_TYPE_TIMESTAMP (93)|  
|SQL_C_TYPE_TIMESTAMP (93)|错误 （从数据挖掘）|错误 （从数据挖掘）|SQL_C_TIMESTAMP (11)|[2] 没有映射|  
  
 [1] 为此，ODBC *3.x*应用程序使用 ODBC *2.x*驱动程序可以使用目录函数返回的结果集中返回的日期、 时间戳代码。  
  
 [2] 为此，ODBC *3.x*应用程序使用 ODBC *3.x*驱动程序可以使用目录函数返回的结果集中返回的日期、 时间戳代码。  
  
 下表显示如何 ODBC *3.x*驱动程序管理器执行的输入中的日期、 时间和时间戳 SQL 数据类型映射*ParameterType*自变量的**SQLBindParameter**或在*数据类型*自变量**SQLGetTypeInfo**。  
  
|数据类型<br /><br /> 输入代码|*2.x*到应用<br /><br /> *2.x* driver|*2.x*到应用<br /><br /> *3.x* driver|*3.x*到应用<br /><br /> *2.x* driver|*3.x*到应用<br /><br /> *3.x* driver|  
|--------------------------------|-----------------------------------|-----------------------------------|-----------------------------------|-----------------------------------|  
|SQL_DATE (9)|无映射|SQL_TYPE_DATE (91)|无映射 [1]|SQL_TYPE_DATE (91)|  
|SQL_TYPE_DATE (91)|错误 （从数据挖掘）|错误 （从数据挖掘）|SQL_DATE (9)|[2] 没有映射|  
|SQL_TIME (10)|无映射|SQL_TYPE_TIME (92)|无映射 [1]|SQL_TYPE_TIME (92)|  
|SQL_TYPE_TIME (92)|错误 （从数据挖掘）|错误 （从数据挖掘）|SQL_TIME (10)|[2] 没有映射|  
|SQL_TIMESTAMP (11)|无映射|SQL_TYPE_TIMESTAMP (93)|无映射 [1]|SQL_TYPE_TIMESTAMP (93)|  
|SQL_TYPE_TIMESTAMP (93)|错误 （从数据挖掘）|错误 （从数据挖掘）|SQL_TIMESTAMP (11)|[2] 没有映射|  
  
 [1] 为此，ODBC *3.x*应用程序使用 ODBC *2.x*驱动程序可以使用目录函数返回的结果集中返回的日期、 时间戳代码。  
  
 [2] 为此，ODBC *3.x*应用程序使用 ODBC *3.x*驱动程序可以使用目录函数返回的结果集中返回的日期、 时间戳代码。
