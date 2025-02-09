---
title: 状态栏（数据库引擎查询编辑器）| Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.technology: scripting
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: e7f2d6f4-bb94-4cf5-a096-c34397e679af
author: markingmyname
ms.author: maghan
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 1c93fcf0c19f41f1dfbb3f2e44a95b623836ebca
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "65821850"
---
# <a name="status-bar-database-engine-query-editor"></a>状态栏（数据库引擎查询编辑器）
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
  [!INCLUDE[ssDE](../../includes/ssde-md.md)] 查询编辑器窗口的状态栏可进行颜色编码，以便指示每个窗口连接到的 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 实例。  
  
1.  **开始之前：** [状态栏颜色](#StatusBarColors)  
  
2.  **在以下位置设置服务器状态颜色的具体步骤：** [对象资源管理器](#SetOEServerColor)、[注册服务器](#SetRegServerColor)  
  
3.  **使用状态颜色的具体步骤：** [使用服务器颜色打开查询编辑器](#OpenServerColor)、[打开指定状态颜色的查询编辑器](#OpenSpecColor)  
  
##  <a name="StatusBarColors"></a> 状态栏颜色  
 您可以在 **“对象资源管理器”** 或 **“已注册服务器”** 中将状态栏颜色与特定的服务器节点相关联。 只能为连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]实例的服务器节点指定颜色，不能为针对其他 SQL Server 技术的服务器节点指定颜色。 您还可以在每次将新的 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 查询编辑器窗口连接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]实例时，指定自定义状态栏颜色。 然后，您可以使用为服务器节点定义的状态颜色打开查询编辑器窗口，或者为该编辑器窗口指定唯一颜色。  
  
 在对象资源管理器中为服务器节点设置自定义的状态栏颜色必须在进行连接时完成。 若要更改与某一现有服务器节点相关联的颜色，您必须首先断开连接，然后重新连接并且指定新颜色。  
  
##  <a name="SetOEServerColor"></a> 在对象资源管理器中为服务器设置状态颜色  
 **在对象资源管理器中设置服务器状态颜色**  
  
1.  在“对象资源管理器”中，选择“连接”按钮，然后选择“数据库引擎…”    。  
  
2.  在“连接到服务器”对话框上，选择“选项 >>”   。  
  
3.  选中 **“使用自定义颜色”** 复选框。  
  
4.  若要选择颜色，请选择“选择...”按钮  。  
  
5.  选择基础颜色或自定义颜色，然后选择“确定”。  
  
6.  填写其余连接信息，然后选择 **“连接”** 按钮。  
  
##  <a name="SetRegServerColor"></a> 为已注册服务器设置状态颜色  
 **为已注册服务器设置服务器颜色**  
  
1.  在“已注册服务器”中，右键单击服务器节点，然后选择“属性…”   。  
  
2.  在 **“编辑服务器注册属性”** 对话框中，选择 **“连接属性”** 选项卡。  
  
3.  选中 **“使用自定义颜色”** 复选框。  
  
4.  若要选择颜色，请选择“选择...”按钮  。  
  
5.  选择基础颜色或自定义颜色，然后选择“确定”。  
  
6.  在 **“编辑服务器注册属性”** 对话框中，选择 **“保存”** 按钮。  
  
##  <a name="OpenServerColor"></a> 使用服务器颜色打开编辑器  
 **使用服务器颜色打开编辑器窗口**  
  
-   右键单击“对象资源管理器”或“已注册服务器”中的服务器节点，然后选择“新建查询”    。  
  
-   或者，突出显示服务器节点，然后选择 **“新建查询”** 工具栏按钮。  
  
-   编辑器窗口中的状态栏将使用为关联服务器定义的颜色。  
  
##  <a name="OpenSpecColor"></a> 打开编辑器并且指定状态颜色  
 **打开编辑器窗口并且指定状态颜色**  
  
-   打开 **“文件”** 菜单，选择 **“新建”** ，然后选择 **“数据库引擎查询”** 。  
  
-   在“连接到服务器”对话框上，选择“选项 >>”   。  
  
-   选中 **“使用自定义颜色”** 复选框。  
  
-   若要选择颜色，请选择“选择...”按钮  。  
  
-   选择基础颜色或自定义颜色，然后选择“确定”。  
  
-   填写其余连接信息，然后选择 **“连接”** 按钮。  
  
## <a name="see-also"></a>另请参阅  
 [查询和文本编辑器 (SQL Server Management Studio)](../../relational-databases/scripting/query-and-text-editors-sql-server-management-studio.md)  
  
  
