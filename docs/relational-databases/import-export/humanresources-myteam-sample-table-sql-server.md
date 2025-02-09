---
title: HumanResources.myTeam 示例表 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: data-movement
ms.topic: conceptual
helpviewer_keywords:
- myTeam sample table [SQL Server]
- bulk importing [SQL Server], examples
- bulk exporting [SQL Server], examples
ms.assetid: 27da45a0-c1f4-4bf4-ab24-6196e80d3834
author: MashaMSFT
ms.author: mathoma
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 19ac990e7288885c2fd29c8114837be24dae9a88
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "64946184"
---
# <a name="humanresourcesmyteam-sample-table-sql-server"></a>HumanResources.myTeam 示例表 (SQL Server)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
  [导入和导出大容量数据](../../relational-databases/import-export/bulk-import-and-export-of-data-sql-server.md) 中的许多代码示例都需要一个名为 **myTeam**的具有特殊用途的测试表。 您必须在 **数据库的** HumanResources **架构中创建** myTeam [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 表，才能运行这些示例。  
  
> [!NOTE]  
>  [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 是 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]中的一个示例数据库。  
  
 myTeam 表包含以下列  。  
  
|“列”|数据类型|可空性|描述|  
|------------|---------------|-----------------|-----------------|  
|**EmployeeID**|**smallint**|非空|行的主键。 我的工作组中成员的雇员 ID。|  
|**名称**|**nvarchar(50)**|非空|我的工作组中成员的名称。|  
|**标题**|**nvarchar(50)**|可以为 Null|我的工作组中雇员的职位。|  
|**背景**|**nvarchar(50)**|非空|上次更新行的日期和时间。 （默认值）|  
  
**创建 HumanResources.myTeam**  
  
-   使用以下 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句：  
  
    ```sql
    --Create HumanResources.MyTeam:   
    USE AdventureWorks;  
    GO  
    CREATE TABLE HumanResources.myTeam   
    (EmployeeID smallint NOT NULL,  
    Name nvarchar(50) NOT NULL,  
    Title nvarchar(50) NULL,  
    Background nvarchar(50) NOT NULL DEFAULT ''  
    );  
    GO  
    ```  
  
**填充 HumanResources.myTeam**  
  
-   执行下列 `INSERT` 语句以在表中填充两行：  
  
    ```sql
    USE AdventureWorks;  
    GO  
    INSERT INTO HumanResources.myTeam(EmployeeID,Name,Title,Background)  
       VALUES(77,'Mia Doppleganger','Administrative Assistant','Microsoft Office');  
    GO  
    INSERT INTO HumanResources.myTeam(EmployeeID,Name,Title,Background)  
       VALUES(49,'Hirum Mollicat','I.T. Specialist','Report Writing and Data Mining');  
    GO  
    ```  
  
    > [!NOTE]  
    >  这些语句跳过第四列，即 `Background`列。 这样会有默认值。 跳过该列使 `INSERT` 语句将该列保留为空。  
  
## <a name="see-also"></a>另请参阅  
 [批量导入和导出数据 (SQL Server)](../../relational-databases/import-export/bulk-import-and-export-of-data-sql-server.md)  
  
  
