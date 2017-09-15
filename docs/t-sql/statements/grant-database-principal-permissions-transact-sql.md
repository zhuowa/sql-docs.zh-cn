---
title: "GRANT 数据库主体权限 (Transact SQL) |Microsoft 文档"
ms.custom: 
ms.date: 03/12/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- database roles [SQL Server], permissions
- permissions [SQL Server], database roles
- granting permissions [SQL Server], database users
- granting permissions [SQL Server], application roles
- granting permissions [SQL Server], database roles
- database user permissions [SQL Server]
- permissions [SQL Server], application roles
- permissions [SQL Server], database users
- GRANT statement, users
- GRANT statement, roles
- application roles [SQL Server], permissions
ms.assetid: 012588a2-cbe1-48f0-a731-b4a2b83203d5
caps.latest.revision: 24
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: a2d78167459a509d788e65ad31d4660298107558
ms.contentlocale: zh-cn
ms.lasthandoff: 09/01/2017

---
# <a name="grant-database-principal-permissions-transact-sql"></a>GRANT 数据库主体权限 (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  授予对 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中数据库用户、数据库角色或应用程序角色的权限。  
  

 ![主题链接图标](../../database-engine/configure-windows/media/topic-link.gif "主题链接图标") [TRANSACT-SQL 语法约定](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>语法  
  
```  
GRANT permission [ ,...n ]    
    ON   
    {  [ USER :: database_user ]  
     | [ ROLE :: database_role ]  
     | [ APPLICATION ROLE :: application_role ]  
    }  
    TO <database_principal> [ ,...n ]  
       [ WITH GRANT OPTION ]  
       [ AS <database_principal> ]  
  
<database_principal> ::=  
    Database_user   
  | Database_role   
  | Application_role   
  | Database_user_mapped_to_Windows_User   
  | Database_user_mapped_to_Windows_Group   
  | Database_user_mapped_to_certificate   
  | Database_user_mapped_to_asymmetric_key   
  | Database_user_with_no_login   
```  
  
## <a name="arguments"></a>参数  
 *权限*  
 指定可对数据库主体授予的权限。 有关权限的列表，请参阅本主题后面的“备注”部分。  
  
 用户::*database_user*  
 指定要对其授予权限的用户的类和名称。 需要作用域限定符 ::。  
  
 角色::*database_role*  
 指定要对其授予权限的角色的类和名称。 需要作用域限定符 ::。  
  
 应用程序角色::*application_role*  
   
 指定要对其授予权限的应用程序角色的类和名称。 需要作用域限定符 ::。  
  
 WITH GRANT OPTION  
 指示该主体还可以向其他主体授予所指定的权限。  
  
 AS \<database_principal >  
 指定一个主体，执行该查询的主体从该主体获得授予该权限的权利。  
  
 *Database_user*  
 指定数据库用户。  
  
 *Database_role*  
 指定数据库角色。  
  
 *Application_role*  
 **适用于**:[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]通过[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]， [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)]。  
  
 指定应用程序角色。  
  
 *Database_user_mapped_to_Windows_User*  
 指定一个映射到 Windows 用户的数据库用户。  
  
 *Database_user_mapped_to_Windows_Group*  
  
 指定映射到 Windows 组的数据库用户。  
  
 *Database_user_mapped_to_certificate*  
  
 指定映射到证书的数据库用户。  
  
 *Database_user_mapped_to_asymmetric_key*  
  
 指定映射到非对称密钥的数据库用户。  
  
 *Database_user_with_no_login*  
 指定无相应服务器级主体的数据库用户。  
  
## <a name="remarks"></a>注释  
 有关数据库主体的信息会显示在[sys.database_principals](../../relational-databases/system-catalog-views/sys-database-principals-transact-sql.md)目录视图。 有关数据库级别权限的信息会显示在[sys.database_permissions](../../relational-databases/system-catalog-views/sys-database-permissions-transact-sql.md)目录视图。  
  
## <a name="database-user-permissions"></a>数据库用户权限  
 数据库用户是一个数据库级的安全对象，包含于权限层次结构中作为其父级的数据库中。 下表列出了可授予的对数据库用户最为具体的限定权限，以及隐含这些权限的更为通用的权限。  
  
|数据库用户权限|数据库用户权限隐含的权限|数据库权限隐含的权限|  
|------------------------------|-----------------------------------------|------------------------------------|  
|CONTROL|CONTROL|CONTROL|  
|IMPERSONATE|CONTROL|CONTROL|  
|ALTER|CONTROL|ALTER ANY USER|  
|VIEW DEFINITION|CONTROL|VIEW DEFINITION|  
  
## <a name="database-role-permissions"></a>数据库角色权限  
 数据库角色是一个数据库级的安全对象，包含于权限层次结构中作为其父级的数据库中。 下表列出了可授予的对数据库角色最为具体的限定权限，以及隐含这些权限的更为通用的权限。  
  
|数据库角色权限|数据库角色权限隐含的权限|数据库权限隐含的权限|  
|------------------------------|-----------------------------------------|------------------------------------|  
|CONTROL|CONTROL|CONTROL|  
|TAKE OWNERSHIP|CONTROL|CONTROL|  
|ALTER|CONTROL|ALTER ANY ROLE|  
|VIEW DEFINITION|CONTROL|VIEW DEFINITION|  
  
## <a name="application-role-permissions"></a>应用程序角色权限  
 应用程序角色是一个数据库级的安全对象，包含于权限层次结构中作为其父级的数据库中。 下面列出了可授予的对应用程序角色最为具体的限定权限，以及隐含这些权限的更为通用的权限。  
  
|应用程序角色权限|应用程序角色权限隐含的权限|数据库权限隐含的权限|  
|---------------------------------|--------------------------------------------|------------------------------------|  
|CONTROL|CONTROL|CONTROL|  
|ALTER|CONTROL|ALTER ANY APPLICATION ROLE|  
|VIEW DEFINITION|CONTROL|VIEW DEFINITION|  
  
## <a name="permissions"></a>Permissions  
 授权者（或用 AS 选项指定的主体）必须具有带 GRANT OPTION 的相同权限，或具有隐含所授予权限的更高权限。  
  
 若要使用 AS 选项，还必须满足以下附加要求：  
  
|AS *granting_principal*|所需的其他权限|  
|------------------------------|------------------------------------|  
|数据库用户|对用户的 IMPERSONATE 权限、db_securityadmin 固定数据库角色的成员身份、db_owner 固定数据库角色的成员身份或 sysadmin 固定服务器角色的成员身份。|  
|映射到 Windows 用户的数据库用户|对用户的 IMPERSONATE 权限、db_securityadmin 固定数据库角色的成员身份、db_owner 固定数据库角色的成员身份或 sysadmin 固定服务器角色的成员身份。|  
|映射到 Windows 组的数据库用户|Windows 组的成员身份、db_securityadmin 固定数据库角色的成员身份、db_owner 固定数据库角色的成员身份或 sysadmin 固定服务器角色的成员身份。|  
|映射到证书的数据库用户|db_securityadmin 固定数据库角色的成员身份、db_owner 固定数据库角色的成员身份或 sysadmin 固定服务器角色的成员身份。|  
|映射到非对称密钥的数据库用户|Db_securityadminfixed 数据库角色的成员身份，成员资格中 db_owner 固定数据库角色或成员身份中 sysadmin 固定的服务器角色。|  
|未映射到任何服务器主体的数据库用户|对用户的 IMPERSONATE 权限、db_securityadmin 固定数据库角色的成员身份、db_owner 固定数据库角色的成员身份或 sysadmin 固定服务器角色的成员身份。|  
|数据库角色|对具有 ALTER 权限角色、 db_securityadminfixed 数据库角色的成员身份、 db_owner 固定的数据库角色中的成员身份或 sysadmin 固定的服务器角色的成员身份。|  
|应用程序角色|对角色的 ALTER 权限、db_securityadmin 固定数据库角色的成员身份、db_owner 固定数据库角色的成员身份或 sysadmin 固定服务器角色的成员身份。|  
  
 对某安全对象具有 CONTROL 权限的主体可以授予对该安全对象的权限。  
  
 将某一数据库的 CONTROL 权限授予用户（例如，db_owner 固定数据库角色的成员）后，该用户就可授予对该数据库中任何一个安全对象的任意权限。  
  
## <a name="examples"></a>示例  
  
### <a name="a-granting-control-permission-on-a-user-to-another-user"></a>A. 将对某个用户的 CONTROL 权限授予另一个用户  
 以下示例将对 `CONTROL` 用户 `AdventureWorks2012` 的 `Wanida` 权限授予用户 `RolandX`。  
  
```  
GRANT CONTROL ON USER::Wanida TO RolandX;  
GO  
```  
  
### <a name="b-granting-view-definition-permission-on-a-role-to-a-user-with-grant-option"></a>B. 使用 GRANT OPTION 将对角色的 VIEW DEFINITION 权限授予用户  
 以下示例使用 `VIEW DEFINITION`，将对 `AdventureWorks2012` 角色 `SammamishParking` 的 `GRANT OPTION` 权限授予数据库用户 `JinghaoLiu`。  
  
```  
GRANT VIEW DEFINITION ON ROLE::SammamishParking   
    TO JinghaoLiu WITH GRANT OPTION;  
GO  
```  
  
### <a name="c-granting-impersonate-permission-on-a-user-to-an-application-role"></a>C. 将对用户的 IMPERSONATE 权限授予应用程序角色  
 以下示例将对用户 `IMPERSONATE` 的 `HamithaL` 权限授予 `AdventureWorks2012` 应用程序角色 `AccountsPayable17`。  
  
**适用于**:[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]通过[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]， [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)]。  
  
```  
GRANT IMPERSONATE ON USER::HamithaL TO AccountsPayable17;  
GO    
```  
  
## <a name="see-also"></a>另请参阅  
 [DENY 数据库主体权限 &#40;Transact SQL &#41;](../../t-sql/statements/deny-database-principal-permissions-transact-sql.md)   
 [REVOKE 数据库主体权限 &#40;Transact SQL &#41;](../../t-sql/statements/revoke-database-principal-permissions-transact-sql.md)   
 [sys.database_principals (Transact-SQL)](../../relational-databases/system-catalog-views/sys-database-principals-transact-sql.md)   
 [sys.database_permissions &#40;Transact SQL &#41;](../../relational-databases/system-catalog-views/sys-database-permissions-transact-sql.md)   
 [CREATE USER (Transact-SQL)](../../t-sql/statements/create-user-transact-sql.md)   
 [创建应用程序角色 &#40;Transact SQL &#41;](../../t-sql/statements/create-application-role-transact-sql.md)   
 [创建角色 &#40;Transact SQL &#41;](../../t-sql/statements/create-role-transact-sql.md)   
 [GRANT (Transact-SQL)](../../t-sql/statements/grant-transact-sql.md)   
 [权限（数据库引擎）](../../relational-databases/security/permissions-database-engine.md)   
 [主体（数据库引擎）](../../relational-databases/security/authentication-access/principals-database-engine.md)  
  
  
