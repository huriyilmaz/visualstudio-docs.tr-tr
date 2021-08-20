---
title: Merhaba Dünya WPF ile uygulama Visual Basic
description: Windows Windows Presentation Foundation (WPF) UI çerçevesini kullanarak Visual Basic Visual Studio desktop .NET Windows Presentation Foundation basit bir uygulama oluşturun.
ms.custom: vs-acquisition, seodec18, get-started
ms.date: 04/23/2019
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
ms.topic: tutorial
dev_langs:
- VB
ms.assetid: f84339c7-d617-4f56-bfcd-af2215c347ba
author: anandmeg
ms.author: meghaanand
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 5d03f461a65e6fdb8bc11df6672b2c0069a2fc1a
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122157819"
---
# <a name="tutorial-create-a-simple-application-with-visual-basic"></a>Öğretici: Visual Basic ile basit bir uygulama oluşturma

Bu öğreticiyi tamamlayarak, bu öğreticiyle uygulama geliştirirken kullanabileceğiniz birçok araç, iletişim kutusu ve tasarımcı hakkında bilgi Visual Studio. Tümleşik geliştirme ortamında[(IDE)](visual-studio-ide.md)çalışma hakkında bilgi edinirken bir "Merhaba Dünya" uygulaması oluşturacak, kullanıcı arabirimini tasarlar, kod ekler ve hata ayıklarsınız.

::: moniker range="vs-2017"

Daha önce yüklememiş Visual Studio indirmeler [sayfasına Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) ücretsiz yükleyin.

::: moniker-end

::: moniker range="vs-2019"

Daha önce yüklememiş Visual Studio indirmeler [sayfasına Visual Studio](https://visualstudio.microsoft.com/downloads) ücretsiz yükleyin.

::: moniker-end

::: moniker range="vs-2022"

Visual Studio 2022 Preview'Visual Studio henüz yüklememişsinizdir, ücretsiz olarak yüklemek için [Visual Studio 2022 Preview](https://visualstudio.microsoft.com/vs/preview/vs2022) indirmeleri sayfasına gidin.

::: moniker-end

## <a name="configure-the-ide"></a>IDE'yi yapılandırma

::: moniker range="vs-2017"

İlk Visual Studio için oturum açmanız istenir. Bu adım bu öğretici için isteğe bağlıdır. Ardından, geliştirme ayarlarınızı ve renk temanızı seçmenizi isteyen bir iletişim kutusu gösterebilirsiniz. Varsayılan değerleri tut ve Başlat'ı **Visual Studio.**

![Ayarları seç iletişim kutusu](../media/exploreide-settings.png)

Bu Visual Studio sonra araç pencerelerini, menüleri ve araç çubuklarını ve ana pencere boşluklarını görebilirsiniz. Araç pencereleri, uygulama penceresinin sol ve sağ kenarlarında, **Hızlı Başlat,** menü çubuğu ve standart araç çubuğu en üstte yer alan bir şekilde yerleştirildi. Uygulama penceresinin merkezinde Başlangıç Sayfası **yer almaktadır.** Bir çözümü veya projeyi yükleyebilirsiniz. Düzenleyiciler ve tasarımcılar, Başlangıç Sayfasının bulunduğu **alanda** görünür. Bir uygulama geliştirirken, zaman çoğunu bu merkezi alanda geçireceksiniz.

![Visual Studio 2017 IDE genel Ayarlar Uygulandı](../media/exploreide-idewithgeneralsettings.png)

::: moniker-end

::: moniker range=">=vs-2019"

Uygulamayı Visual Studio önce başlangıç penceresi açılır. Geliştirme **ortamını açmak için Kod** olmadan devam'ı seçin. Araç pencerelerini, menüleri ve araç çubuklarını ve ana pencere boşluklarını görebilirsiniz. Araç pencereleri uygulama penceresinin sol ve sağ tarafına yerleştirildi. Arama kutusu, menü çubuğu ve standart araç çubuğu en üstte yer alan standart araç çubuğuyla birlikte. Bir çözümü veya projeyi yükleyemediniz mi, düzenleyiciler ve tasarımcılar uygulama penceresinin merkezi alanda görünür. Bir uygulama geliştirirken, zaman çoğunu bu merkezi alanda geçireceksiniz.

::: moniker-end

## <a name="create-the-project"></a>Proje oluşturma

Visual Studio'da bir uygulama oluştururken önce bir proje ve bir çözüm oluşturursunuz. Bu örnekte, bir Windows Presentation Foundation (WPF) projesi oluşturabilirsiniz.

::: moniker range="vs-2017"

1. Yeni bir proje oluşturma. Menü çubuğunda Dosya Yeni'yi **seçin**  >  **ve**  >  **Project.**

     ![Menü çubuğunda Dosya, Yeni ve Yeni'yi Project](../media/exploreide-filenewproject.png)

2. Yeni **Project** iletişim kutusunda Yüklü Visual Basic Windows Desktop kategorisini ve ardından WPF Uygulaması  >    >   **(.NET Framework) şablonunu** seçin. Projeye **HelloWPFApp adını girin ve** Tamam'ı **seçin.**

     ![Visual Studio New Project iletişim kutusunda WPF uygulama şablonu](media/exploreide-newproject-vb.png)

Visual Studio HelloWPFApp projesini ve çözümünü oluşturur **ve Çözüm Gezgini** dosyaları gösterir. **WPF Tasarımcısı,** bölünmüş görünümde *MainWindow.xaml'in* bir tasarım görünümünü ve XAML görünümünü gösterir. Görünümlerden birini daha fazla veya daha az göstermek için böleni kaydırabilirsiniz. Yalnızca görsel görünümünü veya yalnızca XAML görünümünü görüntülemeyi seçebilirsiniz. Aşağıdaki öğeler **Çözüm Gezgini:**

![Çözüm Gezgini HelloWPFApp dosyaları yüklü](../media/exploreide-hellowpfappfiles.png)

::: moniker-end

::: moniker range=">=vs-2019"

1. Visual Studio'yu açın.

2. Yeni proje **oluştur ekranında** "WPF" araması ve WPF Uygulaması **(.NET Framework)**'yi ve ardından Sonraki'yi **seçin.**

   ![Visual Studio New Project iletişim kutusunda WPF uygulama şablonu](media/vs-2019/exploreide-newprojectvb-vs2019.png)

3. Sonraki ekranda projeye **HelloWPFApp** adını girin ve Oluştur'a **tıklayın.**

Visual Studio HelloWPFApp projesini ve çözümünü oluşturur **ve Çözüm Gezgini** dosyaları gösterir. **WPF Tasarımcısı,** bölünmüş görünümde *MainWindow.xaml'in* bir tasarım görünümünü ve XAML görünümünü gösterir. Görünümlerden birini daha fazla veya daha az göstermek için böleni kaydırabilirsiniz. Yalnızca görsel görünümünü veya yalnızca XAML görünümünü görüntülemeyi seçebilirsiniz. Aşağıdaki öğeler **Çözüm Gezgini:**

![Çözüm Gezgini HelloWPFApp dosyaları yüklü](../media/vs-2019/exploreide-hellowpfappfiles.png)

::: moniker-end

> [!NOTE]
> XAML (eXtensible Uygulama Biçimlendirme Dili) hakkında daha fazla bilgi için [WPF için XAML'ye genel bakış sayfasına](/dotnet/framework/wpf/advanced/xaml-overview-wpf) bakın.

Projeyi oluşturduktan sonra özelleştirebilirsiniz. Özellikler penceresini **kullanarak** (Görünüm  menüsünde bulunur), bir uygulamadaki proje öğeleri, denetimler ve diğer öğeler için seçenekleri görüntüp değiştirebilirsiniz.

### <a name="change-the-name-of-mainwindowxaml"></a>MainWindow.xaml adını değiştirme

MainWindow'a daha belirli bir ad vealım. Bu **Çözüm Gezgini** *MainWindow.xaml'e sağ tıklayın ve* Yeniden Adlandır'ı **seçin.** Dosyayı *Greetings.xaml olarak yeniden adlandırır.*

## <a name="design-the-user-interface-ui"></a>Kullanıcı arabirimini (UI) tasarlama

Tasarımcı açık değilse, Çözüm Gezgini içinde *Greetings.xaml* öğesini **seçin** ve **Shift** + **F7** tuşuna basarak tasarımcıyı açın.

Bu uygulamaya üç tür denetim ekleyecek: <xref:System.Windows.Controls.TextBlock> denetim, iki <xref:System.Windows.Controls.RadioButton> denetim ve <xref:System.Windows.Controls.Button> denetim.

### <a name="add-a-textblock-control"></a>TextBlock denetimi ekleme

1. Arama **kutusunu etkinleştirmek için Ctrl** + **Q** tuşlarına basın ve Araç Kutusu **yazın.** Sonuçlar **listesinden > Araç Kutusu'nı** seçin.

2. Araç **Kutusunda,** Ortak **WPF Denetimleri düğümünü genişletarak** TextBlock denetimine bakın.

     ![TextBlock denetimi vurgulanmış araç kutusu](../media/exploreide-textblocktoolbox.png)

3. TextBlock öğesini seçerek ve tasarım yüzeyinde pencereye sürükleyerek tasarım yüzeyine bir **TextBlock** denetimi ekleyin. Denetimi pencerenin üst kısmında ortalar. 2019 Visual Studio sonraki bir yıl içinde kırmızı yönergeleri kullanarak denetimi ortalayabilirsiniz.

Pencereniz aşağıdaki gösterime benzemelidir:

![Greetings formunda TextBlock denetimi](../media/exploreide-greetingswithtextblockonly.png)

XAML işaretlemesi aşağıdaki örnekteki gibi gösterilsin:

```xaml
<TextBlock HorizontalAlignment="Left" Margin="381,100,0,0" TextWrapping="Wrap" Text="TextBlock" VerticalAlignment="Top"/>
```

### <a name="customize-the-text-in-the-text-block"></a>Metin bloğunda metni özelleştirme

1. XAML görünümünde TextBlock işaretlemesini bulun ve Text özniteliğini değiştirme:

   ```xaml
   Text="Select a message option and then choose the Display button."
   ```

2. Gerekirse TextBlock'un ortalarını yeniden alın ve Ctrl+S tuşlarına basarak veya Dosya menü **öğesini kullanarak değişikliklerinizi** kaydedin.

Ardından forma iki [RadioButton](/dotnet/framework/wpf/controls/radiobutton) denetimi eksersiniz.

### <a name="add-radio-buttons"></a>Radyo düğmesi ekleme

1. Araç **Kutusunda** **RadioButton denetimi** bulun.

     ![RadioButton denetimi seçili araç kutusu penceresi](../media/exploreide-radiobuttontoolbox.png)

2. **RadioButton** öğesini seçerek ve tasarım yüzeyindeki pencereye sürükleyerek tasarım yüzeyine iki RadioButton denetimi ekleyin. Düğmelerin TextBlock denetimi altında yan yana görünmesi için düğmeleri (seçerek ve ok tuşlarını kullanarak) hareket ettirin. Denetimleri hizalamak için kırmızı yönergeleri kullanın.

     Pencerenizin şuna benzemesi gerekir:

     ![TextBlock denetimi ve iki radyo düğmesi ile Greetings formu](../media/exploreide-greetingswithradiobuttons.png)

3. Sol  RadioButton denetimine ait Özellikler penceresinde **Name** özelliğini (Özellikler penceresinin en üstünde yer alan **özellik) olarak** `HelloButton` değiştirin.

     ![RadioButton özellikleri penceresi](../media/exploreide-buttonproperties.png)

4. Sağ  RadioButton denetimi için Özellikler penceresinde Name özelliğini olarak **değiştirin** ve `GoodbyeButton` ardından değişikliklerinizi kaydedin.

Artık her bir RadioButton denetimi için görüntü metni ekleyebilirsiniz. Aşağıdaki yordam, RadioButton denetimi için **Content** özelliğini günceller.

### <a name="add-display-text-for-each-radio-button"></a>Her radyo düğmesi için görüntüleme metni ekleme

XAML'de ve için **Content** `HelloButton` `GoodbyeButton` `"Hello"` `"Goodbye"` özniteliğini güncelleştirin. XAML işaretlemesi artık aşağıdaki örnekteki gibi görünüyor olabilir:

   ```xaml
   <Grid>
        <TextBlock HorizontalAlignment="Left" Margin="252,47,0,0" TextWrapping="Wrap" Text="Select a message option and then choose the Display button." VerticalAlignment="Top"/>
        <RadioButton x:Name="HelloButton" Content="Hello" HorizontalAlignment="Left" Margin="297,161,0,0" VerticalAlignment="Top"/>
        <RadioButton x:Name="GoodbyeButton" Content="Goodbye" HorizontalAlignment="Left" Margin="488,161,0,0" VerticalAlignment="Top"/>
   </Grid>
   ```

### <a name="set-a-radio-button-to-be-checked-by-default"></a>Radyo düğmesini varsayılan olarak denetlenir olarak ayarlayın

Bu adımda, iki radyo düğmesiden birinin her zaman seçili olması için HelloButton'ın varsayılan olarak denetlenmesi için ayarlayıyoruz.

XAML görünümünde HelloButton işaretlemesi bulun ve bir **IsChecked özniteliği** ekleyin:

```xaml
IsChecked="True"
```

Ekley istediğiniz son kullanıcı arabirimi öğesi düğme [denetimidir.](/dotnet/framework/wpf/controls/button)

### <a name="add-the-button-control"></a>Düğme denetimi ekleme

1. Araç **Kutusunda Düğme** **denetimi'ne** tıklayın ve ardından tasarım görünümünde forma sürükleyerek RadioButton denetimlerinin altındaki tasarım yüzeyine ekleyin. Visual Studio 2019 veya sonraki bir 2019 veya sonraki bir 2019 kullanıyorsanız kırmızı çizgi denetimi ortalar.

2. XAML görünümünde, Düğme denetimi **için İçerik** değerini olarak olarak `Content="Button"` `Content="Display"` değiştirerek değişiklikleri kaydedin.

     Biçimlendirme aşağıdaki örneğe benzemelidir:   `<Button Content="Display" HorizontalAlignment="Left" VerticalAlignment="Top" Width="75" Margin="215,204,0,0"/>`

     Pencereniz aşağıdaki gösterime benzemelidir.

     ![Denetim etiketleriyle Greetings formu](../media/exploreide-greetingswithcontrollabels.png)

### <a name="add-code-to-the-display-button"></a>Görüntü düğmesine kod ekleme

Bu uygulama çalıştığında, bir Kullanıcı radyo düğmesini seçtikten sonra **görüntüle** düğmesini seçtiğinde bir ileti kutusu görünür. Merhaba için bir ileti kutusu ve Güle Güle için bir diğer ileti kutusu görünecektir. Bu davranışı oluşturmak için `Button_Click` *Greetings. xaml. vb* veya *Greetings. xaml. cs* içindeki olaya kod ekleyeceksiniz.

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

2. Hata ayıklamayı Durdur hata ayıklamayı **Durdur seçeneğini belirleyerek** durdurun  >  .

Bu öğreticinin başlangıcında *MainWindow. xaml* ' i *Greetings. xaml* olarak yeniden adlandırdık, ancak kod yine de uygulama için başlangıç URI 'si olarak *MainWindow. xaml* 'e başvuruyor, bu nedenle proje başlatılamıyor.

#### <a name="specify-greetingsxaml-as-the-startup-uri"></a>Başlangıç URI 'SI olarak Greetings. xaml belirtin

1. **Çözüm Gezgini**, *Application. xaml* dosyasını açın.

2. `StartupUri="MainWindow.xaml"`Olarak değiştirin `StartupUri="Greetings.xaml"` ve değişiklikleri kaydedin.

Hata ayıklayıcıyı yeniden başlatın ( **F5** tuşuna basın). Uygulamanın **Greetings** penceresini görmeniz gerekir.

::: moniker range="vs-2017"
![Çalışan uygulamanın ekran görüntüsü](media/exploreide-wpf-running-app.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Çalışan uygulamanın ekran görüntüsü](media/vs-2019/exploreide-wpf-running-app.png)
::: moniker-end

 Hata ayıklamayı durdurmak için şimdi uygulama penceresini kapatın.

### <a name="debug-with-breakpoints&quot;></a>Kesme noktalarıyla hata ayıkla

Hata ayıklama sırasında bazı kesme noktaları ekleyerek kodu test edebilirsiniz. Kesme   >  **noktası geçiş noktasını** seçerek, kesmenin gerçekleşmesini istediğiniz kod satırının yanındaki düzenleyicinin sol kenar boşluğuna tıklayarak veya **F9** tuşuna basarak kesme noktaları ekleyebilirsiniz.

#### <a name=&quot;add-breakpoints&quot;></a>Kesme noktası ekleme

1. *Greetings. xaml. vb* dosyasını açın ve aşağıdaki satırı seçin:`MessageBox.Show(&quot;Hello.")`

2. **Hata Ayıkla**' yı ve ardından **kesme noktası**' nı seçip menüden **F9** tuşuna basarak bir kesme noktası ekleyin.

   Düzenleyici penceresinin en sol kenar boşluğunda, kod satırının yanında kırmızı bir daire görünür.

3. Aşağıdaki satırı seçin: `MessageBox.Show("Goodbye.")` .

4. Bir kesme noktası eklemek için **F9** tuşuna basın ve sonra hata ayıklamayı başlatmak için **F5** 'e basın.

5. **Tebrikler** penceresinde, **Merhaba** radyo düğmesini seçin ve ardından **görüntüle** düğmesini seçin.

   Çizgi `MessageBox.Show("Hello.")` sarı renkle vurgulanır. ıde 'nin en altında, oto, yereller ve Watch pencereleri, sol tarafa birlikte yerleştirilir ve çağrı yığını, kesme noktaları, özel durum Ayarlar, komut, anlık ve çıkış pencereleri sağ tarafta bir araya yerleştirildi.

   ![Hata ayıklayıcıda kesme noktası ekran görüntüsü](media/exploreide-debugbreakpoint.png)

6. Menü çubuğunda **Hata Ayıkla**  >  **Step Out**' ı seçin.

     Uygulama yürütmeyi sürdürür ve "Hello&quot; sözcüğünü içeren bir ileti kutusu görünür.

7. İletiyi kapatmak için ileti kutusunda **Tamam** düğmesini seçin.

8. **Tebrikler** penceresinde, **güle** radyo düğmesini seçin ve ardından **görüntüle** düğmesini seçin.

     Çizgi `MessageBox.Show(&quot;Goodbye.")` sarı renkle vurgulanır.

9. Hata ayıklamaya devam etmek için **F5** tuşunu seçin. İleti kutusu göründüğünde kapatmak için ileti kutusunda **Tamam** düğmesini seçin.

10. Hata ayıklamayı durdurmak için uygulama penceresini kapatın.

11. Menü çubuğunda, **Hata Ayıkla**  >  **tüm kesme noktalarını devre dışı bırak**' ı seçin.

### <a name="view-a-representation-of-the-ui-elements"></a>UI öğelerinin gösterimini görüntüleme

Çalışan uygulamada, pencerenizin en üstünde görüntülenen bir pencere öğesi görmeniz gerekir. Bu, bazı yararlı hata ayıklama özelliklerine hızlı erişim sağlayan bir çalışma zamanı yardımcıdır. İlk düğmesine tıklayın, **canlı görsel ağaç**' a gidin. Sayfanızın tüm görsel öğelerini içeren bir ağacı olan bir pencere görmeniz gerekir. Eklediğiniz düğmeleri bulmak için düğümleri genişletin.

![Canlı görsel ağaç penceresinin ekran görüntüsü](media/vs-2019/exploreide-live-visual-tree.png)

### <a name="build-a-release-version-of-the-application"></a>Uygulamanın yayın sürümünü oluşturma

Her şeyin çalıştığından emin olduğunuza göre, uygulamanın yayın derlemesini hazırlayabilirsiniz.

1. Ana menüde,   >  önceki derlemeler sırasında oluşturulan ara dosyaları ve çıktı dosyalarını silmek için **temiz çözüm** oluştur ' u seçin. Bu gerekli değildir, ancak hata ayıklama oluşturma çıkışlarını temizler.

2. Araç çubuğundaki DropDown denetimini kullanarak HelloWPFApp için derleme yapılandırmasını **hata ayıklamadan** **Yayınla** değiştirin (Şu anda "hata ayıkla" ifadesini alır).

3. **Build**  >  **Build Solution** öğesini seçerek çözümü oluşturun.

Tebrikler, bu öğreticiyi tamamlama! Çözümünüz ve proje dizininiz (*. ..\Hellowpfapp\hellowpfapp\bin\release*) altında oluşturduğunuz *.exe* bulabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

::: moniker range="vs-2017"

- [Visual Studio 2017’deki yenilikler](../../ide/whats-new-visual-studio-2017.md)
- [Üretkenlik ipuçları](../../ide/productivity-features.md)

::: moniker-end

::: moniker range="vs-2019"

- [Visual Studio 2019 ' deki yenilikler](../../ide/whats-new-visual-studio-2019.md)
- [Üretkenlik ipuçları](../../ide/productivity-features.md)

::: moniker-end

::: moniker range="vs-2022"

- [Üretkenlik ipuçları](../../ide/productivity-features.md)

::: moniker-end
