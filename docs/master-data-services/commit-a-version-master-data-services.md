---
title: "提交版本 (Master Data Services) |Microsoft 文档"
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
- committing versions [Master Data Services]
- versions [Master Data Services], committing
ms.assetid: 6b967a39-b333-4b84-9e5f-4fb07e156826
caps.latest.revision: 7
author: sabotta
ms.author: carlasab
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 28fd453f17c08b708b4a49f1f4646eb1be7a51ab
ms.contentlocale: zh-cn
ms.lasthandoff: 08/02/2017

---
# <a name="commit-a-version-master-data-services"></a>提交版本 (Master Data Services)
  在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]中，提交某一模型的版本以便防止对该模型的成员及其属性的更改。 已提交的版本无法取消锁定。  
  
## <a name="prerequisites"></a>先决条件  
 若要执行此过程：  
  
-   您必须有权访问 **“版本管理”** 功能区域。  
  
-   您必须是模型管理员。 有关详细信息，请参阅[管理员 (Master Data Services)](../master-data-services/administrators-master-data-services.md)。  
  
-   版本的状态必须是 **“已锁定”**。 有关详细信息，请参阅[锁定版本 (Master Data Services)](../master-data-services/lock-a-version-master-data-services.md)。  
  
-   所有成员必须已经成功验证。  
  
-   你必须有权访问“版本管理”功能区域。 有关详细信息，请参阅[功能区域权限 (Master Data Services)](../master-data-services/functional-area-permissions-master-data-services.md)。  
  
### <a name="to-commit-a-version"></a>提交版本  
  
1.  在 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]中，单击 **“版本管理”**。  
  
2.  在 **“管理版本”** 页上，从菜单栏中，单击 **“验证版本”**。  
  
3.  在 **“验证版本”** 页上，选择要提交的模型和版本。  
  
4.  单击 **“提交”**。  
  
5.  在确认对话框中，单击 **“确定”**。  
  
## <a name="next-steps"></a>后续步骤  
  
-   [创建版本标志 &#40;Master Data Services &#41;](../master-data-services/create-a-version-flag-master-data-services.md)  
  
-   [向版本 &#40; 分配标志Master Data Services &#41;](../master-data-services/assign-a-flag-to-a-version-master-data-services.md)  
  
-   [复制版本 &#40;Master Data Services &#41;](../master-data-services/copy-a-version-master-data-services.md)  
  
## <a name="see-also"></a>另请参阅  
 [版本 &#40;Master Data Services &#41;](../master-data-services/versions-master-data-services.md)  
  
  