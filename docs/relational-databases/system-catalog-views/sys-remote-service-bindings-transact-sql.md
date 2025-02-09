---
title: sys.remote_service_bindings (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.remote_service_bindings_TSQL
- remote_service_bindings_TSQL
- remote_service_bindings
- sys.remote_service_bindings
dev_langs:
- TSQL
helpviewer_keywords:
- sys.remote_service_bindings catalog view
ms.assetid: 4e1a885d-eed1-4993-9c87-e6fd781f437d
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: 2a0b326eef888ebf36fded7ae4ab95fe9f1b6bc0
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "62639123"
---
# <a name="sysremoteservicebindings-transact-sql"></a>sys.remote_service_bindings (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  每个远程服务绑定都在该目录视图中占一行。 
  
|列名|数据类型|Description|  
|-----------------|---------------|-----------------|  
|**名称**|**sysname**|该远程服务绑定的名称。 不可为 NULL。|  
|**remote_service_binding_id**|**int**|该远程服务绑定的 ID。 不可为 NULL。|  
|**principal_id**|**int**|拥有该远程服务绑定的数据库主体的 ID。 可以为 NULL。|  
|**remote_service_name**|**nvarchar(256)**|应用该绑定的远程服务的名称。 可以为 NULL。|  
|**service_contract_id**|**int**|应用该绑定的约定的 ID。 值 0 为通配符，表示该绑定应用于服务的所有约定。 不可为 NULL。|  
|**remote_principal_id**|**int**|远程服务绑定中指定的用户的 ID。 Service Broker 使用该用户拥有的证书与指定约定中的指定服务进行通信。 可以为 NULL。|  
|**is_anonymous_on**|**bit**|该远程服务绑定使用 ANONYMOUS 安全性。 未向目标服务提供开始会话的用户的标识。 不可为 NULL。|  
  
## <a name="permissions"></a>权限  
 [!INCLUDE[ssCatViewPerm](../../includes/sscatviewperm-md.md)] 有关详细信息，请参阅 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)。  
  
  
