---
title: Durum çubuğunu genişletme | Microsoft Docs
description: IDE 'nin altında, bilgi görüntüleyen Visual Studio durum çubuğunu genişletmeyi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- status bars, about status bars
- status bars, overview
ms.assetid: f955115c-4c5f-45ec-b41b-365868c5ec0c
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7776c7fa35cd7ac06dec60ced3604cb67c96da4a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99903193"
---
# <a name="extend-the-status-bar"></a>Durum çubuğunu genişletme
Bilgileri göstermek için IDE 'nin altındaki Visual Studio durum çubuğunu kullanabilirsiniz.

 Durum çubuğunu genişlettiğinizde, bilgileri ve Kullanıcı arabirimini dört bölgede görüntüleyebilirsiniz: geri bildirim bölgesi, ilerleme çubuğu, animasyon bölgesi ve tasarımcı bölgesi. Geri bildirim bölgesi, metin görüntülemenizi ve görüntülenen metni vurgulamanızı sağlar. İlerleme çubuğu, bir dosyayı kaydetme gibi kısa süreli işlemler için artımlı ilerlemeyi gösterir. Animasyon bölgesi, bir çözümde birden çok proje oluşturmak gibi uzun süre çalışan işlemler veya belirlenmeyen uzunluktaki işlem için sürekli olarak kıvrımlı bir animasyon görüntüler. Ve tasarımcı bölgesi, imleç konumunun satır ve sütun numarasını gösterir.

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar>Arabirimi (hizmetten) kullanarak durum çubuğunu alabilirsiniz <xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar> . Ayrıca, bir pencere çerçevesinde yer alan herhangi bir nesne, arabirimini uygulayarak bir durum çubuğu istemci nesnesi olarak kayıt yapabilir <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> . Her pencere etkinleştirildiğinde, Visual Studio bu pencerede arabirim için nesneyi sorgular `IVsStatusbarUser` . Bulunursa, <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> döndürülen arabirimde yöntemini çağırır ve nesne durum çubuğunu bu yöntemin içinden güncelleştirebilir. Belge pencereleri, örneğin, <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> etkin hale geldiğinde tasarımcı bölgesindeki bilgileri güncelleştirmek için yöntemini kullanabilir.

 Aşağıdaki yordamlarda, bir VSıX projesi oluşturma ve özel bir menü komutu ekleme işlemlerinin nasıl yapılacağı varsayılmaktadır. Daha fazla bilgi için bkz. [bir menü komutuyla uzantı oluşturma](../extensibility/creating-an-extension-with-a-menu-command.md).

## <a name="modify-the-status-bar"></a>Durum çubuğunu değiştirme
 Bu yordamda, metin ayarlama ve alma, statik metin görüntüleme ve durum çubuğunun geri bildirim bölgesinde görüntülenen metni vurgulamanın nasıl yapılacağı gösterilir.

### <a name="read-and-write-to-the-status-bar"></a>Durum çubuğunu oku ve yaz

1. **TestStatusBarExtension** ADLı bir VSIX projesi oluşturun ve **TestStatusBarCommand** adlı bir menü komutu ekleyin.

2. *TestStatusBarCommand.cs* içinde, komut işleyici yöntemi kodunu ( `MenuItemCallback` ) aşağıdaki kodla değiştirin:

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

     Durum çubuğundaki metnin artık **durum çubuğuna Yazdığımğunu** okuduğunu görmeniz gerekir. ve görüntülenen ileti kutusu aynı metne sahiptir.

### <a name="update-the-progress-bar"></a>İlerleme çubuğunu güncelleştirme

1. Bu yordamda ilerleme çubuğunun nasıl başlatılacağını ve güncelleştirilmesini göstereceğiz.

2. *TestStatusBarCommand.cs* dosyasını açın ve `MenuItemCallback` yöntemi aşağıdaki kodla değiştirin:

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

     Durum çubuğundaki metnin şimdi **ilerleme çubuğuna yazmayı** okuyabileceğini görmeniz gerekir. Ayrıca, 20 saniye boyunca ilerleme çubuğunun her saniye güncelleştirilmesini görmeniz gerekir. Durum çubuğu ve ilerleme çubuğu temizlenmeden sonra.

### <a name="display-an-animation"></a>Animasyon görüntüleme

1. Durum çubuğu, uzun süre çalışan bir işlem (örneğin, bir çözümde birden çok proje oluşturma) gösteren bir döngü animasyonu görüntüler. Bu animasyonu görmüyorsanız, doğru **Araçlar**  >  **seçenekleri** ayarlarına sahip olduğunuzdan emin olun:

     **Araçlar**  >  **Seçenekler**  >  **genel** sekmesine gidin ve **istemci performansına göre görsel deneyimi otomatik olarak ayarla** seçeneğinin işaretini kaldırın. Ardından **zengin istemci görsel deneyimini etkinleştir** alt seçeneğini işaretleyin. Şimdi Visual Studio 'nun deneysel örneğinde projeyi derlediğinizde animasyonu görebilmeniz gerekir.

     Bu yordamda, bir proje veya çözüm oluşturmayı temsil eden standart Visual Studio animasyonunu görüntüliyoruz.

2. *TestStatusBarCommand.cs* dosyasını açın ve `MenuItemCallback` yöntemi aşağıdaki kodla değiştirin:

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
