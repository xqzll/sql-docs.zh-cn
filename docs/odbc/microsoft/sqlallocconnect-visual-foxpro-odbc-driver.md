---
title: SQLAllocConnect （Visual FoxPro ODBC 驱动程序） |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLAllocConnect function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 70d48b12-def5-475c-b8e1-654a55fdfe0f
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: cc05bae8e67098bb89345b1cf0333abae68397d1
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "63313319"
---
# <a name="sqlallocconnect-visual-foxpro-odbc-driver"></a>SQLAllocConnect（Visual FoxPro ODBC 驱动程序）
> [!NOTE]  
>  本主题包含 Visual FoxPro ODBC 驱动程序特定信息。 有关此函数的常规信息，请参阅下的相应主题[ODBC API 参考](../../odbc/reference/syntax/odbc-api-reference.md)。  
  
 支持：完全  
  
 ODBC API 一致性：核心级别  
  
 为连接句柄，分配内存*hdbc*，由标识在环境中*henv*。 驱动程序管理器处理此调用，并调用在驱动程序**SQLAllocConnect**每当[SQLConnect](../../odbc/microsoft/sqlconnect-visual-foxpro-odbc-driver.md)， **SQLBrowseConnect**，或[SQLDriverConnect](../../odbc/microsoft/sqldriverconnect-visual-foxpro-odbc-driver.md)调用。  
  
 有关详细信息，请参阅[SQLAllocConnect](../../odbc/reference/syntax/sqlallocconnect-function.md)中*ODBC 程序员参考*。
