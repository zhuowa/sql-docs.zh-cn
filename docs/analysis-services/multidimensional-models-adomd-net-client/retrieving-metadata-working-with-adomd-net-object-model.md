---
title: 使用 ADOMD.NET 对象模型 |Microsoft 文档
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: adomd
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 29e59b5811f6c13c7aa222c7d6eba31f9bcd706e
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/10/2018
---
# <a name="retrieving-metadata---working-with-adomdnet-object-model"></a>检索元数据-使用 ADOMD.NET 对象模型
  ADOMD.NET 提供了一个对象模型，用于查看分析数据源中包含的多维数据集和从属对象。 但通过对象模型并不能获得给定分析数据源中的所有元数据。 通过对象模型只可访问那些对客户端应用程序的显示而言最有用的信息，以允许用户以交互方式构造命令。 由于要显示的元数据的复杂性较低，因而 ADOMD.NET 对象模型的使用较为简单。  
  
 在 ADOMD.NET 对象模型中，通过 <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> 对象可访问有关针对分析数据源定义的联机分析处理 (OLAP) 多维数据集和挖掘模型以及相关对象（如维度、命名集和挖掘算法）的信息。  
  
## <a name="retrieving-olap-metadata"></a>检索 OLAP 元数据  
 每个 <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> 对象有一个 <xref:Microsoft.AnalysisServices.AdomdClient.CubeDef> 对象的集合，集合中的对象表示可供用户或应用程序使用的多维数据集。 <xref:Microsoft.AnalysisServices.AdomdClient.CubeDef> 对象公开有关多维数据集以及与多维数据集相关的各种对象（如维度、关键绩效指标、度量值、命名集等）的信息。  
  
 对于旨在支持多个 OLAP 服务器或进行常规元数据显示和访问的客户端应用程序，应尽可能在其中使用 <xref:Microsoft.AnalysisServices.AdomdClient.CubeDef> 对象表示元数据。  
  
> [!NOTE]  
>  对于特定于访问接口的元数据，或用于元数据的详细显示和访问，请使用架构行集检索元数据。 有关详细信息，请参阅 [Working with Schema Rowsets in ADOMD.NET](../../analysis-services/multidimensional-models-adomd-net-client/retrieving-metadata-working-with-schema-rowsets.md)。  
  
 下面的示例使用 <xref:Microsoft.AnalysisServices.AdomdClient.CubeDef> 对象从本地服务器检索可见多维数据集及其维度：  
  
 [!code-cs[Adomd.NetClient#RetrieveCubesAndDimensions](../../analysis-services/multidimensional-models-adomd-net-client/codesnippet/csharp/retrieving-metadata-work_1_1.cs)]  
  
## <a name="retrieving-data-mining-metadata"></a>检索数据挖掘元数据  
 每个 <xref:Microsoft.AnalysisServices.AdomdClient.AdomdConnection> 对象有多个提供数据源的数据挖掘功能相关信息的集合：  
  
-   <xref:Microsoft.AnalysisServices.AdomdClient.MiningModelCollection> 包含数据源中所有挖掘模型的列表。  
  
-   <xref:Microsoft.AnalysisServices.AdomdClient.MiningServiceCollection> 提供有关可用挖掘算法的信息。  
  
-   <xref:Microsoft.AnalysisServices.AdomdClient.MiningStructureCollection> 公开有关服务器上的挖掘结构的信息。  
  
 若要确定对服务器中的挖掘模型的查询方式，请遍历 <xref:Microsoft.AnalysisServices.AdomdServer.MiningModel.Columns%2A> 集合。 每个 <xref:Microsoft.AnalysisServices.AdomdClient.MiningModelColumn> 对象公开以下特征：  
  
-   对象是否为输入列 (<xref:Microsoft.AnalysisServices.AdomdClient.MiningModelColumn.IsInput%2A>)。  
  
-   对象是否为预测列 (<xref:Microsoft.AnalysisServices.AdomdClient.MiningModelColumn.IsPredictable%2A>)。  
  
-   与离散列关联的值 (<xref:Microsoft.AnalysisServices.AdomdClient.MiningModelColumn.Values%2A>)。  
  
-   列中数据的类型 (<xref:Microsoft.AnalysisServices.AdomdClient.MiningModelColumn.Type%2A>)。  
  
## <a name="see-also"></a>另请参阅  
 [从分析数据源检索元数据](../../analysis-services/multidimensional-models-adomd-net-client/retrieving-metadata-from-an-analytical-data-source.md)  
  
  
