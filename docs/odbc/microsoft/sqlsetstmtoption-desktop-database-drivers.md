---
title: SQLSetStmtOption （桌面数据库驱动程序） |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLSetStmtOption function [ODBC], Desktop Database Drivers
ms.assetid: 98db9631-eb9b-4962-abe4-96f495133a5d
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 48dc5dff83e942b894548d44e3673c19ca0746c5
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "63305795"
---
# <a name="sqlsetstmtoption-desktop-database-drivers"></a>SQLSetStmtOption（桌面数据库驱动程序）

|*fOption*|注释|  
|---------------|--------------|  
|SQL_ASYNC_ENABLE|不支持异步处理。 SQL_ASYNC_ENABLE fOption 将返回 SQLSTATE S1C00 （驱动程序不支持）。|  
|SQL_KEYSET_SIZE|唯一有效的键集大小为 0，因为混合和动态游标不支持。 如果此值设置为其他任何数字，则将其更改为 0，则调用将返回 SQL_SUCCESS_WITH_INFO 和 SQLSTATE 01S02 （选项值已更改）。|  
|SQL_MAX_ROWS|唯一有效的行集大小为 0，因为桌面数据库驱动程序不支持限制返回的行数。 如果此值设置为其他任何数字，则将其更改为 0，则调用将返回 SQL_SUCCESS_WITH_INFO 和 SQLSTATE 01S02 （选项值已更改）。|  
|SQL_QUERY_TIMEOUT|不提供支持。|  
|SQL_ROW_NUMBER|不提供支持。|  
|SQL_SIMULATE_CURSOR|不提供支持。|
