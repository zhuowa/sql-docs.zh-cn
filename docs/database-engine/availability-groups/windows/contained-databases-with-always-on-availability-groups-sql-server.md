---
title: 包含的数据库与 AlwaysOn 可用性组 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 05/17/2016
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.suite: sql
ms.technology: high-availability
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], interoperability
- contained database, AlwaysOnAvailabilityGroups
ms.assetid: cacce3ae-e940-4566-8298-6607c4268e74
caps.latest.revision: 9
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 13a67108c4e8a245735adb348c4f391be75a8a96
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="contained-databases-with-always-on-availability-groups-sql-server"></a>包含的数据库与 Always On 可用性组 (SQL Server)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  本主题包含将包含数据库用于 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 中的 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]的相关信息。  
  
 **本主题内容：**  
  
-   [先决条件](#Prerequisites)  
  
-   [相关任务](#RelatedTasks)  
  
##  <a name="Prerequisites"></a> 先决条件  
  
-   在将包含数据库添加到某一可用性组之前，请确保在承载该可用性组的可用性副本的每个服务器实例上 **contained database authentication** 服务器选项都设置为 **1** 。 有关详细信息，请参阅 [contained database authentication 服务器配置选项](../../../database-engine/configure-windows/contained-database-authentication-server-configuration-option.md) 和 [服务器配置选项 (SQL Server)](../../../database-engine/configure-windows/server-configuration-options-sql-server.md)的相关信息。  
  
##  <a name="RelatedTasks"></a> 相关任务  
  
-   [服务器配置选项 (SQL Server)](../../../database-engine/configure-windows/server-configuration-options-sql-server.md)  
  
## <a name="see-also"></a>另请参阅  
 [AlwaysOn 可用性组概述 (SQL Server)](../../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)   
 [包含的数据库](../../../relational-databases/databases/contained-databases.md)  
  
  
