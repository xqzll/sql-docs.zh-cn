---
title: '@@VERSION (Transact-SQL) | Microsoft Docs'
ms.custom: ''
ms.date: 03/20/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- '@@VERSION'
- '@@VERSION_TSQL'
dev_langs:
- TSQL
helpviewer_keywords:
- '@@VERSION function'
- current SQL Server installation information
- versions [SQL Server], @@VERSION
- processors [SQL Server], types
ms.assetid: 385ba80e-7c28-41a5-9cdb-5648f3785983
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 323ef47423e796443a50761e9ac1e1fb6153cb03
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "65947364"
---
# <a name="x40x40version---transact-sql-configuration-functions"></a>&#x40;&#x40;Version - Transact SQL 配置函数
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  返回 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的当前安装的系统和生成信息。  
  
 ![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "主题链接图标") [TRANSACT-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>语法  
  
```  
@@VERSION  
```  
  
## <a name="return-types"></a>返回类型  
 **nvarchar**  
  
## <a name="remarks"></a>Remarks  
 @@VERSION 结果显示为一个 nvarchar 字符串。 可以使用 [SERVERPROPERTY (Transact-SQL)](../../t-sql/functions/serverproperty-transact-sql.md) 函数检索各个属性值。  
  
 对于 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]，返回以下信息。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 版本  
  
-   处理器体系结构  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 生成日期  
  
-   版权声明  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 版本  
  
-   操作系统版本  
  
 对于 [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]，返回以下信息。  
  
-   版本 -“Microsoft SQL Azure”  
  
-   产品级别 -“(RTM)”  
  
-   产品版本  
  
-   生成日期  
  
-   版权声明  

> [!NOTE]  
> 我们已注意到一个问题，即 @@VERSION 报告的产品版本对于 Azure SQL 数据库来说不正确。 Azure SQL 数据库运行的 SQL Server 数据库引擎的版本始终领先于 SQL Server 的本地版本，且包含最新安全修补程序。 这意味着，此修补程序级别始终等同于或领先于 SQL Server 的本地版本，且 SQL Server 中提供的最新功能在 Azure SQL 数据库中可用。
>
> 若要以编程方式确定引擎版本，请使用 SELECT SERVERPROPERTY('EngineEdition')。 此查询将在 Azure SQL 数据库中针对单一数据库/弹性池返回“5”，针对托管实例返回“8”。 
>
> 解决此问题后，我们将更新文档。

  
## <a name="examples"></a>示例  
  
### <a name="a-return-the-current-version-of-includessnoversionincludesssnoversion-mdmd"></a>A:返回 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的当前版本  
 以下示例显示返回当前安装的版本信息。  
  
```  
SELECT @@VERSION AS 'SQL Server Version';  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>示例：[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] 和 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="b-return-the-current-version-of-includessdwincludesssdw-mdmd"></a>B. 返回 [!INCLUDE[ssDW](../../includes/ssdw-md.md)] 的当前版本  
  
```  
SELECT @@VERSION AS 'SQL Server PDW Version';  
```  
  
## <a name="see-also"></a>另请参阅  
 [SERVERPROPERTY (Transact-SQL)](../../t-sql/functions/serverproperty-transact-sql.md)  
  
  

