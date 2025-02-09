---
title: “XML 索引”对话框 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdt.dlgbox.xmlindexes
ms.assetid: eef38310-4498-4ccc-bb77-5bbd1c7cc477
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 2a0ffb3a5b0eee643438e68fa8e3bf3477a04273
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "65104507"
---
# <a name="xml-indexes-dialog-box-visual-database-tools"></a>“XML 索引”对话框 (Visual Database Tools)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
使用“XML 索引”  对话框可为 XML 数据类型的列创建索引，这些列不能使用“索引/键”  对话框创建索引。 每个 XML 列都可以有多个 XML 索引，但最先创建的索引（主索引）将成为其他索引（二级索引）的基础。 删除主 XML 索引后，二级索引也会随之删除。  
  
## <a name="options"></a>选项  
**选定的 XML 索引**  
列出现有的 XML 索引。 选择一个索引即可在右侧网格中显示其属性。 如果该列表为空，则表示尚未为该表定义任何 XML 索引。  
  
**“添加”**  
创建新的 XML 索引。  
  
**删除**  
删除在“选定的 XML 索引”  列表中选定的 XML 索引。 如果删除主 XML 索引，系统将通知您这会同时删除所有二级索引，此时您可以继续操作或取消操作。  
  
**常规类别**  
展开此项可显示“列”  、“是主要的”  和“类型”  的属性字段。  
  
**“列”**  
显示此索引按升序排序。  
  
**是主要的**  
指示此索引是否为主索引。 基于该列创建的第一个 XML 索引将成为其他索引的基础。  
  
**主引用名**  
在此索引为二级索引时显示主索引的名称。 只有在此索引为二级索引时才可用。  
  
**次要类型**  
显示二级索引的类型。 只有在此索引为二级索引时才可用。  
  
**类型**  
显示此索引为 XML 索引。  
  
**标识类别**  
展开此项可显示“名称”  和“说明”  属性字段。  
  
**名称**  
显示 XML 索引的名称。 在创建一个新索引时，将基于表设计器的活动窗口中的表为其指定默认名称。 您可以随时更改该名称。  
  
**Description**  
描述该索引。 若要编写更详细的说明，请单击“说明”，再单击属性字段右侧显示的省略号按钮 (…)   。 这可以提供一个更大的文本编写区域。  
  
**表设计器类别**  
展开此项可显示有关此 XML 索引的属性的信息。  
  
**填充规范**  
展开此项可显示有关“填充因子”  和“填充索引”  的信息。  
  
**填充因子**  
指定系统在索引页中能够填充的空间百分比。 页面已满后，系统必须拆分页面才能添加新数据，从而影响性能。  
  
-   值为 100 表示将填满页面，这时需要的存储空间量最小但效率最低。 只有在不会对数据进行更改时（例如，对于只读表），才可以使用此设置。  
  
-   值越小，数据页上留出的可用空间就越大，这会减少随索引的增长而拆分数据页的需求。 但是，这需要更大的存储空间。 在需要对表中的数据进行更改的情况下，此设置更为适用。  
  
**填充索引**  
为此索引中的页提供与“填充因子”  中所指定百分比相同的可用空间（填充）百分比。  
  
**已禁用**  
指定是否禁用此索引。 禁用的索引不支持搜索，也不会在表中添加新项时随之更新。 您可以通过禁用索引来提高大容量插入和更新操作的性能。  
  
**允许页锁定**  
指定对此索引是否允许页级锁定。 允许或禁用页级锁定会影响数据库性能。  
  
**重新计算统计数据**  
在创建索引时计算新的统计数据。 重新计算统计数据会降低索引的生成速度，但通常会提高查询性能。  
  
**允许行锁定**  
指定对此索引是否允许行级锁定。 允许或禁用行级锁定会影响数据库性能。  
  
## <a name="see-also"></a>另请参阅  
[创建 XML 索引](../../relational-databases/xml/create-xml-indexes.md)  
  
