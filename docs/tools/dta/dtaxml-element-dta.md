---
title: DTAXML 元素 (DTA) |Microsoft 文档
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.service: ''
ms.component: dta
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- XML
helpviewer_keywords:
- DTAXML element
ms.assetid: 3d9942ed-8a27-40db-a7c9-808984d914a2
caps.latest.revision: 18
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a53c4b2a9a8b55e907a64a5762e1888545479d7e
ms.sourcegitcommit: a85a46312acf8b5a59a8a900310cf088369c4150
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/26/2018
---
# <a name="dtaxml-element-dta"></a>DTAXML 元素 (DTA)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  数据库引擎优化顾问 XML 输入文件或输出文件的根元素 **DTAXML** 包含用于对数据库引擎优化顾问生成的优化输入和优化输出进行说明的所有元素。  
  
## <a name="syntax"></a>语法  
  
```  
  
<DTAXML   
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"   
    xmlns="http://schemas.microsoft.com/sqlserver/2004/07/dta">  
    ...code removed here...  
</DTAXML>  
```  
  
## <a name="element-attributes"></a>元素属性  
  
|Attribute|Description|  
|---------------|-----------------|  
|**xmlns: xsi**|必需的。 标识 XML 架构实例命名空间。 可以使用此命名空间中的属性来引用用于验证数据库引擎优化顾问 XML 文件的架构。<br /><br /> 必需的值：[http://www.w3.org/2001/XMLSchema-instance](http://www.w3.org/2001/XMLSchema-instance)|  
|**xmlns**|必需的。 标识数据库引擎优化顾问命名空间。<br /><br /> 如果在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中使用 XML 编辑器编辑数据库引擎优化顾问 XML 文件，则“F1 帮助”和“动态帮助”将使用此值在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 联机丛书中定位可能的引用主题。<br /><br /> 必需的值：<br /><br /> [Database Engine Tuning Advisor XML Schema](http://go.microsoft.com/fwlink/?LinkId=43100) （数据库引擎优化顾问 XML 架构）命名空间|  
  
## <a name="element-characteristics"></a>元素特征  
  
|特征|Description|  
|--------------------|-----------------|  
|**数据类型和长度**|无。|  
|**默认值**|无。|  
|**出现次数**|每个 DTA XML 文件必须出现一次。|  
  
## <a name="element-relationships"></a>元素关系  
  
|关系|元素|  
|------------------|--------------|  
|**父元素**|InclusionThresholdSetting|  
|**子元素**|[DTAInput 元素 (DTA)](../../tools/dta/dtainput-element-dta.md)<br /><br /> **DTAOutput** 元素（有关信息，请参阅[数据库引擎优化顾问 XML 架构](http://schemas.microsoft.com/sqlserver/)）|  
  
## <a name="remarks"></a>Remarks  
 有关 XML namespaces 的详细信息，请参阅 [MSDN Library 中的](http://go.microsoft.com/fwlink/?LinkId=7341) Namespaces in an XML Document [!INCLUDE[msCoName](../../includes/msconame-md.md)] 。  
  
## <a name="example"></a>示例  
 有关典型 **DTAXML** 元素的示例，请参阅 [XML 输入文件实例 (DTA)](../../tools/dta/xml-input-file-samples-dta.md)。  
  
## <a name="see-also"></a>另请参阅  
 [XML 输入文件引用（数据库引擎优化顾问）](../../tools/dta/xml-input-file-reference-database-engine-tuning-advisor.md)   
 [启动并使用数据库引擎优化顾问](../../relational-databases/performance/start-and-use-the-database-engine-tuning-advisor.md)  
  
  
