---
title: 书签类型 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- result sets [ODBC], bookmarks
- variable-length bookmarks [ODBC]
- bookmarks [ODBC]
- fixed-length bookmarks [ODBC]
ms.assetid: cb2e7443-0260-4d1a-930f-0154db447979
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d9aca006623d9ddb8292147d8a28c93f912fd25d
ms.sourcegitcommit: 56b963446965f3a4bb0fa1446f49578dbff382e0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/11/2019
ms.locfileid: "67794023"
---
# <a name="bookmark-types"></a>书签类型
ODBC 中的所有书签*3.x*长度可变的书签。 这样，主键或唯一索引与表用作书签相关联。 书签还可以为一个 32 位值，因为已在 ODBC 中使用*2.x*。 若要指定与某个游标，ODBC 使用书签*3.x*应用程序设置为 SQL_UB_VARIABLE SQL_ATTR_USE_BOOKMARK 语句属性。 自动使用长度可变的书签。  
  
 应用程序可以调用**SQLColAttribute**与*FieldIdentifier*参数设置为的 SQL_DESC_OCTET_LENGTH 若要获取的书签的长度。 长度可变的书签可以是一个长整型值，因为应用程序应绑定到列 0 除非将该书签用于许多行集中的行。  
  
 定长书签仅支持向后兼容性。 如果 ODBC *2.x*应用程序使用 ODBC *3.x*驱动程序调用**SQLSetStmtOption**若要设置到 SQL_UB_ON SQL_USE_BOOKMARKS，它将映射中驱动程序管理器对 SQL_UB_VARIABLE。 使用长度可变的书签，即使它仅为 32 位进行填充。 如果驱动程序支持定长书签，它将支持长度可变的书签。 如果 ODBC *3.x*应用程序使用 ODBC *2.x*驱动程序调用**SQLSetStmtAttr**若要设置到 SQL_UB_VARIABLE SQL_ATTR_USE_BOOKMARKS，它将映射驱动程序中使用 SQL_UB_ON 和 32 位定长书签管理器。 SQL_ATTR_FETCH_BOOKMARK_PTR 语句属性然后必须指向 32 位书签。 如果长度超过 32 位，如主键用作书签时，使用书签将变为光标必须映射到 32 位值的实际值。 例如，它可以生成它们的哈希表。 当 ODBC *3.x*应用程序使用 ODBC *2.x*驱动程序将绑定一个书签，缓冲区长度必须为 4。
