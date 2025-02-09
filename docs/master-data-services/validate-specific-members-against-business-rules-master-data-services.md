---
title: 针对业务规则验证特定成员 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- applying business rules [Master Data Services]
- business rules [Master Data Services], applying to select members
ms.assetid: 2288ef43-5392-47ea-b651-ec25e5692a14
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 5b0d7a9965d1453441384b09690be7ac97a7f36c
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "65484966"
---
# <a name="validate-specific-members-against-business-rules-master-data-services"></a>针对业务规则验证特定成员 (Master Data Services)

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]中，在您想要根据业务规则更新或验证成员的子级时，可以有选择地应用业务规则。  
  
> [!NOTE]  
>  如果想要将业务规则应用于某个模型版本中的所有成员，请参阅 [针对业务规则验证版本 (Master Data Services)](../master-data-services/validate-a-version-against-business-rules-master-data-services.md)。  
  
## <a name="prerequisites"></a>先决条件  
 若要执行此过程：  
  
-    您必须有权访问“资源管理器”功能区域。  
  
-   对于您要将业务规则应用于的模型对象，您必须至少具有 **“更新”** 权限。  
  
### <a name="to-apply-business-rules-selectively"></a>有选择地应用业务规则  
  
1.  在 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 主页上，从“模型”  下拉列表中，选择某一模型。  
  
2.  从“版本”  下拉列表中，选择某一版本。  
  
3.  单击“资源管理器”选项卡。   
  
4.  从菜单栏中指向 **“实体”** ，然后单击包含要将规则应用于的成员的实体名称。  
  
5.  单击“应用规则”。  业务规则仅应用于在网格中显示的成员。  
  
## <a name="see-also"></a>请参阅  
 [针对业务规则验证版本 (Master Data Services)](../master-data-services/validate-a-version-against-business-rules-master-data-services.md)   
 [业务规则 (Master Data Services)](../master-data-services/business-rules-master-data-services.md)  
  
  
