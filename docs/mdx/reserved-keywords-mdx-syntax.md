---
title: 保留关键字 （MDX 语法） |Microsoft 文档
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
dev_langs:
- kbMDX
helpviewer_keywords:
- reserved words [MDX]
- Multidimensional Expressions [Analysis Services], reserved words
- MDX [Analysis Services], reserved words
ms.assetid: 0baab5fb-bd04-4ab3-b99a-9f91f3470fbb
caps.latest.revision: 26
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: 93d2de2f24bcdc99ea9739f0fbb87fb520af1111
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="reserved-keywords-mdx-syntax"></a>保留关键字（MDX 语法）
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 保留供其独占使用某些关键字。 有关保留关键字的列表，请参阅[MDX 保留字](../mdx/mdx-reserved-words.md)。  
  
 保留关键字遵循下列指导原则：  
  
-   除了 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 定义的位置外，不能在多维表达式 (MDX) 语句中的任何位置包含保留关键字。  
  
-   数据库中任何对象都不能指定与保留关键字相同的名称。 如果存在这样的名称，必须始终使用分隔标识符来引用这个对象。 虽然此方法允许对象名称与保留关键字相同，但应尽量避免使用关键字来命名对象。  
  
-   请使用能避免使用保留关键字的命名约定。 如果对象名称必须与某个保留关键字类似，则可以删除辅音或元音。  
  
## <a name="see-also"></a>另请参阅  
 [MDX 语法元素&#40;MDX&#41;](../mdx/mdx-syntax-elements-mdx.md)  
  
  
