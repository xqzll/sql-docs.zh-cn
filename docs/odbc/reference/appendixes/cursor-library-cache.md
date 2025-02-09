---
title: 游标库缓存 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC cursor library [ODBC], cache
- cursor library [ODBC], cache
- cache [ODBC]
ms.assetid: d6a91cd6-3905-4e3a-98ab-37fce893dbe1
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 95a8e01b42f8bdc2036457b5c8a9e0e4088c16fa
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "63241037"
---
# <a name="cursor-library-cache"></a>游标库缓存
> [!IMPORTANT]  
>  此功能将 Windows 的未来版本中删除。 避免在新的开发工作中使用此功能并计划修改当前使用此功能的应用程序。 Microsoft 建议使用驱动程序的游标功能。  
  
 在结果集中的数据的每一行，该游标库缓存中每个绑定列的数据的长度和行状态的每个绑定列的数据。 游标库使用这两个缓存中的值来返回通过**SQLFetch**并**SQLFetchScroll** ，并构造搜索的语句定位操作。 有关详细信息，请参阅[构造搜索语句](../../../odbc/reference/appendixes/constructing-searched-statements.md)。  
  
 本部分包含以下主题。  
  
-   [列数据](../../../odbc/reference/appendixes/column-data.md)  
  
-   [列数据的长度](../../../odbc/reference/appendixes/length-of-column-data.md)  
  
-   [行状态](../../../odbc/reference/appendixes/row-status.md)  
  
-   [缓存的位置](../../../odbc/reference/appendixes/location-of-cache.md)
