---
title: Durum çubuğunu genişletme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- status bars, about status bars
- status bars, overview
ms.assetid: f955115c-4c5f-45ec-b41b-365868c5ec0c
caps.latest.revision: 24
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 28fc1155279ec624cea576b5a70a25800d4ff837
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204417"
---
# <a name="extending-the-status-bar"></a>Durum Çubuğunu Genişletme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bilgileri göstermek için IDE 'nin altındaki Visual Studio durum çubuğunu kullanabilirsiniz.  
  
 Durum çubuğunu genişlettiğinizde, bilgileri ve Kullanıcı arabirimini dört bölgede görüntüleyebilirsiniz: geri bildirim bölgesi, ilerleme çubuğu, animasyon bölgesi ve tasarımcı bölgesi. Geri bildirim bölgesi, metin görüntülemenizi ve görüntülenen metni vurgulamanızı sağlar. İlerleme çubuğu, bir dosyayı kaydetme gibi kısa süreli işlemler için artımlı ilerlemeyi gösterir. Animasyon bölgesi, bir çözümde birden çok proje oluşturmak gibi uzun süre çalışan işlemler veya belirlenmeyen uzunluktaki işlem için sürekli olarak kıvrımlı bir animasyon görüntüler. Ve tasarımcı bölgesi, imleç konumunun satır ve sütun numarasını gösterir.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar>Arabirimi (hizmetten) kullanarak durum çubuğunu alabilirsiniz <xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar> . Ayrıca, bir pencere çerçevesinde yer alan herhangi bir nesne, arabirimini uygulayarak bir durum çubuğu istemci nesnesi olarak kayıt yapabilir <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> . Her pencere etkinleştirildiğinde, Visual Studio bu pencerede arabirim için nesneyi sorgular `IVsStatusbarUser` . Bulunursa, <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> döndürülen arabirimde yöntemini çağırır ve nesne durum çubuğunu bu yöntemin içinden güncelleştirebilir. Belge pencereleri, örneğin, <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> etkin hale geldiğinde tasarımcı bölgesindeki bilgileri güncelleştirmek için yöntemini kullanabilir.  
  
 Aşağıdaki yordamlarda, bir VSıX projesi oluşturma ve özel bir menü komutu ekleme işlemlerinin nasıl yapılacağı varsayılmaktadır. Daha fazla bilgi için, bkz. [bir menü komutuyla uzantı oluşturma](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
## <a name="modifying-the-status-bar"></a>Durum çubuğunu değiştirme  
 Bu yordamda, metin ayarlama ve alma, statik metin görüntüleme ve durum çubuğunun geri bildirim bölgesinde görüntülenen metni vurgulamanın nasıl yapılacağı gösterilir.  
  
#### <a name="reading-and-writing-to-the-status-bar"></a>Durum çubuğunu okuma ve yazma  
  
1. **TestStatusBarExtension** ADLı bir VSIX projesi oluşturun ve **TestStatusBarCommand**adlı bir menü komutu ekleyin.  
  
2. TestStatusBarCommand.cs içinde, komut işleyici yöntemi kodunu (Menuıitemcallback) aşağıdaki ile değiştirin:  
  
    ```csharp  
    private void MenuItemCallback(object sender, EventArgs e)  
    {  
        IVsStatusbar statusBar = (IVsStatusbar)ServiceProvider.GetService(typeof(SVsStatusbar));  
  
        // Make sure the status bar is not frozen  
        int frozen;  
  
        statusBar.IsFrozen(out frozen);  
  
        if (frozen != 0)   
        {  
            statusBar.FreezeOutput(0);  
        }  
  
        // Set the status bar text and make its display static.  
        statusBar.SetText("We just wrote to the status bar.");  
  
        // Freeze the status bar.  
        statusBar.FreezeOutput(1);  
  
        // Get the status bar text.   
        string text;  
        statusBar.GetText(out text);  
        System.Windows.Forms.MessageBox.Show(text);  
  
        // Clear the status bar text.  
        statusBar.FreezeOutput(0);  
        statusBar.Clear();  
    }  
    ```  
  
3. Kodu derleyin ve hata ayıklamayı başlatın.  
  
4. Visual Studio 'nun Deneysel örneğindeki **Araçlar** menüsünü açın. **Invoke TestStatusBarCommand** düğmesine tıklayın.  
  
     Durum çubuğundaki metnin şimdi **"durum çubuğuna yazdığımız"** okuduğunu görürsünüz. ve görüntülenen ileti kutusu aynı metne sahiptir.  
  
#### <a name="updating-the-progress-bar"></a>İlerleme çubuğunu güncelleştirme  
  
1. Bu yordamda ilerleme çubuğunun nasıl başlatılacağını ve güncelleştirilmesini göstereceğiz.  
  
2. TestStatusBarCommand.cs dosyasını açın ve Menuıitemcallback metodunu şu kodla değiştirin:  
  
    ```csharp  
    private void MenuItemCallback(object sender, EventArgs e)  
    {  
        IVsStatusbar statusBar = (IVsStatusbar)ServiceProvider.GetService(typeof(SVsStatusbar));  
        uint cookie = 0;  
        string label = "Writing to the progress bar";  
  
        // Initialize the progress bar.  
        statusBar.Progress(ref cookie, 1, "", 0, 0);  
  
        for (uint i = 0, total = 20; i <= total; i++)  
        {  
            // Display progress every second.  
            statusBar.Progress(ref cookie, 1, label, i, total);  
            System.Threading.Thread.Sleep(1000);  
        }  
  
        // Clear the progress bar.  
        statusBar.Progress(ref cookie, 0, "", 0, 0);  
    }  
    ```  
  
3. Kodu derleyin ve hata ayıklamayı başlatın.  
  
4. Visual Studio 'nun Deneysel örneğindeki **Araçlar** menüsünü açın. **Çağır TestStatusBarCommand** düğmesine tıklayın.  
  
     Durum çubuğundaki metnin şimdi **"ilerleme çubuğuna yazma** " işlemini okuduğunu görmeniz gerekir. Ayrıca, 20 saniye boyunca ilerleme çubuğunun her saniye güncelleştirilmesini görmeniz gerekir. Durum çubuğu ve ilerleme çubuğu temizlenmeden sonra.  
  
#### <a name="displaying-an-animation"></a>Animasyon görüntüleme  
  
1. Durum çubuğu, uzun süre çalışan bir işlem (örneğin, bir çözümde birden çok proje oluşturma) gösteren bir döngü animasyonu görüntüler. Bu animasyonu görmüyorsanız, doğru **Araçlar/Seçenekler** ayarlarına sahip olduğunuzdan emin olun:  
  
     **Araçlar/Seçenekler/genel** sekmesine gidin ve **Istemci performansına bağlı olarak görsel deneyimi otomatik olarak ayarla**seçeneğinin işaretini kaldırın. Ardından **zengin istemci görsel deneyimini etkinleştir**alt seçeneğini işaretleyin. Şimdi Visual Studio 'nun deneysel örneğinde projeyi derlediğinizde animasyonu görebilmeniz gerekir.  
  
     Bu yordamda, bir proje veya çözüm oluşturmayı temsil eden standart Visual Studio animasyonunu görüntüliyoruz.  
  
2. TestStatusBarCommand.cs dosyasını açın ve Menuıitemcallback metodunu şu kodla değiştirin:  
  
    ```csharp  
    private void MenuItemCallback(object sender, EventArgs e)  
    {  
        IVsStatusbar statusBar =(IVsStatusbar)ServiceProvider.GetService(typeof(SVsStatusbar));  
  
        // Use the standard Visual Studio icon for building.  
        object icon = (short)Microsoft.VisualStudio.Shell.Interop.Constants.SBAI_Build;  
  
        // Display the icon in the Animation region.  
        statusBar.Animation(1, ref icon);  
  
        // The message box pauses execution for you to look at the animation.  
        System.Windows.Forms.MessageBox.Show("showing?");  
  
        // Stop the animation.   
        statusBar.Animation(0, ref icon);  
    }  
    ```  
  
3. Kodu derleyin ve hata ayıklamayı başlatın.  
  
4. Visual Studio 'nun Deneysel örneğindeki **Araçlar** menüsünü açın ve **TestStatusBarCommand çağır**' a tıklayın.  
  
     İleti kutusunu gördüğünüzde, en sağdaki durum çubuğunda animasyonu de görmeniz gerekir. İleti kutusunu kapatmak için animasyon kaybolur.
