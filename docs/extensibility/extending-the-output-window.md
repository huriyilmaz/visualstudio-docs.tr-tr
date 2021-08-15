---
title: Çalışma Çıkış Penceresi | Microsoft Docs
description: Visual Studio SDK'da Çıkış penceresini genişletmeyi ve kendi özel bölmelerinizi oluşturma ve yönetmeyi öğrenin.
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
ms.openlocfilehash: b7b0ba71fa7f1c20d53a084580546d6e85bd0f03515b859589c664e11f0910dd
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121305977"
---
# <a name="extend-the-output-window"></a>Çıkış penceresini genişletme
Çıkış **penceresi,** bir dizi okuma/yazma metin bölmesidir. Visual Studio bölmeleri **vardır:** Projelerin derlemeler hakkında ileti ilettleri Derleme ve IDE ile ilgili iletileri iletir genel [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] bölmeleri. Projeler, arabirim yöntemleri **aracılığıyla** otomatik olarak Derleme bölmesine başvurur ve Visual Studio hizmet aracılığıyla Genel <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg> bölmesine doğrudan erişim  <xref:Microsoft.VisualStudio.Shell.Interop.SVsGeneralOutputWindowPane> sunar. Yerleşik bölmelere ek olarak kendi özel bölmelerinizi oluşturabilir ve yönetebilirsiniz.

 Çıkış penceresini doğrudan **ve** arabirimleri <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> aracılığıyla <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane> kontrolebilirsiniz. Hizmet <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> tarafından sunulan <xref:Microsoft.VisualStudio.Shell.Interop.SVsOutputWindow> arabirimi, Çıkış penceresi bölmelerini oluşturma, alma ve  yok etme yöntemlerini tanımlar. arabirimi <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane> bölmeleri gösterme, bölmeleri gizleme ve metinlerini değiştirme yöntemlerini tanımlar. Çıkış penceresini denetlemenin alternatif **bir** yolu, Otomasyon nesne modelinde ve <xref:EnvDTE.OutputWindow> Visual Studio <xref:EnvDTE.OutputWindowPane> aracılığıyladır. Bu nesneler ve arabirimlerinin neredeyse tüm işlevlerini <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindowPane> kapsüller. Ayrıca, ve nesneleri, Çıkış penceresi bölmelerini numaralara eklemeyi ve bölmelerden metinleri almayı kolaylaştırmak için bazı üst <xref:EnvDTE.OutputWindow> <xref:EnvDTE.OutputWindowPane> düzey işlevler ekler. 

## <a name="create-an-extension-that-uses-the-output-pane"></a>Çıkış bölmesini kullanan bir uzantı oluşturma
 Çıkış bölmesinin farklı yönleriyle alıştırmalar yapacak bir uzantı yapabilirsiniz.

1. TestOutput adlı bir menü komutuyla adlı bir VSIX `TestOutput` **projesi oluşturun.** Daha fazla bilgi için [bkz. Menü komutuyla uzantı oluşturma.](../extensibility/creating-an-extension-with-a-menu-command.md)

2. Aşağıdaki başvuruları ekleyin:

    1. Envdte

    2. EnvDTE80

3. *TestOutput.cs içinde* aşağıdaki using deyimini ekleyin:

    ```f#
    using EnvDTE;
    using EnvDTE80;
    ```

4. *TestOutput.cs içinde* yöntemini `ShowMessageBox` silin. Aşağıdaki yöntem saplama ekleyin:

    ```csharp
    private void OutputCommandHandler(object sender, EventArgs e)
    {
    }
    ```

5. TestOutput oluşturucus unda, komut işleyicisini OutputCommandHandler olarak değiştirebilirsiniz. Komutları ekleyen bölüm şu şekildedir:

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

6. Aşağıdaki bölümlerde Çıkış bölmesiyle ilgilenmenin farklı yollarının yer alan farklı yöntemleri vardır. Bu yöntemleri yönteminin gövdesine `OutputCommandHandler()` çağırebilirsiniz. Örneğin, aşağıdaki kod sonraki `CreatePane()` bölümde verilen yöntemini ekler.

    ```csharp
    private void OutputCommandHandler(object sender, EventArgs e)
    {
        CreatePane(new Guid(), "Created Pane", true, false);
    }
    ```

## <a name="create-an-output-window-with-ivsoutputwindow"></a>IVsOutputWindow ile Çıkış penceresi oluşturma
 Bu örnekte, arabirimini kullanarak yeni **bir Çıkış** penceresi bölmesi oluşturma <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow> gösterilir.

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

 Önceki bölümde verilen uzantıya bu yöntemi eklersiniz, **TestOutput** Çağır komutuna tıklarsanız Çıkış penceresinin Çıkış penceresinin Şu çıkışta  olduğunu **görebilirsiniz: Çıktıyı göster: CreatedPane** ve bölmenin kendisinde Bu Oluşturuldu Bölmesidir. 

## <a name="create-an-output-window-with-outputwindow"></a>OutputWindow ile Çıkış penceresi oluşturma
 Bu örnekte, nesnesini kullanarak **çıkış** penceresi bölmesi oluşturma <xref:EnvDTE.OutputWindow> gösterilir.

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

 Koleksiyon <xref:EnvDTE.OutputWindowPanes> başlığına göre  bir Çıkış penceresi bölmesi alasınız ancak bölme başlıklarının benzersiz olması garanti edilemez. Bir başlığın benzersizliği konusunda şüpheniz varsa, <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputWindow.GetPane%2A> GUID'sini kullanarak doğru bölmeyi almak için yöntemini kullanın.

 Önceki bölümde verilen uzantıya bu yöntemi eklersiniz, **TestOutput** Çağır komutuna tıklarsanız Çıkış penceresinin çıkışını **göster: DTEPane** ve bölmenin kendisinde **DTE** Bölmesi Eklendi sözcüklerinin yer alır.

## <a name="delete-an-output-window"></a>Çıkış penceresini silme
 Bu örnekte çıkış penceresi bölmesinin **nasıl silinecekleri** gösterilir.

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

 Önceki bölümde verilen uzantıya bu yöntemi eklersiniz, **TestOutput** Çağır komutuna tıklarsanız Çıkış penceresinin  çıkışını göster: Yeni  Bölme ve bölmenin kendisinde Oluşturulan Bölme eklendi sözcüklerinin yer alır. **TestOutput'u Çağır komutuna** yeniden tıklarsanız bölme silinir.

## <a name="get-the-general-pane-of-the-output-window"></a>Çıkış penceresinin Genel bölmesini al
 Bu örnekte Çıkış penceresinin yerleşik Genel **bölmesinin** nasıl elde **edilecekleri gösterilir.**

```csharp
IVsOutputWindowPane GetGeneralPane()
{
    return (IVsOutputWindowPane)GetService(
        typeof(SVsGeneralOutputWindowPane));
}
```

 Önceki bölümde verilen uzantıya bu yöntemi eklersiniz, **TestOutput** Çağır komutuna tıklarsanız Çıkış penceresinde  bölmede Genel Bulundu bölmesi sözcüklerini görebilirsiniz. 

## <a name="get-the-build-pane-of-the-output-window"></a>Çıkış penceresinin Derleme bölmesini al
 Bu örnekte Derleme bölmesinin nasıl **bulunarak** yaz olduğu gösterilir. Derleme **bölmesi** varsayılan olarak etkinleştirilmez, ayrıca etkinleştirir.

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
