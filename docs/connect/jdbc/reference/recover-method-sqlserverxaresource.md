---
title: 恢复方法 (SQLServerXAResource) |Microsoft 文档
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
apiname:
- SQLServerXAResource.recover
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 840ecfcf-0dd3-4b7b-976f-dc9a96cd1464
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d2e30fa3b1fc9d5ab419cd0f8f8b2b7bbcf018b2
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="recover-method-sqlserverxaresource"></a>recover 方法 (SQLServerXAResource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  从资源管理器获取准备好的事务分支的列表。  
  
## <a name="syntax"></a>语法  
  
```  
  
public javax.transaction.xa.Xid[] recover(int flags)  
```  
  
#### <a name="parameters"></a>Parameters  
 *flag*  
  
 **Int**值，可以采用以下值之一： XAResource.TMSTARTRSCAN 或 XAResource.TMENDRSCAN 或 XAResource.TMNOFLAGS 或 XAResource.TMSTARTTRSCAN |XAResource.TMENDRSCAN。  
  
## <a name="return-value"></a>返回值  
 Xid 对象。  
  
## <a name="exceptions"></a>异常  
 javax.transaction.xa.XAException  
  
## <a name="remarks"></a>注释  
 此恢复方法被指定 javax.transaction.xa.XAResource 接口中的恢复方法。  
  
 如果参数**标志**不 XAResource.TMSTARTRSCAN |XAResource.TMENDRSCAN，恢复扫描必须处于正在进行中。  
  
## <a name="see-also"></a>另请参阅  
 [SQLServerXAResource 方法](../../../connect/jdbc/reference/sqlserverxaresource-methods.md)   
 [SQLServerXAResource 成员](../../../connect/jdbc/reference/sqlserverxaresource-members.md)   
 [SQLServerXAResource 类](../../../connect/jdbc/reference/sqlserverxaresource-class.md)  
  
  
