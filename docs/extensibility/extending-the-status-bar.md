---
title: Durum Çubuğu'| Microsoft Docs
description: Bilgileri görüntüleyen IDE'nin Visual Studio durum çubuğunu genişletmeyi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- status bars, about status bars
- status bars, overview
ms.assetid: f955115c-4c5f-45ec-b41b-365868c5ec0c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: aa0acbd99328b55f0a15335572a0a185e1394ee85cc992cf71a59c2f52e1d9de
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121414902"
---
# <a name="extend-the-status-bar"></a>Durum çubuğunu genişletme
Bilgileri görüntülemek Visual Studio IDE'nin altındaki durum çubuğunu kullanabilirsiniz.

 Durum çubuğunu genişletken bilgileri ve kullanıcı arabirimini dört bölgede görüntülayabilirsiniz: geri bildirim bölgesi, ilerleme çubuğu, animasyon bölgesi ve tasarımcı bölgesi. Geri bildirim bölgesi, metin görüntülemenizi ve görüntülenen metni vurgulamayı sağlar. İlerleme çubuğu, bir dosyayı kaydetme gibi kısa süre çalışan işlemler için artımlı ilerlemeyi gösterir. Animasyon bölgesi, bir çözümde birden çok proje oluşturmak gibi uzun süre çalışan işlemler veya belirsiz uzunluktaki işlemler için sürekli döngülü bir animasyon görüntüler. Tasarımcı bölgesinde ise imleç konumunun satır ve sütun numarası gösterilir.

 Durum çubuğunu almak için arabirimini <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbar> (hizmetten) <xref:Microsoft.VisualStudio.Shell.Interop.SVsStatusbar> kullanın. Ayrıca, bir pencere çerçevesinde siteli herhangi bir nesne arabirimini uygulayarak durum çubuğu istemci nesnesi olarak <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser> kaydedebilirsiniz. Bir pencere etkinleştirildiğinde Visual Studio arabirimi için bu pencerede bulunan nesneyi `IVsStatusbarUser` sorgular. Bulunursa, döndürülen <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> arabirimde yöntemini çağırarak nesnesi bu yöntemin içindeki durum çubuğunu güncelleştirebilirsiniz. Örneğin belge pencereleri, etkin hale <xref:Microsoft.VisualStudio.Shell.Interop.IVsStatusbarUser.SetInfo%2A> geldiğinde tasarımcı bölgesinde bilgileri güncelleştirmek için yöntemini kullanabilir.

 Aşağıdaki yordamlarda VSIX projesi oluşturma ve özel menü komutu ekleme hakkında bilgi edinebilirsiniz. Bilgi için [bkz. Menü komutuyla uzantı oluşturma.](../extensibility/creating-an-extension-with-a-menu-command.md)

## <a name="modify-the-status-bar"></a>Durum çubuğunu değiştirme
 Bu yordamda metin ayarlama ve almaya, statik metin görüntülemeye ve durum çubuğunun geri bildirim bölgesinde görüntülenen metni vurgulama işlemleri gösterilir.

### <a name="read-and-write-to-the-status-bar"></a>Durum çubuğuna okuma ve yazma

1. **TestStatusBarExtension** adlı bir VSIX projesi oluşturun ve **TestStatusBarCommand** adlı bir menü komutu ekleyin.

2. *TestStatusBarCommand.cs* içinde, komut işleyicisi yöntem kodunu ( `MenuItemCallback` ) aşağıdakiyle değiştirin:

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

3. Kodu derle ve hata ayıklamayı başlat.

4. Deneysel **Visual Studio'nin** deneysel örneğinde Araçlar menüsünü açın. **TestStatusBarCommand Çağır düğmesine** tıklayın.

     Durum çubuğundaki metnin artık Durum çubuğuna yeni **yazdık makalesini okuduğuna bakabilirsiniz.** ve görüntülenen ileti kutusu aynı metine sahip.

### <a name="update-the-progress-bar"></a>İlerleme çubuğunu güncelleştirme

1. Bu yordamda ilerleme çubuğunu başlatmayı ve güncelleştirmeyi gösterebilirsiniz.

2. *TestStatusBarCommand.cs dosyasını* açın ve `MenuItemCallback` yöntemini aşağıdaki kodla değiştirin:

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

3. Kodu derle ve hata ayıklamayı başlat.

4. Deneysel **Visual Studio'nin** deneysel örneğinde Araçlar menüsünü açın. **TestStatusBarCommand Düğmesini Çağır'a** tıklayın.

     Durum çubuğundaki metnin artık ilerleme çubuğuna **yazma'nın okunana kadar olduğunu görüyoruz.** Ayrıca ilerleme çubuğunun 20 saniye süreyle her saniye güncelleştirilmiş olduğunu da görüyor olun. Bundan sonra durum çubuğu ve ilerleme çubuğu temiz.

### <a name="display-an-animation"></a>Animasyon görüntüleme

1. Durum çubuğunda, uzun süre çalışan bir işlemi (örneğin, bir çözümde birden çok proje oluşturmak) gösteren bir döngü animasyonu görüntülenir. Bu animasyonu görmüyorsanız doğru Araç Seçenekleri ayarlarına sahip **olduğundan**  >  **emin** olun:

     Araçlar Seçenekler Genel  >  **sekmesine**  >  **gidin** ve Görsel deneyimi istemci **performansına göre otomatik olarak ayarla'nın işaretini kaldırın.** Ardından Zengin istemci görsel deneyimini **etkinleştir alt seçeneğini işaretleyin.** Artık projeyi deneysel Visual Studio örneğinde derlemek için animasyonu Visual Studio.

     Bu yordamda, proje veya Visual Studio temsil eden standart animasyonu görüntülemektedir.

2. *TestStatusBarCommand.cs dosyasını* açın ve `MenuItemCallback` yöntemini aşağıdaki kodla değiştirin:

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

3. Kodu derle ve hata ayıklamayı başlat.

4. Visual Studio'nin deneysel örneğinde Araçlar menüsünü açın ve **TestStatusBarCommand'i Çağır'a tıklayın.** 

     İleti kutusunu gördüğünüzde, en sağında durum çubuğunda animasyonu da görüyor gerekir. İleti kutusunu çıkarsanız animasyon kaybolur.
