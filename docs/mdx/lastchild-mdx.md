---
title: LastChild (MDX) |Microsoft 文档
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- LASTCHILD
dev_langs:
- kbMDX
helpviewer_keywords:
- LastChild function
ms.assetid: 70d09bd0-4330-4be8-8bb5-7a30f44fb4ae
caps.latest.revision: 29
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: 0d15b5e9a661d5d2ecd33117e82c55ee6471d56c
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="lastchild-mdx"></a>LastChild (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  返回指定成员的最后一个子成员。  
  
## <a name="syntax"></a>语法  
  
```  
  
Member_Expression.LastChild   
```  
  
## <a name="arguments"></a>参数  
 *Member_Expression*  
 返回成员的有效多维表达式 (MDX)。  
  
### <a name="example"></a>示例  
 下例将返回 2001 年 9 月的值，它是 2002 会计年度第一个会计季度的最后一个子成员。  
  
```  
SELECT [Date].[Fiscal].[Fiscal Quarter].[Q1 FY 2002].LastChild ON 0  
FROM [Adventure Works]  
```  
  
## <a name="see-also"></a>另请参阅  
 [FirstChild &#40;MDX&#41;](../mdx/firstchild-mdx.md)   
 [MDX 函数引用 & #40;MDX & #41;](../mdx/mdx-function-reference-mdx.md)  
  
  
