---
title: sys.dm_fts_parser (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.dm_fts_parser_TSQL
- dm_fts_parser
- dm_fts_parser_TSQL
- sys.dm_fts_parser
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_fts_parser dynamic management function
- troubleshooting [SQL Server], full-text search
ms.assetid: 2736d376-fb9d-4b28-93ef-472b7a27623a
author: pmasl
ms.author: pelopes
ms.reviewer: mikeray
manager: craigg
ms.openlocfilehash: 16df7ce483209be058d44448e9071406f897b41a
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "66822363"
---
# <a name="sysdmftsparser-transact-sql"></a>sys.dm_fts_parser (Transact-SQL)

[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  在应用后返回的最终词汇切分结果给定[断字符](../../relational-databases/search/configure-and-manage-word-breakers-and-stemmers-for-search.md)，[同义词库](../../relational-databases/search/configure-and-manage-thesaurus-files-for-full-text-search.md)，并[非索引字表](../../relational-databases/search/configure-and-manage-stopwords-and-stoplists-for-full-text-search.md)组合到查询字符串输入。 此词语切分结果等效于全文引擎针对指定查询字符串的输出。  
  
 sys.dm_fts_parser 是动态管理函数。  
  
## <a name="syntax"></a>语法  
  
```  
sys.dm_fts_parser('query_string', lcid, stoplist_id, accent_sensitivity)  
```  
  
## <a name="arguments"></a>参数  
 *query_string*  
 要分析的查询。 *query_string*可以是字符串链[CONTAINS](../../t-sql/queries/contains-transact-sql.md)语法支持。 例如，您可以包括变形、同义词库和逻辑运算符。  
  
 *lcid*  
 要用于分析的断字符的区域设置标识符 (LCID) *query_string*。  
  
 *stoplist_id*  
 非索引字表，如果有，用于通过标识的断字符的 ID *lcid*。 *stoplist_id*是**int**。如果指定 NULL，则不使用任何非索引字表。 如果指定 0，则使用系统 STOPLIST。  
  
 非索引字表 ID 在数据库中是唯一的。 若要获取给定的表使用的全文索引非索引字表 ID [sys.fulltext_indexes](../../relational-databases/system-catalog-views/sys-fulltext-indexes-transact-sql.md)目录视图。  
  
 *accent_sensitivity*  
 控制全文搜索是否区分音调符号的布尔值。 *accent_sensitivity*是**位**，使用以下值之一：  
  
|ReplTest1|重音区分设置是...|  
|-----------|----------------------------|  
|0|不区分<br /><br /> 以相同方式处理词，如"吧"及"咖啡厅"。|  
|1|区分<br /><br /> "咖啡厅"和"咖啡馆"等词的处理方式不同。|  
  
> [!NOTE]  
>  若要查看全文目录中该值的当前设置，请运行以下[!INCLUDE[tsql](../../includes/tsql-md.md)]语句： `SELECT fulltextcatalogproperty('` *catalog_name*`', 'AccentSensitivity');`。  
  
## <a name="table-returned"></a>返回的表  
  
|列名|数据类型|Description|  
|-----------------|---------------|-----------------|  
|关键字 (keyword)|**varbinary(128)**|断字符返回的给定关键字的十六进制表示形式。 该表示形式用于存储全文索引的关键字。 此值不是用户可读，但它对于相关给定的关键字输出返回的返回内容的一个全文索引的索引，如其他动态管理视图很有用[sys.dm_fts_index_keywords](../../relational-databases/system-dynamic-management-views/sys-dm-fts-index-keywords-transact-sql.md)和[sys.dm_fts_index_keywords_by_document](../../relational-databases/system-dynamic-management-views/sys-dm-fts-index-keywords-by-document-transact-sql.md)。<br /><br /> **注意：** OxFF 表示指示文件或数据集的末尾的特殊字符。|  
|group_id|**int**|包含一个整数值，用于区分从中生成给定字词的逻辑组。 例如，'`Server AND DB OR FORMSOF(THESAURUS, DB)"`' 生成以下英语 group_id 值：<br /><br /> 1：“服务器”<br />2:DB<br />3：DB|  
|phrase_id|**int**|包含一个整数值，用于区别断字符给出复合词（如 full-text）替代形式的情况。 有时，如果存在复合词（“multi-millon”），断字符将给出替代形式。 这些替代形式（短语）有时需要加以区别。<br /><br /> 例如，'`multi-million`' 生成以下英语 phrase_id 值：<br /><br /> 1 表示 `multi`<br />1 表示 `million`<br />2 表示 `multimillion`|  
|occurrence|**int**|指示分析结果中每个字词的顺序。 例如，对于短语“`SQL Server query processor`”，occurrence 会包含该英语短语中字词的以下 occurrence 值：<br /><br /> 1 表示 `SQL`<br />2 表示 `Server`<br />为 3 `query`<br />4 `processor`|  
|special_term|**nvarchar(4000)**|包含有关断字符给出的字词特征的信息，可以是以下值之一：<br /><br /> Exact match<br /><br /> Noise word<br /><br /> End of Sentence<br /><br /> End of paragraph<br /><br /> End of Chapter|  
|display_term|**nvarchar(4000)**|包含关键字的可读形式。 与旨在访问全文索引内容的函数一样，由于非规范化限制，此显示字词可能与原始字词并不完全相同。 不过，该字词应该具有足够高的准确性，可帮助您从原始输入中识别它。|  
|expansion_type|**int**|包含有关给定字词的扩展特性的信息，可以是以下值之一：<br /><br /> 0 = 单个词的情况<br /><br /> 2 = 变形扩展<br /><br /> 4 = 同义词库扩展/替换<br /><br /> 例如，请考虑同义词库将 run 定义为 `jog` 扩展的情况：<br /><br /> `<expansion>`<br /><br /> `<sub>run</sub>`<br /><br /> `<sub>jog</sub>`<br /><br /> `</expansion>`<br /><br /> 字词 `FORMSOF (FREETEXT, run)` 生成以下输出：<br /><br /> `run`，其中 expansion_type=0<br /><br /> `runs`，其中 expansion_type=2<br /><br /> `running`，其中 expansion_type=2<br /><br /> `ran`，其中 expansion_type=2<br /><br /> `jog`，其中 expansion_type=4|  
|source_term|**nvarchar(4000)**|从中生成或分析给定字词的字词或短语。 例如，对 '"`word breakers" AND stemmers'` 的查询生成以下英语 source_term 值：<br /><br /> `word breakers` 有关 display_term`word`<br />`word breakers` 有关 display_term`breakers`<br />`stemmers` 有关 display_term`stemmers`|  
  
## <a name="remarks"></a>备注  
 **sys.dm_fts_parser**支持的语法和功能的全文谓词，如[CONTAINS](../../t-sql/queries/contains-transact-sql.md)并[FREETEXT](../../t-sql/queries/freetext-transact-sql.md)，和函数，如[CONTAINSTABLE](../../relational-databases/system-functions/containstable-transact-sql.md)并[FREETEXTTABLE](../../relational-databases/system-functions/freetexttable-transact-sql.md)。  
  
## <a name="using-unicode-for-parsing-special-characters"></a>使用 Unicode 分析特殊字符  
 当分析查询字符串时， **sys.dm_fts_parser**使用您所连接的数据库的排序规则，除非您指定的查询字符串为 Unicode。 因此，非 Unicode 字符串，包含特殊字符，如 ü 或？，输出可能不会出现，具体取决于数据库排序规则。 若要处理独立于数据库排序规则的查询字符串，字符串前添加前缀`N`，即， `N'` *query_string*`'`。  
  
 有关详细信息，请参阅本主题后面的“C. 显示包含特殊字符的字符串的输出”。  
  
## <a name="when-to-use-sysdmftsparser"></a>何时使用 sys.dm_fts_parser  
 **sys.dm_fts_parser**可以出于调试目的非常强大。 一些主要的应用场景包括：  
  
-   了解给定断字符如何处理给定输入  
  
     当查询返回意外结果时，问题可能出在断字符分析和断开数据的方式。 通过使用 sys.dm_fts_parser，您可以找到断字符传递给全文索引的结果。 此外，还可以查看哪些字词是在全文索引中不搜索的非索引字。 对于给定的语言取决于它是否在指定的非索引字表中某个字词是否非索引字*stoplist_id*在函数中声明的值。  
  
     还要注意重音区分标志，用户可通过该标志了解断字符是如何根据重音区分信息分析输入的。  
  
-   了解词干分析器如何处理给定输入  
  
     通过指定包含以下 FORMSOF 子句的 CONTAINS 或 CONTAINSTABLE 查询，您可以了解断字符和词干分析器如何分析查询字词及其词干形式：  
  
    ```  
    FORMSOF( INFLECTIONAL, query_term )  
    ```  
  
     可以从结果中看出，将哪些字词传递给了全文索引。  
  
-   了解同义词库如何扩展或替换全部或部分输入  
  
     您还可以指定：  
  
    ```  
    FORMSOF( THESAURUS, query_term )  
    ```  
  
     此查询的结果显示了断字符和同义词库是如何交互以获得查询字词的。 您可以看到来自同义词库的扩展或替换，并确定实际针对全文索引发出的结果查询。  
  
     请注意，如果用户发出：  
  
    ```  
    FORMSOF( FREETEXT, query_term )  
    ```  
  
     将自动执行变形和同义词库功能。  
  
 除了上述应用场景外，sys.dm_fts_parser 还在很大程度上帮助您了解和解决很多其他的全文查询问题。  
  
## <a name="permissions"></a>权限  
 要求的成员身份**sysadmin**固定服务器角色和访问权限指定非索引字表。  
  
## <a name="examples"></a>示例  
  
### <a name="a-displaying-the-output-of-a-given-word-breaker-for-a-keyword-or-phrase"></a>A. 显示对某个关键字或短语使用给定断字符的输出  
 下面的示例返回对以下查询字符串使用英语断字符（LCID 为 1033）且不使用非索引字表的输出：  
  
 `The Microsoft business analysis`  
  
 禁用了重音区分。  
  
```sql
SELECT * FROM sys.dm_fts_parser (' "The Microsoft business analysis" ', 1033, 0, 0);  
```  
  
### <a name="b-displaying-the-output-of-a-given-word-breaker-in-the-context-of-stoplist-filtering"></a>B. 显示给定断字符在非索引字表筛选上下文中的输出  
 下面的示例返回对以下查询字符串使用英语断字符（LCID 为 1033）和英语非索引字表（ID 为 77）的输出：  
  
 `"The Microsoft business analysis" OR "MS revenue"`  
  
 禁用了重音区分。  
  
```sql
SELECT * FROM sys.dm_fts_parser (' "The Microsoft business analysis"  OR " MS revenue" ', 1033, 77, 0);  
```  
  
### <a name="c-displaying-the-output-of-a-string-that-contains-special-characters"></a>C. 显示包含特殊字符的字符串的输出  
 下面的示例使用 Unicode 来分析以下法语字符串：  
  
 `français`  
  
 示例指定了法语的 LCID `1036`，以及用户定义的非索引字表的 ID `5`。 启用了重音区分。  
  
```sql
SELECT * FROM sys.dm_fts_parser(N'français', 1036, 5, 1);  
```  
  
## <a name="see-also"></a>请参阅  
 [全文搜索和语义搜索动态管理视图和函数&#40;Transact SQL&#41;](../../relational-databases/system-dynamic-management-views/full-text-and-semantic-search-dynamic-management-views-functions.md)   
 [全文搜索](../../relational-databases/search/full-text-search.md)   
 [配置和管理断字符和词干分析器以便搜索](../../relational-databases/search/configure-and-manage-word-breakers-and-stemmers-for-search.md)   
 [配置和管理全文搜索同义词库文件](../../relational-databases/search/configure-and-manage-thesaurus-files-for-full-text-search.md)   
 [为全文搜索配置和管理非索引字和非索引字表](../../relational-databases/search/configure-and-manage-stopwords-and-stoplists-for-full-text-search.md)   
 [使用全文搜索查询](../../relational-databases/search/query-with-full-text-search.md)   
 [使用全文搜索查询](../../relational-databases/search/query-with-full-text-search.md)   
 [安全对象](../../relational-databases/security/securables.md)  
  
  
