---
title: 孙级聚合 |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- grandchild aggregates [ADO]
- data shaping [ADO], grandchild aggregates
ms.assetid: 4162d35f-2ce1-4218-80a5-b6933348837e
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: e81a2d2274d557bf722a3762f7a3e039dfcc5d4d
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "66700832"
---
# <a name="grandchild-aggregates"></a>孙级聚合
创建的形状命令子句中的章节列中可能会获得*章别名*（通常使用 AS 关键字）。 可以识别的形状的任何一章中的任何列**记录集**与标识包含的列的子级的完全限定名称。 例如，如果父一章，chap1，包含子章节，chap2，具有一个 amount 列，amt 设置，则限定的名称将为 chap1.chap2.amt。然后可以作为一个聚合函数 （SUM、 AVG、 最大值、 最小值、 计数、 STDEV、 或任意） 的参数使用的限定的名称。  
  
## <a name="see-also"></a>请参阅  
 [数据整理示例](../../../ado/guide/data/data-shaping-example.md)
