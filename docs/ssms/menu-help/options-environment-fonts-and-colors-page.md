---
title: 选项（“环境”-“字体和颜色”页）| Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
ms.assetid: ea3aa222-538d-485f-99dc-01eb02cdcfea
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 755cc08f8e431e062ce9fdf3049d99453d724be6
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "65098378"
---
# <a name="options-environment---fonts-and-colors-page"></a>选项（“环境” - “字体和颜色”页）
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
使用“选项”  对话框可以为 [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中的各种用户界面元素建立自定义的字体和配色方案。 在“工具”  菜单上，单击“选项”  ，展开“环境”  文件夹，然后选择“字体和颜色”  。  
  
在更改配色方案的会话期间，更改不会生效。 您可以通过打开 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 的另一个实例，并将其设置为您的更改要应用的环境，来评估颜色更改效果。  
  
## <a name="uielement-list"></a>UIElement 列表  
**显示其设置**  
列出可以为其更改字体和配色方案的所有用户界面元素。 从此列表中选择某项后，即可自定义“显示项”  中所选项的颜色设置。  
  
|术语|定义|  
|--------|--------------|  
|文本编辑器|更改文本编辑器的字形、字号和颜色显示设置，会影响默认文本编辑器中文本的外观。 在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 之外的文本编辑器中打开的文档将不会受到这些设置的影响。|  
|打印机|更改打印机的字形、字号和颜色显示设置，会影响打印文档中文本的外观。<br /><br />注意：选择的默认打印字体可以不同于文本编辑器中的默认显示字体。 在打印代码同时包含单字节字符和双字节字符时，这可能非常有用。|  
|[全部文本工具窗口 **]**|更改此项的字形、字号和颜色显示设置，会影响那些有输出窗格的 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]工具窗口中文本的外观。 例如，“输出”窗口、“文本结果”窗口等。<br /><br />注意：在更改 [全部文本工具窗口] 项的文本的会话期间，更改不会生效。 通过打开 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]的另一个实例，可以评估这些更改的效果。|  
|“查找结果”窗口|更改此项的字形、字号和颜色显示设置，会影响“查找结果”窗口中文本的外观。|  
|输出窗口|更改此项的字形、字号和颜色显示设置，会影响“输出”窗口中文本的外观。|  
|网格结果|更改此项的字形、字号和颜色显示设置，会影响“查询”窗口的“网格结果”  区域中文本的外观。|  
|执行计划|更改此项的字形、字号和颜色显示设置，会影响 [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 和 [!INCLUDE[ssEW](../../includes/ssew-md.md)] 查询的“执行计划”中文本的外观。|  
|文本结果|更改此项的字形、字号和颜色显示设置，会影响“查询”窗口的“文本结果”  区域中文本的外观。|  
|商业智能设计器|更改此项的字形、字号和颜色显示设置，会影响“商业智能设计器”窗口中文本的外观。|  
  
**使用默认值**  
“使用默认值”  按钮可以重置从“显示其设置”  列表中选择的列表项的默认字体值和颜色值。  
  
**字体(粗体表示等宽字体)**  
列出系统上安装的所有字体。 如果第一次打开此下拉列表，则会选中“显示其设置”  列表中所选元素的当前字体。 固定字体（更易于在编辑器中对齐）显示为粗体。  
  
**大小**  
列出选定字体的可用磅值。 更改字体大小会影响选择的“显示其设置”  的所有“显示项”  。  
  
**显示项**  
列出可以修改其前景色和背景色的项。  
  
> [!NOTE]  
>  默认显示项为“文本”。 这样，分配给“文本”的属性将会被分配给其他显示项的属性覆盖。 例如，如果将蓝色分配给“文本”  并将绿色分配给“标识符”，则所有标识符将显示为绿色。 在此示例中，“标识符”属性覆盖了“文本”属性。  
  
一些显示项包括：  
  
-   指示器边距：显示断点和书签图标的代码编辑器的左边距。  
  
-   可折叠的文本：可以在代码编辑器（仅 XML）内显示或隐藏的文本块或代码块。  
  
**项前景色**  
列出可以为“显示项”  中选定项的前景选择的可用颜色。 因为某些项是相关的，所以应该始终使用一致的显示方案；例如，更改文本的前景色也会更改“字符串”等元素的前景色。  
  
**自定义**  
显示“颜色”  对话框，在其中可以为“显示项”  列表中所选的项设置自定义颜色。  
  
> [!NOTE]  
> 定义自定义颜色的能力可能会受到计算机显示屏的颜色设置的限制。 例如，如果计算机设置为显示 256 色，并且从“颜色”  对话框中选择自定义颜色，那么 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 会在“基本颜色”  中选择最接近的可用值作为默认值，并且会在“颜色”  对话框中显示黑色。  
  
**项背景色**  
提供一个调色板，可以用来为“显示项”  中选定的项选择背景色。 因为某些项是相关的，所以应该始终使用一致的显示方案；例如，更改文本的背景色也会更改“SQL 字符串”等元素的背景色。  
  
**Custom**  
显示“颜色”  对话框，在其中可以为“显示项”  列表中所选的项设置自定义颜色。  
  
**加粗**  
选中此复选框可以将选定“显示项”的文本以粗体显示。 粗体文本在编辑器中更易于辨别。  
  
**示例**  
显示在“显示其设置”  和“显示项”  中选定值的字形、字号和颜色方案的示例。 在尝试不同格式设置选项时，您可以使用此文本框来预览结果。  
  
## <a name="see-also"></a>另请参阅  
[代码编辑器中的颜色代码](../../relational-databases/scripting/color-coding-in-query-editors.md)  
[选项（“文本编辑器/编辑器选项卡和状态栏”页）](https://msdn.microsoft.com/e4815678-7885-4631-878f-c6a2b857ee05)  
  
