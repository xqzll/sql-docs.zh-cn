---
title: 增量搜索活动文档 | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.technology: scripting
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- searches [SQL Server Management Studio], incremental
- Query Editor [SQL Server Management Studio], incremental search
- incremental searches [SQL Server Management Studio]
ms.assetid: 490bb36c-dd43-4219-9e2a-ff27046b9395
author: markingmyname
ms.author: maghan
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: e491d415ec1bcb62c95366f2471ba6780ad3874f
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "65821961"
---
# <a name="search-an-active-document-incrementally"></a>增量搜索活动文档
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
  您可以通过输入文字来对单个文档或窗口执行渐进式搜索。 搜索操作会突出显示与在文档或窗口的渐进式搜索过程中输入的字符相匹配的第一个字符集。 渐进式搜索会自动搜索文档或窗口内的所有文字，但隐藏文字除外。  
  
 对于 **“大小写匹配”** 选项，渐进式搜索将使用上一次搜索的条件。 例如，如果使用“在文件中查找”  对话框跨多个文件执行搜索，并选择“大小写匹配”  ，然后执行渐进式搜索，则此搜索将区分大小写。  
  
### <a name="to-search-incrementally"></a>执行渐进式搜索  
  
1.  打开您要搜索的文件或窗口。  
  
2.  在 **“编辑”** 菜单中，指向 **“高级”** ，然后单击 **“渐进式搜索”** 。  
  
     光标图标会变为带箭头的望远镜，指示搜索方向，并且状态栏显示“渐进式搜索”。  
  
3.  开始键入文本字符串。  
  
     当编辑器突出显示此文本的第一个匹配项时，状态栏会显示您正在输入的文本。 编辑器会随着您的继续键入而移动到下一个匹配项并使其突出显示。 如果没有匹配项，状态栏会显示以下信息。  
  
    ```  
    Incremental Search: <text> (not found)  
    ```  
  
 渐进式搜索从文档中的当前位置向下自左至右执行。 可以使用键盘快捷键完成渐进式搜索。  
  
> [!NOTE]  
>  有关键盘快捷键的完整列表，请参阅 [SQL Server Management Studio 键盘快捷键](../../tools/sql-server-management-studio/sql-server-management-studio-keyboard-shortcuts.md)。  
  
## <a name="see-also"></a>另请参阅  
 [搜索和替换](../../relational-databases/scripting/search-and-replace.md)   
 [交互式搜索文档](../../relational-databases/scripting/search-documents-interactively.md)   
 [使用结果列表搜索文档](../../relational-databases/scripting/search-documents-using-results-lists.md)   
 [使用通配符搜索文本](../../relational-databases/scripting/search-text-with-wildcards.md)   
 [使用正则表达式搜索文本](../../relational-databases/scripting/search-text-with-regular-expressions.md)  
  
  
