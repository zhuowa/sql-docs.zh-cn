---
title: XactAttributeEnum |Microsoft 文档
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
- XactAttributeEnum
helpviewer_keywords:
- XactAttributeEnum enumeration [ADO]
ms.assetid: e7dcecd3-7dc7-445c-b922-f700c3067fbc
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7d2548bdec658e11980189fdfaae1c60594f71d8
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="xactattributeenum"></a>XactAttributeEnum
指定的事务属性[连接](../../../ado/reference/ado-api/connection-object-ado.md)对象。  
  
|常量|“值”|Description|  
|--------------|-----------|-----------------|  
|**adXactAbortRetaining**|262144|通过调用执行保留中止[不](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-ado.md)为自动启动一个新的事务。 并非所有提供程序支持此行为。|  
|**adXactCommitRetaining**|131072|通过调用执行保留提交[CommitTrans](../../../ado/reference/ado-api/begintrans-committrans-and-rollbacktrans-methods-ado.md)为自动启动一个新的事务。 并非所有提供程序支持此行为。|  
  
## <a name="adowfc-equivalent"></a>ADO/WFC 等效项  
 包： **com.ms.wfc.data**  
  
|常量|  
|--------------|  
|AdoEnums.XactAttribute.ABORTRETAINING|  
|AdoEnums.XactAttribute.COMMITRETAINING|  
  
## <a name="applies-to"></a>适用范围  
 [Attributes 属性 (ADO)](../../../ado/reference/ado-api/attributes-property-ado.md)
