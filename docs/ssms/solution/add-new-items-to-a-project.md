---
title: 向项目添加新项 | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- projects [SQL Server Management Studio], item additions
- adding project items
ms.assetid: 76af8692-324f-4f5e-b1a0-d72ca8a107e3
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: fcb6d5e1a811f13a346a3daf89de459273cd2140
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "65105348"
---
# <a name="add-new-items-to-a-project"></a>向项目添加新项
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
向项目中添加新项，以扩展应用程序功能。 新项可以是查询或连接。 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 包含两个项目类型：[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 脚本项目和 Analysis Services 脚本项目。 至于哪些项可以添加到项目中，这取决于项目类型。 例如，可以将 [!INCLUDE[tsql](../../includes/tsql-md.md)] 查询（扩展名为 .sql 的文件）添加到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 脚本项目，但是不能将其添加到 Analysis Services 脚本项目。  
  
[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 不允许在项目中创建文件夹。 若要组织您的工作，请在解决方案中创建多个项目。  
  
### <a name="to-add-a-new-query-to-an-existing-project"></a>在现有项目中添加新查询  
  
1.  在解决方案资源管理器中，选择目标项目。  
  
2.  在 **“项目”** 菜单上，单击 **“添加新项”** 。  
  
3.  在“添加新项”  对话框的左窗格中，选择一个类别。  
  
4.  在右窗格中选择一个查询模板，再单击“添加”  。 新查询随即被添加到项目的“查询”  文件夹中。  
  
5.  在“连接到数据库引擎”  对话框中，为新查询指定一个连接，再单击“连接”  。 如果不希望将连接与新查询关联，可以在连接对话框中单击“取消”  。  
  
6.  如果需要，可在解决方案资源管理器中重命名查询。  
  
### <a name="to-add-a-new-connection-to-an-existing-project"></a>在现有项目中添加新连接  
  
1.  在解决方案资源管理器中，选择目标项目。  
  
2.  在 **“项目”** 菜单上，单击 **“添加新项”** 。  
  
3.  在左窗格中选择“连接”  。  
  
4.  在右窗格中选择“新建连接”  ，再单击“添加”  。  
  
5.  在“连接到数据库引擎”  对话框中，为新查询指定一个连接，再单击“连接”  。 新连接随即被添加到项目的“连接”  文件夹中。  
  
## <a name="see-also"></a>另请参阅  
[解决方案资源管理器](../../ssms/solution/solution-explorer.md)  
[将文件扩展名与代码编辑器关联](../../relational-databases/scripting/associate-file-extensions-to-a-code-editor.md)  
[向项目中添加现有项](../../ssms/solution/add-existing-items-to-a-project.md)  
[移除或删除项或项目](../../ssms/solution/remove-or-delete-an-item-or-project.md)  
  
