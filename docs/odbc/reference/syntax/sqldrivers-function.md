---
title: SQLDrivers 函数 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLDrivers
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLDrivers
helpviewer_keywords:
- SQLDrivers function [ODBC]
ms.assetid: 6b5b7514-e9cb-4cfd-8b7a-ab51dfab9efa
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 181d3aea0b2c756abc0dc603348cc9cfd728ac4f
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "65538155"
---
# <a name="sqldrivers-function"></a>SQLDrivers 函数
**符合性**  
 版本引入了：ODBC 2.0 标准符合性：ODBC  
  
 **摘要**  
 **SQLDrivers**列出驱动程序说明和驱动程序属性关键字。 执行此函数仅由驱动程序管理器。  
  
## <a name="syntax"></a>语法  
  
```cpp  
  
SQLRETURN SQLDrivers(  
     SQLHENV         EnvironmentHandle,  
     SQLUSMALLINT    Direction,  
     SQLCHAR *       DriverDescription,  
     SQLSMALLINT     BufferLength1,  
     SQLSMALLINT *   DescriptionLengthPtr,  
     SQLCHAR *       DriverAttributes,  
     SQLSMALLINT     BufferLength2,  
     SQLSMALLINT *   AttributesLengthPtr);  
```  
  
## <a name="arguments"></a>参数  
 *EnvironmentHandle*  
 [输入]环境句柄。  
  
 *方向*  
 [输入]确定驱动程序管理器是否提取下一步中的列表 (SQL_FETCH_NEXT)，或是否从列表 (SQL_FETCH_FIRST) 的开头开始搜索驱动程序的描述。  
  
 *DriverDescription*  
 [输出]指向用于返回驱动程序的描述缓冲区的指针。  
  
 如果*DriverDescription*为 NULL， *DescriptionLengthPtr*仍将返回的字符 （不包括字符数据的 null 终止字符） 总数可用于在中返回指向缓冲区*DriverDescription*。  
  
 *BufferLength1*  
 [输入]长度 **DriverDescription*缓冲区，以字符为单位。  
  
 *DescriptionLengthPtr*  
 [输出]指向用于返回的字符 （不包括 null 终止字符） 总数的缓冲区可用于在中返回\* *DriverDescription*。 可用于返回的字符数是否大于或等于*BufferLength1*，驱动程序中的描述\* *DriverDescription*截断为*BufferLength1*减去 null 终止字符的长度。  
  
 *DriverAttributes*  
 [输出]为其返回 （请参阅"注释"） 的驱动程序属性值对的列表中的缓冲区的指针。  
  
 如果*DriverAttributes*为 NULL， *AttributesLengthPtr*仍将返回的总字节数 （不包括字符数据的 null 终止字符） 可用于在缓冲区中返回指向*DriverAttributes*。  
  
 *BufferLength2*  
 [输入]长度\* *DriverAttributes*缓冲区，以字符为单位。 如果 *\*DriverDescription*值为 Unicode 字符串 (在调用时**SQLDriversW**)，则*BufferLength*参数必须为偶数。  
  
 *AttributesLengthPtr*  
 [输出]指向用于返回的总字节数 （不包括 null 终止字节） 的缓冲区可用于在中返回\* *DriverAttributes*。 可用来返回的字节数是否大于或等于*BufferLength2*中的属性值对的列表\* *DriverAttributes*截断为*BufferLength2*减去的 null 终止字符的长度。  
  
## <a name="returns"></a>返回  
 SQL_SUCCESS、 SQL_SUCCESS_WITH_INFO、 SQL_NO_DATA、 SQL_ERROR 或 SQL_INVALID_HANDLE。  
  
## <a name="diagnostics"></a>诊断  
 当**SQLDrivers**返回 SQL_ERROR 或 SQL_SUCCESS_WITH_INFO，可以通过调用获取关联的 SQLSTATE 值**SQLGetDiagRec**与*HandleType*的SQL_HANDLE_ENV 和一个*处理*的*EnvironmentHandle*。 下表列出了通常由返回的 SQLSTATE 值**SQLDrivers** ，并解释了此函数; 每个上下文中的表示法"（数据挖掘）"之前 SQLSTATEs 返回由驱动程序管理器的说明。 与每个 SQLSTATE 值关联的返回代码是 SQL_ERROR，除非另有说明。  
  
|SQLSTATE|错误|Description|  
|--------------|-----------|-----------------|  
|01000|常规警告|(DM) 特定于驱动程序管理器的信息性消息。 （函数返回 SQL_SUCCESS_WITH_INFO。）|  
|01004|字符串数据，右截断|(DM) 缓冲区\* *DriverDescription*是否不足够大以返回完成驱动程序的描述。 因此，说明已被截断。 在返回完成驱动程序说明的长度\* *DescriptionLengthPtr*。 （函数返回 SQL_SUCCESS_WITH_INFO。）<br /><br /> (DM) 缓冲区\* *DriverAttributes*是否不足够大以返回属性值对的完整列表。 因此，该列表已被截断。 在返回的属性值对的未截断的列表长度 **AttributesLengthPtr*。 （函数返回 SQL_SUCCESS_WITH_INFO。）|  
|HY000|常规错误|有关其中没有任何特定的 SQLSTATE 和为其定义任何特定于实现的 SQLSTATE 出错。 返回的错误消息**SQLGetDiagRec**中 *\*MessageText*缓冲区描述错误以及其原因。|  
|HY001|内存分配错误|(DM) 的驱动程序管理器无法分配支持执行或完成该函数所需的内存。|  
|HY010|函数序列错误|（数据挖掘） **SQLExecute**， **SQLExecDirect**，或**SQLMoreResults**曾为*StatementHandle*和返回 SQL_PARAM_DATA_可用。 数据已检索到的所有经过流处理参数之前调用此函数。|  
|HY013|内存管理错误|无法处理函数调用，因为基础内存对象无法访问，可能是由于内存不足的情况。|  
|HY090|字符串或缓冲区长度无效|(DM) 为参数指定的值*BufferLength1*小于 0。<br /><br /> (DM) 为参数指定的值*BufferLength2*为小于 0 或等于 1。|  
|HY103|检索代码无效|(DM) 的参数指定的值*方向*不是等于 SQL_FETCH_FIRST 或 SQL_FETCH_NEXT。|  
|HY117|由于未知的事务状态而挂起连接。 仅断开连接，并允许使用只读的函数。|(DM) 有关挂起状态的详细信息，请参阅[SQLEndTran 函数](../../../odbc/reference/syntax/sqlendtran-function.md)。|  
  
## <a name="comments"></a>注释  
 **SQLDrivers**返回中的驱动程序说明\* *DriverDescription*缓冲区。 它将返回有关中的驱动程序的其他信息\* *DriverAttributes*缓冲区作为关键字值对的列表。 所有关键字所都列的系统信息的驱动程序将为所有驱动程序返回除**CreateDSN**，它用于提示创建的数据源，并因此是可选的。 每个对终止 null 字节，并终止 null 字节的完整列表 （即，两个 null 字节标记列表的末尾）。 例如，使用 C 语法的基于文件的驱动程序可能会返回以下列表的属性 （"\0"表示 null 字符）：  
  
```  
FileUsage=1\0FileExtns=*.dbf\0\0  
```  
  
 如果\* *DriverAttributes*是不足够大以保存整个列表，列表将被截断， **SQLDrivers**返回 SQLSTATE 01004 （截断的数据） 和列表的长度 (不包括中返回最后一个 null 终止字节） **AttributesLengthPtr*。  
  
 安装该驱动程序时，将从系统信息中添加驱动程序属性关键字。 有关详细信息，请参阅[安装 ODBC 组件](../../../odbc/reference/install/installing-odbc-components.md)。  
  
 应用程序可以调用**SQLDrivers**多次来检索所有驱动程序说明。 驱动程序管理器中的系统信息中检索此信息。 当没有更多的驱动程序说明**SQLDrivers**返回 sql_no_data 为止。 如果**SQLDrivers** SQL_FETCH_NEXT 被调用，立即返回 sql_no_data 指示到达后，会返回第一个驱动程序的描述。 有关如何应用程序使用返回的信息**SQLDrivers**，请参阅[选择数据源或驱动程序](../../../odbc/reference/develop-app/choosing-a-data-source-or-driver.md)。  
  
 如果 SQL_FETCH_NEXT 传递给**SQLDrivers**第一次调用时， **SQLDrivers**返回第一个数据源名称。  
  
 因为**SQLDrivers**实现在驱动程序管理器中，支持它而不考虑特定驱动程序的标准符合性的所有驱动程序。  
  
## <a name="related-functions"></a>相关函数  
  
|有关信息|请参阅|  
|---------------------------|---------|  
|发现和列出连接到数据源所需值|[SQLBrowseConnect 函数](../../../odbc/reference/syntax/sqlbrowseconnect-function.md)|  
|连接到数据源|[SQLConnect 函数](../../../odbc/reference/syntax/sqlconnect-function.md)|  
|返回数据源名称|[SQLDataSources 函数](../../../odbc/reference/syntax/sqldatasources-function.md)|  
|连接到使用连接字符串或对话框中的数据源|[SQLDriverConnect 函数](../../../odbc/reference/syntax/sqldriverconnect-function.md)|  
  
## <a name="see-also"></a>请参阅  
 [ODBC API 参考](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC 头文件](../../../odbc/reference/install/odbc-header-files.md)
