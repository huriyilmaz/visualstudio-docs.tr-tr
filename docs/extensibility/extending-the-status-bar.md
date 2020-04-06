---
title: Durum Çubuğunu Genişletme | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- status bars, about status bars
- status bars, overview
ms.assetid: f955115c-4c5f-45ec-b41b-365868c5ec0c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: aa62326d82d81f7ee4d10a838209364355cc488e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711537"
---
# <a name="extend-the-status-bar"></a>Durum çubuğunu genişletme
Bilgileri görüntülemek için IDE'nin altındaki Visual Studio durum çubuğunu kullanabilirsiniz.

 Durum çubuğunu uzattığınızda, bilgileri ve kullanıcı kullanıcı larını dört bölgede görüntüleyebilirsiniz: geri bildirim bölgesi, ilerleme çubuğu, animasyon bölgesi ve tasarımcı bölgesi. Geri bildirim bölgesi, metni görüntülemenize ve görüntülenen metni vurgulamanıza olanak tanır. İlerleme çubuğu, dosyayı kaydetme gibi kısa süren işlemler için artımlı ilerleme gösterir. Animasyon bölgesi, uzun süren işlemler veya çözümde birden çok proje oluşturmak gibi belirsiz uzunlukta ki işlemler için sürekli döngülü bir animasyon görüntüler. Ve tasarımcı bölgesi imleç konumunun satır ve sütun numarasını gösterir.

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar> Arabirimi (hizmetten) kullanarak durum çubuğunu <xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar> alabilirsiniz. Buna ek olarak, bir pencere çerçevesi üzerinde sited herhangi bir nesne <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> arabirimi uygulayarak bir durum çubuğu istemci nesneolarak kaydedebilirsiniz. Bir pencere etkinleştirildiğinde, Visual Studio `IVsStatusbarUser` arabirim için bu pencerede bulunan nesneyi sorgular. Bulunursa, döndürülen arabirimdeki <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> yöntemi çağırır ve nesne durum çubuğunu bu yöntemin içinden güncelleştirebilir. Belge pencereleri, örneğin, <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> etkin hale geldiklerinde tasarımcı bölgesindeki bilgileri güncelleştirmek için yöntemi kullanabilir.

 Aşağıdaki yordamlar, bir VSIX projesi oluşturmak ve özel bir menü komutu eklemek nasıl anlamak varsayalım. Daha fazla bilgi için [bkz.](../extensibility/creating-an-extension-with-a-menu-command.md)

## <a name="modify-the-status-bar"></a>Durum çubuğunu değiştirme
 Bu yordam, metin ayarlamak ve almak, statik metin görüntülemek ve durum çubuğunun geribildirim bölgesinde görüntülenen metni vurgulamak nasıl gösterir.

### <a name="read-and-write-to-the-status-bar"></a>Durum çubuğuna okuma ve yazma

1. **TestStatusBarExtension** adında bir VSIX projesi oluşturun ve **TestStatusBarCommand**adlı bir menü komutu ekleyin.

2. *TestStatusBarCommand.cs*, komut işleyicisi`MenuItemCallback`yöntem kodunu ( ) aşağıdakilerle değiştirin:

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

3. Kodu derle ve hata ayıklamaya başlayın.

4. Visual Studio'nun deneysel örneğinde **Araçlar** menüsünü açın. Çağrı **TestStatusBarCommand** düğmesini tıklatın.

     Durum çubuğundaki metnin şimdi okuduğunu görmelisiniz biz **sadece durum çubuğuna yazdık.** ve görünen ileti kutusu aynı metne sahiptir.

### <a name="update-the-progress-bar"></a>İlerleme çubuğunu güncelleştirme

1. Bu yordamda, ilerleme çubuğunun nasıl başlatılmasını ve güncelleştirilebildiğini göstereceğiz.

2. *TestStatusBarCommand.cs* dosyasını açın `MenuItemCallback` ve yöntemi aşağıdaki kodla değiştirin:

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

3. Kodu derle ve hata ayıklamaya başlayın.

4. Visual Studio'nun deneysel örneğinde **Araçlar** menüsünü açın. **TestStatusBarCommand'ı Çağır** düğmesini tıklatın.

     Durum çubuğundaki metnin artık ilerleme **çubuğuna Yazma'yı** okuduğunu görmeniz gerekir. İlerleme çubuğunun her saniye 20 saniye boyunca güncelleştirileni de görmelisiniz. Bundan sonra durum çubuğu ve ilerleme çubuğu temizlenir.

### <a name="display-an-animation"></a>Animasyon görüntüleme

1. Durum çubuğu, uzun süren bir işlemi (örneğin, bir çözümde birden çok proje oluşturma) gösteren bir döngü animasyonu görüntüler. Bu animasyonu görmüyorsanız, doğru **Araç** > **Seçenekleri** ayarlarına sahip olduğundan emin olun:

     **Araçlar** > **Seçenekleri** > **Genel** sekmesine gidin ve **istemci performansına göre görsel deneyimi otomatik olarak ayarlayın.** Ardından alt seçeneği ni işaretleyin **Zengin istemci görsel deneyimini etkinleştirin.** Artık projeyi visual studio'nun deneysel örneğinde oluştururken animasyonu görebilmelisiniz.

     Bu yordamda, bir proje veya çözüm oluşturmayı temsil eden standart Visual Studio animasyonu görüntülenir.

2. *TestStatusBarCommand.cs* dosyasını açın `MenuItemCallback` ve yöntemi aşağıdaki kodla değiştirin:

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

3. Kodu derle ve hata ayıklamaya başlayın.

4. Visual Studio'nun deneysel örneğinde **Araçlar** menüsünü açın ve **TestStatusBarCommand'ı Çağır'ı**tıklatın.

     İleti kutusunu gördüğünüzde, en sağdaki durum çubuğundaki animasyonu da görmeniz gerekir. İleti kutusunu kapattınğınızda, animasyon kaybolur.
