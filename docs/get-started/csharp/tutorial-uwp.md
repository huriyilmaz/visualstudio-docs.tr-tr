---
title: 'Visual Studio ve C ile UWP uygulaması oluşturma #'
description: "Visual Studio 'da XAML ve C ile bir UWP uygulaması oluşturma #"
titleSuffix: ''
ms.custom: seodec18, get-started, SEO-VS-2020
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
ms.openlocfilehash: 2e68039e02a6181ef7970fdc6a1b3bd6ad173093
ms.sourcegitcommit: 6d88913a8b5a9e5eda01d3f95205b4d138f440f8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/13/2021
ms.locfileid: "107295643"
---
# <a name="tutorial-create-your-first-universal-windows-platform-application-in-visual-studio-with-xaml-and-c35"></a>Öğretici: Visual Studio 'da XAML ve C ile ilk Evrensel Windows Platformu uygulamanızı oluşturma&#35;

Visual Studio tümleşik geliştirme ortamına (IDE) Bu giriş bölümünde, herhangi bir Windows 10 cihazında çalışan bir "Merhaba Dünya" uygulaması oluşturacaksınız. Bunu yapmak için Evrensel Windows Platformu (UWP) proje şablonu, Extensible Application Markup Language (XAML) ve C# programlama dilini kullanacaksınız.

::: moniker range="vs-2017"
Visual Studio 'Yu henüz yüklemediyseniz, [Visual Studio İndirmeleri](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) sayfasına giderek ücretsiz olarak yükleme yapın.
::: moniker-end
::: moniker range="vs-2019"
Visual Studio 'Yu henüz yüklemediyseniz, [Visual Studio İndirmeleri](https://visualstudio.microsoft.com/downloads) sayfasına giderek ücretsiz olarak yükleme yapın.
::: moniker-end

## <a name="create-a-project"></a>Proje oluşturma

İlk olarak, bir Evrensel Windows Platformu projesi oluşturun. Proje türü, ihtiyacınız olan tüm şablon dosyaları ile birlikte gelir, hatta herhangi bir şey eklemeden önce!

::: moniker range="vs-2017"
1. Visual Studio'yu açın.

1. Üstteki menü çubuğundan **Dosya** > **Yeni** > **Proje**' yi seçin.

1. **Yeni proje** iletişim kutusunun sol bölmesinde, **Visual C#**' ı genişletin ve ardından **Windows Universal**' ı seçin. Orta bölmede **boş uygulama (Evrensel Windows)** öğesini seçin. Ardından, projeyi *HelloWorld* olarak adlandırın ve **Tamam**' ı seçin.

   > [!NOTE]
   > Kaynak proje konumunun, Işletim sistemi (OS) sürücünüz gibi **Yeni bir teknoloji dosya sistemi (NTFS)** biçimli bir sürücüde olduğundan emin olun. Aksi takdirde, projenizi oluşturma ve çalıştırma konusunda sorun yaşayabilirsiniz. 

   ![Visual Studio IDE 'de yeni proje iletişim kutusunda Windows Evrensel proje şablonu](media/new-project-csharp-uwp-helloworld.png)

   > [!NOTE]
   > **Boş uygulama (Evrensel Windows)** proje şablonunu görmüyorsanız, **Yeni proje** Iletişim kutusunun sol bölmesindeki **Aç Visual Studio yükleyicisi** bağlantısına tıklayın.<br><br>![Yeni proje iletişim kutusundan Visual Studio Yükleyicisi aç bağlantısına tıklayın](../../ide/media/vb-open-visual-studio-installer-hello-world.png)<br><br>Visual Studio Yükleyicisi başlatılır. **Evrensel Windows platformu geliştirme** iş yükünü seçin ve ardından **Değiştir**' i seçin.<br><br>![Visual Studio Yükleyicisi Evrensel Windows Platformu geliştirme iş yükü](media/uwp-dev-workload.png)

1. **Yeni Evrensel Windows platformu projesi** iletişim kutusunda varsayılan **hedef sürümü** ve **En düşük sürüm** ayarlarını kabul edin.

   ![Yeni Evrensel Windows Platformu Projesi iletişim kutusunda varsayılan hedef sürümü ve en düşük sürüm ayarlarını kabul edin](media/new-uwp-project-target-minver-dialog.png)
::: moniker-end

::: moniker range=">=vs-2019"
1. Visual Studio 'yu açın ve başlangıç penceresinde **Yeni proje oluştur**' u seçin.

1. **Yeni proje oluştur** ekranında, arama kutusuna *Evrensel Windows* girin, **boş uygulama (Evrensel Windows)** Için C# şablonunu seçin ve ardından **İleri**' yi seçin.

   ![Yeni Proje ekranı oluşturma ekranının ekran görüntüsü](media/vs-2019/uwp-create-new-project.png)

   > [!NOTE]
   > **Boş uygulama (Evrensel Windows)** proje şablonunu görmüyorsanız, **daha fazla araç ve özellik yüklemesi** bağlantısına tıklayın.<br><br>![Daha fazla araç ve özellik yüklemesi bağlantısına tıklayın](media/vs-2019/uwp-not-finding.png)<br><br>Visual Studio Yükleyicisi başlatılır. **Evrensel Windows platformu geliştirme** iş yükünü seçin ve ardından **Değiştir**' i seçin.<br><br>![Visual Studio Yükleyicisi Evrensel Windows Platformu geliştirme iş yükü](media/uwp-dev-workload.png)

1. Projeye bir ad, _HelloWorld_ ve **Oluştur** seçeneğini belirleyin.

   ![Proje ekranınızı yapılandırma](media/vs-2019/uwp-configure-your-project.png)

1. **Yeni Evrensel Windows platformu projesi** iletişim kutusunda varsayılan **hedef sürümü** ve **En düşük sürüm** ayarlarını kabul edin.

   ![Yeni Evrensel Windows Platformu Projesi iletişim kutusunda varsayılan hedef sürümü ve en düşük sürüm ayarlarını kabul et](media/vs-2019/new-uwp-project-target-minver-dialog.png)
::: moniker-end

   > [!NOTE]
   > UWP uygulaması oluşturmak için Visual Studio 'Yu ilk kez kullandıysanız, bir **Ayarlar** iletişim kutusu görünebilir. **Geliştirici modu**' nu seçin ve ardından **Evet**' i seçin.<br><br>
   > ![UWP ayarları iletişim kutusunda Geliştirici modunu etkinleştirme](media/enable-developer-mode.png)<br><br>Visual Studio sizin için ek bir geliştirici modu paketi yüklüyor. Paket yüklemesi tamamlandığında, **Ayarlar** iletişim kutusunu kapatın.

## <a name="create-the-application"></a>Uygulama oluşturma

Geliştirmeye başlama zamanı. Düğme denetimi ekleyecek, düğmeye bir eylem ekleyecek ve sonra nasıl göründüğünü görmek için "Merhaba Dünya" uygulamasını başlatacak.

### <a name="add-a-button-to-the-design-canvas"></a>Tasarım tuvaline düğme ekleme

1. **Çözüm Gezgini** bölünmüş bir görünüm açmak Için *MainPage. xaml* öğesine çift tıklayın.

   ::: moniker range="vs-2017"
   ![Çözüm Gezgini MainPage. xaml ' i açın ](media/uwp-solution-explorer-MainPage-xaml.png)
   ::: moniker-end
   ::: moniker range=">=vs-2019"
   ![Çözüm Gezgini MainPage. xaml ' i açın](media/vs-2019/uwp-solution-explorer-mainpage-xaml.png)
   ::: moniker-end

   İki bölme vardır: tasarım tuvali içeren **XAML Tasarımcısı** ve kod ekleyebileceğiniz veya değiştirebileceğiniz **xaml Düzenleyicisi**.

   ![XAML düzenleyicisinde XAML Tasarımcısı bölmesi](media/uwp-xaml-editor.png)

1. Araç **kutusu ' nu seçerek araç** kutusu açılır penceresini açın.

   ![Araç kutusu ' na tıklayarak araç kutusu açılır penceresini açın](media/uwp-toolbox.png)

   ( **Araç kutusu** seçeneğini görmüyorsanız, menü çubuğundan açabilirsiniz. Bunu yapmak için   >  **araç çubuğunu** görüntüle ' yi seçin. Ya da **CTRL** + **alt** + **X** tuşlarına basın.)

1. Araç kutusu penceresini sabitlemek için **sabitle** simgesine tıklayın.

   ![Araç kutusu penceresini sabitlemek için Sabitle simgesine tıklayın](media/uwp-toolbox-autohide.png)

1. **Düğme** denetimine tıklayın ve sonra tasarım tuvalinden sürükleyin.

   ![Düğme denetimine tıklayın ve tasarım tuvaline sürükleyin](media/uwp-toolbox-add-button-control.png)

   **Xaml düzenleyicisinde** koda bakarsanız, düğmenin de bu şekilde eklendiğini görürsünüz:

   ![XAML düzenleyicisinde düğmeyi göster](media/uwp-xaml-control-code-window.png)

### <a name="add-a-label-to-the-button"></a>Düğmeye etiket ekleyin

1. **Xaml düzenleyicisinde**, düğme içerik değerini "Button" iken "Merhaba Dünya!" olarak değiştirin

   ![Düğme içerik değerini Merhaba Dünya olarak değiştirin](media/uwp-change-button-text-in-xaml-code-window.png)

1. **XAML Tasarımcısı** düğmenin de değiştiği hakkında dikkat edin.

   ![Düğme tasarım tuvalindeki Merhaba Dünya değiştirilir](media/uwp-button-text-change-in-design-canvas.png)

### <a name="add-an-event-handler"></a>Olay işleyicisi ekleme

"Olay işleyicisi" karmaşıktır, ancak bir olay gerçekleştiğinde çağrılan kod için yalnızca başka bir addır. Bu durumda, "Merhaba Dünya!" öğesine bir eylem ekler tıklayın.

1. Tasarım tuvalindeki düğme denetimine çift tıklayın.

1. *MainPage. xaml. cs* içindeki olay işleyici kodunu, arka plan kod sayfasında düzenleyin.

   İşte ilginç şeyler. Varsayılan olay işleyicisi şöyle görünür:

   ![Varsayılan Button_Click olay işleyicisi ](media/uwp-button-click-code.png)

   Bunu değiştirelim, şöyle görünür:

   ![Yeni zaman uyumsuz Button_Click olay işleyicisi ](media/uwp-add-hello-world-async-code.png)

   Kopyalanacak ve yapıştırılacak kod aşağıda verilmiştir:

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

#### <a name="what-did-we-just-do"></a>Ne yapmalıyım?

Kod, bir konuşma senıs nesnesi oluşturmak için bazı Windows API 'Lerini kullanır ve sonra buna biraz metin verir. (Kullanma hakkında daha fazla bilgi için `SpeechSynthesis` bkz  <xref:System.Speech.Synthesis> ..)

## <a name="run-the-application"></a>Uygulamayı çalıştırma

::: moniker range="vs-2017"
"Merhaba Dünya" UWP uygulamasını oluşturmak, dağıtmak ve bunların nasıl göründüğünü ve seslerinin nasıl çalıştığını görmek zaman alabilir. Aşağıdaki adımları uygulayın:

1. Uygulamayı yerel makinede başlatmak için Oynat düğmesini ( **yerel makine**) kullanın.

   ![UWP uygulamanızı başlatmak ve hatalarını ayıklamak için yerel makine ' ye tıklayın](media/uwp-start-or-debug.png)

   (Alternatif olarak, **Hata Ayıkla** > ' yı seçebilirsiniz. Menü çubuğundan **hata ayıklamayı başlatın** veya F5 'e basarak uygulamanızı başlatın.)

1. Giriş ekranı kaybolduktan sonra görüntülenen uygulamanızı görüntüleyin. Uygulama şuna benzer görünmelidir:

   ![UWP "Merhaba Dünya" uygulaması](media/uwp-hello-world-app.png)

1. **Merhaba Dünya** düğmesine tıklayın.

   Windows 10 cihazınız, "Merhaba, Dünya!" harfine sahip olacak

1. Uygulamayı kapatmak için araç çubuğunda **hata ayıklamayı Durdur** düğmesine tıklayın. (Alternatif olarak, **Hata Ayıkla**  >  ' yı seçin Menü çubuğundan **hata ayıklamayı durdurun** veya SHIFT + F5 tuşlarına basın.)

::: moniker-end
::: moniker range=">=vs-2019"
"Merhaba Dünya" UWP uygulamasını oluşturmak, dağıtmak ve bunların nasıl göründüğünü ve seslerinin nasıl çalıştığını görmek zaman alabilir. Aşağıdaki adımları uygulayın:

1. Uygulamayı yerel makinede başlatmak için Oynat düğmesini ( **yerel makine**) kullanın.

   ![UWP uygulamanızı başlatmak ve hatalarını ayıklamak için yerel makine ' ye tıklayın](media/uwp-start-or-debug.png)

   (Alternatif olarak, **Hata Ayıkla** > ' yı seçebilirsiniz. Menü çubuğundan **hata ayıklamayı başlatın** veya F5 'e basarak uygulamanızı başlatın.)

1. Giriş ekranı kaybolduktan sonra görüntülenen uygulamanızı görüntüleyin. Uygulama şuna benzer görünmelidir:

   ![UWP "Merhaba Dünya" uygulaması](media/vs-2019/uwp-hello-world-app.png)

1. **Merhaba Dünya** düğmesine tıklayın.

   Windows 10 cihazınız, "Merhaba, Dünya!" harfine sahip olacak

1. Uygulamayı kapatmak için araç çubuğunda **hata ayıklamayı Durdur** düğmesine tıklayın. (Alternatif olarak, **Hata Ayıkla**  >  ' yı seçin Menü çubuğundan **hata ayıklamayı durdurun** veya SHIFT + F5 tuşlarına basın.)

::: moniker-end

## <a name="next-steps"></a>Sonraki adımlar

Tebrikler, bu öğreticiyi tamamlama! UWP ve Visual Studio IDE hakkında bazı temel bilgileri öğrendiklerinizi umuyoruz. Daha fazla bilgi edinmek için aşağıdaki öğreticiyle devam edin:

> [!div class="nextstepaction"]
> [Kullanıcı arabirimi oluşturma](/windows/uwp/design/basics/xaml-basics-ui)

## <a name="see-also"></a>Ayrıca bkz.

- [UWP’ye genel bakış](/windows/uwp/get-started/universal-application-platform-guide)
- [UWP uygulama örnekleri al](/windows/uwp/get-started/get-uwp-app-samples)
