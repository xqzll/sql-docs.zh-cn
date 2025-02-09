---
title: ODBC 函数摘要 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- functions [ODBC], listed by task
ms.assetid: 7aa635da-e6b7-439f-8e9b-c3860e24de5e
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a6829f4f5197fca28944e5bc9d2f636f6624c9d7
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "62653329"
---
# <a name="odbc-function-summary"></a>ODBC 函数摘要
下表列出了按类型的任务中，分组的 ODBC 函数，并包括指定的一致性和每个函数的用途的简要说明。 有关符合性标志的详细信息，请参阅[ODBC 和标准 CLI](../../../odbc/reference/odbc-and-the-standard-cli.md)。 有关语法和语义为每个函数的详细信息，请参阅[ODBC API 参考](../../../odbc/reference/syntax/odbc-api-reference.md)。  
  
 应用程序可以调用**SQLGetInfo**函数可获得有关驱动程序的符合性信息。 若要获取有关支持的驱动程序中的特定函数的信息，应用程序可以调用**SQLGetFunctions**。  
  
|任务|函数名称|符合性|用途|  
|----------|-------------------|-----------------|-------------|  
|连接到数据源|[SQLAllocHandle](../../../odbc/reference/syntax/sqlallochandle-function.md)|ISO 92|获取环境、 连接、 语句或描述符句柄。|  
||[SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md)|ISO 92|连接到特定的驱动程序的数据源名称、 用户 ID 和密码。|  
||[SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md)|ODBC|通过连接字符串或请求的驱动程序管理器和驱动程序显示用户的连接对话框连接到特定的驱动程序。|  
||[SQLBrowseConnect](../../../odbc/reference/syntax/sqlbrowseconnect-function.md)|ODBC|返回连接属性和有效的特性值的连续级别。 如果已为每个连接属性指定值，连接到数据源。|  
|获取有关驱动程序和数据源的信息|[SQLDataSources](../../../odbc/reference/syntax/sqldatasources-function.md)<br /><br /> [SQLDrivers](../../../odbc/reference/syntax/sqldrivers-function.md)|ISO 92<br /><br /> ODBC|返回可用数据源的列表。<br /><br /> 返回安装的驱动程序和其属性的列表。|  
||[SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md)|ISO 92|返回有关特定驱动程序和数据源的信息。|  
||[SQLGetFunctions](../../../odbc/reference/syntax/sqlgetfunctions-function.md)|ISO 92|返回支持的驱动程序函数。|  
||[SQLGetTypeInfo](../../../odbc/reference/syntax/sqlgettypeinfo-function.md)|ISO 92|返回有关受支持的数据类型的信息。|  
|设置和检索驱动程序属性|[SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md)<br /><br /> [SQLGetConnectAttr](../../../odbc/reference/syntax/sqlgetconnectattr-function.md)|ISO 92<br /><br /> ISO 92|设置连接属性。<br /><br /> 返回连接属性的值。|  
||[SQLSetEnvAttr](../../../odbc/reference/syntax/sqlsetenvattr-function.md)|ISO 92|设置一个环境属性。|  
||[SQLGetEnvAttr](../../../odbc/reference/syntax/sqlgetenvattr-function.md)|ISO 92|返回环境属性的值。|  
||[SQLSetStmtAttr](../../../odbc/reference/syntax/sqlsetstmtattr-function.md)|ISO 92|设置语句属性。|  
||[SQLGetStmtAttr](../../../odbc/reference/syntax/sqlgetstmtattr-function.md)|ISO 92|返回的语句属性的值。|  
|设置和检索描述符字段|[SQLGetDescField](../../../odbc/reference/syntax/sqlgetdescfield-function.md)<br /><br /> [SQLGetDescRec](../../../odbc/reference/syntax/sqlgetdescrec-function.md)|ISO 92<br /><br /> ISO 92|返回单一的描述符字段的值。<br /><br /> 返回多个描述符字段的值。|  
||[SQLSetDescField](../../../odbc/reference/syntax/sqlsetdescfield-function.md)|ISO 92|设置单一的描述符字段。|  
||[SQLSetDescRec](../../../odbc/reference/syntax/sqlsetdescrec-function.md)|ISO 92|设置多个描述符字段。|  
||[SQLCopyDesc](../../../odbc/reference/syntax/sqlcopydesc-function.md)|ISO 92|将描述符信息从一个描述符句柄复制到另一个。|  
|准备 SQL 的工作请求|[SQLPrepare](../../../odbc/reference/syntax/sqlprepare-function.md)|ISO 92|准备供以后执行的 SQL 语句。|  
||[SQLBindParameter](../../../odbc/reference/syntax/sqlbindparameter-function.md)|ODBC|分配存储在 SQL 语句中的参数。|  
||[SQLGetCursorName](../../../odbc/reference/syntax/sqlgetcursorname-function.md)|ISO 92|返回与语句句柄关联的游标名称。|  
||[SQLSetCursorName](../../../odbc/reference/syntax/sqlsetcursorname-function.md)|ISO 92|指定游标名称。|  
||[SQLSetScrollOptions](../../../odbc/reference/syntax/sqlsetscrolloptions-function.md)|ODBC|设置用于控制游标行为的选项。|  
|提交请求|[SQLExecute](../../../odbc/reference/syntax/sqlexecute-function.md)<br /><br /> [SQLExecDirect](../../../odbc/reference/syntax/sqlexecdirect-function.md)|ISO 92<br /><br /> ISO 92|执行已准备的语句。<br /><br /> 执行语句。|  
||[SQLNativeSql](../../../odbc/reference/syntax/sqlnativesql-function.md)|ODBC|转换后的驱动程序返回的 SQL 语句的文本。|  
||[SQLDescribeParam](../../../odbc/reference/syntax/sqldescribeparam-function.md)|ODBC|在语句中返回特定参数的说明。|  
||[SQLNumParams](../../../odbc/reference/syntax/sqlnumparams-function.md)|ISO 92|在语句中返回参数的数目。|  
||[SQLParamData](../../../odbc/reference/syntax/sqlparamdata-function.md)|ISO 92|结合使用**SQLPutData**提供在执行时的参数数据。 （适用于长数据值。）|  
||[SQLPutData](../../../odbc/reference/syntax/sqlputdata-function.md)|ISO 92|将发送部分或全部参数的数据值。 （适用于长数据值。）|  
|检索结果和有关结果的信息|[SQLRowCount](../../../odbc/reference/syntax/sqlrowcount-function.md)<br /><br /> [SQLNumResultCols](../../../odbc/reference/syntax/sqlnumresultcols-function.md)|ISO 92<br /><br /> ISO 92|返回受 insert、 update 或 delete 请求影响的行数。<br /><br /> 返回结果集中的列数。|  
||[SQLDescribeCol](../../../odbc/reference/syntax/sqldescribecol-function.md)|ISO 92|在结果集中列的说明。|  
||[SQLColAttribute](../../../odbc/reference/syntax/sqlcolattribute-function.md)|ISO 92|描述结果集中的列的属性。|  
||[SQLBindCol](../../../odbc/reference/syntax/sqlbindcol-function.md)|ISO 92|分配结果列的存储，并指定数据类型。|  
||[SQLFetch](../../../odbc/reference/syntax/sqlfetch-function.md)|ISO 92|返回多个结果行。|  
||[SQLFetchScroll](../../../odbc/reference/syntax/sqlfetchscroll-function.md)|ISO 92|返回可滚动的结果行。|  
||[SQLGetData](../../../odbc/reference/syntax/sqlgetdata-function.md)|ISO 92|返回部分或全部的结果的一个行的某一列的设置。 （适用于长数据值。）|  
||[SQLSetPos](../../../odbc/reference/syntax/sqlsetpos-function.md)|ODBC|定位游标中提取的数据块并允许应用程序刷新行集中的数据或将更新或删除结果集中的数据。|  
||[SQLBulkOperations](../../../odbc/reference/syntax/sqlbulkoperations-function.md)|ODBC|执行大容量插入和大容量书签操作，包括更新、 删除和提取按书签。|  
||[SQLMoreResults](../../../odbc/reference/syntax/sqlmoreresults-function.md)|ODBC|确定是否有多个结果集可用，和如果是这样，初始化为下一步的结果集的处理。|  
||[SQLGetDiagField](../../../odbc/reference/syntax/sqlgetdiagfield-function.md)|ISO 92|返回其他诊断信息 （单个字段的诊断数据结构）。|  
||[SQLGetDiagRec](../../../odbc/reference/syntax/sqlgetdiagrec-function.md)|ISO 92|返回其他诊断信息 （多个字段的诊断数据结构）。|  
|获取有关数据源的系统表 （目录函数） 的信息|[SQLColumnPrivileges](../../../odbc/reference/syntax/sqlcolumnprivileges-function.md)<br /><br /> [SQLColumns](../../../odbc/reference/syntax/sqlcolumns-function.md)|ODBC<br /><br /> 打开组|返回的列和一个或多个表关联的特权的列表。<br /><br /> 返回指定表中的列名称的列表。|  
||[SQLForeignKeys](../../../odbc/reference/syntax/sqlforeignkeys-function.md)|ODBC|如果指定表的存在，则返回组成外键的列名称的列表。|  
||[SQLPrimaryKeys](../../../odbc/reference/syntax/sqlprimarykeys-function.md)|ODBC|返回构成了表的主键的列名称的列表。|  
||[SQLProcedureColumns](../../../odbc/reference/syntax/sqlprocedurecolumns-function.md)|ODBC|返回输入和输出参数，以及组成的指定过程的结果集的列的列表。|  
||[SQLProcedures](../../../odbc/reference/syntax/sqlprocedures-function.md)|ODBC|返回的特定数据源中存储的过程名称的列表。|  
||[SQLSpecialColumns](../../../odbc/reference/syntax/sqlspecialcolumns-function.md)|打开组|返回唯一标识指定表中的某一行的列或行中的任何值更新的事务时，会自动更新的列的最佳集合有关的信息。|  
||[SQLStatistics](../../../odbc/reference/syntax/sqlstatistics-function.md)|ISO 92|返回有关单个表和索引与表关联的列表的统计信息。|  
||[SQLTablePrivileges](../../../odbc/reference/syntax/sqltableprivileges-function.md)|ODBC|返回表和关联与每个表的权限的列表。|  
||[SQLTables](../../../odbc/reference/syntax/sqltables-function.md)|打开组|返回特定数据源中存储的表名称的列表。|  
|终止语句|[SQLFreeStmt](../../../odbc/reference/syntax/sqlfreestmt-function.md)|ISO 92|结束语句处理、 放弃挂起的结果，并 （可选） 释放语句句柄关联的所有资源。|  
||[SQLCloseCursor](../../../odbc/reference/syntax/sqlclosecursor-function.md)|ISO 92|关闭对语句句柄已打开的游标。|  
||[SQLCancel](../../../odbc/reference/syntax/sqlcancel-function.md)|ISO 92|取消语句处理。|  
||[SQLCancelHandle](../../../odbc/reference/syntax/sqlcancelhandle-function.md)|ODBC|取消语句或连接上的处理。|  
||[SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md)|ISO 92|提交或回滚事务。|  
|终止连接|[SQLDisconnect](../../../odbc/reference/syntax/sqldisconnect-function.md)<br /><br /> [SQLFreeHandle](../../../odbc/reference/syntax/sqlfreehandle-function.md)|ISO 92<br /><br /> ISO 92|关闭连接。<br /><br /> 释放环境、 连接、 语句或描述符句柄。|
