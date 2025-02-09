---
title: 映射源数据库和目标数据库 (AccessToSQL) |Microsoft 文档
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- database schemas
- mapping, databases
- schemas, mapping to
- schemas, SQL Azure
- schemas, SQL Server
- source database
- target database
ms.assetid: 69bee937-7b2c-49ee-8866-7518c683fad4
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: d2be7854240a52edd8f3308ea92e3ea7eb25924f
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "63299203"
---
# <a name="mapping-source-and-target-databases-accesstosql"></a>映射源数据库和目标数据库 (AccessToSQL)
当您连接到[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]或 SQL Azure，您需要指定目标数据库以进行迁移。 如果您有多个 Access 数据库可以将它们映射到多个[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]数据库 （或架构） 或向下连接的 SQL Azure 数据库的多个架构。  
  
## <a name="sql-server-or-sql-azure-database-schemas"></a>SQL Server 或 SQL Azure 数据库架构  
[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库使用的概念架构将数据库中的对象划分为逻辑组。 例如，图书馆数据库可以使用三个架构名为**书籍**，**音频**，和**视频**相互独立册，音频和视频对象。 默认情况下，access 数据库映射到**主**数据库和**dbo**架构中的[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]和已连接的数据库和**dbo**在 SQL Azure 中的架构。  
  
除非您自定义每个 Access 数据库之间的映射和[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]数据库和架构，SSMA 要迁移的架构和 access 数据库的默认数据库映射到关联的数据。  
  
## <a name="modifying-the-target-database-and-schema"></a>修改目标数据库和架构  
SSMA 可以映射到每个 Access 数据库[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]或 SQL Azure 数据库和架构。 下面的过程描述了如何自定义每个数据库的映射。  
  
**若要修改目标数据库和架构**  
  
1.  在访问元数据资源管理器窗格中，选择**访问元数据**。  
  
    架构映射时，还可用选择**数据库**数据库中的任何节点。 为所选对象自定义架构映射列表。  
  
2.  在右窗格中，单击**架构映射**选项卡。  
  
    您将看到一个表包含访问数据库名称及其相应的 ssNoVersion 或 Sql Azure 架构。 目标架构中的两个部件的表示法 (database.schema) 表示。  
  
3.  选择包含您要自定义，然后单击的映射行**修改**。  
  
4.  在**选择目标架构**对话框，可以浏览可用的目标数据库和架构或类型的数据库和架构两个部件表示法 (database.schema) 的文本框中的名称，然后单击**确定**.  
  
**模式的映射**  
  
-   映射到 SQL Server  
  
您可以将源数据库映射到任何目标数据库。 默认情况下映射源数据库与目标[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]与之有连接使用 SSMA 数据库。 如果要映射的目标数据库上不存在[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]，然后将会有一条消息提示 **"目标中不存在的数据库和/或架构[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]元数据。在同步过程中将创建它。是否想要继续？"** 单击是。 同样，您可以映射到目标下不存在架构的架构[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]将在同步过程中创建的数据库。  
  
-   映射到 SQL Azure  
  
您可以将源数据库映射到连接目标[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]数据库或连接的目标中的任何架构[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]数据库。 如果将源架构映射到已连接的目标数据库下的任何不存在架构，则将会有一条消息提示 **"架构中不存在目标元数据。在同步过程中将创建它。你想要继续吗？"** 单击是。  
  
## <a name="reverting-to-your-initial-database-and-schema"></a>还原为初始数据库和架构  
如果您自定义 Access 数据库之间的映射和一个[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]或 SQL Azure 数据库和架构，您可以还原回您指定连接到的数据库的映射[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]或 SQL Azure。  
  
**若要重置为默认数据库和架构**  
  
1.  在架构映射选项卡下选择任何行，然后单击**重置为默认值**还原为默认数据库和架构。  
  
## <a name="next-step"></a>下一步  
下一步迁移过程中[转换数据库对象](converting-access-database-objects-accesstosql.md)  
  
## <a name="see-also"></a>请参阅  
[Access 数据库迁移到 SQL Server](migrating-access-databases-to-sql-server-azure-sql-db-accesstosql.md)  
  
