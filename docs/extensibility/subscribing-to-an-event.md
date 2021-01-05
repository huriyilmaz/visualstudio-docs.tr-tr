---
title: Bir olaya abone olma | Microsoft Docs
description: Visual Studio SDK 'da çalışan bir belge tablosundaki olaylara yanıt veren bir araç penceresi oluşturmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- running document table (RDT), responding to events
- running document table (RDT), subscribing to events
ms.assetid: e94a4fea-94df-488e-8560-9538413422bc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c739dad7be8d2a000662eca478bc117699694c8a
ms.sourcegitcommit: 94a57a7bda3601b83949e710a5ca779c709a6a4e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/21/2020
ms.locfileid: "97715879"
---
# <a name="subscribing-to-an-event"></a>Bir Olaya Abone Olma
Bu izlenecek yol, çalışan bir belge tablosundaki (RDT) olaylara yanıt veren bir araç penceresinin nasıl oluşturulacağını açıklar. Bir araç penceresi, uygulayan bir kullanıcı denetimini barındırır <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents> . <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A>Yöntemi, arabirimini olaylara bağlar.

## <a name="prerequisites"></a>Ön koşullar
 Visual Studio 2015 ' den başlayarak, Visual Studio SDK 'sını indirme merkezinden yüklememeyin. Visual Studio kurulumuna isteğe bağlı bir özellik olarak dahildir. VS SDK ' yı daha sonra da yükleyebilirsiniz. Daha fazla bilgi için bkz. [Visual Studio SDK 'Yı yükleme](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="subscribing-to-rdt-events"></a>RDT olaylarına abone olma

#### <a name="to-create-an-extension-with-a-tool-window"></a>Bir araç penceresi ile uzantı oluşturmak için

1. VSıX şablonunu kullanarak **rdmpl** adlı bir proje oluşturun ve **RDTExplorerWindow** adlı özel bir araç penceresi öğesi şablonu ekleyin.

     Araç penceresiyle uzantı oluşturma hakkında daha fazla bilgi için bkz. [bir araç penceresi Ile uzantı oluşturma](../extensibility/creating-an-extension-with-a-tool-window.md).

#### <a name="to-subscribe-to-rdt-events"></a>RDT olaylarına abone olmak için

1. RDTExplorerWindowControl. xaml dosyasını açın ve adlı düğmeyi silin `button1` . Bir <xref:System.Windows.Forms.ListBox> denetim ekleyin ve varsayılan adı kabul edin. Grid öğesi şöyle görünmelidir:

    ```xml
    <Grid>
        <StackPanel Orientation="Vertical" Margin="-10,10,10,0">
            <TextBlock Margin="10" HorizontalAlignment="Center">RDTExplorerWindow</TextBlock>
            <ListBox x:Name="listBox" Height="100" />
        </StackPanel>
    </Grid>
    ```

2. Kod görünümünde RDTExplorerWindow.cs dosyasını açın. Aşağıdaki using yönergelerini dosyanın başlangıcına ekleyin.

    ```csharp
    using Microsoft.VisualStudio;
    using Microsoft.VisualStudio.Shell;
    using Microsoft.VisualStudio.Shell.Interop;
    ```

3. Sınıfı, `RDTExplorerWindow` sınıfından Türetmenin yanı sıra arabirimini de uyguladığı şekilde değiştirin <xref:Microsoft.VisualStudio.Shell.ToolWindowPane> <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents> .

    ```csharp
    public class RDTExplorerWindow : ToolWindowPane, IVsRunningDocTableEvents
    {. . .}
    ```

4. Uygulayın <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents> .

    - Arabirimini uygulayın. İmleci IVsRunningDocTableEvents adına yerleştirin. Sol kenar boşluğunda bir ampul görmeniz gerekir. Ampul sağ tarafındaki aşağı oka tıklayın ve **arabirim Uygula**' yı seçin.

5. Arabirimindeki her yöntemde `throw new NotImplementedException();` aşağıdaki satırı ile değiştirin:

    ```csharp
    return VSConstants.S_OK;
    ```

6. RDTExplorerWindow sınıfına bir tanımlama bilgisi alanı ekleyin.

    ```csharp
    private uint rdtCookie;
    ```

     Bu, yöntemi tarafından döndürülen tanımlama bilgisini barındırır <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A> .

7. RDT olaylarına kaydolmak için RDTExplorerWindow 'un Initialize () yöntemini geçersiz kılın. Araç bölmesinde değil, her zaman ToolWindowPane Initialize () yönteminde Hizmetleri almalısınız.

    ```csharp
    protected override void Initialize()
    {
        IVsRunningDocumentTable rdt = (IVsRunningDocumentTable)
        this.GetService(typeof(SVsRunningDocumentTable));
        rdt.AdviseRunningDocTableEvents(this, out rdtCookie);
    }
    ```

     <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>Hizmet bir arabirim elde etmek için çağırılır <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable> . <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A>Yöntemi, RDT olaylarını <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents> Bu durumda bir rdbir nesnesi olan bir nesneye bağlar.

8. RDTExplorerWindow 'un Dispose () yöntemini güncelleştirin.

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

     <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnadviseRunningDocTableEvents%2A>Yöntemi, `RDTExplorer` ve RDT olay bildirimi arasındaki bağlantıyı siler.

9. <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnBeforeLastDocumentUnlock%2A>Deyimden hemen önce, işleyicinin gövdesine aşağıdaki satırı ekleyin `return` .

    ```csharp
    public int OnBeforeLastDocumentUnlock(uint docCookie, uint dwRDTLockType, uint dwReadLocksRemaining, uint dwEditLocksRemaining)
    {
        ((RDTExplorerWindowControl)this.Content).listBox.Items.Add("Entering OnBeforeLastDocumentUnlock");
        return VSConstants.S_OK;
    }
    ```

10. <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnAfterFirstDocumentLock%2A>İşleyicinin gövdesine ve liste kutusunda görmek istediğiniz diğer olaylara benzer bir satır ekleyin.

    ```csharp
    public int OnAfterFirstDocumentLock(uint docCookie, uint dwRDTLockType, uint dwReadLocksRemaining, uint dwEditLocksRemaining)
    {
        ((RDTExplorerWindowControl)this.Content).listBox.Items.Add("Entering OnAfterFirstDocumentLock");
        return VSConstants.S_OK;
    }
    ```

11. Projeyi derleyin ve hata ayıklamayı başlatın. Visual Studio deneysel örneği görüntülenir.

12. **RDTExplorerWindow** (**Görünüm/diğer pencereler/RDTExplorerWindow**) öğesini açın.

     **RDTExplorerWindow** penceresi boş bir olay listesi ile açılır.

13. Bir çözüm açın veya oluşturun.

     `OnBeforeLastDocument`Ve `OnAfterFirstDocument` olayları harekete geçirildiğinde, olay listesinde her bir olayın bildirimi görünür.
