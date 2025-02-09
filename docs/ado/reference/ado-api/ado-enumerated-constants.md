---
title: ADO 枚举常量 |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- enumerated constants [ADO]
ms.assetid: c97ed131-1a93-463c-9e61-22f029b0c474
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 4d9b2e581bfbce225bd34e78761b9e8ade621172
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "66696731"
---
# <a name="ado-enumerated-constants"></a>ADO 枚举常量
若要帮助调试，ADO 枚举列出每个常量的值。 但是，此值是纯粹是参考性的并且可能从一个版本的 ADO 更改为另一个。 你的代码应仅依赖于不是实际值，每个枚举常量的名称。  
  
|||  
|-|-|  
|[ADCPROP_ASYNCTHREADPRIORITY_ENUM](../../../ado/reference/ado-api/adcprop-asyncthreadpriority-enum.md)|Rds**记录集**对象，指定异步检索数据的线程的执行优先级。|  
|[ADCPROP_AUTORECALC_ENUM](../../../ado/reference/ado-api/adcprop-autorecalc-enum.md)|指定何时**MSDataShape**提供程序重新计算聚合和计算列中的分层**记录集**。|  
|[ADCPROP_UPDATECRITERIA_ENUM](../../../ado/reference/ado-api/adcprop-updatecriteria-enum.md)|指定哪些字段可用于在具有的数据源的行中的开放式更新过程中检测冲突**记录集**对象。|  
|[ADCPROP_UPDATERESYNC_ENUM](../../../ado/reference/ado-api/adcprop-updateresync-enum.md)|指定是否**UpdateBatch**方法后跟一个隐式**重新同步**方法操作，如果是，该操作的范围。|  
|[AffectEnum](../../../ado/reference/ado-api/affectenum.md)|指定的操作会影响哪些记录。|  
|[BookmarkEnum](../../../ado/reference/ado-api/bookmarkenum.md)|指定一个书签，用于指示该操作应开始的位置。|  
|[CommandTypeEnum](../../../ado/reference/ado-api/commandtypeenum.md)|指定应如何解释命令参数。|  
|[CompareEnum](../../../ado/reference/ado-api/compareenum.md)|指定由其书签的两条记录的相对位置。|  
|[ConnectModeEnum](../../../ado/reference/ado-api/connectmodeenum.md)|指定用于修改数据中的可用权限**连接**，打开**记录**，或为指定值**模式**属性**记录**并**Stream**对象。|  
|[ConnectOptionEnum](../../../ado/reference/ado-api/connectoptionenum.md)|指定是否**开放**方法**连接**对象应返回后 （同步） 或才能建立连接 （以异步方式）。|  
|[ConnectPromptEnum](../../../ado/reference/ado-api/connectpromptenum.md)|指定是否应显示一个对话框以打开与 ODBC 数据源的连接时提示输入缺少的参数。|  
|[CopyRecordOptionsEnum](../../../ado/reference/ado-api/copyrecordoptionsenum.md)|指定的行为**CopyRecord**方法。|  
|[CursorLocationEnum](../../../ado/reference/ado-api/cursorlocationenum.md)|指定游标引擎的位置。|  
|[CursorOptionEnum](../../../ado/reference/ado-api/cursoroptionenum.md)|指定哪些功能**支持**应测试方法。|  
|[CursorTypeEnum](../../../ado/reference/ado-api/cursortypeenum.md)|指定的游标中使用的类型**记录集**对象。|  
|[DataTypeEnum](../../../ado/reference/ado-api/datatypeenum.md)|指定的数据类型**字段**，**参数**，或**属性**。|  
|[EditModeEnum](../../../ado/reference/ado-api/editmodeenum.md)|指定一条记录的编辑状态。|  
|[ErrorValueEnum](../../../ado/reference/ado-api/errorvalueenum.md)|指定 ADO 运行时错误的类型。|  
|[EventReasonEnum](../../../ado/reference/ado-api/eventreasonenum.md)|指定导致了事件发生的原因。|  
|[EventStatusEnum](../../../ado/reference/ado-api/eventstatusenum.md)|指定的事件执行的当前状态。|  
|[ExecuteOptionEnum](../../../ado/reference/ado-api/executeoptionenum.md)|指定如何提供程序应执行的命令。|  
|[FieldEnum](../../../ado/reference/ado-api/fieldenum.md)|指定特殊的字段中引用**字段**系列**记录**对象。|  
|[FieldAttributeEnum](../../../ado/reference/ado-api/fieldattributeenum.md)|指定的一个或多个特性**字段**对象。|  
|[FieldStatusEnum](../../../ado/reference/ado-api/fieldstatusenum.md)|指定的状态**字段**对象。|  
|[FilterGroupEnum](../../../ado/reference/ado-api/filtergroupenum.md)|指定要从筛选的记录的组**记录集**。|  
|[GetRowsOptionEnum](../../../ado/reference/ado-api/getrowsoptionenum.md)|指定要检索的记录数**记录集**。|  
|[IsolationLevelEnum](../../../ado/reference/ado-api/isolationlevelenum.md)|指定的事务隔离级别**连接**对象。|  
|[LineSeparatorsEnum](../../../ado/reference/ado-api/lineseparatorsenum.md)|指定用作文本中的行分隔符的字符**Stream**对象。|  
|[LockTypeEnum](../../../ado/reference/ado-api/locktypeenum.md)|指定锁，在编辑期间放置在记录的类型。|  
|[MarshalOptionsEnum](../../../ado/reference/ado-api/marshaloptionsenum.md)|指定应返回哪些记录到服务器。|  
|[MoveRecordOptionsEnum](../../../ado/reference/ado-api/moverecordoptionsenum.md)|指定的行为**记录**对象**MoveRecord**方法。|  
|[ObjectStateEnum](../../../ado/reference/ado-api/objectstateenum.md)|指定对象是否为开放还是闭合，连接到数据源，执行命令，或提取数据。|  
|[ParameterAttributesEnum](../../../ado/reference/ado-api/parameterattributesenum.md)|指定的特性**参数**对象。|  
|[ParameterDirectionEnum](../../../ado/reference/ado-api/parameterdirectionenum.md)|指定是否**参数**表示输入的参数、 输出参数，或两者，或如果参数是存储过程的返回值。|  
|[PersistFormatEnum](../../../ado/reference/ado-api/persistformatenum.md)|指定要在其中保存格式**记录集**。|  
|[PositionEnum](../../../ado/reference/ado-api/positionenum.md)|指定在记录指针的当前位置**记录集**。|  
|[PropertyAttributesEnum](../../../ado/reference/ado-api/propertyattributesenum.md)|指定的特性**属性**对象。|  
|[RecordCreateOptionsEnum](../../../ado/reference/ado-api/recordcreateoptionsenum.md)|为指定**记录**对象**打开**方法是否将现有**记录**应为打开，或一个新**记录**应创建。|  
|[RecordOpenOptionsEnum](../../../ado/reference/ado-api/recordopenoptionsenum.md)|指定用于打开选项**记录**。 可以通过使用 OR 运算符组合这些值。|  
|[RecordStatusEnum](../../../ado/reference/ado-api/recordstatusenum.md)|指定的批更新和其他大容量操作的记录的状态。|  
|[RecordTypeEnum](../../../ado/reference/ado-api/recordtypeenum.md)|指定的类型**记录**对象。|  
|[ResyncEnum](../../../ado/reference/ado-api/resyncenum.md)|指定基础值将覆盖通过调用**重新同步**。|  
|[SaveOptionsEnum](../../../ado/reference/ado-api/saveoptionsenum.md)|指定文件是否应创建或覆盖从保存时**Stream**对象。 可以使用 AND 运算符组合这些值。|  
|[SchemaEnum](../../../ado/reference/ado-api/schemaenum.md)|指定的架构的类型**记录集**的**OpenSchema**方法检索。 指定的记录中搜索的方向**记录集**。|  
|[SearchDirectionEnum](../../../ado/reference/ado-api/searchdirectionenum.md)|指定的记录中搜索的方向**记录集**。 指定的类型**Seek**执行。|  
|[SeekEnum](../../../ado/reference/ado-api/seekenum.md)|指定的类型**Seek**执行。 指定用于打开选项**Stream**对象。 可以使用 AND 运算符组合这些值。|  
|[StreamOpenOptionsEnum](../../../ado/reference/ado-api/streamopenoptionsenum.md)|指定用于打开选项**Stream**对象。 可以使用 AND 运算符组合这些值。 指定是否应从读取整个流或下一行**Stream**对象。|  
|[StreamReadEnum](../../../ado/reference/ado-api/streamreadenum.md)|指定是否应从读取整个流或下一行**Stream**对象。 指定存储中的数据类型**Stream**对象。|  
|[StreamTypeEnum](../../../ado/reference/ado-api/streamtypeenum.md)|指定存储中的数据类型**Stream**对象。 指定是否将行分隔符追加到字符串写入到**Stream**对象。|  
|[StreamWriteEnum](../../../ado/reference/ado-api/streamwriteenum.md)|指定是否将行分隔符追加到字符串写入到**Stream**对象。 检索时指定的格式**记录集**作为字符串。|  
|[StringFormatEnum](../../../ado/reference/ado-api/stringformatenum.md)|检索时指定的格式**记录集**作为字符串。 指定的事务特性**连接**对象。|  
|[XactAttributeEnum](../../../ado/reference/ado-api/xactattributeenum.md)|指定的事务特性**连接**对象。|  
  
## <a name="see-also"></a>请参阅  
 [ADO API 参考](../../../ado/reference/ado-api/ado-api-reference.md)   
 [ADO 集合](../../../ado/reference/ado-api/ado-collections.md)   
 [ADO 动态属性](../../../ado/reference/ado-api/ado-dynamic-properties.md)   
 [附录 B：ADO 错误](../../../ado/guide/appendixes/appendix-b-ado-errors.md)   
 [ADO 事件](../../../ado/reference/ado-api/ado-events.md)   
 [ADO 方法](../../../ado/reference/ado-api/ado-methods.md)   
 [ADO 对象模型](../../../ado/reference/ado-api/ado-object-model.md)   
 [ADO 对象和接口](../../../ado/reference/ado-api/ado-objects-and-interfaces.md)   
 [ADO 属性](../../../ado/reference/ado-api/ado-properties.md)
