---
title: Microsoft SQL 和 GDPR 要求 | Microsoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: security
ms.tgt_pltfrm: ''
ms.topic: conceptual
caps.latest.revision: 2
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: e5144b4ec829f57b77ae92fb3d55a724bb08964b
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="guide-to-enhancing-privacy-and-addressing-gdpr-requirements-with-the-microsoft-sql-platform"></a>增强隐私和使用 Microsoft SQL 平台应对 GDPR 要求的指南
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

## <a name="summary"></a>“摘要”
欧盟的一项隐私法律将于 2018 年 5 月 25 日生效，其中针对隐私权、安全性和合规性设定了新的全球禁令。 《一般数据保护条例》(GDPR) 主要用于保护个人隐私权和促进此权利的行使，其中设定了严格的全球隐私要求，旨在监管个人数据的管理和保护方式，同时尊重个人选择。 

Microsoft SQL 客户需遵守 GDPR，无论他们管理基于云的数据库还是本地数据库或两者兼有，都需要确保根据 GDPR 原则对其数据库系统中的合格数据进行合理处理和保护。 这意味着，许多客户将需要评审或修改其数据库管理和数据处理过程，尤其要重点关注 GDPR 中所规定的数据处理安全性。

基于 Microsoft SQL 的技术提供了许多内置安全功能，可帮助降低数据的风险，同时在数据库级别及更高级别改进对数据的保护和可管理性。 本指南将检验这些功能，并分享一些 Microsoft 自己的方法，使用 Microsoft SQL 实现 GDPR 的数据隐私目标。
   
  
**作者：**Ronit Reger

**技术审阅人员：**Conor Cunningham、Joachim Hammer、Shai Kariv、Julie Koesmarno、Alice Kupcik、Ron Matchoro、Gilad Mittelman、Dan Rediske、Tomer Weisberg 
  
**发布时间：**2017 年 5 月  
  
**适用于：**SQL Server（所有版本）、Azure SQL 数据库、Azure SQL 数据仓库、Analytics Platform System 
  
若要查看该文档，请下载[关于如何使用 Microsoft SQL 平台增强隐私和应对 GDPR 要求的指南](http://download.microsoft.com/download/4/9/4/4948194B-A613-49ED-90A5-5144313549AB/microsoft-sql-and-the-gdpr.pdf)文档。   
