---
title: SQLColAttributes （Visual FoxPro ODBC 驱动程序） |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLColAttribute function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: d403dfa0-c26d-47d4-91d9-2f29aa387399
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e34929315d3a3548799bc605dbb8f3c4a2f665d0
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "62928165"
---
# <a name="sqlcolattributes-visual-foxpro-odbc-driver"></a>SQLColAttributes（Visual FoxPro ODBC 驱动程序）
> [!NOTE]  
>  本主题包含 Visual FoxPro ODBC 驱动程序特定信息。 有关此函数的常规信息，请参阅下的相应主题[ODBC API 参考](../../odbc/reference/syntax/odbc-api-reference.md)。  
  
 支持：完全  
  
 ODBC API 一致性：核心级别  
  
 在结果集中返回列的描述符信息。 描述符信息返回为字符串、 一个 32 位依赖于描述符的值或一个整数值。  
  
> [!NOTE]  
>  **SQLColAttributes**不能用于返回有关书签列 （列 0） 的信息。  
  
 Visual FoxPro ODBC 驱动程序支持所有*fDescType*值。 下表包含对所选值的驱动程序的实现的注释。  
  
|*fDescType*|注释|  
|-----------------|-------------|  
|SQL_COLUMN_AUTO_INCREMENT|返回 FALSE:Visual FoxPro 没有任何计数器字段。|  
|SQL_COLUMN_CASE_SENSITIVE|如果列类型是字符，始终返回 TRUE。|  
|SQL_COLUMN_LABEL|返回列名称，也会返回 SQL_COLUMN_NAME。|  
|SQL_COLUMN_MONEY|如果列类型是货币 （由 Visual FoxPro 语言中的"Y"），则返回 TRUE。|  
|SQL_COLUMN_OWNER_NAME|始终返回空字符串。|  
|SQL_COLUMN_QUALIFIER_NAME|始终返回空字符串。|  
|SQL_COLUMN_SEARCHABLE|对于常规; 类型的列返回 SQL_UNSEARCHABLE不能在 WHERE 子句中使用这些列。<br /><br /> 类型字符或 NOCPTRANS 与备注的列，则返回 SQL_SEARCHABLE 未设置;这些列可以包含任何比较运算符的 WHERE 子句中使用。<br /><br /> 对于所有其他列类型; 返回 SQL_ALL_EXCEPT_LIKE可以使用类似于除外的所有比较运算符的 WHERE 子句中使用这些列。|  
|SQL_COLUMN_TABLE_NAME|始终返回空字符串。|  
  
 有关详细信息，请参阅[SQLColAttributes](../../odbc/reference/syntax/sqlcolattributes-function.md)中*ODBC 程序员参考*。
