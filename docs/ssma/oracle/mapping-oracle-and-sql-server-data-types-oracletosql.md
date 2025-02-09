---
title: 映射 Oracle 和 SQL Server 数据类型 (OracleToSQL) |Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Type Mapping Inheritance
ms.assetid: 05da1495-63b9-47b7-86e2-6746394a2d8a
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.openlocfilehash: 06e538ebbdab9d6438182eaa0b61d44818286547
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "62796018"
---
# <a name="mapping-oracle-and-sql-server-data-types-oracletosql"></a>映射 Oracle 和 SQL Server 数据类型 (OracleToSQL)
Oracle 数据库类型不同于[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]数据库类型。 转换到的 Oracle 数据库对象时[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]对象，您必须指定如何将数据类型从 oracle 迁移到[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。 可以接受默认数据类型映射，也可以自定义映射，如以下各节中所示。  
  
## <a name="default-mappings"></a>默认映射  
SSMA 具有一组默认的数据类型映射。 有关默认映射的列表，请参阅[项目设置&#40;类型映射&#41; &#40;OracleToSQL&#41;](../../ssma/oracle/project-settings-type-mapping-oracletosql.md)。  
  
## <a name="type-mapping-inheritance"></a>映射继承的类型  
您可以自定义在项目级别、 对象 （例如所有存储过程） 的类别级别或对象级别的类型映射。 除非它们在较低级别重写从更高级别继承设置。 例如，如果您将映射**smallmoney**到**资金**在项目级别，该项目中的所有对象将都使用此映射，除非你自定义对象或类别级别的映射。  
  
当您查看**类型映射**SSMA，在后台中的选项卡了彩色编码来显示继承的类型映射。 黄色表示任何继承的类型映射，并在当前级别上指定任何映射的白色背景的类型映射。  
  
## <a name="customizing-data-type-mappings"></a>自定义数据类型映射  
以下过程演示如何在项目、 数据库或对象级别的数据类型映射：  
  
**若要将数据类型映射**  
  
1.  若要自定义整个项目的数据类型映射，请打开**项目设置**对话框：  
  
    1.  上**工具**菜单中，选择**项目设置**。  
  
    2.  在左窗格中，选择**类型映射**。  
  
        类型映射表和按钮显示在右窗格中。  
  
    或者，若要自定义数据类型映射在数据库、 表、 视图或存储的过程级别选择数据库、 对象类别或对象 Oracle 元数据资源管理器中：  
  
    1.  在 Oracle 元数据资源管理器中，选择要自定义对象的文件夹。  
  
    2.  在右窗格中，单击**类型映射**选项卡。  
  
2.  若要添加新的映射，请执行以下操作：  
  
    1.  单击 **“添加”** 。  
  
    2.  下**源类型**，选择要映射的 Oracle 数据类型。  
  
    3.  如果类型要求长度，指定映射中的最小数据长度**从**框和中的最大数据长度**到**框。  
  
        这允许您自定义的相同的数据类型的更小且更大值的数据映射。  
  
    4.  下**目标类型**，选择目标[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]数据类型。  
  
        某些类型需要目标数据类型长度。 如果需要，输入中的新数据长度**替换为**框。  
  
    5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
3.  若要修改的数据类型映射，请执行以下操作：  
  
    1.  单击 **“编辑”** 。  
  
    2.  下**源类型**，选择要映射的 Oracle 数据类型。  
  
    3.  如果类型要求长度，指定映射中的最小数据长度**从**框和中的最大数据长度**到**框。  
  
        这允许您自定义的相同的数据类型的更小且更大值的数据映射。  
  
    4.  下**目标类型**，选择目标[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]数据类型。  
  
        某些类型需要目标数据类型长度。 如果需要，输入中的新数据长度**替换为**框中，然后 [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
4.  若要删除自定义数据类型映射，请执行以下操作：  
  
    1.  包含你想要删除的数据类型映射的类型映射列表中选择行。  
  
    2.  单击 **“删除”** 。  
  
        不能删除继承的映射。 但是，由特定对象或对象类别的自定义映射中重写继承的映射。  
  
## <a name="next-steps"></a>后续步骤  
迁移过程中的下一步是为[创建评估报告](assessing-oracle-schemas-for-conversion-oracletosql.md)或[将 Oracle 数据库对象转换为 SQL Server 语法](converting-oracle-schemas-oracletosql.md)。 如果您创建评估报告，Oracle 对象会自动转换在评估期间。  
  
## <a name="see-also"></a>请参阅  
[迁移的 Oracle 数据库移到 SQL Server &#40;OracleToSQL&#41;](../../ssma/oracle/migrating-oracle-databases-to-sql-server-oracletosql.md)  
  
