---
title: 什么是 SQL Server 2017 Analysis Services 中的新增功能 |Microsoft Docs
ms.date: 03/08/2019
ms.prod: sql
ms.technology: analysis-services
ms.custom: ''
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
monikerRange: '>= sql-server-2017 || = sqlallproducts-allversions'
ms.openlocfilehash: 1f322b395f897780f3693d1186767aeef7dbfd4a
ms.sourcegitcommit: a6949111461eda0cc9a71689f86b517de3c5d4c1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/19/2019
ms.locfileid: "67263265"
---
# <a name="whats-new-in-sql-server-2017-analysis-services"></a>SQL Server 2017 Analysis Services 中的新增功能
[!INCLUDE[ssas-appliesto-sql2017](../includes/ssas-appliesto-sql2017.md)]

SQL Server 2017 Analysis Services 将，因为 SQL Server 2012 一些最重要的增强功能。 在表格模式 （SQL Server 2012 Analysis Services 中首次引入） 的成功构建此版本中会使表格模型比以往更强大。

多维模式和 Power Pivot for SharePoint 模式是许多 Analysis Services 部署一个书钉。 在 Analysis Services 产品生命周期，这些模式是成熟。 没有为此版本中这些模式的新功能。 但是，bug 修复和性能改进是包含。

SQL Server 2017 Analysis Services 中包含了此处所述的功能。 为了充分利用它们，还必须使用的最新版本，但是[SQL Server Data Tools](../ssdt/download-sql-server-data-tools-ssdt.md) (SSDT) 和[SQL Server Management Studio](../ssms/download-sql-server-management-studio-ssms.md) (SSMS)。 SSDT 和 SSMS 使用新的和改进功能通常与 SQL Server 中的新功能同时发生每月更新。  

时务必要了解所有新功能，还有一点需要知道什么被弃用，但在此版本和将来的版本中停止使用。 请务必查看[向后兼容性 (SQL Server 2017 Analysis Services)](analysis-services-backward-compatibility-sql2017.md)。

在此版本中，让我们看一些关键新功能。

## <a name="1400-compatibility-level-for-tabular-models"></a>针对表格模型的 1400 兼容级别
  若要在此处要利用的许多新功能和所述的功能，必须设置新的或现有的表格模型或将其升级到 1400年兼容性级别。 不能将 1400 兼容级别的模型部署到 SQL Server 2016 SP1 或更早版本，也不能降级为较低的兼容级别。 若要了解详细信息，请参阅[Analysis Services 表格模型的兼容性级别](../analysis-services/tabular-models/compatibility-level-for-tabular-models-in-analysis-services.md)。
  
在 SSDT 中，新建表格模型项目时可以选择新的 1400 兼容级别。 

![AS_NewTabular1400Project](../analysis-services/media/as-newtabular1400project.png)


若要升级现有表格模型在 SSDT 中，在解决方案资源管理器，右键单击**Model.bim**，然后在**属性**，将**兼容性级别**属性设置为**SQL Server 2017 (1400)** 。 

![AS_Model_Properties](../analysis-services/media/as-model-properties.png)

务必要注意，一旦将现有的模型升级到 1400年时，不能降级。 请确保将 1200年模型数据库的备份保留。

## <a name="modern-get-data-experience"></a>新式获取数据体验
当涉及到从数据源的数据导入到表格模型时，SQL Server Data Tools (SSDT) 引入了新式**获取数据**体验 1400年兼容性级别的模型。 这一新功能基于 Power BI Desktop 和 Microsoft Excel 2016 中类似的功能。 新式获取数据体验使用获取数据查询生成器和 M 表达式提供巨大的数据转换和数据混合功能。

新式获取数据体验提供对各种数据源的支持。 今后，更新将包括对更多的支持。

![AS_Get_Data_in_SSDT](../analysis-services/media/as-get-data-in-ssdt.png)

 功能强大且直观的用户界面可选择你的数据和数据转换/混合功能比以往更容易。

![高级混合应用程序](../analysis-services/media/as-get-data-advanced.png)


新式获取数据体验和 M 混合功能不适用于现有表格模型 upraded 从到 1400年兼容性级别为 1200年。 新体验仅适用于在 1400年兼容级别创建的新模型。

## <a name="encoding-hints"></a>编码提示
此版本引入了编码提示，这是一种用于优化大型内存中表格模型处理（数据刷新）的高级功能。 若要更好地了解编码，请参阅[性能优化的表格模型 SQL Server 2012 Analysis Services 中](https://msdn.microsoft.com/library/dn393915.aspx)白皮书，以更好地了解编码。

* 值编码为通常仅用于聚合的列提供更好的查询性能。

* 哈希编码首选用于“分组依据”列（通常为维度表值）和外键。 字符串列始终采用哈希编码。

数值列可使用上述任一编码方法。 Analysis Services 开始处理表格时，如果表为空（有或没有分区）或正在执行全表处理操作，则会对每个数值列采用示例值，确定是要应用值编码还是哈希编码。 默认情况下，选择值编码时列中非重复值的示例有足够空间-否则哈希编码通常会提供更好的压缩。 使 Analysis Services 基于有关数据分布的进一步信息部分处理列后更改编码方法，并重新启动编码的过程;但是，这会增加处理时间，并且会导致效率低下。 性能优化白皮书更详细地讨论了重新编码，并介绍了如何使用 SQL Server Profiler 检测它。

编码提示，建模器来指定给定事先了解从数据事件探查和/或响应重新编码跟踪事件中的编码方法的首选项。 由于哈希编码列的聚合速度低于值编码列的聚合速度，因此可将值编码指定为针对此类列的提示。 不保证应用首选项。 这是一个提示而不是一种设置。 若要指定编码提示，请在列上设置 EncodingHint 属性。 可能的值为"Default"、"值"和"哈希"。 Model.bim 文件中基于 JSON 的以下元数据片段为 Sales Amount 列指定值编码。

```
{
    "name": "Sales Amount",
    "dataType": "decimal",
    "sourceColumn": "SalesAmount",
    "formatString": "\\$#,0.00;(\\$#,0.00);\\$#,0.00",
    "sourceProviderType": "Currency",
    "encodingHint": "Value"
}
```

## <a name="ragged-hierarchies"></a>不规则层次结构
在表格模型中，可以构建父子层次结构模型。 具有不同级别数的层次结构通常称为不规则层次结构。 默认情况下，显示不规则层次结构时，用空白表示低于最低子级的级别。 以下为组织结构图中的不规则层次结构示例：

![AS_Ragged_Hierarchy](../analysis-services/media/as-ragged-hierarchy.png)

此版本引入了“隐藏成员”  属性。 可以将层次结构的“隐藏成员”  属性设置为“隐藏空成员”  。

![AS_Hide_Blank_Members](../analysis-services/media/as-hide-blank-members.png)

 >[!NOTE]
 > 模型中的空成员表示为 DAX 空值，而非空字符串。

设置为“隐藏空成员”  并部署模型后，会在报告客户端（如 Excel）中显示易于阅读的层次结构版本。

![AS_Non_Ragged_Hierarchy](../analysis-services/media/as-non-ragged-hierarchy.png)


## <a name="detail-rows"></a>详细信息行
现在可以定义提供度量值的自定义行集。 详细信息行类似于多维模型中的默认钻取操作。 同聚合级别相比，这允许最终用户查看更为详细的信息。 

以下数据透视表显示 Adventure Works 示例表格模型中的年度 Internet 总销售。 可以从度量值中右键单击含有聚合值的单元格，然后单击“显示详细信息”  ，查看详细信息行。

![AS_Show_Details](../analysis-services/media/as-show-details.png)

默认情况下，显示 Internet 销售表中的关联数据。 对用户而言，此限制行为通常没有意义，因为表可能没有必要的列来显示有用信息（如客户名称和订单信息）。 使用详细信息行，可以指定度量值的“详细信息行表达式”  属性。

#### <a name="detail-rows-expression-property-for-measures"></a>度量值的“详细信息行表达式”属性
度量值的“详细信息行表达式”  属性让模型作者能够自定义返回到最终用户的列和行。

![AS_Detail_Rows_Expression_Property](../analysis-services/media/as-detail-rows-expression-property.png)

[SELECTCOLUMNS](/dax/selectcolumns-function-dax) DAX 函数通常用在详细信息行表达式。 以下示例定义为示例 Adventure Works 表格模型中 Internet 销售表的行返回的列：

```
SELECTCOLUMNS(
    'Internet Sales',
    "Customer First Name", RELATED( Customer[Last Name]),
    "Customer Last Name", RELATED( Customer[First Name]),
    "Order Date", 'Internet Sales'[Order Date],
    "Internet Total Sales", [Internet Total Sales]
)
```

定义属性并部署模型后，用户选择“显示详细信息”  时，会返回自定义行集。 它将自动采用所选单元格的筛选上下文。 在此示例中，仅显示 2010 年值的行：

![AS_Detail_Rows](../analysis-services/media/as-detail-rows.png)

#### <a name="default-detail-rows-expression-property-for-tables"></a>表的“默认详细信息行表达式”属性
除了度量值，表还具有一个用于定义详细信息行表达式的属性。 “默认详细信息行表达式”  属性是表中所有度量值的默认值。 不具有其自己定义的表达式的度量值表继承该表达式，并显示为表定义的行集。 这允许重复使用的表达式，和更高版本会自动添加到表中的新度量值将继承该表达式。

![AS_Default_Detail_Rows_Expression](../analysis-services/media/as-default-detail-rows-expression.png)
 
#### <a name="detailrows-dax-function"></a>DETAILROWS DAX 函数
此版本包括新的 `DETAILROWS` DAX 函数，该函数返回详细信息行表达式定义的行集。 其工作原理类似于 MDX 中的 `DRILLTHROUGH` 语句，此语句也兼容表格模型中定义的详细信息行表达式。

以下 DAX 查询为度量值或表返回详细信息行表达式定义的行集。 如果未定义任何表达式，会返回 Internet 销售表的数据，因为 Internet 销售表是包含度量值的表。

```
EVALUATE DETAILROWS([Internet Total Sales])
```

## <a name="object-level-security"></a>对象级安全性
此版本引入了[对象级安全性](../analysis-services/tabular-models/object-level-security.md)表和列。 除了限制对表和列的数据访问，可以保护敏感的表和列名称。 这有助于防止恶意用户发现此类表的存在。

必须使用基于 JSON 的元数据、 表格模型脚本语言 (TMSL) 或表格对象模型 (TOM) 设置对象级安全性。 

例如，通过将“TablePermission”  类的“MetadataPermission”  属性设置为“无”  ，以下代码可帮助保护示例 Adventure Works 表格模型中的产品表。

```
//Find the Users role in Adventure Works and secure the Product table
ModelRole role = db.Model.Roles.Find("Users");
Table productTable = db.Model.Tables.Find("Product");
if (role != null && productTable != null)
{
    TablePermission tablePermission;
    if (role.TablePermissions.Contains(productTable.Name))
    {
        tablePermission = role.TablePermissions[productTable.Name];
    }
    else
    {
        tablePermission = new TablePermission();
        role.TablePermissions.Add(tablePermission);
        tablePermission.Table = productTable;
    }
    tablePermission.MetadataPermission = MetadataPermission.None;
}
db.Update(UpdateOptions.ExpandFull);
```

## <a name="dynamic-management-views-dmvs"></a>动态管理视图 (DMV)
[Dmv](../analysis-services/instances/use-dynamic-management-views-dmvs-to-monitor-analysis-services.md)是 SQL Server Profiler 中的查询，返回有关本地服务器操作和服务器运行状况的信息。
此版本包括对改进[动态管理视图](https://docs.microsoft.com/sql/analysis-services/instances/use-dynamic-management-views-dmvs-to-monitor-analysis-services)(DMV) 位于 1200年和 1400年兼容级别的表格模型。

[DISCOVER_CALC_DEPENDENCY](https://docs.microsoft.com/bi-reference/schema-rowsets/xml/discover-calc-dependency-rowset)现在可用于表格 1200年和 1400年模型。 表格 1400年模型显示 M 分区、 M 表达式和结构化的数据源之间的依赖项。 若要了解详细信息，请参阅[Analysis Services 博客](https://blogs.msdn.microsoft.com/analysisservices/2017/07/17/whats-new-in-sql-server-2017-rc1-for-analysis-services/)。

[MDSCHEMA_MEASUREGROUP_DIMENSIONS](https://docs.microsoft.com/bi-reference/schema-rowsets/ole-db-olap/mdschema-measuregroup-dimensions-rowset) ，为此 DMV，各种客户端工具用于显示度量值维度提供了改进。 例如，Excel 数据透视表中的资源管理器功能允许用户跨向下钻到与所选度量值相关的维度。 此版本中更正基数列之前显示不正确的值。

## <a name="dax-enhancements"></a>DAX 增强功能
此版本包括对新的 DAX 函数和功能的支持。 为了利用，你需要使用最新版本的 SSDT。 若要了解详细信息，请参阅[的新 DAX 函数](/dax/new-dax-functions)。

一个新的 DAX 功能的最重要部分是新[IN 运算符 / 函数 CONTAINSROW](/dax/in-operator-containsrow-function) DAX 表达式。 这与经常用于在 [`TSQL IN`](https://msdn.microsoft.com/library/ms177682.aspx) 子句中指定多个值的 `WHERE` 运算符类似。

以前，通常使用逻辑 `OR` 运算符指定多值筛选，如以下度量值表达式所示：

```
Filtered Sales:=CALCULATE (
        [Internet Total Sales],
                 'Product'[Color] = "Red"
            || 'Product'[Color] = "Blue"
            || 'Product'[Color] = "Black"
    )
```

使用 `IN` 运算符可简化此操作：
```
Filtered Sales:=CALCULATE (
        [Internet Total Sales], 'Product'[Color] IN { "Red", "Blue", "Black" }
    )
```

在这种情况下， `IN` 运算符引用含有 3 行的单列表，每行对应于一种指定的颜色。 请注意，表构造函数语法使用大括号。

`IN` 运算符的功能与 `CONTAINSROW` 函数相同：
```
Filtered Sales:=CALCULATE (
        [Internet Total Sales], CONTAINSROW({ "Red", "Blue", "Black" }, 'Product'[Color])
    )
```

`IN` 运算符还可和表构造函数有效结合使用。 例如，按产品颜色和类别组合，进行以下度量值筛选：
```
Filtered Sales:=CALCULATE (
        [Internet Total Sales],
        FILTER( ALL('Product'),
              ( 'Product'[Color] = "Red"   && Product[Product Category Name] = "Accessories" )
         || ( 'Product'[Color] = "Blue"  && Product[Product Category Name] = "Bikes" )
         || ( 'Product'[Color] = "Black" && Product[Product Category Name] = "Clothing" )
        )
    )
```

通过新的 `IN` 运算符，以上度量值表达式等效于以下表达式：
```
Filtered Sales:=CALCULATE (
        [Internet Total Sales],
        FILTER( ALL('Product'),
            ('Product'[Color], Product[Product Category Name]) IN
            { ( "Red", "Accessories" ), ( "Blue", "Bikes" ), ( "Black", "Clothing" ) }
        )
    )
```

## <a name="additional-improvements"></a>其他改进
除了所有新功能，Analysis Services、 SSDT 和 SSMS 还包括以下改进：

* 层次结构和列重用显示在 Power BI 字段列表中更有帮助的位置中。
* 日期关系，基于日期字段轻松创建日期维度的关系。
* Analysis Services 的默认安装选项现用于表格模式。
* 新获取的数据 (Power Query) 数据源。
* 用于 SSDT 的 DAX 编辑器。
* 现有 DirectQuery 数据源支持 M 查询。
* SSMS 改进，例如对结构化数据源的查看、编辑和脚本编写支持。



## <a name="see-also"></a>另请参阅
[SQL Server 2017 发行说明](../sql-server/sql-server-2017-release-notes.md)   
[SQL Server 2017 的新增功能](../sql-server/what-s-new-in-sql-server-2017.md)
