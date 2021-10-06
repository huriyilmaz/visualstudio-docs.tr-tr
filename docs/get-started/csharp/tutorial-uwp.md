---
title: 'Öğretici: Visual Studio & C ile UWP Uygulamaları oluşturma #'
description: 'XAML ve C ile Visual Studio bir UWP uygulaması oluşturma #'
titleSuffix: ''
ms.custom: vs-acquisition, get-started, SEO-VS-2020
ms.date: 09/14/2021
ms.technology: vs-ide-general
ms.topic: tutorial
ms.devlang: CSharp
author: anandmeg
ms.author: meghaanand
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: 147931e623f6663d13be8b7fbee722e96c83187b
ms.sourcegitcommit: d63ba1eff845d41ca095efb14b499ea96c4b6eba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/06/2021
ms.locfileid: "129561158"
---
# <a name="tutorial-create-your-first-universal-windows-platform-application-in-visual-studio-with-xaml-and-c35"></a>Öğretici: XAML ve C Visual Studio ile ilk Universal Windows Platform uygulamanızı&#35;

Visual Studio tümleşik geliştirme ortamına (IDE) giriş olarak, herhangi bir Windows 10 veya sonraki bir cihazda çalışan bir "Merhaba Dünya" uygulaması oluşturacağız. Bunu yapmak için Universal Windows Platform (UWP) proje şablonunu, Extensible Application Markup Language (XAML) ve C# programlama dilini kullanabilirsiniz.

::: moniker range="vs-2017"
Daha önce yüklememiş Visual Studio indirmeler [sayfasına Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) ücretsiz yükleyin.
::: moniker-end
::: moniker range=">=vs-2019"
Daha önce yüklememiş Visual Studio indirmeler [sayfasına Visual Studio](https://visualstudio.microsoft.com/downloads) ücretsiz yükleyin.
::: moniker-end

## <a name="create-a-project"></a>Proje oluşturma

İlk olarak, Universal Windows Platform projesi oluşturun. Proje türü, herhangi bir şey eklemeden önce ihtiyacınız olan tüm şablon dosyalarıyla birlikte gelir!

::: moniker range="vs-2017"
1. Visual Studio'yu açın.

1. Üst menü çubuğundan Dosya Yeni **Dosya'Project.** >  > 

1. Yeni Uygulama iletişim kutusunun sol bölmesinde Visual **C#** **Project** genişletin ve ardından **Evrensel'i Windows seçin.** Orta bölmede Boş Uygulama **(Evrensel uygulama) Windows.** Ardından projeye *HelloWorld* adını ve Tamam'ı **seçin.**

   > [!NOTE]
   > Kaynak projenin konumunun İşletim Sistemi (OS) sürücü gibi Yeni Teknoloji Dosya Sistemi **(NTFS)** biçimlendirilmiş bir sürücüde olduğundan emin olun. Aksi takdirde, projenizi inşa ve çalıştırma konusunda sorun olabilir. 

   ![IDE'Windows Yeni Uygulama iletişim kutusundaki Evrensel Project şablonunu gösteren Visual Studio görüntüsü.](media/new-project-csharp-uwp-helloworld.png)

   > [!NOTE]
   > Boş Uygulama **(Evrensel Windows)** proje şablonunu görmüyorsanız Yeni Uygulama iletişim kutusunun **sol** bölmesinde Visual Studio Yükleyicisi Aç bağlantısı **Project na** tıklayın.<br><br>![Yeni Uygulama iletişim kutusunda 'Visual Studio Yükleyicisi' bağlantısını gösteren Project görüntüsü.](../../ide/media/vb-open-visual-studio-installer-hello-world.png)<br><br>Uygulama Visual Studio Yükleyicisi başlatıyor. Universal **Windows Platform geliştirme iş yükünü** ve ardından Değiştir'i **seçin.**<br><br>![Universal Windows Platform geliştirme iş yükünü gösteren Visual Studio Yükleyicisi ekran görüntüsü.](media/uwp-dev-workload.png)

1. Yeni Evrensel Sürüm **Platformu iletişim** **kutusunda varsayılan** Hedef sürüm ve En Windows **sürüm Project** kabul edin.

   ![Varsayılan Hedef sürüm ve En Windows ayarlarını Project Evrensel Platform Platformu iletişim kutusunun ekran görüntüsü.](media/new-uwp-project-target-minver-dialog.png)
::: moniker-end

::: moniker range="vs-2019"
1. Yeni Visual Studio açın ve başlangıç penceresinde Yeni proje **oluştur'a tıklayın.**

1. Yeni proje **oluştur ekranında,** arama *kutusuna Evrensel Windows* girin, Boş Uygulama **(Evrensel Windows)** için C# şablonunu seçin ve ardından Sonraki'yi **seçin.**

   ![Arama kutusuna 'evrensel pencereler' girildi ve 'Boş Uygulama (Evrensel Windows)' proje şablonunun vurgulanmış olduğu 'Yeni proje oluştur' iletişim kutusunun ekran görüntüsü.](media/vs-2019/uwp-create-new-project.png)

   > [!NOTE]
   > Boş Uygulama **(Universal Windows)** proje şablonunu görmüyorsanız Daha fazla araç ve özellik **yükle bağlantısına** tıklayın.<br><br>!['Daha fazla araç ve özellik yükle' bağlantısını gösteren Yeni proje oluştur penceresinin ekran görüntüsü.](media/vs-2019/uwp-not-finding.png)<br><br>Uygulama Visual Studio Yükleyicisi başlatıyor. Universal **Windows Platform geliştirme iş yükünü** ve ardından Değiştir'i **seçin.**<br><br>![Universal Windows Platform geliştirme iş yükünü gösteren Visual Studio Yükleyicisi ekran görüntüsü.](media/uwp-dev-workload.png)

1. Projeye _HelloWorld_ adını girin ve Oluştur'a **seçin.**

   !['Yeni projenizi yapılandır' iletişim kutusunun ekran görüntüsü ve ad alanına 'HelloWorld' Project girildi.](media/vs-2019/uwp-configure-your-project.png)

1. Yeni Evrensel Sürüm **Platformu iletişim** **kutusunda varsayılan** Hedef sürüm ve En Windows **sürüm Project** kabul edin.

   ![Varsayılan Hedef sürüm ve En Windows ayarlarını Project Evrensel Platform Platformu iletişim kutusunun ekran görüntüsü.](media/vs-2019/new-uwp-project-target-minver-dialog.png)
::: moniker-end

::: moniker range=">=vs-2022"
1. Yeni Visual Studio açın ve başlangıç penceresinde Yeni proje **oluştur'a tıklayın.**

1. Yeni proje **oluştur ekranında,** arama *kutusuna Evrensel Windows* girin, Boş Uygulama **(Evrensel Windows)** için C# şablonunu seçin ve ardından Sonraki'yi **seçin.**

   :::image type="content" source="media/vs-2022/uwp-create-new-project.png" alt-text="Arama kutusuna 'Evrensel Windows' girildi ve 'Boş Uygulama (Evrensel Windows)' proje şablonunun vurgulanmış olduğu 'Yeni proje oluştur' iletişim kutusunun ekran görüntüsü.":::

   > [!NOTE]
   > Boş Uygulama **(Universal Windows)** proje şablonunu görmüyorsanız Daha fazla araç ve özellik **yükle bağlantısına** tıklayın.<br><br>:::image type="content" source="media/vs-2022/uwp-not-finding.png" alt-text="'Daha fazla araç ve özellik yükle' bağlantısını gösteren Yeni proje oluştur penceresinin ekran görüntüsü.":::<br><br>Uygulama Visual Studio Yükleyicisi başlatıyor. Universal **Windows Platform geliştirme iş yükünü** ve ardından Değiştir'i **seçin.**<br><br>:::image type="content" source="media/vs-2022/uwp-dev-workload.png" alt-text="Universal Windows Platform geliştirme iş yükünü gösteren Visual Studio Yükleyicisi ekran görüntüsü.":::

1. Projeye *HelloWorld* adını girin ve Oluştur'a **seçin.**

   :::image type="content" source="media/vs-2022/uwp-configure-your-project.png" alt-text="'Yeni projenizi yapılandır' iletişim kutusunun ekran görüntüsü ve ad alanına 'HelloWorld' Project girildi.":::

1. Yeni Evrensel Sürüm **Platformu iletişim** **kutusunda varsayılan** Hedef sürüm ve En Windows **sürüm Project** kabul edin.

   :::image type="content" source="media/vs-2022/new-uwp-project-target-minver-dialog.png" alt-text="Varsayılan Hedef sürüm ve En Windows ayarlarını Project Evrensel Platform Platformu iletişim kutusunun ekran görüntüsü.":::

::: moniker-end

   > [!NOTE]
   > UWP uygulaması oluşturmak için Visual Studio kez kullandıysanız, Ayarlar **iletişim** kutusu görünebilir. Geliştirici **modu'larını** ve ardından Evet'i **seçin.**<br><br>
   > ![Geliştirici Modunu etkinleştirme seçeneğiyle UWP Ayarlar iletişim kutusunu gösteren ekran görüntüsü.](media/enable-developer-mode.png)<br><br>Visual Studio sizin için ek bir Geliştirici Modu paketi yüklü olur. Paket yüklemesi tamamlandığında, Ayarlar **iletişim** kutusunu kapatın.

## <a name="create-the-application"></a>Uygulama oluşturma

Geliştirmeye başlamanın zamanı geldi. Düğme denetimi ekler, düğmeye eylem ekler ve ardından "Merhaba Dünya" uygulamasını başlatarak nasıl göründüğünü kontrol edin.

### <a name="add-a-button-to-the-design-canvas"></a>Tasarım tuvale düğme ekleme

::: moniker range="vs-2017"

1. Dosyanın **Çözüm Gezgini** *MainPage.xaml'e çift* tıklar ve bölünmüş bir görünüm açın.

   ![HelloWorld Çözüm Gezgini özellikleri, başvuruları, varlıkları ve dosyaları gösteren ekran görüntüsü. MainPage.xaml dosyası seçilidir.](media/uwp-solution-explorer-MainPage-xaml.png)

   İki bölme vardır: **XAML Tasarımcısı** tuvali içeren XAML Tasarımcısı ve kod ekpleri değiştirerek **XAML** Düzenleyicisi'ni içerir.

   ![IDE'de MainPage.xaml'in Visual Studio ekran görüntüsü. Bu XAML Tasarımcısı boş bir tasarım yüzeyi, XAML Düzenleyicisi bölmesi ise XAML kodunun bir bölümü gösterir.](media/uwp-xaml-editor.png)

1. Araç **Kutusu açılır** penceresini açmak için Araç Kutusu'nı seçin.

   !['Toolbox' açılır penceresinin sekmesinin, Bölme'nin sol tarafında vurgulanmış XAML Tasarımcısı ekran görüntüsü.](media/uwp-toolbox.png)

   (Araç Kutusu seçeneğini **görmüyorsanız** menü çubuğundan açabilirsiniz. Bunu yapmak için Araç Çubuğunu **Görüntüle'yi**  >  **seçin.** Veya **Ctrl** Alt X +  + **tuşlarına basın.)**

1. Araç Kutusu **penceresini** sabitlemek için Sabitle simgesine tıklayın.

   ![Araç Kutusu penceresinin üst çubuğunda vurgulanmış Sabitle simgesini gösteren ekran görüntüsü.](media/uwp-toolbox-autohide.png)

1. Düğme **denetimine** tıklayın ve tasarım tuvali üzerine sürükleyin.

   ![Araç Kutusu penceresinde 'Düğme' vurgulanmış ve tasarım tuvali üzerinde bir Düğme denetimi gösteren ekran görüntüsü.](media/uwp-toolbox-add-button-control.png)

   **XAML** Düzenleyicisi'nde koda bakarsanız, buraya Düğme'nin de eklenmiştir:

   ![XAML düzenleyicisinde vurgulanan yeni eklenen Düğmenin kodunu gösteren ekran görüntüsü.](media/uwp-xaml-control-code-window.png)

::: moniker-end

::: moniker range="vs-2019"

1. Dosyanın **Çözüm Gezgini** *MainPage.xaml'e çift* tıklar ve bölünmüş bir görünüm açın.

   ![HelloWorld Çözüm Gezgini özellikleri, başvuruları, varlıkları ve dosyaları gösteren ekran görüntüsü. MainPage.xaml dosyası seçilidir.](media/vs-2019/uwp-solution-explorer-mainpage-xaml.png)

   İki bölme vardır: **XAML Tasarımcısı** tuvali içeren XAML Tasarımcısı ve kod ekpleri değiştirerek **XAML** Düzenleyicisi'ni içerir.

   ![IDE'de MainPage.xaml'in Visual Studio ekran görüntüsü. Bu XAML Tasarımcısı boş bir tasarım yüzeyi, XAML Düzenleyicisi bölmesi ise XAML kodunun bir bölümü gösterir.](media/uwp-xaml-editor.png)

1. Araç **Kutusu açılır** penceresini açmak için Araç Kutusu'nı seçin.

   !['Toolbox' açılır penceresinin sekmesinin, Bölme'nin sol tarafında vurgulanmış XAML Tasarımcısı ekran görüntüsü.](media/uwp-toolbox.png)

   (Araç Kutusu seçeneğini **görmüyorsanız** menü çubuğundan açabilirsiniz. Bunu yapmak için Araç Çubuğunu **Görüntüle'yi**  >  **seçin.** Veya **Ctrl** Alt X +  + **tuşlarına basın.)**

1. Araç Kutusu **penceresini** sabitlemek için Sabitle simgesine tıklayın.

   ![Araç Kutusu penceresinin üst çubuğunda vurgulanmış Sabitle simgesini gösteren ekran görüntüsü.](media/uwp-toolbox-autohide.png)

1. Düğme **denetimine** tıklayın ve tasarım tuvali üzerine sürükleyin.

   ![Araç Kutusu penceresinde 'Düğme' vurgulanmış ve tasarım tuvali üzerinde bir Düğme denetimi gösteren ekran görüntüsü.](media/uwp-toolbox-add-button-control.png)

   **XAML** Düzenleyicisi'nde koda bakarsanız, buraya Düğme'nin de eklenmiştir:

   ![XAML düzenleyicisinde vurgulanan yeni eklenen Düğmenin kodunu gösteren ekran görüntüsü.](media/uwp-xaml-control-code-window.png)

::: moniker-end

::: moniker range=">=vs-2022"

1. Dosyanın **Çözüm Gezgini** *MainPage.xaml'e çift* tıklar ve bölünmüş bir görünüm açın.

   :::image type="content" source="media/vs-2022/uwp-solution-explorer-mainpage-xaml.png" alt-text="HelloWorld Çözüm Gezgini özellikleri, başvuruları, varlıkları ve dosyaları gösteren ekran görüntüsü. MainPage.xaml dosyası seçilidir.":::  

   İki bölme vardır: **XAML Tasarımcısı** tuvali içeren XAML Tasarımcısı ve kod ekpleri değiştirerek **XAML** Düzenleyicisi'ni içerir.

   :::image type="content" source="media/vs-2022/uwp-xaml-editor.png" alt-text="IDE'de MainPage.xaml'in Visual Studio ekran görüntüsü. Bu XAML Tasarımcısı boş bir tasarım yüzeyi, XAML Düzenleyicisi bölmesinde ise XAML kodunun bazıları gösterilir.":::

1. Araç **Kutusu açılır** penceresini açmak için Araç Kutusu'nı seçin.

   :::image type="content" source="media/vs-2022/uwp-toolbox.png" alt-text="'Toolbox' açılır penceresinin sekmesinin, Bölme'nin sol tarafında vurgulanmış XAML Tasarımcısı ekran görüntüsü.":::

   (Araç Kutusu seçeneğini **görmüyorsanız** menü çubuğundan açabilirsiniz. Bunu yapmak için Araç Çubuğunu **Görüntüle'yi**  >  **seçin.** Veya **Ctrl** Alt X +  + **tuşlarına basın.)**

1. Araç Kutusu **penceresini** sabitlemek için Sabitle simgesini seçin.

   :::image type="content" source="media/vs-2022/uwp-toolbox-autohide.png" alt-text="Araç Kutusu penceresinin üst çubuğunda vurgulanmış Sabitle simgesini gösteren ekran görüntüsü.":::

1. Düğme **denetimi'ne** tıklayın ve tasarım tuvali üzerine sürükleyin.

   :::image type="content" source="media/vs-2022/uwp-toolbox-add-button-control.png" alt-text="Araç Kutusu penceresinde 'Düğme' vurgulanmış ve tasarım tuvali üzerinde bir Düğme denetimi gösteren ekran görüntüsü.":::

   **XAML** Düzenleyicisi'nde koda bakarsanız, buraya Düğme'nin de eklenmiştir:

   :::image type="content" source="media/vs-2022/uwp-xaml-control-code-window.png" alt-text="XAML düzenleyicisinde vurgulanan yeni eklenen Düğmenin kodunu gösteren ekran görüntüsü.":::
 
::: moniker-end

### <a name="add-a-label-to-the-button"></a>Düğmeye etiket ekleme

::: moniker range="<=vs-2019"

1. **XAML Düzenleyicisi'nde** Düğme İçeriği değerini "Düğme" yerine "Merhaba Dünya!".

   ![XAML düzenleyicisinde Düğme için XAML kodunu gösteren ekran görüntüsü. Content özelliğinin değeri 'Merhaba Dünya!' olarak değiştirildi.](media/uwp-change-button-text-in-xaml-code-window.png)

1. Aşağıdaki düğmenin de **XAML Tasarımcısı** dikkat.

   ![Uygulamanın tuvali üzerinde Düğme XAML Tasarımcısı. Düğmenin etiketi 'Merhaba Dünya!' olarak değiştirildi.](media/uwp-button-text-change-in-design-canvas.png)

::: moniker-end

::: moniker range=">=vs-2022"

1. **XAML Düzenleyicisi'nde** Düğme İçeriği değerini "Düğme" yerine "Merhaba Dünya!".

   :::image type="content" source="media/vs-2022/uwp-change-button-text-in-xaml-code-window.png" alt-text="XAML düzenleyicisinde Düğme için XAML kodunu gösteren ekran görüntüsü. Content özelliğinin değeri 'Merhaba Dünya!' olarak değiştirildi.":::

1. Aşağıdaki düğmenin de **XAML Tasarımcısı** dikkat.

   :::image type="content" source="media/vs-2022/uwp-button-text-change-in-design-canvas.png" alt-text="Uygulamanın tuvali üzerinde Düğme XAML Tasarımcısı. Düğmenin etiketi 'Merhaba Dünya!' olarak değiştirildi.":::

::: moniker-end

### <a name="add-an-event-handler"></a>Olay işleyicisi ekleme

"Olay işleyicisi" karmaşık gibi görünüyor, ancak bir olay olduğunda kod için çağrılmış başka bir addır. Bu durumda, "Merhaba Dünya!" tıklayın.

::: moniker range="vs-2019"

1. Tasarım tuvali üzerinde düğme denetimine çift tıklayın.

1. Olay işleyicisi kodunu *MainPage.xaml.cs* içinde , arka arkasındaki kod sayfasında düzenleyin.

   İşte işler burada ilginçleşiyor. Varsayılan olay işleyicisi şu şekildedir:

   ![Varsayılan olay işleyicisi için C# Button_Click gösteren ekran görüntüsü.](media/uwp-button-click-code.png)

   Şimdi bunu değiştir, şöyle bir görünüme bakalım:

   ![Yeni zaman uyumsuz olay işleyicisi için C# Button_Click gösteren ekran görüntüsü.](media/uwp-add-hello-world-async-code.png)

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

::: moniker-end

::: moniker range=">=vs-2022"

1. Tasarım tuvali üzerinde düğme denetimine çift tıklayın.

1. Olay işleyicisi kodunu *MainPage.xaml.cs* içinde , arka arkasındaki kod sayfasında düzenleyin.

   İşte işler burada ilginçleşiyor. Varsayılan olay işleyicisi şu şekildedir:

   :::image type="content" source="media/vs-2022/uwp-button-click-code.png" alt-text="Varsayılan olay işleyicisi için C# Button_Click gösteren ekran görüntüsü.":::

   Şimdi bunu değiştir, şöyle bir görünüme bakalım:

   :::image type="content" source="media/vs-2022/uwp-add-hello-world-async-code.png" alt-text="Yeni zaman uyumsuz olay işleyicisi için C# Button_Click gösteren ekran görüntüsü.":::

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

::: moniker-end

#### <a name="what-did-we-just-do"></a>Az önce ne yaptık?

Kod, konuşma Windows nesnesi oluşturmak için bazı api'ler kullanır ve ardından bunu söylemesi için biraz metin verir. (kullanma hakkında daha fazla bilgi için `SpeechSynthesis`  <xref:System.Speech.Synthesis> bkz. .)

## <a name="run-the-application"></a>Uygulamayı çalıştırma

::: moniker range="vs-2017"
Şimdi "Merhaba Dünya" UWP uygulamasını derlemenin, dağıtmanın ve başlatmanın zamanı geldi. Aşağıdaki adımları uygulayın:

1. Uygulamayı yerel makinede başlatmak için Oynat **düğmesini (Yerel** Makine metni vardır) kullanın.

   !['Yerel Makine' seçiliyken Oynat düğmesinin yanında açılan kutunun açılmasını gösteren ekran görüntüsü.](media/uwp-start-or-debug.png)

   (Alternatif olarak Hata **Ayıkla'ya da seçebilirsiniz** > **Menü çubuğundan Hata** Ayıklamayı başlat veya **F5 tuşuna** basarak uygulamayı başlat.)

1. Giriş ekranı görüntüden kaybolduktan kısa süre sonra görünen uygulamanızı görüntüleme. Uygulama şuna benzer şekilde görünüyor olmalı:

   ![Çalışan UWP 'Merhaba Dünya' uygulamasını gösteren ekran görüntüsü.](media/uwp-hello-world-app.png)

1. İlke **düğmesine Merhaba Dünya** tıklayın.

   Cihazınız Windows 10 veya sonraki bir cihazda "Hello, World!"

1. Uygulamayı kapatmak için araç **çubuğundaki Hata Ayıklamayı** Durdur düğmesine tıklayın. (Alternatif olarak Hata **Ayıkla'ya da**  >  **Menü çubuğundan hata** ayıklamayı durdurun veya **Shift+F5 tuşlarına basın.)**

::: moniker-end
::: moniker range="vs-2019"
Şimdi "Merhaba Dünya" UWP uygulamasını derlemenin, dağıtmanın ve başlatmanın zamanı geldi. Aşağıdaki adımları uygulayın:

1. Uygulamayı yerel makinede başlatmak için Oynat **düğmesini (Yerel** Makine metni vardır) kullanın.

   !['Yerel Makine' seçiliyken Oynat düğmesinin yanında açılan kutunun açılmasını gösteren ekran görüntüsü.](media/uwp-start-or-debug.png)

   (Alternatif olarak Hata **Ayıkla'ya da seçebilirsiniz** > **Menü çubuğundan Hata** Ayıklamayı başlat veya **F5 tuşuna** basarak uygulamayı başlat.)

1. Giriş ekranı görüntüden kaybolduktan kısa süre sonra görünen uygulamanızı görüntüleme. Uygulama şuna benzer şekilde görünüyor olmalı:

   ![Çalışan UWP 'Merhaba Dünya' uygulamasını gösteren ekran görüntüsü.](media/vs-2019/uwp-hello-world-app.png)

1. İlke **düğmesine Merhaba Dünya** tıklayın.

   Cihazınız Windows 10 veya sonraki bir cihazda "Hello, World!"

1. Uygulamayı kapatmak için araç **çubuğundaki Hata Ayıklamayı** Durdur düğmesine tıklayın. (Alternatif olarak Hata **Ayıkla'ya da**  >  **Menü çubuğundan hata** ayıklamayı durdurun veya **Shift+F5 tuşlarına basın.)**

::: moniker-end

::: moniker range=">=vs-2022"

Şimdi "Merhaba Dünya" UWP uygulamasını derlemenin, dağıtmanın ve başlatmanın zamanı geldi. Aşağıdaki adımları uygulayın:

1. Uygulamayı yerel makinede başlatmak için Oynat **düğmesini (Yerel** Makine metni vardır) kullanın.

   :::image type="content" source="media/vs-2022/uwp-start-or-debug.png" alt-text="'Yerel Makine' seçiliyken Oynat düğmesinin yanında açılan kutunun açılmasını gösteren ekran görüntüsü.":::

   (Alternatif olarak Hata **Ayıkla'ya da seçebilirsiniz** > **Menü çubuğundan Hata** Ayıklamayı başlat veya **F5 tuşuna** basarak uygulamayı başlat.)

1. Giriş ekranı görüntüden kaybolduktan kısa süre sonra görünen uygulamanızı görüntüleme. Uygulama şu görüntüye benzer şekilde görüntüye benzer:

   :::image type="content" source="media/vs-2022/uwp-hello-world-app.png" alt-text="Çalışan UWP 'Merhaba Dünya' uygulamasını gösteren ekran görüntüsü.":::

1. İlke **düğmesini Merhaba Dünya** seçin.

   Cihazınız Windows 10 veya sonraki bir cihazda tam olarak "Hello, World!" (Merhaba Dünya!" şeklindedir.

1. Uygulamayı kapatmak için araç çubuğunda **Hata Ayıklamayı Durdur** düğmesini seçin. (Alternatif olarak Hata **Ayıkla'ya da**  >  **Menü çubuğundan hata** ayıklamayı durdurun veya **Shift+F5 tuşlarına basın.)**

::: moniker-end

## <a name="next-steps"></a>Sonraki adımlar

Tebrikler, bu öğreticiyi tamamladıktan sonra! UWP ve IDE ile ilgili temel bilgileri Visual Studio umuyoruz. Daha fazla bilgi edinmek için aşağıdaki öğreticiyle devam edin:

> [!div class="nextstepaction"]
> [Kullanıcı arabirimi oluşturma](/windows/uwp/design/basics/xaml-basics-ui)

## <a name="see-also"></a>Ayrıca bkz.

- [UWP’ye genel bakış](/windows/uwp/get-started/universal-application-platform-guide)
- [UWP uygulama örneklerini alın](/windows/uwp/get-started/get-uwp-app-samples)
