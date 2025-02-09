---
title: Datetime 数据类型 |Microsoft Docs
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
- data types [ODBC], date
- backward compatibility [ODBC], datetime data types
- timestamp data type [ODBC]
- data types [ODBC], timestamp
- data types [ODBC], backward compatibility
- compatibility [ODBC], datetime data types
- data types [ODBC], time
ms.assetid: 6b9363c9-04bf-4492-a210-7aa15dea4af8
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 13cb433da64b78a8b5e70f28642fd576f6803ed5
ms.sourcegitcommit: 56b963446965f3a4bb0fa1446f49578dbff382e0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/11/2019
ms.locfileid: "67792586"
---
# <a name="datetime-data-types"></a>日期时间数据类型
在 ODBC *3.x*、 的标识符的日期、 时间和时间戳 SQL 数据类型已更改从 SQL_DATE、 SQL_TIME 和 SQL_TIMESTAMP (的实例，并用 **#define** 9、 10 和 11 的标头文件中) 到 SQL_TYPE_DATE、 SQL_TYPE_TIME 和 SQL_TYPE_TIMESTAMP (的实例，并用 **#define** 91、 92 和 93 的标头文件中)，分别。 标识符已更改从 SQL_C_DATE、 SQL_C_TIME 和 SQL_C_TIMESTAMP SQL_C_TYPE_DATE、 SQL_C_TYPE_TIME，和 SQL_C_TYPE_TIMESTAMP，分别对应的 C 类型和实例 **#define**已更改相应地。  
  
 ODBC 中的 SQL 日期时间数据类型返回的列的大小和小数位数*3.x*精度和小数位数相同在 ODBC 中为其返回的是*2.x*。 这些值是不同于 SQL_DESC_PRECISION 和 SQL_DESC_SCALE 描述符字段中的值。 (有关详细信息，请参阅[列的大小、 十进制数字、 传输八位字节长度和显示大小](../../../odbc/reference/appendixes/column-size-decimal-digits-transfer-octet-length-and-display-size.md)中附录 d:数据类型。）  
  
 这些更改会影响**SQLDescribeCol**， **SQLDescribeParam**，并**SQLColAttributes**;**SQLBindCol**， **SQLBindParameter**，并**SQLGetData**; 并且**SQLColumns**， **SQLGetTypeInfo**， **SQLProcedureColumns**， **SQLStatistics**，并且**SQLSpecialColumns**。  
  
 ODBC *3.x*驱动程序处理根据 SQL_ATTR_ODBC_VERSION 环境属性的设置的上一个段落中列出的函数调用。 有关**SQLColumns**， **SQLGetTypeInfo**， **SQLProcedureColumns**， **SQLSpecialColumns**，和**SQLStatistics**如果 SQL_ATTR_ODBC_VERSION 设置为 SQL_OV_ODBC3，函数将返回 SQL_TYPE_DATE、 SQL_TYPE_TIME 和 SQL_TYPE_TIMESTAMP DATA_TYPE 字段中。 COLUMN_SIZE 列 (返回的结果集中**SQLColumns**， **SQLGetTypeInfo**， **SQLProcedureColumns**，和**SQLSpecialColumns**)包含近似数值类型的二进制精度。 NUM_PREC_RADIX 列 (返回的结果集中**SQLColumns**， **SQLGetTypeInfo**，并**SQLProcedureColumns**) 包含值为 2。 如果 SQL_ATTR_ODBC_VERSION 设置为 SQL_OV_ODBC2，则函数返回 SQL_DATE、 SQL_TIME 和 SQL_TIMESTAMP DATA_TYPE 字段中，COLUMN_SIZE 列包含近似数值类型和 NUM_PREC_RADIX 列的小数精度包含值为 10。  
  
 所有数据类型对的调用中的都请求时**SQLGetTypeInfo**，由函数返回的结果集将在 ODBC 中的定义包含 SQL_TYPE_DATE、 SQL_TYPE_TIME 和 SQL_TYPE_TIMESTAMP *3.x*，和 SQL_DATE、 SQL_TIME 和 ODBC 中定义的 SQL_TIMESTAMP *2.x*。  
  
 由于如何 ODBC *3.x*驱动程序管理器执行的日期、 时间和时间戳数据类型，ODBC 映射*3.x*驱动程序仅需要识别 **#defines**的 91、 92，和中输入的日期、 时间和时间戳 C 数据类型为 93 *TargetType*的参数**SQLBindCol**并**SQLGetData**或*ValueType*的参数**SQLBindParameter**，并仅需要识别 **#defines**的 91、 92 和 93、 日期时间，而时间戳 SQL 数据类型输入*ParameterType*自变量的**SQLBindParameter**或*数据类型*自变量**SQLGetTypeInfo**。 有关详细信息，请参阅[日期时间数据类型更改](../../../odbc/reference/develop-app/datetime-data-type-changes.md)。
