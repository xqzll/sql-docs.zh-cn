---
title: 验证数据 (MDS Add-in for Excel) | Microsoft Docs
ms.custom: microsoft-excel-add-in
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: mds
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: 71eda98f-01a4-4fff-8246-be3133782523
author: lrtoyou1223
ms.author: lle
manager: craigg
ms.openlocfilehash: 67a91feab955f0e62e1f6837a00030833d581b19
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "65484557"
---
# <a name="validating-data-mds-add-in-for-excel"></a>验证数据（用于 Excel 的 MDS 外接程序）

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

  在 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]中，当你发布数据时，将进行两种类型的验证：  
  
-   任何已定义的业务规则将应用于数据。  
  
-   根据允许的属性值（例如，字符数或数据类型）对数据进行检查。  
  
 在每种情况下，有效数据都发布到 MDS 存储库中。 无效数据将被突出显示，并且错误的详细信息可能会显示在状态列中。  
  
## <a name="when-validation-occurs"></a>在发生验证时  
 在 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)] [!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]中，在发布新数据或更改的数据时，或者在手动应用业务规则时，将发生验证。  
  
 在业务规则失败时，数据仍发布到 MDS 存储库中。 在输入验证失败时，数据将不会发布到该存储库。  
  
## <a name="validation-statuses"></a>验证状态  
 在 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]中，以下验证状态是可能的。  
  
 有关其他状态的信息，请参阅[验证状态 (Master Data Services)](../../master-data-services/validation-statuses-master-data-services.md)  
  
|“登录属性”|Description|  
|------------|-----------------|  
|验证失败|行中的一个或多个值未通过针对 MDS 管理员定义的业务规则的验证。|  
|验证成功|行中的所有值都已根据业务规则通过了验证。|  
  
## <a name="input-statuses"></a>输入状态  
 在 [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)]中，以下输入状态是可能的  
  
|“登录属性”|Description|  
|------------|-----------------|  
|错误|行中的一个或多个值不符合长度或数据类型之类的系统要求。 值在 MDS 存储库中不更新。|  
|新行|该行中的值尚未发布到 MDS 存储库中。|  
|只读|登录用户对该行中的一个或多个值具有只读权限，并且这些值不能更新。|  
|不变|行中没有任何值在工作表中进行了更改。 这并不意味着存储库中的值已更改；若要获取工作表中的最新数据，请在 **“连接并加载”** 组中单击 **“加载或刷新”** 。<br /><br /> 这是每一行的默认设置。|  
  
## <a name="related-tasks"></a>Related Tasks  
  
|任务说明|主题|  
|----------------------|-----------|  
|确定哪些值未通过定义的业务规则。|[应用业务规则（用于 Excel 的 MDS 外接程序）](../../master-data-services/microsoft-excel-add-in/apply-business-rules-mds-add-in-for-excel.md)|  
|为了帮助纠正验证错误，请查看某一成员发生的所有事务。|[查看成员的所有批注或事务（用于 Excel 的 MDS 外接程序）](../../master-data-services/microsoft-excel-add-in/view-all-annotations-or-transactions-for-a-member-mds-add-in-for-excel.md)|  
  
## <a name="related-content"></a>相关内容  
  
-   [概述：从 Excel 导入数据&#40;MDS add-in for Excel&#41;](../../master-data-services/microsoft-excel-add-in/overview-importing-data-from-excel-mds-add-in-for-excel.md)  
  
  
