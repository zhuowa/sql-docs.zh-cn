---
title: 安装 SQL Server 2016 R Services （数据库） |Microsoft 文档
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 86263158581b92af42a7ad1ce9b538b2c1cdbfa7
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/16/2018
---
# <a name="install-sql-server-2016-r-services-in-database"></a>安装 SQL Server 2016 R Services (In-Database) 
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

此文章介绍了如何安装和配置**SQL Server 2016 R Services （数据库）**。 如果你有 SQL Server 2016，安装此功能以启用 SQL Server 中的 R 代码的执行。

## <a name="bkmk_prereqs"> </a> 预安装清单

+ 如果你想要安装 R Services，SQL Server 2016 安装程序是必需的。 如果你使用的 SQL Server 2017 安装媒体，你应安装[SQL Server 自 2017 年 1 机器学习 Services （数据库）](sql-machine-learning-services-windows-install.md)来获取该版本的 SQL Server 的 R 集成。

+ 数据库引擎实例是必需的。 无法安装仅 R，虽然将其添加到现有实例的以增量方式。

+ 不在故障转移群集上安装 R Services。 隔离 R 进程使用的安全机制不与 Windows Server 故障转移群集环境兼容。

+ 不要在域控制器上安装 R 服务。 安装程序的 R Services 部分将会失败。

+ 请不要安装**共享功能** > **R Server （独立）**同一台计算机上运行数据库中实例。 

+ 因为 SQL Server 实例使用的开放源代码 R 和 Anaconda 分发版各自副本可能会与其他版本的 R 和 Python 的通过并行安装。 但是，运行 SQL Server 外部 SQL Server 计算机使用 R 和 Python 的代码可能导致各种问题：
    
  + 你使用不同的库和不同的可执行文件，并获取不同的结果，不是你在 SQL Server 中运行时执行的操作。
  + 不能由 SQL Server，从而导致资源争用管理外部库中运行的 R 和 Python 脚本。
  
如果你使用任何早期版本的 Revolution Analytics 开发环境或 RevoScaleR 包中，或者如果你安装 SQL Server 2016 的所有预发行版本，你必须卸载它们。 不支持运行 RevoScaleR 和其他专有的包的较旧和较新版本。 正在删除以前版本的帮助，请参阅[升级和安装适用的 SQL Server 机器学习服务的常见问题](../r/upgrade-and-installation-faq-sql-server-r-services.md)。

> [!IMPORTANT]
> 安装程序完成后，请务必完成本文中所述的其他后配置步骤。 这些步骤包括启用 SQL Server 以使用外部脚本和添加 SQL Server 以你的名义运行 R 作业所需的帐户。 配置更改通常需要重新启动实例或重新启动快速启动板服务。

## <a name="get-the-installation-media"></a>获取安装介质

[!INCLUDE[GetInstallationMedia](../../includes/getssmedia.md)]

 ###  <a name="bkmk_ga_instalpatch"></a> 安装修补程序要求 

Microsoft 已发现特定版本的 Microsoft VC++ 2013 运行时二进制文件存在问题，这些二进制文件是作为 SQL Server 系统必备进行安装的。 如果未安装适用于该 VC 运行时二进制文件的更新，则在某些情况下 SQL Server 可能会遇到稳定性问题。 在安装 SQL Server 之前，请按照 [SQL Server 发行说明](../../sql-server/sql-server-2016-release-notes.md#bkmk_ga_instalpatch)中的说明来确定你的电脑是否需要 VC 运行时二进制文件的修补程序。  

## <a name="bkmk2016top"></a>运行安装程序

对于本地安装，必须以管理员身份运行安装程序。 如果从远程共享安装 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，则必须使用对远程共享具有读取和执行权限的域帐户。

1. 启动 SQL Server 2016 安装向导。

2. 上**安装**选项卡上，选择**新的 SQL Server 独立安装或向现有安装添加功能**。
    
   ![安装 R Services （数据库）](media/2016-setup-installation-rsvcs.png "带有 R Services 启动数据库引擎的安装")
   
3. 上**功能选择**页上，选择以下选项：

   - 选择**数据库引擎服务**。 数据库引擎使用机器学习每个实例中需要。
   - 选择**R Services （数据库）**。 安装。 数据库中使用的支持
    
     ![R Services 功能选择](media/2016setup-rsvcs-features.png "选择对于 R 服务数据库中的这些功能")

    > [!IMPORTANT]
    > 确实在同一时间安装 R Server 和 R 服务。 通常，你将安装 R Server （独立） 创建环境，数据科研人员或开发人员用来连接到 SQL Server 和部署 R 解决方案。 因此，不需要在同一台计算机上安装这两个组件。

4.  上**同意安装 Microsoft R Open**页上，单击**接受**。
  
    此许可协议需要下载 Microsoft R Open，其中包括的开放源代码 R 基程序包和工具，以及增强的 R 包和 Microsoft R 开发团队的连接提供商的分布。
  
5. 已接受许可协议后，没有是短暂的暂停准备安装。 单击**下一步**按钮变为可用时。

6. 上**已准备好安装**页上，验证以下各项都包括在内，然后选择**安装**。

   + 数据库引擎服务
   + R Services（数据库内）

    记下的路径下的文件夹位置`..\Setup Bootstrap\Log`存储配置文件。 安装程序完成后，你可以查看摘要文件中的已安装的组件。

7. 安装完成后，重新启动计算机。

##  <a name="bkmk_enableFeature"></a>启用外部脚本执行

1. 打开 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]。 

    > [!TIP]
    > 你可以下载并安装在此页中的相应版本：[下载 SQL Server Management Studio (SSMS)](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms)。
    > 
    > 你还可以试用的预览版本[SQL 操作 Studio](https://docs.microsoft.com/sql/sql-operations-studio/what-is)，它支持管理任务和针对 SQL Server 查询。
  
2. 连接到安装机器学习服务的实例，单击**新查询**来打开查询窗口中，并运行以下命令：

   ```SQL
   sp_configure
   ```
    属性 `external scripts enabled` 的值目前应为 **0**。 这是因为默认情况下关闭功能。 你可以运行 R 或 Python 脚本之前，必须由管理员显式启用该功能。
     
3. 若要启用外部脚本功能，请运行以下语句：
  
    ```SQL
    EXEC sp_configure  'external scripts enabled', 1
    RECONFIGURE WITH OVERRIDE
    ```
  
## <a name="restart-the-service"></a>重新启动服务。

安装完成后，重新启动数据库引擎，然后继续到下一行，启用脚本执行。

此外会自动重新启动 ervice 重启相关[!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)]服务。

你可以重新启动服务使用右击**重新启动**实例在 SSMS 中，或通过使用命令**服务**面板在 Control Panel 中，或使用[SQL Server 配置管理器](../../relational-databases/sql-server-configuration-manager.md).

## <a name="verify-installation"></a>验证安装

使用以下步骤来验证用于启动外部脚本的所有组件正在都运行。

1. 在 SQL Server Management Studio，打开新查询窗口中，并运行以下命令：
    
    ```SQL
    EXEC sp_configure  'external scripts enabled'
    ```

    **run_value** 现在应已设置为 1。

2. 打开**服务**面板或 SQL Server 配置管理器，并验证**SQL Server 快速启动板服务**正在运行。 你应具有一个包含 R 每个数据库引擎实例的服务或 Python 安装。 如果未运行，请重新启动服务。 有关详细信息，请参阅[组件来支持 Python 集成](../python/new-components-in-sql-server-to-support-python-integration.md)。

7. 如果正在快速启动板，你应能够运行简单的 R 来验证外部脚本的运行时可以与 SQL Server 通信。 

    打开一个新**查询**中的窗口[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]，然后运行以下脚本：
    
    ```SQL
    EXEC sp_execute_external_script  @language =N'R',
    @script=N'
    OutputDataSet <- InputDataSet;
    ',
    @input_data_1 =N'SELECT 1 AS hello'
    WITH RESULT SETS (([hello] int not null));
    GO
    ```

    该脚本时，会稍有若要运行，第一次请加载外部脚本运行。 结果应类似如下内容：

    | Hello |
    |----|
    | 1|

## <a name="bkmk_FollowUp"></a> 附加配置

如果外部脚本执行验证步骤成功，你可以从 SQL Server Management Studio、 Visual Studio 代码或可以向服务器发送的 T-SQL 语句的任何其他客户端运行 Python 命令。

如果你在运行命令时收到错误，，查看此部分中的其他配置步骤。 你可能需要对服务或数据库进行其他适当的配置。

需要其他更改的常见方案包括：

* [配置 Windows 防火墙以便进行入站连接](../../database-engine/configure-windows/configure-a-windows-firewall-for-database-engine-access.md)
* [启用其他网络协议](../../database-engine/configure-windows/enable-or-disable-a-server-network-protocol.md)
* [启用远程连接](../../database-engine/configure-windows/configure-the-remote-access-server-configuration-option.md)
* [将内置权限扩展到远程用户](#bkmk_configureAccounts)
* [授予的权限来运行外部脚本](#bkmk_AllowLogon)
* [授予对单个数据库访问权限](#permissions-db)

> [!NOTE]
> 并非所有列出的更改是必需的且无可能需要。 要求取决于安全架构，安装 SQL Server，以及希望用户连接到数据库和运行外部脚本的位置。 其他故障排除提示可在此处找到：[升级和安装常见问题解答](../r/upgrade-and-installation-faq-sql-server-r-services.md)

### <a name="bkmk_configureAccounts"></a>启用快速启动板帐户组的隐式身份验证

在安装期间，某些新的 Windows 用户帐户创建为运行下的安全令牌的任务[!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)]服务。 当用户从外部客户端，发送 R 脚本时[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]激活可用的工作帐户、 将其映射到的调用用户的标识和运行 R 脚本代表用户。 这一新的数据库引擎服务支持调用的外部脚本的安全执行*默示身份验证*。

你可以在 Windows 用户组中查看这些帐户**SQLRUserGroup**。 默认情况下，被创建 20 工作人员帐户，这通常是绰绰有余用于运行 R 作业。

但是，如果你需要从远程数据科学客户端运行 R 脚本，且正在使用 Windows 身份验证，你必须授予这些辅助帐户权限登录到[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]代表你的实例。

1. 在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]的“对象资源管理器”中，展开“安全性” ，右键单击“登录名” ，然后选择“新建登录名” 。
2. 在**登录名-新建**对话框中，选择**搜索**。
3. 选择**对象类型**和**组**复选框，并清除所有其他复选框。
4. 单击**高级**，验证，要搜索的位置为当前计算机，然后单击**立即查找**。
5. 直到找到一个开头的服务器上的组帐户的列表中滚动`SQLRUserGroup`。
    
    + 与的快速启动板服务关联组的名称_默认实例_只始终是**SQLRUserGroup**。 选择此帐户仅对于默认实例。
    + 如果你使用_命名实例_，实例名称追加到默认名称， `SQLRUserGroup`。 因此，如果你的实例名为"MLTEST"，此实例的默认用户组名称将**SQLRUserGroupMLTest**。
5. 单击**确定**以关闭高级的搜索对话框中，并验证你已选择正确的帐户的实例。 每个实例可以使用其自己的快速启动板服务和为该服务创建的组。
6. 单击**确定**一次以关闭**选择用户或组**对话框。
7. 在**登录名-新建**对话框中，单击**确定**。 默认情况下，将登录名分配到 **公共** 角色，且有权连接到数据库引擎。

### <a name="bkmk_AllowLogon"></a>向用户授予的权限来运行外部脚本

> [!NOTE]
> 如果在 SQL Server 计算上下文中运行 R 脚本使用 SQL 登录名，则不需要此步骤。

如果你安装[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]在您自己的实例，你通常将执行脚本以管理员身份，或者至少为数据库的所有者，并因此具有隐式权限各种操作，该数据库，并且能够安装新包中的所有数据根据需要。

但是，在企业方案中，大多数用户来说，包括通过使用 SQL 登录名访问数据库的用户不具有这种提升的权限。 因此，对于每个用户都将运行 R 脚本，必须授予用户权限来将在其中外部脚本使用在每个数据库运行脚本。

```SQL
USE <database_name>
GO
GRANT EXECUTE ANY EXTERNAL SCRIPT  TO [UserName]
```

> [!TIP]
> 需要有关安装程序的帮助？ 不确定是否已执行所有步骤？ 使用这些自定义报表以检查安装状态和运行其他步骤。 
> 
> [监视使用自定义报表的机器学习服务](../r/monitor-r-services-using-custom-reports-in-management-studio.md)。

### <a name="permissions-db"></a> 授予用户读取、 写入或对数据库的 DDL 权限

用于运行 R 的用户帐户可能需要从其他数据库，读取数据创建新表来存储结果，并将数据写入到表。 因此，对于每个用户都将执行 R 脚本，请确保用户对数据库具有适当的权限： *db_datareader*， *db_datawriter*，或*db_ddladmin*.

例如，以下 [!INCLUDE[tsql](../../includes/tsql-md.md)] 语句为 SQL 登录名 *MySQLLogin* 提供在 *RSamples* 数据库中运行 T-SQL 查询的权限。 若要运行此语句，SQL 登录名必须已经存在于服务器的安全上下文中。

```SQL
USE RSamples
GO
EXEC sp_addrolemember 'db_datareader', 'MySQLLogin'
```

有关每个角色中包含的权限的详细信息，请参阅[数据库级角色](../../relational-databases/security/authentication-access/database-level-roles.md)。


### <a name="create-an-odbc-data-source-for-the-instance-on-your-data-science-client"></a>为数据科学客户端上的实例创建 ODBC 数据源

如果你的数据科学客户端计算机上创建 R 解决方案，并且需要通过使用 SQL Server 计算机作为计算上下文来运行代码，你可以使用 SQL 登录名或集成的 Windows 身份验证。

* 对于 SQL 登录名：确保该登录名对要读取数据的数据库拥有相应的权限。 你可以通过添加实现*连接到*和*选择*权限，或通过添加登录到*db_datareader*角色。 对于需要创建对象的登录名，添加*DDL_admin*权限。 必须将数据保存到表的登录名添加到的登录名为*db_datawriter*角色。

* 对于 Windows 身份验证： 你可能需要指定实例名称和其他连接信息的数据科学客户端上配置 ODBC 数据源。 有关详细信息，请参阅[ODBC 数据源管理器](https://docs.microsoft.com/sql/odbc/admin/odbc-data-source-administrator)。

## <a name="suggested-optimizations"></a>建议的优化

现在，你已使用的所有内容，你可能还想要优化的服务器以支持机器学习中，或安装预先训练的模型。

### <a name="add-more-worker-accounts"></a>添加更多的辅助角色帐户

如果您认为可能很大程度，使用 R，或者如果希望多个用户同时处于正在运行的脚本，则可以增加分配给快速启动板服务的工作帐户数。 有关详细信息，请参阅[修改 SQL Server 机器学习服务的用户帐户池](../r/modify-the-user-account-pool-for-sql-server-r-services.md)。

### <a name="bkmk_optimize"></a>优化外部脚本执行的服务器

默认设置[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]安装程序旨在优化各种受数据库引擎，这可能包括提取、 转换和加载 (ETL) 过程，reporting、 审核的服务的服务器的余额和应用程序使用[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]数据。 因此，在默认设置，你可能会发现以及有时限制或限制，尤其是在内存密集型操作的机器学习的资源。

若要确保机学习作业优先级别，并相应地资源，我们建议你使用 SQL Server 资源调控器来配置外部资源池。 你可能还想要更改分配给的内存量[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]数据库引擎，或增加下运行的帐户数[!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)]服务。

- 若要配置用于管理外部资源的资源池，请参阅[创建外部资源池](../../t-sql/statements/create-external-resource-pool-transact-sql.md)。
  
- 若要更改数据库保留的内存量，请参阅[服务器内存配置选项](../../database-engine/configure-windows/server-memory-server-configuration-options.md)。
  
- 若要更改可以通过启动的 R 帐户数[!INCLUDE[rsql_launchpad](../../includes/rsql-launchpad-md.md)]，请参阅[修改用户帐户池的机器学习](../r/modify-the-user-account-pool-for-sql-server-r-services.md)。

如果你使用的标准版并没有资源调控器，则可以使用动态管理视图 (Dmv) 和扩展事件，以及监视，以帮助管理。 通过使用服务器资源的 Windows 事件有关详细信息，请参阅[监视和管理 R Services](../r/managing-and-monitoring-r-solutions.md)。

### <a name="install-additional-r-packages"></a>安装其他 R 包

为 SQL Server 创建 R 解决方案可以调用基本 R 函数，从装有 SQL Server 和第三方 R 包的开放源代码 R SQL Server 安装的版本兼容的 properietary packes 函数。

要通过 SQL Server 使用的包必须安装在实例使用的默认库中。 如果你有 R 的单独安装的计算机上，或包安装到用户库，你将无法使用从 T-SQL 的这些包。

安装和管理 R 包的过程中是不同 SQL Server 2016 和 SQL Server 自 2017 年。 在 SQL Server 2016 中，数据库管理员必须安装用户需要的 R 包。 在 SQL Server 自 2017 年，可以将用户组设置为共享上的每个数据库级别，包或配置数据库角色，以使用户能够安装其自己的包。 有关详细信息，请参阅[包管理](../r/r-package-management-for-sql-server-r-services.md)。


## <a name="get-help"></a>获取帮助

需要安装或升级的帮助？ 常见的问题和已知的问题的答案，请参阅以下文章：

* [升级和安装常见问题-机器学习服务](../r/upgrade-and-installation-faq-sql-server-r-services.md)

若要检查实例的安装状态并修复常见的问题，请尝试这些自定义报表。

* [SQL Server R Services 的自定义报表](../r/monitor-r-services-using-custom-reports-in-management-studio.md)

## <a name="next-steps"></a>后续步骤

R 开发人员可以开始使用一些简单的示例，并了解 R 如何使用 SQL Server 的基础知识。 下一步，请参阅以下链接：

+ [教程： 在 T-SQL 中运行 R](../tutorials/rtsql-using-r-code-in-transact-sql-quickstart.md)
+ [针对 R 开发人员的教程： 在数据库中分析](../tutorials/sqldev-in-database-r-for-sql-developers.md)

若要查看的机器学习基于实际方案的示例，请参阅[机器学习教程](../tutorials/machine-learning-services-tutorials.md)。


