---
title: 协调数据库关系图与已修改的数据库 | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- updating diagram to match database
- reconciling database diagrams
- diagrams [SQL Server], reconciling changes
- updating database to match diagram
- database diagrams [SQL Server], reconciling changes
ms.assetid: eda8dea2-eedd-43a7-85aa-92bd97783b5f
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: bdab377da65fc9dd4068a5d3fc67eecf48655405
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "65098096"
---
# <a name="reconcile-a-database-diagram-with-a-modified-database-visual-database-tools"></a>协调数据库关系图与已修改的数据库 (Visual Database Tools)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
当您准备好对数据库进行更新以与您的关系图匹配时，即可保存数据库关系图。 但是，如果其他用户在您打开关系图后更新了相应的数据库，他们的更改可能会影响您的关系图，同样如果您在其他用户打开关系图后更新数据库，那么您的更改也会影响他们的关系图。  
  
保存关系图将通过改写其他用户的更改来使数据库与您的关系图一致，以便数据库与关系图匹配。  
  
### <a name="to-update-a-database-to-match-your-diagram"></a>更新数据库以匹配关系图  
  
1.  保存数据库关系图。  
  
    如果以前未保存过关系图，请在“保存新的数据库关系图”  对话框中为该关系图键入名称，再选择“确定”  。  
  
2.  “保存”  对话框会列出在保存关系图时将受到影响的表。 选择“是”  继续执行操作。  
  
3.  “检测到数据库更改”  对话框将列出已修改并将进行更改以与关系图匹配的对象。 选择“是”  以保存该关系图并接受更改列表。  
  
    > [!NOTE]  
    > 如果您的关系图中包含已在数据库中删除的表和列，那么当您保存关系图时，数据库中只会重新创建其定义。 此过程无法还原删除这些对象之前存在于这些对象中的任何数据。  
  
### <a name="to-update-your-diagram-to-match-a-modified-database"></a>更新关系图以与已修改的数据库匹配  
  
1.  关闭关系图而不保存更改。  
  
2.  在对象资源管理器中右键单击该关系图。  
  
3.  在快捷菜单中单击“刷新”  。  
  
4.  重新打开该关系图。  
  
## <a name="see-also"></a>另请参阅  
[使用数据库关系图 (Visual Database Tools)](../../ssms/visual-db-tools/work-with-database-diagrams-visual-database-tools.md)  
  
