---
title: sp_syscollector_update_collector_type (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_syscollector_update_collector_type_TSQL
- sp_syscollector_update_collector_type
dev_langs:
- TSQL
helpviewer_keywords:
- sp_syscollector_update_collector_type
- data collector [SQL Server], stored procedures
ms.assetid: 3c414dfd-d9ca-4320-81aa-949465b967bf
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 9d3529d01966c7f9780183d663823d8f4033f47a
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "63001367"
---
# <a name="spsyscollectorupdatecollectortype-transact-sql"></a>sp_syscollector_update_collector_type (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  为收集项更新收集器类型。 给定的名称和收集器类型的 GUID，更新收集器类型配置，包括收集和上载包、 参数架构以及参数格式化程序架构。  
  
 ![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "主题链接图标") [TRANSACT-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>语法  
  
```  
  
sp_syscollector_update_collector_type [ @collector_type_uid = ] 'collector_type_uid' OUTPUT  
          , [ @name = ] 'name'  
          , [ @parameter_schema = ] 'parameter_schema'  
          , [ @collection_package_id = ] collection_package_id  
          , [ @upload_package_id = ] upload_package_id  
```  
  
## <a name="arguments"></a>参数  
`[ @collector_type_uid = ] 'collector_type_uid'` 是收集器类型的 GUID。 *collector_type_uid*是**uniqueidentifier**，并且如果它为的 NULL，它将自动创建并作为 OUTPUT 返回。  
  
`[ @name = ] 'name'` 是收集器类型的名称。 *名称*是**sysname** ，并且必须指定。  
  
`[ @parameter_schema = ] 'parameter_schema'` 是此收集器类型的 XML 架构。 *parameter_schema*是**xml**和可能所必需的某些收集器类型。 如果它不是必需的，此参数可为 NULL。  
  
`[ @collection_package_id = ] collection_package_id` 指向的本地唯一标识符[!INCLUDE[ssIS](../../includes/ssis-md.md)]由收集组的收集包。 *collection_package_id*是**uniqueidentifer**和是必需的。 若要获取的值*collection_package_id*，查询 msdb 数据库中的 dbo.syscollector_collector_types 系统视图。  
  
`[ @upload_package_id = ] upload_package_id` 指向的本地唯一标识符[!INCLUDE[ssIS](../../includes/ssis-md.md)]上载收集组使用的包。 *upload_package_id*是**uniqueidentifier**和是必需的。 若要获取的值*upload_package_id*，查询 msdb 数据库中的 dbo.syscollector_collector_types 系统视图。  
  
## <a name="return-code-values"></a>返回代码值  
 **0** （成功） 或**1** （失败）  
  
## <a name="permissions"></a>权限  
 要求的成员身份**dc_admin** （拥有 EXECUTE 权限） 固定的数据库角色。  
  
## <a name="example"></a>示例  
 此示例更新一般 T-SQL 查询收集器类型。 （在此示例中，使用一般 T-SQL 查询收集器类型的默认架构。）  
  
```  
USE msdb;  
GO  
EXEC sp_syscollector_update_collector_type  
@collector_type_uid = '302E93D1-3424-4BE7-AA8E-84813ECF2419',  
@name = 'Generic T-SQL Query Collector Type',  
@parameter_schema = '<?xml version="1.0" encoding="utf-8"?>  
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema" targetNamespace="DataCollectorType">  
  <xs:element name="TSQLQueryCollector">  
<xs:complexType>  
  <xs:sequence>  
<xs:element name="Query" minOccurs="1" maxOccurs="unbounded">  
  <xs:complexType>  
<xs:sequence>  
  <xs:element name="Value" type="xs:string" />  
  <xs:element name="OutputTable" type="xs:string" />  
</xs:sequence>  
  </xs:complexType>  
</xs:element>  
<xs:element name="Databases" minOccurs="0" maxOccurs="1">  
  <xs:complexType>  
<xs:sequence>  
  <xs:element name="Database" minOccurs="0" maxOccurs="unbounded" type="xs:string" />  
</xs:sequence>  
<xs:attribute name="UseSystemDatabases" type="xs:boolean" use="optional" />  
<xs:attribute name="UseUserDatabases" type="xs:boolean" use="optional" />  
  </xs:complexType>  
</xs:element>  
  </xs:sequence>  
</xs:complexType>  
  </xs:element>  
</xs:schema>',  
@collection_package_id = '292B1476-0F46-4490-A9B7-6DB724DE3C0B',  
@upload_package_id = '6EB73801-39CF-489C-B682-497350C939F0';  
GO  
```  
  
## <a name="see-also"></a>请参阅  
 [系统存储过程 (Transact-SQL)](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [“数据收集”](../../relational-databases/data-collection/data-collection.md)  
  
  
