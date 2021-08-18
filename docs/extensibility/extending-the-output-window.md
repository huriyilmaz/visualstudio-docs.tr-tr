---
title: Çıkış Penceresi genişletiliyor | Microsoft Docs
description: Visual Studio SDK 'sında çıkış penceresini genişletmeyi ve kendi özel bölmelerinizi oluşturma ve yönetme hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Output window, about Output window
ms.assetid: b02fa88c-f92a-4ff6-ba5f-2eb4d48a643a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 32deced6349cf302a2a3da37a2df4c026a0feb84
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122125120"
---
# <a name="extend-the-output-window"></a>Çıkış penceresini genişletme
**Çıkış** penceresi, okuma/yazma metin bölmeleri kümesidir. Visual Studio bu yerleşik bölmelere sahiptir: derleme, projelerin derlemeler hakkındaki iletileri ve **genel** olarak ıde hakkındaki iletileri iletişim kurmasını sağlayan **derleme** [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . projeler, arabirim yöntemleri aracılığıyla **derleme** bölmesine otomatik olarak bir başvuru alır <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> ve Visual Studio hizmet aracılığıyla **genel** bölmeye doğrudan erişim sağlar <xref:Microsoft.VisualStudio.Shell.Interop.SVsGeneralOutputWindowPane> . Yerleşik bölmelere ek olarak kendi özel bölmelerinizi oluşturabilir ve yönetebilirsiniz.

 **Çıkış** penceresini doğrudan <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> ve arabirimleri aracılığıyla denetleyebilirsiniz <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane> . <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow>Hizmet tarafından sunulan arabirim, <xref:Microsoft.VisualStudio.Shell.Interop.SVsOutputWindow> **Çıkış** pencere bölmelerini oluşturma, alma ve yok etme yöntemlerini tanımlar. <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane>Arabirim bölmeleri gösterme, bölmeleri gizleme ve metinlerini düzenleme yöntemlerini tanımlar. **çıkış** penceresini denetlemenin alternatif bir yolu, <xref:EnvDTE.OutputWindow> <xref:EnvDTE.OutputWindowPane> Visual Studio Automation nesne modelindeki nesneler ve nesneler kullanmaktır. Bu nesneler, ve arabirimlerinin neredeyse tüm işlevlerini kapsülleyebilir <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane> . Ayrıca, <xref:EnvDTE.OutputWindow> ve nesneleri, <xref:EnvDTE.OutputWindowPane> **Çıkış** pencere bölmelerini daha kolay bir şekilde numaralandırmak ve bölmelerden metin almak için bazı üst düzey işlevleri de ekler.

## <a name="create-an-extension-that-uses-the-output-pane"></a>Çıkış bölmesini kullanan bir uzantı oluşturma
 Çıkış bölmesinin farklı yönlerini uygulayan bir uzantı yapabilirsiniz.

1. `TestOutput` **TestOutput** adlı bir menü komutuyla adlı bir VSIX projesi oluşturun. Daha fazla bilgi için bkz. [bir menü komutuyla uzantı oluşturma](../extensibility/creating-an-extension-with-a-menu-command.md).

2. Aşağıdaki başvuruları ekleyin:

    1. EnvDTE

    2. EnvDTE80

3. *TestOutput. cs* dosyasında aşağıdaki using ifadesini ekleyin:

    ```f#
    using EnvDTE;
    using EnvDTE80;
    ```

4. *TestOutput. cs* dosyasında, yöntemini silin `ShowMessageBox` . Aşağıdaki yöntem saplaması 'nı ekleyin:

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

6. Aşağıdaki bölümlerde, çıkış bölmesiyle ilgilenmenin farklı yollarını gösteren farklı yöntemler vardır. Yöntemi gövdesine bu yöntemleri çağırabilirsiniz `OutputCommandHandler()` . Örneğin, aşağıdaki kod, `CreatePane()` sonraki bölümde verilen yöntemi ekler.

    ```csharp
    private void OutputCommandHandler(object sender, EventArgs e)
    {
        CreatePane(new Guid(), "Created Pane", true, false);
    }
    ```

## <a name="create-an-output-window-with-ivsoutputwindow"></a>Isoutputwindow ile çıkış penceresi oluşturma
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

## <a name="create-an-output-window-with-outputwindow"></a>OutputWindow ile çıkış penceresi oluşturma
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
        panes.Add(title);
    }
}
```

 Koleksiyon, <xref:EnvDTE.OutputWindowPanes> bir **Çıkış** pencere bölmesini kendi başlığına göre almanıza izin verse de bölme başlıklarının benzersiz olması garanti edilmez. Bir başlığın benzersizliği olduğunu şüpheli yaptığınızda, <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow.GetPane%2A> GUID 'sini kullanarak doğru bölmeyi almak için yöntemini kullanın.

 Önceki bölümde verilen uzantıya bu yöntemi eklerseniz, **TestOutput komutunu çağır** ' a tıkladığınızda, çıkış penceresini, bölmenin bulunduğu bir üst bilgi ile birlikte görmeniz gerekir **: dtepane** ve başlık **eklenen DTE bölmesi** .

## <a name="delete-an-output-window"></a>Çıkış penceresini silme
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

## <a name="get-the-general-pane-of-the-output-window"></a>Çıkış penceresinin Genel bölmesini al
 Bu örnek, **Çıkış** penceresinin yerleşik **genel** bölmesinin nasıl alınacağını gösterir.

```csharp
IVsOutputWindowPane GetGeneralPane()
{
    return (IVsOutputWindowPane)GetService(
        typeof(SVsGeneralOutputWindowPane));
}
```

 Önceki bölümde verilen uzantıya bu yöntemi eklerseniz, **TestOutput komutunu çağır** ' a tıkladığınızda **Çıkış** penceresinde, bölmedeki **genel bölme** sözcüklerini gösterdiğini görmeniz gerekir.

## <a name="get-the-build-pane-of-the-output-window"></a>Çıkış penceresinin derleme bölmesini al
 Bu örnek, **derleme** bölmesinin nasıl bulunacağını ve ona nasıl yazılacağını gösterir. **Yapı** bölmesi varsayılan olarak etkin olmadığından, onu da etkinleştirir.

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
