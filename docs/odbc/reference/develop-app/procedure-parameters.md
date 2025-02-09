---
title: 过程参数 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- procedure parameters [ODBC]
ms.assetid: 54fd857e-d2cb-467d-bb72-121e67a8e88d
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1cab0fea9c39e4946122698f2476668464e556c1
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "62861527"
---
# <a name="procedure-parameters"></a>过程参数
参数在过程调用中的可以输入、 输入/输出或输出参数。 这是从所有其他 SQL 语句，并且始终包含输入的参数中的参数不同。  
  
 输入的参数用于将值发送到该过程。 例如，假设在部件表有 PartID、 描述和价格的列。 InsertPart 过程可能具有表中的每个列的输入的参数。 例如：  
  
```  
{call InsertPart(?, ?, ?)}  
```  
  
 驱动程序不应修改前的输入缓冲区的内容**SQLExecDirect**或**SQLExecute**返回 SQL_SUCCESS、 SQL_SUCCESS_WITH_INFO、 SQL_ERROR、 SQL_INVALID_HANDLE 或 sql_no_data 为止。 不应修改输入缓冲区的内容时**SQLExecDirect**或**SQLExecute**返回 SQL_NEED_DATA 或 SQL_STILL_EXECUTING。  
  
 使用输入/输出参数来将值发送到过程和检索过程中的值。 使用相同的参数作为输入和输出参数往往是令人困惑，应当避免。 例如，假设过程接受一个订单 ID 并返回客户的 ID。 这可以用单个输入/输出参数进行定义：  
  
```  
{call GetCustID(?)}  
```  
  
 可能会更好的做法使用两个参数： 订单 ID 的输出或客户 ID 的输入/输出参数的输入的参数：  
  
```  
{call GetCustID(?, ?)}  
```  
  
 检索过程返回值并检索其值的过程参数，则使用输出参数返回值的过程有时称为*函数*。 例如，假设**GetCustID**刚刚提到的过程将返回一个值，指示它是否能够找到顺序。 在以下调用中，第一个参数是用于检索过程返回值的输出参数，第二个参数是输入的参数用于指定订单 ID，第三个参数是一个用于检索客户 ID 的输出参数：  
  
```  
{? = call GetCustID(?, ?)}  
```  
  
 驱动程序处理的输入值和输入/输出过程中的参数不方式不同于其他 SQL 语句中的输入参数。 该语句执行时，它们检索变量的值绑定到这些参数并将其发送到数据源。  
  
 执行该语句后，驱动程序绑定到这些参数的变量中存储返回的值的输入/输出和输出参数。 这些返回值没有保证之后已提取的过程返回的所有结果之前设置并**SQLMoreResults**已返回 sql_no_data 为止。 如果执行该语句会导致出现错误，则输入/输出参数缓冲区或输出参数缓冲区的内容不确定。  
  
 应用程序调用**SQLProcedure**以确定是否一个过程的返回值。 它将调用**SQLProcedureColumns**来确定每个过程参数的类型 （返回值，输入、 输入/输出或输出）。
