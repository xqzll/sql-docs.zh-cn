---
title: “调用堆栈”窗口 | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.technology: scripting
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- Call Stack Window [Transact-SQL]
ms.assetid: ddb0b19c-87cd-4883-bcb8-ec09ffb30369
author: markingmyname
ms.author: maghan
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 0b8d2845aafb18a9121a5a44320bb361b62c23d0
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "65821777"
---
# <a name="transact-sql-debugger---call-stack-window"></a>Transact-SQL 调试器 -“调用堆栈”窗口
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
  **“调用堆栈”** 窗口显示调用堆栈中的模块以及传递给这些模块的任意参数的数据类型和值。 [!INCLUDE[tsql](../../includes/tsql-md.md)] 模块包括存储过程、函数和触发器。 只有在调试模式下才可以显示调用堆栈。  
  
## <a name="task-list"></a>任务列表  
 **访问“调用堆栈”窗口**  
  
-   在 **“调试”** 菜单上单击 **“窗口”** ，再单击 **“调用堆栈”** 。  
  
 **更改当前调用堆栈帧**  
  
 可以使用以下任一过程使某个堆栈帧成为当前帧：  
  
-   右键单击该堆栈帧，然后单击“切换到帧”  。  
  
-   双击该堆栈帧。  
  
 **查看当前帧以外的帧的源**  
  
-   右键单击该堆栈帧，然后单击“转到源代码”  。  
  
## <a name="stack-frames"></a>堆栈帧  
 **“调用堆栈”** 窗口中的每一行称为一个堆栈帧，表示一个从 [!INCLUDE[tsql](../../includes/tsql-md.md)] 脚本文件到模块的调用或从一个模块到另一个模块的调用。 所显示的最下面的堆栈帧指示 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 查询编辑器窗口中最先调用此堆栈的行。 最上面一行指示调试器暂停执行时所在的行，由该窗口左边距中的黄色箭头标出。 中间的每一行指示调用下一个更高堆栈帧的模块和源代码的行号。  
  
 **“局部变量”** 、 **“监视”** 和 **“快速监视”** 窗口中的所有表达式都是基于当前堆栈帧求值的。 查询编辑器窗口显示当前帧的代码。 默认情况下，当前堆栈帧是 [!INCLUDE[tsql](../../includes/tsql-md.md)] 调试器暂停执行时所在的帧。 如果使另一个帧成为当前堆栈帧，则 **“局部变量”** 、 **“监视”** 和 **“快速监视”** 窗口中的表达式将在新帧环境下重新求值，且查询编辑器窗口中显示此新帧的源代码。  
  
## <a name="columns"></a>“列”  
 **名称**  
 显示有关调用堆栈中某个模块的信息。  
  
 对于调用堆栈中最下面的一行， **“名称”** 列出查询编辑器源窗口和最先调用此堆栈的行的行号。 对于其他行，“名称”  具有 **Module(Instance.Database)(ParmList) LineNumber** 格式。  
  
 **模块**  
 存储过程、函数或调用下一个帧的存储过程的名称。  
  
 **实例.数据库**  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 的实例和保存模块的数据库。  
  
 **参数列表**  
 指示调用模块过程中传递给该模块的各个参数的数据类型、名称和值。  
  
 **LineNumber**  
 对于除最上面一行以外的所有行， **LineNumber** 指示模块中调用帧的是哪一行。 对于最上面一行， **“行号”** 指示调试器当前聚焦的行。  
  
 **语言**  
 如果是 **，则显示** Transact-SQL [!INCLUDE[tsql](../../includes/tsql-md.md)]。  
  
## <a name="see-also"></a>另请参阅  
 [Transact-SQL 调试器](../../relational-databases/scripting/transact-sql-debugger.md)   
 [Transact-SQL 调试器信息](../../relational-databases/scripting/transact-sql-debugger-information.md)   
 [逐句通过 Transact-SQL 代码](../../relational-databases/scripting/step-through-transact-sql-code.md)  
