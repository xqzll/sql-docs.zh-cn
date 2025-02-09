---
title: DECRYPTBYASYMKEY (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- DECRYPTBYASYMKEY
- DECRYPTBYASYMKEY_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- asymmetric keys [SQL Server], DECRYPTBYASYMKEY function
- DECRYPTBYASYMKEY function
- decryption [SQL Server], asymmetric keys
ms.assetid: d9ebcd30-f01c-4cfe-b95e-ffe6ea13788b
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: 3a46b3f19bc676b0b8e9f86db684328940b6e520
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "65945554"
---
# <a name="decryptbyasymkey-transact-sql"></a>DECRYPTBYASYMKEY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

此函数使用非对称密钥解密已加密数据。  
  
 ![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "主题链接图标") [TRANSACT-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>语法  
  
```  
  
DecryptByAsymKey (Asym_Key_ID , { 'ciphertext' | @ciphertext }   
    [ , 'Asym_Key_Password' ] )  
```  
  
## <a name="arguments"></a>参数  
 Asym_Key_ID   
数据库中非对称密钥的 ID。 Asym_Key_ID 具有 int 数据类型   。  
  
 ciphertext   
使用非对称密钥加密的数据字符串。  
  
 @ciphertext  
varbinary 类型的变量，包含使用非对称密钥进行加密的数据  。  
  
 Asym_Key_Password   
用于加密数据库中非对称密钥的密码。  
  
## <a name="return-types"></a>返回类型  
varbinary（最大大小为 8,000 个字节）  。  
  
## <a name="remarks"></a>Remarks  
与对称加密/解密相比，非对称加密/解密的成本更高。 处理大型数据集时（例如存储在表中的用户数据），建议开发人员避免使用非对称密钥加密/解密。  
  
## <a name="permissions"></a>权限  
`DECRYPTBYASYMKEY` 需要对非对称密钥具有 CONTROL 权限。  
  
## <a name="examples"></a>示例  
此示例对最初使用非对称密钥 `JanainaAsymKey02` 加密的已加密文本进行解密。 `AdventureWorks2012.ProtectedData04` 存储此非对称密钥。 该示例使用非对称密钥 `JanainaAsymKey02` 对返回的数据进行解密。 该示例使用密码 `pGFD4bb925DGvbd2439587y` 对此非对称密钥进行解密。 该示例将返回的纯文本转换为类型 nvarchar  。  
  
```  
SELECT CONVERT(nvarchar(max),  
    DecryptByAsymKey( AsymKey_Id('JanainaAsymKey02'),   
    ProtectedData, N'pGFD4bb925DGvbd2439587y' ))   
AS DecryptedData   
FROM [AdventureWorks2012].[Sales].[ProtectedData04]   
WHERE Description = N'encrypted by asym key''JanainaAsymKey02''';  
GO  
```  
  
## <a name="see-also"></a>另请参阅  
 [ENCRYPTBYASYMKEY (Transact-SQL)](../../t-sql/functions/encryptbyasymkey-transact-sql.md)   
 [CREATE ASYMMETRIC KEY &#40;Transact-SQL&#41;](../../t-sql/statements/create-asymmetric-key-transact-sql.md)   
 [ALTER ASYMMETRIC KEY (Transact-SQL)](../../t-sql/statements/alter-asymmetric-key-transact-sql.md)   
 [DROP ASYMMETRIC KEY (Transact-SQL)](../../t-sql/statements/drop-asymmetric-key-transact-sql.md)   
 [选择加密算法](../../relational-databases/security/encryption/choose-an-encryption-algorithm.md)   
 [加密层次结构](../../relational-databases/security/encryption/encryption-hierarchy.md)  
  
  
