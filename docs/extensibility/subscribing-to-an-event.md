---
title: Bir Olay | Microsoft Docs
description: Visual Studio SDK'sı içinde çalışan bir belge tablosunda olaylara yanıt veren bir araç penceresi Visual Studio öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- running document table (RDT), responding to events
- running document table (RDT), subscribing to events
ms.assetid: e94a4fea-94df-488e-8560-9538413422bc
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: f35da7cb7b4129af3aaf6a3289cd2bb0c8b7d10e
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122117403"
---
# <a name="subscribing-to-an-event"></a>Bir Olaya Abone Olma
Bu kılavuzda, çalışan bir belge tablosunda (RDT) olaylara yanıt veren bir araç penceresi oluşturma açıklanır. Araç penceresi, uygulayan bir kullanıcı denetimi <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents> barındırıyor. yöntemi <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A> arabirimini olaylara bağlar.

## <a name="prerequisites"></a>Önkoşullar
 2015'Visual Studio başlayarak, Visual Studio SDK'yı indirme merkezinden yüklemezsiniz. Bu, kurulumda isteğe bağlı bir Visual Studio olarak dahil edilir. VS SDK'yı daha sonra da yükleyebilirsiniz. Daha fazla bilgi için [bkz. Visual Studio SDK'sı yükleme.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="subscribing-to-rdt-events"></a>RDT Olaylarını Abone

#### <a name="to-create-an-extension-with-a-tool-window"></a>Araç penceresiyle uzantı oluşturmak için

1. VSIX şablonunu **kullanarak RDTExplorer** adlı bir proje oluşturun ve **RDTExplorerWindow** adlı özel bir araç pencere öğesi şablonu ekleyin.

     Araç penceresiyle uzantı oluşturma hakkında daha fazla bilgi için bkz. [Araç Penceresi ile Uzantı Oluşturma.](../extensibility/creating-an-extension-with-a-tool-window.md)

#### <a name="to-subscribe-to-rdt-events"></a>RDT olaylarını abone olmak için

1. RDTExplorerWindowControl.xaml dosyasını açın ve adlı düğmeyi `button1` silin. Bir denetim <xref:System.Windows.Forms.ListBox> ekleyin ve varsayılan adı kabul et. Grid öğesi aşağıdaki gibi görünüyor olmalı:

    ```xml
    <Grid>
        <StackPanel Orientation="Vertical" Margin="-10,10,10,0">
            <TextBlock Margin="10" HorizontalAlignment="Center">RDTExplorerWindow</TextBlock>
            <ListBox x:Name="listBox" Height="100" />
        </StackPanel>
    </Grid>
    ```

2. RDTExplorerWindow.cs dosyasını kod görünümünde açın. Aşağıdaki using yönergelerini dosyanın başlangıcına ekleyin.

    ```csharp
    using Microsoft.VisualStudio;
    using Microsoft.VisualStudio.Shell;
    using Microsoft.VisualStudio.Shell.Interop;
    ```

3. `RDTExplorerWindow`sınıfını, sınıfından türetmenin yanı sıra <xref:Microsoft.VisualStudio.Shell.ToolWindowPane> arabirimini uygulayan şekilde <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents> değiştirme.

    ```csharp
    public class RDTExplorerWindow : ToolWindowPane, IVsRunningDocTableEvents
    {. . .}
    ```

4. <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>uygulama.

    - Arabirimini uygulama. İmleci IVsRunningDocTableEvents adına yerleştirin. Sol kenar boşluğunda bir ampul görüyor gerekir. Ampulün sağ yanındaki Aşağı oka tıklayın ve Arabirimi **uygulama'yı seçin.**

5. Arabirimde her yöntemde, satırı şu `throw new NotImplementedException();` şekilde değiştirin:

    ```csharp
    return VSConstants.S_OK;
    ```

6. RDTExplorerWindow sınıfına bir tanımlama bilgisi alanı ekleyin.

    ```csharp
    private uint rdtCookie;
    ```

     Bu, yöntemi tarafından döndürülen tanımlama bilgisini <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A> tutar.

7. RDT olaylarına kaydolmak için RDTExplorerWindow'un Initialize() yöntemini geçersiz kılın. Hizmetleri her zaman oluşturucuda değil ToolWindowPane'ın Initialize() yönteminde almalıdır.

    ```csharp
    protected override void Initialize()
    {
        IVsRunningDocumentTable rdt = (IVsRunningDocumentTable)
        this.GetService(typeof(SVsRunningDocumentTable));
        rdt.AdviseRunningDocTableEvents(this, out rdtCookie);
    }
    ```

     Arabirim <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable> elde etmek için hizmet <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable> çağrılır. yöntemi, RDT olaylarını uygulayan bir nesneye bağlar. Bu <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents> durumda RDTExplorer nesnesi.

8. RDTExplorerWindow'un Dispose() yöntemini güncelleştirin.

    ```csharp
    protected override void Dispose(bool disposing)
    {
        // Release the RDT cookie.
        IVsRunningDocumentTable rdt = (IVsRunningDocumentTable)
            Package.GetGlobalService(typeof(SVsRunningDocumentTable));
        rdt.UnadviseRunningDocTableEvents(rdtCookie);

        base.Dispose(disposing);
    }
    ```

     yöntemi <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnadviseRunningDocTableEvents%2A> ile RDT olay bildirimi `RDTExplorer` arasındaki bağlantıyı siler.

9. Aşağıdaki satırı, deyiminden hemen önce <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnBeforeLastDocumentUnlock%2A> işleyicinin gövdesine `return` ekleyin.

    ```csharp
    public int OnBeforeLastDocumentUnlock(uint docCookie, uint dwRDTLockType, uint dwReadLocksRemaining, uint dwEditLocksRemaining)
    {
        ((RDTExplorerWindowControl)this.Content).listBox.Items.Add("Entering OnBeforeLastDocumentUnlock");
        return VSConstants.S_OK;
    }
    ```

10. İşleyicinin gövdesine ve <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnAfterFirstDocumentLock%2A> liste kutusunda görmek istediğiniz diğer olaylara benzer bir satır ekleyin.

    ```csharp
    public int OnAfterFirstDocumentLock(uint docCookie, uint dwRDTLockType, uint dwReadLocksRemaining, uint dwEditLocksRemaining)
    {
        ((RDTExplorerWindowControl)this.Content).listBox.Items.Add("Entering OnAfterFirstDocumentLock");
        return VSConstants.S_OK;
    }
    ```

11. Projeyi derleme ve hata ayıklamayı başlatma. Deneysel Visual Studio örnek görüntülenir.

12. **RDTExplorerWindow** ( Görünüm / Diğer Windows **/ RDTExplorerWindow ) açın.**

     **RDTExplorerWindow penceresi** boş bir olay listesiyle açılır.

13. Bir çözüm açın veya oluşturun.

     Ve `OnBeforeLastDocument` olayları `OnAfterFirstDocument` başlatıldıklarında, olay listesinde her bir olayın bildirimi görüntülenir.
