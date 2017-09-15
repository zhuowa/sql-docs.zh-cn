---
title: "定义 Transact-SQL 作业步骤选项 | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Transact-SQL job step
- job steps [Transact-SQL]
- SQL Server Agent jobs, Transact-SQL step
ms.assetid: b2a47057-f6fb-432b-a7b6-5d61f33a5d9c
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 4bf48de41b0d89e7b2edc063010bf20826463b22
ms.contentlocale: zh-cn
ms.lasthandoff: 06/22/2017

---
# <a name="define-transact-sql-job-step-options"></a>Define Transact-SQL Job Step Options
本主题介绍了如何使用 [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] 中定义 [!INCLUDE[tsql](../../includes/tsql_md.md)]  [!INCLUDE[ssCurrent](../../includes/sscurrent_md.md)] 代理 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] 作业步骤的选项。  
  
**本主题内容**  
  
-   **开始之前：**  
  
    [Security](#Security)  
  
-   **若要定义 Transact-SQL 作业步骤选项，请使用：** ，  
  
    [SQL Server Management Studio](#SSMS)  
  
    [SQL Server 管理对象](#SMO)  
  
## <a name="BeforeYouBegin"></a>开始之前  
  
### <a name="Security"></a>Security  
有关详细信息，请参阅 [Implement SQL Server Agent Security](../../ssms/agent/implement-sql-server-agent-security.md)。  
  
## <a name="SSMS"></a>使用 SQL Server Management Studio  
  
#### <a name="to-define-transact-sql-job-step-options"></a>定义 Transact-SQL 作业步骤选项  
  
1.  在 **对象资源管理器**中，展开 **“SQL Server 代理”**，展开 **“作业”**，右键单击要编辑的作业，然后单击 **“属性”**。  
  
2.  单击 **“步骤”** 页，单击一个作业步骤，再单击 **“编辑”**。  
  
3.  在 **“作业步骤属性”** 对话框上，确认作业类型为 **“Transact-SQL 脚本(TSQL)”**，然后选择 **“高级”** 页。  
  
4.  如果作业成功，请从 **“成功时要执行的操作”** 列表中进行选择，指定要采取的操作。  
  
5.  在 **“重试次数”** 框中输入 0 到 9999 之间的一个数字，指定重试的次数。  
  
6.  在 **“重试间隔”** 框中输入 0 到 9999 的数字，指定重试的时间间隔。  
  
7.  如果作业失败，请从 **“失败时要执行的操作”** 列表中进行选择，指定要采取的操作。  
  
8.  如果作业是一个 [!INCLUDE[tsql](../../includes/tsql_md.md)] 脚本，则可以从下列选项中进行选择：  
  
    -   输入 **输出文件**的名称。 默认情况下，每次执行作业步骤时都覆盖该文件。 如果不希望覆盖输出文件，请选中 **“将输出追加到现有文件”**。 只有 **sysadmin** 固定服务器角色的成员才能设置此选项。 请注意， [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] 不允许用户查看文件系统中的任意文件。因此您不能使用 [!INCLUDE[ssManStudio](../../includes/ssmanstudio_md.md)] 查看写入文件系统的作业步骤日志。  
  
    -   如果希望将作业步骤记录到一个数据库表中，请选中 **“记录到表”** 。 默认情况下，每次执行作业步骤时都覆盖该表的内容。 如果不希望覆盖表内容，则请选中 **“将输出追加到表中的现有条目”**。 在执行作业步骤后，您可以通过单击 **“查看”**来查看此表的内容。  
  
    -   如果希望将输出包括在步骤的历史记录中，请选中 **“在历史记录中包含步骤输出”** 。 仅当没有错误时，才会显示输出结果。 此外，输出可能会被截断。  
  
9. 如果您是 **sysadmin** 固定服务器角色的成员，并且希望以其他 SQL 登录身份运行此作业步骤，请从 **“作为以下用户运行”** 列表中选择 SQL 登录名。  
  
## <a name="SMO"></a>使用 SQL Server 管理对象  
**定义 Transact-SQL 作业步骤选项**  
  
通过使用所选编程语言（如 Visual Basic、Visual C# 或 PowerShell）来使用 **JobStep** 类。  
  
