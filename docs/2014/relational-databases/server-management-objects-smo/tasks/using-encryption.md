---
title: 使用加密 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- database master key [SMO]
- cryptography [SMO]
- cryptography [SQL Server], SMO
- encryption keys [SMO]
- encryption [SQL Server], SMO
- encryption [SMO]
- certificates [SMO]
- service master key [SMO]
ms.assetid: 405e0ed7-50a9-430e-a343-471f54b4af76
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 09de7053de66d2d280c2bc6da61b8bf6b2ebf55b
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "63213498"
---
# <a name="using-encryption"></a>使用加密
  在 SMO 中，服务主密钥由 <xref:Microsoft.SqlServer.Management.Smo.ServiceMasterKey> 对象表示。 它是由 <xref:Microsoft.SqlServer.Management.Smo.Server.ServiceMasterKey%2A> 对象的 <xref:Microsoft.SqlServer.Management.Smo.Server> 属性引用的。 可以通过使用 <xref:Microsoft.SqlServer.Management.Smo.ServiceMasterKey.Regenerate%2A> 方法重新生成服务主密钥。  
  
 数据库主密钥由 <xref:Microsoft.SqlServer.Management.Smo.MasterKey> 对象表示。 <xref:Microsoft.SqlServer.Management.Smo.MasterKey.IsEncryptedByServer%2A> 属性指示是否通过服务主密钥对数据库主密钥进行加密。 数据库主密钥发生变化时，主数据库中的加密副本会自动进行更新。  
  
 可以采用 <xref:Microsoft.SqlServer.Management.Smo.MasterKey.DropServiceKeyEncryption%2A> 方法删除服务密钥加密，并使用密码加密数据库主密钥。 在这种情况下，您必须显式打开数据库主密钥，然后才能访问已受到安全保护的私钥。  
  
 如果数据库已附加到 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 实例，则必须为数据库主密钥提供密码或执行 <xref:Microsoft.SqlServer.Management.Smo.MasterKey.AddServiceKeyEncryption%2A> 方法，才能生成一个未加密的数据库主密钥的副本，以便使用服务主密钥进行加密。 建议执行此步骤，从而无需显式打开数据库主密钥。  
  
 <xref:Microsoft.SqlServer.Management.Smo.MasterKey.Regenerate%2A> 方法将重新生成数据库主密钥。 当重新生成数据库主密钥时，会对所有使用该数据库主密钥加密的密钥进行解密，然后使用新的数据库主密钥对其进行加密。 <xref:Microsoft.SqlServer.Management.Smo.MasterKey.DropServiceKeyEncryption%2A> 方法将通过服务主密钥删除对数据库主密钥的加密。 <xref:Microsoft.SqlServer.Management.Smo.MasterKey.AddServiceKeyEncryption%2A> 可以通过服务主密钥对主密钥的副本进行加密，然后将副本存储在当前数据库和主数据库中。  
  
 在 SMO 中，证书由 <xref:Microsoft.SqlServer.Management.Smo.Certificate> 对象表示。 <xref:Microsoft.SqlServer.Management.Smo.Certificate> 对象具有指定公钥、主题名称、有效期以及有关颁发者的信息的属性。 可采用 `Grant`、`Revoke` 和 `Deny` 方法控制对证书的访问权限。  
  
## <a name="example"></a>示例  
 对于下面的代码示例，您必须选择编程环境、编程模板和编程语言才能创建应用程序。 有关详细信息，请参阅[在 Visual Studio.NET 中创建 Visual Basic SMO 项目](../../../database-engine/dev-guide/create-a-visual-basic-smo-project-in-visual-studio-net.md)并[创建 Visual C&#35; Visual Studio.NET 中的 SMO 项目](../how-to-create-a-visual-csharp-smo-project-in-visual-studio-net.md)。  
  
## <a name="adding-a-certificate-in-visual-basic"></a>在 Visual Basic 中添加证书  
 该代码示例使用加密密码创建简单证书。 与其他对象不同，<xref:Microsoft.SqlServer.Management.Smo.Certificate.Create%2A> 方法具有若干种重载。 该示例中所使用的重载将使用加密密码创建一个新证书。  
  
<!-- TODO: review snippet reference  [!CODE [SMO How to#SMO_VBCertificate1](SMO How to#SMO_VBCertificate1)]  -->  
  
## <a name="adding-a-certificate-in-visual-c"></a>在 Visual C# 中添加证书  
 该代码示例使用加密密码创建简单证书。 与其他对象不同，<xref:Microsoft.SqlServer.Management.Smo.Certificate.Create%2A> 方法具有若干种重载。 该示例中所使用的重载将使用加密密码创建一个新证书。  
  
```  
{  
            //Connect to the local, default instance of SQL Server.   
            {  
                Server srv = new Server();  
  
                //Reference the AdventureWorks2012 database.   
                Database db = srv.Databases["AdventureWorks2012"];  
  
                //Define a Certificate object variable by supplying the parent database and name in the constructor.   
                Certificate c = new Certificate(db, "Test_Certificate");  
  
                //Set the start date, expiry date, and description.   
                System.DateTime dt;  
                DateTime.TryParse("January 01, 2010", out dt);  
                c.StartDate = dt;  
                DateTime.TryParse("January 01, 2015", out dt);  
                c.ExpirationDate = dt;  
                c.Subject = "This is a test certificate.";  
                //Create the certificate on the instance of SQL Server by supplying the certificate password argument.   
                c.Create("pGFD4bb925DGvbd2439587y");  
            }  
        }   
```  
  
## <a name="adding-a-certificate-in-powershell"></a>在 PowerShell 中添加证书  
 该代码示例使用加密密码创建简单证书。 与其他对象不同，<xref:Microsoft.SqlServer.Management.Smo.Certificate.Create%2A> 方法具有若干种重载。 该示例中所使用的重载将使用加密密码创建一个新证书。  
  
```  
# Set the path context to the local, default instance of SQL Server and get a reference to AdventureWorks2012  
CD \sql\localhost\default\databases  
$db = get-item AdventureWorks2012  
  
#Create a certificate  
  
$c = New-Object -TypeName Microsoft.SqlServer.Management.Smo.Certificate -argumentlist $db, "Test_Certificate"  
$c.StartDate = "January 01, 2010"  
$c.Subject = "This is a test certificate."  
$c.ExpirationDate = "January 01, 2015"  
  
#Create the certificate on the instance of SQL Server by supplying the certificate password argument.  
$c.Create("pGFD4bb925DGvbd2439587y")  
  
```  
  
## <a name="see-also"></a>请参阅  
 [使用加密密钥](using-encryption.md)  
  
  
