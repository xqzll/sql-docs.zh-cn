---
title: 提交和回滚行为 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- interoperability [ODBC], transaction support
- transactions [ODBC], DBMS support
ms.assetid: 2ac8f012-e46d-41ca-81bb-e4a3246e3241
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: bad1706e7283c0b0a5111e93c9dfd7ae494c8ef4
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "63125493"
---
# <a name="commit-and-rollback-behavior"></a>提交和回滚行为
在服务器 Dbms 之间常见行为是关闭游标并放弃时提交或回滚语句预定义的语句。 桌面数据库会更容易保持打开游标并保持预定义的语句。 有关详细信息，请参阅中的 SQL_CURSOR_COMMIT_BEHAVIOR 和 SQL_CURSOR_ROLLBACK_BEHAVIOR 选项[SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md)函数说明和[游标和准备语句上的事务的效果](../../../odbc/reference/develop-app/effect-of-transactions-on-cursors-and-prepared-statements.md).
