---
title: ADO MD 基础知识 |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 02/15/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- ADO MD, fundamentals
ms.assetid: f6a20d9f-c1ab-474c-b9f3-82277e2a126d
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: bbff704e174dd824eca7b1f71c8f9d3fc15def51
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "66704415"
---
# <a name="ado-md-fundamentals"></a>ADO MD 基础知识
Microsoft® ActiveX® 数据对象 （多维） (ADO MD) 可轻松访问多维数据语言 Microsoft Visual Basic®，如从 Microsoft Visual C++®。 ADO MD 扩展了 Microsoft ActiveX® 数据对象 (ADO) 以将对象特定于多维数据，如[CubeDef](../../../ado/reference/ado-md-api/cubedef-object-ado-md.md)并[单元集](../../../ado/reference/ado-md-api/cellset-object-ado-md.md)对象。 使用 ADO MD 可以浏览多维架构、 查询多维数据集，并检索结果。  
  
 例如 ADO，ADO MD 使用基础的 OLE DB 访问接口来访问数据。 若要使用 ADO MD，提供程序必须按照 OLE DB for OLAP 规范的定义是多维数据提供程序 (MDP)。 MDP 提供而不是表格视图的多维视图中的数据，这是表格数据提供程序 (TDP) 如何显示数据。 请参阅的有关特定语法和行为在提供程序支持的详细信息在 OLAP OLE DB 访问接口文档。  
  
 本文档假定 Visual Basic 编程语言的应用知识和 ADO 和 OLAP 的常规知识。 有关详细信息，请参阅[ADO 程序员指南](../../../ado/guide/ado-programmer-s-guide.md)并[OLE DB 的联机分析处理 (OLAP)](https://msdn.microsoft.com/library/windows/desktop/ms717005.aspx)。  
  
 本部分包含以下主题。  
  
-   [多维架构和数据的概述](../../../ado/guide/multidimensional/overview-of-multidimensional-schemas-and-data.md)  
  
-   [使用多维数据](../../../ado/guide/multidimensional/working-with-multidimensional-data.md)  
  
-   [使用 ADO 与 ADO MD](../../../ado/guide/multidimensional/using-ado-with-ado-md.md)  
  
-   [使用 ADO MD 进行编程](../../../ado/guide/multidimensional/programming-with-ado-md.md)  
  
## <a name="see-also"></a>请参阅  
 [ADO MD 对象模型](../../../ado/reference/ado-md-api/ado-md-object-model.md)   
 [ADO 程序员指南](../../../ado/guide/ado-programmer-s-guide.md)   
 [ADO 扩展数据定义语言和安全 (ADOX)](../../../ado/guide/extensions/ado-extensions-for-data-definition-language-and-security-adox.md)   
 [多维架构和数据的概述](../../../ado/guide/multidimensional/overview-of-multidimensional-schemas-and-data.md)   
 [使用 ADO MD 进行编程](../../../ado/guide/multidimensional/programming-with-ado-md.md)   
 [使用 ADO 与 ADO MD](../../../ado/guide/multidimensional/using-ado-with-ado-md.md)   
 [使用多维数据](../../../ado/guide/multidimensional/working-with-multidimensional-data.md)
