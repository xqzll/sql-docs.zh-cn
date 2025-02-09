---
title: ALTER DATABASE SCOPED CREDENTIAL (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 02/27/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- ALTER DATABASE SCOPED CREDENTIAL
- ALTER_DATABASE_SCOPED_CREDENTIAL_TSQL
helpviewer_keywords:
- ALTER DATABASE SCOPED CREDENTIAL statement
- credentials [SQL Server], ALTER DATABASE SCOPED CREDENTIAL statement
ms.assetid: 966b75b5-ca87-4203-8bf9-95c4e00cb0b5
author: VanMSFT
ms.author: vanto
manager: craigg
monikerRange: = azuresqldb-current || = azure-sqldw-latest || = sqlallproducts-allversions
ms.openlocfilehash: 0e9ac1c3e0ff2298acf3b155d5b99189a80e30f5
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "62719397"
---
# <a name="alter-database-scoped-credential-transact-sql"></a>ALTER DATABASE SCOPED CREDENTIAL (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  更改数据库作用域凭据的属性。  
  
 ![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "主题链接图标") [TRANSACT-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>语法  
  
```  
  
ALTER DATABASE SCOPED CREDENTIAL credential_name WITH IDENTITY = 'identity_name'  
    [ , SECRET = 'secret' ]  
```  
  
## <a name="arguments"></a>参数  
 credential_name  
 指定要更改的数据库作用域凭据的名称。  
  
 IDENTITY ='identity_name'  
 指定从服务器外部进行连接时要使用的帐户名称。 要从 Azure Blob 存储导入文件，标识名称必须是 `SHARED ACCESS SIGNATURE`。  有关共享访问签名的详细信息，请参阅[使用共享访问签名 (SAS)](https://docs.microsoft.com/azure/storage/storage-dotnet-shared-access-signature-part-1)。  
    
  
 SECRET ='secret'  
 指定发送身份验证所需的机密内容。 从 Azure Blob 存储导入文件时需要 *secret*。 在其他用途中，*secret* 可能是可选的。   
> [!WARNING]
>  SAS 密钥值可以“?”（问号）开头。 使用 SAS 密钥时，必须删除前导“?”。 否则会阻止操作。    
  
## <a name="remarks"></a>Remarks  
 当数据库作用域凭据发生更改时，identity_name 和 secret 的值都将重置。 如果未指定可选参数 SECRET 的值，则存储的密码值将设置为 NULL。  
  
 使用服务主密钥对密码进行加密。 如果重新生成服务主密钥，则需要使用新服务主密钥对该密码重新加密。  
  
 可在 [sys.database_scoped_credentials](../../relational-databases/system-catalog-views/sys-database-scoped-credentials-transact-sql.md) 目录视图中查看有关数据库范围凭据的信息。  
  
## <a name="permissions"></a>权限  
 需要对凭据拥有 `ALTER` 权限。  
  
## <a name="examples"></a>示例  
  
### <a name="a-changing-the-password-of-a-database-scoped-credential"></a>A. 更改数据库作用域凭据的密码  
 以下示例将更改存储在名为 `Saddles` 的数据库作用域凭据中的密码。 该数据库作用域凭据包含 Windows 登录名 `RettigB` 及其密码。 使用 SECRET 子句将新密码添加到数据库作用域凭据。  
  
```  
ALTER DATABASE SCOPED CREDENTIAL AppCred WITH IDENTITY = 'RettigB',   
    SECRET = 'sdrlk8$40-dksli87nNN8';  
GO  
```  
  
### <a name="b-removing-the-password-from-a-credential"></a>B. 删除凭据的密码  
 以下示例将删除名为 `Frames` 的数据库作用域凭据中的密码。 该数据库作用域凭据包含 Windows 登录名 `Aboulrus8` 和一个密码。 因为未指定 SECRET 选项，所以执行该语句后，数据库作用域凭据的密码为空。  
  
```  
ALTER DATABASE SCOPED CREDENTIAL Frames WITH IDENTITY = 'Aboulrus8';  
GO  
```  
  
## <a name="see-also"></a>另请参阅  
 [凭据（数据库引擎）](../../relational-databases/security/authentication-access/credentials-database-engine.md)   
 [CREATE DATABASE SCOPED CREDENTIAL (Transact-SQL)](../../t-sql/statements/create-database-scoped-credential-transact-sql.md)   
 [DROP DATABASE SCOPED CREDENTIAL (Transact-SQL)](../../t-sql/statements/drop-database-scoped-credential-transact-sql.md)   
 [sys.database_scoped_credentials](../../relational-databases/system-catalog-views/sys-database-scoped-credentials-transact-sql.md)   
 [CREATE CREDENTIAL &#40;Transact-SQL&#41;](../../t-sql/statements/create-credential-transact-sql.md)   
 [sys.credentials (Transact-SQL)](../../relational-databases/system-catalog-views/sys-credentials-transact-sql.md)  
  
  
