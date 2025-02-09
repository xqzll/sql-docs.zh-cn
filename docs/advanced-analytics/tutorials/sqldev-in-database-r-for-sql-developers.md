---
title: 数据库内分析中使用 R 的 SQL Server 机器学习的教程
description: 了解如何将嵌入 R 编程语言在 SQL Server 存储过程和 T-SQL 函数中的代码。
ms.prod: sql
ms.technology: machine-learning
ms.date: 06/13/2019
ms.topic: tutorial
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: 4f0930e3f7f9d037ebb3033cc947f243657a1480
ms.sourcegitcommit: a91c3f4fe2587d474cd4d470bda93239ba2693bb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/14/2019
ms.locfileid: "67140753"
---
# <a name="tutorial-r-data-analytics-for-sql-developers"></a>教程：SQL 开发人员的 R 数据分析
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

在为 SQL 程序员提供本教程中，了解有关 R 集成的生成和部署的基于 R 的机器学习解决方案： 使用[NYCTaxi_sample](demo-data-nyctaxi-in-sql.md)上 SQL Server 数据库。 您将使用 T-SQL、 SQL Server Management Studio，并使用 [机器学习服务] 的数据库引擎实例 ([机器学习服务](../install/sql-machine-learning-services-windows-install.md)和 R 语言支持

本教程向您介绍一种数据建模工作流中使用的 R 函数。 步骤包括数据探索、 构建和训练二元分类模型和模型部署。 将生成该模型预测某个行程是否可能会导致基于时间、 行程，距离和上车位置的提示。 

在本教程中使用的 R 代码的所有包装在存储过程创建并在 Management Studio 中运行。

## <a name="background-for-sql-developers"></a>面向 SQL 开发人员的背景

构建机器学习解决方案的过程很复杂，可以跨多个阶段中涉及多个工具和协调的主题事项专家：

+ 获取并清洗数据
+ 浏览数据和构建适用于建模的功能，
+ 定型集和优化模型
+ 部署到生产环境

是最好使用专用的 R 开发环境执行的实际代码的开发和测试。 但是，在全面测试该脚本后，你可以轻松地将其部署到[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]使用[!INCLUDE[tsql](../../includes/tsql-md.md)]的熟悉的环境中的存储过程[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]。

此多部分教程的目的是迁移"完成 R 的代码"到 SQL Server 的典型工作流简介。 

- [第 1 课：浏览和可视化数据形状和分发通过存储过程中调用 R 函数](../tutorials/sqldev-explore-and-visualize-the-data.md)

- [第 2 课：在 T-SQL 函数中使用 R 创建数据功能](sqldev-create-data-features-using-t-sql.md)
  
- [第 3 课：训练和保存使用函数和存储的过程的 R 模型](sqldev-train-and-save-a-model-using-t-sql.md)
  
- [第 4 课：预测潜在的存储过程中使用 R 模型的结果](../tutorials/sqldev-operationalize-the-model.md)

该模型保存到数据库后，调用该模型用于预测[!INCLUDE[tsql](../../includes/tsql-md.md)]通过使用存储的过程。

## <a name="prerequisites"></a>先决条件

可以完成所有任务使用[!INCLUDE[tsql](../../includes/tsql-md.md)]中的存储过程[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]。

本教程假定你熟悉基本数据库操作，例如创建数据库和表、 导入数据，以及编写 SQL 查询。 它不会假定您知道。在这种情况下，提供所有 R 代码。 

+ [SQL Server 2016 R Services](../install/sql-r-services-windows-install.md#verify-installation)或[使用启用了 R 的 SQL Server 2017 机器学习服务](../install/sql-machine-learning-services-windows-install.md#verify-installation)

+ [R 库](../package-management/installed-package-information.md)

+ [权限](../security/user-permission.md)

+ [NYC 出租车演示数据库](demo-data-nyctaxi-in-sql.md)


## <a name="next-steps"></a>后续步骤

> [!div class="nextstepaction"]
> [浏览和可视化数据的存储过程中使用 R 函数](../tutorials/sqldev-explore-and-visualize-the-data.md)
