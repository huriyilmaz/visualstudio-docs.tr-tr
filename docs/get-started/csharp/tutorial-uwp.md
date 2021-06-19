---
title: 'Öğretici: Visual Studio & C ile UWP Uygulamaları oluşturma #'
description: 'XAML ve C ile Visual Studio bir UWP uygulaması oluşturma #'
titleSuffix: ''
ms.custom: vs-acquisition, get-started, SEO-VS-2020
ms.date: 09/20/2019
ms.technology: vs-ide-general
ms.topic: tutorial
ms.devlang: CSharp
author: j-martens
ms.author: jmartens
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: 2e89c58e3c0dca2b5d009a592d3f242646339f8f
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112390300"
---
# <a name="tutorial-create-your-first-universal-windows-platform-application-in-visual-studio-with-xaml-and-c35"></a>Öğretici: XAML ve C Evrensel Windows Platformu Visual Studio ilk uygulama uygulamanızı&#35;

Visual Studio tümleşik geliştirme ortamına (IDE) giriş olarak, herhangi bir Merhaba Dünya cihazda çalışan bir "Windows 10" uygulaması oluşturabilirsiniz. Bunu yapmak için bir Evrensel Windows Platformu (UWP) proje şablonu, Extensible Application Markup Language (XAML) ve C# programlama dilini kullansınız.

::: moniker range="vs-2017"
Daha önce yüklememiş Visual Studio indirmeler [sayfasına Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) ücretsiz olarak yükleyin.
::: moniker-end
::: moniker range="vs-2019"
Daha önce yüklememiş Visual Studio indirmeler [sayfasına Visual Studio](https://visualstudio.microsoft.com/downloads) ücretsiz olarak yükleyin.
::: moniker-end

## <a name="create-a-project"></a>Proje oluşturma

İlk olarak bir Evrensel Windows Platformu oluşturun. Proje türü, herhangi bir şey eklemeden önce ihtiyacınız olan tüm şablon dosyalarıyla birlikte gelir!

::: moniker range="vs-2017"
1. Visual Studio'yu açın.

1. Üst menü çubuğundan Dosya Yeni **Proje'yi** >  > **seçin.**

1. Yeni Proje iletişim kutusunun sol **bölmesinde** **Visual C#** öğesini genişletin ve Windows Evrensel'i **seçin.** Orta bölmede Boş Uygulama **(Evrensel Windows) 'ı seçin.** Ardından projeye *HelloWorld* adını ve Tamam'ı **seçin.**

   > [!NOTE]
   > Kaynak projenin konumunun İşletim Sistemi (OS) sürücü gibi Yeni Teknoloji Dosya Sistemi **(NTFS)** biçimlendirilmiş bir sürücüde olduğundan emin olun. Aksi takdirde, projenizi inşa ve çalıştırma konusunda sorun olabilir. 

   ![Visual Studio IDE'de Yeni Proje iletişim kutusundaki Windows Evrensel proje şablonu](media/new-project-csharp-uwp-helloworld.png)

   > [!NOTE]
   > Boş Uygulama **(Evrensel Windows)** proje şablonunu görmüyorsanız, Yeni **Proje iletişim** kutusunun sol bölmesinde Visual Studio Yükleyicisi Aç **bağlantısına** tıklayın.<br><br>![Yeni Proje Visual Studio Yükleyicisi Aç bağlantısına tıklayın](../../ide/media/vb-open-visual-studio-installer-hello-world.png)<br><br>Uygulama Visual Studio Yükleyicisi başlatıyor. Geliştirme iş **Evrensel Windows Platformu seçin** ve ardından Değiştir'i **seçin.**<br><br>![Evrensel Windows Platformu geliştirme iş yükünü Visual Studio Yükleyicisi](media/uwp-dev-workload.png)

1. Yeni Sürüm Projesi **iletişim kutusunda** **varsayılan** Hedef sürüm ve En düşük **Evrensel Windows Platformu ayarlarını** kabul edin.

   ![Yeni Sürüm Projesi iletişim kutusunda varsayılan Hedef sürüm ve En düşük Evrensel Windows Platformu ayarlarını kabul edin](media/new-uwp-project-target-minver-dialog.png)
::: moniker-end

::: moniker range=">=vs-2019"
1. Yeni Visual Studio açın ve başlangıç penceresinde Yeni proje **oluştur'a tıklayın.**

1. Yeni **proje oluştur ekranında** arama kutusuna Evrensel Windows yazın, Boş Uygulama **(Evrensel** *Windows)* için C# şablonunu seçin ve ardından Sonraki'yi **seçin.**

   ![Yeni proje oluştur ekran görüntüsü](media/vs-2019/uwp-create-new-project.png)

   > [!NOTE]
   > Boş Uygulama **(Evrensel Windows)** proje şablonunu görmüyorsanız Daha fazla araç ve **özellik yükle bağlantısına** tıklayın.<br><br>![Daha fazla araç ve özellik yükle bağlantısına tıklayın](media/vs-2019/uwp-not-finding.png)<br><br>Uygulama Visual Studio Yükleyicisi başlatıyor. Geliştirme iş **Evrensel Windows Platformu seçin** ve ardından Değiştir'i **seçin.**<br><br>![Evrensel Windows Platformu geliştirme iş yükünü Visual Studio Yükleyicisi](media/uwp-dev-workload.png)

1. Projeye _HelloWorld_ adını girin ve Oluştur'a **seçin.**

   ![Projenizi yapılandırma ekranı](media/vs-2019/uwp-configure-your-project.png)

1. Yeni Sürüm Projesi **iletişim kutusunda** **varsayılan** Hedef sürüm ve En düşük **Evrensel Windows Platformu ayarlarını** kabul edin.

   ![Yeni Sürüm Projesi iletişim kutusunda varsayılan Hedef sürüm ve En düşük Evrensel Windows Platformu ayarlarını kabul edin](media/vs-2019/new-uwp-project-target-minver-dialog.png)
::: moniker-end

   > [!NOTE]
   > UWP uygulaması oluşturmak için Visual Studio kez kullandıysanız, Ayarlar **iletişim** kutusu görünebilir. Geliştirici **modu'larını** ve ardından Evet'i **seçin.**<br><br>
   > ![UWP Ayarları iletişim kutusunda Geliştirici Modunu Etkinleştirme](media/enable-developer-mode.png)<br><br>Visual Studio sizin için ek bir Geliştirici Modu paketi yüklü olur. Paket yüklemesi tamamlandığında Ayarlar iletişim **kutusunu** kapatın.

## <a name="create-the-application"></a>Uygulama oluşturma

Geliştirmeye başlamanın zamanı geldi. Düğme denetimi ekser, düğmeye eylem ekler ve ardından "Merhaba Dünya" uygulamasını başlatarak nasıl göründüğünü kontrol edin.

### <a name="add-a-button-to-the-design-canvas"></a>Tasarım tuvale düğme ekleme

1. Dosyanın **Çözüm Gezgini** *MainPage.xaml'e çift* tıklar ve bölünmüş bir görünüm açın.

   ::: moniker range="vs-2017"
   ![MainPage.xaml'i Çözüm Gezgini ](media/uwp-solution-explorer-MainPage-xaml.png)
   ::: moniker-end
   ::: moniker range=">=vs-2019"
   ![MainPage.xaml'i Çözüm Gezgini](media/vs-2019/uwp-solution-explorer-mainpage-xaml.png)
   ::: moniker-end

   İki bölme vardır: **XAML Tasarımcısı** tuvali içeren XAML Tasarımcısı ve kod ekpleri değiştirerek **XAML** Düzenleyicisi'ni içerir.

   ![XAML düzenleyicisinde XAML Tasarımcısı bölmesi](media/uwp-xaml-editor.png)

1. Araç **Kutusu açılır** penceresini açmak için Araç Kutusu'nı seçin.

   ![Araç Kutusu açılır penceresini açmak için Araç Kutusu'na tıklayın](media/uwp-toolbox.png)

   (Araç Kutusu seçeneğini **görmüyorsanız** menü çubuğundan açabilirsiniz. Bunu yapmak için Araç Çubuğunu **Görüntüle'yi**  >  **seçin.** Veya **Ctrl** Alt X +  + **tuşlarına basın.)**

1. Araç Kutusu **penceresini** sabitlemek için Sabitle simgesine tıklayın.

   ![Araç Kutusu penceresini sabitlemek için Sabitle simgesine tıklayın](media/uwp-toolbox-autohide.png)

1. Düğme **denetimine** tıklayın ve tasarım tuvali üzerine sürükleyin.

   ![Düğme denetimine tıklayın ve Tasarım tuvali üzerine sürükleyin](media/uwp-toolbox-add-button-control.png)

   **XAML** Düzenleyicisi'nde koda bakarsanız, buraya Düğme'nin de eklenmiştir:

   ![XAML düzenleyicisinde göster düğmesi](media/uwp-xaml-control-code-window.png)

### <a name="add-a-label-to-the-button"></a>Düğmeye etiket ekleme

1. **XAML Düzenleyicisi'nde** Düğme İçeriği değerini "Düğme" yerine "Merhaba Dünya!"

   ![Düğme içerik değerini Merhaba Dünya](media/uwp-change-button-text-in-xaml-code-window.png)

1. Aşağıdaki düğmenin de **XAML Tasarımcısı** dikkat.

   ![Düğme tasarım tuvali Merhaba Dünya olarak değişir](media/uwp-button-text-change-in-design-canvas.png)

### <a name="add-an-event-handler"></a>Olay işleyicisi ekleme

"Olay işleyicisi" karmaşık gibi görünüyor, ancak bir olay olduğunda kod için çağrılmış başka bir addır. Bu durumda, "Merhaba Dünya!" tıklayın.

1. Tasarım tuvali üzerinde düğme denetimine çift tıklayın.

1. Olay işleyicisi kodunu *MainPage.xaml.cs* içinde , arka arkasındaki kod sayfasında düzenleyin.

   İşte işler burada ilginçleşiyor. Varsayılan olay işleyicisi şu şekildedir:

   ![Varsayılan olay Button_Click işleyicisi ](media/uwp-button-click-code.png)

   Şimdi bunu değiştir, şöyle bir görünüme bakalım:

   ![Yeni zaman uyumsuz Button_Click işleyicisi ](media/uwp-add-hello-world-async-code.png)

   Kopyalayıp yapıştırmak için kod şu şekildedir:

   ```C#
   private async void Button_Click(object sender, RoutedEventArgs e)
         {
             MediaElement mediaElement = new MediaElement();
             var synth = new Windows.Media.SpeechSynthesis.SpeechSynthesizer();
             Windows.Media.SpeechSynthesis.SpeechSynthesisStream stream = await synth.SynthesizeTextToStreamAsync("Hello, World!");
             mediaElement.SetSource(stream, stream.ContentType);
             mediaElement.Play();
         }
   ```

#### <a name="what-did-we-just-do"></a>Az önce ne yaptık?

Kod, bir konuşma sentezi nesnesi oluşturmak için bazı Windows API'lerini kullanır ve ardından bunu söylemesi için biraz metin verir. (kullanma hakkında daha fazla bilgi için `SpeechSynthesis`  <xref:System.Speech.Synthesis> bkz. .)

## <a name="run-the-application"></a>Uygulamayı çalıştırma

::: moniker range="vs-2017"
Şimdi "Merhaba Dünya" UWP uygulamasını derlemenin, dağıtmanın ve başlatmanın zamanı geldi. Aşağıdaki adımları uygulayın:

1. Uygulamayı yerel makinede başlatmak için Oynat **düğmesini (Yerel** Makine metni vardır) kullanın.

   ![UWP uygulamanızı başlatmak ve hata ayıklamak için Yerel Makine'ye tıklayın](media/uwp-start-or-debug.png)

   (Alternatif olarak Hata **Ayıkla'ya da seçebilirsiniz** > **Menü çubuğundan Hata** Ayıklamayı başlat veya F5 tuşuna basarak uygulamayı başlat.)

1. Giriş ekranı görüntüden kaybolduktan kısa süre sonra görünen uygulamanızı görüntüleme. Uygulama şuna benzer şekilde görünüyor olmalı:

   ![UWP "Merhaba Dünya" uygulaması](media/uwp-hello-world-app.png)

1. Merhaba Dünya **tıklayın.**

   Windows 10 cihazınız tam olarak "Hello, World!"

1. Uygulamayı kapatmak için araç **çubuğundaki Hata Ayıklamayı** Durdur düğmesine tıklayın. (Alternatif olarak Hata **Ayıkla'ya da**  >  **Menü çubuğundan hata** ayıklamayı durdurun veya Shift+F5 tuşlarına basın.)

::: moniker-end
::: moniker range=">=vs-2019"
Şimdi "Merhaba Dünya" UWP uygulamasını derlemenin, dağıtmanın ve başlatmanın zamanı geldi. Aşağıdaki adımları uygulayın:

1. Uygulamayı yerel makinede başlatmak için Oynat **düğmesini (Yerel** Makine metni vardır) kullanın.

   ![UWP uygulamanızı başlatmak ve hata ayıklamak için Yerel Makine'ye tıklayın](media/uwp-start-or-debug.png)

   (Alternatif olarak Hata **Ayıkla'ya da seçebilirsiniz** > **Menü çubuğundan Hata** Ayıklamayı başlat veya F5 tuşuna basarak uygulamayı başlat.)

1. Giriş ekranı görüntüden kaybolduktan kısa süre sonra görünen uygulamanızı görüntüleme. Uygulama şuna benzer şekilde görünüyor olmalı:

   ![UWP "Merhaba Dünya" uygulaması](media/vs-2019/uwp-hello-world-app.png)

1. Merhaba Dünya **tıklayın.**

   Windows 10 cihazınız tam olarak "Hello, World!"

1. Uygulamayı kapatmak için araç **çubuğundaki Hata Ayıklamayı** Durdur düğmesine tıklayın. (Alternatif olarak Hata **Ayıkla'ya da**  >  **Menü çubuğundan hata** ayıklamayı durdurun veya Shift+F5 tuşlarına basın.)

::: moniker-end

## <a name="next-steps"></a>Sonraki adımlar

Tebrikler, bu öğreticiyi tamamladıktan sonra! UWP ve IDE ile ilgili bazı temel bilgileri Visual Studio umuyoruz. Daha fazla bilgi edinmek için aşağıdaki öğreticiyle devam edin:

> [!div class="nextstepaction"]
> [Kullanıcı arabirimi oluşturma](/windows/uwp/design/basics/xaml-basics-ui)

## <a name="see-also"></a>Ayrıca bkz.

- [UWP’ye genel bakış](/windows/uwp/get-started/universal-application-platform-guide)
- [UWP uygulama örneklerini alın](/windows/uwp/get-started/get-uwp-app-samples)
