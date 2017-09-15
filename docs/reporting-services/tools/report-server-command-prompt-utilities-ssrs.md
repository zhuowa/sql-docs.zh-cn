---
title: "报表服务器命令提示实用工具 (SSRS) |Microsoft 文档"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- rsconfig utility
- components [Reporting Services], command line utilities
- rs utility
- command prompt utilities [Reporting Services]
- rskeymgmt utility
ms.assetid: 68f2f9f4-f894-40ff-a71c-f9756bf4b68c
caps.latest.revision: 48
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: eb04937fc5c68bf2efb82ece9914c56409b7f325
ms.contentlocale: zh-cn
ms.lasthandoff: 08/09/2017

---
# <a name="report-server-command-prompt-utilities-ssrs"></a>报表服务器命令提示实用工具 (SSRS)
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]包括若干可用于管理报表服务器的命令行实用工具。 安装报表服务器时将自动安装这些实用工具。  
  
|名称|命令文件|支持的部署模式|Description|  
|----------|------------------|-------------------------------|-----------------|  
|RSS 实用工具|rs.exe|本机模式和 SharePoint 模式。 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] 版本引入 SharePoint 模式支持。|[rs 实用工具](../../reporting-services/tools/rs-exe-utility-ssrs.md) 是可用于执行脚本操作的脚本主机。 使用此工具运行[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]报表服务器数据库之间复制数据的脚本将报表发布，在报表服务器中创建项，数据库和的详细信息。 若要了解有关使用脚本来管理服务器的详细信息，请参阅 [脚本部署和管理任务](../../reporting-services/tools/script-deployment-and-administrative-tasks.md)。|  
|Powershell cmdlet||仅限 SharePoint|有关 powershell cmdlet 列表的详细信息，请参阅 [用于 Reporting Services SharePoint 模式的 PowerShell cmdlet](../../reporting-services/report-server-sharepoint/powershell-cmdlets-for-reporting-services-sharepoint-mode.md)。|  
|rsconfig 配置工具|rsconfig.exe|仅限本机|[rsconfig 实用工具](../../reporting-services/tools/rsconfig-utility-ssrs.md) 用于配置和管理与报表服务器数据库的报表服务器连接。 您还可以使用该工具来指定用于无人参与报表处理的用户帐户。 有关详细信息，请参阅 [Reporting Services 报表服务器（本机模式）](../../reporting-services/report-server/reporting-services-report-server-native-mode.md)。 若要了解有关连接配置的详细信息，请参阅[配置报表服务器数据库连接 (SSRS Configuration Manager)](../../reporting-services/install-windows/configure-a-report-server-database-connection-ssrs-configuration-manager.md)。|  
|Rskeymgmt 实用工具|rskeymgmt.exe|仅限本机|[rskeymgmt 实用工具](../../reporting-services/tools/rskeymgmt-utility-ssrs.md) 是一个加密密钥管理工具。 使用该工具可以备份、应用、重新创建和删除对称密钥。 您还可以使用此工具将报表服务器实例附加到共享的报表服务器数据库。 可以在数据库恢复操作中使用 Rskeymgmt。 通过应用对称密钥的备份副本，可以在新安装中重用现有数据库。 如果无法恢复密钥，此工具为您提供了一种删除不再使用的加密内容的方法。 若要了解有关密钥管理和敏感数据存储的详细信息，请参阅[存储加密报表服务器数据 (SSRS Configuration Manager)](../../reporting-services/install-windows/ssrs-encryption-keys-store-encrypted-report-server-data.md)和[配置和管理加密密钥 (SSRS Configuration Manager)](../../reporting-services/install-windows/ssrs-encryption-keys-manage-encryption-keys.md)。|  
  
> [!NOTE]  
>  如果喜欢使用带有图形用户界面的工具，则可以使用 Reporting Services Configuration Manager 来代替 **rsconfig** 和 **rskeymgmt**。  
  
## <a name="see-also"></a>另请参阅  
 [Reporting Services 配置管理器 &#40;本机模式 &#41;](../../reporting-services/install-windows/reporting-services-configuration-manager-native-mode.md)   
 [Reporting Services 工具](../../reporting-services/tools/reporting-services-tools.md)   
 [Reporting Services 报表服务器 &#40;本机模式 &#41;](../../reporting-services/report-server/reporting-services-report-server-native-mode.md)  
  
  