---
title: SET DATEFIRST (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- SET DATEFIRST
- SET_DATEFIRST_TSQL
- DATEFIRST_TSQL
- DATEFIRST
dev_langs:
- TSQL
helpviewer_keywords:
- first day of week [SQL Server]
- day of week [SQL Server]
- SET DATEFIRST option [SQL Server]
- DATEFIRST option [SQL Server]
- weekdays [SQL Server]
- options [SQL Server], date
ms.assetid: 6b0d0e52-8ac1-4f88-b091-f98d6fb8574a
author: CarlRabeler
ms.author: carlrab
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 8b369aafc68c7bf06ca56e325c036ffa0c7e4341
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "62639351"
---
# <a name="set-datefirst-transact-sql"></a>SET DATEFIRST (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  将一周的第一天设置为从 1 到 7 的一个数字。  
  
 有关所有 [!INCLUDE[tsql](../../includes/tsql-md.md)] 日期和时间数据类型及函数的概述，请参阅[日期和时间数据类型及函数 (Transact-SQL)](../../t-sql/functions/date-and-time-data-types-and-functions-transact-sql.md)。  
  
 ![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "主题链接图标") [TRANSACT-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>语法  
  
```  
-- Syntax for SQL Server and Azure SQL Database  
  
SET DATEFIRST { number | @number_var }   
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
SET DATEFIRST 7 ;  
```  
  
## <a name="arguments"></a>参数  
 number | @number_var     
 指示一周的第一天的一个整数。 可以是下列值之一。  
  
|ReplTest1|一周的第一天是|  
|-----------|------------------------------|  
|**1**|星期一|  
|**2**|星期二|  
|**3**|星期三|  
|**4**|星期四|  
|**5**|星期五|  
|**6**|星期六|  
|**7**英语）|星期日|  
  
## <a name="remarks"></a>Remarks  
 若要查看 SET DATEFIRST 的当前设置，请使用 [@@DATEFIRST](../../t-sql/functions/datefirst-transact-sql.md) 函数。  
  
 SET DATEFIRST 的设置是在执行或运行时设置，而不是在分析时设置。  
  
 指定 SET DATEFIRST 对 DATEDIFF 不起作用。 DATEDIFF 始终使用星期日作为每周的第一天，以确保函数是确定性的。  
  
## <a name="permissions"></a>权限  
 要求 **公共** 角色具有成员身份。  
  
## <a name="examples"></a>示例  
 以下示例显示了某个日期值对应的一周中的一天，并显示了更改 `DATEFIRST` 设置的效果。  
  
```  
-- SET DATEFIRST to U.S. English default value of 7.  
SET DATEFIRST 7;  
  
SELECT CAST('1999-1-1' AS datetime2) AS SelectDate  
    ,DATEPART(dw, '1999-1-1') AS DayOfWeek;  
-- January 1, 1999 is a Friday. Because the U.S. English default   
-- specifies Sunday as the first day of the week, DATEPART of 1999-1-1  
-- (Friday) yields a value of 6, because Friday is the sixth day of the   
-- week when you start with Sunday as day 1.  
  
SET DATEFIRST 3;  
-- Because Wednesday is now considered the first day of the week,  
-- DATEPART now shows that 1999-1-1 (a Friday) is the third day of the   
-- week. The following DATEPART function should return a value of 3.  
SELECT CAST('1999-1-1' AS datetime2) AS SelectDate  
    ,DATEPART(dw, '1999-1-1') AS DayOfWeek;  
GO  
```  
  
## <a name="see-also"></a>另请参阅  
 [SET 语句 (Transact-SQL)](../../t-sql/statements/set-statements-transact-sql.md)  
  
  

