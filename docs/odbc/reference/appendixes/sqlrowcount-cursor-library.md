---
title: SQLRowCount （游标库） |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLRowCount function [ODBC], Cursor Library
ms.assetid: 781cf5a5-325e-4523-8633-d96d9e98277c
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9b3dcd9c348d83dad1e295e253cb37768fbb0abb
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "63473043"
---
# <a name="sqlrowcount-cursor-library"></a>SQLRowCount（游标库）
> [!IMPORTANT]  
>  此功能将 Windows 的未来版本中删除。 避免在新的开发工作中使用此功能并计划修改当前使用此功能的应用程序。 Microsoft 建议使用驱动程序的游标功能。  
  
 本主题介绍如何使用**SQLRowCount**游标库中的函数。 有关常规信息**SQLRowCount**，请参阅[SQLRowCount 函数](../../../odbc/reference/syntax/sqlrowcount-function.md)。  
  
 当应用程序调用**SQLRowCount**与游标相关联的语句，该游标库将返回它是否已从驱动程序检索的数据的行数。  
  
 当应用程序调用**SQLRowCount**使用定位的更新或删除语句相关联的语句，该游标库将返回受语句影响的行数。  
  
 当应用程序调用**SQLRowCount**后**选择**语句，该游标库返回-1。
