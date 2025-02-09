---
title: 连接到 Azure SQL DB (MySQLToSQL) |Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Connecting to SQL Azure, SQL Azure permissions
- Connecting to SQL Azure, synchronization
ms.assetid: d0b6f16a-1880-459d-a0c7-28b7ef15c56a
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 23d018a8d551a5c3a7f2978339b6cf7612f378fd
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "63253278"
---
# <a name="connecting-to-azure-sql-db-mysqltosql"></a>连接到 Azure SQL DB (MySQLToSQL)
若要将 MySQL 数据库迁移到 SQL Azure，必须连接到 SQL Azure 的目标实例。 连接时，SSMA 获取有关 SQL Azure 实例中的所有数据库的元数据，并在 SQL Azure 元数据资源管理器中显示数据库元数据。 SSMA 存储的 SQL Azure 连接到，但不存储密码的实例的信息。  
  
与 SQL Azure 的连接保持活动状态，直到关闭该项目。 当你重新打开该项目时，你必须重新连接到 SQL Azure 中，如果想要的活动连接到服务器。 加载到 SQL Azure 数据库对象并将数据迁移之前，您可以脱机工作。  
  
有关 SQL Azure 实例元数据不会自动同步。 相反，若要更新 SQL Azure 元数据资源管理器中的元数据，必须手动更新 SQL Azure 元数据。 有关详细信息，请参阅本主题后面的"同步 SQL Azure 元数据"部分。  
  
## <a name="required-sql-azure-permissions"></a>SQL Azure 所需的权限  
用于连接到 SQL Azure 的帐户需要不同的权限，具体取决于该帐户执行的操作：  
  
-   要转换到 MySQL 对象[!INCLUDE[tsql](../../includes/tsql-md.md)]语法中，更新元数据从 SQL Azure，或者将保存到转换后的语法编写的脚本，该帐户必须有权登录到 SQL Azure 的实例。  
  
-   若要将数据库对象加载到 SQL Azure，最小权限要求是中的成员身份**db_owner**目标数据库中的数据库角色。  
  
## <a name="establishing-a-sql-azure-connection"></a>建立 SQL Azure 连接  
将 MySQL 数据库对象转换为 SQL Azure 语法之前，必须建立到想要迁移或多个 MySQL 数据库的 SQL Azure 实例的连接。  
  
在定义的连接属性时，还可以指定对象和数据将迁移的数据库。 连接到 SQL Azure 后，可以自定义此映射 MySQL 架构级别上。 有关详细信息，请参阅[映射到 SQL Server 架构的 MySQL 数据库&#40;MySQLToSQL&#41;](../../ssma/mysql/mapping-mysql-databases-to-sql-server-schemas-mysqltosql.md)  
  
> [!IMPORTANT]  
> 尝试连接到 SQL Azure 之前，请确保 SQL Azure 的实例正在运行，并且可以接受连接。  
  
**若要连接到 SQL Azure**  
  
1.  上**文件**菜单中，选择**连接到 SQL Azure** （在创建项目后启用此选项）。  
  
    如果以前已连接到 SQL Azure，命令名称将是**重新连接到 SQL Azure**。  
  
2.  在连接对话框中，输入或选择 SQL Azure 的服务器名称。  
  
3.  输入中，选择或**浏览**数据库名称。  
  
4.  输入或选择**用户名**。  
  
5.  输入**密码**。  
  
6.  SSMA 建议加密的连接到 SQL Azure。  
  
7.  单击 **“连接”** 。  
  
> [!IMPORTANT]  
> 适用于 MySQL 的 SSMA 不支持连接到**主**SQL Azure 中的数据库。  
  
## <a name="synchronizing-sql-azure-metadata"></a>同步 SQL Azure 元数据  
有关 SQL Azure 数据库的元数据不会自动更新。 SQL Azure 元数据资源管理器中的元数据是快照元数据时首次连接到 SQL Azure 或上一次你手动更新元数据。 您可以手动更新所有数据库，或任何单个数据库或数据库对象的元数据。  
  
**同步元数据**  
  
1.  请确保你已连接到 SQL Azure。  
  
2.  SQL Azure 元数据资源管理器中，选择你想要更新的数据库架构的数据库旁边的复选框。  
  
    例如，若要更新的所有数据库的元数据，请选择数据库旁边的框。  
  
3.  右键单击数据库，或单个数据库或数据库架构，然后选择**与数据库同步**。  
  
## <a name="next-step"></a>下一步  
迁移的下一步取决于您的项目需求：  
  
-   若要自定义 MySQL 架构和 SQL Azure 数据库和架构之间的映射，请参阅[映射到 SQL Server 架构的 MySQL 数据库&#40;MySQLToSQL&#41;](../../ssma/mysql/mapping-mysql-databases-to-sql-server-schemas-mysqltosql.md)  
  
-   若要自定义项目的配置选项，请参阅[设置项目选项&#40;MySQLToSQL&#41;](../../ssma/mysql/setting-project-options-mysqltosql.md)  
  
-   若要自定义源和目标数据类型的映射，请参阅[映射 MySQL 和 SQL Server 数据类型&#40;MySQLToSQL&#41;](../../ssma/mysql/mapping-mysql-and-sql-server-data-types-mysqltosql.md)  
  
-   如果不需要执行任何这些任务，可以将 MySQL 数据库对象定义转换到 SQL Azure 对象定义。 有关详细信息，请参阅[转换 MySQL 数据库&#40;MySQLToSQL&#41;](../../ssma/mysql/converting-mysql-databases-mysqltosql.md)  
  
## <a name="see-also"></a>请参阅  
[迁移 MySQL 数据库移到 SQL Server-Azure SQL 数据库&#40;MySQLToSql&#41;](../../ssma/mysql/migrating-mysql-databases-to-sql-server-azure-sql-db-mysqltosql.md)  
  
