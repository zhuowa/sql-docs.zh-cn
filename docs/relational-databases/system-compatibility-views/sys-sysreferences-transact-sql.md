---
title: sys.sysreferences (Transact SQL) |Microsoft 文档
ms.custom: ''
ms.date: 03/15/2017
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse, pdw
ms.component: system-compatibility-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.sysreferences
- sys.sysreferences_TSQL
- sysreferences
- sysreferences_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.sysreferences compatibility view
- sysreferences system table
ms.assetid: 81276f13-202e-4e74-962d-46eb98c98d2e
caps.latest.revision: 38
author: rothja
ms.author: jroth
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: f708e89b4cc152e3f508c5eede3f95f1624148fa
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="syssysreferences-transact-sql"></a>sys.sysreferences (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

  包括 FOREIGN KEY 约束定义到数据库中被引用列的映射。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssnoteCompView](../../includes/ssnotecompview-md.md)]  
  
|列名|数据类型|Description|  
|-----------------|---------------|-----------------|  
|**constid**|**int**|FOREIGN KEY 约束的 ID。|  
|**fkeyid**|**int**|执行引用表的 ID。|  
|**rkeyid**|**int**|被引用表的 ID。|  
|**rkeyindid**|**int**|包含被引用的键列的被引用表的唯一索引的索引 ID。|  
|**keycnt**|**int**|键中的列数。|  
|**forkeys**|**varbinary(32)**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**refkeys**|**varbinary(32)**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**fkeydbid**|**int**|保留。|  
|**rkeydbid**|**int**|保留。|  
|**fkey1**|**int**|引用列的列 ID。|  
|**fkey2**|**int**|引用列的列 ID。|  
|**fkey3**|**int**|引用列的列 ID。|  
|**fkey4**|**int**|引用列的列 ID。|  
|**fkey5**|**int**|引用列的列 ID。|  
|**fkey6**|**int**|引用列的列 ID。|  
|**fkey7**|**int**|引用列的列 ID。|  
|**fkey8**|**int**|引用列的列 ID。|  
|**fkey9**|**int**|引用列的列 ID。|  
|**fkey10**|**int**|引用列的列 ID。|  
|**fkey11**|**int**|引用列的列 ID。|  
|**fkey12**|**int**|引用列的列 ID。|  
|**fkey13**|**int**|引用列的列 ID。|  
|**fkey14**|**int**|引用列的列 ID。|  
|**fkey15**|**int**|引用列的列 ID。|  
|**fkey16**|**int**|引用列的列 ID。|  
|**rkey1**|**int**|被引用列的列 ID。|  
|**rkey2**|**int**|被引用列的列 ID。|  
|**rkey3**|**int**|被引用列的列 ID。|  
|**rkey4**|**int**|被引用列的列 ID。|  
|**rkey5**|**int**|被引用列的列 ID。|  
|**rkey6**|**int**|被引用列的列 ID。|  
|**rkey7**|**int**|被引用列的列 ID。|  
|**rkey8**|**int**|被引用列的列 ID。|  
|**rkey9**|**int**|被引用列的列 ID。|  
|**rkey10**|**int**|被引用列的列 ID。|  
|**rkey11**|**int**|被引用列的列 ID。|  
|**rkey12**|**int**|被引用列的列 ID。|  
|**rkey13**|**int**|被引用列的列 ID。|  
|**rkey14**|**int**|被引用列的列 ID。|  
|**rkey15**|**int**|被引用列的列 ID。|  
|**rkey16**|**int**|被引用列的列 ID。|  
  
## <a name="see-also"></a>另请参阅  
 [将系统表映射到系统视图&#40;Transact SQL&#41;](../../relational-databases/system-tables/mapping-system-tables-to-system-views-transact-sql.md)   
 [兼容性视图 (Transact SQL)](~/relational-databases/system-compatibility-views/system-compatibility-views-transact-sql.md)  
  
  
