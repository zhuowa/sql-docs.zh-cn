---
title: "加载和以编程方式运行本地包 |Microsoft 文档"
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
dev_langs:
- VB
helpviewer_keywords:
- Integration Services packages, running
- events [Integration Services], capturing
- packages [Integration Services], running
- loading packages programmatically
- Visual Basic [Integration Services]
- running packages [Integration Services]
- programmatically load and run packages [SSIS]
ms.assetid: 2f9fc1a8-a001-4c54-8c64-63b443725422
caps.latest.revision: 60
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 4a8ade977c971766c8f716ae5f33cac606c8e22d
ms.openlocfilehash: 07ceb460488ca1973295b6b8e991948efe8b9d2a
ms.contentlocale: zh-cn
ms.lasthandoff: 08/03/2017

---
# <a name="loading-and-running-a-local-package-programmatically"></a>以编程方式加载和运行本地包
  你可以运行[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)]包根据需要或在预定时间通过使用中所述的方法[正在运行的包](https://msdn.microsoft.com/library/ms141708(v=sql.110).aspx)。 但是，也可以只用几行代码，从自定义应用程序（如 Windows 窗体应用程序、控制台应用程序、ASP.NET Web 窗体或 Web 服务、Windows 服务）运行包。  
  
 本主题讨论：  
  
-   以编程方式加载的包  
  
-   以编程方式运行包  
  
 本主题中用于加载和运行包的方法的所有需要引用**Microsoft.SqlServer.ManagedDTS**程序集。 添加新项目中的引用后, 导入<xref:Microsoft.SqlServer.Dts.Runtime>具有命名空间**使用**或**导入**语句。  
  
## <a name="loading-a-package-programmatically"></a>以编程方式加载包  
 若要以编程方式在本地计算机中加载包，无论包是本地存储还是远程存储，都可以调用以下方法之一：  
  
|存储位置|调用的方法|  
|----------------------|--------------------|  
|文件|<xref:Microsoft.SqlServer.Dts.Runtime.Application.LoadPackage%2A>|  
|SSIS 包存储区|<xref:Microsoft.SqlServer.Dts.Runtime.Application.LoadFromDtsServer%2A>|  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|<xref:Microsoft.SqlServer.Dts.Runtime.Application.LoadFromSqlServer%2A>|  
  
> [!IMPORTANT]  
>  <xref:Microsoft.SqlServer.Dts.Runtime.Application> 类中用于处理 SSIS 包存储区的方法只支持“.”、localhost 或本地服务器的服务器名称。 不能使用“(local)”。  
  
## <a name="running-a-package-programmatically"></a>以编程方式运行包  
 以托管代码方式开发在本地计算机上运行包的自定义应用程序需要采用以下方式。 此处总结的步骤在随后的控制台应用程序示例中演示。  
  
#### <a name="to-run-a-package-on-the-local-computer-programmatically"></a>以编程方式在本地计算机中运行包  
  
1.  启动 Visual Studio 开发环境，以您首选的开发语言创建新的应用程序。 本示例使用的是控制台应用程序；但您也可以从 Windows 窗体应用程序、ASP.NET Web 窗体或 Web 服务或者 Windows 服务运行包。  
  
2.  上**项目**菜单上，单击**添加引用**并添加对引用**Microsoft.SqlServer.ManagedDTS.dll**。 单击 **“确定”**。  
  
3.  使用 Visual Basic**导入**语句或 C#**使用**用于导入语句**Microsoft.SqlServer.Dts.Runtime**命名空间。  
  
4.  在主例程中添加以下代码。 完成的控制台应用程序应类似于下面的示例。  
  
    > [!NOTE]  
    >  该示例代码演示如何使用 <xref:Microsoft.SqlServer.Dts.Runtime.Application.LoadPackage%2A> 方法从文件系统加载包。 但您也可以通过调用 <xref:Microsoft.SqlServer.Dts.Runtime.Application.LoadFromSqlServer%2A> 方法，从 MSDB 数据库加载包，或者通过调用 <xref:Microsoft.SqlServer.Dts.Runtime.Application.LoadFromDtsServer%2A> 方法，从 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 包存储区加载包。  
  
5.  运行该项目。 示例代码执行随 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 示例安装的 CalculatedColumns 示例包。 包执行的结果显示在控制台窗口中。  
  
### <a name="sample-code"></a>示例代码  
  
```vb  
Imports Microsoft.SqlServer.Dts.Runtime  
  
Module Module1  
  
  Sub Main()  
  
    Dim pkgLocation As String  
    Dim pkg As New Package  
    Dim app As New Application  
    Dim pkgResults As DTSExecResult  
  
    pkgLocation = _  
      "C:\Program Files\Microsoft SQL Server\100\Samples\Integration Services" & _  
      "\Package Samples\CalculatedColumns Sample\CalculatedColumns\CalculatedColumns.dtsx"  
    pkg = app.LoadPackage(pkgLocation, Nothing)  
    pkgResults = pkg.Execute()  
  
    Console.WriteLine(pkgResults.ToString())  
    Console.ReadKey()  
  
  End Sub  
  
End Module  
```  
  
```csharp  
using System;  
using Microsoft.SqlServer.Dts.Runtime;  
  
namespace RunFromClientAppCS  
{  
  class Program  
  {  
    static void Main(string[] args)  
    {  
      string pkgLocation;  
      Package pkg;  
      Application app;  
      DTSExecResult pkgResults;  
  
      pkgLocation =  
        @"C:\Program Files\Microsoft SQL Server\100\Samples\Integration Services" +  
        @"\Package Samples\CalculatedColumns Sample\CalculatedColumns\CalculatedColumns.dtsx";  
      app = new Application();  
      pkg = app.LoadPackage(pkgLocation, null);  
      pkgResults = pkg.Execute();  
  
      Console.WriteLine(pkgResults.ToString());  
      Console.ReadKey();  
    }  
  }  
}  
```  
  
## <a name="capturing-events-from-a-running-package"></a>从运行中的包捕获事件  
 当您按照上面的示例所示以编程方式运行包时，还可以捕获包执行时发生的错误及其他事件。 为此，请添加从 <xref:Microsoft.SqlServer.Dts.Runtime.DefaultEvents> 类继承的类，并在加载包时传递对该类的引用。 下面的示例仅捕获 <xref:Microsoft.SqlServer.Dts.Runtime.DefaultEvents.OnError%2A> 事件，但还有其他很多事件可以通过 <xref:Microsoft.SqlServer.Dts.Runtime.DefaultEvents> 类捕获。  
  
#### <a name="to-run-a-package-on-the-local-computer-programmatically-and-capture-package-events"></a>以编程方式在本地计算机中运行包同时捕获包事件  
  
1.  按照前面示例中的步骤为此示例创建项目。  
  
2.  在主例程中添加以下代码。 完成的控制台应用程序应类似于下面的示例。  
  
3.  运行该项目。 示例代码执行随 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 示例安装的 CalculatedColumns 示例包。 包执行的结果显示在控制台窗口中，同时显示发生的所有错误。  
  
### <a name="sample-code"></a>示例代码  
  
```vb  
Imports Microsoft.SqlServer.Dts.Runtime  
  
Module Module1  
  
  Sub Main()  
  
    Dim pkgLocation As String  
    Dim pkg As New Package  
    Dim app As New Application  
    Dim pkgResults As DTSExecResult  
  
    Dim eventListener As New EventListener()  
  
    pkgLocation = _  
      "C:\Program Files\Microsoft SQL Server\100\Samples\Integration Services" & _  
      "\Package Samples\CalculatedColumns Sample\CalculatedColumns\CalculatedColumns.dtsx"  
    pkg = app.LoadPackage(pkgLocation, eventListener)  
    pkgResults = pkg.Execute(Nothing, Nothing, eventListener, Nothing, Nothing)  
  
    Console.WriteLine(pkgResults.ToString())  
    Console.ReadKey()  
  
  End Sub  
  
End Module  
  
Class EventListener  
  Inherits DefaultEvents  
  
  Public Overrides Function OnError(ByVal source As Microsoft.SqlServer.Dts.Runtime.DtsObject, _  
    ByVal errorCode As Integer, ByVal subComponent As String, ByVal description As String, _  
    ByVal helpFile As String, ByVal helpContext As Integer, _  
    ByVal idofInterfaceWithError As String) As Boolean  
  
    ' Add application–specific diagnostics here.  
    Console.WriteLine("Error in {0}/{1} : {2}", source, subComponent, description)  
    Return False  
  
  End Function  
  
End Class  
```  
  
```csharp  
using System;  
using Microsoft.SqlServer.Dts.Runtime;  
  
namespace RunFromClientAppWithEventsCS  
{  
  class MyEventListener : DefaultEvents  
  {  
    public override bool OnError(DtsObject source, int errorCode, string subComponent,   
      string description, string helpFile, int helpContext, string idofInterfaceWithError)  
    {  
      // Add application-specific diagnostics here.  
      Console.WriteLine("Error in {0}/{1} : {2}", source, subComponent, description);  
      return false;  
    }  
  }  
  class Program  
  {  
    static void Main(string[] args)  
    {  
      string pkgLocation;  
      Package pkg;  
      Application app;  
      DTSExecResult pkgResults;  
  
      MyEventListener eventListener = new MyEventListener();  
  
      pkgLocation =  
        @"C:\Program Files\Microsoft SQL Server\100\Samples\Integration Services" +  
        @"\Package Samples\CalculatedColumns Sample\CalculatedColumns\CalculatedColumns.dtsx";  
      app = new Application();  
      pkg = app.LoadPackage(pkgLocation, eventListener);  
      pkgResults = pkg.Execute(null, null, eventListener, null, null);  
  
      Console.WriteLine(pkgResults.ToString());  
      Console.ReadKey();  
    }  
  }  
}  
```  
  
## <a name="see-also"></a>另请参阅  
 [了解本地和远程执行之间的差异](../../integration-services/run-manage-packages-programmatically/understanding-the-differences-between-local-and-remote-execution.md)   
 [加载和以编程方式运行远程包](../../integration-services/run-manage-packages-programmatically/loading-and-running-a-remote-package-programmatically.md)   
 [加载本地包的输出](../../integration-services/run-manage-packages-programmatically/loading-the-output-of-a-local-package.md)  
  
  