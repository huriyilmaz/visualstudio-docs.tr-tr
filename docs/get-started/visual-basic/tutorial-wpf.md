---
title: Visual Basic içinde WPF ile uygulama Merhaba Dünya
description: Windows Presentation Foundation (WPF) Kullanıcı arabirimi çerçevesini kullanarak Visual Studio ile Visual Basic basit bir Windows Masaüstü .NET uygulaması oluşturun.
ms.custom: seodec18, get-started
ms.date: 04/23/2019
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: tutorial
dev_langs:
- VB
ms.assetid: f84339c7-d617-4f56-bfcd-af2215c347ba
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: bc57e3d104d7f8427e97eb6b3dd97ca3e89bc49e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85419217"
---
# <a name="tutorial-create-a-simple-application-with-visual-basic"></a>Öğretici: Visual Basic ile basit bir uygulama oluşturma

Bu öğreticiyi tamamlayarak, Visual Studio ile uygulama geliştirirken kullanabileceğiniz birçok araç, iletişim kutusu ve tasarımcı hakkında bilgi sahibi olacaksınız. Tümleşik geliştirme ortamında ([IDE](visual-studio-ide.md)) çalışmayı öğrenirken, "Merhaba, Dünya" uygulaması, Kullanıcı arabirimini tasarlayacağınız, kod ekleyerek ve hata ayıkladığınızda bir "Hello, World" uygulaması oluşturacaksınız.

::: moniker range="vs-2017"

Visual Studio 'Yu henüz yüklemediyseniz, [Visual Studio İndirmeleri](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) sayfasına giderek ücretsiz olarak yükleme yapın.

::: moniker-end

::: moniker range=">=vs-2019"

Visual Studio 'Yu henüz yüklemediyseniz, [Visual Studio İndirmeleri](https://visualstudio.microsoft.com/downloads) sayfasına giderek ücretsiz olarak yükleme yapın.

::: moniker-end

## <a name="configure-the-ide"></a>IDE'yi yapılandırma

::: moniker range="vs-2017"

Visual Studio 'Yu ilk kez açtığınızda, oturum açmanız istenir. Bu adım, bu öğretici için isteğe bağlıdır. Ardından, geliştirme ayarlarınızı ve renk temasını seçmenizi isteyen bir iletişim kutusu görüntülenebilir. Varsayılanları koruyun ve **Visual Studio 'Yu Başlat**' ı seçin.

![Ayarları Seç iletişim kutusu](../media/exploreide-settings.png)

Visual Studio başlatıldıktan sonra araç pencerelerini, menüleri ve araç çubuklarını ve ana pencere alanını görürsünüz. Araç pencereleri, **Hızlı Başlat**, menü çubuğu ve en üstteki Standart araç çubuğu ile uygulama penceresinin sol ve sağ taraflarına yerleştirilir. Uygulama penceresinin merkezinde **Başlangıç sayfası**bulunur. Bir çözüm veya proje yüklediğinizde, düzenleyiciler ve tasarımcılar **Başlangıç sayfasının** bulunduğu alanda görüntülenir. Bir uygulama geliştirirken, bu merkezi alanda zamanınızın çoğunu harcarcaksınız.

![Genel ayarlar uygulanmış şekilde Visual Studio 2017 IDE](../media/exploreide-idewithgeneralsettings.png)

::: moniker-end

::: moniker range=">=vs-2019"

Visual Studio 'Yu başlattığınızda ilk olarak başlangıç penceresi açılır. Geliştirme ortamını açmak için **kod olmadan devam et** ' i seçin. Araç pencerelerini, menüleri ve araç çubuklarını ve ana pencere alanını görürsünüz. Araç pencereleri, uygulama penceresinin sol ve sağ taraflarından, bir arama kutusuyla, menü çubuğundan ve en üstteki Standart araç çubuğundan yerleştirildi. Bir çözüm veya proje yüklediğinizde, düzenleyiciler ve tasarımcılar uygulama penceresinin orta alanında görüntülenir. Bir uygulama geliştirirken, bu merkezi alanda zamanınızın çoğunu harcarcaksınız.

::: moniker-end

## <a name="create-the-project"></a>Proje oluşturma

Visual Studio'da bir uygulama oluştururken önce bir proje ve bir çözüm oluşturursunuz. Bu örnekte, bir Windows Presentation Foundation (WPF) projesi oluşturacaksınız.

::: moniker range="vs-2017"

1. Yeni bir proje oluşturma. Menü çubuğunda **Dosya**  >  **Yeni**  >  **Proje**' yi seçin.

     ![Menü çubuğunda dosya, yeni, proje ' yi seçin.](../media/exploreide-filenewproject.png)

2. **Yeni proje** iletişim kutusunda, **Installed**  >  **Visual Basic**  >  **Windows Masaüstü** Visual Basic yüklendi kategorisini seçin ve ardından **WPF uygulaması (.NET Framework)** şablonunu seçin. Projeyi **HelloWPFApp**olarak adlandırın ve **Tamam**' ı seçin.

     ![Visual Studio 'da WPF uygulama şablonu yeni proje iletişim kutusu](media/exploreide-newproject-vb.png)

Visual Studio HelloWPFApp projesini ve çözümünü oluşturur ve **Çözüm Gezgini** çeşitli dosyaları gösterir. **WPF Tasarımcısı** , bölünmüş bir görünümde *MainWindow. xaml* ' in BIR Tasarım görünümünü ve XAML görünümünü gösterir. Herhangi bir görünümden daha fazla veya daha az görünmesi için Bölümlendirici slaytı gösterebilirsiniz. Yalnızca görsel görünümü veya yalnızca XAML görünümünü görmeyi seçebilirsiniz. Aşağıdaki öğeler **Çözüm Gezgini**görüntülenir:

![HelloWPFApp dosyaları yüklü Çözüm Gezgini](../media/exploreide-hellowpfappfiles.png)

::: moniker-end

::: moniker range="vs-2019"

1. Visual Studio 2019 ' i açın.

2. **Yeni proje oluştur** ekranında, "WPF" araması yapın ve **WPF uygulaması (.NET Framework)** öğesini seçin ve ardından **İleri**' yi seçin.

   ![Visual Studio 'da WPF uygulama şablonu yeni proje iletişim kutusu](media/vs-2019/exploreide-newprojectvb-vs2019.png)

3. Sonraki ekranda, projeye **HelloWPFApp**adını verin ve **Oluştur**' u seçin.

Visual Studio HelloWPFApp projesini ve çözümünü oluşturur ve **Çözüm Gezgini** çeşitli dosyaları gösterir. **WPF Tasarımcısı** , bölünmüş bir görünümde *MainWindow. xaml* ' in BIR Tasarım görünümünü ve XAML görünümünü gösterir. Herhangi bir görünümden daha fazla veya daha az görünmesi için Bölümlendirici slaytı gösterebilirsiniz. Yalnızca görsel görünümü veya yalnızca XAML görünümünü görmeyi seçebilirsiniz. Aşağıdaki öğeler **Çözüm Gezgini**görüntülenir:

![HelloWPFApp dosyaları yüklü Çözüm Gezgini](../media/vs-2019/exploreide-hellowpfappfiles.png)

::: moniker-end

> [!NOTE]
> XAML (Genişletilebilir uygulama biçimlendirme dili) hakkında daha fazla bilgi için bkz. [WPF Için xaml genel bakış](/dotnet/framework/wpf/advanced/xaml-overview-wpf) sayfası.

Projeyi oluşturduktan sonra özelleştirebilirsiniz. **Özellikler** penceresini kullanarak ( **Görünüm** menüsünde bulunur), bir uygulamadaki proje öğeleri, denetimler ve diğer öğeler için seçenekleri görüntüleyebilir ve değiştirebilirsiniz.

### <a name="change-the-name-of-mainwindowxaml"></a>MainWindow. xaml adını değiştirme

Şimdi, MainWindow 'e daha özel bir ad verelim. **Çözüm Gezgini**, *MainWindow. xaml* ' e sağ tıklayıp **Yeniden Adlandır**' ı seçin. Dosyayı *Greetings. xaml*olarak yeniden adlandırın.

## <a name="design-the-user-interface-ui"></a>Kullanıcı arabirimini (UI) tasarlama

Tasarımcı açık değilse, **Çözüm Gezgini** *Greetings. xaml* ' i seçin ve sonra **Shift** + da tasarımcıyı açmak için SHIFT**F7** tuşuna basın.

Bu uygulamaya üç tür denetim ekleyeceğiz: <xref:System.Windows.Controls.TextBlock> Denetim, iki denetim <xref:System.Windows.Controls.RadioButton> ve bir <xref:System.Windows.Controls.Button> Denetim.

### <a name="add-a-textblock-control"></a>TextBlock denetimi ekleme

1. **CTRL** + **Q** tuşlarına basarak arama kutusunu etkinleştirin ve **araç kutusu**yazın. Sonuçlar listesinden **> araç kutusunu görüntüle** ' yi seçin.

2. **Araç kutusunda**, TextBlock denetimini görmek IÇIN **ortak WPF denetimleri** düğümünü genişletin.

     ![TextBlock denetimi vurgulanmış olan araç kutusu](../media/exploreide-textblocktoolbox.png)

3. **TextBlock** öğesini seçerek ve tasarım yüzeyinde pencereye sürükleyerek tasarım yüzeyine bir TextBlock denetimi ekleyin. Pencerenin üst kısmına yakın olan denetimi ortalayın. Visual Studio 2019 ve üzeri sürümlerde, denetimi ortalamak için kırmızı yönergeleri kullanabilirsiniz.

Pencereniz aşağıdaki gösterime benzemelidir:

![Greetings formundaki TextBlock denetimi](../media/exploreide-greetingswithtextblockonly.png)

XAML işaretlemesi aşağıdaki örnekteki gibi görünmelidir:

```xaml
<TextBlock HorizontalAlignment="Left" Margin="381,100,0,0" TextWrapping="Wrap" Text="TextBlock" VerticalAlignment="Top"/>
```

### <a name="customize-the-text-in-the-text-block"></a>Metin bloğundaki metni özelleştirme

1. XAML görünümünde TextBlock için biçimlendirmeyi bulun ve metin özniteliğini değiştirin:

   ```xaml
   Text="Select a message option and then choose the Display button."
   ```

2. Gerekirse TextBlock 'ı yeniden ortalayın ve CTRL + S tuşlarına basarak veya **Dosya** menü öğesini kullanarak yaptığınız değişiklikleri kaydedin.

Ardından, forma iki [RadioButton](/dotnet/framework/wpf/controls/radiobutton) denetimi ekleyeceksiniz.

### <a name="add-radio-buttons"></a>Radyo düğmesi ekleme

1. **Araç kutusunda** **RadioButton** denetimini bulun.

     ![RadioButton denetimi seçiliyken araç kutusu penceresi](../media/exploreide-radiobuttontoolbox.png)

2. **RadioButton** öğesini seçerek ve tasarım yüzeyinde pencereye sürükleyerek tasarım yüzeyine iki RadioButton denetimi ekleyin. Düğmeleri TextBlock denetimi altında yan yana görünecek şekilde düğmeleri (onları seçerek ve ok tuşlarını kullanarak) taşıyın. Denetimleri hizalamak için kırmızı yönergeleri kullanın.

     Pencerenizin şuna benzemesi gerekir:

     ![TextBlock denetimi ve iki radyo düğmesi içeren Tebrikler formu](../media/exploreide-greetingswithradiobuttons.png)

3. Sol RadioButton denetimi için **Özellikler** penceresinde, **ad** özelliğini ( **Özellikler** penceresinin üst kısmındaki özellik) olarak değiştirin `HelloButton` .

     ![RadioButton Özellikler penceresi](../media/exploreide-buttonproperties.png)

4. Sağ RadioButton denetimi için **Özellikler** penceresinde, **ad** özelliğini olarak değiştirin `GoodbyeButton` ve ardından değişikliklerinizi kaydedin.

Artık her bir RadioButton denetimi için görüntü metni ekleyebilirsiniz. Aşağıdaki yordam bir RadioButton denetimi için **içerik** özelliğini güncelleştirir.

### <a name="add-display-text-for-each-radio-button"></a>Her radyo düğmesi için görüntü metni Ekle

XAML içinde ve için **içerik** özniteliğini `HelloButton` güncelleştirin `GoodbyeButton` `"Hello"` `"Goodbye"` . XAML işaretlemesi artık aşağıdaki örneğe benzer şekilde görünmelidir:

   ```xaml
   <Grid>
        <TextBlock HorizontalAlignment="Left" Margin="252,47,0,0" TextWrapping="Wrap" Text="Select a message option and then choose the Display button." VerticalAlignment="Top"/>
        <RadioButton x:Name="HelloButton" Content="Hello" HorizontalAlignment="Left" Margin="297,161,0,0" VerticalAlignment="Top"/>
        <RadioButton x:Name="GoodbyeButton" Content="Goodbye" HorizontalAlignment="Left" Margin="488,161,0,0" VerticalAlignment="Top"/>
   </Grid>
   ```

### <a name="set-a-radio-button-to-be-checked-by-default"></a>Radyo düğmesini varsayılan olarak denetlenecek şekilde ayarla

Bu adımda, her zaman iki radyo düğmelerinden biri seçili olacak şekilde, Merhaba düğmesini varsayılan olarak denetlenecek şekilde ayarlayacağız.

XAML görünümünde, Merhaba düğmesine yönelik biçimlendirmeyi bulun ve bir **IsChecked** özniteliği ekleyin:

```xaml
IsChecked="True"
```

Ekleyeceğiniz son UI öğesi bir [düğme](/dotnet/framework/wpf/controls/button) denetimidir.

### <a name="add-the-button-control"></a>Düğme denetimini ekleme

1. **Araç kutusunda** **düğme** denetimini bulun ve ardından Tasarım görünümündeki forma sürükleyerek RadioButton denetimlerinin altındaki tasarım yüzeyine ekleyin. Visual Studio 2019 veya sonraki bir sürümü kullanıyorsanız, kırmızı bir çizgi denetimi ortalemenize yardımcı olur.

2. XAML görünümünde düğme denetimi için **içerik** değerini `Content="Button"` olarak değiştirin `Content="Display"` ve ardından değişiklikleri kaydedin.

     Biçimlendirme aşağıdaki örneğe benzemelidir:   `<Button Content="Display" HorizontalAlignment="Left" VerticalAlignment="Top" Width="75" Margin="215,204,0,0"/>`

     Pencereniz aşağıdaki gösterime benzemelidir.

     ![Denetim etiketleriyle Greetings formu](../media/exploreide-greetingswithcontrollabels.png)

### <a name="add-code-to-the-display-button"></a>Görüntü düğmesine kod ekleme

Bu uygulama çalıştığında, bir Kullanıcı radyo düğmesini seçtikten sonra **görüntüle** düğmesini seçtiğinde bir ileti kutusu görünür. Merhaba için bir ileti kutusu ve Güle Güle için bir diğer ileti kutusu görünecektir. Bu davranışı oluşturmak için `Button_Click` *Greetings. xaml. vb* veya *Greetings.xaml.cs*içindeki olaya kod ekleyeceksiniz.

1. Tasarım yüzeyinde **görüntüle** düğmesine çift tıklayın.

     *Greetings. xaml. vb* , olayında imleç ile açılır `Button_Click` .

    ```vb
    Private Sub Button_Click(sender As Object, e As RoutedEventArgs)

    End Sub
    ```

2. Aşağıdaki kodu girin:

    ```vb
    If HelloButton.IsChecked = True Then
        MessageBox.Show("Hello.")
    ElseIf GoodbyeButton.IsChecked = True Then
        MessageBox.Show("Goodbye.")
    End If
    ```

3. Uygulamayı kaydedin.

## <a name="debug-and-test-the-application"></a>Uygulamanın hatalarını ayıklama ve test etme

Sonra, hataları bulmak ve her iki ileti kutusunun doğru şekilde göründüğünü sınamak için uygulamada hata ayıklaması yapacaksınız. Aşağıdaki yönergelerde hata ayıklayıcıyı nasıl derleyip başlatacağınız, ancak daha sonra daha fazla bilgi için WPF [uygulaması (WPF) oluşturma](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf) ve [WPF hata ayıklama](../../debugger/debugging-wpf.md) işlemlerini okuyabilirsiniz.

### <a name="find-and-fix-errors"></a>Hataları bulma ve düzeltme

Bu adımda, daha önce *MainWindow. xaml* dosyasının adını değiştirerek neden olduğumuz hatayı bulacaksınız.

#### <a name="start-debugging-and-find-the-error"></a>Hata ayıklamayı başlatma ve hatayı bulma

1. **F5** tuşuna basarak veya **Hata Ayıkla**' yı seçerek hata ayıklayıcıyı başlatın ve ardından **hata ayıklamayı başlatın**.

   **Kesme modu** penceresi görünür ve **Çıkış** penceresi bir IOException oluştuğunu belirtir: ' MainWindow. xaml ' kaynağı bulunamıyor.

   ![IOException iletisinin ekran görüntüsü](../media/exploreide-ioexception.png)

2. Hata ayıklamayı Durdur hata ayıklamayı **Durdur seçeneğini belirleyerek**durdurun  >  **Stop Debugging**.

Bu öğreticinin başlangıcında *MainWindow. xaml* ' i *Greetings. xaml* olarak yeniden adlandırdık, ancak kod yine de uygulama için başlangıç URI 'si olarak *MainWindow. xaml* 'e başvuruyor, bu nedenle proje başlatılamıyor.

#### <a name="specify-greetingsxaml-as-the-startup-uri"></a>Başlangıç URI 'SI olarak Greetings. xaml belirtin

1. **Çözüm Gezgini**, *Application. xaml* dosyasını açın.

2. `StartupUri="MainWindow.xaml"`Olarak değiştirin `StartupUri="Greetings.xaml"` ve değişiklikleri kaydedin.

Hata ayıklayıcıyı yeniden başlatın ( **F5**tuşuna basın). Uygulamanın **Greetings** penceresini görmeniz gerekir.

::: moniker range="vs-2017"
![Çalışan uygulamanın ekran görüntüsü](media/exploreide-wpf-running-app.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Çalışan uygulamanın ekran görüntüsü](media/vs-2019/exploreide-wpf-running-app.png)
::: moniker-end

 Hata ayıklamayı durdurmak için şimdi uygulama penceresini kapatın.

### <a name="debug-with-breakpoints"></a>Kesme noktalarıyla hata ayıkla

Hata ayıklama sırasında bazı kesme noktaları ekleyerek kodu test edebilirsiniz. Kesme **Debug**  >  **noktası geçiş noktasını**seçerek, kesmenin gerçekleşmesini istediğiniz kod satırının yanındaki düzenleyicinin sol kenar boşluğuna tıklayarak veya **F9**tuşuna basarak kesme noktaları ekleyebilirsiniz.

#### <a name="add-breakpoints"></a>Kesme noktası ekleme

1. *Greetings. xaml. vb*dosyasını açın ve aşağıdaki satırı seçin:`MessageBox.Show("Hello.")`

2. **Hata Ayıkla**' yı ve ardından **kesme noktası**' nı seçip menüden **F9** tuşuna basarak bir kesme noktası ekleyin.

   Düzenleyici penceresinin en sol kenar boşluğunda, kod satırının yanında kırmızı bir daire görünür.

3. Aşağıdaki satırı seçin: `MessageBox.Show("Goodbye.")` .

4. Bir kesme noktası eklemek için **F9** tuşuna basın ve sonra hata ayıklamayı başlatmak için **F5** 'e basın.

5. **Tebrikler** penceresinde, **Merhaba** radyo düğmesini seçin ve ardından **görüntüle** düğmesini seçin.

   Çizgi `MessageBox.Show("Hello.")` sarı renkle vurgulanır. IDE 'nin en altında, oto, Yereller ve Watch pencereleri, sol tarafa birlikte yerleştirilir ve çağrı yığını, kesme noktaları, özel durum ayarları, komut, anlık ve çıkış pencereleri sağ tarafta birlikte yerleştirilir.

   ![Hata ayıklayıcıda kesme noktası ekran görüntüsü](media/exploreide-debugbreakpoint.png)

6. Menü çubuğunda **Hata Ayıkla**  >  **Step Out**' ı seçin.

     Uygulama yürütmeyi sürdürür ve "Hello" sözcüğünü içeren bir ileti kutusu görünür.

7. İletiyi kapatmak için ileti kutusunda **Tamam** düğmesini seçin.

8. **Tebrikler** penceresinde, **güle** radyo düğmesini seçin ve ardından **görüntüle** düğmesini seçin.

     Çizgi `MessageBox.Show("Goodbye.")` sarı renkle vurgulanır.

9. Hata ayıklamaya devam etmek için **F5** tuşunu seçin. İleti kutusu göründüğünde kapatmak için ileti kutusunda **Tamam** düğmesini seçin.

10. Hata ayıklamayı durdurmak için uygulama penceresini kapatın.

11. Menü çubuğunda, **Hata Ayıkla**  >  **tüm kesme noktalarını devre dışı bırak**' ı seçin.

### <a name="view-a-representation-of-the-ui-elements"></a>UI öğelerinin gösterimini görüntüleme

Çalışan uygulamada, pencerenizin en üstünde görüntülenen bir pencere öğesi görmeniz gerekir. Bu, bazı yararlı hata ayıklama özelliklerine hızlı erişim sağlayan bir çalışma zamanı yardımcıdır. İlk düğmesine tıklayın, **canlı görsel ağaç**' a gidin. Sayfanızın tüm görsel öğelerini içeren bir ağacı olan bir pencere görmeniz gerekir. Eklediğiniz düğmeleri bulmak için düğümleri genişletin.

![Canlı görsel ağaç penceresinin ekran görüntüsü](media/vs-2019/exploreide-live-visual-tree.png)

### <a name="build-a-release-version-of-the-application"></a>Uygulamanın yayın sürümünü oluşturma

Her şeyin çalıştığından emin olduğunuza göre, uygulamanın yayın derlemesini hazırlayabilirsiniz.

1. Ana menüde, **Build**  >  önceki derlemeler sırasında oluşturulan ara dosyaları ve çıktı dosyalarını silmek için**temiz çözüm** oluştur ' u seçin. Bu gerekli değildir, ancak hata ayıklama oluşturma çıkışlarını temizler.

2. Araç çubuğundaki DropDown denetimini kullanarak HelloWPFApp için derleme yapılandırmasını **hata ayıklamadan** **Yayınla** değiştirin (Şu anda "hata ayıkla" ifadesini alır).

3. **Build**  >  **Build Solution**öğesini seçerek çözümü oluşturun.

Tebrikler, bu öğreticiyi tamamlama! Çözümünüz ve proje dizininiz (*. ..\Hellowpfapp\hellowpfapp\bin\release*) altında oluşturduğunuz *. exe dosyasını* bulabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

::: moniker range="vs-2017"

- [Visual Studio 2017’deki yenilikler](../../ide/whats-new-visual-studio-2017.md)
- [Üretkenlik ipuçları](../../ide/productivity-features.md)

::: moniker-end

::: moniker range="vs-2019"

- [Visual Studio 2019 ' deki yenilikler](../../ide/whats-new-visual-studio-2019.md)
- [Üretkenlik ipuçları](../../ide/productivity-features.md)

::: moniker-end