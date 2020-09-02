---
title: Bir olaya abone olma | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- running document table (RDT), responding to events
- running document table (RDT), subscribing to events
ms.assetid: e94a4fea-94df-488e-8560-9538413422bc
caps.latest.revision: 36
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 324e74c78f01da47c544b5f640ad0bd9052a1bb4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68160554"
---
# <a name="subscribing-to-an-event"></a>Bir Olaya Abone Olma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu izlenecek yol, çalışan bir belge tablosundaki (RDT) olaylara yanıt veren bir araç penceresinin nasıl oluşturulacağını açıklar. Bir araç penceresi, uygulayan bir kullanıcı denetimini barındırır <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocTableEvents> . <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.AdviseRunningDocTableEvents%2A>Yöntemi, arabirimini olaylara bağlar.  
  
## <a name="prerequisites"></a>Önkoşullar  
 Visual Studio 2015 ' den başlayarak, Visual Studio SDK 'sını indirme merkezinden yüklememeyin. Visual Studio kurulumuna isteğe bağlı bir özellik olarak dahildir. VS SDK ' yı daha sonra da yükleyebilirsiniz. Daha fazla bilgi için bkz. [Visual Studio SDK 'Yı yükleme](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="subscribing-to-rdt-events"></a>RDT olaylarına abone olma  
  
#### <a name="to-create-an-extension-with-a-tool-window"></a>Bir araç penceresi ile uzantı oluşturmak için  
  
1. VSıX şablonunu kullanarak **rdmpl** adlı bir proje oluşturun ve **RDTExplorerWindow**adlı özel bir araç penceresi öğesi şablonu ekleyin.  
  
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
  
2. Kod görünümünde RDTExplorerWindow.cs dosyasını açın. Aşağıdaki using deyimlerini dosyanın başlangıcına ekleyin.  
  
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
