---
title: 使用数据库镜像终结点证书 (Transact-SQL) | Microsoft Docs
ms.custom: ''
ms.date: 05/17/2016
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- database mirroring [SQL Server], deployment
- certificates [SQL Server], database mirroring
- authentication [SQL Server], database mirroring
- database mirroring [SQL Server], security
ms.assetid: f7c23cc2-48dc-4b78-b441-89ca29a0bd9e
author: MikeRayMSFT
ms.author: mikeray
manager: jroth
ms.openlocfilehash: b03d55317715a554eb7a07161948122e88f896ae
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "66795104"
---
# <a name="use-certificates-for-a-database-mirroring-endpoint-transact-sql"></a>使用数据库镜像端点证书 (Transact-SQL)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  若要在给定的服务器实例上启用数据库镜像的证书验证，系统管理员必须配置每个服务器实例，以在出站连接和进站连接中使用证书。 必须先配置出站连接。  
  
> [!NOTE]  
>  服务器实例上的所有镜像连接都使用单个数据库镜像端点，必须在创建端点时指定服务器实例的身份验证方法。 因此，可以对数据库镜像的每个服务器实例只使用一种验证方式。  
  
## <a name="configuring-outbound-connections"></a>配置出站连接  
 在为数据库镜像配置的每个服务器实例上执行下列步骤：  
  
1.  在 **master** 数据库中，创建数据库主密钥。  
  
2.  在 **master** 数据库中，为服务器实例创建加密证书。  
  
3.  使用服务器实例的证书为该服务器实例创建端点。  
  
4.  将证书备份到文件，并将其安全地复制到其他系统。  
  
 必须对每一个伙伴和见证服务器（如果存在）完成以上步骤。  
  
 有关详细信息，请参阅 [允许数据库镜像终结点使用证书进行出站连接 (Transact-SQL)](../../database-engine/database-mirroring/database-mirroring-use-certificates-for-outbound-connections.md)。  
  
## <a name="configuring-inbound-connections"></a>配置入站连接  
 然后，对为数据库镜像配置的每个伙伴执行这些步骤。 在 **master** 数据库中：  
  
1.  为其他系统创建登录名。  
  
2.  创建一个使用该登录名的用户。  
  
3.  获取其他服务器实例的镜像端点的证书。  
  
4.  将该证书与在步骤 2 中创建的用户相关联。  
  
5.  授予对该镜像端点的登录名的 CONNECT 权限。  
  
 如果存在见证服务器，还必须为见证服务器设置进站连接。 这需要在两个伙伴上为见证服务器设置登录名、用户和证书，反之亦然。  
  
 有关详细信息，请参阅 [允许数据库镜像终结点将证书用于入站连接 (Transact-SQL)](../../database-engine/database-mirroring/database-mirroring-use-certificates-for-inbound-connections.md)。  
  
## <a name="security"></a>Security  
 建议您对数据库镜像连接进行加密，除非您能够保证网络的安全。 有关详细信息，请参阅 [数据库镜像终结点 (SQL Server)](../../database-engine/database-mirroring/the-database-mirroring-endpoint-sql-server.md)。  
  
 将证书复制到其他系统时，请使用安全的复制方法。 必须格外小心地保证所有证书的安全。  
  
## <a name="see-also"></a>另请参阅  
 [创建数据库主密钥](../../relational-databases/security/encryption/create-a-database-master-key.md)   
 [CREATE MASTER KEY (Transact-SQL)](../../t-sql/statements/create-master-key-transact-sql.md)   
 [针对数据库镜像和 AlwaysOn 可用性组的传输安全性 (SQL Server)](../../database-engine/database-mirroring/transport-security-database-mirroring-always-on-availability.md)   
 [SQL Server 数据库引擎和 Azure SQL 数据库的安全中心](../../relational-databases/security/security-center-for-sql-server-database-engine-and-azure-sql-database.md)   
 [数据库镜像终结点 (SQL Server)](../../database-engine/database-mirroring/the-database-mirroring-endpoint-sql-server.md)  
  
  
