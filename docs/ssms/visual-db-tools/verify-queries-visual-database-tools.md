---
title: 验证查询 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdtsql.chm:100644
helpviewer_keywords:
- verifying queries
- queries [SQL Server], verifying
- checking queries
ms.assetid: 1382c0c0-46dc-45f9-ab38-9bba1d347eea
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: ceb12a0510cd11c515c5398b4cc4051940720dd2
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "65105556"
---
# <a name="verify-queries-visual-database-tools"></a>验证查询 (Visual Database Tools)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
为了避免问题，可以对所生成的查询进行检查以确保其语法正确。 在 [SQL 窗格](../../ssms/visual-db-tools/sql-pane-visual-database-tools.md)中输入语句时，此选项尤其有用。  
  
在验证查询时应谨记以下几点：  
  
-   即使无法在“关系图”  窗格和“条件”  窗格中表示某个语句，该语句也可能是有效的，因此可以通过验证。  
  
-   SQL 验证可检测某些 SQL 错误，但不能检测所有 SQL 错误。 如果查询包含在 SQL 验证过程中未检测到的错误，则在运行该查询时，数据库将检测到该错误。  
  
-   无法对包含参数的查询进行验证。  
  
### <a name="to-verify-an-sql-statement"></a>验证 SQL 语句  
  
-   右键单击“SQL 窗格”  ，然后从快捷菜单中选择“验证 SQL 语法”  。  
  
## <a name="see-also"></a>另请参阅  
[运行查询 (Visual Database Tools)](../../ssms/visual-db-tools/run-queries-visual-database-tools.md)  
[执行基本的查询操作 (Visual Database Tools)](../../ssms/visual-db-tools/perform-basic-operations-with-queries-visual-database-tools.md)  
  
