---
title: "保留字 (Master Data Services) |Microsoft 文档"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- master-data-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- reserved words [Master Data Services]
- Master Data Services, reserved words
ms.assetid: 88afd0d0-4362-4394-8357-4e65388fc0fc
caps.latest.revision: 11
author: sabotta
ms.author: carlasab
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 6815fb319b670226694e2fad4ed5768470d79e5e
ms.contentlocale: zh-cn
ms.lasthandoff: 08/02/2017

---
# <a name="reserved-words-master-data-services"></a>保留字 (Master Data Services)
  在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]中，当您创建模型对象或成员时，不能使用某些字词。 使用这些字词可能导致错误。  
  
> [!NOTE]  
>  您还应限制使用特殊字符（符号、连字符等）。  
  
-   [Models](../master-data-services/reserved-words-master-data-services.md#models)  
  
-   [实体](../master-data-services/reserved-words-master-data-services.md#entities)  
  
-   [显式层次结构](../master-data-services/reserved-words-master-data-services.md#exhierarchies)  
  
-   [属性](../master-data-services/reserved-words-master-data-services.md#attributes)  
  
-   [成员](../master-data-services/reserved-words-master-data-services.md#members)  
  
##  <a name="models"></a> Models  
 如果你创建名称设置为 **Name** 或 **Code**的模型，则不要选择“使用与模型相同的名称创建实体”，因为 **Name** 或 **Code** 不能用于实体名称。   
  
##  <a name="entities"></a> 实体  
 对于实体名称，不能使用 **Name** 或 **Code**。  
  
##  <a name="exhierarchies"></a> 显式层次结构  
 对于显式层次结构名称，不能使用 **Name** 或 **Code**。  
  
##  <a name="attributes"></a> 属性  
  
-   **ID**  
  
-   **Code**  
  
-   **EnterUserName**  
  
-   **LastChgUserName**  
  
-   **Name**  
  
-   **EnterDTM**  
  
-   **EnterUserID**  
  
-   **EnterUserName**  
  
-   **LastChgDTM**  
  
-   **LastChgUserID**  
  
-   **Status_ID**  
  
-   **ValidationStatus_ID**  
  
-   **Version_ID**  
  
##  <a name="members"></a> 成员  
 对于成员，不能对 **Code**属性值使用 **MDMMemberStatus**、 **MDMUnused** 或 **ROOT** 。  
  
## <a name="see-also"></a>另请参阅  
 [Master Data Services 概述 (MDS)](../master-data-services/master-data-services-overview-mds.md)  
  
  