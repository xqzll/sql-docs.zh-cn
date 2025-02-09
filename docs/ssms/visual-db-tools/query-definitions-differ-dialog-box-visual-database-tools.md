---
title: “查询定义不同”对话框 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdtsql.chm:69639
- vdtsql.chm:69640
- vdt.dlgbox.querydefinitionsdiffer
ms.assetid: 90383473-2922-40e5-9682-3850849aa856
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 4e065ac17e913d766813076df75a6a65ffe9472e
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "65098272"
---
# <a name="query-definitions-differ-dialog-box-visual-database-tools"></a>“查询定义不同”对话框 (Visual Database Tools)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
此对话框可通知您查询无法以图形形式显示在“关系图”窗格和“条件”窗格中，因此您只能在 SQL 窗格中编辑查询。  
  
在 SQL 窗格中输入或编辑 SQL 语句，然后移动到另一个窗格，验证查询或尝试执行查询，并且符合以下条件之一时，将显示此对话框：  
  
-   SQL 语句不完整或者包含一个或多个语法错误。  
  
-   SQL 语句有效但在图形窗格中不支持（如联合查询）。  
  
-   SQL 语句有效但包含特定于所使用数据连接的语法。  
  
> [!TIP]  
> 可以使用“查询”  工具栏上的“验证 SQL 语句”  按钮来检查语句是否有效。  
  
该对话框将显示一条消息，指示不能显示 SQL 语句的原因，并询问如何继续。  
  
> [!NOTE]  
> 如果已经隐藏了“关系图”窗格和“条件”窗格，则不会显示“查询定义不同”  对话框。  
  
## <a name="options"></a>选项  
**“忽略”按钮**  
选择此按钮可指定接受 SQL 语句，以进一步编辑语句或执行语句。 如果接受语句，“关系图”窗格和“条件”窗格将显示为灰色，以指示不能它们显示 SQL 窗格中的语句。  
  
**“撤消”按钮**  
选择此按钮可放弃对 SQL 窗格中内容所做的更改。  
  
> [!NOTE]  
> 如果语句正确但不支持以图形形式在查询和视图设计器中显示，那么即使语句不能在“关系图”窗格和“条件”窗格中显示，您也可以执行它。 例如，如果输入联合查询，该语句可以执行，但不能在其他窗格中显示。  
  
## <a name="see-also"></a>另请参阅  
[查询和视图设计器工具 (Visual Database Tools)](../../ssms/visual-db-tools/query-and-view-designer-tools-visual-database-tools.md)  
  
