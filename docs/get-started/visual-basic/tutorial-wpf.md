---
title: Visual Basic içinde WPF ile uygulama Merhaba Dünya
description: Windows Presentation Foundation (WPF) kullanıcı arabirimi çerçevesini kullanarak Visual Studio ile Visual Basic basit bir Windows masaüstü .net uygulaması oluşturun.
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
ms.sourcegitcommit: 8e74969ff61b609c89b3139434dff5a742c18ff4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2021
ms.locfileid: "128431152"
---
# <a name="tutorial-create-a-simple-application-with-visual-basic"></a>Öğretici: Visual Basic ile basit bir uygulama oluşturma

Bu öğreticiyi tamamlayarak, Visual Studio ile uygulama geliştirirken kullanabileceğiniz birçok araç, iletişim kutusu ve tasarımcı hakkında bilgi sahibi olacaksınız. Tümleşik geliştirme ortamında ([IDE](visual-studio-ide.md)) çalışmayı öğrenirken, "Merhaba, Dünya" uygulaması, Kullanıcı arabirimini tasarlayacağınız, kod ekleyerek ve hata ayıkladığınızda bir "Hello, World" uygulaması oluşturacaksınız.

::: moniker range="vs-2017"

Visual Studio henüz yüklemediyseniz, [Visual Studio indirmeleri](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) sayfasına giderek ücretsiz yükleme yapın.

::: moniker-end

::: moniker range=">=vs-2019"

Visual Studio henüz yüklemediyseniz, [Visual Studio indirmeleri](https://visualstudio.microsoft.com/downloads) sayfasına giderek ücretsiz yükleme yapın.

::: moniker-end

## <a name="configure-the-ide"></a>IDE'yi yapılandırma

::: moniker range="vs-2017"

Visual Studio ilk kez açtığınızda, oturum açmanız istenir. Bu adım, bu öğretici için isteğe bağlıdır. Ardından, geliştirme ayarlarınızı ve renk temasını seçmenizi isteyen bir iletişim kutusu görüntülenebilir. Varsayılanları tutun ve **Visual Studio Başlat**' ı seçin.

![Ayarları Seç iletişim kutusu](../media/exploreide-settings.png)

Visual Studio başlatıldıktan sonra araç pencerelerini, menüleri ve araç çubuklarını ve ana pencere alanını görürsünüz. Araç pencereleri, **Hızlı Başlat**, menü çubuğu ve en üstteki Standart araç çubuğu ile uygulama penceresinin sol ve sağ taraflarına yerleştirilir. Uygulama penceresinin merkezinde **Başlangıç sayfası** bulunur. Bir çözüm veya proje yüklediğinizde, düzenleyiciler ve tasarımcılar **Başlangıç sayfasının** bulunduğu alanda görüntülenir. Bir uygulama geliştirirken, bu merkezi alanda zamanınızın çoğunu harcarcaksınız.

![genel Ayarlar uygulanmış Visual Studio 2017 ıde](../media/exploreide-idewithgeneralsettings.png)

::: moniker-end

::: moniker range=">=vs-2019"

Visual Studio başlattığınızda ilk pencere açılır. Geliştirme ortamını açmak için **kod olmadan devam et** ' i seçin. Araç pencerelerini, menüleri ve araç çubuklarını ve ana pencere alanını görürsünüz. Araç pencereleri, uygulama penceresinin sol ve sağ taraflarına yerleştirilir. Arama kutusu, menü çubuğu ve standart araç çubuğu en üstte bulunur. Bir çözüm veya proje yüklediğinizde, düzenleyiciler ve tasarımcılar uygulama penceresinin orta alanında görüntülenir. Bir uygulama geliştirirken, bu merkezi alanda zamanınızın çoğunu harcarcaksınız.

::: moniker-end

## <a name="create-the-project"></a>Proje oluşturma

Visual Studio'da bir uygulama oluştururken önce bir proje ve bir çözüm oluşturursunuz. bu örnekte, bir Windows Presentation Foundation (WPF) projesi oluşturacaksınız.

::: moniker range="vs-2017"

1. Yeni bir proje oluşturma. menü çubuğunda **dosya**  >  **yeni**  >  **Project**' yi seçin.

     ![Menü çubuğunda dosya, yeni, Project ' yi seçin.](../media/exploreide-filenewproject.png)

1. **yeni Project** iletişim kutusunda, **yüklü**  >  **Visual Basic**  >  **Windows masaüstü** kategorisini seçin ve ardından **WPF uygulaması (.NET Framework)** şablonunu seçin. Projeyi **HelloWPFApp** olarak adlandırın ve **Tamam**' ı seçin.

     ![Visual Studio yeni Project iletişim kutusunda WPF uygulama şablonu](media/exploreide-newproject-vb.png)

Visual Studio hellowpfapp projesini ve çözümünü oluşturur ve **Çözüm Gezgini** çeşitli dosyaları gösterir. **WPF Tasarımcısı** , bölünmüş bir görünümde *MainWindow. xaml* ' in BIR Tasarım görünümünü ve XAML görünümünü gösterir. Herhangi bir görünümden daha fazla veya daha az görünmesi için Bölümlendirici slaytı gösterebilirsiniz. Yalnızca görsel görünümü veya yalnızca XAML görünümünü görmeyi seçebilirsiniz. Aşağıdaki öğeler **Çözüm Gezgini** görüntülenir:

![HelloWPFApp dosyaları yüklü Çözüm Gezgini](../media/exploreide-hellowpfappfiles.png)

::: moniker-end

::: moniker range="vs-2019"

1. Visual Studio'yu açın.

1. **yeni proje oluştur** ekranında, "wpf" araması yapın ve **WPF uygulaması (.NET Framework)** öğesini seçin ve ardından **ileri**' yi seçin.

   ![arama kutusuna "yeni proje oluştur" iletişim kutusunun ve ' wpf uygulaması (.NET Framework) ' proje şablonunda girilen ekran görüntüsü.](media/vs-2019/exploreide-newprojectvb-vs2019.png)

1. Sonraki ekranda, projeye **HelloWPFApp** adını verin ve **Oluştur**' u seçin.

Visual Studio hellowpfapp projesini ve çözümünü oluşturur ve **Çözüm Gezgini** çeşitli dosyaları gösterir. **WPF Tasarımcısı** , bölünmüş bir görünümde *MainWindow. xaml* ' in BIR Tasarım görünümünü ve XAML görünümünü gösterir. Herhangi bir görünümden daha fazla veya daha az görünmesi için Bölümlendirici slaytı gösterebilirsiniz. Yalnızca görsel görünümü veya yalnızca XAML görünümünü görmeyi seçebilirsiniz. Aşağıdaki öğeler **Çözüm Gezgini** görüntülenir:

![Çözüm Gezgini HelloWPFApp projesinde ve çözümünde bulunan dosyaları gösteren ekran görüntüsü.](../media/vs-2019/exploreide-hellowpfappfiles.png)

::: moniker-end

::: moniker range=">=vs-2022"

1. Visual Studio'yu açın.
 
1. Başlangıç penceresinde **Yeni proje oluştur**' u seçin.

   :::image type="content" source="media/vs-2022/start-window-create-new-project.png" alt-text="Visual Studio 2022 ' de ' yeni proje oluştur ' seçeneği vurgulanmış olarak başlangıç penceresinin ekran görüntüsü.":::

1. **yeni proje oluştur** ekranında, "WPF" araması yapın ve **tüm diller** açılan listesinden **Visual Basic** seçin. **WPF uygulaması (.NET Framework)** öğesini seçin ve ardından **ileri**' yi seçin.

   :::image type="content" source="media/vs-2022/explore-ide-new-wpf-app-project-vb.png" alt-text="&quot;yeni proje oluştur&quot; iletişim kutusunda ' wpf ', diller listesinde seçilen ' Visual Basic ' ve ' wpf uygulaması (.NET Framework) ' proje şablonu vurgulanmış ' ' bir ekran görüntüsü.":::

1. Sonraki ekranda, projeye **HelloWPFApp** adını verin ve **Oluştur**' u seçin.

Visual Studio hellowpfapp projesini ve çözümünü oluşturur ve **Çözüm Gezgini** çeşitli dosyaları gösterir. **WPF Tasarımcısı** , bölünmüş bir görünümde *MainWindow. xaml* ' in BIR Tasarım görünümünü ve XAML görünümünü gösterir. Herhangi bir görünümden daha fazla veya daha az görünmesi için Bölümlendirici slaytı gösterebilirsiniz. Yalnızca görsel görünümü veya yalnızca XAML görünümünü görmeyi seçebilirsiniz. Aşağıdaki öğeler **Çözüm Gezgini** görüntülenir:

:::image type="content" source="media/vs-2022/explore-ide-hello-wpf-app-files.png" alt-text="Çözüm Gezgini HelloWPFApp projesinde ve çözümünde bulunan dosyaları gösteren ekran görüntüsü.":::

::: moniker-end

> [!NOTE]
> XAML (Genişletilebilir uygulama biçimlendirme dili) hakkında daha fazla bilgi için bkz. [WPF Için xaml genel bakış](/dotnet/framework/wpf/advanced/xaml-overview-wpf) sayfası.

Projeyi oluşturduktan sonra özelleştirebilirsiniz. **Özellikler** penceresini kullanarak ( **Görünüm** menüsünde bulunur), bir uygulamadaki proje öğeleri, denetimler ve diğer öğeler için seçenekleri görüntüleyebilir ve değiştirebilirsiniz.

### <a name="change-the-name-of-mainwindowxaml"></a>MainWindow. xaml adını değiştirme

Şimdi, MainWindow 'e daha özel bir ad verelim. **Çözüm Gezgini**, *MainWindow. xaml* ' e sağ tıklayıp **Yeniden Adlandır**' ı seçin. Dosyayı *Greetings. xaml* olarak yeniden adlandırın.

İsteğe bağlı bir adım olarak, uygulama pencerenizin başlığını bu yeni adla eşleşecek şekilde değiştirecek karışıklıklara engel olur.

1. **Çözüm Gezgini**' de, az önce yeniden adlandırdığınız *Greetings. xaml* dosyasını açın.

1. XAML görünümünde  **Window. title** özelliğinin değerini `Title="MainWindow"` olarak değiştirin `Title="Greetings"` ve değişiklikleri kaydedin.

## <a name="design-the-user-interface-ui"></a>Kullanıcı arabirimini (UI) tasarlama

Tasarımcı açık değilse, **Çözüm Gezgini** *Greetings. xaml* ' i seçin ve sonra  + da tasarımcıyı açmak için SHIFT **F7** tuşuna basın.

Bu uygulamaya üç tür denetim ekleyeceğiz: <xref:System.Windows.Controls.TextBlock> Denetim, iki denetim <xref:System.Windows.Controls.RadioButton> ve bir <xref:System.Windows.Controls.Button> Denetim.

### <a name="add-a-textblock-control"></a>TextBlock denetimi ekleme

::: moniker range="vs-2019"

1. **CTRL** + **Q** tuşlarına basarak arama kutusunu etkinleştirin ve **araç kutusu** yazın. Sonuçlar listesinden **> araç kutusunu görüntüle** ' yi seçin.

1. **Araç kutusunda**, TextBlock denetimini görmek IÇIN **ortak WPF denetimleri** düğümünü genişletin.

   ![Ortak WPF denetimleri listesinde TextBlock denetimiyle vurgulanmış araç kutusu penceresini gösteren ekran görüntüsü.](../media/exploreide-textblocktoolbox.png)

1. **TextBlock** öğesini seçerek ve tasarım yüzeyinde pencereye sürükleyerek tasarım yüzeyine bir TextBlock denetimi ekleyin. Pencerenin üst kısmına yakın olan denetimi ortalayın. Visual Studio 2019 ve üzeri sürümlerde, denetimi ortalamak için kırmızı yönergeleri kullanabilirsiniz.

Pencereniz aşağıdaki gösterime benzemelidir:

![Greetings formunda konumlandırılmış TextBlock denetimini gösteren ekran görüntüsü.](../media/exploreide-greetingswithtextblockonly.png)

XAML işaretlemesi aşağıdaki örnekteki gibi görünmelidir:

```xaml
<TextBlock HorizontalAlignment="Left" Margin="381,100,0,0" TextWrapping="Wrap" Text="TextBlock" VerticalAlignment="Top"/>
```

::: moniker-end

::: moniker range=">=vs-2022"

1. **CTRL** + **Q** tuşlarına basarak arama kutusunu etkinleştirin ve **araç kutusu** yazın. Sonuçlar listesinden **> araç kutusunu görüntüle** ' yi seçin.

1. **Araç kutusunda**, TextBlock denetimini görmek IÇIN **ortak WPF denetimleri** düğümünü genişletin.

   :::image type="content" source="media/vs-2022/explore-ide-textblock-toolbox.png" alt-text="Ortak WPF denetimleri listesinde TextBlock denetimiyle vurgulanmış araç kutusu penceresini gösteren ekran görüntüsü.":::

1. **TextBlock** öğesini seçerek ve tasarım yüzeyinde pencereye sürükleyerek tasarım yüzeyine bir TextBlock denetimi ekleyin. Pencerenin üst kısmına yakın olan denetimi ortalayın. Denetimi ortalamak için yönergeleri kullanabilirsiniz.

Pencereniz aşağıdaki görüntüye benzemelidir:

:::image type="content" source="media/vs-2022/explore-ide-greetings-with-textblock-only.png" alt-text="Selamlamalar biçiminde bulunan ve görünen kılavuzlarla birlikte bulunan TextBlock denetimini gösteren ekran görüntüsü.":::

XAML işaretlemesi aşağıdaki örnekteki gibi görünmelidir:

```xaml
<TextBlock HorizontalAlignment="Left" Margin="381,100,0,0" TextWrapping="Wrap" Text="TextBlock" VerticalAlignment="Top"/>
```

::: moniker-end

### <a name="customize-the-text-in-the-text-block"></a>Metin bloğundaki metni özelleştirme

1. XAML görünümünde TextBlock için biçimlendirmeyi bulun ve metin özniteliğini değiştirin:

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

![Çalışan uygulamanın ekran görüntüsü](media/exploreide-wpf-running-app.png "TextBlock, RadioButtons ve düğme denetimlerinin görünür olduğu Greetings penceresinin ekran görüntüsü. ' Merhaba ' radyo düğmesi seçildi.")

::: moniker-end

::: moniker range="vs-2019"

![Çalışan uygulamanın ekran görüntüsü](media/vs-2019/exploreide-wpf-running-app.png "TextBlock, RadioButtons ve düğme denetimlerinin görünür olduğu Greetings penceresinin ekran görüntüsü. ' Merhaba ' radyo düğmesi seçildi.")

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

1. Hata ayıklamaya devam etmek için **F5** tuşunu seçin. İleti kutusu göründüğünde kapatmak için ileti kutusunda **Tamam** düğmesini seçin.

1. Hata ayıklamayı durdurmak için uygulama penceresini kapatın.

1. Menü çubuğunda, **Hata Ayıkla** > **tüm kesme noktalarını devre dışı bırak**' ı seçin.

::: moniker-end

::: moniker range=">=vs-2022"

1. *Greetings. xaml. vb* dosyasını açın ve aşağıdaki satırı seçin:`MessageBox.Show("Hello.")`

1. **Hata Ayıkla**' yı ve ardından **kesme noktası**' nı seçip menüden **F9** tuşuna basarak bir kesme noktası ekleyin.

   Sol taraftaki kenar boşluğunda veya düzenleyici penceresinin cilt payından kod satırının yanında kırmızı bir daire görünür.

1. Aşağıdaki satırı seçin: `MessageBox.Show("Goodbye.")` .

1. Bir kesme noktası eklemek için **F9** tuşuna basın ve sonra hata ayıklamayı başlatmak için **F5** 'e basın.

1. **Tebrikler** penceresinde, **Merhaba** radyo düğmesini seçin ve ardından **görüntüle** düğmesini seçin.

   Çizgi `MessageBox.Show("Hello.")` sarı renkle vurgulanır. ıde 'nin en altında, oto, yereller ve Watch pencereleri, sol tarafa birlikte yerleştirilir ve çağrı yığını, kesme noktaları, özel durum Ayarlar, komut, anlık ve çıkış pencereleri sağ tarafta bir araya yerleştirildi.

   :::image type="content" source="media/vs-2022/explore-ide-debug-breakpoint.png" alt-text="kod, tanılama ile Visual Studio bir hata ayıklama oturumunun gösterildiği ekran görüntüsü. Oto ve çağrı yığını pencereleri açık. Yürütme, Greetings. xaml. vb içindeki bir kesme noktasında durdurulur.":::

1. Menü çubuğunda **Hata Ayıkla** > **Step Out**' ı seçin.

     Uygulama yürütmeyi sürdürür ve "Hello" sözcüğünü içeren bir ileti kutusu görünür.

1. İletiyi kapatmak için ileti kutusunda **Tamam** düğmesini seçin.

1. **Tebrikler** penceresinde, **güle** radyo düğmesini seçin ve ardından **görüntüle** düğmesini seçin.

     Çizgi `MessageBox.Show("Goodbye.")` sarı renkle vurgulanır.

1. Hata ayıklamaya devam etmek için **F5** tuşunu seçin. İleti kutusu göründüğünde kapatmak için ileti kutusunda **Tamam** düğmesini seçin.

1. Hata ayıklamayı durdurmak için uygulama penceresini kapatın.

1. Menü çubuğunda, **Hata Ayıkla** > **tüm kesme noktalarını devre dışı bırak**' ı seçin.

::: moniker-end

### <a name="view-a-representation-of-the-ui-elements"></a>UI öğelerinin gösterimini görüntüleme

Çalışan uygulamada, pencerenizin en üstünde görüntülenen bir pencere öğesi görmeniz gerekir. Bu, bazı yararlı hata ayıklama özelliklerine hızlı erişim sağlayan bir çalışma zamanı yardımcıdır. İlk düğmesine tıklayın, **canlı görsel ağaç**' a gidin. Sayfanızın tüm görsel öğelerini içeren bir ağacı olan bir pencere görmeniz gerekir. Eklediğiniz düğmeleri bulmak için düğümleri genişletin.

::: moniker range="vs-2019"

![HelloWPFApp.exe için tüm görsel öğeleri içeren bir ağaç görüntüleyen canlı görsel ağaç penceresini gösteren ekran görüntüsü.](media/vs-2019/exploreide-live-visual-tree.png)

::: moniker-end

::: moniker range=">=vs-2022"

:::image type="content" source="media/vs-2022/explore-ide-live-visual-tree.png" alt-text="HelloWPFApp.exe için tüm görsel öğeleri içeren bir ağaç görüntüleyen canlı görsel ağaç penceresini gösteren ekran görüntüsü.":::

::: moniker-end
### <a name="build-a-release-version-of-the-application"></a>Uygulamanın yayın sürümünü oluşturma

Her şeyin çalıştığından emin olduğunuza göre, uygulamanın yayın derlemesini hazırlayabilirsiniz.

1. Ana menüde,   >  önceki derlemeler sırasında oluşturulan ara dosyaları ve çıktı dosyalarını silmek için **temiz çözüm** oluştur ' u seçin. Bu gerekli değildir, ancak hata ayıklama oluşturma çıkışlarını temizler.

1. Araç çubuğundaki DropDown denetimini kullanarak HelloWPFApp için derleme yapılandırmasını **hata ayıklamadan** **Yayınla** değiştirin (Şu anda "hata ayıkla" ifadesini alır).

1. **Build**  >  **Build Solution** öğesini seçerek çözümü oluşturun.

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

- [Visual Studio 2022 ' deki yenilikler](../../ide/whats-new-visual-studio-2022.md)
- [Üretkenlik ipuçları](../../ide/productivity-features.md)

::: moniker-end
