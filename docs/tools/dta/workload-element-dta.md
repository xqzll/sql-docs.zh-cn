---
title: 工作负荷元素 (DTA) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- Workload element
ms.assetid: 68ffd473-6546-4015-98d0-3763165de65c
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 063a15a8278fa10e5c72326c7757ad4946b067f7
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "63033859"
---
# <a name="workload-element-dta"></a>工作负荷元素 (DTA)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  指定要用于优化会话的工作负荷。  
  
## <a name="syntax"></a>语法  
  
```  
  
<DTAInput>  
    <Server>  
...code removed...  
    <Workload>...</Workload>  
```  
  
## <a name="element-characteristics"></a>元素特征  
  
|特征|描述|  
|--------------------|-----------------|  
|**数据类型和长度**|无。|  
|**默认值**|无。|  
|**出现次数**|对于每个 **DTAInput** 元素必须使用一次。|  
  
## <a name="element-relationships"></a>元素关系  
  
|关系|元素|  
|------------------|--------------|  
|**父元素**|[启动并使用数据库引擎优化顾问](../../relational-databases/performance/start-and-use-the-database-engine-tuning-advisor.md)|  
|**子元素**|[文件元素 (DTA)](../../tools/dta/file-element-dta.md)<br /><br /> [工作负荷的数据库元素 (DTA)](../../tools/dta/database-element-for-workload-dta.md)<br /><br /> [EventString 元素 (DTA)](../../tools/dta/eventstring-element-dta.md)|  
  
## <a name="remarks"></a>Remarks  
 工作负荷是对要优化的一个或多个数据库执行的一组 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句。 数据库引擎优化顾问可以将 [!INCLUDE[tsql](../../includes/tsql-md.md)] 脚本、跟踪文件和跟踪表用作工作负荷。  
  
 如果在 XML 输入文件中指定了一个工作负荷，同时又使用 **dta** 工具在命令行中指定了一个工作负荷，则将使用命令行中指定的工作负荷进行优化。 命令行中指定的所有优化选项的优先级均高于 XML 输入文件中指定的优化选项。 唯一的例外情况是：在计算模式下，在 XML 输入文件中输入用户指定的配置。 例如，如果在 XML 输入文件的 **Configuration** 元素中输入了一个配置，同时在优化选项中指定了 **EvaluateConfiguration** 元素，则 XML 输入文件中指定的优化选项将覆盖命令提示行中输入的任何优化选项。  
  
 必须为每个优化会话指定一个工作负荷。  
  
## <a name="example"></a>示例  
 下列代码示例指定 **Workload** 元素的 **MyDatabase.MyDBOwner.TuningTable001** 跟踪表。 使用带有 SQL Server 事件探查器的优化模板创建 **TuningTable001** ，并将该跟踪输出另存为一个表。  
  
```  
<DTAXML ...>  
  <DTAInput>  
    <Server>  
...code removed here...  
    </Server>  
    <Workload>  
      <Database>  
        <Name>MyDatabase</Name>  
        <Schema>  
          <Name>MyDBOwner</Name>  
            <Table>  
              <Name>TuningTable001</Name>  
            </Table>  
        </Schema>  
      </Database>  
    </Workload>  
...code removed here...  
  </DTAInput>  
</DTAXML>  
```  
  
## <a name="see-also"></a>另请参阅  
 [XML 输入文件引用（数据库引擎优化顾问）](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
