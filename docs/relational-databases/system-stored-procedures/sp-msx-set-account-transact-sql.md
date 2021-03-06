---
title: sp_msx_set_account (Transact SQL) |Microsoft 文档
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_msx_set_account
- sp_msx_set_account_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_msx_set_account
ms.assetid: 314ec720-3a37-48f7-bb6b-8d5b894bf843
caps.latest.revision: 26
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: a2d776a7ad3d29c180a4a2d2b017f5e1e6d0158a
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="spmsxsetaccount-transact-sql"></a>sp_msx_set_account (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  设置目标服务器上的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理主服务器帐户名和密码。  
  
 ![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "主题链接图标") [TRANSACT-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>语法  
  
```  
  
sp_msx_set_account [ @credential_name = ] 'credential_name'  | [ @credential_id = ] credential_id  
```  
  
## <a name="arguments"></a>参数  
 [ **@credential_name=** ] **'***credential_name***'**  
 用于登录到主服务器的凭据的名称。 所提供的名称必须是现有凭据的名称。 任一*credential_name*或*credential_id*必须指定。  
  
 [ **@credential_id=** ] *credential_id*  
 用于登录到主服务器的凭据的标识符。 标识符必须是现有凭据的标识符。 任一*credential_name*或*credential_id*必须指定。  
  
## <a name="return-code-values"></a>返回代码值  
 **0** （成功） 或**1** （失败）  
  
## <a name="result-sets"></a>结果集  
 无。  
  
## <a name="remarks"></a>注释  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 使用凭据存储目标服务器用于登录到主服务器的用户名和密码信息。 该过程将设置此目标服务器的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 代理用于登录到主服务器的凭据。  
  
 所指定的凭据必须是现有凭据。 有关创建凭据的详细信息，请参阅[CREATE CREDENTIAL &#40;TRANSACT-SQL&#41;](../../t-sql/statements/create-credential-transact-sql.md)。  
  
## <a name="permissions"></a>权限  
 执行权限**sp_msx_set_account**的成员的默认**sysadmin**固定的服务器角色。  
  
## <a name="examples"></a>示例  
 以下是设置该服务器，以使用凭据 `MsxAccount` 登录到主服务器的示例。  
  
```  
USE msdb ;  
GO  
  
EXECUTE dbo.sp_msx_set_account @credential_name = MsxAccount ;  
GO  
```  
  
## <a name="see-also"></a>另请参阅  
 [SQL Server 代理存储过程&#40;Transact SQL&#41;](../../relational-databases/system-stored-procedures/sql-server-agent-stored-procedures-transact-sql.md)   
 [CREATE CREDENTIAL &#40;Transact-SQL&#41;](../../t-sql/statements/create-credential-transact-sql.md)   
 [sp_msx_get_account &#40;Transact SQL&#41;](../../relational-databases/system-stored-procedures/sp-msx-get-account-transact-sql.md)  
  
  
