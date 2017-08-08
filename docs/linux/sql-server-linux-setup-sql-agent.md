---
title: "在 Linux 上安装 SQL Server 代理 |Microsoft 文档"
description: "本主题介绍如何在 Linux 上安装 SQL Server 代理。"
author: rothja
ms.author: jroth
manager: jhubbard
ms.date: 07/17/2017
ms.topic: article
ms.prod: sql-linux
ms.technology: database-engine
ms.assetid: 77f16adc-e6cb-4a57-82f3-7b9780369868
ms.translationtype: MT
ms.sourcegitcommit: ea75391663eb4d509c10fb785fcf321558ff0b6e
ms.openlocfilehash: 1f6f741a87a13e5b5bc8ba83741e86b065378bad
ms.contentlocale: zh-cn
ms.lasthandoff: 08/02/2017

---
# <a name="install-sql-server-agent-on-linux"></a>在 Linux 上安装 SQL Server 代理

以下步骤安装 SQL Server 代理 (**mssql server 代理**) 在 Linux 上。 [SQL Server 代理](https://docs.microsoft.com/sql/ssms/agent/sql-server-agent)运行计划的 SQL Server 作业。 对于此版本的 SQL Server 代理支持的功能的信息，请参阅[发行说明](sql-server-linux-release-notes.md)。

> [!NOTE]
> 之前先安装 SQL Server 代理[安装 SQL Server RC2 +](sql-server-linux-setup.md#platforms)。 这会将配置的密钥和安装时使用的存储库**mssql server 代理**包。

为以下平台安装 SQL Server 代理：

- [Red Hat Enterprise Linux](#RHEL)
- [Ubuntu](#ubuntu)
- [SUSE Linux Enterprise Server](#SLES)

## <a name="RHEL">在 RHEL 上安装</a>

使用以下步骤来安装**mssql server 代理**Red Hat Enterprise Linux 上。 

```bash
sudo yum install mssql-server-agent
sudo systemctl restart mssql-server
```

如果你已有**mssql server 代理**安装，你可以更新到最新版本使用以下命令：

```bash
sudo yum check-update
sudo yum update mssql-server-agent
sudo systemctl restart mssql-server
```

如果你需要的脱机安装，查找中的 SQL Server 代理包下载内容[发行说明](sql-server-linux-release-notes.md)。 然后，使用主题中所述的相同脱机安装步骤[安装 SQL Server](sql-server-linux-setup.md#offline)。

## <a name="ubuntu">在 Ubuntu 上安装</a>

使用以下步骤来安装**mssql server 代理**在 Ubuntu 上。 

```bash
sudo apt-get update 
sudo apt-get install mssql-server-agent
sudo systemctl restart mssql-server
```

如果你已有**mssql server 代理**安装，你可以更新到最新版本使用以下命令：

```bash
sudo apt-get update 
sudo apt-get install mssql-server-agent
sudo systemctl restart mssql-server
```

如果你需要的脱机安装，查找中的 SQL Server 代理包下载内容[发行说明](sql-server-linux-release-notes.md)。 然后，使用主题中所述的相同脱机安装步骤[安装 SQL Server](sql-server-linux-setup.md#offline)。

## <a name="SLES">在 SLES 上安装</a>

使用以下步骤来安装**mssql server 代理**SUSE Linux Enterprise Server 上。 

安装**mssql server 代理** 

```bash
sudo zypper install mssql-server-agent
sudo systemctl restart mssql-server
```

如果你已有**mssql server 代理**安装，你可以更新到最新版本使用以下命令：

```bash
sudo zypper refresh
sudo zypper update mssql-server-agent
sudo systemctl restart mssql-server
```

如果你需要的脱机安装，查找中的 SQL Server 代理包下载内容[发行说明](sql-server-linux-release-notes.md)。 然后，使用主题中所述的相同脱机安装步骤[安装 SQL Server](sql-server-linux-setup.md#offline)。

## <a name="next-steps"></a>后续步骤
有关如何使用 SQL Server 代理来创建、 计划和运行作业的详细信息，请参阅[在 Linux 上运行的 SQL Server 代理作业](sql-server-linux-run-sql-server-agent-job.md)。
