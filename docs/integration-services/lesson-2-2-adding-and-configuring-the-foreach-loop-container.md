---
title: "步骤 2： 添加和配置 Foreach 循环容器 |Microsoft 文档"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: get-started-article
applies_to:
- SQL Server 2016
ms.assetid: 88a973cc-0f23-4ecf-adb6-5b06279c2df6
caps.latest.revision: 36
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: a2e3655bedbb24f2174a62c8792cd168e7642592
ms.openlocfilehash: 315933379f0ec61453fa0fd783686f9446a977c0
ms.contentlocale: zh-cn
ms.lasthandoff: 08/03/2017

---
# <a name="lesson-2-2---adding-and-configuring-the-foreach-loop-container"></a>课程 2-2-添加和配置 Foreach 循环容器
在本任务中，将添加循环访问平面文件的文件夹的功能，并将第 1 课中使用的同一数据流转换应用于其中的每个平面文件。 实现方法是将 Foreach 循环容器添加到控制流中并进行配置。  
  
所添加的 Foreach 循环容器必须能够连接到该文件夹中的每个平面文件。 由于该文件夹中的所有文件都具有相同的格式，因此，Foreach 循环容器可以使用同一平面文件连接管理器来连接其中的每个文件。 该容器所使用的平面文件连接管理器与您在第 1 课中创建的平面文件连接管理器相同。  
  
目前，第 1 课中的平面文件连接管理器只连接一个特定的平面文件。 若要循环地连接该文件夹中的每个平面文件，必须同时对 Foreach 循环容器和平面文件连接管理器进行如下配置：  
  
-   **Foreach 循环容器** ：将该容器的枚举值映射为用户定义的包变量。 然后，该容器将使用此用户定义变量来动态修改平面文件连接管理器的 **ConnectionString** 属性，并循环连接该文件夹中的每个平面文件。  
  
-   **平面文件连接管理器** ：使用用户定义的变量填充在第 1 课中创建的连接管理器的 **ConnectionString** 属性，以修改该连接管理器。  
  
本任务中的过程向您显示如何创建和修改 Foreach 循环容器以使用用户定义的包变量，以及如何将数据流任务添加到该循环中。 您将了解改平面文件连接管理器，以便在下一任务中使用用户定义的变量。  
  
在对该包进行这些修改后，当该包运行时，Foreach 循环容器将循环访问示例数据文件夹中的文件集合。 每次找到一个与条件相匹配的文件时，Foreach 循环容器都会用文件名填充用户定义的变量，将用户定义的变量映射到 Sample Currency Data 平面文件连接管理器的 **ConnectionString** 属性，然后对该文件运行数据流。 因此，在 Foreach 循环的每次迭代中，数据流任务都将使用一个不同的平面文件。  
  
> [!NOTE]  
> 因为[!INCLUDE[msCoName](../includes/msconame-md.md)][!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]离职控制从数据流的流，你将添加到控制流任何循环将不需要这些数据对数据流的修改。 因此，无需更改在第 1 课中创建的数据流。  
  
### <a name="to-add-a-foreach-loop-container"></a>添加 Foreach 循环容器  
  
1.  在“SQL Server Data Tools”中，单击“控制流”选项卡。  
  
2.  在“SSIS 工具箱”中，展开“容器”，然后将“Foreach 循环容器”拖到“控制流”选项卡的设计图面上。  
  
3.  右键单击新添加的“Foreach 循环容器”，然后选择“编辑”。  
  
4.  在“Foreach 循环编辑器”对话框的“常规”页中，为“名称”输入 **Foreach File in Folder**。 单击 **“确定”**。  
  
5.  右键单击“Foreach 循环容器”，然后单击“属性”，在“属性”窗口中，确保已将“LocaleID”属性设置为“英语(美国)”。  
  
### <a name="to-configure-the-enumerator-for-the-foreach-loop-container"></a>为 Foreach 循环容器配置枚举器  
  
1.  双击“Foreach File in Folder”以重新打开“Foreach 循环编辑器”。  
  
2.  单击“集合”。  
  
3.  在“集合”页上，选择“Foreach 文件枚举器”。  
  
4.  在“枚举器配置”组中，单击“浏览”。  
  
5.  在“浏览文件夹”对话框中，找到计算机上包含 Currency_*.txt 文件的文件夹。  
  
    此示例数据与 [!INCLUDE[ssIS](../includes/ssis-md.md)] 课程包一起提供。 要下载示例数据和课程包，请执行以下操作：  
  
    1.  导航到 [Integration Services 产品示例](http://go.microsoft.com/fwlink/?LinkId=275027)。 
  
    2.  单击 **“下载”** 选项卡。  
  
    3.  单击链接获取[SQL2012。Integration_Services.Create_Simple_ETL_Tutorial.Sample.zip](http://msftisprodsamples.codeplex.com/downloads/get/596031)文件。  
  
6.  在“文件”框中，键入 **Currency_\*.txt**。  
  
### <a name="to-map-the-enumerator-to-a-user-defined-variable"></a>将枚举器映射为用户定义的变量  
  
1.  单击“变量映射”。  
  
2.  上**变量映射**页上，在**变量**列中，单击空单元格，然后选择**\<新建变量...>**。  
  
3.  在“添加变量”对话框中，为“名称”键入 **varFileName**。  
  
    > [!IMPORTANT]  
    > 变量名称区分大小写。  
  
4.  单击 **“确定”**。  
  
5.  再次单击“确定”，退出“Foreach 循环编辑器”对话框。  
  
### <a name="to-add-the-data-flow-task-to-the-loop"></a>将数据流任务添加到循环中  
  
-   将“Extract Sample Currency Data”数据流任务拖到现已重命名为 **Foreach File in Folder** 的 Foreach 循环容器中。  
  
## <a name="next-lesson-task"></a>下一课程任务  
[步骤 3： 修改平面文件连接管理器](../integration-services/lesson-2-3-modifying-the-flat-file-connection-manager.md)  
  
## <a name="see-also"></a>另请参阅  
[配置 Foreach 循环容器](http://msdn.microsoft.com/library/519c6f96-5e1f-47d2-b96a-d49946948c25)  
[在包中使用变量](http://msdn.microsoft.com/library/7742e92d-46c5-4cc4-b9a3-45b688ddb787)  
  
  
  
