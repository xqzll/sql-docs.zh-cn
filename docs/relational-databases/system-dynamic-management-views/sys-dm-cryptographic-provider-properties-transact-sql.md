---
title: sys.dm_cryptographic_provider_properties (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- dm_cryptographic_provider_properties_TSQL
- sys.dm_cryptographic_provider_properties
- sys.dm_cryptographic_provider_properties_TSQL
- dm_cryptographic_provider_properties
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_cryptographic_provider_properties dynamic management view
ms.assetid: 024b0095-6766-4189-a39a-d316c5ec2874
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: f8f497019dea80bbe79903c60531f506d7950371
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "62741975"
---
# <a name="sysdmcryptographicproviderproperties-transact-sql"></a>sys.dm_cryptographic_provider_properties (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  返回有关注册的加密提供程序的信息。  
  
 
|列名|数据类型|描述|  
|-----------------|---------------|-----------------|  
|provider_id|**int**|加密提供程序的标识号。|  
|guid|**uniqueidentifier**|唯一的提供程序 GUID。|  
|provider_version|**nvarchar(256)**|版本格式的提供程序*aa.bb.cccc.dd*。|  
|sqlcrypt_version|**nvarchar(256)**|主版本[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]加密 API 采用格式*aa.bb.cccc.dd*。|  
|friendly_name|**nvarchar(2048)**|提供程序提供的名称。|  
|authentication_type|**nvarchar(256)**|WINDOWS、 BASIC 或其他。|  
|symmetric_key_support|**tinyint**|0（不支持）<br /><br /> 1（支持）|  
|symmetric_key_export|**tinyint**|0（不支持）<br /><br /> 1（支持）|  
|symmetric_key_import|**tinyint**|0（不支持）<br /><br /> 1（支持）|  
|symmetric_key_persistance|**tinyint**|0（不支持）<br /><br /> 1（支持）|  
|asymmetric_key_support|**tinyint**|0（不支持）<br /><br /> 1（支持）|  
|asymmetric_key_export|**tinyint**|0（不支持）<br /><br /> 1（支持）|  
|symmetric_key_import|**tinyint**|0（不支持）<br /><br /> 1（支持）|  
|symmetric_key_persistance|**tinyint**|0（不支持）<br /><br /> 1（支持）|  
  
## <a name="remarks"></a>备注  
 sys.dm_cryptographic_provider_properties 视图是公开显示的。  
  
## <a name="see-also"></a>请参阅  
 [安全性目录视图 (Transact-SQL)](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)   
 [加密层次结构](../../relational-databases/security/encryption/encryption-hierarchy.md)   
 [可扩展密钥管理 &#40;EKM&#41;](../../relational-databases/security/encryption/extensible-key-management-ekm.md)   
 [CREATE CRYPTOGRAPHIC PROVIDER &#40;Transact-SQL&#41;](../../t-sql/statements/create-cryptographic-provider-transact-sql.md)   
 [与安全性相关的动态管理视图和函数 (Transact-SQL)](../../relational-databases/system-dynamic-management-views/security-related-dynamic-management-views-and-functions-transact-sql.md)  
  
  
