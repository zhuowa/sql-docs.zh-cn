---
title: "sys.dm_xtp_gc_queue_stats (TRANSACT-SQL) |Microsoft 文档"
ms.custom: 
ms.date: 08/02/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: dmv's
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- dm_xtp_gc_stats
- dm_xtp_gc_stats_TSQL
- sys.dm_xtp_gc_stats_TSQL
- sys.dm_xtp_gc_stats
dev_langs: TSQL
helpviewer_keywords: sys.dm_xtp_gc_stats dynamic management view
ms.assetid: addef774-318d-46a7-85df-f93168a800cb
caps.latest.revision: "18"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 1f5af0d350c90067c75a8f26d2fbf429d018acff
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/17/2017
---
# <a name="sysdmxtpgcqueuestats-transact-sql"></a>sys.dm_xtp_gc_queue_stats (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2014-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2014-xxxx-xxxx-xxx-md.md)]

  输出有关服务器上每个垃圾回收工作线程队列的信息，以及有关每个队列的各种统计信息。 每个逻辑 CPU 有一个队列。  
  
 主垃圾回收线程（空闲线程）针对自上次调用主垃圾回收线程以来完成的所有事务跟踪已更新、删除和插入的行。 垃圾回收线程唤醒时，它会确定最早活动事务的时间戳是否已更改。 如果最早活动事务已更改，则空闲线程会针对不再需要写入集的事务，将工作项（16 行为一个块区）排入队列。 例如，如果您删除 1,024 行，则最终将看到 64 个垃圾回收工作项排队，每个工作项都包含 16 个已删除行。  用户事务提交之后，它选择其计划程序上的所有排队项。 如果其计划程序上没有排队项，则用户事务会搜索当前 NUMA 节点中的任何队列。  
  
 您可以通过执行 sys.dm_xtp_gc_queue_stats 以查看是否在处理排队工作，确定垃圾回收是否在为已删除行释放内存。 如果没有被处理 current_queue_depth 中的条目，或者向 current_queue_depth 添加任何新的工作项，这是垃圾回收不释放内存的指示。 例如，如果存在长时间运行的事务，则垃圾回收无法进行。  
  
 有关详细信息，请参阅[内存中 OLTP&#40;内存中优化&#41;](../../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)。  
  

|列名|类型|Description|  
|-----------------|----------|-----------------|  
|queue_id|**int**|队列的唯一标识符。|  
|total_enqueues|**bigint**|自启动服务器以来排入此队列的垃圾回收工作项的总数。|  
|total_dequeues|**bigint**|自启动服务器以来离开此队列的垃圾回收工作项的总数。|  
|current_queue_depth|**bigint**|此队列中现有的垃圾回收工作项的当前数量。 此项可能意味着要对一个或多个项进行垃圾回收。|  
|maximum_queue_depth|**bigint**|此队列已显示的最大深度。|  
|last_service_ticks|**bigint**|上次服务队列时的 CPU 时钟周期。|  
  
## <a name="permissions"></a>Permissions  
 需要 VIEW SERVER STATE 权限。  
  
## <a name="user-scenario"></a>使用方案  
 此输出显示，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 通过 4 个内核运行，或者 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 实例已关联到 4 个内核：  
  
 此输出显示，要处理的队列中没有工作项。 对于队列 0，自 SQL 启动后取消排队的总工作项数为 15625，最大队列深度是 215625。  
  
```  
queue_id total_enqueues total_dequeues current_queue_depth  maximum_queue_depth  last_service_ticks  
----------------------------------------------------------------------------------------------------  
0        15625                15625    0                    15625                1233573168347  
1        15625                15625    0                    15625                1234123295566  
2        15625                15625    0                    15625                1233569418146  
3        15625                15625    0                    15625                1233571605761  
```  
  
## <a name="see-also"></a>另请参阅  
 [内存优化表的动态管理视图 &#40;Transact SQL &#41;](../../relational-databases/system-dynamic-management-views/memory-optimized-table-dynamic-management-views-transact-sql.md)  
  
  