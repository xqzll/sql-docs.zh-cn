---
title: COLLATIONPROPERTY (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 10/24/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- COLLATIONPROPERTY_TSQL
- COLLATIONPROPERTY
dev_langs:
- TSQL
helpviewer_keywords:
- collations [SQL Server], properties
- COLLATIONPROPERTY function
ms.assetid: f5029e74-a1db-4f69-b0f5-5ee920c3311d
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 06d2a9417d001e18b9bb8a5f34ce90575510e649
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "65944011"
---
# <a name="collation-functions---collationproperty-transact-sql"></a>排序规则函数 - COLLATIONPROPERTY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

此函数返回指定排序规则请求的属性。
  
![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "主题链接图标") [TRANSACT-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>语法  
  
```sql
COLLATIONPROPERTY( collation_name , property )  
```  
  
## <a name="arguments"></a>参数  
*collation_name*  
排序规则的名称。 collation_name 自变量具有一个 nvarchar(128) 数据类型，无默认值   。
  
property   
排序规则的属性。 property 自变量具有一个 varchar(128) 数据类型，并且可具有下列值之一   ：
  
|属性名称|描述|  
|---|---|
|**CodePage**|排序规则的非 Unicode 代码页。 这是 varchar  数据使用的字符集。 请参阅 [Appendix G DBCS/Unicode Mapping Tables](https://msdn.microsoft.com/library/cc194886.aspx)（附录 G DBCS/Unicode 映射表）和 [Appendix H Code Pages](https://msdn.microsoft.com/library/cc195051.aspx)（附录 H 代码页）以转换这些值并查看它们的字符映射。<br /><br />基本数据类型：int |  
|**LCID**|排序规则的 Windows 区域设置 ID。 此区域性用于排序和比较规则。 请参阅 [LCID Structure](https://msdn.microsoft.com/library/cc233968.aspx)（LCID 结构）以转换这些值（首先需要转换为 varbinary）  。<br /><br />基本数据类型：int |  
|**ComparisonStyle**|排序规则的 Windows 比较样式。 对于二进制排序规则（(\_BIN) 和 (\_BIN2)），以及需区分所有属性时（ (\_CS\_AS\_KS\_WS)、(\_CS\_AS\_KS\_WS\_SC) 和 (\_CS\_AS\_KS\_WS\_VSS)），返回 0。 位掩码值：<br /><br /> 忽略大小写：1<br /><br /> 忽略重音：2<br /><br /> 忽略假名：65536<br /><br /> 忽略宽度：131072<br /><br /> 注意：尽管会影响比较行为，但此值中不会显示区分变体选择符 (\_VSS) 选项。<br /><br />基本数据类型：int |  
|**版本(Version)**|排序规则的版本。 返回的值介于 0 到 3 之间。<br /><br /> 名称中含有“140”的排序规则返回 3。<br /><br /> 名称中含有“100”的排序规则返回 2。<br /><br /> 名称中含有“90”的排序规则返回 1。<br /><br /> 所有其他排序规则均返回 0。<br /><br />基本数据类型：tinyint |  
  
## <a name="return-types"></a>返回类型
**sql_variant**
  
## <a name="examples"></a>示例  
  
```sql
SELECT COLLATIONPROPERTY('Traditional_Spanish_CS_AS_KS_WS', 'CodePage');  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
1252   
```  
  
[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] 和 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
```sql
SELECT COLLATIONPROPERTY('Traditional_Spanish_CS_AS_KS_WS', 'CodePage')  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]
  
```sql
1252   
```  
  
## <a name="see-also"></a>另请参阅
[sys.fn_helpcollations (Transact-SQL)](../../relational-databases/system-functions/sys-fn-helpcollations-transact-sql.md)
  
  

