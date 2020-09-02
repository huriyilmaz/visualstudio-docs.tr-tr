---
title: Çıkış Penceresi genişletiliyor | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Output window, about Output window
ms.assetid: b02fa88c-f92a-4ff6-ba5f-2eb4d48a643a
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2788903c60564d501770616fbe3ad2335e60a250
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204432"
---
# <a name="extending-the-output-window"></a>Çıkış Penceresini Genişletme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**Çıkış** penceresi, okuma/yazma metin bölmeleri kümesidir. Visual Studio, bu yerleşik bölmelere sahiptir: derleme, projelerin derlemeler hakkındaki iletileri ve **genel**olarak IDE hakkındaki iletileri iletişim kurmasını sağlayan **derleme** [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Projeler, arabirim yöntemleri aracılığıyla **derleme** bölmesine otomatik olarak bir başvuru alır <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> ve Visual Studio, hizmet aracılığıyla **genel** bölmeye doğrudan erişim sağlar <xref:Microsoft.VisualStudio.Shell.Interop.SVsGeneralOutputWindowPane> . Yerleşik bölmelere ek olarak kendi özel bölmelerinizi oluşturabilir ve yönetebilirsiniz.  
  
 **Çıkış** penceresini doğrudan <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> ve arabirimleri aracılığıyla denetleyebilirsiniz <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane> . <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow>Hizmet tarafından sunulan arabirim, <xref:Microsoft.VisualStudio.Shell.Interop.SVsOutputWindow> **Çıkış** pencere bölmelerini oluşturma, alma ve yok etme yöntemlerini tanımlar. <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow>Arabirim bölmeleri gösterme, bölmeleri gizleme ve metinlerini düzenleme yöntemlerini tanımlar. **Çıktı** penceresini denetlemenin alternatif bir yolu, <xref:EnvDTE.OutputWindow> <xref:EnvDTE.OutputWindowPane> Visual Studio Automation nesne modelindeki ve nesneleri kullanmaktır. Bu nesneler, ve arabirimlerinin neredeyse tüm işlevlerini kapsülleyebilir <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane> . Ayrıca, <xref:EnvDTE.OutputWindow> ve nesneleri, <xref:EnvDTE.OutputWindowPane> **Çıkış** pencere bölmelerini daha kolay bir şekilde numaralandırmak ve bölmelerden metin almak için bazı üst düzey işlevleri de ekler.  
  
## <a name="creating-an-extension-that-uses-the-output-pane"></a>Çıkış bölmesini kullanan bir uzantı oluşturma  
 Çıkış bölmesinin farklı yönlerini uygulayan bir uzantı yapabilirsiniz.  
  
1. `TestOutput` **TestOutput**adlı bir menü komutuyla adlı bir VSIX projesi oluşturun. Daha fazla bilgi için bkz. [bir menü komutuyla uzantı oluşturma](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
2. Aşağıdaki başvuruları ekleyin:  
  
    1. EnvDTE  
  
    2. EnvDTE80  
  
3. TestOutput.cs ' de, aşağıdaki using ifadesini ekleyin:  
  
    ```f#  
    using EnvDTE;  
    using EnvDTE80;  
    ```  
  
4. TestOutput.cs ' de ShowMessageBox yöntemini silin. Aşağıdaki yöntem saplaması 'nı ekleyin:  
  
    ```csharp  
    private void OutputCommandHandler(object sender, EventArgs e)  
    {  
    }  
    ```  
  
5. TestOutput oluşturucusunda, komut işleyicisini OutputCommandHandler olarak değiştirin. Komutları ekleyen bölüm aşağıda verilmiştir:  
  
    ```csharp  
    OleMenuCommandService commandService = this.ServiceProvider.GetService(typeof(IMenuCommandService)) as OleMenuCommandService;  
    if (commandService != null)  
    {  
        CommandID menuCommandID = new CommandID(MenuGroup, CommandId);  
        EventHandler eventHandler = OutputCommandHandler;  
        MenuCommand menuItem = new MenuCommand(eventHandler, menuCommandID);  
        commandService.AddCommand(menuItem);  
    }  
    ```  
  
6. Aşağıdaki bölümlerde, çıkış bölmesiyle ilgilenmenin farklı yollarını gösteren farklı yöntemler vardır. Bu yöntemleri OutputCommandHandler () yönteminin gövdesine çağırabilirsiniz. Örneğin, aşağıdaki kod, sonraki bölümde verilen CreatePane () metodunu ekler.  
  
    ```csharp  
    private void OutputCommandHandler(object sender, EventArgs e)  
    {  
        CreatePane(new Guid(), "Created Pane", true, false);  
    }  
    ```  
  
## <a name="creating-an-output-window-with-ivsoutputwindow"></a>Isoutputwindow ile Çıkış Penceresi oluşturma  
 Bu örnekte, arabirimi kullanılarak nasıl yeni bir **Çıkış** pencere bölmesi oluşturulacağı gösterilmektedir <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> .  
  
```csharp  
void CreatePane(Guid paneGuid, string title,   
    bool visible, bool clearWithSolution)  
{  
    IVsOutputWindow output =   
        (IVsOutputWindow)GetService(typeof(SVsOutputWindow));  
    IVsOutputWindowPane pane;  
  
    // Create a new pane.  
    output.CreatePane(  
        ref paneGuid,   
        title,   
        Convert.ToInt32(visible),   
        Convert.ToInt32(clearWithSolution));  
  
    // Retrieve the new pane.  
    output.GetPane(ref paneGuid, out pane);  
  
     pane.OutputString("This is the Created Pane \n");  
}  
```  
  
 Önceki bölümde verilen uzantıya bu yöntemi eklerseniz, **Invoke TestOutput** komutuna tıkladığınızda **Çıkış** penceresini, **Çıkış penceresini göster: createdpane** ve bu, bölmenin kendisi tarafından **oluşturulan böleni** görürsünüz.  
  
## <a name="creating-an-output-window-with-outputwindow"></a>OutputWindow ile Çıkış Penceresi oluşturma  
 Bu örnek, nesnesini kullanarak **Çıkış** pencere bölmesinin nasıl oluşturulacağını gösterir <xref:EnvDTE.OutputWindow> .  
  
```csharp  
void CreatePane(string title)  
{  
    DTE2 dte = (DTE2)GetService(typeof(DTE));  
    OutputWindowPanes panes =  
        dte.ToolWindows.OutputWindow.OutputWindowPanes;  
  
    try  
    {  
        // If the pane exists already, write to it.  
        panes.Item(title);  
    }  
    catch (ArgumentException)  
    {  
        // Create a new pane and write to it.  
        return panes.Add(title);  
    }  
}  
```  
  
 Koleksiyon, <xref:EnvDTE.OutputWindowPanes> bir **Çıkış** pencere bölmesini kendi başlığına göre almanıza izin verse de bölme başlıklarının benzersiz olması garanti edilmez. Bir başlığın benzersizliği olduğunu şüpheli yaptığınızda, <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow.GetPane%2A> GUID 'sini kullanarak doğru bölmeyi almak için yöntemini kullanın.  
  
 Önceki bölümde verilen uzantıya bu yöntemi eklerseniz, **TestOutput komutunu çağır** ' a tıkladığınızda, çıkış penceresini, bölmenin bulunduğu bir üst bilgi ile birlikte görmeniz gerekir **: dtepane** ve başlık **eklenen DTE bölmesi** .  
  
## <a name="deleting-an-output-window"></a>Çıkış Penceresi silme  
 Bu örnek, bir **Çıkış** pencere bölmesinin nasıl silineceğini gösterir.  
  
```csharp  
void DeletePane(Guid paneGuid)  
{  
    IVsOutputWindow output =  
    (IVsOutputWindow)ServiceProvider.GetService(typeof(SVsOutputWindow));  
  
    IVsOutputWindowPane pane;  
    output.GetPane(ref paneGuid, out pane);  
  
    if (pane == null)  
    {  
        CreatePane(paneGuid, "New Pane\n", true, true);  
    }  
     else  
    {  
        output.DeletePane(ref paneGuid);  
    }  
}  
```  
  
 Önceki bölümde verilen uzantıya bu yöntemi eklerseniz, **TestOutput komutunu çağır** ' a tıkladığınızda çıkış penceresini, çıkış penceresine şu **çıktıyı göster: yeni bölmesi** ve bu bölme **eklenen** bir başlık ile birlikte görüntülenir. **TestOutput** komutunu yeniden çağır ' a tıklarsanız, bölmesi silinir.  
  
## <a name="getting-the-general-pane-of-the-output-window"></a>Çıkış Penceresi genel bölmesini alma  
 Bu örnek, **Çıkış** penceresinin yerleşik **genel** bölmesinin nasıl alınacağını gösterir.  
  
```csharp  
void GetGeneralPane()  
{  
    return (IVsOutputWindowPane)GetService(  
        typeof(SVsGeneralOutputWindowPane));  
}  
```  
  
 Önceki bölümde verilen uzantıya bu yöntemi eklerseniz, **TestOutput komutunu çağır** ' a tıkladığınızda **Çıkış** penceresinde, bölmedeki **genel bölme** sözcüklerini gösterdiğini görmeniz gerekir.  
  
## <a name="getting-the-build-pane-of-the-output-window"></a>Çıkış Penceresi Yapı bölmesini alma  
 Bu örnek, derleme bölmesinin nasıl bulunacağını ve ona nasıl yazılacağını gösterir. Yapı bölmesi varsayılan olarak etkin olmadığından, onu da etkinleştirir.  
  
```csharp  
void OutputTaskItemStringExExample(string buildMessage)  
{  
    EnvDTE80.DTE2 dte = (EnvDTE80.DTE2)ServiceProvider.GetService(typeof(EnvDTE.DTE));  
  
    EnvDTE.OutputWindowPanes panes =  
        dte.ToolWindows.OutputWindow.OutputWindowPanes;  
    foreach (EnvDTE.OutputWindowPane pane in panes)  
        {  
            if (pane.Name.Contains("Build"))  
            {  
                pane.OutputString(buildMessage + "\n");  
                pane.Activate();  
                return;  
             }  
        }  
}  
```
