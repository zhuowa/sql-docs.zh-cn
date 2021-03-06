---
title: 事务复制的发布类型 | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: replication
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- transactional replication, publications
ms.assetid: ad66aa34-3e37-401e-a6a1-fc1514eb6d50
caps.latest.revision: 32
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 75f9cacabd9ccebd7767e67b653c6f72df34970b
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="publication-types-for-transactional-replication"></a>事务复制的发布类型
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  事务复制提供了三种发布类型：  
  
|发布类型|Description|  
|----------------------|-----------------|  
|标准事务发布|适合于订阅服务器上的所有数据均为只读的拓扑（事务复制在订阅服务器上并不强制如此）。<br /><br /> 默认情况下，在使用 Transact-SQL 或复制管理对象 (RMO) 时创建标准事务发布。 使用新建发布向导时，将通过选择 **“发布类型”** 页上的 **“事务发布”** 来创建标准事务发布。<br /><br /> 有关创建发布的详细信息，请参阅 [发布数据和数据库对象](../../../relational-databases/replication/publish/publish-data-and-database-objects.md)。|  
|对等拓扑中的事务发布|此发布类型的特征如下：<br /><br /> - 每个位置都具有相同的数据，兼作发布服务器和订阅服务器。<br /><br /> - 同一行每次只能在一个位置进行更改。<br /><br /> - 此拓扑最适合需要高可用性和读取可伸缩性的服务器环境。<br /><br /> <br /><br /> 有关详细信息，请参阅 [Peer-to-Peer Transactional Replication](../../../relational-databases/replication/transactional/peer-to-peer-transactional-replication.md)。|  
  
## <a name="see-also"></a>另请参阅  
 [事务复制](../../../relational-databases/replication/transactional/transactional-replication.md)  
  
  
