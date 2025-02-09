---
title: 什么是锁定？ | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- cursors [ADO], locking
- locks [ADO], about locking
ms.assetid: f8989555-28c6-4c17-9bf8-7f44a8a5c407
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 59234b24d7a3e07c1d6500c41dd0ec2a16f95ee1
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "66718376"
---
# <a name="what-is-a-lock"></a>什么是锁定？
锁定是 DBMS 将访问限制为多用户环境中的行的过程。 以独占方式锁定行或列，不允许其他用户访问锁定的数据，直到锁被释放。 这可确保两个用户不能同时更新行中的同一列。  
  
 锁会从资源角度来看很高，应仅在需要时保持数据完整性。 在数据库中的数百或数千个用户可能会尝试访问的记录每秒-如数据库连接到 Internet 的不必要的锁定可快速导致性能降低应用程序中。  
  
 您可以控制如何在数据源和 ADO 游标库管理通过选择适当的锁定选项的并发。  
  
 设置**LockType**打开之前的属性**记录集**指定打开它时，应使用哪种类型的锁定该提供程序。 要返回的锁定中使用的一种开放类型的属性中读取**记录集**对象。  
  
 提供程序可能不支持所有的锁类型。 如果提供程序无法支持请求**LockType**设置，它将替换为另一种类型的锁定。 若要确定在可用的实际锁定功能**记录集**对象，请使用[支持](../../../ado/reference/ado-api/supports-method.md)方法替换**adUpdate**和**adUpdateBatch**.  
  
 **AdLockPessimistic**如果不支持设置[CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md)属性设置为**adUseClient。** 如果设置不支持的值，不会产生错误;最接近的支持**LockType**将改为使用。  
  
 **LockType**属性为读/写时**记录集**打开时为已关闭，并且是只读的。  
  
 本部分包含以下主题。  
  
-   [锁定类型](../../../ado/guide/data/types-of-locks.md)
