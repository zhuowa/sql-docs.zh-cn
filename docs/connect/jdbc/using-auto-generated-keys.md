---
title: "使用自动生成密钥 |Microsoft 文档"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 55a062c7-45ce-40e3-9a6f-4a0f4da4e2a6
caps.latest.revision: 18
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: ff2df18e392d8c72e1c92aea7d9908d72496b3aa
ms.contentlocale: zh-cn
ms.lasthandoff: 09/09/2017

---
# <a name="using-auto-generated-keys"></a>使用自动生成的键
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)]支持可选的 JDBC 3.0 Api 检索自动生成行标识符。 这项功能的主要意义在于，为更新数据库表的应用程序提供获得 IDENTITY 值的方法，从而无需执行查询以及对服务器进行再次往返通信。  
  
 因为[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]标识符不支持伪列，则必须使用自动生成的关键功能的更新必须对包含标识列的表执行操作。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]允许只有一个标识列每个表。 结果集返回[getGeneratedKeys](../../connect/jdbc/reference/getgeneratedkeys-method-sqlserverstatement.md)方法[SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md)类将具有只有一个列，其中 GENERATED_KEYS 返回的列名称。 如果对不包含 IDENTITY 列的表请求生成的键，则 JDBC 驱动程序将返回空结果集。  
  
 例如，创建下的表中[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)]示例数据库：  
  
```  
CREATE TABLE TestTable   
   (Col1 int IDENTITY,   
    Col2 varchar(50),   
    Col3 int);  
```  
  
 在下面的示例中，与的开放连接[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)]示例数据库中传递给函数、 构造 SQL 语句这会将数据添加到表中，然后运行该语句并显示的标识列值。  
  
 [!code[JDBC#UsingAutoGeneratedKeys1](../../connect/jdbc/codesnippet/Java/using-auto-generated-keys_1.java)]  
  
## <a name="see-also"></a>另请参阅  
 [语句使用 JDBC 驱动程序](../../connect/jdbc/using-statements-with-the-jdbc-driver.md)  
  
  