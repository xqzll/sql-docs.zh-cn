---
title: ASYMKEY_ID (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/24/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- AsymKey_ID
- ASYMKEY_ID_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- asymmetric keys [SQL Server], AsymKey_ID
- ASYMKEY_ID function
- encryption [SQL Server], asymmetric keys
- identification numbers [SQL Server], asymmetric keys
- IDs [SQL Server], asymmetric keys
- cryptography [SQL Server], asymmetric keys
ms.assetid: d697daf8-2106-4ebb-b09a-ca0be465d747
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: 48bb97bdf073026ffdc7cde48eac1b295a06bd75
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "65944964"
---
# <a name="asymkeyid-transact-sql"></a>ASYMKEY_ID (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

返回非对称密钥的 ID。
  
![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "主题链接图标") [TRANSACT-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>语法  
  
```sql
ASYMKEY_ID ( 'Asym_Key_Name' )  
```  
  
## <a name="arguments"></a>参数  
*Asym_Key_Name*  
数据库中非对称密钥的名称。
  
## <a name="return-types"></a>返回类型
 **int**  
  
## <a name="permissions"></a>权限  
需要对非对称密钥具有相应的权限，并且调用方对非对称密钥的 VIEW 权限没有被拒绝。 有关非对称密钥权限的详细信息，请参阅 [CREATE ASYMMETRIC KEY (Transact-SQL)](../../t-sql/statements/create-asymmetric-key-transact-sql.md)。
  
## <a name="examples"></a>示例  
此示例返回非对称密钥 `ABerglundKey11` 的 ID。
  
```sql
SELECT ASYMKEY_ID('ABerglundKey11');  
GO  
```  
  
## <a name="see-also"></a>另请参阅
[CREATE ASYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-asymmetric-key-transact-sql.md)  
[ALTER ASYMMETRIC KEY (Transact-SQL)](../../t-sql/statements/alter-asymmetric-key-transact-sql.md)  
[DROP ASYMMETRIC KEY (Transact-SQL)](../../t-sql/statements/drop-asymmetric-key-transact-sql.md)  
[SIGNBYASYMKEY (Transact-SQL)](../../t-sql/functions/signbyasymkey-transact-sql.md)  
[VERIFYSIGNEDBYASYMKEY (Transact-SQL)](../../t-sql/functions/verifysignedbyasymkey-transact-sql.md)  
[加密层次结构](../../relational-databases/security/encryption/encryption-hierarchy.md)  
[sys.asymmetric_keys (Transact-SQL)](../../relational-databases/system-catalog-views/sys-asymmetric-keys-transact-sql.md)  
[安全性目录视图 (Transact-SQL)](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)  
[ASYMKEYPROPERTY (Transact-SQL)](../../t-sql/functions/asymkeyproperty-transact-sql.md)  
[KEY_ID (Transact-SQL)](../../t-sql/functions/key-id-transact-sql.md)
  
  
