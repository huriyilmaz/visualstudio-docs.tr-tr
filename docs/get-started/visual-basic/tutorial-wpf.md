---
title: Merhaba Dünya WPF ile uygulama Visual Basic
description: Windows Visual Basic (WPF) kullanıcı arabirimi çerçevesini Visual Studio basit bir Windows Presentation Foundation Desktop .NET uygulaması oluşturun.
ms.custom: vs-acquisition, seodec18, get-started
ms.date: 09/14/2021
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
ms.openlocfilehash: b33078255f2a85bc9067e3c9b7a8b4e0412b8fe6
ms.sourcegitcommit: 59613afd06a8f184efab8e108410066824a2b712
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/18/2021
ms.locfileid: "127920353"
---
# <a name="tutorial-create-a-simple-application-with-visual-basic"></a>Öğretici: Visual Basic ile basit bir uygulama oluşturma

Bu öğreticiyi tamamlayarak, bu öğreticiyle uygulama geliştirirken kullanabileceğiniz birçok araç, iletişim kutusu ve tasarımcı hakkında bilgi Visual Studio. Tümleşik geliştirme ortamında ([IDE)](visual-studio-ide.md)çalışma hakkında bilgi edinirken bir "Merhaba Dünya" uygulaması oluşturacak, kullanıcı arabirimini tasarlar, kod ekler ve hata ayıklarsınız.

::: moniker range="vs-2017"

Daha önce yüklememiş Visual Studio indirmeler [sayfasına Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) ücretsiz olarak yükleyin.

::: moniker-end

::: moniker range=">=vs-2019"

Daha önce yüklememiş Visual Studio indirmeler [sayfasına Visual Studio](https://visualstudio.microsoft.com/downloads) ücretsiz olarak yükleyin.

::: moniker-end

## <a name="configure-the-ide"></a>IDE'yi yapılandırma

::: moniker range="vs-2017"

İlk Visual Studio için oturum açmanız istenir. Bu adım bu öğretici için isteğe bağlıdır. Ardından, geliştirme ayarlarınızı ve renk temanızı seçmenizi isteyen bir iletişim kutusu gösterebilirsiniz. Varsayılan değerleri tut ve Başlat'ı **Visual Studio.**

![Ayarları seç iletişim kutusu](../media/exploreide-settings.png)

Bu Visual Studio sonra araç pencerelerini, menüleri ve araç çubuklarını ve ana pencere boşluklarını görebilirsiniz. Araç pencereleri, uygulama penceresinin sol ve sağ kenarlarında, **Hızlı Başlat,** menü çubuğu ve standart araç çubuğu en üstte yer alan bir şekilde yerleştirildi. Uygulama penceresinin merkezinde Başlangıç Sayfası **yer almaktadır.** Bir çözümü veya projeyi yükleyebilirsiniz. Düzenleyiciler ve tasarımcılar, Başlangıç Sayfasının bulunduğu **alanda** görünür. Bir uygulama geliştirirken, zaman çoğunu bu merkezi alanda geçireceksiniz.

![Visual Studio 2017 IDE genel Ayarlar Uygulandı](../media/exploreide-idewithgeneralsettings.png)

::: moniker-end

::: moniker range=">=vs-2019"

Uygulamayı Visual Studio önce başlangıç penceresi açılır. Geliştirme **ortamını açmak için Kod** olmadan devam'ı seçin. Araç pencerelerini, menüleri ve araç çubuklarını ve ana pencere boşluklarını görebilirsiniz. Araç pencereleri, uygulama penceresinin sol ve sağ tarafına yerleştirildi. Arama kutusu, menü çubuğu ve standart araç çubuğu en üstte bulunur. Bir çözümü veya projeyi yükleyemediniz mi, düzenleyiciler ve tasarımcılar uygulama penceresinin merkezi alanda görünür. Bir uygulama geliştirirken, zaman çoğunu bu merkezi alanda geçireceksiniz.

::: moniker-end

## <a name="create-the-project"></a>Proje oluşturma

Visual Studio'da bir uygulama oluştururken önce bir proje ve bir çözüm oluşturursunuz. Bu örnekte, bir Windows Presentation Foundation (WPF) projesi oluşturabilirsiniz.

::: moniker range="vs-2017"

1. Yeni bir proje oluşturma. Menü çubuğunda Dosya **Yeni'yi seçin**  >  **ve**  >  **Project.**

     ![Menü çubuğunda Dosya, Yeni ve Yeni'yi Project](../media/exploreide-filenewproject.png)

1. Yeni **Project** iletişim kutusunda Yüklü Visual Basic Windows Desktop kategorisini ve ardından WPF Uygulaması  >    >   **(.NET Framework) şablonunu** seçin. Projeye **HelloWPFApp adını girin ve** Tamam'ı **seçin.**

     ![Yeni uygulama iletişim kutusundaki Visual Studio WPF Project şablonu](media/exploreide-newproject-vb.png)

Visual Studio HelloWPFApp projesini ve çözümünü oluşturur **ve Çözüm Gezgini** dosyaları gösterir. **WPF Tasarımcısı,** bölünmüş görünümde *MainWindow.xaml'in* bir tasarım görünümünü ve XAML görünümünü gösterir. Görünümlerden birini daha fazla veya daha az göstermek için böleni kaydırabilirsiniz. Yalnızca görsel görünümünü veya yalnızca XAML görünümünü görüntülemeyi seçebilirsiniz. Aşağıdaki öğeler **Çözüm Gezgini:**

![Çözüm Gezgini HelloWPFApp dosyaları yüklü](../media/exploreide-hellowpfappfiles.png)

::: moniker-end

::: moniker range="vs-2019"

1. Visual Studio'yu açın.

1. Yeni proje **oluştur ekranında** "WPF" araması ve WPF Uygulaması **(.NET Framework)** ve ardından Sonraki'yi **seçin.**

   ![Arama kutusuna 'WPF' girildi ve 'WPF Uygulaması (.NET Framework)' proje şablonunun seçili olduğu 'Yeni proje oluştur' iletişim kutusunun ekran görüntüsü.](media/vs-2019/exploreide-newprojectvb-vs2019.png)

1. Sonraki ekranda projeye **HelloWPFApp** adını girin ve Oluştur'a **tıklayın.**

Visual Studio HelloWPFApp projesini ve çözümünü oluşturur **ve Çözüm Gezgini** dosyaları gösterir. **WPF Tasarımcısı,** bölünmüş görünümde *MainWindow.xaml'in* bir tasarım görünümünü ve XAML görünümünü gösterir. Görünümlerden birini daha fazla veya daha az göstermek için böleni kaydırabilirsiniz. Yalnızca görsel görünümünü veya yalnızca XAML görünümünü görüntülemeyi seçebilirsiniz. Aşağıdaki öğeler **Çözüm Gezgini:**

![Uygulamanın HelloWPFApp projesinde ve çözümünde yer alan dosyaları gösteren Çözüm Gezgini.](../media/vs-2019/exploreide-hellowpfappfiles.png)

::: moniker-end

::: moniker range=">=vs-2022"

1. Visual Studio'yu açın.
 
1. Başlangıç penceresinde Yeni proje **oluştur'a tıklayın.**

   :::image type="content" source="media/vs-2022/start-window-create-new-project.png" alt-text="'Yeni proje oluştur' Visual Studio 2022'de başlangıç penceresinin ekran görüntüsü.":::

1. Yeni **proje oluştur ekranında** "WPF" araması Visual Basic  Tüm diller **açılan** listesinden Yenile'yi seçin. **WPF Uygulaması (.NET Framework) ve** ardından Sonraki'yi **seçin.**

   :::image type="content" source="media/vs-2022/explore-ide-new-wpf-app-project-vb.png" alt-text="Arama kutusuna 'WPF' girildi, diller listesinde 'Visual Basic' seçildi ve 'WPF Uygulaması (.NET Framework)' proje şablonu vurgulanmış 'Yeni proje oluştur' iletişim kutusunun ekran görüntüsü.":::

1. Sonraki ekranda projeye **HelloWPFApp** adını girin ve Oluştur'a **tıklayın.**

Visual Studio HelloWPFApp projesini ve çözümünü oluşturur **ve Çözüm Gezgini** dosyaları gösterir. **WPF Tasarımcısı,** bölünmüş görünümde *MainWindow.xaml'in* bir tasarım görünümünü ve XAML görünümünü gösterir. Görünümlerden birini daha fazla veya daha az göstermek için böleni kaydırabilirsiniz. Yalnızca görsel görünümünü veya yalnızca XAML görünümünü görüntülemeyi seçebilirsiniz. Aşağıdaki öğeler **Çözüm Gezgini:**

:::image type="content" source="media/vs-2022/explore-ide-hello-wpf-app-files.png" alt-text="Uygulamanın HelloWPFApp projesinde ve çözümünde yer alan dosyaları gösteren Çözüm Gezgini.":::

::: moniker-end

> [!NOTE]
> XAML (eXtensible Uygulama Biçimlendirme Dili) hakkında daha fazla bilgi için [WPF için XAML'ye genel bakış sayfasına](/dotnet/framework/wpf/advanced/xaml-overview-wpf) bakın.

Projeyi oluşturduktan sonra özelleştirebilirsiniz. Özellikler penceresini **kullanarak** (Görünüm  menüsünde bulunur), bir uygulamadaki proje öğeleri, denetimler ve diğer öğeler için seçenekleri görüntüp değiştirebilirsiniz.

### <a name="change-the-name-of-mainwindowxaml"></a>MainWindow.xaml adını değiştirme

MainWindow'a daha belirli bir ad vealım. Bu **Çözüm Gezgini** *MainWindow.xaml'e sağ tıklayın* ve Yeniden Adlandır'ı **seçin.** Dosyayı *Greetings.xaml olarak yeniden adlandırır.*

İsteğe bağlı bir adım olarak, uygulama pencerenizin başlığını bu yeni adla eş değiştirecek şekilde değiştirmek karışıklığı önlemektedir.

1. Bu **Çözüm Gezgini,** yeni yeniden *adlandırdınız Greetings.xaml* dosyasını açın.

1. XAML  **görünümünde, Window.Title** özelliğinin değerini olarak olarak `Title="MainWindow"` `Title="Greetings"` değiştirerek değişiklikleri kaydedin.

## <a name="design-the-user-interface-ui"></a>Kullanıcı arabirimini (UI) tasarlama

Tasarımcı açık yoksa, Çözüm Gezgini içinde *Greetings.xaml* öğesini **seçin** ve **Shift** + **F7** tuşuna basarak tasarımcıyı açın.

Bu uygulamaya üç tür denetim ekleyecek: <xref:System.Windows.Controls.TextBlock> denetim, iki <xref:System.Windows.Controls.RadioButton> denetim ve <xref:System.Windows.Controls.Button> denetim.

### <a name="add-a-textblock-control"></a>TextBlock denetimi ekleme

::: moniker range="vs-2019"

1. Arama **kutusunu etkinleştirmek için Ctrl** + **Q** tuşlarına basın ve Araç Kutusu **yazın.** Sonuçlar **listesinden > Araç Kutusu'nı** seçin.

1. Araç **Kutusunda,** Ortak **WPF Denetimleri düğümünü genişletarak** TextBlock denetimine bakın.

   ![Ortak WPF Denetimleri listesinde TextBlock denetimi vurgulanmış Araç Kutusu penceresini gösteren ekran görüntüsü.](../media/exploreide-textblocktoolbox.png)

1. TextBlock öğesini seçerek ve tasarım yüzeyinde pencereye sürükleyerek tasarım yüzeyine bir **TextBlock** denetimi ekleyin. Denetimi pencerenin üst kısmında ortalar. 2019 Visual Studio sonraki bir yıl içinde kırmızı yönergeleri kullanarak denetimi ortalayabilirsiniz.

Pencereniz aşağıdaki gösterime benzemelidir:

![Greetings formunda yer alan TextBlock denetimlerini gösteren ekran görüntüsü.](../media/exploreide-greetingswithtextblockonly.png)

XAML işaretlemesi aşağıdaki örnekteki gibi gösterilsin:

```xaml
<TextBlock HorizontalAlignment="Left" Margin="381,100,0,0" TextWrapping="Wrap" Text="TextBlock" VerticalAlignment="Top"/>
```

::: moniker-end

::: moniker range=">=vs-2022"

1. Arama **kutusunu etkinleştirmek için Ctrl** + **Q** tuşlarına basın ve Araç Kutusu **yazın.** Sonuçlar **listesinden > Araç Kutusu'nı** seçin.

1. Araç **Kutusunda,** Ortak **WPF Denetimleri düğümünü genişletarak** TextBlock denetimine bakın.

   :::image type="content" source="media/vs-2022/explore-ide-textblock-toolbox.png" alt-text="Ortak WPF Denetimleri listesinde TextBlock denetimi vurgulanmış Araç Kutusu penceresini gösteren ekran görüntüsü.":::

1. TextBlock öğesini seçerek ve tasarım yüzeyinde pencereye sürükleyerek tasarım yüzeyine bir **TextBlock** denetimi ekleyin. Denetimi pencerenin üst kısmında ortalar. Denetimi merkezi yapmak için yönergeleri kullanabilirsiniz.

Pencereniz aşağıdaki görüntüye benzer:

:::image type="content" source="media/vs-2022/explore-ide-greetings-with-textblock-only.png" alt-text="Yönergelerin görünür olduğu Greetings formunda yer alan TextBlock denetimlerini gösteren ekran görüntüsü.":::

XAML işaretlemesi aşağıdaki örnekteki gibi gösterilsin:

```xaml
<TextBlock HorizontalAlignment="Left" Margin="381,100,0,0" TextWrapping="Wrap" Text="TextBlock" VerticalAlignment="Top"/>
```

::: moniker-end

### <a name="customize-the-text-in-the-text-block"></a>Metin bloğunda metni özelleştirme

1. XAML görünümünde TextBlock işaretlemesini bulun ve Text özniteliğini değiştirme:

   ```xaml
   Text="Select a message option and then choose the Display button."
   ```

1. Gerekirse TextBlock 'ı yeniden ortalayın ve CTRL + S tuşlarına basarak veya **Dosya** menü öğesini kullanarak yaptığınız değişiklikleri kaydedin.

Ardından, forma iki [RadioButton](/dotnet/framework/wpf/controls/radiobutton) denetimi ekleyeceksiniz.

### <a name="add-radio-buttons"></a>Radyo düğmesi ekleme

::: moniker range="vs-2019"

1. **Araç kutusunda** **RadioButton** denetimini bulun.

     ![Ortak WPF denetimleri listesinde seçilmiş RadioButton denetimiyle araç kutusu penceresini gösteren ekran görüntüsü.](../media/exploreide-radiobuttontoolbox.png)

1. **RadioButton** öğesini seçerek ve tasarım yüzeyinde pencereye sürükleyerek tasarım yüzeyine iki RadioButton denetimi ekleyin. Düğmeleri TextBlock denetimi altında yan yana görünecek şekilde düğmeleri (onları seçerek ve ok tuşlarını kullanarak) taşıyın. Denetimleri hizalamak için kırmızı yönergeleri kullanın.

     Pencerenizin şuna benzemesi gerekir:

     ![Bir TextBlock denetimi ve iki radyo düğmesi ile Greetings formunu gösteren ekran görüntüsü.](../media/exploreide-greetingswithradiobuttons.png)

1. Sol RadioButton denetimi için **Özellikler** penceresinde, **ad** özelliğini ( **Özellikler** penceresinin üst kısmındaki özellik) olarak değiştirin `HelloButton` .

     ![' HelloButton ' RadioButton için Çözüm Gezgini Özellikler penceresi gösteren ekran görüntüsü.](../media/exploreide-buttonproperties.png)

1. Sağ RadioButton denetimi için **Özellikler** penceresinde, **ad** özelliğini olarak değiştirin `GoodbyeButton` ve ardından değişikliklerinizi kaydedin.

Artık her bir RadioButton denetimi için görüntü metni ekleyebilirsiniz. Aşağıdaki yordam bir RadioButton denetimi için **içerik** özelliğini güncelleştirir.

::: moniker-end

::: moniker range=">=vs-2022"

1. **Araç kutusunda** **RadioButton** denetimini bulun.

     :::image type="content" source="media/vs-2022/explore-ide-radiobutton-toolbox.png" alt-text="Ortak WPF denetimleri listesinde seçilmiş RadioButton denetimiyle araç kutusu penceresini gösteren ekran görüntüsü.":::

1. **RadioButton** öğesini seçerek ve tasarım yüzeyinde pencereye sürükleyerek tasarım yüzeyine iki RadioButton denetimi ekleyin. Düğmeleri TextBlock denetimi altında yan yana görünecek şekilde düğmeleri (onları seçerek ve ok tuşlarını kullanarak) taşıyın. Denetimleri hizalamak için yönergeleri kullanın.

     Pencerenizin şuna benzemesi gerekir:

     :::image type="content" source="media/vs-2022/explore-ide-greetings-with-radiobuttons.png" alt-text="Bir TextBlock denetimi ve iki radyo düğmesi ile Greetings formunu gösteren ekran görüntüsü.":::

1. Sol RadioButton denetimi için **Özellikler** penceresinde, **ad** özelliğini ( **Özellikler** penceresinin üst kısmındaki özellik) olarak değiştirin `HelloButton` .

     :::image type="content" source="media/vs-2022/explore-ide-button-properties.png" alt-text="' HelloButton ' RadioButton için Çözüm Gezgini Özellikler penceresi gösteren ekran görüntüsü.":::

1. Sağ RadioButton denetimi için **Özellikler** penceresinde, **ad** özelliğini olarak değiştirin `GoodbyeButton` ve ardından değişikliklerinizi kaydedin.

Artık her bir RadioButton denetimi için görüntü metni ekleyebilirsiniz. Aşağıdaki yordam bir RadioButton denetimi için **içerik** özelliğini güncelleştirir.

::: moniker-end
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

::: moniker range="vs-2019"

1. **Araç kutusunda** **düğme** denetimini bulun ve ardından Tasarım görünümündeki forma sürükleyerek RadioButton denetimlerinin altındaki tasarım yüzeyine ekleyin. Yönergeler, denetimi ortaetmenize yardımcı olabilir.

1. XAML görünümünde düğme denetimi için **içerik** değerini `Content="Button"` olarak değiştirin `Content="Display"` ve ardından değişiklikleri kaydedin.

   Biçimlendirme aşağıdaki örneğe benzemelidir:  `<Button Content="Display" HorizontalAlignment="Left" VerticalAlignment="Top" Width="75" Margin="215,204,0,0"/>`

   Pencereniz aşağıdaki gösterime benzemelidir.

   ![TextBlock ile Greetings formunu gösteren ekran görüntüsü, ' Merhaba ' ve ' güle ' etiketli RadioButtons ve ' Display ' etiketini içeren düğme denetimi, formda konumlandırılmış.](../media/exploreide-greetingswithcontrollabels.png)

::: moniker-end

::: moniker range=">=vs-2022"

1. **Araç kutusunda** **düğme** denetimini bulun ve ardından Tasarım görünümündeki forma sürükleyerek RadioButton denetimlerinin altındaki tasarım yüzeyine ekleyin. Yönergeler, denetimi ortaetmenize yardımcı olabilir.

1. XAML görünümünde düğme denetimi için **içerik** değerini `Content="Button"` olarak değiştirin `Content="Display"` ve ardından değişiklikleri kaydedin.

   Biçimlendirme aşağıdaki örneğe benzemelidir:

   ```xaml
   <Button Content="Display" HorizontalAlignment="Left" VerticalAlignment="Top" Width="75" Margin="215,204,0,0"/>
   ```

   Pencereniz aşağıdaki görüntüye benzemelidir.

   :::image type="content" source="media/vs-2022/explore-ide-greetings-with-control-labels.png" alt-text="TextBlock ile Greetings formunu gösteren ekran görüntüsü, ' Merhaba ' ve ' güle ' etiketli RadioButtons ve ' Display ' etiketini içeren düğme denetimi, formda konumlandırılmış.":::

::: moniker-end
### <a name="add-code-to-the-display-button"></a>Görüntü düğmesine kod ekleme

Bu uygulama çalıştığında, bir Kullanıcı radyo düğmesini seçtikten sonra **görüntüle** düğmesini seçtiğinde bir ileti kutusu görünür. Merhaba için bir ileti kutusu ve Güle Güle için bir diğer ileti kutusu görünecektir. Bu davranışı oluşturmak için `Button_Click` *Greetings. xaml. vb* veya *Greetings. xaml. cs* içindeki olaya kod ekleyeceksiniz.

1. Tasarım yüzeyinde **görüntüle** düğmesine çift tıklayın.

     *Greetings. xaml. vb* , olayında imleç ile açılır `Button_Click` .

    ```vb
    Private Sub Button_Click(sender As Object, e As RoutedEventArgs)

    End Sub
    ```

1. Aşağıdaki kodu girin:

    ```vb
    If HelloButton.IsChecked = True Then
        MessageBox.Show("Hello.")
    ElseIf GoodbyeButton.IsChecked = True Then
        MessageBox.Show("Goodbye.")
    End If
    ```

1. Uygulamayı kaydedin.

## <a name="debug-and-test-the-application"></a>Uygulamanın hatalarını ayıklama ve test etme

Sonra, hataları bulmak ve her iki ileti kutusunun doğru şekilde göründüğünü sınamak için uygulamada hata ayıklaması yapacaksınız. Aşağıdaki yönergelerde hata ayıklayıcıyı nasıl derleyip başlatacağınız, ancak daha sonra daha fazla bilgi için WPF [uygulaması (WPF) oluşturma](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf) ve [WPF hata ayıklama](../../debugger/debugging-wpf.md) işlemlerini okuyabilirsiniz.

### <a name="find-and-fix-errors"></a>Hataları bulma ve düzeltme

Bu adımda, daha önce *MainWindow. xaml* dosyasının adını değiştirerek neden olduğumuz hatayı bulacaksınız.

#### <a name="start-debugging-and-find-the-error"></a>Hata ayıklamayı başlatma ve hatayı bulma

::: moniker range="vs-2019"

1. **F5** tuşuna basarak veya **Hata Ayıkla**' yı seçerek hata ayıklayıcıyı başlatın ve ardından **hata ayıklamayı başlatın**.

   **Kesme modu** penceresi görünür ve **Çıkış** penceresi bir IOException oluştuğunu belirtir: ' MainWindow. xaml ' kaynağı bulunamıyor.

   ![' Özel durum Işlenmemiş ' penceresini, ' ' MainWindow. xaml bulunamıyor ' kaynağını okuyan bir System. ıO. Exception iletisi ile gösteren ekran görüntüsü.](../media/exploreide-ioexception.png)

1. Hata ayıklamayı Durdur hata ayıklamayı **Durdur seçeneğini belirleyerek** durdurun > .

Bu öğreticinin başlangıcında *MainWindow. xaml* ' i *Greetings. xaml* olarak yeniden adlandırdık, ancak kod yine de uygulama için başlangıç URI 'si olarak *MainWindow. xaml* 'e başvuruyor, bu nedenle proje başlatılamıyor.

::: moniker-end

::: moniker range=">=vs-2022"

1. **F5** tuşuna basarak veya **Hata Ayıkla**' yı seçerek hata ayıklayıcıyı başlatın ve ardından **hata ayıklamayı başlatın**.

   **Kesme modu** penceresi görünür ve **Çıkış** penceresi bir IOException oluştuğunu belirtir: ' MainWindow. xaml ' kaynağı bulunamıyor.

   :::image type="content" source="media/vs-2022/explore-ide-ioexception.png" alt-text="' Özel durum Işlenmemiş ' penceresini, ' ' MainWindow. xaml bulunamıyor ' kaynağını okuyan bir System. ıO. Exception iletisi ile gösteren ekran görüntüsü.":::

1. Hata ayıklamayı Durdur hata ayıklamayı **Durdur seçeneğini belirleyerek** durdurun > .

Bu öğreticinin başlangıcında *MainWindow. xaml* ' i *Greetings. xaml* olarak yeniden adlandırdık, ancak kod yine de uygulama için başlangıç URI 'si olarak *MainWindow. xaml* 'e başvuruyor, bu nedenle proje başlatılamıyor.

::: moniker-end

#### <a name="specify-greetingsxaml-as-the-startup-uri"></a>Başlangıç URI 'SI olarak Greetings. xaml belirtin

1. **Çözüm Gezgini**, *Application. xaml* dosyasını açın.

1. `StartupUri="MainWindow.xaml"`Olarak değiştirin `StartupUri="Greetings.xaml"` ve değişiklikleri kaydedin.

Hata ayıklayıcıyı yeniden başlatın ( **F5** tuşuna basın). Artık uygulamanızın **Greetings** penceresini görmeniz gerekir.

::: moniker range="vs-2017"

![Çalışan uygulamanın ekran görüntüsü](media/exploreide-wpf-running-app.png "TextBlock, RadioButtons ve Button denetimlerinin görünür olduğu Greetings penceresinin ekran görüntüsü. 'Hello' radyo düğmesi seçilidir.")

::: moniker-end

::: moniker range="vs-2019"

![Çalışan uygulamanın ekran görüntüsü](media/vs-2019/exploreide-wpf-running-app.png "TextBlock, RadioButtons ve Button denetimlerinin görünür olduğu Greetings penceresinin ekran görüntüsü. 'Hello' radyo düğmesi seçilidir.")

::: moniker-end

::: moniker range=">=vs-2022"

:::image type="content" source="media/vs-2022/explore-ide-wpf-running-app.png" alt-text="TextBlock, RadioButtons ve düğme denetimlerinin görünür olduğu Greetings penceresinin ekran görüntüsü. ' Merhaba ' radyo düğmesi seçildi.":::

::: moniker-end

Hata ayıklamayı durdurmak için şimdi uygulama penceresini kapatın.

### <a name="debug-with-breakpoints"></a>Kesme noktalarıyla hata ayıkla

Hata ayıklama sırasında bazı kesme noktaları ekleyerek kodu test edebilirsiniz. Kesme   >  **noktası geçiş noktasını** seçerek, kesmenin gerçekleşmesini istediğiniz kod satırının yanındaki düzenleyicinin sol kenar boşluğuna tıklayarak veya **F9** tuşuna basarak kesme noktaları ekleyebilirsiniz.

#### <a name="add-breakpoints"></a>Kesme noktası ekleme

::: moniker range="vs-2019"

1. *Greetings. xaml. vb* dosyasını açın ve aşağıdaki satırı seçin:`MessageBox.Show("Hello.")`

1. **Hata Ayıkla**' yı ve ardından **kesme noktası**' nı seçip menüden **F9** tuşuna basarak bir kesme noktası ekleyin.

   Düzenleyici penceresinin en sol kenar boşluğunda, kod satırının yanında kırmızı bir daire görünür.

1. Aşağıdaki satırı seçin: `MessageBox.Show("Goodbye.")` .

1. Bir kesme noktası eklemek için **F9** tuşuna basın ve sonra hata ayıklamayı başlatmak için **F5** 'e basın.

1. **Tebrikler** penceresinde, **Merhaba** radyo düğmesini seçin ve ardından **görüntüle** düğmesini seçin.

   Çizgi `MessageBox.Show("Hello.")` sarı renkle vurgulanır. ıde 'nin en altında, oto, yereller ve Watch pencereleri, sol tarafa birlikte yerleştirilir ve çağrı yığını, kesme noktaları, özel durum Ayarlar, komut, anlık ve çıkış pencereleri sağ tarafta bir araya yerleştirildi.

   ![kod, tanılama ile Visual Studio bir hata ayıklama oturumunun gösterildiği ekran görüntüsü. Oto ve çağrı yığını pencereleri açık. Yürütme, Greetings. xaml. vb içindeki bir kesme noktasında durdurulur.](media/exploreide-debugbreakpoint.png)

1. Menü çubuğunda **Hata Ayıkla** > **Step Out**' ı seçin.

     Uygulama yürütmeyi sürdürür ve "Hello&quot; sözcüğünü içeren bir ileti kutusu görünür.

1. İletiyi kapatmak için ileti kutusunda **Tamam** düğmesini seçin.

1. **Tebrikler** penceresinde, **güle** radyo düğmesini seçin ve ardından **görüntüle** düğmesini seçin.

     Çizgi `MessageBox.Show(&quot;Goodbye.")` sarı renkle vurgulanır.

1. Hata **ayıklamaya devam etmek** için F5 tuşuna basın. İleti kutusu görüntülendiğinde, kapatmak **için** ileti kutusunda Tamam düğmesini seçin.

1. Hata ayıklamayı durdurmak için uygulama penceresini kapatın.

1. Menü çubuğunda Hata Ayıkla Tüm **Kesme Noktaları'nın** > **Devre Dışı Bırak'ı seçin.**

::: moniker-end

::: moniker range=">=vs-2022"

1. *Greetings.xaml.vb'yi* açın ve aşağıdaki satırı seçin:`MessageBox.Show("Hello.")`

1. F9 tuşuna basarak veya **menüden** Hata Ayıkla'ya ve ardından Kesme Noktası **Aç/Aç/Aç'ı seçerek bir kesme noktası ekleyin.**

   Düzenleyici penceresinin en sol kenar boşluğunda veya boşluğunda kod satırın yanında kırmızı bir daire görünür.

1. Şu satırı seçin: `MessageBox.Show("Goodbye.")` .

1. Kesme noktası **eklemek için F9** tuşuna basın ve ardından hata ayıklamayı **başlatmak için F5** tuşuna basın.

1. Selamlama **penceresinde** Hello radyo **düğmesini** ve ardından Görüntüle **düğmesini** seçin.

   Satır `MessageBox.Show("Hello.")` sarıyla vurgulanır. IDE'nin alt kısmında, Sol tarafta Otomatikler, Yereller ve İzleme pencereleri bir araya, Çağrı Yığını, Kesme Noktaları, Özel Durum Ayarlar, Komut, Anlık ve Çıkış pencereleri de sağ tarafta birlikte yer almaktadır.

   :::image type="content" source="media/vs-2022/explore-ide-debug-breakpoint.png" alt-text="Kod, Tanılama ile Visual Studio hata ayıklama oturumunu gösteren ekran görüntüsü. Otomatikler ve Çağrı Yığını pencereleri açılır. Yürütme Greetings.xaml.vb.'de bir kesme noktası sırasında durdurulur.":::

1. Menü çubuğunda Hata Ayıkla **Adım Dışarı seçeneğini** > **belirleyin.**

     Uygulama yürütmeyi sürdürür ve "Hello" sözcüğüyle bir ileti kutusu görüntülenir.

1. kapatmak **için** ileti kutusunda Tamam düğmesini seçin.

1. Selamlama **penceresinde** Güle Güle radyo **düğmesini** ve ardından Görüntüle **düğmesini** seçin.

     Satır `MessageBox.Show("Goodbye.")` sarıyla vurgulanır.

1. Hata **ayıklamaya devam etmek** için F5 tuşuna basın. İleti kutusu görüntülendiğinde, kapatmak **için** ileti kutusunda Tamam düğmesini seçin.

1. Hata ayıklamayı durdurmak için uygulama penceresini kapatın.

1. Menü çubuğunda Hata Ayıkla Tüm **Kesme Noktaları'nın** > **Devre Dışı Bırak'ı seçin.**

::: moniker-end

### <a name="view-a-representation-of-the-ui-elements"></a>Kullanıcı arabirimi öğelerinin bir gösterimini görüntüleme

Çalışan uygulamada, pencerenizin üst kısmında görünen bir pencere öğesi görüyor olun. Bu, bazı yararlı hata ayıklama özelliklerine hızlı erişim sağlayan bir çalışma zamanı yardımcıdır. İlk düğmeye tıklayın, **Canlı Görsel Ağaç'a gidin.** Sayfanın tüm görsel öğelerini içeren bir ağaç içeren bir pencere görüyor gerekir. Eklenen düğmeleri bulmak için düğümleri genişletin.

::: moniker range="vs-2019"

![Görsel öğeler için tüm görsel öğeleri içeren bir ağacı görüntüleyen Canlı Görsel Ağaç penceresini gösteren HelloWPFApp.exe.](media/vs-2019/exploreide-live-visual-tree.png)

::: moniker-end

::: moniker range=">=vs-2022"

:::image type="content" source="media/vs-2022/explore-ide-live-visual-tree.png" alt-text="Görsel öğeler için tüm görsel öğeleri içeren bir ağacı görüntüleyen Canlı Görsel Ağaç penceresini gösteren HelloWPFApp.exe.":::

::: moniker-end
### <a name="build-a-release-version-of-the-application"></a>Uygulamanın yayın sürümünü oluşturma

Her şeyin çalıştığını doğruladıktan sonra uygulamanın yayın derlemesi hazırlanabilir.

1. Ana menüde, önceki **derlemeler sırasında** oluşturulan ara dosyaları ve çıkış dosyalarını silmek için Derleme Temizleme  >   çözümü'ne tıklayın. Bu gerekli değildir, ancak hata ayıklama derleme çıkışlarını temizler.

1. Araç çubuğundaki açılır menü denetimiyle HelloWPFApp derleme yapılandırmasını Hata Ayıklama'dan Sürüm'e (şu anda "Hata Ayıkla" olarak görünür) değiştirebilirsiniz.  

1. Çözümü Derleme **Çözümü'dür'dür'**  >  **seçerek çözümü derleme.**

Tebrikler, bu öğreticiyi tamamladıktan sonra! Çözüm ve proje *.exe* (*...\HelloWPFApp\HelloWPFApp\bin\Release)* altında yerleşik olarak bulundurduyabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

::: moniker range="vs-2017"

- [Visual Studio 2017’deki yenilikler](../../ide/whats-new-visual-studio-2017.md)
- [Üretkenlik ipuçları](../../ide/productivity-features.md)

::: moniker-end

::: moniker range="vs-2019"

- [Visual Studio 2019'daki yeniler](../../ide/whats-new-visual-studio-2019.md)
- [Üretkenlik ipuçları](../../ide/productivity-features.md)

::: moniker-end

::: moniker range="vs-2022"

- [Visual Studio 2022'de yapılan yeniler](../../ide/whats-new-visual-studio-2022.md)
- [Üretkenlik ipuçları](../../ide/productivity-features.md)

::: moniker-end
