---
title: 如何：查看数据差异 | Microsoft Docs
ms.custom:
- SSDT
ms.date: 02/09/2017
ms.prod: sql
ms.technology: ssdt
ms.reviewer: ''
ms.topic: conceptual
f1_keywords:
- sql.data.tools.datacompare.f1
ms.assetid: f88d3350-2eaf-44cc-96a8-84008b6cd071
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 935a2671c2496cb6cbb996d25cddc123bc4d782d
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "65095925"
---
# <a name="how-to-view-data-differences"></a>如何：查看数据差异
在比较两个数据库中的数据后，将显示比较的每个数据库对象  及其状态。 还可以查看每个对象中的记录的结果（按状态分组）。  
  
查看差异后，可以针对部分或全部不同的、缺少的或新的对象或记录更新目标  以便与源  匹配。  
  
### <a name="to-view-data-differences"></a>查看数据差异  
  
1.  比较源数据库和目标数据库中的数据。  
  
2.  （可选）执行下列一种或两种操作：  
  
    -   默认情况下，将显示所有对象的结果，不管其状态如何。 若要仅显示具有特定状态的那些对象，请单击“筛选器”  列表中的选项。  
  
    -   若要查看某个特定对象内的记录的结果，请在主结果窗格中单击该对象，再单击“记录视图”窗格中的某个选项卡。 每个选项卡都将显示该对象内具有特定状态的所有记录：不同、只在源中、只在目标中以及相同。 数据按记录和列显示。  
  
## <a name="see-also"></a>另请参阅  
[如何：使用架构比较来比较不同数据库定义](../ssdt/how-to-use-schema-compare-to-compare-different-database-definitions.md)  
  
