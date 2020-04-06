---
title: Çıkış Penceresini Genişletme | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Output window, about Output window
ms.assetid: b02fa88c-f92a-4ff6-ba5f-2eb4d48a643a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 800b443b079111d1d09fffdd900b246a020578f4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711652"
---
# <a name="extend-the-output-window"></a>Çıktı penceresini genişletme
**Çıktı** penceresi bir okuma/yazma metin bölmeleri kümesidir. Visual Studio'da bu yerleşik bölmeler vardır: **Yapı**, hangi projeler yapılar hakkında [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] mesajları iletişim ve **Genel**, hangi IDE hakkında iletiler iletişim. <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> Projeler arabirim yöntemleri aracılığıyla otomatik olarak **Yapı** bölmesine bir başvuru alır ve Visual Studio <xref:Microsoft.VisualStudio.Shell.Interop.SVsGeneralOutputWindowPane> hizmet aracılığıyla **Genel** bölmeye doğrudan erişim sağlar. Yerleşik bölmelere ek olarak, kendi özel bölmelerinizi oluşturabilir ve yönetebilirsiniz.

 **Çıkış** penceresini doğrudan <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane> arabirimlerden denetleyebilirsiniz. Hizmet tarafından sunulan arabirim, Çıktı penceresi bölmelerini oluşturma, alma ve yok etme yöntemlerini tanımlar. **Output** <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> <xref:Microsoft.VisualStudio.Shell.Interop.SVsOutputWindow> Arabirim, <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane> bölmeleri gösterme, bölmeleri gizleme ve metinlerini değiştirme yöntemlerini tanımlar. **Çıktı** penceresini denetlemenin alternatif bir <xref:EnvDTE.OutputWindow> yolu, Visual Studio Automation nesne modelindeki <xref:EnvDTE.OutputWindowPane> nesnelerden geçer. Bu nesneler, arabirimlerin <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane> arabirimlerin işlevselliğinin neredeyse tamamını kapsüller. Buna ek <xref:EnvDTE.OutputWindow> olarak, ve <xref:EnvDTE.OutputWindowPane> **nesneler, Çıktı** penceresi bölmelerini saymayı ve bölmelerden metin almayı kolaylaştırmak için bazı üst düzey işlevler ekler.

## <a name="create-an-extension-that-uses-the-output-pane"></a>Çıktı bölmesini kullanan bir uzantı oluşturma
 Çıktı bölmesinin farklı yönlerini çalıştıran bir uzantı yapabilirsiniz.

1. **TestOutput**adlı bir `TestOutput` menü komutu ile adlı bir VSIX projesi oluşturun. Daha fazla bilgi için [bkz.](../extensibility/creating-an-extension-with-a-menu-command.md)

2. Aşağıdaki referansları ekleyin:

    1. Envdte

    2. EnvDTE80

3. *TestOutput.cs,* aşağıdaki leri kullanarak ifadeyi ekleyin:

    ```f#
    using EnvDTE;
    using EnvDTE80;
    ```

4. *TestOutput.cs,* `ShowMessageBox` yöntemi silin. Aşağıdaki yöntem saplama ekleyin:

    ```csharp
    private void OutputCommandHandler(object sender, EventArgs e)
    {
    }
    ```

5. TestOutput oluşturucuda komut işleyicisini OutputCommandHandler olarak değiştirin. Komutları ekleyen bölüm şunlardır:

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

6. Aşağıdaki bölümlerde Çıktı bölmesiyle başa çıkmanın farklı yollarını gösteren farklı yöntemler vardır. Bu yöntemleri yöntemin gövdesine `OutputCommandHandler()` çağırabilirsiniz. Örneğin, aşağıdaki kod sonraki `CreatePane()` bölümde verilen yöntemi ekler.

    ```csharp
    private void OutputCommandHandler(object sender, EventArgs e)
    {
        CreatePane(new Guid(), "Created Pane", true, false);
    }
    ```

## <a name="create-an-output-window-with-ivsoutputwindow"></a>IVsOutputWindow ile Çıkış penceresi oluşturma
 Bu örnek, arabirimi **Output** kullanarak yeni bir Çıktı <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> penceresi bölmesinin nasıl oluşturultuğunu gÜ

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

 Bu yöntemi önceki bölümde verilen uzantıya eklerseniz, **Çağrı TestiÇıktı** komutunu tıklattığınızda **Çıktı** penceresini aşağıdakilerden çıktıyı göster yazan bir üstbilgiyle görmeniz **gerekir: CreatedPane** ve bölmedeki **Oluşturulan Bölme bu** sözcüklerdir.

## <a name="create-an-output-window-with-outputwindow"></a>OutputWindow ile Çıkış Penceresi Oluşturma
 Bu örnek, nesneyi kullanarak bir **Çıkış** <xref:EnvDTE.OutputWindow> penceresi bölmesinin nasıl oluşturulacak olduğunu gösterir.

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

 Koleksiyon, başlığına göre **Bir Çıktı** penceresi bölmesini almanıza olanak sunsa da, bölme başlıklarının benzersiz olacağı garanti edilmez. <xref:EnvDTE.OutputWindowPanes> Bir başlığın benzersizliğinden şüphe ettiğinizde, <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow.GetPane%2A> GUID ile doğru bölmeyi almak için yöntemi kullanın.

 Bu yöntemi önceki bölümde verilen uzantıya eklerseniz, **Çağrı TestiÇıktı** komutunu tıklattığınızda Çıktı penceresini **bkz.** **Added DTE Pane**

## <a name="delete-an-output-window"></a>Çıktı pencereni silme
 Bu örnek, Bir **Çıktı** penceresi bölmesini nasıl silergösteriz.

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

 Bu yöntemi önceki bölümde verilen uzantıya eklerseniz, **Çağrı TestiÇıktı** komutunu tıklattığınızda Çıktı penceresini bir üstbilgiyle görmeniz **gerekir: Yeni Bölme** ve bölmesi kendisinde Oluşturulan Bölme **eklenen** sözcükler. **TestÇıktı'yı** yeniden tıklattığınızda bölme silinir.

## <a name="get-the-general-pane-of-the-output-window"></a>Çıktı penceresinin Genel bölmesini alma
 Bu örnek, **Çıktı** penceresinin yerleşik **Genel** bölmesini nasıl elde edilebildiğini gösterir.

```csharp
IVsOutputWindowPane GetGeneralPane()
{
    return (IVsOutputWindowPane)GetService(
        typeof(SVsGeneralOutputWindowPane));
}
```

 Bu yöntemi önceki bölümde verilen uzanta eklerseniz, Çağrı **TestiÇıktı** komutunu tıklattığınızda, **Çıktı** penceresinin bölmede **Bulunan Genel bölmedeki sözcükleri** gösterdiğini görmeniz gerekir.

## <a name="get-the-build-pane-of-the-output-window"></a>Çıktı penceresinin Yapı bölmesini alma
 Bu örnek, **Yapı** bölmesini nasıl bulup ona nasıl yazabileceğinizi gösterir. **Yapı** bölmesi varsayılan olarak etkinleştirilmediği için, aynı zamanda etkinleştirir.

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
