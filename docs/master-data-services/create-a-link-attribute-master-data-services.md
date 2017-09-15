---
title: "创建链接属性 (Master Data Services) |Microsoft 文档"
ms.custom:
- SQL2016_New_Updated
ms.date: 03/15/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- master-data-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- attributes [Master Data Services], creating link attributes
- creating link attributes [Master Data Services]
ms.assetid: e6658e9c-5b08-4b8d-b556-17ec2dd041d2
caps.latest.revision: 9
author: sabotta
ms.author: carlasab
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 1b5c1a0c51283b981daf0df5e65740892fb830c2
ms.contentlocale: zh-cn
ms.lasthandoff: 08/02/2017

---
# <a name="create-a-link-attribute-master-data-services"></a>创建链接属性 (Master Data Services)
  在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]中，在您希望用户输入超链接作为属性值（例如 http://www.contoso.com）时创建链接属性。  
  
> [!NOTE]  
>  当用户为链接属性输入值时，该字符串必须以 **http://** 开头，否则将显示错误。  
  
## <a name="prerequisites"></a>先决条件  
 若要执行此过程：  
  
-   您必须有权访问 **“系统管理”** 功能区域。  
  
-   您必须是模型管理员。 有关详细信息，请参阅[管理员 (Master Data Services)](../master-data-services/administrators-master-data-services.md)。  
  
-   要为其创建属性的实体必须存在。 有关详细信息，请参阅[创建实体 (Master Data Services)](../master-data-services/create-an-entity-master-data-services.md)。  
  
## <a name="attribute-information"></a>属性信息  
 对于创建的每个属性，系统都会在网格中添加一行（其中包含七列）。 下表对这些列进行了说明。  
  
|列|Description|  
|------------|-----------------|  
|状态|属性状态。<br /><br /> 当你单击保存![更新状态的图标](../master-data-services/media/mds-statusicon-updating.png "更新状态的图标")图像，表示属性正在更新。<br /><br /> 如果在创建或编辑属性时出错![错误状态的图标](../master-data-services/media/mds-statusicon-error.png "错误状态的图标")图像显示。<br /><br /> 否则，状态为正常和![正常状态的图标](../master-data-services/media/mds-statusicon-ok.png "正常状态的图标")图像显示。|  
|名称|属性名称。|  
|显示名称|属性显示名称。|  
|Description|属性说明。|  
|显示像素宽度|属性宽度。|  
|类型和属性|属性的类型和数据类型信息。|  
|启用更改跟踪|指定是否启用该属性以进行更改跟踪，并在括号中显示组号。|  
  
 单击属性后可看到以下信息。  
  
-   **创建者**：创建属性的用户的用户名。  
  
-   **创建时间**：创建属性的日期和时间。  
  
-   **更新者**：上次更新属性的用户的用户名。  
  
-   **创建时间**：上次更新属性的日期和时间。  
  
### <a name="to-create-a-link-attribute"></a>创建链接属性  
  
1.  在 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]中，单击 **“系统管理”**。  
  
2.  在“管理模型”  页上，从网格中选择一个模型，然后单击“实体” 。  
  
3.  在“管理实体”  页上，选择要为其创建属性的实体所在的行。  
  
4.  单击 **“属性”**。  
  
5.  在“管理属性”  页上，执行下列操作之一，然后单击“添加” 。  
  
    -   如果属性是针对叶成员，则从“成员类型”  列表框选择“叶”  。  
  
    -   如果属性是针对合并成员，则从“成员类型”  列表框中选择“合并”  。  
  
    -   如果属性是针对集合，则从“成员类型”  列表框中选择“集合”  。  
  
6.  在 **“名称”** 框中，键入属性的名称。 有关不可用作属性名称的单词列表，请参阅[保留字 (Master Data Services)](../master-data-services/reserved-words-master-data-services.md)。  
  
7.  （可选）键入显示名称，并在“说明”  框中键入属性的说明。  
  
8.  在 **“显示像素宽度”** 框中，键入要在 **“资源管理器”** 网格中显示的属性列的宽度。  
  
9. 从“属性类型”列表中，选择“自由格式”。  
  
10. 从 **“数据类型”** 列表中，选择 **“链接”**。  
  
11. 在 **“长度”** 框中，键入允许的最大字符数。  
  
12. 根据需要，选择 **“启用更改跟踪”** 可以跟踪对属性组的更改。 有关详细信息，请参阅[向更改跟踪组添加属性 (Master Data Services)](../master-data-services/add-attributes-to-a-change-tracking-group-master-data-services.md)。  
  
13. 单击 **“保存”**。  
  
## <a name="see-also"></a>另请参阅  
 [属性 (Master Data Services)](../master-data-services/attributes-master-data-services.md)   
 [更改的属性名称和数据类型 &#40;Master Data Services &#41;](../master-data-services/change-an-attribute-name-and-data-type-master-data-services.md)   
 [创建基于域的属性 &#40;Master Data Services &#41;](../master-data-services/create-a-domain-based-attribute-master-data-services.md)   
 [创建文件属性 (Master Data Services)](../master-data-services/create-a-file-attribute-master-data-services.md)  
  
  