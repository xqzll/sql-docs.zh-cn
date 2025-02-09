---
title: DROP EXTERNAL LANGUAGE (Transact-SQL) - SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 05/22/2019
ms.prod: sql
ms.technology: t-sql
ms.topic: language-reference
author: nelgson
ms.author: negust
ms.reviewer: dphansen
manager: cgronlun
monikerRange: '>=sql-server-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 29bb832fc1123b5261088b52232b693ca1c10138
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "65994935"
---
# <a name="drop-external-library-transact-sql"></a>DROP EXTERNAL LIBRARY (Transact-SQL)  
[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

删除一个现有外部语言。

## <a name="syntax"></a>语法

```text
DROP EXTERNAL LANGUAGE <language_name>
```

### <a name="arguments"></a>参数

**language_name**

语言是数据库范围的对象。 语言名称在数据库中必须唯一。

## <a name="permissions"></a>权限

必须拥有 ALTER ANY EXTERNAL LANGUAGE 权限，才能删除语言。 默认情况下，任何数据库所有者或对象所有者也可以删除外部语言。

> [!NOTE]
> 请注意，在删除外部语言之前，需要删除引用外部语言的外部库。

### <a name="return-values"></a>返回值

如果语句成功，则返回信息性消息。

## <a name="remarks"></a>Remarks

在删除外部语言之前，需要删除指定的语言的所有外部库。

## <a name="examples"></a>示例

创建外部语言 Java  ：

```sql
CREATE EXTERNAL LANGUAGE Java 
FROM (CONTENT = N'<path-to-zip>', FILE_NAME = 'javaextension.dll');
GO
```

删除外部语言：

```sql
DROP EXTERNAL LANGUAGE Java;
```

## <a name="see-also"></a>另请参阅

[CREATE EXTERNAL LANGUAGE (Transact-SQL)](create-external-language-transact-sql.md)  
[ALTER EXTERNAL LANGUAGE (Transact-SQL)](alter-external-language-transact-sql.md)  
[sys.external_languages](../../relational-databases/system-catalog-views/sys-external-languages-transact-sql.md)  
[sys.external_language_files](../../relational-databases/system-catalog-views/sys-external-language-files-transact-sql.md)  
