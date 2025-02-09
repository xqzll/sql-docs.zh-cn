---
title: 从 SQL 到 C：Date | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- converting data from SQL to C types [ODBC], date
- date data type [ODBC]
- data conversions from SQL to C types [ODBC], date
ms.assetid: 703c7960-9cf4-4d7a-9920-53b29c184f97
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: fe0c30f0f0fbf0ea695d79387fdec3694a54ebca
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "63151276"
---
# <a name="sql-to-c-date"></a>从 SQL 到 C：Date
ODBC SQL 数据类型是日期的标识符：  
  
 SQL_TYPE_DATE  
  
 下表显示 ODBC C 数据类型可能会转换为日期 SQL 数据。 列和表中的条款的说明，请参阅[从 SQL 到 C 数据类型的转换的数据](../../../odbc/reference/appendixes/converting-data-from-sql-to-c-data-types.md)。  
  
|C 类型标识符|测试|**TargetValuePtr*|**StrLen_or_IndPtr*|SQLSTATE|  
|-----------------------|----------|------------------------|----------------------------|--------------|  
|SQL_C_CHAR|*BufferLength* > 字符字节长度<br /><br /> 11 < = *BufferLength* < = 字符字节长度<br /><br /> *BufferLength* < 11|数据<br /><br /> 截断的数据<br /><br /> 未定义|10<br /><br /> 以字节为单位的数据的长度<br /><br /> 未定义|不适用<br /><br /> 01004<br /><br /> 22003|  
|SQL_C_WCHAR|*BufferLength* > 字符长度<br /><br /> 11 < = *BufferLength* < = 字符长度<br /><br /> *BufferLength* < 11|数据<br /><br /> 截断的数据<br /><br /> 未定义|10<br /><br /> 以字符为单位的数据的长度<br /><br /> 未定义|不适用<br /><br /> 01004<br /><br /> 22003|  
|SQL_C_BINARY|数据的字节长度 < = *BufferLength*<br /><br /> 数据的字节长度 > *BufferLength*|数据<br /><br /> 未定义|以字节为单位的数据的长度<br /><br /> 未定义|不适用<br /><br /> 22003|  
|SQL_C_TYPE_DATE|None[a]|数据|6[c]|不适用|  
|SQL_C_TYPE_TIMESTAMP|None[a]|Data[b]|16[c]|不适用|  
  
 [a] 的值*BufferLength*忽略此转换。 驱动程序假定的大小 **TargetValuePtr*是 C 数据类型的大小。  
  
 [时间戳结构 b] 的时间字段设置为零。  
  
 [c] 这是相应的 C 数据类型的大小。  
  
 当日期 SQL 数据转换为 C 字符数据时，生成的字符串是中"*yyyy*-*mm*-*dd*"格式。 此格式不受 Windows® 国家/地区设置。
