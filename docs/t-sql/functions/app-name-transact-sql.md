---
title: "APP_NAME (Transact SQL) |Microsoft 文档"
ms.custom: 
ms.date: 07/24/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- APP_NAME_TSQL
- APP_NAME
dev_langs:
- TSQL
helpviewer_keywords:
- name checking for current session [SQL Server]
- sessions [SQL Server], application names
- applications [SQL Server], names
- current session application names
- APP_NAME function
ms.assetid: e491e192-9b30-4243-bc19-33c133fe08a8
caps.latest.revision: 35
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: c4f63ae216bad0269415ac5e0aa57a7543500f0c
ms.contentlocale: zh-cn
ms.lasthandoff: 09/01/2017

---
# <a name="appname-transact-sql"></a>APP_NAME (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

返回当前会话的应用程序名称（如果应用程序进行了设置）。
  
> [!IMPORTANT]  
>  应用程序名称由客户端提供，并不以任何方式进行验证。 不要使用**APP_NAME**作为一种安全检查的一部分。  
  
![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "主题链接图标") [TRANSACT-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)
  
## <a name="syntax"></a>语法  
  
```sql
  
APP_NAME  ( )  
```  
  
## <a name="return-types"></a>返回类型  
**nvarchar （128)**
  
## <a name="remarks"></a>注释  
使用**APP_NAME**如果想要为不同的应用程序执行不同操作。 例如，针对不同应用程序进行不同的日期格式化，或返回信息性消息到某些应用程序。
  
在中设置应用程序名称[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]中**连接到数据库引擎**对话框中，单击**选项**。 上**其他连接参数**选项卡上，提供**应用**格式的属性`;app='application_name'`
  
## <a name="examples"></a>示例  
以下示例检查了初始化该进程的客户端应用程序是否是一个 `SQL Server Management Studio` 会话，并且提供 US 或 ANSI 格式的日期。
  
```sql
USE AdventureWorks2012;  
GO  
IF APP_NAME() = 'Microsoft SQL Server Management Studio - Query'  
PRINT 'This process was started by ' + APP_NAME() + '. The date is ' + CONVERT ( varchar(100) , GETDATE(), 101) + '.';  
ELSE   
PRINT 'This process was started by ' + APP_NAME() + '. The date is ' + CONVERT ( varchar(100) , GETDATE(), 102) + '.';  
GO  
```  
  
## <a name="see-also"></a>另请参阅
[系统函数 &#40;Transact SQL &#41;](../../relational-databases/system-functions/system-functions-for-transact-sql.md)  
[函数](../../t-sql/functions/functions.md)
  
  
