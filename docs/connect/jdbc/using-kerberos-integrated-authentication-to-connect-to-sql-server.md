---
title: 使用 Kerberos 集成身份验证连接到 SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 01/21/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 687802dc-042a-4363-89aa-741685d165b3
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 89c87ecb551e3e75397bc431bdefc47fad18f8d2
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 06/07/2019
ms.locfileid: "66798602"
---
# <a name="using-kerberos-integrated-authentication-to-connect-to-sql-server"></a>使用 Kerberos 集成身份验证连接到 SQL Server

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

从 [!INCLUDE[jdbc_40](../../includes/jdbc_40_md.md)] 开始，应用程序可使用 authenticationScheme 连接属性指示它希望连接到使用类型 4 Kerberos 集成身份验证的数据库  。 请参阅[连接属性设置](../../connect/jdbc/setting-the-connection-properties.md)的连接属性的详细信息。 有关 Kerberos 的详细信息，请参阅[Microsoft Kerberos](https://go.microsoft.com/fwlink/?LinkID=100758)。

对 Java Krb5LoginModule 使用集成身份验证时，可使用[类 Krb5LoginModule](https://docs.oracle.com/javase/8/docs/jre/api/security/jaas/spec/com/sun/security/auth/module/Krb5LoginModule.html) 配置该模块  。

[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] 针对 IBM Java VM 设置了以下属性：

- **useDefaultCcache = true**
- **moduleBanner = false**

[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] 针对所有其他 Java VM 设置了以下属性：

- **useTicketCache = true**
- **doNotPrompt = true**

## <a name="remarks"></a>Remarks

早于[!INCLUDE[jdbc_40](../../includes/jdbc_40_md.md)]，应用程序可以指定集成身份验证 （使用 Kerberos 或 NTLM，具体取决于所提供） 通过使用**integratedSecurity**连接属性和通过引用**sqljdbc_auth.dll**，如中所述[创建连接 URL](../../connect/jdbc/building-the-connection-url.md)。

从 [!INCLUDE[jdbc_40](../../includes/jdbc_40_md.md)] 开始，应用程序可使用 authenticationScheme 连接属性指示它希望通过纯 Java Kerberos 实现连接到使用 Kerberos 集成身份验证的数据库  ：

- 如果你想要使用集成身份验证**Krb5LoginModule**，仍必须指定**integratedSecurity = true**连接属性。 然后，将还指定**authenticationScheme = JavaKerberos**连接属性。

- 若要继续使用集成身份验证**sqljdbc_auth.dll**，只需指定**integratedSecurity = true**连接属性 (和 （可选） **authenticationScheme =NativeAuthentication**)。

- 如果指定**authenticationScheme = JavaKerberos**但未同时指定**integratedSecurity = true**，则驱动程序将忽略**authenticationScheme**连接属性，并将希望在连接字符串中找到用户名和密码凭据。

使用数据源来创建连接时，可使用 setAuthenticationScheme 以编程方式设置身份验证方案，也可选择性地使用 setServerSpn 为 Kerberos 连接设置 SPN   。

新增了一个记录程序以支持 Kerberos 身份验证：com.microsoft.sqlserver.jdbc.internals.KerbAuthentication。 有关详细信息，请参阅[跟踪驱动程序操作](../../connect/jdbc/tracing-driver-operation.md)。

以下准则将有助于您配置 Kerberos：

1. 设置**AllowTgtSessionKey**为 1 的 Windows 注册表中。 有关详细信息，请参阅 [Windows Server 2003 中的 Kerberos 协议注册表项和 KDC 配置项](https://support.microsoft.com/kb/837361)。
2. 请确保 Kerberos 配置（UNIX 环境中的 krb5.conf）指向您的环境中正确的领域和 KDC。
3. 通过使用 kinit 或登录到域来初始化 TGT 缓存。
4. 当在 Windows Vista 或 Windows 7 操作系统上运行使用 authenticationScheme=JavaKerberos 的应用程序时，应使用标准用户帐户  。 但是，如果在管理员帐户下运行应用程序，则该程序必须以管理员特权运行。

> [!NOTE]  
> serverSpn 连接属性仅受 Microsoft JDBC Driver 4.2 及更高版本支持。

## <a name="service-principal-names"></a>服务主体名称

服务主体名称 (SPN) 是客户端用来唯一标识服务实例的名称。

可以使用 serverSpn 连接属性指定 SPN 或只需让驱动程序生成它（默认）  。 此属性采用“MSSQLSvc/fqdn:port\@REALM”的形式，其中 fqdn 是完全限定的域名，port 是端口号，REALM 是 SQL Server 的 Kerberos 领域（采用大写形式）。 如果 Kerberos 配置的默认领域与该 Server 的领域相同且不默认包含在内，则此属性的领域部分可选。 如果想要支持跨领域身份验证方案，其中 Kerberos 配置中的默认领域与服务器的领域不同，则必须使用 serverSpn 属性设置 SPN。

例如，你的 SPN 可能如下所示:"MSSQLSvc/some-server.zzz.corp.contoso.com:1433\@ZZZZ。CORP.CONTOSO.COM"

有关服务主体名称 (SPN) 的详细信息，请参阅：

- [如何在 SQL Server 中使用 Kerberos 身份验证](https://support.microsoft.com/kb/319723)

- [对 SQL Server 使用 Kerberos](https://go.microsoft.com/fwlink/?LinkId=207814)

> [!NOTE]  
> 在 6.2 版本的用于跨领域 Kerberos 的正确使用 JDBC 驱动程序之前将需要显式设置**serverSpn**。
>
> 6\.2 从版本开始，驱动程序将能够构建**serverSpn**默认情况下，即使使用跨领域 Kerberos。 尽管可以使用**serverSpn**显式过。

## <a name="creating-a-login-module-configuration-file"></a>创建登录模块配置文件

您也可选择指定 Kerberos 配置文件。 如果未指定配置文件，则以下设置有效：

Sun JVM  
 com.sun.security.auth.module.Krb5LoginModule required useTicketCache=true;

IBM JVM  
 com.ibm.security.auth.module.Krb5LoginModule required useDefaultCcache = true;

如果您决定创建登录模块配置文件，则该文件必须遵循以下格式：

```java
<name> {  
    <LoginModule> <flag> <LoginModule options>;  
    <optional_additional_LoginModules, flags_and_options>;  
};  
```

登录配置文件包含一个或多个条目，每个条目分别指定应用于某个特定应用程序或多个应用程序的基础身份验证技术。 例如，

```java
SQLJDBCDriver {  
   com.sun.security.auth.module.Krb5LoginModule required useTicketCache=true;  
};  
```

因此，每个登录模块配置文件条目均包含一个名称，该名称后跟一个或多个特定于 LoginModule 的条目，其中每个特定于 LoginModule 的条目以分号结尾，并且整个特定于 LoginModule 的条目组都包含在大括号中。 每个配置文件条目均以分号结尾。

除了允许驱动程序使用登录配置模块文件中指定的设置获取 Kerberos 凭据之外，驱动程序还可使用现有凭据。 如果应用程序需要使用多个用户凭据来创建连接，则这非常有用。

在尝试使用指定登录模块登录之前，如果现有凭据可用，则驱动程序将尝试使用它们。 因此，在使用 `Subject.doAs` 方法在特定上下文中执行代码时，可通过传递到 `Subject.doAs` 调用的凭据创建连接。

有关详细信息，请参阅 [JAAS 登录配置文件](https://docs.oracle.com/javase/8/docs/technotes/guides/security/jgss/tutorials/LoginConfigFile.html)和[类 Krb5LoginModule](https://docs.oracle.com/javase/8/docs/jre/api/security/jaas/spec/com/sun/security/auth/module/Krb5LoginModule.html)。

从 Microsoft JDBC Driver 6.2 开始，登录模块配置文件的名称可以根据需要传递使用连接属性`jaasConfigurationName`，这样，具有其自己的登录名配置的每个连接。

## <a name="creating-a-kerberos-configuration-file"></a>创建 Kerberos 配置文件

有关 Kerberos 配置文件的详细信息，请参阅 [Kerberos 需求](https://docs.oracle.com/javase/8/docs/technotes/guides/security/jgss/tutorials/KerberosReq.html)。

这是一个示例域配置文件，其中 YYYY 和 ZZZZ 是域名。

```ini
[libdefaults]  
default_realm = YYYY.CORP.CONTOSO.COM  
dns_lookup_realm = false  
dns_lookup_kdc = true  
ticket_lifetime = 24h  
forwardable = yes  

[domain_realm]  
.yyyy.corp.contoso.com = YYYY.CORP.CONTOSO.COM  
.zzzz.corp.contoso.com = ZZZZ.CORP.CONTOSO.COM  

[realms]  
        YYYY.CORP.CONTOSO.COM = {  
  kdc = krbtgt/YYYY.CORP. CONTOSO.COM @ YYYY.CORP. CONTOSO.COM  
  default_domain = YYYY.CORP. CONTOSO.COM  
}  

        ZZZZ.CORP. CONTOSO.COM = {  
  kdc = krbtgt/ZZZZ.CORP. CONTOSO.COM @ ZZZZ.CORP. CONTOSO.COM  
  default_domain = ZZZZ.CORP. CONTOSO.COM  
}  

```

## <a name="enabling-the-domain-configuration-file-and-the-login-module-configuration-file"></a>启用域配置文件和登录模块配置文件

您可以使用 -Djava.security.krb5.conf 启用域配置文件。 可以启用登录模块配置文件 **-Djava.security.auth.login.config**。

例如，可以使用以下命令启动应用程序：

```bash
Java.exe -Djava.security.auth.login.config=SQLJDBCDriver.conf -Djava.security.krb5.conf=krb5.ini <APPLICATION_NAME>  

```

## <a name="verifying-that-sql-server-can-be-accessed-via-kerberos"></a>验证可通过 Kerberos 访问 SQL Server

在 SQL Server Management Studio 中运行以下查询：

```sql
select auth_scheme from sys.dm_exec_connections where session_id=\@\@spid
```

请确保您具有运行此查询的必要权限。

## <a name="constrained-delegation"></a>约束委派

从 Microsoft JDBC Driver 6.2 开始，该驱动程序支持 Kerberos 约束委派。 委派的凭据可以作为 org.ietf.jgss.GSSCredential 对象传入，这些凭据由驱动程序，以建立连接。

```java
Properties driverProperties = new Properties();
GSSCredential impersonatedUserCredential = [userCredential]
driverProperties.setProperty("integratedSecurity", "true");
driverProperties.setProperty("authenticationScheme", "JavaKerberos");
driverProperties.put("gsscredential", impersonatedUserCredential);
Connection conn = DriverManager.getConnection(CONNECTION_URI, driverProperties);
```

## <a name="kerberos-connection-using-principal-names-and-password"></a>Kerberos 连接使用主体名称和密码

从 Microsoft JDBC Driver 6.2 开始，驱动程序可以在连接字符串建立的 Kerberos 传递连接使用主体的名称和密码。

```java
jdbc:sqlserver://servername=server_name;integratedSecurity=true;authenticationScheme=JavaKerberos;userName=user@REALM;password=****
```

Username 属性不需要领域，如果用户属于 default_realm krb5.conf 文件中设置。 当`userName`并`password`设置连同`integratedSecurity=true;`和`authenticationScheme=JavaKerberos;`属性，该连接会建立与用户名的值作为 Kerberos 主体沿与提供的密码。

## <a name="using-kerberos-authentication-from-unix-machines-on-the-same-domain"></a>在同一个域上使用 Kerberos 身份验证从 Unix 计算机

本指南假定一个有效的 Kerberos 设置已存在。 具有使用 Kerberos 身份验证以验证前面提到的则返回 true 的 Windows 计算机上运行下面的代码。 如果成功，则控制台中的代码将打印输出":: KERBEROS 身份验证方案"。 需要外部提供的任何其他运行时标志、 依赖项或驱动程序设置。 可以验证成功的连接的 linux 操作系统上运行相同的代码块。

```java
SQLServerDataSource ds = new SQLServerDataSource();
ds.setServerName("<server>");
ds.setPortNumber(1433); // change if necessary
ds.setIntegratedSecurity(true);
ds.setAuthenticationScheme("JavaKerberos");
ds.setDatabaseName("<database>");

try (Connection c = ds.getConnection(); Statement s = c.createStatement();
        ResultSet rs = s.executeQuery("select auth_scheme from sys.dm_exec_connections where session_id=@@spid")) {
    while (rs.next()) {
        System.out.println("Authentication Scheme: " + rs.getString(1));
    }
}
```

1. 域将客户端计算机加入到与服务器位于同一域中。
2. （可选）设置默认的 Kerberos 票证位置。 这非常方便地通过设置`KRB5CCNAME`环境变量。
3. 获取 Kerberos 票证，通过生成一个新或者将它们放置的现有默认 Kerberos 票证位置中。 若要生成一个票证，只需使用终端并初始化该票证通过`kinit USER@DOMAIN.AD`其中"用户"和"域。AD"分别是主体服务器和域。 例如 `kinit SQL_SERVER_USER03@MICROSOFT.COM`。 在默认票证位置，或者在将生成票证`KRB5CCNAME`路径如果设置。
4. 终端会提示输入密码，输入的密码。
5. 验证是否通过在票证中的凭据`klist`并确认你想要用于身份验证的凭据。
6. 运行上面的示例代码，并确认 Kerberos 身份验证成功。

## <a name="see-also"></a>另请参阅

[通过 JDBC 驱动程序连接到 SQL Server](../../connect/jdbc/connecting-to-sql-server-with-the-jdbc-driver.md)
