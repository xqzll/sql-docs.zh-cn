---
title: 可用性组的“输入密码”页（添加副本向导）
description: 关于在 SQL Server Management Studio 的“添加副本”向导中的“输入密码”页上找到的属性的说明。
ms.custom: seodec18
ms.date: 05/17/2016
ms.prod: sql
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql13.swb.addreplicawizard.enterpasswords.f1
ms.assetid: e69207a0-c5c4-44e4-ae9a-4afbb67251d1
author: MashaMSFT
ms.author: mathoma
manager: jroth
ms.openlocfilehash: 59a4e60fa68223939a595be96c9adb872e01202a
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "66769064"
---
# <a name="enter-passwords-page-add-replica-wizard-for-always-on-availability-groups"></a>AlwaysOn 可用性组的“输入密码”页（添加副本向导）
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  本帮助主题介绍了“输入密码”  页中的选项。 本主题适用于 [!INCLUDE[ssAoAddRepWiz](../../../includes/ssaoaddrepwiz-md.md)] 的 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]。  
  
 如果你在“指定副本”  页中选择的副本包含具有数据库主密钥的数据库，则会出现“输入密码”页。  
  
## <a name="enter-passwords-options"></a>输入密码选项  
 **“此 SQL Server 实例上的用户数据库”** 网格列出每个本地用户数据库。 这些列如下所示：  
  
 **名称**  
 显示本地用户数据库的名称。  
  
 **大小**  
 显示数据库大小（如果在该向导中提供）。  
  
 **“状态”**  
 指示具有数据库主密钥的数据库“需要密码”  。 在“密码”  列中输入数据库主密钥的密码后，请单击“刷新”  。 如果你正确输入了密码，  “状态”列指示“输入的密码”  。  
  
 如果数据库没有数据库主密钥，  “状态”列指示  “不需要密码”。  
  
 **密码**  
 如果“状态”  列指示“需要密码”  ，则输入数据库主密钥的密码。  
  
 **“刷新”**  
 单击以刷新该网格。 输入所需的密码后，该操作非常有用。  
  
## <a name="related-tasks"></a>Related Tasks  
  
-   [使用“将副本添加到可用性组向导”(SQL Server Management Studio)](../../../database-engine/availability-groups/windows/use-the-add-replica-to-availability-group-wizard-sql-server-management-studio.md)  
  
## <a name="see-also"></a>另请参阅  
 [针对 AlwaysOn 可用性组的先决条件、限制和建议 (SQL Server)](../../../database-engine/availability-groups/windows/prereqs-restrictions-recommendations-always-on-availability.md)  
  
  
