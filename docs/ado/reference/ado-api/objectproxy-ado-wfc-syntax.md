---
title: ObjectProxy (ADO-WFC 语法) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
helpviewer_keywords:
- ObjectProxy collection [ADO]
ms.assetid: f68f58bc-ad28-46cc-9fb3-099e1a678397
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: c0b1a69ebbc96197a5bf8fc1cb617e7fde65c731
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "66707176"
---
# <a name="objectproxy-ado---wfc-syntax"></a>ObjectProxy（ADO - WFC 语法）
**ObjectProxy**对象表示的服务器，并返回由**createObject**方法[DataSpace](../../../ado/reference/rds-api/dataspace-object-rds.md)对象。 ObjectProxy 类具有一种方法**调用**，这可以在服务器上调用方法并返回该调用中生成的对象。  
  
 **package com.ms.wfc.data**  
  
## <a name="methods"></a>方法  
  
### <a name="call-method-adowfc-syntax"></a>调用方法 （ADO/WFC 语法）  
 调用由 ObjectProxy 所表示的服务器上的方法。 （可选） 可能会作为对象的数组传递方法自变量。  
  
#### <a name="syntax"></a>语法  
  
```  
public Object ObjectProxy.( String method )  
public Object ObjectProxy.( String method, Object[] args)  
```  
  
#### <a name="returns"></a>返回  
 Object  
 调用该方法生成的对象。  
  
#### <a name="parameters"></a>Parameters  
 *ObjectProxy*  
 **ObjectProxy**表示服务器的对象。  
  
 *方法*  
 一个字符串，包含要在服务器上调用的方法的名称。  
  
 *args*  
 可选。 是在服务器上的方法的参数的对象的数组。 Java 数据类型自动转换为适用于在服务器上使用的数据类型中。
