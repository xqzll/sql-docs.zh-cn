---
title: sys.sequences (Transact SQL) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sys.sequences_TSQL
- sys.sequences
- sequences
- sequences_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sequence number object, sys. sequences catalog view
- sys.sequences catalog view
ms.assetid: 0e1b0e32-1cce-40f7-83c8-860ec660138a
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 64532403f495a65cd61fbf6a8bc95369a0a4add3
ms.sourcegitcommit: 0a4879dad09c6c42ad1ff717e4512cfea46820e9
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/27/2019
ms.locfileid: "67413080"
---
# <a name="syssequences-transact-sql"></a>sys.sequences (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  数据库中的每个序列对象各占一行。  
  
|列名|数据类型|Description|  
|-----------------|---------------|-----------------|  
|\<继承列 >||继承中的所有列[sys.objects](../../relational-databases/system-catalog-views/sys-objects-transact-sql.md)。|  
|**start_value**|**sql_variant 不为 NULL**|序列对象的起始值。 如果使用 ALTER SEQUENCE 重新启动序列对象，它将以此值重新启动。 当序列对象周期它继续到**minimum_value**或**maximum_value**，而不**start_value**。|  
|**increment**|**sql_variant 不为 NULL**|用于在每个生成值后使序列对象递增的值。|  
|**minimum_value**|**sql_variant NULL**|序列对象可以生成的最小值。 在达到此值后，序列对象将在尝试生成多个值时返回错误，或在指定 CYCLE 选项时重新启动。 如果尚未指定任何 MINVALUE，此列将返回序列生成器的数据类型所支持的最小值。|  
|**maximum_value**|**sql_variant NULL**|序列对象可以生成的最大值。 在达到此值后，序列对象将在尝试生成多个值时开始返回错误，或在指定 CYCLE 选项时重新启动。 如果未指定任何 MAXVALUE，此列将返回序列对象的数据类型所支持的最大值。|  
|**is_cycling**|**位 NOT NULL**|如果为序列对象指定 NO CYCLE，则返回 0；如果指定 CYCLE，则返回 1。|  
|**is_cached**|**位 NOT NULL**|如果为序列对象指定 NO CACHE，则返回 0；如果指定 CACHE，则返回 1。|  
|**cache_size**|**int NULL**|返回序列对象的指定缓存大小。 如果创建序列时使用了 NO CACHE 选项或者指定了 CACHE 但未指定缓存大小，此列将包含 NULL。 如果缓存大小指定的值大于序列对象可以返回的值的最大数量，仍会显示该无法获得的缓存大小。|  
|**system_type_id**|**tinyint NOT NULL**|序列对象的数据类型的系统类型的 ID。|  
|**user_type_id**|**int NOT NULL**|用作用户定义的序列对象的数据类型的 ID。|  
|**精度**|**tinyint NOT NULL**|数据类型的最大精度。|  
|**scale**|**tinyint NOT NULL**|数据类型的最大小数位数。 小数位数与精度一起返回，以便为用户提供完整的元数据。 由于序列对象只允许使用整数类型，因此其小数位数始终为 0。|  
|**current_value**|**sql_variant 不为 NULL**|强制的最后一个值。 从最近执行 NEXT VALUE FOR 函数或执行的最后一个值返回的值，即**sp_sequence_get_range**过程。 如果从未使用过该序列，则返回 START WITH 值。|  
|**is_exhausted**|**位 NOT NULL**|0 表示可从序列中生成多个值。 1 表示序列对象已达到 MAXVALUE 参数，该序列未设置为 CYCLE。 使用 ALTER SEQUENCE 重新启动序列之前，NEXT VALUE FOR 函数将返回错误。|  
|**last_used_value**|**sql_variant NULL**|返回生成的最后一个值[Next Value For](../../t-sql/functions/next-value-for-transact-sql.md)函数。 适用于 SQL Server 2017 及更高版本。|  
  
## <a name="permissions"></a>权限  
 在 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 及更高版本中，目录视图中仅显示用户拥有的安全对象的元数据，或用户对其拥有某些权限的安全对象的元数据。 有关详细信息，请参阅 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)。  
  
## <a name="see-also"></a>请参阅  
 [序列号](../../relational-databases/sequence-numbers/sequence-numbers.md)   
 [CREATE SEQUENCE (Transact-SQL)](../../t-sql/statements/create-sequence-transact-sql.md)   
 [ALTER SEQUENCE (Transact-SQL)](../../t-sql/statements/alter-sequence-transact-sql.md)   
 [DROP SEQUENCE (Transact-SQL)](../../t-sql/statements/drop-sequence-transact-sql.md)   
 [NEXT VALUE FOR (Transact-SQL)](../../t-sql/functions/next-value-for-transact-sql.md)   
 [sp_sequence_get_range (Transact-SQL)](../../relational-databases/system-stored-procedures/sp-sequence-get-range-transact-sql.md)  
  
  
