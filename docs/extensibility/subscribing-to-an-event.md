---
title: Bir olaya abone olma | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- running document table (RDT), responding to events
- running document table (RDT), subscribing to events
ms.assetid: e94a4fea-94df-488e-8560-9538413422bc
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bd2933ee3e0e162740f0c7eb3f3c2307e17ec46d
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72647925"
---
# <a name="subscribing-to-an-event"></a>Bir Olaya Abone Olma
Bu izlenecek yol, çalışan bir belge tablosundaki (RDT) olaylara yanıt veren bir araç penceresinin nasıl oluşturulacağını açıklar. Bir araç penceresi, <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents> uygulayan bir kullanıcı denetimi barındırır. @No__t_0 yöntemi arabirimi olaylara bağlar.

## <a name="prerequisites"></a>Prerequisites
 Visual Studio 2015 ' den başlayarak, Visual Studio SDK 'sını indirme merkezinden yüklememeyin. Visual Studio kurulumuna isteğe bağlı bir özellik olarak dahildir. VS SDK ' yı daha sonra da yükleyebilirsiniz. Daha fazla bilgi için bkz. [Visual Studio SDK 'Yı yükleme](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="subscribing-to-rdt-events"></a>RDT olaylarına abone olma

#### <a name="to-create-an-extension-with-a-tool-window"></a>Bir araç penceresi ile uzantı oluşturmak için

1. VSıX şablonunu kullanarak **rdmpl** adlı bir proje oluşturun ve **RDTExplorerWindow**adlı özel bir araç penceresi öğesi şablonu ekleyin.

     Araç penceresiyle uzantı oluşturma hakkında daha fazla bilgi için bkz. [bir araç penceresi Ile uzantı oluşturma](../extensibility/creating-an-extension-with-a-tool-window.md).

#### <a name="to-subscribe-to-rdt-events"></a>RDT olaylarına abone olmak için

1. RDTExplorerWindowControl. xaml dosyasını açın ve `button1` adlı düğmeyi silin. @No__t_0 bir denetim ekleyin ve varsayılan adı kabul edin. Grid öğesi şöyle görünmelidir:

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

3. @No__t_0 sınıfını değiştirerek, <xref:Microsoft.VisualStudio.Shell.ToolWindowPane> sınıfından Türetmenin yanı sıra <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents> arabirimini uygular.

    ```csharp
    public class RDTExplorerWindow : ToolWindowPane, IVsRunningDocTableEvents
    {. . .}
    ```

4. @No__t_0 uygulayın.

    - Arabirimini uygulayın. İmleci IVsRunningDocTableEvents adına yerleştirin. Sol kenar boşluğunda bir ampul görmeniz gerekir. Ampul sağ tarafındaki aşağı oka tıklayın ve **arabirim Uygula**' yı seçin.

5. Arabirimindeki her yöntemde, satır `throw new NotImplementedException();` şu şekilde değiştirin:

    ```csharp
    return VSConstants.S_OK;
    ```

6. RDTExplorerWindow sınıfına bir tanımlama bilgisi alanı ekleyin.

    ```csharp
    private uint rdtCookie;
    ```

     Bu, <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A> yöntemi tarafından döndürülen tanımlama bilgisini barındırır.

7. RDT olaylarına kaydolmak için RDTExplorerWindow 'un Initialize () yöntemini geçersiz kılın. Araç bölmesinde değil, her zaman ToolWindowPane Initialize () yönteminde Hizmetleri almalısınız.

    ```csharp
    protected override void Initialize()
    {
        IVsRunningDocumentTable rdt = (IVsRunningDocumentTable)
        this.GetService(typeof(SVsRunningDocumentTable));
        rdt.AdviseRunningDocTableEvents(this, out rdtCookie);
    }
    ```

     @No__t_0 hizmeti <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable> arabirimini almak için çağrılır. @No__t_0 yöntemi, RDT olaylarını Bu örnekte bir Rdbir nesnesi olan <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents> uygulayan bir nesneye bağlar.

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

     @No__t_0 yöntemi `RDTExplorer` ile RDT olay bildirimi arasındaki bağlantıyı siler.

9. Aşağıdaki satırı, `return` ifadesinden hemen önce <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnBeforeLastDocumentUnlock%2A> işleyicisinin gövdesine ekleyin.

    ```csharp
    public int OnBeforeLastDocumentUnlock(uint docCookie, uint dwRDTLockType, uint dwReadLocksRemaining, uint dwEditLocksRemaining)
    {
        ((RDTExplorerWindowControl)this.Content).listBox.Items.Add("Entering OnBeforeLastDocumentUnlock");
        return VSConstants.S_OK;
    }
    ```

10. @No__t_0 işleyicisinin gövdesine ve liste kutusunda görmek istediğiniz diğer olaylara benzer bir satır ekleyin.

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

     @No__t_0 ve `OnAfterFirstDocument` olaylar tetiklendiğinde, her olay bildirimi olay listesinde görünür.
