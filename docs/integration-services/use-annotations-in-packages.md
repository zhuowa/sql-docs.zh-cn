---
title: "在包中使用批注 | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "自行记录包"
  - "添加批注"
  - "批注 [Integration Services]"
ms.assetid: 48c8ed9a-b10d-490c-9ba7-4b77aa44e3dd
caps.latest.revision: 42
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 41
---
# 在包中使用批注
  [!INCLUDE[ssIS](../includes/ssis-md.md)] 设计器提供批注，利用它们可使包自文档化，且更易理解和维护。 可以将批注添加到 [!INCLUDE[ssIS](../includes/ssis-md.md)] 设计器的控制流、数据流和事件处理程序设计图面。 批注可以包含任何类型的文本，对将标签、注释和其他说明性信息添加到包十分有用。 批注仅为设计时功能。 例如，批注不会写入日志。  
  
 按 Enter 时，文本会换行到下一行。 在添加其他文本行时，批注框的大小会自动增加。 包批注会以明文形式持久保持在包文件的 CDATA 部分。  
  
 有关更改包文件格式的详细信息，请参阅 [SSIS 包格式](../Topic/SSIS%20Package%20Format.md)。  
  
 保存包时， [!INCLUDE[ssIS](../includes/ssis-md.md)] 设计器将批注保存在包中。  
  
### 将批注添加到包  
  
-   [将批注添加到包](../Topic/Add%20an%20Annotation%20to%20a%20Package.md)  
  
  