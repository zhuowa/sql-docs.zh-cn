---
title: sys.dm_exec_valid_use_hints (Transact SQL) |Microsoft 文档
ms.custom: ''
ms.date: 11/17/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: dmv's
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sys.dm_exec_valid_use_hints
- sys.dm_exec_valid_use_hints_TSQL
- dm_exec_valid_use_hints
- dm_exec_valid_use_hints_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.dm_exec_valid_use_hints management view
ms.assetid: 65d50589-39c2-4046-92b6-0c4587d8c593
caps.latest.revision: 5
author: pmasl
ms.author: pelopes
manager: craigg
ms.openlocfilehash: 63fe1f46a60f04175b10039d227af153a73c6f58
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="sysdmexecvalidusehints-transact-sql"></a>sys.dm_exec_valid_use_hints (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

返回[使用提示](../../t-sql/queries/hints-transact-sql-query.md)支持提示名称。 它列出每个行的一个提示名称。  
  
使用此 DMV 以查看所有支持提示下使用提示表示法的列表。  
  
|列名|数据类型|Description|  
|-----------------|---------------|-----------------|  
|name|**sysname**|提示的名称。|

请参阅[查询提示](../../t-sql/queries/hints-transact-sql-query.md)有关每个提示的说明。

中引入[!INCLUDE[ssSQL15_md](../../includes/sssql15-md.md)]SP1。
  
## <a name="see-also"></a>另请参阅  
    
 [动态管理视图和函数 (Transact-SQL)](~/relational-databases/system-dynamic-management-views/system-dynamic-management-views.md)   
 [与数据库相关的动态管理视图&#40;Transact SQL&#41;](../../relational-databases/system-dynamic-management-views/database-related-dynamic-management-views-transact-sql.md)  

