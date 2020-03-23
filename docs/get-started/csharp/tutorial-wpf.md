---
title: 'C WPF ile Merhaba Dünya uygulaması #'
description: Windows Presentation Foundation (WPF) Kullanıcı Bira Sıtkı çerçevesini kullanarak Visual Studio ile C#'da basit bir Windows Desktop .NET uygulaması oluşturun.
ms.custom: seodec18, get-started
ms.date: 08/09/2019
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.topic: conceptual
dev_langs:
- CSharp
ms.assetid: f84339c7-d617-4f56-bfcd-af2215c347ba
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: ba8a29a75b21351d94c818837f07ff22785a07b5
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77579984"
---
# <a name="tutorial-create-a-simple-application-with-c"></a>Öğretici: C ile basit bir uygulama oluşturun\#

Bu öğreticiyi tamamlayarak, Visual Studio ile uygulama geliştirirken kullanabileceğiniz birçok araç, iletişim kutusu ve tasarımcıyı öğreneceksiniz. Entegre geliştirme ortamında[(IDE)](visual-studio-ide.md)çalışmayı öğrenirken bir "Merhaba, Dünya" uygulaması oluşturacak, kullanıcı yı tasarlayacak, kod ekleyecek ve hata ayıklama hataları yapacaksınız.

## <a name="prerequisites"></a>Önkoşullar

::: moniker range="vs-2017"
Visual Studio'yu henüz yüklemediyseniz, visual [studio indirme sayfasına](https://visualstudio.microsoft.com/vs/older-downloads/?) gidin ve ücretsiz olarak yükleyin.
::: moniker-end
::: moniker range=">=vs-2019"

- Visual Studio'yu henüz yüklemediyseniz, visual [studio indirme sayfasına](https://visualstudio.microsoft.com/downloads/) gidin ve ücretsiz olarak yükleyin.
- Bu öğretici için .NET Framework veya .NET Core'u kullanabilirsiniz. .NET Core daha yeni, daha modern bir çerçevedir. .NET Core Visual Studio 2019 sürüm 16.3 veya daha sonra gerektirir.
::: moniker-end

## <a name="configure-the-ide"></a>IDE'yi yapılandırma

::: moniker range="vs-2017"

Visual Studio'yu ilk kez açtığınızda oturum açmanız istenir. Bu adım bu öğretici için isteğe bağlıdır. Ardından, geliştirme ayarlarınızı ve renk temanızı seçmenizi isteyen bir iletişim kutusu gösterilebilir. Varsayılanları koruyun ve **Görsel Stüdyoyu Başlat'ı**seçin.

![Ayarlar iletişim kutusunu seçin](../media/exploreide-settings.png)

Visual Studio başlattıktan sonra araç pencerelerini, menüleri ve araç çubuklarını ve ana pencere alanını görürsünüz. Araç pencereleri uygulama penceresinin sol ve sağ kenarlarına, **Hızlı Başlatma,** menü çubuğu ve üstteki standart araç çubuğuyla sabitlenir. Uygulama penceresinin ortasında Başlat **Sayfası**dır. Bir çözüm veya proje yüklediğinizde, düzenleyiciler ve tasarımcılar **Başlangıç Sayfasının** bulunduğu alanda görünür. Bir uygulama geliştirdiğinizde, zamanınızın çoğunu bu merkezi alanda geçirirsiniz.

![Visual Studio 2017 IDE Genel Ayarları uygulanarak](../media/exploreide-idewithgeneralsettings.png "Visual Studio 2017 IDE'nin Genel Ayarları uygulanan ekran görüntüsü")

::: moniker-end

::: moniker range=">=vs-2019"

Visual Studio'yu başlattığınızda, önce başlangıç penceresi açılır. Geliştirme ortamını açmak için **kodsuz Devam** et'i seçin. Araç pencerelerini, menüleri ve araç çubuklarını ve ana pencere alanını görürsünüz. Araç pencereleri uygulama penceresinin sol ve sağ kenarlarına, bir arama kutusu, menü çubuğu ve en üstteki standart araç çubuğuyla sabitlenir. Bir çözüm veya proje yüklediğinizde, uygulama penceresinin merkezi alanında düzenleyiciler ve tasarımcılar görünür. Bir uygulama geliştirdiğinizde, zamanınızın çoğunu bu merkezi alanda geçirirsiniz.

::: moniker-end

## <a name="create-the-project"></a>Proje oluşturma

Visual Studio'da bir uygulama oluştururken önce bir proje ve bir çözüm oluşturursunuz. Bu örnekte, bir Windows Sunu Temeli (WPF) projesi oluşturursunuz.

::: moniker range="vs-2017"

1. Yeni bir proje oluşturma. Menü çubuğunda**Yeni** > **Proje** **yi seç.** > 

     ![Menü çubuğunda Dosya, Yeni, Proje'yi seçin](../media/exploreide-filenewproject.png "Dosya, Yeni, Proje'yi seçtiğiniz menü çubuğunun ekran görüntüsü")

1. Yeni **Proje** iletişim kutusunda, **Yüklü** > **Görsel C#** > **Windows Masaüstü** kategorisini seçin ve ardından **WPF Uygulaması (.NET Framework)** şablonunu seçin. Projeye **HelloWPFApp**adını ve **Tamam'ı**seçin.

     ![Visual Studio Yeni Proje iletişim kutusunda WPF uygulama şablonu](media/exploreide-newprojectcsharp.png "Yeni Proje iletişim kutusundaki WPF uygulama şablonunun ekran görüntüsü")

::: moniker-end

::: moniker range="vs-2019"

1. Görsel Stüdyo 2019'u açın.

1. Başlangıç penceresinde yeni **proje oluştur'u**seçin.

   !['Yeni proje oluşturma' penceresini görüntüleme](../../get-started/media/vs-2019/start-window-create-new-project.png "'Yeni bir proje oluşturma' penceresinin ekran görüntüsü")

1. Yeni **bir proje oluşturma** ekranında "WPF"yi arayın, **WPF Uygulamasını (.NET Core)** seçin ve sonra **İleri'yi**seçin.

   !['Yeni bir proje oluşturma' iletişim kutusunda WPF uygulama şablonu](media/vs-2019/exploreide-newprojectcsharp-vs2019.png "'Yeni bir proje oluşturma' iletişim kutusundaki WPF uygulama şablonunun ekran görüntüsü")

   > [!NOTE]
   > Biri .NET Framework, diğeri .NET Core için olmak üzere iki WPF masaüstü şablonu bulabilirsiniz. .NET Core şablonu Visual Studio 2019 sürüm 16.3 ve sonraki sürümlerde mevcuttur. Bu öğretici için her ikisini de kullanabilirsiniz, ancak yeni geliştirme için .NET Core'u öneririz.

1. Bir sonraki ekranda, proje bir isim vermek, **HelloWPFApp**, ve **Oluştur**seçin .

   ![Projenize 'HelloWPFApp' adını vereb](./media/vs-2019/exploreide-nameproject.png "Projenizi adlandırdığınız pencerenin ekran görüntüsü")

::: moniker-end

Visual Studio HelloWPFApp proje ve çözüm oluşturur ve **Çözüm Explorer** çeşitli dosyaları gösterir. **WPF Tasarımcısı** bölünmüş bir görünümde *MainWindow.xaml'ın* tasarım görünümünü ve XAML görünümünü gösterir. Her iki görünümü daha fazla veya daha az göstermek için ayırıcıyı kaydırabilirsiniz. Yalnızca görsel görünümü veya yalnızca XAML görünümünü görmeyi seçebilirsiniz.

![IDE'de WPF projesi ve çözümü](media/exploreide-wpfproject-cs.png "IDE'deki WPF projesinin ve çözümünün ekran görüntüsü")

> [!NOTE]
> XAML (eXtensible Application Markup Language) hakkında daha fazla bilgi için WPF sayfası [için XAML genel görünümüne](/dotnet/framework/wpf/advanced/xaml-overview-wpf) bakın.

Projeyi oluşturduktan sonra özelleştirebilirsiniz. Bunu yapmak için **Görünüm** menüsünden **Özellikler Penceresi'ni** seçin veya **F4**tuşuna basın. Ardından, bir uygulamadaki proje öğeleri, denetimler ve diğer öğeler için seçenekleri görüntüleyebilir ve değiştirebilirsiniz.

   ![Özellik penceresi](../media/exploreide-hellowpfappfiles.png "WPF dosya uygulama adlarıyla Özellikler penceresinin ekran görüntüsü")   

### <a name="change-the-name-of-mainwindowxaml"></a>MainWindow.xaml adını değiştirin

MainWindow'a daha özel bir ad verelim. **Solution Explorer'da** *MainWindow.xaml'a* sağ tıklayın ve **Yeniden Adlandır'ı**seçin. Dosyayı *Greetings.xaml*olarak yeniden adlandırın.

## <a name="design-the-user-interface-ui"></a>Kullanıcı arabirimini (UI) tasarlama

Tasarımcı açık değilse, *Greetings.xaml'ı* seçin ve tasarımcıyı açmak için **Shift**+**F7** tuşuna basın.

Bu uygulamaya üç tür denetim ekleriz: <xref:System.Windows.Controls.TextBlock> bir <xref:System.Windows.Controls.RadioButton> denetim, iki <xref:System.Windows.Controls.Button> denetim ve bir denetim.

### <a name="add-a-textblock-control"></a>TextBlock denetimi ekleme

1. Arama kutusunu etkinleştirmek için **Ctrl**+**Q** tuşuna basın ve **Toolbox**yazın. Sonuç listesinden **Araç > Görüntüle'yi** seçin.

1. Araç **Kutusunda,** TextBlock denetimini görmek için **Ortak WPF Denetimleri** düğümlerini genişletin.

     ![TextBlock denetimi vurgulanmış araç kutusu](../media/exploreide-textblocktoolbox.png "TextBlock denetimi vurgulanmış Araç Kutusu penceresinin ekran görüntüsü")

1. TextBlock öğesini seçip tasarım yüzeyindeki pencereye sürükleyerek tasarım yüzeyine **textblock** denetimi ekleyin. Denetimi pencerenin üst kısmından ortala. Visual Studio 2019 ve sonraki durumlarda, denetimi ortalamak için kırmızı yönergeleri kullanabilirsiniz.

    Pencereniz aşağıdaki gösterime benzemelidir:

    ![Selamlar formunda TextBlock denetimi](../media/exploreide-greetingswithtextblockonly.png "Selamlar formundaki TextBlock denetiminin ekran görüntüsü")

   XAML biçimlendirmesi aşağıdaki örneğe benzer:

    ```xaml
    <Grid>
        <TextBlock HorizontalAlignment="Left" Margin="387,60,0,0" TextWrapping="Wrap" Text="TextBlock" VerticalAlignment="Top"/>
    </Grid>
    ```

### <a name="customize-the-text-in-the-text-block"></a>Metin bloğundaki metni özelleştirme

1. XAML görünümünde **TextBlock** için biçimlendirmeyi bulun **Text** ve Metin `TextBox` özniteliğini`Select a message option and then choose the Display button.`

   XAML biçimlendirmesi aşağıdaki örneğe benzer:

   ```xaml
   <Grid>
       <TextBlock HorizontalAlignment="Left" Margin="387,60,0,0" TextWrapping="Wrap" Text="Select a message option and then choose the Display button." VerticalAlignment="Top"/>
   </Grid>
   ```

1. İsterseniz TextBlock'u yeniden ortalayın ve **Ctrl+S** tuşuna basarak veya **Dosya** menü öğesini kullanarak değişikliklerinizi kaydedin.

Ardından, forma iki [RadioButton](/dotnet/framework/wpf/controls/radiobutton) denetimi eklersiniz.

### <a name="add-radio-buttons"></a>Radyo düğmesi ekleme

1. Araç **Kutusunda,** **RadioButton** denetimini bulun.

     ![RadioButton denetimi seçili araç kutusu penceresi](../media/exploreide-radiobuttontoolbox.png "RadioButton denetimi seçili Araç Kutusu penceresinin ekran görüntüsü")

1. RadioButton öğesini seçip tasarım yüzeyindeki pencereye sürükleyerek tasarım yüzeyine iki **RadioButton** denetimi ekleyin. Düğmeleri (seçerek ve ok tuşlarını kullanarak) metin bloğu denetimialtında düğmelerin yan yana görünmesi için taşıyın. Denetimleri hizalamak için kırmızı yönergeleri kullanın.

   Pencerenizin şuna benzemesi gerekir:

   ![TextBlock ve iki radyo düğmesi ile selamlama formu](../media/exploreide-greetingswithradiobuttons.png "TextBlock ve iki radyo düğmesi ile Selamlar formunun ekran görüntüsü")

1. Sol RadioButton denetimi için **Özellikler** penceresinde Ad **özelliğini** **(Özellikler** penceresinin üst kısmındaki özellik) `HelloButton`değiştirin.

    ![RadioButton özellikleri penceresi](../media/exploreide-buttonproperties.png "RadioButton özellikleri penceresinin ekran görüntüsü")

1. Doğru RadioButton denetimi için **Özellikler** penceresinde, **Ad** `GoodbyeButton`özelliğini '' olarak değiştirin ve değişikliklerinizi kaydedin.

Ardından, her RadioButton denetimi için görüntü metni eklersiniz. Aşağıdaki yordam, RadioButton denetimi için **İçerik** özelliğini güncelleştirir.

### <a name="add-display-text-for-each-radio-button"></a>Her radyo düğmesi için görüntü metni ekleme

1. XAML için `HelloButton` `GoodbyeButton` `"Hello"` ve `"Goodbye"` XAML'de **İçerik** özniteliğini güncelleştirin. XAML biçimlendirmesi şimdi aşağıdaki örneğe benzer olmalıdır:

   ```xaml
   <Grid>
        <TextBlock HorizontalAlignment="Left" Margin="252,47,0,0" TextWrapping="Wrap" Text="Select a message option and then choose the Display button." VerticalAlignment="Top"/>
        <RadioButton x:Name="HelloButton" Content="Hello" HorizontalAlignment="Left" Margin="297,161,0,0" VerticalAlignment="Top"/>
        <RadioButton x:Name="GoodbyeButton" Content="Goodbye" HorizontalAlignment="Left" Margin="488,161,0,0" VerticalAlignment="Top"/>
   </Grid>
   ```

### <a name="set-a-radio-button-to-be-checked-by-default"></a>Varsayılan olarak denetlenecek bir radyo düğmesi ayarlama

Bu adımda, HelloButton'u varsayılan olarak denetlenecek şekilde ayarlayacağız, böylece iki radyo düğmesinden biri her zaman seçilir.

1. XAML görünümünde HelloButton için biçimlendirmeyi bulun.

1. **IsChecked** özniteliği ekleyin ve **True**olarak ayarlayın. Özellikle, `IsChecked="True"`ekleyin.

   XAML biçimlendirmesi şimdi aşağıdaki örneğe benzer olmalıdır:

   ```xaml
   <Grid>
        <TextBlock HorizontalAlignment="Left" Margin="252,47,0,0" TextWrapping="Wrap" Text="Select a message option and then choose the Display button." VerticalAlignment="Top"/>
        <RadioButton x:Name="HelloButton" Content="Hello" IsChecked="True" HorizontalAlignment="Left" Margin="297,161,0,0" VerticalAlignment="Top"/>
        <RadioButton x:Name="GoodbyeButton" Content="Goodbye" HorizontalAlignment="Left" Margin="488,161,0,0" VerticalAlignment="Top"/>
   </Grid>
   ```

Ekleyeceğiniz son UI öğesi bir [Düğme](/dotnet/framework/wpf/controls/button) denetimidir.

### <a name="add-the-button-control"></a>Düğme denetimini ekleme

1. Araç **Kutusunda,** **Düğme** denetimini bulun ve ardından tasarım görünümündeki forma sürükleyerek RadioButton denetimleri altındaki tasarım yüzeyine ekleyin. Visual Studio 2019 veya sonraki bir tarihte kullanıyorsanız, kırmızı bir çizgi denetimi ortalamanıza yardımcı olur.

1. XAML görünümünde, Düğme denetimi `Content="Button"` `Content="Display"`için **İçeriğin** değerini değiştirin ve değişiklikleri kaydedin.

     Pencereniz aşağıdaki gösterime benzemelidir.

     ![Denetim etiketleri ile selamlama formu](media/exploreide-greetingswithcontrollabels-cs.png "Denetim etiketleri ile Selamlar formunun ekran görüntüsü")

   XAML biçimlendirmesi şimdi aşağıdaki örneğe benzer olmalıdır:

   ```xaml
   <Grid>
        <TextBlock HorizontalAlignment="Left" Margin="252,47,0,0" TextWrapping="Wrap" Text="Select a message option and then choose the Display button." VerticalAlignment="Top"/>
        <RadioButton x:Name="HelloButton" Content="Hello" IsChecked="True" HorizontalAlignment="Left" Margin="297,161,0,0" VerticalAlignment="Top"/>
        <RadioButton x:Name="GoodbyeButton" Content="Goodbye" HorizontalAlignment="Left" Margin="488,161,0,0" VerticalAlignment="Top"/>
        <Button Content="Display" HorizontalAlignment="Left" Margin="377,270,0,0" VerticalAlignment="Top" Width="75"/>
   </Grid>
   ```

### <a name="add-code-to-the-display-button"></a>Ekran düğmesine kod ekleme

Bu uygulama çalıştığında, kullanıcı bir radyo düğmesini seçtikten sonra bir ileti kutusu görüntülenir ve **ardından Ekran** düğmesini seçer. Merhaba için bir ileti kutusu ve Güle Güle için bir diğer ileti kutusu görünecektir. Bu davranışı oluşturmak için, `Button_Click` *Greetings.xaml.cs'da*olaya kod eklersiniz.

1. Tasarım **yüzeyinde, Görüntüle** düğmesini çift tıklatın.

     *Greetings.xaml.cs,* `Button_Click` olayimleç ile açılır.

    ```csharp
    private void Button_Click(object sender, RoutedEventArgs e)
    {

    }
    ```

1. Aşağıdaki kodu girin:

    ```csharp
    if (HelloButton.IsChecked == true)
    {
         MessageBox.Show("Hello.");
    }
    else if (GoodbyeButton.IsChecked == true)
    {
        MessageBox.Show("Goodbye.");
    }
    ```

1. Uygulamayı kaydedin.

## <a name="debug-and-test-the-application"></a>Uygulamanın hatalarını ayıklama ve test etme

Ardından, hataları aramak ve her iki ileti kutusunun da doğru görünmesini test etmek için uygulamayı hata ayıklamanız olur. Aşağıdaki yönergeler, hata ayıklamanın nasıl oluşturup başlatacağınız hakkında bilgi verebolur, ancak daha sonra daha fazla bilgi için [WPF uygulaması oluştur (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf) ve [Hata Ayıklama WPF'yi](../../debugger/debugging-wpf.md) okuyabilirsiniz.

### <a name="find-and-fix-errors"></a>Hataları bulma ve düzeltme

Bu adımda, *MainWindow.xaml* dosyasının adını değiştirerek daha önce neden olduğumuz hatayı bulacaksınız.

#### <a name="start-debugging-and-find-the-error"></a>Hata ayıklamayı başlatın ve hatayı bulun

1. Hata ayıklayıcıyı **F5** tuşuna basarak veya **Hata Ayıklama'yı**seçerek başlatın, ardından Hata **Ayıklamaya Başlayın.**

   **Kesme Modu** penceresi görüntülenir ve **Çıktı** penceresi bir IOException oluştuğunu gösterir: kaynak 'mainwindow.xaml' bulamıyor.

   ![IOException iletisi](../media/exploreide-ioexception.png "IOException iletisinin ekran görüntüsü")

1. Hata**Ayıklama'yı Durdurun Hata Ayıklama'yı** **Debug** > seçerek hata ayıklamayı durdurun.

Bu öğreticinin başında *MainWindow.xaml* adını *Greetings.xaml* olarak yeniden adlandırdık, ancak kod yine de uygulama için başlangıç URI olarak *MainWindow.xaml'a* başvuruyor, bu nedenle proje başlatılamayamaz.

#### <a name="specify-greetingsxaml-as-the-startup-uri"></a>Başlangıç URI olarak Greetings.xaml belirtin

1. **Solution Explorer'da** *App.xaml* dosyasını açın.

1. `StartupUri="MainWindow.xaml"` 'ye `StartupUri="Greetings.xaml"`değiştirin ve değişiklikleri kaydedin.

Hata ayıklamayı yeniden başlatın **(F5**tuşuna basın). Uygulamanın **Selamlar** penceresini görmeniz gerekir.

::: moniker range="vs-2017"
![Çalışan uygulamanın ekran görüntüsü](media/exploreide-wpf-running-app.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Çalışan uygulamanın ekran görüntüsü](media/vs-2019/exploreide-wpf-running-app.png)
::: moniker-end

Hata ayıklamayı durdurmak için uygulama penceresini kapatın.

### <a name="debug-with-breakpoints"></a>Kesme noktaları yla hata ayıklama

Bazı kesme noktaları ekleyerek hata ayıklama sırasında kodu sınayabilirsiniz. **Hata Ayıklama** > **Geçiş Noktası'nı**seçerek kesme noktaları ekleyebilirsiniz , yazı düzenleyicisinin sol kenar boşluğuna tıklayarak, sonunun oluşmasını istediğiniz kod satırının yanındaki kenar boşluğuna tıklayarak veya **F9**tuşuna basarak .

#### <a name="add-breakpoints"></a>Kesme noktaları ekleme

1. *Greetings.xaml.cs*açın ve aşağıdaki satırı seçin:`MessageBox.Show("Hello.")`

1. **Hata**Ayıklama'yı seçerek menüden bir kesme noktası ekleyin, ardından Kesme **Noktasını Toggle.**

     Düzenleyici penceresinin en sol kenar boşluğunda, kod satırının yanında kırmızı bir daire görünür.

1. Aşağıdaki satırı seçin: `MessageBox.Show("Goodbye.")`.

1. Kesme noktası eklemek için **F9** tuşuna basın ve hata ayıklamaya başlamak için **F5** tuşuna basın.

1. **Selamlar** penceresinde **Merhaba** radyo düğmesini seçin ve ardından **Görüntüle** düğmesini seçin.

    Çizgi `MessageBox.Show("Hello.")` sarı ile vurgulanır. IDE'nin alt kısmında, Otomatikler, Yerel ler ve İzle pencereleri sol tarafta birbirine kenetlenir ve Arama Yığını, Kesme Noktaları, Özel Durum Ayarları, Komut, Hemen ve Çıkış pencereleri sağ tarafta birbirine kenetlenir.

    ![Hata ayıklamadaki kesme noktası](media/exploreide-debugbreakpoint.png "Hata ayıklamadaki kesme noktasının ekran görüntüsü")

1. Menü çubuğunda **Hata Ayıklama** > **Adım ını**seçin.

     Uygulama yürütmedevam eder ve "Merhaba" sözcüğü içeren bir ileti kutusu görüntülenir.

1. Kapatmak için ileti kutusundaki **Tamam** düğmesini seçin.

1. **Selamlar** **penceresinde, Hoşçakal** radyo düğmesini seçin ve ardından **Görüntüle** düğmesini seçin.

     Çizgi `MessageBox.Show("Goodbye.")` sarı ile vurgulanır.

1. Hata ayıklama devam etmek için **F5** tuşunu seçin. İleti kutusu göründüğünde, kapatmak için ileti kutusundaki **Tamam** düğmesini seçin.

1. Hata ayıklamayı durdurmak için uygulama penceresini kapatın.

1. Menü çubuğunda, Hata **Ayıklama** > **Tüm Kesme Noktalarını**Devre Dışı Bırakmayı seçin.

### <a name="view-a-representation-of-the-ui-elements"></a>UI öğelerinin temsilini görüntüleyin

Çalışan uygulamada, pencerenizin üst kısmında görünen bir widget görmeniz gerekir. Bu, bazı yararlı hata ayıklama özelliklerine hızlı erişim sağlayan bir çalışma zamanı yardımcısıdır. İlk düğmeye tıklayın, **Canlı Görsel Ağaç gidin.** Sayfanızın tüm görsel öğelerini içeren bir ağaç içeren bir pencere görmeniz gerekir. Eklediğiniz düğmeleri bulmak için düğümleri genişletin.

![Canlı Görsel Ağaç penceresinin ekran görüntüsü](media/vs-2019/exploreide-live-visual-tree.png)

### <a name="build-a-release-version-of-the-application"></a>Uygulamanın yayın sürümünü oluşturma

Artık her şeyin işe yaradığını doğruladığınıziçin, uygulamanın bir sürüm oluşturma sını hazırlayabilirsiniz.

1. Ana menüde, önceki yapılarsırasında oluşturulan ara dosyaları ve çıktı dosyalarını silmek için**Temizle çözümünü** **oluştur'u** > seçin. Bu gerekli değildir, ancak hata ayıklama yapı çıktılarını temizler.

1. HelloWPFApp'ın yapı yapılandırmasını araç çubuğundaki açılır bırakma denetimini kullanarak **Hata Ayıklama'dan** **Release'e** değiştirin (şu anda "Hata Ayıklama" yazıyor).

1. **Build Build** > **Solution'ı**seçerek çözümü oluşturun.

Bu öğretici tamamladıktan sonra tebrikler! Çözüm ve proje dizini altında oluşturduğunuz *.exe'yi* *(...\HelloWPFApp\HelloWPFApp\bin\Release)* bulabilirsiniz.

## <a name="next-steps"></a>Sonraki adımlar

Bu öğretici tamamladıktan sonra tebrikler! Daha fazla bilgi edinmek için aşağıdaki öğreticilere devam edin.

> [!div class="nextstepaction"]
> [Daha fazla WPF öğreticisiyle devam edin](/dotnet/framework/wpf/getting-started/wpf-walkthroughs/)

## <a name="see-also"></a>Ayrıca bkz.

- [Üretkenlik ipuçları](../../ide/productivity-features.md)
