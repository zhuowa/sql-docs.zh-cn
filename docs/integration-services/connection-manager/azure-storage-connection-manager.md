---
title: "Azure 存储连接管理器 |Microsoft 文档"
ms.custom:
- SQL2016_New_Updated
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.designer.afpstorageconn.f1
- sql14.dts.designer.afpstorageconn.f1
ms.assetid: 68bd1d04-d20f-4357-a34e-7c9c76457062
caps.latest.revision: 13
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 848b0f0e3e639d31fa739e8d744fc4b80839a5fd
ms.contentlocale: zh-cn
ms.lasthandoff: 08/03/2017

---
# <a name="azure-storage-connection-manager"></a>Azure 存储连接管理器
  **Azure 存储连接管理器** 使一个 SSIS 包可使用你指定的属性值连接到 Azure 存储帐户：存储帐户名称和帐户密钥。  
   
 **Azure 存储空间连接管理器**的组成部分[用于 Azure 的 SQL Server Integration Services (SSIS) 功能包](../../integration-services/azure-feature-pack-for-integration-services-ssis.md)。 
  
1.  在“添加 SSIS 连接管理器”  对话框中，选择“AzureStorage” ，然后单击“添加” 。  
  
2.  在“Azure 存储连接管理器编辑器”对话框中，选择“使用 Azure 帐户”  以通过 Internet 连接到 Azure 存储服务，或选择“使用本地开发人员帐户”  以连接到 Azure 存储模拟器承载的本地服务。  
  
3.  如果选择了“使用 Azure 帐户”  选项，请执行以下操作：  
  
    1.  为“存储帐户名称”  和“帐户密钥”  字段指定值。 这些值将存储为 SSIS 包中的敏感数据。  
  
    2.  如果你想要使用 HTTPS 而不是 HTTP 来连接到 Azure 存储服务，请选择“使用 HTTPS”  。  
  
4.  单击 **“确定”** 关闭对话框。  
  
5.  你可以看到你在“属性”  窗口中创建的连接管理器的属性。  
  
  
