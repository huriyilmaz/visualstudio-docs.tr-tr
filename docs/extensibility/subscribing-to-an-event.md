---
title: Bir Etkinliğe Abone Olma | Microsoft Dokümanlar
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
ms.openlocfilehash: 6aefe2efce897aefc26f63835844b0cc705fb5b1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699681"
---
# <a name="subscribing-to-an-event"></a>Bir Olaya Abone Olma
Bu izbis, çalışan belge tablosundaki (RDT) olaylara yanıt veren bir araç penceresinin nasıl oluşturuluğunu açıklar. Bir araç penceresi uygulayan bir <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>kullanıcı denetimi barındırıyor. Yöntem, <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A> arabirimi olaylara bağlar.

## <a name="prerequisites"></a>Ön koşullar
 Visual Studio 2015'ten itibaren Visual Studio SDK'yı indirme merkezinden yüklemezsiniz. Visual Studio kurulumunda isteğe bağlı bir özellik olarak yer almaktadır. VS SDK'yı daha sonra da yükleyebilirsiniz. Daha fazla bilgi için Visual [Studio SDK'yı yükleme ye](../extensibility/installing-the-visual-studio-sdk.md)bakın.

## <a name="subscribing-to-rdt-events"></a>RDT Etkinliklerine Abone Olma

#### <a name="to-create-an-extension-with-a-tool-window"></a>Araç penceresi olan bir uzantı oluşturmak için

1. VSIX şablonu kullanarak **RDTExplorer** adında bir proje oluşturun ve **RDTExplorerWindow**adlı özel bir araç penceresi öğesi şablonu ekleyin.

     Araç penceresiyle uzantı oluşturma hakkında daha fazla bilgi için [bkz.](../extensibility/creating-an-extension-with-a-tool-window.md)

#### <a name="to-subscribe-to-rdt-events"></a>RDT etkinliklerine abone olmak için

1. RDTExplorerWindowControl.xaml dosyasını açın ve `button1`adlı düğmeyi silin. Denetim <xref:System.Windows.Forms.ListBox> ekleyin ve varsayılan adı kabul edin. Izgara öğesi aşağıdaki gibi görünmelidir:

    ```xml
    <Grid>
        <StackPanel Orientation="Vertical" Margin="-10,10,10,0">
            <TextBlock Margin="10" HorizontalAlignment="Center">RDTExplorerWindow</TextBlock>
            <ListBox x:Name="listBox" Height="100" />
        </StackPanel>
    </Grid>
    ```

2. RDTExplorerWindow.cs dosyasını kod görünümünde açın. Dosyanın başlangıcına yönergeleri kullanarak aşağıdaki yönergeleri ekleyin.

    ```csharp
    using Microsoft.VisualStudio;
    using Microsoft.VisualStudio.Shell;
    using Microsoft.VisualStudio.Shell.Interop;
    ```

3. `RDTExplorerWindow` Sınıfı değiştirin, <xref:Microsoft.VisualStudio.Shell.ToolWindowPane> böylece, sınıftan türeyen ek olarak, <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents> arabirimi uygular.

    ```csharp
    public class RDTExplorerWindow : ToolWindowPane, IVsRunningDocTableEvents
    {. . .}
    ```

4. Uygulayın. <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>

    - Arabirimi uygulayın. İmleci IVsRunningDocTableEvents adına yerleştirin. Sol kenar boşluğunda bir ampul görmelisiniz. Ampulün sağındaki Aşağı ok'u tıklatın ve **arabirimi Uygula'yı**seçin.

5. Arabirimdeki her yöntemde, `throw new NotImplementedException();` satırı şuyla değiştirin:

    ```csharp
    return VSConstants.S_OK;
    ```

6. RDTExplorerWindow sınıfına bir çerez alanı ekleyin.

    ```csharp
    private uint rdtCookie;
    ```

     Bu <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A> yöntem tarafından döndürülen çerez tutar.

7. RDT olaylarına kaydolmak için RDTExplorerWindow'un Initialize() yöntemini geçersiz kılın. Her zaman ToolWindowPane's Initialize() yönteminde, yapıcı değil hizmetleri almalısınız.

    ```csharp
    protected override void Initialize()
    {
        IVsRunningDocumentTable rdt = (IVsRunningDocumentTable)
        this.GetService(typeof(SVsRunningDocumentTable));
        rdt.AdviseRunningDocTableEvents(this, out rdtCookie);
    }
    ```

     Hizmet <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable> bir <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable> arabirim elde etmek için çağrılır. Yöntem, <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A> RDT olaylarını bu durumda <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents>bir RDTExplorer nesnesini uygulayan bir nesneye bağlar.

8. RDTExplorerWindow'un Elden Çıkar() yöntemini güncelleştirin.

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

     Yöntem, <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.UnadviseRunningDocTableEvents%2A> RDT olay `RDTExplorer` bildirimi ile arasındaki bağlantıyı siler.

9. İfadeden hemen önce <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnBeforeLastDocumentUnlock%2A> işleyicinin gövdesine aşağıdaki satırı ekleyin. `return`

    ```csharp
    public int OnBeforeLastDocumentUnlock(uint docCookie, uint dwRDTLockType, uint dwReadLocksRemaining, uint dwEditLocksRemaining)
    {
        ((RDTExplorerWindowControl)this.Content).listBox.Items.Add("Entering OnBeforeLastDocumentUnlock");
        return VSConstants.S_OK;
    }
    ```

10. <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents.OnAfterFirstDocumentLock%2A> İşleyicinin gövdesine ve liste kutusunda görmek istediğiniz diğer olaylara benzer bir satır ekleyin.

    ```csharp
    public int OnAfterFirstDocumentLock(uint docCookie, uint dwRDTLockType, uint dwReadLocksRemaining, uint dwEditLocksRemaining)
    {
        ((RDTExplorerWindowControl)this.Content).listBox.Items.Add("Entering OnAfterFirstDocumentLock");
        return VSConstants.S_OK;
    }
    ```

11. Projeyi oluşturun ve hata ayıklamaya başlayın. Visual Studio deneysel örneği görüntülenir.

12. **RDTExplorerWindow'u** açın (**Görünüm / Diğer Windows / RDTExplorerWindow**).

     **RDTExplorerWindow** penceresi boş bir olay listesiyle açılır.

13. Açın veya bir çözüm oluşturun.

     Olaylar `OnBeforeLastDocument` `OnAfterFirstDocument` ateşlendikçe, her olayın bildirimi olay listesinde görünür.
