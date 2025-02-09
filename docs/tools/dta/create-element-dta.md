---
title: 创建元素 (DTA) |Microsoft Docs
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
- Create element (DTA)
ms.assetid: 9d076c90-f933-45f4-b6d9-447793f6528b
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: c8f645884e28d93bf25032aa6cf89ae3d5dd6774
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "62857194"
---
# <a name="create-element-dta"></a>创建元素 (DTA)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  包含有关用户指定配置中的索引、统计信息或堆结构的信息。  
  
## <a name="syntax"></a>语法  
  
```  
  
<Recommendation>  
    <Create>  
    ...code removed here...  
    </Create>  
</Recommendation>  
```  
  
## <a name="element-characteristics"></a>元素特征  
  
|特征|描述|  
|--------------------|-----------------|  
|**数据类型和长度**|无。|  
|**默认值**|无。|  
|**出现次数**|对每个物理设计结构类型（索引、统计或堆结构）只需使用一次。|  
  
## <a name="element-relationships"></a>元素关系  
  
|关系|元素|  
|------------------|--------------|  
|**父元素**|[建议元素 (DTA)](../../tools/dta/recommendation-element-dta.md)|  
|**子元素**|[索引元素 (DTA)](../../tools/dta/index-element-dta.md)<br /><br /> **Statistics** 元素（有关信息，请参阅 [数据库引擎优化顾问 XML 架构](https://schemas.microsoft.com/sqlserver/) ）<br /><br /> **Heap** 元素（有关信息，请参阅 [数据库引擎优化顾问 XML 架构](https://schemas.microsoft.com/sqlserver/) ）|  
  
## <a name="remarks"></a>Remarks  
 在数据库引擎优化顾问 XML 架构中，此元素的名称为 **CreateTypecomplexType** 。 此元素用于为用户指定的配置创建索引、统计信息和堆结构。 请勿将此 **Create** 元素和其他可用于创建视图 (**CreateViewType**) 或分区 (**CreatePType**) 的其他类型混淆。 有关其他 [Create](https://schemas.microsoft.com/sqlserver/) 元素类型的信息，请参阅 **数据库引擎优化顾问 XML 架构** 。  
  
## <a name="example"></a>示例  
 有关此元素的用法示例，请参阅[用户指定配置 (DTA) 的 XML 输入文件示例](../../tools/dta/xml-input-file-sample-with-user-specified-configuration-dta.md)。  
  
## <a name="see-also"></a>另请参阅  
 [XML 输入文件引用（数据库引擎优化顾问）](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
