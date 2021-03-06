---
title: AffectEnum |Microsoft 文档
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
- AffectEnum
helpviewer_keywords:
- AffectEnum enumeration [ADO]
ms.assetid: 1ab921a0-6c57-43b4-9291-701b2599f3e8
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2c0efaeacb53492eab6485ca9d89629f27e4dfcd
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="affectenum"></a>AffectEnum
指定的操作会影响哪些记录。  
  
|常量|“值”|Description|  
|--------------|-----------|-----------------|  
|**adAffectAll**|3|如果没有[筛选器](../../../ado/reference/ado-api/filter-property.md)应用于**记录集**，影响所有记录。<br /><br /> 如果**筛选器**属性设置为字符串条件 (如"作者 = 'Smith'")，则该操作会影响当前章节中的可见记录。<br /><br /> 如果**筛选器**属性设置为属于[FilterGroupEnum](../../../ado/reference/ado-api/filtergroupenum.md)或数组的书签，则该操作将影响的所有行**记录集**。 **注意：****adAffectAll**在 Visual Basic 对象浏览器中隐藏。|  
|**adAffectAllChapters**|4|影响的所有同级章节中的所有记录**记录集**，包括那些通过任何不可见**筛选器**，当前应用。|  
|**adAffectCurrent**|1|影响仅当前记录。|  
|**adAffectGroup**|2|影响满足当前的记录[筛选器](../../../ado/reference/ado-api/filter-property.md)属性设置。 必须设置**筛选器**属性**FilterGroupEnum**值或数组的**书签**要使用此选项。|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC 等效项  
 包： **com.ms.wfc.data**  
  
|常量|  
|--------------|  
|AdoEnums.Affect.ALL|  
|AdoEnums.Affect.ALLCHAPTERS|  
|AdoEnums.Affect.CURRENT|  
|AdoEnums.Affect.GROUP|  
  
## <a name="applies-to"></a>适用范围  
  
|||  
|-|-|  
|[CancelBatch 方法 (ADO)](../../../ado/reference/ado-api/cancelbatch-method-ado.md)|[Delete 方法（ADO 记录集）](../../../ado/reference/ado-api/delete-method-ado-recordset.md)|  
|[重新同步方法](../../../ado/reference/ado-api/resync-method.md)|[UpdateBatch 方法](../../../ado/reference/ado-api/updatebatch-method.md)|
