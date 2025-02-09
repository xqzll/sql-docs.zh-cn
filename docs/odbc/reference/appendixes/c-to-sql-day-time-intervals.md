---
title: 从 C 到 SQL：日期时间间隔 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- day-time intervals [ODBC]
- data conversions from C to SQL types [ODBC], day-time intervals
- converting data from c to SQL types [ODBC], day-time intervals
- intervals [ODBC], converting
ms.assetid: f9ee1ddb-dec7-4f78-b6e2-5ba34e7d6f59
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: cb41d658637258c6d60b5adb4e0d7abb9ae81d91
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "63213415"
---
# <a name="c-to-sql-day-time-intervals"></a>从 C 到 SQL：日期时间间隔
日期时间间隔 ODBC C 数据类型的标识符是：  
  
 SQL_C_INTERVAL_DAY  
  
 SQL_C_INTERVAL_HOUR  
  
 SQL_C_INTERVAL_MINUTE  
  
 SQL_C_INTERVAL_SECOND  
  
 SQL_C_INTERVAL_DAY_TO_HOUR  
  
 SQL_C_INTERVAL_DAY_TO_MINUTE  
  
 SQL_C_INTERVAL_DAY_TO_SECOND  
  
 SQL_C_INTERVAL_HOUR_TO_MINUTE  
  
 SQL_C_INTERVAL_HOUR_TO_SECOND  
  
 SQL_C_INTERVAL_MINUTE_TO_SECOND  
  
 下表显示 ODBC SQL 间隔 C 数据可能转换到的数据类型。 列和表中的条款的说明，请参阅[转换将数据从 C 到 SQL 数据类型](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md)。  
  
|SQL 类型标识符|测试|SQLSTATE|  
|-------------------------|----------|--------------|  
|SQL_CHAR[a]<br /><br /> SQL_VARCHAR[a]<br /><br /> SQL_LONGVARCHAR[a]|列的字节长度 > = 字符字节长度<br /><br /> 列的字节长度 < 字符字节长度 [a]<br /><br /> 数据值不是有效的时间间隔文本|不适用<br /><br /> 22001<br /><br /> 22015|  
|SQL_WCHAR[a]<br /><br /> SQL_WVARCHAR[a]<br /><br /> SQL_WLONGVARCHAR[a]|列的字符长度 > = 字符长度的数据<br /><br /> 列的字符长度 < 字符长度的数据 [a]<br /><br /> 数据值不是有效的时间间隔文本|不适用<br /><br /> 22001<br /><br /> 22015|  
|SQL_TINYINT[b]<br /><br /> SQL_SMALLINT[b] SQL_INTEGER[b]<br /><br /> SQL_BIGINT[b] SQL_NUMERIC[b]<br /><br /> SQL_DECIMAL[b]|单字段间隔转换没有导致截断的整个数字<br /><br /> 转换导致截断的整个数字|不适用<br /><br /> 22003|  
|SQL_INTERVAL_DAY<br /><br /> SQL_INTERVAL_HOUR<br /><br /> SQL_INTERVAL_MINUTE<br /><br /> SQL_INTERVAL_SECOND<br /><br /> SQL_INTERVAL_DAY_TO_HOUR<br /><br /> SQL_INTERVAL_DAY_TO_MINUTE<br /><br /> SQL_INTERVAL_DAY_TO_SECOND<br /><br /> SQL_INTERVAL_HOUR_TO_MINUTE<br /><br /> SQL_INTERVAL_HOUR_TO_SECOND<br /><br /> SQL_INTERVAL_MINUTE_TO_SECOND|而无需截断的任何字段的已转换数据值<br /><br /> 在转换期间已被截断的数据值的一个或多个字段，|不适用<br /><br /> 22015|  
  
 [a] 所有的 C 间隔数据类型可以转换为字符数据类型。  
  
 [C 类型的间隔 b] 如果间隔结构中的类型字段是这样的间隔是单个字段 （SQL_DAY、 SQL_HOUR、 SQL_MINUTE 或 SQL_SECOND），可以转换为任何精确数值 (SQL_TINYINT，SQL_SMALLINT，SQL_INTEGER，SQL_BIGINTSQL_DECIMAL 或 SQL_NUMERIC)。  
  
 C 间隔类型的默认值转换为相应的日期时间间隔 SQL 类型。  
  
 该驱动程序将数据从间隔 C 数据类型转换时将忽略此长度/指示器值，并假定数据缓冲区的大小是间隔 C 数据类型的大小。 中传递的长度/指示器值*StrLen_or_Ind*中的参数**SQLPutData**并使用指定的缓冲区中*StrLen_or_IndPtr*中参数**SQLBindParameter**。 使用指定的数据缓冲区*DataPtr*中的参数**SQLPutData**并*ParameterValuePtr*中的参数**SQLBindParameter**.  
  
 下面的示例演示如何将发送到数据库列中存储 SQL_INTERVAL_STRUCT 结构中的 C 间隔数据。 间隔结构包含一个 DAY_TO_SECOND 间隔;它将存储在类型 SQL_INTERVAL_DAY_TO_MINUTE 的数据库列。  
  
```  
SQL_INTERVAL_STRUCT is;  
SQLINTEGER cbValue;  
  
// Initialize the interval struct to contain the DAY_TO_SECOND  
// interval "154 days, 22 hours, 44 minutes, and 10 seconds"  
is.intval.day_second.day      = 154;  
is.intval.day_second.hour     = 22;  
is.intval.day_second.minute   = 44;  
is.intval.day_second.second   = 10;  
is.interval_sign              = SQL_FALSE;  
  
// Bind the dynamic parameter  
SQLBindParameter(hstmt, 1, SQL_PARAM_INPUT, SQL_C_INTERVAL_DAY_TO_SECOND,  
                  SQL_INTERVAL_DAY_TO_MINUTE, 0, 0, &is,  
                  sizeof(SQL_INTERVAL_STRUCT), &cbValue);  
  
// Execute an insert statement; "interval_column" is a column  
// whose data type is SQL_INTERVAL_DAY_TO_MINUTE.  
SQLExecDirect(hstmt,"INSERT INTO table(interval_column) VALUES (?)",SQL_NTS);  
```
