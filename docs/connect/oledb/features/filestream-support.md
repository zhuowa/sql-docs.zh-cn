---
title: FILESTREAM 支持 |Microsoft 文档
description: OLE DB 驱动程序中的 SQL Server 的 FILESTREAM 支持
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: oledb|features
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- FILESTREAM [SQL Server], OLE DB Driver for SQL Server
- OLE DB Driver for SQL Server [FILESTREAM support]
author: pmasl
ms.author: Pedro.Lopes
manager: craigg
ms.openlocfilehash: d9774e55a9366f99ad96fb5c2165abb3992f6e03
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="filestream-support"></a>FILESTREAM 支持
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

开头[!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)]，OLE DB 驱动程序的 SQL Server 支持增强的 FILESTREAM 功能。 有关示例，请参阅[Filestream 和 OLE DB](../../oledb/ole-db-how-to/filestream/filestream-and-ole-db.md)。  

FILESTREAM 允许通过 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 或通过直接访问 Windows 文件系统来存储和访问大型二进制值。 大型二进制值是大于 2 GB 的值。 有关增强 FILESTREAM 支持的详细信息，请参阅[FILESTREAM &#40;SQL Server&#41;](../../../relational-databases/blob/filestream-sql-server.md)。  
  
当打开数据库连接时， **@@TEXTSIZE** 将设置为-1 （"无限制"），默认情况下。  
  
还可以使用 Windows 文件系统 API 访问和更新 FILESTREAM 列。  
  
有关详细信息，请参阅[使用 OpenSqlFilestream 访问 FILESTREAM 数据](../../../relational-databases/blob/access-filestream-data-with-opensqlfilestream.md)  
  
## <a name="querying-for-filestream-columns"></a>查询 FILESTREAM 列  
OLE DB 中的架构行集不会报告某个列是否为 FILESTREAM 列。 在 OLE DB ITableDefinition 不能用于创建 FILESTREAM 列。    
  
若要创建 FILESTREAM 列或检测哪些现有列是 FILESTREAM 列，可以使用**is_filestream**列[sys.columns](../../../relational-databases/system-catalog-views/sys-columns-transact-sql.md)目录视图。  
  
以下是一个示例：  
  
```sql  
-- Create a table with a FILESTREAM column.  
CREATE TABLE Bob_01 (GuidCol1 uniqueidentifier ROWGUIDCOL NOT NULL UNIQUE DEFAULT NEWID(), IntCol2 int, varbinaryCol3 varbinary(max) FILESTREAM);  
  
-- Find FILESTREAM columns.  
SELECT name FROM sys.columns WHERE is_filestream=1;  
  
-- Determine whether a column is a FILESTREAM column.  
SELECT is_filestream FROM sys.columns WHERE name = 'varbinaryCol3' AND object_id IN (SELECT object_id FROM sys.tables WHERE name='Bob_01');  
```  
  
## <a name="down-level-compatibility"></a>下级兼容性  
如果你的客户端已经过编译使用 SQL Server 的 OLE DB 驱动程序，应用程序连接到[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)]通过[!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)])，然后**varbinary （max)** 行为会不兼容的行为通过引入[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]中本机客户端[!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]。 就是说，返回数据的最大大小将限制为不超过 2 GB。 更大的结果值的 2 GB，将发生截断，并且将返回"右侧的字符串数据的截断"警告。 
  
如果将数据类型兼容性设置为 80，则客户端行为将与下级客户端行为一致。  
  
使用 SQLOLEDB 或其他提供程序之前发布的客户端[!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]， **varbinary （max)** 将映射到映像。  
  
## <a name="comments"></a>注释
- 发送和接收**varbinary （max)** 大于 2 GB 的值，应用程序使用**DBTYPE_IUNKNOWN**中参数和结果绑定。 参数的提供程序必须调用 iunknown:: Queryinterface ISequentialStream 和返回 ISequentialStream 的结果。  

-  用于 OLE DB，检查相关为 ISequentialStream 值将通过放宽。 当*wType*是**DBTYPE_IUNKNOWN**中**DBBINDING**结构，检查长度可以是禁用通过省略**DBPART_LENGTH**从*dwPart*或通过设置数据的长度 (按偏移量*obLength*数据缓冲区中) 到 ~ 0。 在此情况下，提供程序将不检查值的长度，并且将请求和返回可通过流提供的所有数据。 这一更改将适用于所有大型对象 (LOB) 类型和 XML，但只在连接到 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)]（或更高版本）服务器时才适用。 这将为开发人员提供更高的灵活性，同时为现有应用程序和下级服务器维护一致性和向下兼容性。  此更改影响所有传输数据，主要 irowset:: Getdata、 ICommand::Execute 和 IRowsetFastLoad::InsertRow 的接口。
 

## <a name="see-also"></a>另请参阅  
 [适用于 SQL Server 的 OLE DB 驱动程序功能](../../oledb/features/oledb-driver-for-sql-server-features.md)  
  
  
