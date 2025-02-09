---
title: 项目设置 （类型映射） (AccessToSQL) |Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Access data types
- data types, default mappings
- default data type mappings
- Project Settings dialog box, Type Mapping
- SQL Server data types
- Type Mapping settings
ms.assetid: b87b9683-abed-4677-8c50-18bdba704655
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 8a695217909641c737b7780fc4f8b80b2cb08152
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "63299131"
---
# <a name="project-settings-type-mapping-accesstosql"></a>项目设置 （类型映射） (AccessToSQL)
类型映射项目设置，可以设置 SSMA 项目的默认类型映射。 此外可以指定单个数据库对象的类型映射。 有关详细信息，请参阅[映射源和目标数据类型](mapping-source-and-target-data-types-accesstosql.md)。  
  
类型映射现已推出**项目设置**并**默认项目设置**对话框：  
  
-   使用**项目设置**对话框来设置当前项目的配置选项。 若要访问的类型映射设置，在**工具**菜单中，选择**项目设置**，然后单击**类型映射**的左窗格中。  
  
-   使用**默认项目设置**对话框来设置所有项目的配置选项。 若要访问的类型映射设置，在**工具**菜单中，选择**默认项目设置**，选择迁移项目类型设置为其所需查看 / 更改从**迁移目标版本**下拉列表中，然后单击**类型映射**的左窗格中。  
  
## <a name="options"></a>选项  
**源类型**  
要映射的访问的数据类型。  
  
**目标类型**  
目标[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]或 SQL Azure 指定访问数据类型的数据类型。  
  
下表显示源和目标数据类型之间的默认映射。  
  
|访问数据类型|SQL Server 数据类型|  
|--------------------|------------------------|  
|**binary[\*..\*]**|**varbinary[\*]**|  
|**boolean**|**bit**|  
|**byte**|**tinyint**|  
|**currency**|**money**|  
|**date**|**datetime**|  
|**decimal**|**float**|  
|**double**|**float**|  
|**guid**|**uniqueidentifier**|  
|**integer**|**smallint**|  
|**long**|**int**|  
|**longbinary**|**varbinary(max)**|  
|**memo**|**nvarchar(max)**|  
|**备注**-适用于 Access 97|**varchar(max)**|  
|**single**|**real**|  
|**text[\*..\*]**|**nvarchar[\*]**|  
|**text[\*..\*]** - for Access 97|**varchar[\*]**|  
  
**“添加”**  
单击此项可将数据类型添加到映射列表。  
  
**编辑**  
单击此项可编辑的映射列表中的数据类型。  
  
**删除**  
单击以从映射列表中删除所选的数据类型映射。  
  
重置为默认值  
单击重置为 SSMA 默认值的所有数据类型映射。  
  
## <a name="see-also"></a>请参阅  
[映射源和目标数据类型](mapping-source-and-target-data-types-accesstosql.md)  
[用户界面 Reference(Access)](https://msdn.microsoft.com/af24c303-4a41-449b-9c86-d6558a97e839)  
  
