---
title: 处理 SSMA 项目 (OracleToSQL) |Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Customizing Project Settings
ms.assetid: ee5d94c0-c7a6-4779-bd32-729bdaf61e1b
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.openlocfilehash: 3ec3a2f9bcdf43657649263d77eff3b31c9a57a3
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "63283554"
---
# <a name="working-with-ssma-projects-oracletosql"></a>处理 SSMA 项目 (OracleToSQL)
将 Oracle 数据库迁移到[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]，首先创建 SSMA 项目。 项目是一个文件包含以下信息：  
  
-   想要迁移到的 Oracle 数据库的相关元数据[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。  
  
-   有关的目标实例的元数据[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]将接收迁移的对象和数据。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 连接信息。  
  
-   项目设置。  
  
当您打开一个项目时，它从断开连接时 Oracle 和[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。 允许您在脱机工作。 了解如何重新连接到[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]，请参阅[连接到 SQL Server &#40;OracleToSQL&#41;](../../ssma/oracle/connecting-to-sql-server-oracletosql.md)。  
  
## <a name="reviewing-default-project-settings"></a>查看默认项目设置  
SSMA 进行转换和加载数据库对象，迁移数据，并且同步与 Oracle 的 SSMA 包含多个设置和[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。 默认设置是适用于多个用户。 但是，创建一个新的 SSMA 项目之前，应查看的设置。 如果愿意，可以更改将用于所有新项目的默认设置。  
  
**若要查看默认项目设置**  
  
1.  上**工具**菜单上，单击**默认项目设置**。  
  
2.  选择项目类型中的**迁移目标版本**下拉列表中的哪些是需要设置要查看或更改，然后单击**常规**选项卡。  
  
3.  在左窗格中，单击**转换**。  
  
4.  在右窗格中，查看并根据需要更改的设置。 有关这些设置的详细信息，请参阅[项目设置&#40;转换&#41; &#40;OracleToSQL&#41;](../../ssma/oracle/project-settings-conversion-oracletosql.md)。  
  
5.  重复步骤 1-3 的迁移、 同步、 加载系统对象、 GUI，和类型映射页。  
  
    -   有关迁移设置的信息，请参阅[项目设置&#40;迁移&#41; &#40;OracleToSQL&#41;](../../ssma/oracle/project-settings-migration-oracletosql.md)。  
  
    -   有关系统对象设置的信息，请参阅[项目设置&#40;加载系统对象&#41; &#40;OracleToSQL&#41;](../../ssma/oracle/project-settings-loading-system-objects-oracletosql.md)。  
  
    -   有关设置同步到信息[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]，请参阅[项目设置&#40;同步&#41; &#40;OracleToSQL&#41;](../../ssma/oracle/project-settings-synchronization-oracletosql.md)。  
  
    -   有关 GUI 设置的信息，请参阅[项目设置&#40;GUI&#41; &#40;OracleToSQL&#41;](../../ssma/oracle/project-settings-gui-oracletosql.md)。  
  
    -   有关数据类型映射设置的信息，请参阅[项目设置&#40;类型映射&#41; &#40;OracleToSQL&#41;](../../ssma/oracle/project-settings-type-mapping-oracletosql.md)。  
  
## <a name="creating-new-projects"></a>创建新项目  
若要将数据从 Oracle 数据库到迁移[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]，首先必须创建一个项目。  
  
**若要创建项目**  
  
1.  上**文件**菜单上，单击**新项目**。  
  
    此时将显示“新建项目”  对话框。  
  
2.  在中**名称**框中，输入你的项目的名称。  
  
3.  在中**位置**框中，输入或选择的项目文件夹，然后单击**确定**。  
  
4.  在中**迁移到**下拉列表中，选择的目标版本[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]用于迁移。 可用选项包括：  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2005  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2008  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2014  
  
    -   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 2016  
  
    -   Azure SQL DB  
  
## <a name="customizing-project-settings"></a>自定义项目设置  
除了定义应用于所有新的 SSMA 项目的默认项目设置，可以自定义每个项目的设置。 有关详细信息，请参阅[设置项目选项&#40;OracleToSQL&#41;](../../ssma/oracle/setting-project-options-oracletosql.md)。  
  
自定义源和目标数据库之间的数据类型映射时，可以定义项目、 数据库或对象级别上的映射。 有关详细信息，请参阅[映射 Oracle 和 SQL Server 数据类型&#40;OracleToSQL&#41;](../../ssma/oracle/mapping-oracle-and-sql-server-data-types-oracletosql.md)。  
  
## <a name="saving-projects"></a>正在保存项目  
当保存项目时，SSMA 将保留项目设置，和 （可选） 数据库元数据，对项目文件。  
  
**若要保存项目**  
  
-   上**文件**菜单上，单击**保存项目**。  
  
    如果项目中的架构已更改，或者尚未转换，SSMA 将提示您加载和保存元数据。 加载和保存元数据将允许您脱机工作。 它还允许您将完整的项目文件发送给其他人，例如技术支持人员。 如果系统提示保存元数据，请执行以下操作：  
  
    1.  有关显示的状态为每个架构**元数据缺少**，选择数据库名称旁边的复选框。  
  
        正在保存元数据可能需要几分钟的时间。 如果您不希望保存元数据，不选中任何复选框。  
  
    2.  单击“保存”  按钮。  
  
        SSMA 会分析 Oracle 架构并将元数据保存到项目文件。  
  
## <a name="opening-projects"></a>打开项目  
从 Oracle 和断开时打开的项目， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。 允许您在脱机工作。 若要更新的元数据，数据库将对象加载到[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。 若要将数据迁移，你必须重新连接到 Oracle 和[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。  
  
**若要打开的项目**  
  
1.  可使用下列过程之一：  
  
    -   上**文件**菜单，依次指向**最近使用的项目**，然后单击你想要打开的项目。  
  
    -   上**文件**菜单中，选择**打开项目**，找到.o2ssproj 项目文件中，选择的文件，然后单击**打开**。  
  
2.  若要重新连接到 Oracle 上,**文件**菜单上，单击**重新连接到 Oracle**。  
  
3.  若要重新连接到[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]，然后在**文件**菜单中，单击**重新连接到 SQL Server**。  
  
## <a name="next-step"></a>下一步  
迁移过程中的下一步是[连接到 Oracle 数据库 (OracleToSQL)](https://msdn.microsoft.com/e276cdbf-3ebc-4ba8-b40d-a7a42befa2b6)。  
  
## <a name="see-also"></a>请参阅  
[迁移的 Oracle 数据库移到 SQL Server &#40;OracleToSQL&#41;](../../ssma/oracle/migrating-oracle-databases-to-sql-server-oracletosql.md)  
[连接到 Oracle 数据库&#40;OracleToSQL&#41;](../../ssma/oracle/connecting-to-oracle-database-oracletosql.md)  
[连接到 SQL Server &#40;OracleToSQL&#41;](../../ssma/oracle/connecting-to-sql-server-oracletosql.md)  
  
