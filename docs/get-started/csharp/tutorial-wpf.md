---
title: İçinde WPF ile uygulama Merhaba DünyaC#
description: Windows Presentation Foundation (WPF) Kullanıcı arabirimi çerçevesini kullanarak C# Visual Studio ile basit bir Windows Masaüstü .NET uygulaması oluşturun.
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
ms.sourcegitcommit: 2ae2436dc3484b9dfa10e0483afba1e5a02a52eb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/25/2020
ms.locfileid: "77579984"
---
# <a name="tutorial-create-a-simple-application-with-c"></a>Öğretici: C\# ile basit bir uygulama oluşturma

Bu öğreticiyi tamamlayarak, Visual Studio ile uygulama geliştirirken kullanabileceğiniz birçok araç, iletişim kutusu ve tasarımcı hakkında bilgi sahibi olacaksınız. Tümleşik geliştirme ortamında ([IDE](visual-studio-ide.md)) çalışmayı öğrenirken, "Merhaba, Dünya" uygulaması, Kullanıcı arabirimini tasarlayacağınız, kod ekleyerek ve hata ayıkladığınızda bir "Hello, World" uygulaması oluşturacaksınız.

## <a name="prerequisites"></a>Önkoşullar

::: moniker range="vs-2017"
Visual Studio 'Yu henüz yüklemediyseniz, [Visual Studio İndirmeleri](https://visualstudio.microsoft.com/vs/older-downloads/?) sayfasına giderek ücretsiz olarak yükleme yapın.
::: moniker-end
::: moniker range=">=vs-2019"

- Visual Studio 'Yu henüz yüklemediyseniz, [Visual Studio İndirmeleri](https://visualstudio.microsoft.com/downloads/) sayfasına giderek ücretsiz olarak yükleme yapın.
- Bu öğretici için .NET Framework ya da .NET Core kullanabilirsiniz. .NET Core, daha yeni ve modern bir çerçevedir. .NET Core, Visual Studio 2019 sürüm 16,3 veya üstünü gerektirir.
::: moniker-end

## <a name="configure-the-ide"></a>{1&gt;IDE'yi yapılandırma&lt;1}

::: moniker range="vs-2017"

Visual Studio 'Yu ilk kez açtığınızda, oturum açmanız istenir. Bu adım, bu öğretici için isteğe bağlıdır. Ardından, geliştirme ayarlarınızı ve renk temasını seçmenizi isteyen bir iletişim kutusu görüntülenebilir. Varsayılanları koruyun ve **Visual Studio 'Yu Başlat**' ı seçin.

![Ayarları Seç iletişim kutusu](../media/exploreide-settings.png)

Visual Studio başlatıldıktan sonra araç pencerelerini, menüleri ve araç çubuklarını ve ana pencere alanını görürsünüz. Araç pencereleri, **Hızlı Başlat**, menü çubuğu ve en üstteki Standart araç çubuğu ile uygulama penceresinin sol ve sağ taraflarına yerleştirilir. Uygulama penceresinin merkezinde **Başlangıç sayfası**bulunur. Bir çözüm veya proje yüklediğinizde, düzenleyiciler ve tasarımcılar **Başlangıç sayfasının** bulunduğu alanda görüntülenir. Bir uygulama geliştirirken, bu merkezi alanda zamanınızın çoğunu harcarcaksınız.

![Genel ayarlar uygulanmış şekilde Visual Studio 2017 IDE](../media/exploreide-idewithgeneralsettings.png "Genel ayarların uygulanmış olduğu Visual Studio 2017 IDE ekran görüntüsü")

::: moniker-end

::: moniker range=">=vs-2019"

Visual Studio 'Yu başlattığınızda ilk olarak başlangıç penceresi açılır. Geliştirme ortamını açmak için **kod olmadan devam et** ' i seçin. Araç pencerelerini, menüleri ve araç çubuklarını ve ana pencere alanını görürsünüz. Araç pencereleri, uygulama penceresinin sol ve sağ taraflarından, bir arama kutusuyla, menü çubuğundan ve en üstteki Standart araç çubuğundan yerleştirildi. Bir çözüm veya proje yüklediğinizde, düzenleyiciler ve tasarımcılar uygulama penceresinin orta alanında görüntülenir. Bir uygulama geliştirirken, bu merkezi alanda zamanınızın çoğunu harcarcaksınız.

::: moniker-end

## <a name="create-the-project"></a>Proje oluşturma

Visual Studio'da bir uygulama oluştururken önce bir proje ve bir çözüm oluşturursunuz. Bu örnekte, bir Windows Presentation Foundation (WPF) projesi oluşturacaksınız.

::: moniker range="vs-2017"

1. Yeni bir proje oluşturma. Menü çubuğunda **dosya** > **Yeni** > **projesi**' ni seçin.

     ![Menü çubuğunda dosya, yeni, proje ' yi seçin.](../media/exploreide-filenewproject.png "Dosya, yeni, proje ' yi seçtiğiniz menü çubuğunun ekran görüntüsü")

1. **Yeni proje** iletişim kutusunda, **yüklü** > **Visual C#**  > **Windows Masaüstü** kategorisini seçin ve ardından **WPF uygulaması (.NET Framework)** şablonunu seçin. Projeyi **HelloWPFApp**olarak adlandırın ve **Tamam**' ı seçin.

     ![Visual Studio 'da WPF uygulama şablonu yeni proje iletişim kutusu](media/exploreide-newprojectcsharp.png "Yeni proje iletişim kutusunda WPF uygulama şablonunun ekran görüntüsü")

::: moniker-end

::: moniker range="vs-2019"

1. Visual Studio 2019 ' i açın.

1. Başlangıç penceresinde **Yeni proje oluştur**' u seçin.

   ![' Yeni proje oluştur ' penceresini görüntüleyin](../../get-started/media/vs-2019/start-window-create-new-project.png "' Yeni proje oluştur ' penceresinin ekran görüntüsü")

1. **Yeni proje oluştur** ekranında, "WPF" araması yapın **WPF uygulaması (.NET Core)** öğesini seçin ve ardından **İleri**' yi seçin.

   ![' Yeni proje oluştur ' iletişim kutusunda WPF uygulama şablonu](media/vs-2019/exploreide-newprojectcsharp-vs2019.png "' Yeni proje oluştur ' iletişim kutusunda WPF uygulama şablonunun ekran görüntüsü")

   > [!NOTE]
   > Biri .NET Framework ve diğeri .NET Core için olmak üzere iki WPF Masaüstü şablonu bulabilirsiniz. .NET Core şablonu, Visual Studio 2019 sürüm 16,3 ve sonraki sürümlerinde kullanılabilir. Bu öğretici için bunlardan birini kullanabilirsiniz, ancak yeni geliştirme için .NET Core önerilir.

1. Sonraki ekranda, projeye **HelloWPFApp**adını verin ve **Oluştur**' u seçin.

   ![Projenizin ' HelloWPFApp ' olarak adlandırın](./media/vs-2019/exploreide-nameproject.png "Projenizin adını girdiğiniz pencerenin ekran görüntüsü")

::: moniker-end

Visual Studio HelloWPFApp projesini ve çözümünü oluşturur ve **Çözüm Gezgini** çeşitli dosyaları gösterir. **WPF Tasarımcısı** , bölünmüş bir görünümde *MainWindow. xaml* ' in BIR Tasarım görünümünü ve XAML görünümünü gösterir. Herhangi bir görünümden daha fazla veya daha az görünmesi için Bölümlendirici slaytı gösterebilirsiniz. Yalnızca görsel görünümü veya yalnızca XAML görünümünü görmeyi seçebilirsiniz.

![IDE 'de WPF projesi ve çözümü](media/exploreide-wpfproject-cs.png "IDE 'deki WPF projesi ve çözümünün ekran görüntüsü")

> [!NOTE]
> XAML (Genişletilebilir uygulama biçimlendirme dili) hakkında daha fazla bilgi için bkz. [WPF Için xaml genel bakış](/dotnet/framework/wpf/advanced/xaml-overview-wpf) sayfası.

Projeyi oluşturduktan sonra özelleştirebilirsiniz. Bunu yapmak için, **Görünüm** menüsünden **Özellikler penceresi** ' ni seçin veya **F4**tuşuna basın. Daha sonra, bir uygulamadaki proje öğeleri, denetimler ve diğer öğeler için seçenekleri görüntüleyebilir ve değiştirebilirsiniz.

   ![Özellikler penceresi](../media/exploreide-hellowpfappfiles.png "WPF dosya uygulama adlarıyla Özellikler penceresi ekran görüntüsü")   

### <a name="change-the-name-of-mainwindowxaml"></a>MainWindow. xaml adını değiştirme

Şimdi, MainWindow 'e daha özel bir ad verelim. **Çözüm Gezgini**, *MainWindow. xaml* ' e sağ tıklayıp **Yeniden Adlandır**' ı seçin. Dosyayı *Greetings. xaml*olarak yeniden adlandırın.

## <a name="design-the-user-interface-ui"></a>Kullanıcı arabirimini (UI) tasarlama

Tasarımcı açık değilse, *Greetings. xaml* ' i seçin ve tasarımcıyı açmak için **SHIFT**+**F7** tuşuna basın.

Bu uygulamaya üç tür denetim ekleyeceğiz: bir <xref:System.Windows.Controls.TextBlock> denetimi, iki <xref:System.Windows.Controls.RadioButton> denetimi ve bir <xref:System.Windows.Controls.Button> denetimi.

### <a name="add-a-textblock-control"></a>TextBlock denetimi ekleme

1. **Ctrl**+**Q** tuşlarına basarak arama kutusunu etkinleştirin ve **araç kutusu**yazın. Sonuçlar listesinden **> araç kutusunu görüntüle** ' yi seçin.

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

1. XAML görünümünde **TextBlock** için biçimlendirmeyi bulun ve **metin** özniteliğini `TextBox` `Select a message option and then choose the Display button.` olarak değiştirin

   XAML işaretlemesi aşağıdaki örnekteki gibi görünmelidir:

   ```xaml
   <Grid>
       <TextBlock HorizontalAlignment="Left" Margin="387,60,0,0" TextWrapping="Wrap" Text="Select a message option and then choose the Display button." VerticalAlignment="Top"/>
   </Grid>
   ```

1. Gerekirse, daha sonra **CTRL + S** tuşlarına basarak veya **Dosya** menü öğesini kullanarak değişikliklerinizi yeniden ortalayın.

Ardından, forma iki [RadioButton](/dotnet/framework/wpf/controls/radiobutton) denetimi ekleyeceksiniz.

### <a name="add-radio-buttons"></a>Radyo düğmeleri ekleme

1. **Araç kutusunda** **RadioButton** denetimini bulun.

     ![RadioButton denetimi seçiliyken araç kutusu penceresi](../media/exploreide-radiobuttontoolbox.png "RadioButton denetimi seçiliyken araç kutusu penceresinin ekran görüntüsü")

1. **RadioButton** öğesini seçerek ve tasarım yüzeyinde pencereye sürükleyerek tasarım yüzeyine iki RadioButton denetimi ekleyin. Düğmeleri TextBlock denetimi altında yan yana görünecek şekilde düğmeleri (onları seçerek ve ok tuşlarını kullanarak) taşıyın. Denetimleri hizalamak için kırmızı yönergeleri kullanın.

   Pencerenizin şuna benzemesi gerekir:

   ![TextBlock ve iki radyo düğmesi içeren Tebrikler formu](../media/exploreide-greetingswithradiobuttons.png "TextBlock ve iki radyo düğmesi ile Greetings formunun ekran görüntüsü")

1. Sol RadioButton denetimi için **Özellikler** penceresinde, **ad** özelliğini ( **Özellikler** penceresinin üst kısmındaki özellik) `HelloButton`olarak değiştirin.

    ![RadioButton Özellikler penceresi](../media/exploreide-buttonproperties.png "RadioButton Özellikleri penceresinin ekran görüntüsü")

1. Sağ RadioButton denetimi için **Özellikler** penceresinde, **ad** özelliğini `GoodbyeButton`olarak değiştirin ve ardından değişikliklerinizi kaydedin.

Ardından, her RadioButton denetimi için görüntü metni ekleyeceksiniz. Aşağıdaki yordam bir RadioButton denetimi için **içerik** özelliğini güncelleştirir.

### <a name="add-display-text-for-each-radio-button"></a>Her radyo düğmesi için görüntü metni Ekle

1. `HelloButton` için **içerik** özniteliğini GÜNCELLEŞTIRIN ve XAML 'de `"Hello"` ve `"Goodbye"` `GoodbyeButton`. XAML işaretlemesi artık aşağıdaki örneğe benzer şekilde görünmelidir:

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

1. Bir **IsChecked** özniteliği ekleyin ve bunu **true**olarak ayarlayın. Özellikle `IsChecked="True"`ekleyin.

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

1. XAML görünümünde, düğme denetimi için **içerik** değerini `Content="Display"``Content="Button"` değiştirin ve sonra değişiklikleri kaydedin.

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

Bu uygulama çalıştığında, bir Kullanıcı radyo düğmesini seçtikten sonra **görüntüle** düğmesini seçtiğinde bir ileti kutusu görünür. Merhaba için bir ileti kutusu ve Güle Güle için bir diğer ileti kutusu görünecektir. Bu davranışı oluşturmak için, *Greetings.xaml.cs*içinde `Button_Click` olayına kod ekleyeceksiniz.

1. Tasarım yüzeyinde **görüntüle** düğmesine çift tıklayın.

     *Greetings.xaml.cs* , imleç `Button_Click` olayında açılır.

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

1. Hata ayıklamayı **durdurmak > hata** **ayıklamayı**Durdur seçeneğini belirleyerek durdurun.

Bu öğreticinin başlangıcında *MainWindow. xaml* ' i *Greetings. xaml* olarak yeniden adlandırdık, ancak kod yine de uygulama için başlangıç URI 'si olarak *MainWindow. xaml* 'e başvuruyor, bu nedenle proje başlatılamıyor.

#### <a name="specify-greetingsxaml-as-the-startup-uri"></a>Başlangıç URI 'SI olarak Greetings. xaml belirtin

1. **Çözüm Gezgini**' de *app. xaml* dosyasını açın.

1. `StartupUri="MainWindow.xaml"` `StartupUri="Greetings.xaml"`olarak değiştirin ve değişiklikleri kaydedin.

Hata ayıklayıcıyı yeniden başlatın ( **F5**tuşuna basın). Uygulamanın **Greetings** penceresini görmeniz gerekir.

::: moniker range="vs-2017"
![Çalışan uygulamanın ekran görüntüsü](media/exploreide-wpf-running-app.png)
::: moniker-end
::: moniker range=">=vs-2019"
![Çalışan uygulamanın ekran görüntüsü](media/vs-2019/exploreide-wpf-running-app.png)
::: moniker-end

Hata ayıklamayı durdurmak için şimdi uygulama penceresini kapatın.

### <a name="debug-with-breakpoints"></a>Kesme noktalarıyla hata ayıkla

Hata ayıklama sırasında bazı kesme noktaları ekleyerek kodu test edebilirsiniz. Kesme noktası ** > '** yi seçerek kesme noktası ' nı seçerek kesme noktası ' nı seçin ve kesmenin gerçekleşmesini istediğiniz kod satırının yanındaki düzenleyicinin sol kenar boşluğuna tıklayarak veya **F9**tuşuna basarak kesme **noktası**ekleyebilirsiniz.

#### <a name="add-breakpoints"></a>Kesme noktaları Ekle

1. *Greetings.xaml.cs*açın ve aşağıdaki satırı seçin: `MessageBox.Show("Hello.")`

1. Menüden **Hata Ayıkla**' yı ve ardından **kesme noktasını aç**' ı seçerek bir kesme noktası ekleyin.

     Düzenleyici penceresinin en sol kenar boşluğunda, kod satırının yanında kırmızı bir daire görünür.

1. Aşağıdaki satırı seçin: `MessageBox.Show("Goodbye.")`.

1. Bir kesme noktası eklemek için **F9** tuşuna basın ve sonra hata ayıklamayı başlatmak için **F5** 'e basın.

1. **Tebrikler** penceresinde, **Merhaba** radyo düğmesini seçin ve ardından **görüntüle** düğmesini seçin.

    Satır `MessageBox.Show("Hello.")` sarı renkle vurgulanır. IDE 'nin en altında, oto, Yereller ve Watch pencereleri, sol tarafa birlikte yerleştirilir ve çağrı yığını, kesme noktaları, özel durum ayarları, komut, anlık ve çıkış pencereleri sağ tarafta birlikte yerleştirilir.

    ![Hata ayıklayıcıda kesme noktası](media/exploreide-debugbreakpoint.png "Hata ayıklayıcıda kesme noktası ekran görüntüsü")

1. Menü çubuğunda **hata ayıkla** > **Step Out**' ı seçin.

     Uygulama yürütmeyi sürdürür ve "Hello" sözcüğünü içeren bir ileti kutusu görünür.

1. İletiyi kapatmak için ileti kutusunda **Tamam** düğmesini seçin.

1. **Tebrikler** penceresinde, **güle** radyo düğmesini seçin ve ardından **görüntüle** düğmesini seçin.

     Satır `MessageBox.Show("Goodbye.")` sarı renkle vurgulanır.

1. Hata ayıklamaya devam etmek için **F5** tuşunu seçin. İleti kutusu göründüğünde kapatmak için ileti kutusunda **Tamam** düğmesini seçin.

1. Hata ayıklamayı durdurmak için uygulama penceresini kapatın.

1. Menü çubuğunda, **hata ayıkla** > **tüm kesme noktalarını devre dışı bırak**' ı seçin.

### <a name="view-a-representation-of-the-ui-elements"></a>UI öğelerinin gösterimini görüntüleme

Çalışan uygulamada, pencerenizin en üstünde görüntülenen bir pencere öğesi görmeniz gerekir. Bu, bazı yararlı hata ayıklama özelliklerine hızlı erişim sağlayan bir çalışma zamanı yardımcıdır. İlk düğmesine tıklayın, **canlı görsel ağaç**' a gidin. Sayfanızın tüm görsel öğelerini içeren bir ağacı olan bir pencere görmeniz gerekir. Eklediğiniz düğmeleri bulmak için düğümleri genişletin.

![Canlı görsel ağaç penceresinin ekran görüntüsü](media/vs-2019/exploreide-live-visual-tree.png)

### <a name="build-a-release-version-of-the-application"></a>Uygulamanın yayın sürümünü oluşturma

Her şeyin çalıştığını doğruladığınıza göre uygulamanın bir yayın derlemesini hazırlayabilirsiniz.

1. Ana menüde, önceki derlemeler sırasında oluşturulan ara dosyaları ve çıktı dosyalarını silmek için **oluştur** > **Çözümü Temizle** ' yi seçin. Bu gerekli değildir, ancak hata ayıklama oluşturma çıkışlarını temizler.

1. Araç çubuğundaki DropDown denetimini kullanarak HelloWPFApp için derleme yapılandırmasını **hata ayıklamadan** **Yayınla** değiştirin (Şu anda "hata ayıkla" ifadesini alır).

1. **Build > ** **Build Solution**öğesini seçerek çözümü oluşturun.

Bu öğreticiyi tamamlamak Tebrikler! Çözümünüz ve proje dizininiz ( *. ..\Hellowpfapp\hellowpfapp\bin\release*) altında oluşturduğunuz *. exe dosyasını* bulabilirsiniz.

## <a name="next-steps"></a>Sonraki adımlar

Bu öğreticiyi tamamlamak Tebrikler! Daha da fazla bilgi edinmek için aşağıdaki öğreticilerle devam edin.

> [!div class="nextstepaction"]
> [Daha fazla WPF öğreticiyle devam edin](/dotnet/framework/wpf/getting-started/wpf-walkthroughs/)

## <a name="see-also"></a>Ayrıca bkz.

- [Üretkenlik ipuçları](../../ide/productivity-features.md)
