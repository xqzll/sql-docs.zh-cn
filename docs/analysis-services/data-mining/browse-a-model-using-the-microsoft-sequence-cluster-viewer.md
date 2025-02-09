---
title: 使用 Microsoft 序列分类查看器浏览模型 |Microsoft Docs
ms.date: 05/01/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: data-mining
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: cce1203b73f5a1685634c4b50f6e5941bed3eb98
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/15/2019
ms.locfileid: "62671315"
---
# <a name="browse-a-model-using-the-microsoft-sequence-cluster-viewer"></a>使用 Microsoft 序列分类查看器浏览模型
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 中的 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 序列分类查看器显示使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 顺序分析和聚类分析算法生成的挖掘模型。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 顺序分析和聚类分析算法是用于探析特定数据的顺序分析算法，这些数据所包含的事件可通过以下路径（又称“序列  ”）联系起来。 有关此算法的详细信息，请参阅 [Microsoft 顺序分析和聚类分析算法](../../analysis-services/data-mining/microsoft-sequence-clustering-algorithm.md)。  
  
> [!NOTE]  
>  若要查看有关模型中使用的公式以及所发现的模式的详细信息，请使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 一般内容树查看器。 有关详细信息，请参阅[使用 Microsoft 一般内容树查看器浏览模型](../../analysis-services/data-mining/browse-a-model-using-the-microsoft-generic-content-tree-viewer.md)或 [Microsoft 一般内容树查看器（数据挖掘）](http://msdn.microsoft.com/library/751b4393-f6fd-48c1-bcef-bdca589ce34c)。  
  
> [!NOTE]  
>  [!INCLUDE[msCoName](../../includes/msconame-md.md)] 序列分类查看器提供了与 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 分类查看器类似的功能和选项。 有关详细信息，请参阅 [使用 Microsoft 分类查看器浏览模型](../../analysis-services/data-mining/browse-a-model-using-the-microsoft-cluster-viewer.md)。  
  
##  <a name="BKMK_ViewerTabs"></a> 查看器的选项卡  
 在 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]中浏览挖掘模型时，该模型会显示在其相应查看器的数据挖掘设计器的 **“挖掘模型查看器”** 选项卡上。 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 序列分类查看器提供了以下选项卡，用于浏览顺序分析和聚类分析挖掘模型：  
  
-   [分类关系图](#BKMK_Diagram)  
  
-   [分类剖面图](#BKMK_Profile)  
  
-   [分类特征](#BKMK_Characteristics)  
  
-   [分类对比](#BKMK_Discrimination)  
  
-   [分类转换](#BKMK_Transitions)  
  
###  <a name="BKMK_Diagram"></a> 分类关系图  
 **序列分类查看器的** “分类关系图” [!INCLUDE[msCoName](../../includes/msconame-md.md)] 选项卡可显示挖掘模型中的全部分类。 两个分类之间连线的明暗度表示分类的相似程度。 如果明暗度较浅或无明暗度，则表示分类的相似程度较低。 连线的颜色越深，链接的相似性越强。 通过调整分类右侧的滑块，可以调整查看器显示的连线数。 降低滑块将只显示最强链接。  
  
 默认情况下，明暗度代表分类的总体。 通过使用“明暗度****变量”  和“状态”  选项，可以选择明暗度代表的属性和状态对。 明暗度越深，特定状态所对应的属性分布范围就越大。 明暗度越浅，分布范围就越小。  
  
 若要重命名某个群集，请右键单击其节点并选择“重命名群集”  。 新名称会在服务器中永久保留。  
  
 若要将关系图的可见部分复制到剪贴板，请单击 **“复制图形视图”** 。 若要复制完整的关系图，请单击 **“复制整个图形”** 。 使用 **“放大”** 和 **“缩小”** 可以放大或缩小关系图，使用 **“缩放关系图以适应窗口”** 可以适应屏幕大小。  
  
 [返回页首](#BKMK_ViewerTabs)  
  
###  <a name="BKMK_Profile"></a> 分类剖面图  
 **“分类剖面图”** 选项卡可以提供模型中的算法创建的分类的总体视图。 网格中 **“总体”** 列后的每一列都代表模型发现的分类。 \<属性 > s 行代表不同的群集中存在的数据序列和\<属性 > 行进行了说明分类包含的所有项及其总体分布。  
  
 通过“直方图条”  选项，可以控制直方图中可见的条数。 如果存在的图条数多于您选择显示的图条数，则会保留重要性最高的那些图条，其余图条则组合到一个灰色的存储桶内。  
  
 您可以更改分类的默认名称，使名称更具描述性。 右键单击群集的列标题，再选择  “重命名群集”，即可重命名群集。 可以选中 **“隐藏列”** 隐藏分类，也可以通过在查看器中拖动列来将其重新排序。  
  
 若要打开一个窗口，以便为群集提供更大、更详细的视图，请双击“状态”  列中的任一单元格，或双击查看器中的任一直方图。  
  
 [返回页首](#BKMK_ViewerTabs)  
  
###  <a name="BKMK_Characteristics"></a> 分类特征  
 若要使用“分类特征”  选项卡，请从“分类”  列表中选择一个分类。 选择分类后，可以检查特定分类的组成特征。 分类包含的属性列在 **“变量”** 列中，所列属性的状态列在 **“值”** 列中。 属性状态将按重要性顺序列出，重要性由这些状态会出现在分类中的概率表示。 概率显示在 **“概率”** 列中。  
  
 [返回页首](#BKMK_ViewerTabs)  
  
###  <a name="BKMK_Discrimination"></a> 分类对比  
 可以使用 **“分类对比”** 选项卡来比较两个分类的属性，以确定序列中的项所倾向的分类。 使用 **“分类 1”** 和 **“分类 2”** 列表选择要比较的分类。 查看器将确定分类之间最为重要的一些差异，并按重要性顺序显示与这些差异关联的属性状态。 属性右侧的条表示属性状态所倾向的分类，条的大小则表示属性状态倾向于相应分类的程度。  
  
 [返回页首](#BKMK_ViewerTabs)  
  
###  <a name="BKMK_Transitions"></a> 分类转换  
 在 **“分类转换”** 选项卡中选中一个分类后，可在选中的分类中浏览序列状态之间的转换。 查看器中的每个节点代表序列列的一个状态。 箭头代表两个状态之间的转换以及与该转换相关联的概率。 如果转换返回到初始节点，那么会有一个箭头指向该初始节点。  
  
 以圆点为起点的箭头代表序列从此节点处开始的概率。 末端指向空值的箭头代表序列至此节点处结束的概率。  
  
 可以使用位于选项卡左侧的滑块来筛选节点边缘。  
  
 [返回页首](#BKMK_ViewerTabs)  
  
## <a name="see-also"></a>请参阅  
 [挖掘模型查看器任务和操作指南](../../analysis-services/data-mining/mining-model-viewer-tasks-and-how-tos.md)   
 [挖掘模型查看器任务和操作指南](../../analysis-services/data-mining/mining-model-viewer-tasks-and-how-tos.md)   
 [Microsoft 顺序分析和聚类分析算法](../../analysis-services/data-mining/microsoft-sequence-clustering-algorithm.md)   
 [数据挖掘工具](../../analysis-services/data-mining/data-mining-tools.md)   
 [数据挖掘模型查看器](../../analysis-services/data-mining/data-mining-model-viewers.md)   
 [使用 Microsoft 分类查看器浏览模型](../../analysis-services/data-mining/browse-a-model-using-the-microsoft-cluster-viewer.md)  
  
  
