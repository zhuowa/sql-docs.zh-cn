---
title: 连接库和框架 |Microsoft 文档
description: 列出客户端应用程序可用于从各种语言连接到 Microsoft SQL Server 在本地运行或在云中，在 Linux、 Windows 或 Docker 以及 Azure SQL 数据库和 Azure SQL 数据仓库的连接驱动程序。
author: rothja
ms.author: jroth
manager: craigg
ms.date: 03/17/2017
ms.topic: article
ms.prod: sql
ms.prod_service: database-engine
ms.component: ''
ms.suite: sql
ms.custom: sql-linux
ms.technology: database-engine
ms.assetid: 80efe5ff-09ba-48a0-ac93-a91d62cff47c
ms.openlocfilehash: 46a83abcd74b9e4ae16bb5e97c7593f428b054a2
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="connectivity-libraries-and-frameworks-for-microsoft-sql-server"></a>适用于 Microsoft SQL Server 的连接库和框架

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

签出[入门教程](http://aka.ms/sqldev)快速开始使用编程语言，例如 C#、 Java、 Node.js、 PHP 和 Python 和生成在 macOS 上使用 Linux 或 Windows 或 Docker 上的 SQL Server 的应用程序。

下表列出了连接库或*驱动程序*客户端应用程序可以使用不同的语言来连接到并使用 Microsoft SQL Server 在本地运行或在云中，在 Linux、 Windows 或 Docker 上和此外为 Azure SQL 数据库和 Azure SQL 数据仓库。 

| 语言 | 平台 | 其他资源 | 下载 | 开始操作 |
| :-- | :-- | :-- | :-- | :-- |
| C# | Windows、Linux、macOS | [用于 SQL Server 的 Microsoft ADO.NET](http://msdn.microsoft.com/library/mt657768.aspx) | [下载](https://msdn.microsoft.com/vstudio/aa496123.aspx) | [要开始](https://www.microsoft.com/en-us/sql-server/developer-get-started/csharp/ubuntu)
| Java | Windows、Linux、macOS | [Microsoft JDBC Driver for SQL Server](http://msdn.microsoft.com/library/mt484311.aspx) | [下载](http://go.microsoft.com/fwlink/?LinkId=245496) |  [要开始](https://www.microsoft.com/en-us/sql-server/developer-get-started/java/ubuntu)
| PHP | Windows、Linux、macOS| [SQL Server 的 PHP SQL 驱动程序](http://msdn.microsoft.com/library/dn865013.aspx) | 操作系统： <br/> \* [Windows](https://www.microsoft.com/download/details.aspx?id=20098) <br/> \* [Linux](https://github.com/Microsoft/msphpsql/tree/dev#install-unix) <br/> \* [macOS](https://github.com/Microsoft/msphpsql/tree/dev#install-unix) |  [要开始](https://www.microsoft.com/en-us/sql-server/developer-get-started/php/ubuntu)
| Node.js | Windows、Linux、macOS | [适用于 SQL Server 的 Node.js 驱动程序](../connect/node-js/node-js-driver-for-sql-server.md) |  [要开始](https://www.microsoft.com/en-us/sql-server/developer-get-started/node/ubuntu)
| Python | Windows、Linux、macOS | [Python SQL 驱动程序](../connect/python/python-driver-for-sql-server.md) <br/> \* [pyodbc](http://msdn.microsoft.com/library/mt763257.aspx) |  [要开始](https://www.microsoft.com/en-us/sql-server/developer-get-started/python/ubuntu)
| Ruby | Windows、Linux、macOS | [适用于 SQL Server 的 Ruby 驱动程序](../connect/ruby/ruby-driver-for-sql-server.md) | [要开始](https://www.microsoft.com/en-us/sql-server/developer-get-started/ruby/ubuntu)
| C++ | Windows、Linux、macOS | [Microsoft ODBC Driver for SQL Server](https://msdn.microsoft.com/en-us/library/mt654048(v=sql.1).aspx) | [下载](https://msdn.microsoft.com/en-us/library/mt654048(v=sql.1).aspx) |  

下表列出的对象关系映射 (ORM) 框架和 web 框架的客户端应用程序可以使用与 Microsoft SQL Server 在本地运行或在云中，在 Linux、 Windows 或 Docker 和 Azure SQL 数据库的几个示例和Azure SQL 数据仓库。 

| 语言 | 平台 | ORM(s) |
| :-- | :-- | :-- |
| C# | Windows、Linux、macOS | [实体框架](https://docs.microsoft.com/en-us/ef)<br>[实体框架核心](https://docs.microsoft.com/en-us/ef/core/index) |
| Java | Windows、Linux、macOS |[休眠 ORM](http://hibernate.org/orm)|
| PHP | Windows、Linux | [Laravel （最强大的）](https://laravel.com/docs/5.0/eloquent) |
| Node.js | Windows、Linux、macOS | [Sequelize ORM](http://docs.sequelizejs.com) |
| Python | Windows、Linux、macOS |[Django](https://www.djangoproject.com/) |
| Ruby | Windows、Linux、macOS | [Ruby on Rails](http://rubyonrails.org/) |

## <a name="related-links"></a>相关链接
- [SQL Server 驱动程序](http://msdn.microsoft.com/library/mt654049.aspx)用于从客户端应用程序连接
