---
title: sys.fulltext_semantic_languages (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- fulltext_semantic_languages
- fulltext_semantic_languages_TSQL
- sys.fulltext_semantic_languages
- sys.fulltext_semantic_languages_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.fulltext_semantic_languages catalog view
ms.assetid: b42a85e6-1db9-4a22-8a70-014574c95198
author: pmasl
ms.author: pelopes
ms.reviewer: mikeray
manager: craigg
ms.openlocfilehash: f1acc995223ba9785055839beb5e12b11ea7494f
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "64945664"
---
# <a name="sysfulltextsemanticlanguages-transact-sql"></a>sys.fulltext_semantic_languages (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  为在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例中注册统计模型的每种语言返回一行。 注册语言模型后，则支持对该语言进行语义索引。  
  
 此目录视图是类似于[sys.fulltext_languages &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-fulltext-languages-transact-sql.md)。  
    
||||  
|-|-|-|  
|**列名**|**类型**|**说明**|  
|lcid|ssNoversion|语言的 Microsoft Windows 区域设置标识符 (LCID)。|  
|name|sysname|是中的别名值[sys.syslanguages &#40;TRANSACT-SQL&#41; ](../../relational-databases/system-compatibility-views/sys-syslanguages-transact-sql.md)的值对应**lcid**，或是数值 LCID 的字符串表示形式。|  
  
## <a name="general-remarks"></a>一般备注  
 有关详细信息，请参阅 [安装和配置语义搜索](../../relational-databases/search/install-and-configure-semantic-search.md)。  
  
## <a name="metadata"></a>元数据  
 有关安装以支持语义索引的语义语言统计数据库的详细信息，请查询目录视图[sys.fulltext_semantic_language_statistics_database &#40;TRANSACT-SQL&#41; ](../../relational-databases/system-catalog-views/sys-fulltext-semantic-language-statistics-database-transact-sql.md).  
  
## <a name="security"></a>安全性  
  
### <a name="permissions"></a>权限  
 目录视图中仅显示用户拥有的安全对象的元数据，或用户对其拥有某些权限的安全对象的元数据。  
  
## <a name="examples"></a>示例  
 下面的示例演示如何通过查询**sys.fulltext_semantic_languages**若要获取有关所有注册的语言模型的信息的语义索引的当前实例上[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。  
  
```  
SELECT * FROM sys.fulltext_semantic_languages;  
GO  
```  
  
## <a name="see-also"></a>请参阅  
 [安装和配置语义搜索](../../relational-databases/search/install-and-configure-semantic-search.md)  
  
  
