---
title: "比较书签 |Microsoft 文档"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- result sets [ODBC], bookmarks
- comparing bookmarks [ODBC]
- bookmarks [ODBC]
ms.assetid: ea347635-fbe3-41c1-b537-4048b7c0f7da
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 7ebcf375311af498dbb4c777707b7febcddb05a3
ms.contentlocale: zh-cn
ms.lasthandoff: 09/09/2017

---
# <a name="comparing-bookmarks"></a>比较的书签
因为字节比较，书签将变为，它们可以比较相等。 为此，应用程序将视为的字节数组的每个书签，并比较两个书签的字节。 要仅在结果集内非重复，保证具有书签，因为它没有意义要比较的书签，获取从不同的结果集。