---
title: PersistFormatEnum |Microsoft 文档
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
- PersistFormatEnum
helpviewer_keywords:
- PersistFormatEnum enumeration [ADO]
ms.assetid: ebe1a2ab-e9f1-43a2-8f94-b190c9613d70
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 141590f2755323422f44aacb4617905191d3a154
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="persistformatenum"></a>PersistFormatEnum
指定要在其中保存格式[记录集](../../../ado/reference/ado-api/recordset-object-ado.md)。  
  
|常量|“值”|Description|  
|--------------|-----------|-----------------|  
|**adPersistADTG**|0|指示 Microsoft 高级数据表图 (ADTG) 格式。|  
|**adPersistADO**|1|表示将使用 ADO 自己可扩展标记语言 (XML) 格式。 此值是 xml 格式持久化记录相同，包括有关向后兼容性。|  
|**adPersistXML**|1|指示可扩展标记语言 (XML) 格式。|  
|**adPersistProviderSpecific**|2|指示提供程序将保持**记录集**使用其自己的格式。|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC 等效项  
 包： **com.ms.wfc.data**  
  
|常量|  
|--------------|  
|AdoEnums.PersistFormat.ADTG|  
|AdoEnums.PersistFormat.XML|  
  
## <a name="applies-to"></a>适用范围  
 [Save 方法](../../../ado/reference/ado-api/save-method.md)
