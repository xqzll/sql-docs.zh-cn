---
title: CERTPROPERTY (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 07/24/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: t-sql
ms.topic: language-reference
f1_keywords:
- CERTPROPERTY
- CERTPROPERTY_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- certificates [SQL Server], schema names
- schemas [SQL Server], names
- CERTPROPERTY function
ms.assetid: 966c09aa-bc4e-45b0-ba53-c8381871f638
author: VanMSFT
ms.author: vanto
manager: craigg
ms.openlocfilehash: c27111dac0da8d9248bea1b7d7408cd70130d01b
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "65948807"
---
# <a name="certproperty-transact-sql"></a>CERTPROPERTY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

返回指定证书属性的值。
  
![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "主题链接图标") [TRANSACT-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>语法  
  
```sql
CertProperty ( Cert_ID , '<PropertyName>' )  
  
<PropertyName> ::=  
   Expiry_Date | Start_Date | Issuer_Name   
   | Cert_Serial_Number | Subject | SID | String_SID   
```  
  
## <a name="arguments"></a>参数  
Cert_ID   
int 数据类型的证书 ID 值。
  
Expiry_Date   
证书过期日期。
  
Start_Date   
证书开始生效的日期。
  
Issuer_Name   
证书颁发者的名称。
  
Cert_Serial_Number   
证书序列号。
  
*主题*  
证书主题。
  
 SID   
证书 SID。 这也是映射到该证书的所有登录或用户的 SID。
  
String_SID   
字符串形式的证书的 SID。 这也是映射到该证书的所有登录或用户的 SID。
  
## <a name="return-types"></a>返回类型
必须以单引号括起属性规范。
  
返回类型取决于在函数调用中指定的属性。 返回类型 sql_variant 包装所有返回值  。
-   Expiry_Date 和 Start_Date 返回 datetime    。  
-   Cert_Serial_Number、Issuer_Name、String_SID 和 Subject 全部都返回 nvarchar      。  
-   SID 返回 varbinary   。  
  
## <a name="remarks"></a>Remarks  
请参阅 [sys.certificates](../../relational-databases/system-catalog-views/sys-certificates-transact-sql.md) 目录视图中的证书信息。
  
## <a name="permissions"></a>权限  
需要对证书具有相应的权限，并且调用方对证书的 VIEW 权限没有被拒绝。 请参阅 [CREATE CERTIFICATE (Transact-SQL)](../../t-sql/statements/create-certificate-transact-sql.md) 和 [GRANT CERTIFICATE PERMISSIONS (Transact-SQL)](../../t-sql/statements/grant-certificate-permissions-transact-sql.md)，获取有关证书权限的详细信息。
  
## <a name="examples"></a>示例  
以下示例返回证书主题。
  
```sql
-- First create a certificate.  
CREATE CERTIFICATE Marketing19 WITH   
    START_DATE = '04/04/2004' ,  
    EXPIRY_DATE = '07/07/2040' ,  
    SUBJECT = 'Marketing Print Division';  
GO  
  
-- Now use CertProperty to examine certificate  
-- Marketing19's properties.  
DECLARE @CertSubject sql_variant;  
set @CertSubject = CertProperty( Cert_ID('Marketing19'), 'Subject');  
PRINT CONVERT(nvarchar, @CertSubject);  
GO  
```  
  
## <a name="see-also"></a>另请参阅
[CREATE CERTIFICATE (Transact-SQL)](../../t-sql/statements/create-certificate-transact-sql.md)  
[ALTER CERTIFICATE (Transact-SQL)](../../t-sql/statements/alter-certificate-transact-sql.md)  
[CERT_ID (Transact-SQL)](../../t-sql/functions/cert-id-transact-sql.md) 
[加密层次结构](../../relational-databases/security/encryption/encryption-hierarchy.md)
[sys.certificates (Transact-SQL)](../../relational-databases/system-catalog-views/sys-certificates-transact-sql.md) 
[安全目录视图 (Transact-SQL)](../../relational-databases/system-catalog-views/security-catalog-views-transact-sql.md)
  
  
