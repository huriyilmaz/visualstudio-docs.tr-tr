---
title: 'Visual Studio ve C ile Evrensel Bir Windows Platformu (UWP) Uygulaması Oluşturun #'
description: "Visual Studio'da XAML ve C ile bir UWP uygulaması oluşturma #"
titleSuffix: ''
ms.custom: seodec18, get-started
ms.date: 09/20/2019
ms.technology: vs-ide-general
ms.topic: tutorial
ms.devlang: CSharp
author: ornellaalt
ms.author: ornella
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: 8be56581374aefbef41a5173836d1189cceff290
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "77580005"
---
# <a name="tutorial-create-your-first-universal-windows-platform-application-in-visual-studio-with-xaml-and-c35"></a>Öğretici: XAML ve C&#35; ile Visual Studio'da ilk Evrensel Windows Platform uygulamanızı oluşturun

Visual Studio tümleşik geliştirme ortamına (IDE) giriş yaptığınızda, herhangi bir Windows 10 aygıtında çalışan bir "Hello World" uygulaması oluşturursunuz. Bunu yapmak için Evrensel Windows Platformu (UWP) proje şablonu, Genişletilebilir Uygulama Biçimlendirme Dili (XAML) ve C# programlama dilini kullanırsınız.

::: moniker range="vs-2017"
Visual Studio'yu henüz yüklemediyseniz, visual [studio indirme sayfasına](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) gidin ve ücretsiz olarak yükleyin.
::: moniker-end
::: moniker range="vs-2019"
Visual Studio'yu henüz yüklemediyseniz, visual [studio indirme sayfasına](https://visualstudio.microsoft.com/downloads) gidin ve ücretsiz olarak yükleyin.
::: moniker-end

## <a name="create-a-project"></a>Proje oluşturma

İlk olarak, evrensel bir Windows Platformu projesi oluşturun. Proje türü, daha bir şey eklemeden önce ihtiyacınız olan tüm şablon dosyalarıyla birlikte gelir!

::: moniker range="vs-2017"
1. Visual Studio'yu açın.

1. Üst menü çubuğundan **Yeni** > **New** > **Dosya Yı**seçin.

1. **Yeni Proje** iletişim kutusunun sol bölmesinde **Visual C#** seçeneğini genişletin ve ardından **Windows Universal'ı**seçin. Orta bölmede Boş **Uygulama 'yı (Evrensel Windows)** seçin. Daha sonra, proje *HelloWorld* adını ve **Tamam**seçin.

   ![Visual Studio IDE'deki Yeni Proje iletişim kutusunda Windows Universal proje şablonu](media/new-project-csharp-uwp-helloworld.png)

   > [!NOTE]
   > **Boş Uygulama (Evrensel Windows)** proje şablonunu görmüyorsanız, **Yeni Proje** iletişim kutusunun sol bölmesinde Görsel **Stüdyo Yükleyici** Aç bağlantısını tıklatın.<br><br>![Yeni Proje iletişim kutusundan Görsel Stüdyo Yükleyiciaç'ı Aç bağlantısını tıklayın](../../ide/media/vb-open-visual-studio-installer-hello-world.png)<br><br>Visual Studio Installer başlattı. Evrensel **Windows Platformu geliştirme** iş yükünü seçin ve sonra **Değiştir'i**seçin.<br><br>![Visual Studio Installer'da Evrensel Windows Platformu geliştirme iş yükü](media/uwp-dev-workload.png)

1. **Yeni Evrensel Windows Platformu Projesi** iletişim kutusunda varsayılan Hedef **sürümünü** ve **Minimum sürüm** ayarlarını kabul edin.

   ![Yeni Evrensel Windows Platformu Projesi iletişim kutusunda varsayılan Hedef sürümünü ve Minimum sürüm ayarlarını kabul edin](media/new-uwp-project-target-minver-dialog.png)
::: moniker-end

::: moniker range=">=vs-2019"
1. Visual Studio'yu açın ve başlangıç penceresinde **yeni bir proje oluştur'u**seçin.

1. Yeni **bir proje oluşturma** ekranında, arama kutusuna *Evrensel Windows* girin, Boş Uygulama için C# şablonunu **(Evrensel Windows)** seçin ve sonra **İleri'yi**seçin.

   ![Yeni proje ekranı oluşturma ekran görüntüsü](media/vs-2019/uwp-create-new-project.png)

   > [!NOTE]
   > **Boş Uygulama (Evrensel Windows)** proje şablonu görmüyorsanız, **daha fazla araç ve özellik yükle** bağlantısını tıklatın.<br><br>![Diğer araçları ve özellikleri yükle bağlantısını tıklatın](media/vs-2019/uwp-not-finding.png)<br><br>Visual Studio Installer başlattı. Evrensel **Windows Platformu geliştirme** iş yükünü seçin ve sonra **Değiştir'i**seçin.<br><br>![Visual Studio Installer'da Evrensel Windows Platformu geliştirme iş yükü](media/uwp-dev-workload.png)

1. Projeye _HelloWorld_adında bir ad verin ve **Oluştur'u**seçin.

   ![Proje ekranınızı yapılandırın](media/vs-2019/uwp-configure-your-project.png)

1. **Yeni Evrensel Windows Platformu Projesi** iletişim kutusunda varsayılan Hedef **sürümünü** ve **Minimum sürüm** ayarlarını kabul edin.

   ![Yeni Evrensel Windows Platformu Projesi iletişim kutusunda varsayılan Hedef sürümünü ve Minimum sürüm ayarlarını kabul edin](media/vs-2019/new-uwp-project-target-minver-dialog.png)
::: moniker-end

   > [!NOTE]
   > Bir UWP uygulaması oluşturmak için Visual Studio'yu ilk kez kullandıysanız, **Ayarlar** iletişim kutusu görünebilir. **Geliştirici modunu**seçin ve ardından **Evet'i**seçin.<br><br>
   > ![UWP Ayarları iletişim kutusunda Geliştirici Modunu etkinleştirme](media/enable-developer-mode.png)<br><br>Visual Studio sizin için ek bir Geliştirici Modu paketi yükler. Paket yükleme tamamlandığında **Ayarlar** iletişim kutusunu kapatın.

## <a name="create-the-application"></a>Uygulama oluşturma

Gelişmeye başlama nın zamanı. Bir düğme denetimi ekler, düğmeye bir eylem ekler ve ardından nasıl göründüğünü görmek için "Hello World" uygulamasını başlatırsınız.

### <a name="add-a-button-to-the-design-canvas"></a>Tasarım tuvaline bir düğme ekleme

1. Çözüm **Gezgini'nde,** bölünmüş bir görünüm açmak için *MainPage.xaml'ı* çift tıklatın.

   ::: moniker range="vs-2017"
   ![Solution Explorer'dan MainPage.xaml'ı aç ](media/uwp-solution-explorer-MainPage-xaml.png)
   ::: moniker-end
   ::: moniker range=">=vs-2019"
   ![Solution Explorer'dan MainPage.xaml'ı aç](media/vs-2019/uwp-solution-explorer-mainpage-xaml.png)
   ::: moniker-end

   İki bölme vardır: Bir tasarım tuvali içeren **XAML Tasarımcısı**ve kod ekleyebileceğiniz veya değiştirebileceğiniz **XAML**Düzenleyicisi.

   ![XAML düzenleyicisindeki XAML Designer bölmesi](media/uwp-xaml-editor.png)

1. Araç Kutusu fly-out penceresini açmak için **Araç Kutusu'nu** seçin.

   ![Araç Kutusu fly-out penceresini açmak için Araç Kutusu'nu tıklatın](media/uwp-toolbox.png)

   (Araç **Kutusu** seçeneğini görmüyorsanız, menü çubuğundan açabilirsiniz. Bunu yapmak için**Araç Çubuğu'nı** **Görüntüle'yi** > seçin. Veya **Ctrl**+**Alt**+**X**tuşuna basın .)

1. Araç Kutusu penceresini sabitlemek için **Pin** simgesini tıklatın.

   ![Araç Kutusu penceresini sabitlemek için Pin simgesine tıklayın](media/uwp-toolbox-autohide.png)

1. **Düğme** denetimini tıklatın ve ardından tasarım tuvaline sürükleyin.

   ![Düğme denetimini tıklatın ve Tasarım tuvaline sürükleyin](media/uwp-toolbox-add-button-control.png)

   **XAML**Düzenleyicisi'ndeki koda bakarsanız, Düğme'nin de oraya eklendiğini görürsünüz:

   ![Düğme denetimini tıklatın ve Tasarım tuvaline sürükleyin](media/uwp-xaml-control-code-window.png)

### <a name="add-a-label-to-the-button"></a>Düğmeye etiket ekleme

1. **XAML Düzenleyicisi'nde**Düğme İçerik değerini "Button"dan "Hello World!" olarak değiştirin.

   ![Düğme içerik değerini Hello World olarak değiştirme](media/uwp-change-button-text-in-xaml-code-window.png)

1. **XAML Designer'daki** düğmenin de değiştiğine dikkat edin.

   ![Düğme, tasarım tuvalinde Hello World olarak değişir](media/uwp-button-text-change-in-design-canvas.png)

### <a name="add-an-event-handler"></a>Olay işleyicisi ekleme

Bir "olay işleyicisi" karmaşık gelebilir, ancak bir olay olduğunda kod için başka bir addır. Bu durumda, "Merhaba Dünya!" tıklayın.

1. Tasarım tuvalindeki düğme denetimini çift tıklatın.

1. MainPage.xaml.cs, kod arkası sayfasında *MainPage.xaml.cs*olay işleyicisi kodunu düzenledi.

   İşte işler burada ilginçleşiyor. Varsayılan olay işleyicisi aşağıdaki gibi görünür:

   ![Varsayılan Button_Click olay işleyicisi ](media/uwp-button-click-code.png)

   Değiştirelim, şöyle görünsün:

   ![Yeni async Button_Click olay işleyicisi ](media/uwp-add-hello-world-async-code.png)

   Kopyalamak ve yapıştırmak için kod aşağıda veda etmek için:

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

Kod, bir konuşma sentezi nesnesi oluşturmak için bazı Windows API'larını kullanır ve ardından bunu söylemek için bazı metinler verir. (Kullanma `SpeechSynthesis`hakkında daha fazla <xref:System.Speech.Synthesis>bilgi için bkz.)

## <a name="run-the-application"></a>Uygulamayı çalıştırma


::: moniker range="vs-2017"
Ne göründüğünü ve nasıl göründüğünü görmek için "Hello World" UWP uygulamasını oluşturma, dağıtma ve başlatma zamanı geldi. Aşağıdaki adımları uygulayın:

1. Uygulamayı yerel makinede başlatmak için Oynat düğmesini **(Yerel Makine**metnine sahiptir) kullanın.

   ![UWP uygulamanızı başlatmak ve hata ayıklamak için Yerel Makine'yi tıklatın](media/uwp-start-or-debug.png)

   (Alternatif olarak, menü çubuğundan **Hata** > **Ayıklama Başlatma Hata Ayıklama'yı** seçebilir veya uygulamanızı başlatmak için F5 tuşuna basabilirsiniz.)

1. Bir sıçrama ekranı kaybolduktan kısa bir süre sonra görünen uygulamanızı görüntüleyin. Uygulama buna benzer olmalıdır:

   ![Bir UWP "Hello World" uygulaması](media/uwp-hello-world-app.png)

1. Hello **World** düğmesini tıklatın.

   Windows 10 aygıtınız kelimenin tam anlamıyla "Merhaba, Dünya!" diyecek.

1. Uygulamayı kapatmak için araç çubuğundaki **Hata Hata Ayıklamayı Durdur** düğmesini tıklatın. (Alternatif olarak, menü çubuğundan **hata** > **ayıklama** yı seçin veya Shift+F5 tuşuna basın.)

::: moniker-end
::: moniker range=">=vs-2019"
Ne göründüğünü ve nasıl göründüğünü görmek için "Hello World" UWP uygulamasını oluşturma, dağıtma ve başlatma zamanı geldi. Aşağıdaki adımları uygulayın:

1. Uygulamayı yerel makinede başlatmak için Oynat düğmesini **(Yerel Makine**metnine sahiptir) kullanın.

   ![UWP uygulamanızı başlatmak ve hata ayıklamak için Yerel Makine'yi tıklatın](media/uwp-start-or-debug.png)

   (Alternatif olarak, menü çubuğundan **Hata** > **Ayıklama Başlatma Hata Ayıklama'yı** seçebilir veya uygulamanızı başlatmak için F5 tuşuna basabilirsiniz.)

1. Bir sıçrama ekranı kaybolduktan kısa bir süre sonra görünen uygulamanızı görüntüleyin. Uygulama buna benzer olmalıdır:

   ![Bir UWP "Hello World" uygulaması](media/vs-2019/uwp-hello-world-app.png)

1. Hello **World** düğmesini tıklatın.

   Windows 10 aygıtınız kelimenin tam anlamıyla "Merhaba, Dünya!" diyecek.

1. Uygulamayı kapatmak için araç çubuğundaki **Hata Hata Ayıklamayı Durdur** düğmesini tıklatın. (Alternatif olarak, menü çubuğundan **hata** > **ayıklama** yı seçin veya Shift+F5 tuşuna basın.)

::: moniker-end

## <a name="next-steps"></a>Sonraki adımlar

Bu öğretici tamamladıktan sonra tebrikler! UWP ve Visual Studio IDE hakkında bazı temel bilgiler öğrenmişsinizi umuyoruz. Daha fazla bilgi edinmek için aşağıdaki öğreticiyle devam edin:

> [!div class="nextstepaction"]
> [Kullanıcı arabirimi oluşturma](/windows/uwp/design/basics/xaml-basics-ui)

## <a name="see-also"></a>Ayrıca bkz.

- [UWP genel bakış](/windows/uwp/get-started/universal-application-platform-guide)
- [UWP uygulama örneklerini alın](/windows/uwp/get-started/get-uwp-app-samples)