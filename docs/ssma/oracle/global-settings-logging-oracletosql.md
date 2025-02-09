---
title: 全局设置 （日志记录） (OracleToSQL) |Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 12dbcd77-2b90-4fa1-9cf9-239231ea5773
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.openlocfilehash: abe73fd789a74d358c0573b6c0778a15612532a4
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "63192390"
---
# <a name="global-settings-logging-oracletosql"></a>全局设置（日志记录）(OracleToSQL)
使用**全局设置**对话框可以指定 SSMA 的日志记录设置。 通常情况下，仅当与产品支持人员时，才会更改这些设置。  
  
若要访问此对话框，请在**工具**菜单中，选择**全局设置**，然后单击**日志记录**左窗格底部的按钮。  
  
## <a name="options"></a>选项  
**消息级别**  
下以下选项将可用**消息级别**:  
  
|Option|Description|  
|----------|---------------|  
|**[所有类别]**|用于设置以下选项中的所有日志记录级别。|  
|**Collector**|收集有关源架构的元数据并将其保存到项目。|  
|**Converter**|转换为结构的源数据库对象，如表和存储的过程对应[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]结构。|  
|**数据迁移器**|将数据迁移从源数据库到[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。|  
|**格式化程序**|为生成脚本的转换器的子组件[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]架构。|  
|**图形用户界面**|使用 SSMA 工具时出现的消息。|  
|**链接器**|解析的 SQL 标识符，并提供对其他组件的信息。|  
|**其他**|不在任何其他类别中的所有消息。|  
|**Parser**|分析源架构。|  
|**同步器**|加载源数据库对象到[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]。|  
|**TreeConverter**|将转换到的源元数据中的对象[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]元数据。|  
|**测试人员**|使用 SSMA 测试人员时，将显示的消息。|  
  
每个选项下**消息级别**，为 SSMA 配置以下日志记录级别之一：  
  
|||  
|-|-|  
|**致命错误**|仅错误消息写入日志。|  
|**错误**|在日志中写入错误消息和错误消息。|  
|**警告**|警告、 错误和错误消息写入日志。|  
|**Info**|信息性、 警告、 错误消息和错误消息写入日志。|  
|**调试**|将所有消息，包括调试消息，向日志都写入。|  
  
**日志文件路径**  
文件路径和名称的 SSMA 日志文件。 若要指定其他名称，单击当前路径，然后单击浏览 ( **...** ) 按钮。  
  
**日志文件大小**  
日志文件以 kb 为单位的最大大小。 最小大小为 10 KB。 默认大小为 10240 KB。  
  
**日志文件的总数**  
当一个日志已满时，SSMA 将重命名日志文件，并启动一个新。 通过使用此设置，指定日志文件，使最大数目。 最小值为 2。  
  
