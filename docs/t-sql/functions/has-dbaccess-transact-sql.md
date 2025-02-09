---
title: HAS_DBACCESS (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 10/23/2017
ms.prod: sql
ms.prod_service: sql-data-warehouse, pdw, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- HAS_DBACCESS_TSQL
- HAS_DBACCESS
dev_langs:
- TSQL
helpviewer_keywords:
- permissions [SQL Server], verifying
- permissions [SQL Server], user access status
- HAS_DBACCESS
- checking permission status
- verifying permission status
- users [SQL Server], access rights status
- testing permissions
- status information [SQL Server], user access
ms.assetid: 99b43a72-0722-4a7b-a493-bdee1c74c7b9
author: VanMSFT
ms.author: vanto
manager: craigg
monikerRange: '>=aps-pdw-2016||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 3bf3b9c4dfd1216cccadb3a82e949168626206a6
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "65943121"
---
# <a name="hasdbaccess-transact-sql"></a>HAS_DBACCESS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

  返回信息，说明用户是否可以访问指定的数据库。  
  
 ![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "主题链接图标") [TRANSACT-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>语法  
  
```  
HAS_DBACCESS ( 'database_name' )  
```  
  
## <a name="arguments"></a>参数  
 'database_name'   
 数据库的名称，用户希望获取有关该数据库的访问信息。 database_name 的数据类型为 sysname   。  
  
## <a name="return-types"></a>返回类型  
 **int**  
  
## <a name="remarks"></a>Remarks  
 如果用户可以访问该数据库，则 HAS_DBACCESS 返回 1。如果用户不能访问该数据库，则返回 0。如果该数据库名无效，则返回 NULL。  
  
 如果数据库处于脱机或可疑状态，HAS_DBACCESS 将返回 0。  
  
 如果数据库处于单用户模式并且该数据库正由另一个用户使用，HAS_DBACCESS 将返回 0。  
  
## <a name="permissions"></a>权限  
 要求具有 public 角色的成员身份。  
  
## <a name="examples"></a>示例  
 下面的示例测试当前用户是否有权访问 `AdventureWorks2012` 数据库。  
  
```  
SELECT HAS_DBACCESS('AdventureWorks2012');  
GO  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>示例：[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] 和 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 下面的示例测试当前用户是否有权访问 `AdventureWorksPDW2012` 数据库。  
  
```  
SELECT HAS_DBACCESS('AdventureWorksPDW2012');  
GO  
```  
  
## <a name="see-also"></a>另请参阅  
 [IS_MEMBER (Transact-SQL)](../../t-sql/functions/is-member-transact-sql.md)   
 [IS_SRVROLEMEMBER (Transact-SQL)](../../t-sql/functions/is-srvrolemember-transact-sql.md)  
  
  

