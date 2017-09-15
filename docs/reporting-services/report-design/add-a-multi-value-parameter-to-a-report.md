---
title: "向报表添加多值参数 |Microsoft 文档"
ms.custom: 
ms.date: 03/07/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-sharepoint
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 12ad0e77-4c28-4bbb-ab11-473ae89ec9f1
caps.latest.revision: 7
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 0411de7999d497b3198e6864d185cb54a4a5e1f5
ms.contentlocale: zh-cn
ms.lasthandoff: 08/09/2017

---
# <a name="add-a-multi-value-parameter-to-a-report"></a>将多值参数添加到报表
  可以将参数添加到报表，以允许用户为参数选择多个值。  
  
 您可以在报表 URL 中将多个参数值传递给报表。 有关包含多值参数的 URL 示例，请参阅 [在 URL 内传递报表参数](../../reporting-services/pass-a-report-parameter-within-a-url.md)。  
  
 有关如何将多个参数值传递给存储过程的信息，请参阅 mssqltips.com 上的 [使用 SSRS 报表的多选参数](http://go.microsoft.com/fwlink/?LinkId=321529) 。  
  
## <a name="to-add-a-multi-value-parameter"></a>添加多值参数  
  
1.  在报表生成器中，打开您希望将多值参数添加到其中的报表。  
  
2.  右键单击报表数据集，并依次**数据集属性**  
  
3.  通过在 **“查询”** 框中编辑查询文本或通过使用查询设计器添加筛选器，将变量添加到数据集查询中。 有关详细信息，请参阅[在关系查询设计器中生成查询（报表生成器和 SSRS）](../../reporting-services/report-data/build-a-query-in-the-relational-query-designer-report-builder-and-ssrs.md)。  
  
    ```  
    WHERE  
      Production.ProductInventory.ProductID IN (@ProductID)  
    ```  
  
    > [!IMPORTANT]  
    > *  查询文本不得包含针对查询变量的 DECLARE 语句。  
    > *  查询变量的文本必须包含 **IN** 运算符，如以下示例所示。  
    > *  请务必在变量两侧加上括号，如上所示。 否则报表将无法呈现且会显示“必须声明标量变量”错误。  
  
    自动为查询变量创建嵌入数据集或共享数据集的数据集参数。 自动为数据集参数创建报表参数。  
  
4.  在**报表数据**窗格中，展开**参数**节点，右键单击已为数据集参数自动创建的报表参数，再单击**参数属性**。  
  
5.  在 **“常规”** 选项卡中，选择 **“允许多个值”** 以允许用户为参数选择多个值。  
  
6.  （可选）在**可用**值选项卡上，指定要向用户显示的可用值的列表。  
  
     可用值列表将限制用户只能选择参数的有效值。 对于多值参数，列表的顶部具有一个 **“全选”** 功能，因此用户只需一次单击即可选中或取消选中所有值。 如果您选择从数据集查询中获取报表参数的可用值，请确保选择不包含与同一报表参数关联的查询变量的数据集。  
  
     有关详细信息，请参阅[添加、 更改或删除报表参数 &#40; 的可用值报表生成器和 SSRS &#41;](../../reporting-services/report-design/add-change-or-delete-available-values-for-a-report-parameter.md).  
  
## <a name="to-add-a-multi-value-parameter"></a>添加多值参数  
  
1.  在报表生成器中，打开您希望将多值参数添加到其中的报表。  
  
2.  右键单击报表数据集，并依次**数据集属性**  
  
3.  通过在 **“查询”** 框中编辑查询文本或通过使用查询设计器添加筛选器，将变量添加到数据集查询中。 有关详细信息，请参阅[在关系查询设计器中生成查询（报表生成器和 SSRS）](../../reporting-services/report-data/build-a-query-in-the-relational-query-designer-report-builder-and-ssrs.md)。  
  
     ```  
    WHERE  
      Production.ProductInventory.ProductID IN (@ProductID)  
    ```  
  
    > [!IMPORTANT]  
    > *  查询文本不得包含针对查询变量的 DECLARE 语句。  
    > *  查询变量的文本必须包含 **IN** 运算符，如以下示例所示。  
    > *  请务必在变量两侧加上括号，如上所示。 否则报表将无法呈现且会显示“必须声明标量变量”错误  
      
    自动为查询变量创建嵌入数据集或共享数据集的数据集参数。 自动为数据集参数创建报表参数。  
  
4.  在**报表数据**窗格中，展开**参数**节点，右键单击已为数据集参数自动创建的报表参数，再单击**参数属性**。  
  
5.  在 **“常规”** 选项卡中，选择 **“允许多个值”** 以允许用户为参数选择多个值。  
  
6.  （可选）在**可用**值选项卡上，指定要向用户显示的可用值的列表。  
  
     可用值列表将限制用户只能选择参数的有效值。 对于多值参数，列表的顶部具有一个 **“全选”** 功能，因此用户只需一次单击即可选中或取消选中所有值。 如果您选择从数据集查询中获取报表参数的可用值，请确保选择不包含与同一报表参数关联的查询变量的数据集。  
  
     有关详细信息，请参阅[添加、 更改或删除报表参数 &#40; 的可用值报表生成器和 SSRS &#41;](../../reporting-services/report-design/add-change-or-delete-available-values-for-a-report-parameter.md).  
  
## <a name="see-also"></a>另请参阅  
 [向报表添加级联参数（报表生成器和 SSRS）](../../reporting-services/report-design/add-cascading-parameters-to-a-report-report-builder-and-ssrs.md)   
 [添加、更改或删除报表参数（报表生成器和 SSRS）](../../reporting-services/report-design/add-change-or-delete-a-report-parameter-report-builder-and-ssrs.md)  
  
  