---
title: "ALTER 队列 (Transact SQL) |Microsoft 文档"
ms.custom: 
ms.date: 05/01/2016
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ALTER_QUEUE_TSQL
- ALTER QUEUE
dev_langs:
- TSQL
helpviewer_keywords:
- number of queue readers
- modifying queues
- ALTER QUEUE statement
- queue readers [SQL Server]
- queues [Service Broker], modifying
- unavailable queues [SQL Server]
- activation stored procedures [Service Broker]
ms.assetid: d54aa325-8761-4cd4-8da7-acf33df12296
caps.latest.revision: 49
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 9320e2f2af4bccd07ee8b255166b513c0b204a76
ms.contentlocale: zh-cn
ms.lasthandoff: 09/01/2017

---
# <a name="alter-queue-transact-sql"></a>ALTER QUEUE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  更改队列的属性。  
  
 ![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "主题链接图标") [TRANSACT-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>语法  
  
```  
ALTER QUEUE <object>   
   queue_settings  
   | queue_action  
[ ; ]  
  
<object> : :=  
{  
    [ database_name. [ schema_name ] . | schema_name. ]  
        queue_name  
}   
  
<queue_settings> : :=  
WITH  
   [ STATUS = { ON | OFF } [ , ] ]  
   [ RETENTION = { ON | OFF } [ , ] ]  
   [ ACTIVATION (  
       { [ STATUS = { ON | OFF } [ , ] ]   
         [ PROCEDURE_NAME = <procedure> [ , ] ]  
         [ MAX_QUEUE_READERS = max_readers [ , ] ]  
         [ EXECUTE AS { SELF | 'user_name'  | OWNER } ]  
       |  DROP }  
          ) [ , ]]  
         [ POISON_MESSAGE_HANDLING (  
          STATUS = { ON | OFF } )  
         ]   
  
<queue_action> : :=  
   REBUILD [ WITH <query_rebuild_options> ]  
   | REORGANIZE [ WITH (LOB_COMPACTION = { ON | OFF } ) ]  
   | MOVE TO { file_group | "default" }  
  
<procedure> : :=  
{  
    [ database_name. [ schema_name ] . | schema_name. ]  
        stored_procedure_name  
}  
  
<queue_rebuild_options> : :=  
{  
   ( MAXDOP = max_degree_of_parallelism )  
}  
  
```  
  
## <a name="arguments"></a>参数  
 *database_name* （对象）  
 包含要更改队列的数据库的名称。 如果没有*database_name*提供，这将默认为当前数据库。  
  
 *schema_name* （对象）  
 新队列所属架构的名称。 如果没有*schema_name*提供，这将默认为当前用户的默认架构。  
  
 *queue_name*  
 要更改的队列的名称。  
  
 STATUS（队列）  
 指定队列是可用 (ON) 还是不可用 (OFF)。 如果队列不可用，则不能向队列添加消息或从队列中删除消息。  
  
 RETENTION  
 指定队列的保持期设置。 如果 RETENTION = ON，则在会话中使用此队列发送或接收的所有消息都将保持在队列中，直到会话结束为止。 这样便可保留消息以用于审核，或在发生错误时执行补偿事务。  
  
> [!NOTE]  
>  设置保留期 = ON 可能会降低性能。 仅当需要符合应用程序的服务级别协议时，才应使用此设置。  
  
 ACTIVATION  
 指定有关存储过程的信息，该存储过程可被激活以处理到达此队列的消息。  
  
 STATUS（激活）  
 指定队列是否激活存储过程。 当 STATUS = ON 时，如果当前运行的过程数小于 MAX_QUEUE_READERS，并且消息抵达队列的速度比存储过程接收消息的速度快，则队列启动用 PROCEDURE_NAME 指定的存储过程。 当 STATUS = OFF 时，队列不激活存储过程。  
  
 重新生成 [WITH \<queue_rebuild_options >]  
 **适用范围**： [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] 到 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]。  
  
 重新生成队列内部表上的所有索引。 当你遇到由于高负载的碎片问题，请使用此功能。 MAXDOP 是唯一受支持的队列的 rebuild 选项。 重新生成始终是脱机操作。  
  
 重新组织 [与 (LOB_COMPACTION = {ON |关闭}）]  
 **适用范围**： [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] 到 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]。  
  
 重新组织队列内部表上的所有索引。   
与用户表的 REORGANIZE，不同队列上的重新组织都始终执行脱机操作因为上队列已显式禁用页级锁。  
  
> [!TIP]  
>  有关索引碎片的一般指南 5%到 30%之间碎片时，重新组织索引。 超过 30%碎片时，重新生成索引。 但是，这些数字仅适用于一个起始点，你的环境的常规指导。 若要确定索引碎片数量，使用[sys.dm_db_index_physical_stats &#40;Transact SQL &#41;](../../relational-databases/system-dynamic-management-views/sys-dm-db-index-physical-stats-transact-sql.md) -请参阅有关示例该文章中的示例 G。  
  
 将移至 { *file_group* |"默认"}  
 **适用范围**： [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] 到 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]。  
  
 将 （具有其索引） 的队列内部表移动到用户指定的文件组。  新的文件组中不能是只读的。  
  
 PROCEDURE_NAME =\<过程 >  
 指定当队列包含要处理的消息时，要激活的存储过程的名称。 此值必须是一个 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 标识符。  
  
 *database_name* （过程）  
 包含存储过程的数据库的名称。  
  
 *schema_name* （过程）  
 拥有存储过程的架构的名称。  
  
 *stored_procedure_name*  
 是存储过程的名称。  
  
 MAX_QUEUE_READERS =*max_reader*  
 指定的最大队列将同时启动的激活存储过程的实例数。 值*max_readers*必须是介于 0 和 32767 之间的数字。  
  
 EXECUTE AS  
 指定用于运行激活存储过程的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 数据库用户帐户。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 必须能在队列激活存储过程时检查此用户的权限。 对于 Windows 域用户，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 必须连接到域，并能够在激活过程时验证指定用户的权限，否则激活失败。 对于 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 用户，服务器始终可检查权限。  
  
 SELF  
 指定存储过程以当前用户身份执行。 （执行该 ALTER QUEUE 语句的数据库主体。）  
  
 *user_name*  
 存储过程执行时所用的用户的名称。 *user_name*必须为有效[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]用户指定为[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]标识符。 当前用户必须具有 IMPERSONATE 权限*user_name*指定。  
  
 OWNER  
 指定存储过程以队列的所有者身份执行。  
  
 DROP  
 删除与队列关联的所有激活信息。  
  
 POISON_MESSAGE_HANDLING  
 指定是否启用有害消息处理。 默认值为 ON。  
  
 将有害消息处理设置为 OFF 的队列在五个连续的事务回滚之后不会被禁用。 这样，应用程序就可以定义自定义的有害消息处理系统。  
  
## <a name="remarks"></a>注释  
 当指定了激活存储过程的队列中包含消息时，如果将激活状态从 OFF 更改为 ON，则会立即激活该激活存储过程。 如果将激活状态从 ON 更改为 OFF，则会阻止代理激活存储过程的实例，但不会停止正在运行的存储过程实例。  
  
 修改队列以添加激活存储过程时，不会更改该队列的激活状态。 更改队列的激活存储过程时，也不会影响当前正在运行的激活存储过程实例。  
  
 激活过程中，[!INCLUDE[ssSB](../../includes/sssb-md.md)] 会检查队列的最大队列读取器数。 因此，更改某一队列以增加最大队列读取器数时，[!INCLUDE[ssSB](../../includes/sssb-md.md)] 可以立即启动激活存储过程的更多实例。 修改某一队列以减少最大队列读取器数时，不会影响当前正在运行的激活存储过程实例。 但直到激活存储过程的实例数降至低于配置的最大数目时，[!INCLUDE[ssSB](../../includes/sssb-md.md)] 才会启动该存储过程的新实例。  
  
 队列不可用时，[!INCLUDE[ssSB](../../includes/sssb-md.md)] 将在数据库的传输队列中保存使用该队列的服务的消息。 [Sys.transmission_queue](../../relational-databases/system-catalog-views/sys-transmission-queue-transact-sql.md)目录视图提供的传输队列的视图。  
  
 如果 RECEIVE 语句或 GET CONVERSATION GROUP 语句指定了不可用的队列，则该语句将失败，并出现 [!INCLUDE[tsql](../../includes/tsql-md.md)] 错误。  
  
## <a name="permissions"></a>Permissions  
 默认情况下，队列的所有者、db_ddladmin 或 db_owner 固定数据库角色的成员及 sysadmin 固定服务器角色的成员具有修改队列的权限。  
  
## <a name="examples"></a>示例  
  
### <a name="a-making-a-queue-unavailable"></a>A. 使队列不可用  
 以下示例使 `ExpenseQueue` 队列无法接收消息。  
  
```  
ALTER QUEUE ExpenseQueue WITH STATUS = OFF ;  
```  
  
### <a name="b-changing-the-activation-stored-procedure"></a>B. 更改激活存储过程  
 以下示例更改队列启动的存储过程。 此存储过程以运行 `ALTER QUEUE` 语句的用户的身份执行。  
  
```  
ALTER QUEUE ExpenseQueue  
    WITH ACTIVATION (  
        PROCEDURE_NAME = new_stored_proc,  
        EXECUTE AS SELF) ;  
```  
  
### <a name="c-changing-the-number-of-queue-readers"></a>C. 更改队列读取器数  
 以下示例将 [!INCLUDE[ssSB](../../includes/sssb-md.md)] 为此队列启动的最大存储过程实例数设置为 `7`。  
  
```  
ALTER QUEUE ExpenseQueue WITH ACTIVATION (MAX_QUEUE_READERS = 7) ;  
```  
  
### <a name="d-changing-the-activation-stored-procedure-and-the-execute-as-account"></a>D. 更改激活存储过程和 EXECUTE AS 帐户  
 以下示例更改 [!INCLUDE[ssSB](../../includes/sssb-md.md)] 启动的存储过程。 该存储过程以用户 `SecurityAccount` 的身份执行。  
  
```  
ALTER QUEUE ExpenseQueue  
    WITH ACTIVATION (  
        PROCEDURE_NAME = AdventureWorks2012.dbo.new_stored_proc ,  
        EXECUTE AS 'SecurityAccount') ;  
```  
  
### <a name="e-setting-the-queue-to-retain-messages"></a>E. 将队列设置为保留消息  
 以下示例将队列设置为保留消息。 在包含消息的会话结束之前，队列将一直保留使用此队列的服务收发的所有消息。  
  
```  
ALTER QUEUE ExpenseQueue WITH RETENTION = ON ;  
```  
  
### <a name="f-removing-activation-from-a-queue"></a>F. 从队列中删除激活  
 以下示例从队列中删除所有激活信息。  
  
```  
ALTER QUEUE ExpenseQueue WITH ACTIVATION (DROP) ;  
```  
  
### <a name="g-rebuilding-queue-indexes"></a>G. 重新生成队列索引  
  
**适用范围**： [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] 到 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]。  
  
 下面的示例重新生成队列索引  
  
```  
ALTER QUEUE ExpenseQueue REBUILD WITH (MAXDOP = 2)   
```  
  
### <a name="h-reorganizing-queue-indexes"></a>H. 重新组织队列索引  
  
**适用范围**： [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] 到 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]。  
  
 下面的示例将重组队列索引  
  
```  
ALTER QUEUE ExpenseQueue REORGANIZE   
```  
  
### <a name="i-moving-queue-internal-table-to-another-filegroup"></a>I： 将队列内部表移动到另一个文件组  
  
**适用范围**： [!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] 到 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]。  
  
```  
ALTER QUEUE ExpenseQueue MOVE TO [NewFilegroup]   
```  
  
## <a name="see-also"></a>另请参阅  
 [CREATE QUEUE (Transact SQL)](../../t-sql/statements/create-queue-transact-sql.md)   
 [删除队列 &#40;Transact SQL &#41;](../../t-sql/statements/drop-queue-transact-sql.md)   
 [EVENTDATA (Transact-SQL)](../../t-sql/functions/eventdata-transact-sql.md)   
 [sys.dm_db_index_physical_stats (Transact-SQL)](../../relational-databases/system-dynamic-management-views/sys-dm-db-index-physical-stats-transact-sql.md)  
  
  
