---
title: 从 C 到 SQL：Date | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- date data type [ODBC]
- converting data from c to SQL types [ODBC], date
- data conversions from C to SQL types [ODBC], date
ms.assetid: bea087d3-911f-418b-b483-d2b5b334da19
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8edb075be1bf64dad8f4ef18924a6396b7c64e80
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "63294373"
---
# <a name="c-to-sql-date"></a>从 C 到 SQL：Date
日期 ODBC C 数据类型的标识符是：  
  
 SQL_C_TYPE_DATE  
  
 下表显示 ODBC SQL 日期 C 数据可能转换到的数据类型。 列和表中的条款的说明，请参阅[转换将数据从 C 到 SQL 数据类型](../../../odbc/reference/appendixes/converting-data-from-c-to-sql-data-types.md)。  
  
|SQL 类型标识符|测试|SQLSTATE|  
|-------------------------|----------|--------------|  
|SQL_CHAR<br /><br /> SQL_VARCHAR<br /><br /> SQL_LONGVARCHAR|列的字节长度 > = 10<br /><br /> 列字节长度 < 10<br /><br /> 数据值不是有效的日期|不适用<br /><br /> 22001<br /><br /> 22008|  
|SQL_WCHAR<br /><br /> SQL_WVARCHAR<br /><br /> SQL_WLONGVARCHAR|列的字符长度 > = 10<br /><br /> 列的字符长度 < 10<br /><br /> 数据值不是有效的日期|不适用<br /><br /> 22001<br /><br /> 22008|  
|SQL_TYPE_DATE|数据值是有效的日期<br /><br /> 数据值不是有效的日期|不适用<br /><br /> 22007|  
|SQL_TYPE_TIMESTAMP|数据值是有效的日期 [a]<br /><br /> 数据值不是有效的日期|不适用<br /><br /> 22007|  
  
 [a] 的时间戳的时间部分设置为零。  
  
 有关哪些值是有效 SQL_C_TYPE_DATE 结构中的信息，请参阅[C 数据类型](../../../odbc/reference/appendixes/c-data-types.md)本附录前面。  
  
 当日期 C 数据转换为字符 SQL 数据时，生成的字符数据，在"*yyyy*-*mm*-*dd*"格式。  
  
 该驱动程序将数据转换从日期 C 数据类型时，将忽略此长度/指示器值，并假定数据缓冲区的大小是日期 C 数据类型的大小。 中传递的长度/指示器值*StrLen_or_Ind*中的参数**SQLPutData**并使用指定的缓冲区中*StrLen_or_IndPtr*中参数**SQLBindParameter**。 使用指定的数据缓冲区*DataPtr*中的参数**SQLPutData**并*ParameterValuePtr*中的参数**SQLBindParameter**.
