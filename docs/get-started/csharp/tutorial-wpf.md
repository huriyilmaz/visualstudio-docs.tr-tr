---
title: "C 'de WPF ile uygulama Merhaba Dünya #"
description: C# ' de Windows Presentation Foundation (WPF) kullanıcı arabirimi çerçevesini kullanarak Visual Studio basit bir Windows masaüstü .net uygulaması oluşturun.
ms.custom: vs-acquisition, get-started
ms.date: 02/10/2021
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.topic: tutorial
dev_langs:
- CSharp
ms.assetid: f84339c7-d617-4f56-bfcd-af2215c347ba
author: anandmeg
ms.author: meghaanand
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 9f9de66433b9795df31ea708f54012bcf8818538
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122144255"
---
# <a name="tutorial-create-a-simple-application-with-c"></a>Öğretici: C ile basit bir uygulama oluşturma\#

Bu öğreticiyi tamamlayarak, Visual Studio ile uygulama geliştirirken kullanabileceğiniz birçok araç, iletişim kutusu ve tasarımcı hakkında bilgi sahibi olacaksınız. Tümleşik geliştirme ortamında ([IDE](visual-studio-ide.md)) çalışmayı öğrenirken, "Merhaba, Dünya" uygulaması, Kullanıcı arabirimini tasarlayacağınız, kod ekleyerek ve hata ayıkladığınızda bir "Hello, World" uygulaması oluşturacaksınız.

## <a name="prerequisites"></a>Önkoşullar

::: moniker range="vs-2017"
Visual Studio henüz yüklemediyseniz, [Visual Studio indirmeleri](https://visualstudio.microsoft.com/vs/older-downloads/?) sayfasına giderek ücretsiz yükleme yapın.
::: moniker-end
::: moniker range=">=vs-2019"

- Visual Studio henüz yüklemediyseniz, [Visual Studio indirmeleri](https://visualstudio.microsoft.com/downloads/) sayfasına giderek ücretsiz yükleme yapın.
- bu öğretici için .NET Framework ya da .net Core kullanabilirsiniz. .NET Core, daha yeni ve modern bir çerçevedir. .net Core Visual Studio 2019 sürüm 16,3 veya üstünü gerektirir.
::: moniker-end

## <a name="configure-the-ide"></a>IDE'yi yapılandırma

::: moniker range="vs-2017"

Visual Studio ilk kez açtığınızda, oturum açmanız istenir. Bu adım, bu öğretici için isteğe bağlıdır. Ardından, geliştirme ayarlarınızı ve renk temasını seçmenizi isteyen bir iletişim kutusu görüntülenebilir. Varsayılanları tutun ve **Visual Studio Başlat**' ı seçin.

![Ayarları Seç iletişim kutusu](../media/exploreide-settings.png)

Visual Studio başlatıldıktan sonra araç pencerelerini, menüleri ve araç çubuklarını ve ana pencere alanını görürsünüz. Araç pencereleri, **Hızlı Başlat**, menü çubuğu ve en üstteki Standart araç çubuğu ile uygulama penceresinin sol ve sağ taraflarına yerleştirilir. Uygulama penceresinin merkezinde **Başlangıç sayfası** bulunur. Bir çözüm veya proje yüklediğinizde, düzenleyiciler ve tasarımcılar **Başlangıç sayfasının** bulunduğu alanda görüntülenir. Bir uygulama geliştirirken, bu merkezi alanda zamanınızın çoğunu harcarcaksınız.

![genel Ayarlar uygulanmış Visual Studio 2017 ıde](../media/exploreide-idewithgeneralsettings.png "genel Ayarlar uygulanmış Visual Studio 2017 ıde ekran görüntüsü")

::: moniker-end

::: moniker range=">=vs-2019"

Visual Studio başlattığınızda ilk pencere açılır. Geliştirme ortamını açmak için **kod olmadan devam et** ' i seçin. Araç pencerelerini, menüleri ve araç çubuklarını ve ana pencere alanını görürsünüz. Araç pencereleri, uygulama penceresinin sol ve sağ taraflarından, bir arama kutusuyla, menü çubuğundan ve en üstteki Standart araç çubuğundan yerleştirildi. Bir çözüm veya proje yüklediğinizde, düzenleyiciler ve tasarımcılar uygulama penceresinin orta alanında görüntülenir. Bir uygulama geliştirirken, bu merkezi alanda zamanınızın çoğunu harcarcaksınız.

::: moniker-end

## <a name="create-the-project"></a>Proje oluşturma

Visual Studio'da bir uygulama oluştururken önce bir proje ve bir çözüm oluşturursunuz. bu örnekte, bir Windows Presentation Foundation (WPF) projesi oluşturacaksınız.

::: moniker range="vs-2017"

1. Yeni bir proje oluşturma. menü çubuğunda **dosya**  >  **yeni**  >  **Project**' yi seçin.

     ![Menü çubuğunda dosya, yeni, Project ' yi seçin.](../media/exploreide-filenewproject.png "Dosya, yeni, Project seçtiğiniz menü çubuğunun ekran görüntüsü")

1. **yeni Project** iletişim kutusunda, **yüklü**  >  **Visual C#**  >  **Windows Desktop** kategorisini seçin ve ardından **WPF uygulaması (.NET Framework)** şablonunu seçin. Projeyi **HelloWPFApp** olarak adlandırın ve **Tamam**' ı seçin.

     ![Visual Studio yeni Project iletişim kutusunda WPF uygulama şablonu](media/exploreide-newprojectcsharp.png "yeni Project iletişim kutusunda WPF uygulama şablonunun ekran görüntüsü")

::: moniker-end

::: moniker range=">=vs-2019"

1. Visual Studio'yu açın.

1. Başlangıç penceresinde **Yeni proje oluştur**' u seçin.

   ![' Yeni proje oluştur ' penceresini görüntüleyin](../../get-started/media/vs-2019/start-window-create-new-project.png "' Yeni proje oluştur ' penceresinin ekran görüntüsü")

1. **Yeni proje oluştur** ekranında, "WPF" araması yapın **WPF uygulaması**' nı seçin ve ardından **İleri**' yi seçin.

   :::image type="content" source="media/vs-2019/explore-ide-new-project-csharp-vs-2019.png" alt-text="' Yeni proje oluştur ' iletişim kutusunda WPF uygulama şablonu":::

1. Sonraki ekranda, projeye **HelloWPFApp** adını verin ve **İleri**' yi seçin.

   :::image type="content" source="./media/vs-2019/explore-ide-name-project.png" alt-text="Projenizin ' HelloWPFApp ' olarak adlandırın":::

1. **Ek bilgi** penceresinde **.NET Core 3,1** , hedef çerçeve'niz için zaten seçilmelidir. Aksi takdirde, **.NET Core 3,1**' i seçin. Ardından **Oluştur**' u seçin.

   :::image type="content" source="./media/vs-2019/wpf-target-framework.png" alt-text="' Ek bilgi ' penceresinde, .NET Core 3,1 ' ın seçili olduğundan emin olun":::

::: moniker-end

Visual Studio hellowpfapp projesini ve çözümünü oluşturur ve **Çözüm Gezgini** çeşitli dosyaları gösterir. **WPF Tasarımcısı** , bölünmüş bir görünümde *MainWindow. xaml* ' in BIR Tasarım görünümünü ve XAML görünümünü gösterir. Herhangi bir görünümden daha fazla veya daha az görünmesi için Bölümlendirici slaytı gösterebilirsiniz. Yalnızca görsel görünümü veya yalnızca XAML görünümünü görmeyi seçebilirsiniz.

![IDE 'de WPF projesi ve çözümü](media/exploreide-wpfproject-cs.png "IDE 'deki WPF projesi ve çözümünün ekran görüntüsü")

> [!NOTE]
> XAML (Genişletilebilir uygulama biçimlendirme dili) hakkında daha fazla bilgi için bkz. [WPF Için xaml genel bakış](/dotnet/framework/wpf/advanced/xaml-overview-wpf) sayfası.

Projeyi oluşturduktan sonra özelleştirebilirsiniz. Bunu yapmak için, **Görünüm** menüsünden **Özellikler penceresi** ' ni seçin veya **F4** tuşuna basın. Daha sonra, bir uygulamadaki proje öğeleri, denetimler ve diğer öğeler için seçenekleri görüntüleyebilir ve değiştirebilirsiniz.

   ![Özellik penceresi](../media/exploreide-hellowpfappfiles.png "WPF dosya uygulama adlarıyla Özellikler penceresi ekran görüntüsü")   

### <a name="change-the-name-of-mainwindowxaml"></a>MainWindow. xaml adını değiştirme

Şimdi, MainWindow 'e daha özel bir ad verelim. **Çözüm Gezgini**, *MainWindow. xaml* ' e sağ tıklayıp **Yeniden Adlandır**' ı seçin. Dosyayı *Greetings. xaml* olarak yeniden adlandırın.

## <a name="design-the-user-interface-ui"></a>Kullanıcı arabirimini (UI) tasarlama

Tasarımcı açık değilse, *Greetings. xaml* ' i seçin ve sonra  + da tasarımcıyı açmak için SHIFT **F7** tuşuna basın.

Bu uygulamaya üç tür denetim ekleyeceğiz: <xref:System.Windows.Controls.TextBlock> Denetim, iki denetim <xref:System.Windows.Controls.RadioButton> ve bir <xref:System.Windows.Controls.Button> Denetim.

### <a name="add-a-textblock-control"></a>TextBlock denetimi ekleme

1. **CTRL** + **Q** tuşlarına basarak arama kutusunu etkinleştirin ve **araç kutusu** yazın. Sonuçlar listesinden **> araç kutusunu görüntüle** ' yi seçin.

1. **Araç kutusunda**, TextBlock denetimini görmek IÇIN **ortak WPF denetimleri** düğümünü genişletin.

     ![TextBlock denetimi vurgulanmış olan araç kutusu](../media/exploreide-textblocktoolbox.png "TextBlock denetimi vurgulanmış şekilde araç kutusu penceresinin ekran görüntüsü")

1. **TextBlock** öğesini seçerek ve tasarım yüzeyinde pencereye sürükleyerek tasarım yüzeyine bir TextBlock denetimi ekleyin. Pencerenin üst kısmına yakın olan denetimi ortalayın. Visual Studio 2019 ve üzeri sürümlerde, denetimi ortalamak için kırmızı yönergeleri kullanabilirsiniz.

    Pencereniz aşağıdaki gösterime benzemelidir:

    ![Greetings formundaki TextBlock denetimi](../media/exploreide-greetingswithtextblockonly.png "Tebrikler formundaki TextBlock denetiminin ekran görüntüsü")

   XAML işaretlemesi aşağıdaki örnekteki gibi görünmelidir:

    ```xaml
    <Grid>
        <TextBlock HorizontalAlignment="Left" Margin="387,60,0,0" TextWrapping="Wrap" Text="TextBlock" VerticalAlignment="Top"/>
    </Grid>
    ```

### <a name="customize-the-text-in-the-text-block"></a>Metin bloğundaki metni özelleştirme

1. XAML görünümünde **TextBlock** için biçimlendirmeyi bulun ve **metin** özniteliğini ' den ' a değiştirin. `TextBox``Select a message option and then choose the Display button.`

   XAML işaretlemesi aşağıdaki örnekteki gibi görünmelidir:

   ```xaml
   <Grid>
       <TextBlock HorizontalAlignment="Left" Margin="387,60,0,0" TextWrapping="Wrap" Text="Select a message option and then choose the Display button." VerticalAlignment="Top"/>
   </Grid>
   ```

1. Gerekirse, daha sonra **CTRL + S** tuşlarına basarak veya **Dosya** menü öğesini kullanarak değişikliklerinizi yeniden ortalayın.

Ardından, forma iki [RadioButton](/dotnet/framework/wpf/controls/radiobutton) denetimi ekleyeceksiniz.

### <a name="add-radio-buttons"></a>Radyo düğmesi ekleme

1. **Araç kutusunda** **RadioButton** denetimini bulun.

     ![RadioButton denetimi seçiliyken araç kutusu penceresi](../media/exploreide-radiobuttontoolbox.png "RadioButton denetimi seçiliyken araç kutusu penceresinin ekran görüntüsü")

1. **RadioButton** öğesini seçerek ve tasarım yüzeyinde pencereye sürükleyerek tasarım yüzeyine iki RadioButton denetimi ekleyin. Düğmeleri TextBlock denetimi altında yan yana görünecek şekilde düğmeleri (onları seçerek ve ok tuşlarını kullanarak) taşıyın. Denetimleri hizalamak için kırmızı yönergeleri kullanın.

   Pencerenizin şuna benzemesi gerekir:

   ![TextBlock ve iki radyo düğmesi içeren Tebrikler formu](../media/exploreide-greetingswithradiobuttons.png "TextBlock ve iki radyo düğmesi ile Greetings formunun ekran görüntüsü")

1. Sol RadioButton denetimi için **Özellikler** penceresinde, **ad** özelliğini ( **Özellikler** penceresinin üst kısmındaki özellik) olarak değiştirin `HelloButton` .

    ![RadioButton Özellikler penceresi](../media/exploreide-buttonproperties.png "RadioButton Özellikleri penceresinin ekran görüntüsü")

1. Sağ RadioButton denetimi için **Özellikler** penceresinde, **ad** özelliğini olarak değiştirin `GoodbyeButton` ve ardından değişikliklerinizi kaydedin.

Ardından, her RadioButton denetimi için görüntü metni ekleyeceksiniz. Aşağıdaki yordam bir RadioButton denetimi için **içerik** özelliğini güncelleştirir.

### <a name="add-display-text-for-each-radio-button"></a>Her radyo düğmesi için görüntü metni Ekle

1. XAML içinde ve için **içerik** özniteliğini `HelloButton` güncelleştirin `GoodbyeButton` `"Hello"` `"Goodbye"` . XAML işaretlemesi artık aşağıdaki örneğe benzer şekilde görünmelidir:

   ```xaml
   <Grid>
        <TextBlock HorizontalAlignment="Left" Margin="252,47,0,0" TextWrapping="Wrap" Text="Select a message option and then choose the Display button." VerticalAlignment="Top"/>
        <RadioButton x:Name="HelloButton" Content="Hello" HorizontalAlignment="Left" Margin="297,161,0,0" VerticalAlignment="Top"/>
        <RadioButton x:Name="GoodbyeButton" Content="Goodbye" HorizontalAlignment="Left" Margin="488,161,0,0" VerticalAlignment="Top"/>
   </Grid>
   ```

### <a name="set-a-radio-button-to-be-checked-by-default"></a>Radyo düğmesini varsayılan olarak denetlenecek şekilde ayarla

Bu adımda, her zaman iki radyo düğmelerinden biri seçili olacak şekilde, Merhaba düğmesini varsayılan olarak denetlenecek şekilde ayarlayacağız.

1. XAML görünümünde, Merhaba düğmesine yönelik biçimlendirmeyi bulun.

1. Bir **IsChecked** özniteliği ekleyin ve bunu **true** olarak ayarlayın. Özellikle, ekleyin `IsChecked="True"` .

   XAML işaretlemesi artık aşağıdaki örneğe benzer şekilde görünmelidir:

   ```xaml
   <Grid>
        <TextBlock HorizontalAlignment="Left" Margin="252,47,0,0" TextWrapping="Wrap" Text="Select a message option and then choose the Display button." VerticalAlignment="Top"/>
        <RadioButton x:Name="HelloButton" Content="Hello" IsChecked="True" HorizontalAlignment="Left" Margin="297,161,0,0" VerticalAlignment="Top"/>
        <RadioButton x:Name="GoodbyeButton" Content="Goodbye" HorizontalAlignment="Left" Margin="488,161,0,0" VerticalAlignment="Top"/>
   </Grid>
   ```

Ekleyeceğiniz son UI öğesi bir [düğme](/dotnet/framework/wpf/controls/button) denetimidir.

### <a name="add-the-button-control"></a>Düğme denetimini ekleme

1. **Araç kutusunda** **düğme** denetimini bulun ve ardından Tasarım görünümündeki forma sürükleyerek RadioButton denetimlerinin altındaki tasarım yüzeyine ekleyin. Visual Studio 2019 veya sonraki bir sürümü kullanıyorsanız, kırmızı bir çizgi denetimi ortalemenize yardımcı olur.

1. XAML görünümünde düğme denetimi için **içerik** değerini `Content="Button"` olarak değiştirin `Content="Display"` ve ardından değişiklikleri kaydedin.

     Pencereniz aşağıdaki gösterime benzemelidir.

     ![Denetim etiketleriyle Greetings formu](media/exploreide-greetingswithcontrollabels-cs.png "Denetim etiketleriyle Greetings formunun ekran görüntüsü")

   XAML işaretlemesi artık aşağıdaki örneğe benzer şekilde görünmelidir:

   ```xaml
   <Grid>
        <TextBlock HorizontalAlignment="Left" Margin="252,47,0,0" TextWrapping="Wrap" Text="Select a message option and then choose the Display button." VerticalAlignment="Top"/>
        <RadioButton x:Name="HelloButton" Content="Hello" IsChecked="True" HorizontalAlignment="Left" Margin="297,161,0,0" VerticalAlignment="Top"/>
        <RadioButton x:Name="GoodbyeButton" Content="Goodbye" HorizontalAlignment="Left" Margin="488,161,0,0" VerticalAlignment="Top"/>
        <Button Content="Display" HorizontalAlignment="Left" Margin="377,270,0,0" VerticalAlignment="Top" Width="75"/>
   </Grid>
   ```

### <a name="add-code-to-the-display-button"></a>Görüntü düğmesine kod ekleme

Bu uygulama çalıştığında, bir Kullanıcı radyo düğmesini seçtikten sonra **görüntüle** düğmesini seçtiğinde bir ileti kutusu görünür. Merhaba için bir ileti kutusu ve Güle Güle için bir diğer ileti kutusu görünecektir. Bu davranışı oluşturmak için `Button_Click` *Greetings. xaml. cs* içindeki olaya kod ekleyeceksiniz.

1. Tasarım yüzeyinde **görüntüle** düğmesine çift tıklayın.

     *Greetings. xaml. cs* , olayında imleç ile açılır `Button_Click` .

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

Sonra, hataları bulmak ve her iki ileti kutusunun doğru şekilde göründüğünü sınamak için uygulamada hata ayıklaması yapacaksınız. Aşağıdaki yönergelerde hata ayıklayıcıyı nasıl derleyip başlatacağınız, ancak daha sonra daha fazla bilgi için WPF [uygulaması (WPF) oluşturma](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf) ve [WPF hata ayıklama](../../debugger/debugging-wpf.md) işlemlerini okuyabilirsiniz.

### <a name="find-and-fix-errors"></a>Hataları bulma ve düzeltme

Bu adımda, daha önce *MainWindow. xaml* dosyasının adını değiştirerek neden olduğumuz hatayı bulacaksınız.

#### <a name="start-debugging-and-find-the-error"></a>Hata ayıklamayı başlatma ve hatayı bulma

1. **F5** tuşuna basarak veya **Hata Ayıkla**' yı seçerek hata ayıklayıcıyı başlatın ve ardından **hata ayıklamayı başlatın**.

   **Kesme modu** penceresi görünür ve **Çıkış** penceresi bir IOException oluştuğunu belirtir: ' MainWindow. xaml ' kaynağı bulunamıyor.

   ![IOException iletisi](../media/exploreide-ioexception.png "IOException iletisinin ekran görüntüsü")

1. Hata ayıklamayı Durdur hata ayıklamayı **Durdur seçeneğini belirleyerek** durdurun  >  .

Bu öğreticinin başlangıcında *MainWindow. xaml* ' i *Greetings. xaml* olarak yeniden adlandırdık, ancak kod yine de uygulama için başlangıç URI 'si olarak *MainWindow. xaml* 'e başvuruyor, bu nedenle proje başlatılamıyor.

#### <a name="specify-greetingsxaml-as-the-startup-uri"></a>Başlangıç URI 'SI olarak Greetings. xaml belirtin

1. **Çözüm Gezgini**' de *app. xaml* dosyasını açın.

1. `StartupUri="MainWindow.xaml"`Olarak değiştirin `StartupUri="Greetings.xaml"` ve değişiklikleri kaydedin.

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

1. *Greetings. xaml. cs*' yi açın ve aşağıdaki satırı seçin:`MessageBox.Show(&quot;Hello.")`

1. Menüden **Hata Ayıkla**' yı ve ardından **kesme noktasını aç**' ı seçerek bir kesme noktası ekleyin.

     Düzenleyici penceresinin en sol kenar boşluğunda, kod satırının yanında kırmızı bir daire görünür.

1. Aşağıdaki satırı seçin: `MessageBox.Show("Goodbye.")` .

1. Bir kesme noktası eklemek için **F9** tuşuna basın ve sonra hata ayıklamayı başlatmak için **F5** 'e basın.

1. **Tebrikler** penceresinde, **Merhaba** radyo düğmesini seçin ve ardından **görüntüle** düğmesini seçin.

    Çizgi `MessageBox.Show("Hello.")` sarı renkle vurgulanır. ıde 'nin en altında, oto, yereller ve Watch pencereleri, sol tarafa birlikte yerleştirilir ve çağrı yığını, kesme noktaları, özel durum Ayarlar, komut, anlık ve çıkış pencereleri sağ tarafta bir araya yerleştirildi.

    ![Hata ayıklayıcıda kesme noktası](media/exploreide-debugbreakpoint.png "Hata ayıklayıcıda kesme noktası ekran görüntüsü")

1. Menü çubuğunda **Hata Ayıkla**  >  **Step Out**' ı seçin.

     Uygulama yürütmeyi sürdürür ve "Hello" sözcüğünü içeren bir ileti kutusu görünür.

1. İletiyi kapatmak için ileti kutusunda **Tamam** düğmesini seçin.

1. **Tebrikler** penceresinde, **güle** radyo düğmesini seçin ve ardından **görüntüle** düğmesini seçin.

     Çizgi `MessageBox.Show("Goodbye.")` sarı renkle vurgulanır.

1. Hata ayıklamaya devam etmek için **F5** tuşunu seçin. İleti kutusu göründüğünde kapatmak için ileti kutusunda **Tamam** düğmesini seçin.

1. Hata ayıklamayı durdurmak için uygulama penceresini kapatın.

1. Menü çubuğunda, **Hata Ayıkla**  >  **tüm kesme noktalarını devre dışı bırak**' ı seçin.

### <a name="view-a-representation-of-the-ui-elements"></a>UI öğelerinin gösterimini görüntüleme

Çalışan uygulamada, pencerenizin en üstünde görüntülenen bir pencere öğesi görmeniz gerekir. Bu, bazı yararlı hata ayıklama özelliklerine hızlı erişim sağlayan bir çalışma zamanı yardımcıdır. İlk düğmesine tıklayın, **canlı görsel ağaç**' a gidin. Sayfanızın tüm görsel öğelerini içeren bir ağacı olan bir pencere görmeniz gerekir. Eklediğiniz düğmeleri bulmak için düğümleri genişletin.

![Canlı görsel ağaç penceresinin ekran görüntüsü](media/vs-2019/exploreide-live-visual-tree.png)

### <a name="build-a-release-version-of-the-application"></a>Uygulamanın yayın sürümünü oluşturma

Her şeyin çalıştığından emin olduğunuza göre, uygulamanın yayın derlemesini hazırlayabilirsiniz.

1. Ana menüde,   >  önceki derlemeler sırasında oluşturulan ara dosyaları ve çıktı dosyalarını silmek için **temiz çözüm** oluştur ' u seçin. Bu gerekli değildir, ancak hata ayıklama oluşturma çıkışlarını temizler.

1. Araç çubuğundaki DropDown denetimini kullanarak HelloWPFApp için derleme yapılandırmasını **hata ayıklamadan** **Yayınla** değiştirin (Şu anda "hata ayıkla" ifadesini alır).

1. **Build**  >  **Build Solution** öğesini seçerek çözümü oluşturun.

Tebrikler, bu öğreticiyi tamamlama! Çözümünüz ve proje dizininiz (*. ..\Hellowpfapp\hellowpfapp\bin\release*) altında oluşturduğunuz *.exe* bulabilirsiniz.

## <a name="next-steps"></a>Sonraki adımlar

Tebrikler, bu öğreticiyi tamamlama! Daha da fazla bilgi edinmek için aşağıdaki öğreticilerle devam edin.

> [!div class="nextstepaction"]
> [Daha fazla WPF öğreticiyle devam edin](/dotnet/framework/wpf/getting-started/wpf-walkthroughs/)

## <a name="see-also"></a>Ayrıca bkz.

- [Üretkenlik ipuçları](../../ide/productivity-features.md)
