---
title: “索引 - 键”对话框 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdtsql.chm:65539
- vdt.ppg.indexeskeys
ms.assetid: 9e4060ba-80c3-468f-bccb-e12e99f672c2
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: fb350568200226585f4c3138224e65816e617780
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "65096663"
---
# <a name="indexes---keys-dialog-box-visual-database-tools"></a>“索引 - 键”对话框 (Visual Database Tools)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
使用此对话框可以创建或修改索引、主键和唯一键。 若要访问此对话框，请打开具有索引或键的表定义，右键单击表定义网格，再单击“索引/键”  。  
  
> [!NOTE]  
> 如果表是为复制发布的，则必须使用 Transact-SQL 语句 [ALTER TABLE](../../t-sql/statements/alter-table-transact-sql.md) 或 SQL Server 管理对象 (SMO) 对架构进行更改。 使用表设计器或数据库关系图设计器更改架构后，会尝试删除并重新创建表。 由于您不能删除已发布的对象，因此架构更改将失败。  
  
## <a name="options"></a>选项  
**选定的主/唯一键或索引**  
列出现有的主键/唯一键和索引。 选择其中任意一项可在右侧网格中显示其属性。 如果该列表为空，则表示尚未为该表定义任何 XML 索引。  
  
**“添加”**  
创建新的主键/唯一键或索引。  
  
**删除**  
删除在“选定的主/唯一键或索引”  列表中所选的键或索引。  
  
**常规类别**  
展开此项可显示属性“列”  、“是唯一的”  和“类型”  。  
  
**“列”**  
列出键或索引中的列的所选排序顺序，并且通过此项可访问可在其中定义排序顺序的对话框。 若要显示该对话框，请单击“列”，再单击属性字段右侧显示的省略号 (…)  。  
  
**是唯一的**  
指示输入到此索引或键中的数据是否必须是唯一的。 这不适用于 XML 索引。  
  
**类型**  
指定在“选定的主/唯一键或索引”  列表中所选的项是否为唯一键、主键或索引。 此字段对于主键是只读的。  
  
**标识类别**  
展开此项可显示“名称”  和“说明”  属性字段。  
  
**名称**  
显示键或索引的名称。 在创建一个新索引时，将基于表设计器的活动窗口中的表为其指定默认名称。 您可以随时更改该名称。  
  
**Description**  
提供一个描述键或索引的位置。 若要编写更详细的说明，请单击“说明”，再单击属性字段右侧显示的省略号按钮 (…)   。 这可以提供一个更大的文本编写区域。  
  
**表设计器类别**  
展开此项可显示有关“创建为聚集的”  的信息。  
  
**创建为聚集的**  
指定创建聚集键或聚集索引。 对于每个表只能创建一个聚集索引。 表中数据按聚集索引的顺序进行存储。 有关详细信息，请参阅 [创建聚集索引](../../relational-databases/indexes/create-clustered-indexes.md) 和 [创建非聚集索引](../../relational-databases/indexes/create-nonclustered-indexes.md)。  
  
**数据空间规范**  
展开此项可显示有关“(数据空间类型)”  、“文件组或分区方案名称”  和“分区列列表”  的信息。  
  
**(数据空间类型)**  
指示此索引或键是属于文件组还是分区方案。  
  
**文件组或分区方案名称**  
显示用于存储索引或键的文件组或分区方案的名称。  
  
**分区列列表**  
显示一个逗号分隔的列表，其中列出了参与分区列功能的各个列。 如果在“(数据空间类型)”  字段中选择了“文件组”，则此项不可用。  
  
**填充规范**  
展开此项可显示有关“填充因子”  和“填充索引”  的信息。  
  
**填充因子**  
指定系统在索引叶级页中能够填充的空间百分比。 一旦页面已满，系统就必须拆分页面以添加新数据，因而会影响性能。  
  
-   值为 100 表示页面将填满。 此时需要的存储空间量最小。 只有在不会对数据进行更改时（例如，对于只读表），才可以使用此设置。  
  
-   值越小，数据页上的可用空间就越大。 这样可以减少在索引增长过程中对数据页进行拆分的需要，但需要更大的存储空间。  
  
**填充索引**  
指示此索引中的中间页在增长过程中是否使用与在“填充因子”  中指定的百分比相同的可用空间（填充）百分比设置。  
  
**忽略重复的键**  
指定在大容量插入操作过程中插入具有与现有键值相同的键值的行时的行为。 如果选择：  
  
-   **是** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 将发出警告，忽略有问题的传入行，并尝试插入剩余行。  
  
-   **否** [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 将发出错误信息并回滚整个大容量插入操作。  
  
**包含列**  
显示一个用逗号分隔的列表，其中列出用于组成索引键的所有列的名称。 只能为非聚集索引指定子键列。 此属性对 XML 索引是隐藏的。  
  
**已禁用**  
指示是否禁用此索引。 此属性是只读属性。 只有在 Visual Database tools 之外禁用了索引，此属性才可设置为“是”  。  
  
**为全文本键**  
指定此索引是否为全文本键。 有关全文本键的详细信息，请参阅 SQL Server 联机丛书。 此属性对 XML 索引是隐藏的。  
  
**允许页锁定**  
指定对此索引是否允许页级锁定。 允许或禁用页级锁定会影响数据库性能。 建议设置为“是”  。  
  
**重新计算统计数据**  
指定在创建索引后，基础 [!INCLUDE[ssDE](../../includes/ssde_md.md)] 是否计算新的统计数据。 重新计算统计数据会降低索引的生成速度，但很有可能提高查询性能。  
  
**允许行锁定**  
指定对此索引是否允许行级锁定。 允许或禁用行级锁定会影响数据库性能。 建议设置为“是”  。  
  
## <a name="see-also"></a>另请参阅  
[使用约束 (Visual Database Tools)](https://msdn.microsoft.com/637098af-2567-48f8-90f4-b41df059833e)  
[使用键 (Visual Database Tools)](https://msdn.microsoft.com/31fbcc9f-2dc5-4bf9-aa50-ed70ec7b5bcd)  
  
