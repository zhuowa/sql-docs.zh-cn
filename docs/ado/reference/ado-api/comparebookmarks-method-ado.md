---
title: CompareBookmarks 方法 (ADO) |Microsoft 文档
ms.prod: sql
ms.prod_service: connectivity
ms.component: ado
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- CompareBookmarks
- Recordset20::CompareBookmarks
- Recordset20::raw_CompareBookmarks
helpviewer_keywords:
- CompareBookmarks method [ADO]
ms.assetid: d0b64286-2cc4-4a22-8f1d-9aefeebbcbc6
caps.latest.revision: 14
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f17b1bbb0793e06a5ecbbec393fd87ebcdbc311e
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="comparebookmarks-method-ado"></a>CompareBookmarks 方法 (ADO)
比较两个的书签，并返回对其相对值的指示。  
  
## <a name="syntax"></a>语法  
  
```  
  
result = recordset.CompareBookmarks(Bookmark1, Bookmark2)  
```  
  
## <a name="return-value"></a>返回值  
 返回[CompareEnum](../../../ado/reference/ado-api/compareenum.md)值，该值指示由其书签的两条记录的相对的行位置。  
  
#### <a name="parameters"></a>Parameters  
 *Bookmark1*  
 第一个行的书签。  
  
 *Bookmark2*  
 第二行的书签。  
  
## <a name="remarks"></a>注释  
 书签必须应用到同一个[记录集](../../../ado/reference/ado-api/recordset-object-ado.md)对象，或**记录集**对象并将其[克隆](../../../ado/reference/ado-api/clone-method-ado.md)。 不能可靠地比较通过不同的书签**记录集**对象，即使它们已创建从相同的源或命令。 也可以比较书签**记录集**其基础提供程序不支持比较的对象。  
  
 书签唯一标识中的行**记录集**对象。 使用[书签](../../../ado/reference/ado-api/bookmark-property-ado.md)要获取其书签的当前行的属性。  
  
 书签的数据类型是特定于每个提供程序，因为 ADO 公开其作为**Variant**。 例如，SQL Server，书签将变为类型 DBTYPE_R8 的 (**Double**)。 ADO 将公开此类型作为**Variant**的子类型与**Double**。  
  
 在比较书签时，ADO 不会尝试强制任何类型。 将值只需传递给提供程序进行比较。 如果书签传递给**CompareBookmarks**方法存储在不同类型的变量，它可以生成以下类型不匹配错误:"自变量的类型不正确，超出可接受的范围，或正在发生冲突与每个其他。  
  
 无效或格式不正确的书签会导致错误。  
  
## <a name="applies-to"></a>适用范围  
 [记录集对象 (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>另请参阅  
 [CompareBookmarks 方法示例 (VB)](../../../ado/reference/ado-api/comparebookmarks-method-example-vb.md)   
 [CompareBookmarks 方法示例 （VC + +）](../../../ado/reference/ado-api/comparebookmarks-method-example-vc.md)   
 [Bookmark 属性 (ADO)](../../../ado/reference/ado-api/bookmark-property-ado.md)
