---
title: FREETEXTTABLE (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- FREETEXTTABLE_TSQL
- FREETEXTTABLE
dev_langs:
- TSQL
helpviewer_keywords:
- search conditions [SQL Server], meaning matches
- meaning matches [full-text search]
- FREETEXTTABLE function (Transact-SQL)
- ranked results [full-text search]
- column searches [full-text search]
ms.assetid: 4523ae15-4260-40a7-a53c-8df15e1fee79
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 42372b9ed94ad941c4a2436a28d0b9eaeb9f3b67
ms.sourcegitcommit: d9c5b9ab3c282775ed61712892eeb3e150ccc808
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/05/2019
ms.locfileid: "67597480"
---
# <a name="freetexttable-transact-sql"></a>FREETEXTTABLE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  是一个函数，用于[FROM 子句](../../t-sql/queries/from-transact-sql.md)的[!INCLUDE[tsql](../../includes/tsql-md.md)]的 SELECT 语句以执行[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]全文搜索的全文索引包含基于字符的数据类型的列。 此函数返回的零个、 一个或多个行包含以下与匹配含义，而不仅仅是确切的措辞中指定的文本的值的列的表*freetext_string*。 FREETEXTTABLE 被视为一个常规表名来引用。  
  
 FREETEXTTABLE 可用于相同类型的匹配项作为[FREETEXT &#40;TRANSACT-SQL&#41;](../../t-sql/queries/freetext-transact-sql.md)，  
  
 使用 FREETEXTTABLE 的查询返回每一行的相关性排名值 (RANK) 和全文键 (KEY)。  
  
> [!NOTE]  
>  有关 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 支持的全文搜索形式的信息，请参阅[使用全文搜索查询](../../relational-databases/search/query-with-full-text-search.md)。  
  
(https://azure.microsoft.com/documentation/articles/sql-database-preview-whats-new/?WT.mc_id=TSQL_GetItTag)).|  
  
 ![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "主题链接图标") [TRANSACT-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>语法  
  
```  
  
FREETEXTTABLE (table , { column_name | (column_list) | * }   
          , 'freetext_string'   
     [ , LANGUAGE language_term ]   
     [ , top_n_by_rank ] )  
```  
  
## <a name="arguments"></a>参数  
 *table*  
 表的名称，该表已标记为全文查询。 *表*或*视图*可以是由一个、 两个或三部分组成的数据库对象的名称。 查询视图时，仅能涉及一个全文索引的基表。  
  
 *表*不能指定服务器名称和不能对链接服务器的查询中使用。  
  
 column_name   
 FROM 子句中指定表的一个或多个全文索引列的名称。 列可以是 char、varchar、nchar、nvarchar、text、ntext、image、xml、varbinary 或 varbinary(max) 类型           。  
  
 *column_list*  
 指示可以指定多个列（以逗号分隔）。 column_list 必须用括号括起来  。 除非指定 language_term，否则 column_list 中所有列的语言必须相同   。  
  
 \*  
 指定所有注册全文搜索的列均应用于搜索给定的 freetext_string  。 除非*language_term*指定，则表中的所有全文索引列的语言必须相同。  
  
 *freetext_string*  
 要在 column_name 中搜索的文本  。 可以输入任何文本，包括单词、短语或句子。 只要在全文索引中找到任何术语或术语格式，就会生成匹配项。  
  
 与不同的 CONTAINS 搜索条件和中使用时是一个关键字， *freetext_string*单词和被视为干扰词或[非索引字](../../relational-databases/search/configure-and-manage-stopwords-and-stoplists-for-full-text-search.md)，因此会丢弃。  
  
 不允许使用 WEIGHT、FORMSOF、通配符、NEAR 和其他语法。 系统将通过同义词库对 freetext_string 进行断字处理、词干分析，然后执行同义词库查询  。  
  
 LANGUAGE language_term   
 特定的语言，查询时，其资源将用于断字、词干分析、同义词库查询以及非索引字删除。 此参数是可选的，可以将其指定为与语言区域设置标识符 (LCID) 对应的字符串、整数或十六进制值。 如果指定了 language_term，则它表示的语言将应用于搜索条件的所有元素  。 如果未指定值，则使用该列的全文语言。  
  
 如果将不同语言的文档一起作为二进制大型对象 (BLOB) 存储在单个列中，则指定文档的区域设置标识符 (LCID) 将决定对其内容编制索引时使用哪种语言。 在对这种列进行查询时，指定 LANGUAGElanguage_term 可增大找到有效匹配项的可能性  。  
  
 如果指定为字符串，language_term 将对应于 [sys.syslanguages (Transact-SQL)](../../relational-databases/system-compatibility-views/sys-syslanguages-transact-sql.md) 兼容性视图中的 alias 列值   。  字符串必须用单引号引起来，如 'language_term'  。 如果指定为整数，则 language_term 就是标识该语言的实际 LCID  。 如果指定为十六进制值，则 language_term 将以 0x 开头，后跟 LCID 的十六进制值  。 十六进制值不能超过八位（包括前导零在内）。  
  
 如果该值是双字节字符集 (DBCS) 格式，则 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 会将其转换为 Unicode 格式。  
  
 如果指定的语言无效，或者未安装对应于该语言的资源，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 将返回错误。 若要使用非特定语言资源，请将 0x0 指定为 language_term  。  
  
 *top_n_by_rank*  
 指定仅*n*最高排名的匹配项，按降序返回。 仅适用于整数值， *n*，指定。 如果 *top_n_by_rank* 与其他参数组合使用，则查询返回的行数可能会少于实际与所有谓词都匹配的行数。 *top_n_by_rank*允许您通过调取仅最相关的命中项来提高查询性能。  
  
## <a name="remarks"></a>备注  
 全文谓词和函数作用于 FROM 谓词所示的单个表。 若要对多个表进行搜索，请在 FROM 子句中使用联接表，以搜索由两个或更多个表的乘积构成的结果集。  
  
 FREETEXTTABLE 使用与 FREETEXT 谓词相同的搜索条件。  
  
 和 CONTAINSTABLE 一样，返回的表具有名为的列**键**并**排名**，获取相应的行并使用行排名值在查询中引用。  
  
## <a name="permissions"></a>权限  
 只有对指定表或表中所引用的列具有适当的 SELECT 权限的用户才能调用 FREETEXTTABLE。  
  
## <a name="examples"></a>示例  
  
### <a name="a-simple-example"></a>A. 简单示例  
 下面的示例创建并填充一个简单的表的两个列，其中列出了 3 个所在国家/地区和其标志中的颜色。 It 创建并填充全文目录和索引的表。 然后**FREETEXTTABLE**语法进行了演示。  
  
```  
CREATE TABLE Flags (Country nvarchar(30) NOT NULL, FlagColors varchar(200));  
CREATE UNIQUE CLUSTERED INDEX FlagKey ON Flags(Country);  
INSERT Flags VALUES ('France', 'Blue and White and Red');  
INSERT Flags VALUES ('Italy', 'Green and White and Red');  
INSERT Flags VALUES ('Tanzania', 'Green and Yellow and Black and Yellow and Blue');  
SELECT * FROM Flags;  
GO  
  
CREATE FULLTEXT CATALOG TestFTCat;  
CREATE FULLTEXT INDEX ON Flags(FlagColors) KEY INDEX FlagKey ON TestFTCat;  
GO   
  
SELECT * FROM Flags;  
SELECT * FROM FREETEXTTABLE (Flags, FlagColors, 'Blue');  
SELECT * FROM FREETEXTTABLE (Flags, FlagColors, 'Yellow');  
```  
  
### <a name="b-using-freetext-in-an-inner-join"></a>B. 在 INNER JOIN 中使用 FREETEXT  
 下面的示例返回的说明和任何匹配的含义的说明的产品的秩`high level of performance`。  
  
```  
USE AdventureWorks2012;  
GO  
  
SELECT FT_TBL.Description  
    ,KEY_TBL.RANK  
FROM Production.ProductDescription AS FT_TBL   
    INNER JOIN FREETEXTTABLE(Production.ProductDescription,  
    Description,   
    'high level of performance') AS KEY_TBL  
ON FT_TBL.ProductDescriptionID = KEY_TBL.[KEY]  
ORDER BY RANK DESC;  
GO  
```  
  
### <a name="c-specifying-language-and-highest-ranked-matches"></a>C. 指定语言和排名最高的匹配项  
 下面的示例相同，并演示如何使用`LANGUAGE` *language_term*并*top_n_by_rank*参数。  
  
```  
USE AdventureWorks2012;  
GO  
  
SELECT FT_TBL.Description  
    ,KEY_TBL.RANK  
FROM Production.ProductDescription AS FT_TBL   
    INNER JOIN FREETEXTTABLE(Production.ProductDescription,  
    Description,   
    'high level of performance',  
    LANGUAGE N'English', 2) AS KEY_TBL  
ON FT_TBL.ProductDescriptionID = KEY_TBL.[KEY]  
ORDER BY RANK DESC;  
GO  
```  
  
> [!NOTE]
>  语言*language_term*参数不需要使用*top_n_by_rank*参数。  
  
## <a name="see-also"></a>请参阅  
 [全文搜索入门](../../relational-databases/search/get-started-with-full-text-search.md)   
 [创建和管理全文目录](../../relational-databases/search/create-and-manage-full-text-catalogs.md)   
 [CREATE FULLTEXT CATALOG (Transact-SQL)](../../t-sql/statements/create-fulltext-catalog-transact-sql.md)   
 [CREATE FULLTEXT INDEX (Transact-SQL)](../../t-sql/statements/create-fulltext-index-transact-sql.md)   
 [创建和管理全文索引](../../relational-databases/search/create-and-manage-full-text-indexes.md)   
 [使用全文搜索查询](../../relational-databases/search/query-with-full-text-search.md)   
 [创建全文搜索查询 (Visual Database Tools)](https://msdn.microsoft.com/library/537fa556-390e-4c88-9b8e-679848d94abc)   
 [CONTAINS (Transact-SQL)](../../t-sql/queries/contains-transact-sql.md)   
 [CONTAINSTABLE (Transact-SQL)](../../relational-databases/system-functions/containstable-transact-sql.md)   
 [FREETEXT (Transact-SQL)](../../t-sql/queries/freetext-transact-sql.md)   
 [行集函数 (Transact-SQL)](../../t-sql/functions/rowset-functions-transact-sql.md)   
 [SELECT (Transact-SQL)](../../t-sql/queries/select-transact-sql.md)   
 [WHERE (Transact-SQL)](../../t-sql/queries/where-transact-sql.md)   
 [“预计算等级”服务器配置选项](../../database-engine/configure-windows/precompute-rank-server-configuration-option.md)  
  
  
