---
title: "RangeMax (DMX) |Microsoft 文档"
ms.custom: 
ms.date: 03/02/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- RangeMax
dev_langs:
- DMX
helpviewer_keywords:
- RangeMax function
ms.assetid: 6798d9d7-c3dc-40fb-bd8e-56cb1a6d0e5f
caps.latest.revision: 31
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 8b8cb363e9d5db767ed172206f497ff300bb29a6
ms.contentlocale: zh-cn
ms.lasthandoff: 08/02/2017

---
# <a name="rangemax-dmx"></a>RangeMax (DMX)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  返回为离散化列发现的预测存储桶的高端值。  
  
## <a name="syntax"></a>語法  
  
```  
  
RangeMax(<scalar column reference>)  
```  
  
## <a name="applies-to"></a>适用范围  
 标量列。  
  
## <a name="return-type"></a>返回类型  
 一个标量值。  
  
## <a name="remarks"></a>備註  
 **RangeMax**函数可在[SELECT DISTINCT FROM &#60; 模型 &#62; &#40; DMX &#41;](../dmx/select-distinct-from-model-dmx.md)查询。 与这种类型的查询一起使用时，标量列引用可以包含连续或离散的可预测列或输入列。  
  
 如果用于[SELECT FROM #60; 模型 &#62;预测联接 &#40; DMX &#41;](../dmx/select-from-model-prediction-join-dmx.md)、 **RangeMin**， **RangeMid**，和**RangeMax**函数将返回指定的存储桶的实际边界值。 例如，如果对一个离散化列执行预测，查询将返回该离散化列中存储桶数的预测值。 **RangeMin**， **RangeMid**，和**RangeMax**函数描述预测指定的存储桶。 当**RangeMax**使用 PREDICTION JOIN 语句使用函数、 标量列引用只能包含离散、 可预测列。  
  
## <a name="examples"></a>示例  
 以下示例返回 Decision Tree 挖掘模型中“年收入”连续列的最小值、最大值和平均值。  
  
```  
SELECT DISTINCT   
    RangeMin([Yearly Income]) AS [Bucket Minimum],  
    RangeMid([Yearly Income]) AS [Bucket Average],   
    RangeMax([Yearly Income]) AS [Bucket Maximum]  
FROM [TM Decision Tree]  
```  
  
## <a name="see-also"></a>另請參閱  
 [数据挖掘扩展插件 &#40; DMX &#41;函数参考](../dmx/data-mining-extensions-dmx-function-reference.md)   
 [函数 &#40; DMX &#41;](../dmx/functions-dmx.md)   
 [常规预测函数 &#40; DMX &#41;](../dmx/general-prediction-functions-dmx.md)   
 [RangeMid &#40; DMX &#41;](../dmx/rangemid-dmx.md)   
 [RangeMin &#40; DMX &#41;](../dmx/rangemin-dmx.md)  
  
  
