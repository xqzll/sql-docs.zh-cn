---
title: 配置 (DTA) 数据库元素 |Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- Database element
ms.assetid: e91ba243-6cc9-457a-8f5a-134f3c71ae69
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 2823734aec3138dd030a0d0399d11d458a970a8a
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "62857418"
---
# <a name="database-element-for-configuration-dta"></a>用于配置的数据库元素 (DTA)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  指定要用数据库引擎优化顾问进行假设配置（由 **配置** 元素指定）评估的数据库。  
  
## <a name="syntax"></a>语法  
  
```  
  
<Server>  
...code removed here...  
    <Database>...</Database>  
```  
  
## <a name="element-characteristics"></a>元素特征  
  
|特征|描述|  
|--------------------|-----------------|  
|**数据类型和长度**|无。|  
|**默认值**|无。|  
|**出现次数**|对于每个 **Server** 元素需要使用一次或多次。|  
  
## <a name="element-relationships"></a>元素关系  
  
|关系|元素|  
|------------------|--------------|  
|**父元素**|[用于配置的服务器元素 (DTA)](../../tools/dta/server-element-for-configuration-dta.md)|  
|**子元素**|[数据库的名称元素 (DTA)](../../tools/dta/name-element-for-database-dta.md)<br /><br /> [数据库的架构元素 (DTA)](../../tools/dta/schema-element-for-database-dta.md)<br /><br /> [建议元素 (DTA)](../../tools/dta/recommendation-element-dta.md)|  
  
## <a name="remarks"></a>Remarks  
 在数据库引擎优化顾问 XML 架构中，此元素的名称为 **DatabaseTypecomplexType** 。 不要将此 **Database** 元素与其根父为 **Server** 元素的元素（出现在 XML 输入文件的顶部）混淆。 有关详细信息，请参阅[服务器的数据库元素 (DTA)](../../tools/dta/database-element-for-server-dta.md)。  
  
## <a name="example"></a>示例  
 有关此**数据库**元素的用法示例，请参阅[使用用户指定配置 (DTA) 的 XML 输入文件示例](../../tools/dta/xml-input-file-sample-with-user-specified-configuration-dta.md)。  
  
## <a name="see-also"></a>另请参阅  
 [XML 输入文件引用（数据库引擎优化顾问）](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
