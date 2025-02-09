---
title: 如何：打开 SQL Server 单元测试以进行编辑 | Microsoft Docs
ms.custom:
- SSDT
ms.date: 02/09/2017
ms.prod: sql
ms.technology: ssdt
ms.reviewer: ''
ms.topic: conceptual
ms.assetid: c6af1b12-54cd-42f9-b2ef-7164f8078323
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: d464ba2cd7b3b5b3cb2ac687f9f9e1b3ae8023b0
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "65098448"
---
# <a name="how-to-open-a-sql-server-unit-test-to-edit"></a>如何：打开 SQL Server 单元测试以进行编辑
在创建 SQL Server 单元测试之后，你可以使用  “SQL Server 单元测试设计器”添加 Transact\-SQL 语句和测试条件。 使用设计器创建的测试将会生成 Visual C# 或 Visual Basic 代码。 此代码即为测试运行时所执行的代码。  
  
如果您对您的测试满意，则可以按原样运行它。 如果您想要为此单元测试添加更多功能，则可以编辑其代码。 此代码位于测试项目的 .cs 或 .vb 文件中。 有关详细信息，请参阅 [SQL Server 单元测试文件](../ssdt/sql-server-unit-test-files.md)。 也可以通过创建新的测试条件来自定义您的测试。 有关详细信息，请参阅[如何：为数据库单元测试设计器创建测试条件 (Visual Studio 2010)](https://msdn.microsoft.com/library/aa833409(VS.100).aspx)。  
  
> [!NOTE]  
> 如果你通过编辑 .cs 或 .vb 文件来删除某个测试方法，则该测试方法仍将出现在“SQL Server 单元测试设计器”  中。 出现这种情况的原因是，测试类的 InitializeComponent 方法仍包含用于此测试的成员变量。 尽管此测试会出现在设计器中，但因为其代码已不存在，所以您无法运行此测试。 若要重新生成此测试的测试方法，请在编辑器中编辑 Transact\-SQL，然后保存 .cs 或 .vb 测试文件，或者也可以重新生成此测试项目。  
  
### <a name="to-open-the-source-code-file-of-a-sql-server-unit-test-from-solution-explorer"></a>从解决方案资源管理器中打开 SQL Server 单元测试的源代码文件  
  
-   在“解决方案资源管理器”  中，右键单击包含 SQL Server 单元测试的源代码文件，然后单击“查看代码”  。  
  
    当源代码文件打开时将会在 Visual Studio 的主编辑窗口中显示单元测试的测试方法。  
  
### <a name="to-open-the-source-code-file-of-a-sql-server-unit-test-from-the-test-view-window-visual-studio-2010"></a>从“测试视图”窗口中打开 SQL Server 单元测试的源代码文件 (Visual Studio 2010)  
  
1.  运行单元测试。 有关详细信息，请参阅[演练：创建和运行 SQL Server 单元测试](../ssdt/walkthrough-creating-and-running-a-sql-server-unit-test.md)中的“运行 SQL Server 单元测试”一节。  
  
2.  在“测试视图”窗口中，右键单击此测试，然后单击“打开测试”  。  
  
    当源代码文件打开时将会在 Visual Studio 的主编辑窗口中显示单元测试的测试方法。  
  
### <a name="to-open-the-source-code-file-of-a-sql-server-unit-test-from-the-test-view-window-visual-studio-2012"></a>从“测试视图”窗口中打开 SQL Server 单元测试的源代码文件 (Visual Studio 2012)  
  
1.  运行单元测试。 有关详细信息，请参阅[演练：创建和运行 SQL Server 单元测试](../ssdt/walkthrough-creating-and-running-a-sql-server-unit-test.md)中的“运行 SQL Server 单元测试”一节。  
  
2.  在“测试资源管理器”窗口中，单击单元测试源代码文件的名称。  
  
    当源代码文件打开时将会在 Visual Studio 的主编辑窗口中显示单元测试的测试方法。  
  
## <a name="see-also"></a>另请参阅  
[创建和定义 SQL Server 单元测试](../ssdt/creating-and-defining-sql-server-unit-tests.md)  
[使用 SQL Server 单元测试验证数据库代码](../ssdt/verifying-database-code-by-using-sql-server-unit-tests.md)  
  
