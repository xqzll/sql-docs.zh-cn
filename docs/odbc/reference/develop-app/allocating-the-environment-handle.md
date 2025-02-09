---
title: 分配环境句柄 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC drivers [ODBC], environment handles
- allocating environment handles [ODBC]
- connecting to driver [ODBC], environment handles
- environment handles [ODBC]
- data sources [ODBC], environment handles
- connecting to data source [ODBC], environment handles
- handles [ODBC], environment
ms.assetid: 77b5d1d6-7eb7-428d-bf75-a5c5a325d25c
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7a8eefe5bc6678462099afda8381d6b16bd076dd
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "63287665"
---
# <a name="allocating-the-environment-handle"></a>分配环境句柄
任何 ODBC 应用程序的第一个任务是加载驱动程序管理器;如何做到这一点与操作系统相关。 例如，在运行 Microsoft® Windows NT® Server/Windows 2000 Server、 Windows NT 工作站/Windows 2000 Professional 或 Microsoft Windows® 95/98 的计算机，该应用程序或者链接到驱动程序管理器库或调用**LoadLibrary**加载驱动程序管理器 DLL。  
  
 必须在应用程序可以调用任何其他 ODBC 函数之前完成，下一个任务是初始化 ODBC 环境并分配环境句柄，之后，如下所示：  
  
1.  应用程序声明类型 SQLHENV 的变量。 然后，它调用**SQLAllocHandle** ，并将传递此变量和 SQL_HANDLE_ENV 选项的地址。 例如：  
  
    ```  
    SQLHENV henv1;  
  
    SQLAllocHandle(SQL_HANDLE_ENV, SQL_NULL_HANDLE, &henv1);  
    ```  
  
2.  驱动程序管理器分配要在其中存储有关环境的信息的结构，并在变量中返回的环境句柄。  
  
 驱动程序管理器不会调用**SQLAllocHandle**此驱动程序中的时间，因为它不知道要调用的驱动程序。 它会调用延迟**SQLAllocHandle**驱动程序直到应用程序调用一个函数来连接到数据源中。 有关详细信息，请参阅[的连接过程中的驱动程序管理器角色](../../../odbc/reference/develop-app/driver-manager-s-role-in-the-connection-process.md)稍后在本部分中。  
  
 完成后使用 ODBC 的应用程序，它释放环境句柄与**SQLFreeHandle**。 释放环境后, 是编程错误应用程序对 ODBC 函数; 的调用中使用的环境句柄这样做存在未定义，但可能严重后果。  
  
 当**SQLFreeHandle**调用时，该结构用于存储有关环境的信息的驱动程序版本。 请注意， **SQLFreeHandle**后已释放该环境句柄上的所有连接句柄不能为环境句柄之前调用。  
  
 有关环境句柄的详细信息，请参阅[环境处理](../../../odbc/reference/develop-app/environment-handles.md)。
