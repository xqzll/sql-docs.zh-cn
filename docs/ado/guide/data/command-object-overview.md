---
title: 命令对象概述 |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- command object [ADO]
ms.assetid: e84a14b1-3c2a-4f7d-a966-9e08a93948df
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: d9dd8315945d07aa4c6e99dc8661c26c7d92fb95
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "66718457"
---
# <a name="command-object-overview"></a>命令对象概述
与**命令**对象，您可以执行以下操作：  
  
-   通过使用定义的命令 （例如，SQL 语句或存储的过程） 可执行文件的文本**CommandText**属性。  
  
-   使用定义参数化的查询或存储的过程参数**参数**对象和**参数**集合。  
  
-   执行命令并返回**记录集**对象，如果需要，通过使用**Execute**方法。  
  
-   使用指定的命令的类型**CommandType**属性，然后执行以优化性能。  
  
-   使用指定的命令文本有关的特定信息**方言**的属性**命令**对象。  
  
-   提供程序是否使用保存之前执行该命令的准备就绪 （或已编译） 版本控制**已准备**属性。  
  
-   设置提供程序将等待命令执行使用的秒数**CommandTimeout**属性。  
  
-   将与打开的连接相关联**命令**对象通过设置其**ActiveConnection**属性。  
  
-   设置**名称**属性来标识**命令**作为关联的方法的对象**连接**对象。  
  
-   传递**命令**对象传递给**源**属性**记录集**为获得数据。  
  
-   传递**Stream**对象，它包含到提供程序支持它的命令 （例如，XML 命令）。
