---
title: sp_helpmergefilter (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_helpmergefilter
- sp_helpmergefilter_TSQL
helpviewer_keywords:
- sp_helpmergefilter
ms.assetid: f133a094-0009-4771-b93b-e86a5c01e40b
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 668233ad7ee79617caa60933a9eef33c5a810164
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "62502798"
---
# <a name="sphelpmergefilter-transact-sql"></a>sp_helpmergefilter (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  返回有关合并筛选器的信息。 此存储过程在发布服务器的任何数据库中执行。  
  
 ![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "主题链接图标") [TRANSACT-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>语法  
  
```  
  
sp_helpmergefilter [ @publication= ] 'publication'   
    [ , [ @article= ] 'article']  
    [ , [ @filtername= ] 'filtername']  
```  
  
## <a name="arguments"></a>参数  
`[ @publication = ] 'publication'` 是发布的名称。 *发布*是**sysname**，无默认值。  
  
`[ @article = ] 'article'` 是的名称。 *文章*是**sysname**，默认值为 **%** ，这会返回所有项目的名称。  
  
`[ @filtername = ] 'filtername'` 是要返回其信息的筛选器的名称。 *filtername*是**sysname**，默认值为 **%** ，表示返回有关项目或发布上定义的所有筛选器的信息。  
  
## <a name="result-sets"></a>结果集  
  
|列名|数据类型|Description|  
|-----------------|---------------|-----------------|  
|**join_filterid**|**int**|联接筛选器的 ID。|  
|**filtername**|**sysname**|筛选器名称。|  
|**联接项目名称**|**sysname**|联接项目名。|  
|**join_filterclause**|**nvarchar(2000)**|用于限定联接的筛选子句。|  
|**join_unique_key**|**int**|表示是否在唯一键上联接。|  
|**基表所有者**|**sysname**|基表所有者的名称。|  
|**基本表的名称**|**sysname**|基表的名称。|  
|**联接表的所有者**|**sysname**|与基表联接的表所有者的名称。|  
|**联接表名称**|**sysname**|与基表联接的表名。|  
|**项目名称**|**sysname**|与基表联接的表项目名。|  
|**filter_type**|**tinyint**|合并筛选器的类型，可以为下面的一种：<br /><br /> **1** = 联接筛选器<br /><br /> **2** = 逻辑记录关系<br /><br /> **3** = both|  
  
## <a name="return-code-values"></a>返回代码值  
 **0** （成功） 或**1** （失败）  
  
## <a name="remarks"></a>备注  
 **sp_helpmergefilter**合并复制中使用。  
  
## <a name="permissions"></a>权限  
 只有的成员**sysadmin**固定的服务器角色和**db_owner**固定的数据库角色可以执行**sp_helpmergefilter**。  
  
## <a name="see-also"></a>请参阅  
 [sp_addmergefilter (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-addmergefilter-transact-sql.md)   
 [sp_changemergefilter (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-changemergefilter-transact-sql.md)   
 [sp_dropmergefilter (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-dropmergefilter-transact-sql.md)   
 [系统存储过程 (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  
