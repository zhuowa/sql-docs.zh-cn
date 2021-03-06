---
title: sys.dm_db_session_space_usage (TRANSACT-SQL) |Microsoft 文档
ms.custom: ''
ms.date: 11/16/2015
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- dm_db_session_space_usage_TSQL
- dm_db_session_space_usage
- sys.dm_db_session_space_usage
- sys.dm_db_session_space_usage_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_db_session_space_usage dynamic management view
ms.assetid: a67a6045-8e14-460a-9fe3-912b846c08c1
caps.latest.revision: 34
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 472bafe71a952b471c871af3f789698cf0053b9d
ms.sourcegitcommit: d2573a8dec2d4102ce8882ee232cdba080d39628
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
---
# <a name="sysdmdbsessionspaceusage-transact-sql"></a>sys.dm_db_session_space_usage (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  返回每个会话为数据库分配和释放的页数。  
  
> [!NOTE]  
>  此视图是仅适用于[tempdb 数据库](../../relational-databases/databases/tempdb-database.md)。  
  
> [!NOTE]  
>  若要从我们称之为[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]或[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]，使用名称**sys.dm_pdw_nodes_db_session_space_usage**。  
  
|列名|数据类型|Description|  
|-----------------|---------------|-----------------|  
|**session_id**|**int**|会话 ID。<br /><br /> **session_id**映射到**session_id**中[sys.dm_exec_sessions](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sessions-transact-sql.md)。|  
|**database_id**|**int**|数据库 ID。|  
|**user_objects_alloc_page_count**|**bigint**|由该会话为用户对象保留或分配的页数。|  
|**user_objects_dealloc_page_count**|**bigint**|由该会话释放并不再为用户对象保留的页数。|  
|**internal_objects_alloc_page_count**|**bigint**|由该会话为内部对象保留或分配的页数。|  
|**internal_objects_dealloc_page_count**|**bigint**|由该会话释放并不再为内部对象保留的页数。|  
|**user_objects_deferred_dealloc_page_count**|**bigint**|已标记为延迟释放的页的数目。<br /><br /> **注意：** service pack 中引入[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]和[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]。|  
|**pdw_node_id**|**int**|**适用于**: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]， [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]<br /><br /> 此分布的节点标识符。|  
  
## <a name="permissions"></a>权限  

上[!INCLUDE[ssNoVersion_md](../../includes/ssnoversion-md.md)]，需要`VIEW SERVER STATE`权限。   
上[!INCLUDE[ssSDS_md](../../includes/sssds-md.md)]，需要`VIEW DATABASE STATE`数据库中的权限。   

## <a name="remarks"></a>注释  
 由该视图报告的分配或释放的计数不包括 IAM 页。  
  
 在会话开始时，页计数器被初始化为零 (0)。 计数器跟踪为会话中已经完成的任务分配或释放的总页数。 仅当任务结束时，该计数器才更新；它们不反映正在运行的任务。  
  
 会话可同时包含多个活动请求。 如果是并行查询，则请求可启动多个线程和任务。  
  
 有关会话、 请求和任务的详细信息，请参阅[sys.dm_exec_sessions &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sessions-transact-sql.md)， [sys.dm_exec_requests &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md)，和[sys.dm_os_tasks &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-tasks-transact-sql.md)。  
  
## <a name="user-objects"></a>用户对象  
 用户对象页计数器中包括下列对象：  
  
-   用户定义的表和索引  
  
-   系统表和索引  
  
-   全局临时表和索引  
  
-   局部临时表和索引  
  
-   表变量  
  
-   表值函数中返回的表  
  
## <a name="internal-objects"></a>内部对象  
 内部对象才在**tempdb**。 内部对象页计数器中包括下列对象：  
  
-   用于游标或假脱机操作以及临时大型对象 (LOB) 存储的工作表  
  
-   用于哈希联接等操作的工作文件  
  
-   排序段  
  
## <a name="physical-joins"></a>物理联接  
 ![有关 sys.dm_db_session_space_usage 物理联接](../../relational-databases/system-dynamic-management-views/media/join-dm-db-session-space-usage-1.gif "物理联接为 sys.dm_db_session_space_usage")  
  
## <a name="relationship-cardinalities"></a>关系基数  
  
|从|若要|关系|  
|----------|--------|------------------|  
|dm_db_session_space_usage.session_id|dm_exec_sessions.session_id|一对一|  
  
## <a name="see-also"></a>另请参阅  
 [动态管理视图和函数 (Transact-SQL)](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [与数据库相关的动态管理视图&#40;Transact SQL&#41;](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)   
 [sys.dm_exec_sessions &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-sessions-transact-sql.md)   
 [sys.dm_exec_requests &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql.md)   
 [sys.dm_os_tasks &#40;Transact SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-os-tasks-transact-sql.md)   
 [sys.dm_db_task_space_usage &#40;Transact SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-task-space-usage-transact-sql.md)   
 [sys.dm_db_file_space_usage (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-db-file-space-usage-transact-sql.md)  
  
  



