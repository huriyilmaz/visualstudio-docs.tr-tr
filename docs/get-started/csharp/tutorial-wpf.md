---
title: "Merhaba Dünya C'de WPF ile uygulama #"
description: Windows Presentation Foundation (WPF) UI çerçevesini kullanarak C# Visual Studio basit bir Windows Masaüstü .NET uygulaması oluşturun.
ms.custom: seodec18, get-started
ms.date: 02/10/2021
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.topic: tutorial
dev_langs:
- CSharp
ms.assetid: f84339c7-d617-4f56-bfcd-af2215c347ba
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: ee7b5ecc023d1319f4d7551e0e7b186d76d86741
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/17/2021
ms.locfileid: "112308486"
---
# <a name="tutorial-create-a-simple-application-with-c"></a>Öğretici: C ile basit bir uygulama oluşturma\#

Bu öğreticiyi tamamlayarak, bu öğreticiyle uygulama geliştirirken kullanabileceğiniz birçok araç, iletişim kutusu ve tasarımcı hakkında bilgi Visual Studio. Tümleşik geliştirme ortamında ([IDE)](visual-studio-ide.md)çalışma hakkında bilgi edinirken bir "Merhaba Dünya" uygulaması oluşturacak, kullanıcı arabirimini tasarlar, kod ekler ve hata ayıklarsınız.

## <a name="prerequisites"></a>Önkoşullar

::: moniker range="vs-2017"
Daha önce yüklememiş Visual Studio indirmeler [sayfasına Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?) ücretsiz olarak yükleyin.
::: moniker-end
::: moniker range=">=vs-2019"

- Daha önce yüklememiş Visual Studio indirmeler [sayfasına Visual Studio](https://visualstudio.microsoft.com/downloads/) ücretsiz olarak yükleyin.
- Bu öğretici için .NET Framework veya .NET Core kullanabilirsiniz. .NET Core, daha yeni ve daha modern bir çerçevedir. .NET Core için 2019 Visual Studio 16.3 veya sonraki bir sürümü gerekir.
::: moniker-end

## <a name="configure-the-ide"></a>IDE'yi yapılandırma

::: moniker range="vs-2017"

İlk Visual Studio için oturum açmanız istenir. Bu adım bu öğretici için isteğe bağlıdır. Ardından, geliştirme ayarlarınızı ve renk temanızı seçmenizi isteyen bir iletişim kutusu gösterebilirsiniz. Varsayılan değerleri tut ve Başlat'ı **Visual Studio.**

![Ayarları seç iletişim kutusu](../media/exploreide-settings.png)

Bu Visual Studio sonra araç pencerelerini, menüleri ve araç çubuklarını ve ana pencere boşluklarını görebilirsiniz. Araç pencereleri, uygulama penceresinin sol ve sağ kenarlarında, **Hızlı Başlat,** menü çubuğu ve standart araç çubuğu en üstte yer alan bir şekilde yerleştirildi. Uygulama penceresinin merkezinde Başlangıç Sayfası **yer almaktadır.** Bir çözümü veya projeyi yükleyebilirsiniz. Düzenleyiciler ve tasarımcılar, Başlangıç Sayfasının bulunduğu **alanda** görünür. Bir uygulama geliştirirken, zaman çoğunu bu merkezi alanda geçireceksiniz.

![Visual Studio Ayarları uygulanmış 2017 IDE](../media/exploreide-idewithgeneralsettings.png "Genel ayarların uygulanmış olduğu Visual Studio 2017 IDE ekran görüntüsü")

::: moniker-end

::: moniker range=">=vs-2019"

Uygulamayı Visual Studio önce başlangıç penceresi açılır. Geliştirme **ortamını açmak için Kod** olmadan devam'ı seçin. Araç pencerelerini, menüleri ve araç çubuklarını ve ana pencere boşluklarını görebilirsiniz. Araç pencereleri uygulama penceresinin sol ve sağ tarafına yerleştirildi. Arama kutusu, menü çubuğu ve standart araç çubuğu en üstte yer alan standart araç çubuğuyla birlikte. Bir çözümü veya projeyi yükleyemediniz mi, düzenleyiciler ve tasarımcılar uygulama penceresinin merkezi alanda görünür. Bir uygulama geliştirirken, zaman çoğunu bu merkezi alanda geçireceksiniz.

::: moniker-end

## <a name="create-the-project"></a>Proje oluşturma

Visual Studio'da bir uygulama oluştururken önce bir proje ve bir çözüm oluşturursunuz. Bu örnekte, bir Windows Presentation Foundation (WPF) projesi oluşturabilirsiniz.

::: moniker range="vs-2017"

1. Yeni bir proje oluşturma. Menü çubuğunda Dosya Yeni **Proje'yi**  >    >  **seçin.**

     ![Menü çubuğunda Dosya, Yeni, Proje'yi seçin](../media/exploreide-filenewproject.png "Dosya, yeni, proje ' yi seçtiğiniz menü çubuğunun ekran görüntüsü")

1. Yeni **Proje iletişim kutusunda** Yüklü Visual C# Windows Masaüstü kategorisini ve ardından  >    >   **WPF Uygulaması (.NET Framework) şablonunu** seçin. Projeye **HelloWPFApp adını girin ve** Tamam'ı **seçin.**

     ![Yeni Proje iletişim kutusunda Visual Studio WPF uygulama şablonu](media/exploreide-newprojectcsharp.png "Yeni proje iletişim kutusunda WPF uygulama şablonunun ekran görüntüsü")

::: moniker-end

::: moniker range=">=vs-2019"

1. Visual Studio'yu açın.

1. Başlangıç penceresinde Yeni proje **oluştur'a tıklayın.**

   !['Yeni proje oluştur' penceresini görüntüleme](../../get-started/media/vs-2019/start-window-create-new-project.png "' Yeni proje oluştur ' penceresinin ekran görüntüsü")

1. Yeni proje **oluştur ekranında** "WPF" araması, **WPF Uygulaması'nın ardından** Sonraki'yi **seçin.**

   :::image type="content" source="media/vs-2019/explore-ide-new-project-csharp-vs-2019.png" alt-text="'Yeni proje oluştur' iletişim kutusunda WPF uygulama şablonu":::

1. Sonraki ekranda projeye **HelloWPFApp** adını girin ve Sonraki'yi **seçin.**

   :::image type="content" source="./media/vs-2019/explore-ide-name-project.png" alt-text="Projenizi 'HelloWPFApp' olarak adlandır":::

1. Ek **bilgiler penceresinde** hedef **çerçeveniz için .NET Core 3.1** zaten seçilmiş olması gerekir. Yoksa **.NET Core 3.1'i seçin.** Ardından **Oluştur'a seçin.**

   :::image type="content" source="./media/vs-2019/wpf-target-framework.png" alt-text="'Ek bilgiler' penceresinde .NET Core 3.1'in seçili olduğundan emin olun":::

::: moniker-end

Visual Studio HelloWPFApp projesini ve çözümünü oluşturur **ve Çözüm Gezgini** dosyaları gösterir. **WPF Tasarımcısı,** bölünmüş görünümde *MainWindow.xaml'in* bir tasarım görünümünü ve XAML görünümünü gösterir. Görünümlerden birini daha fazla veya daha az göstermek için böleni kaydırabilirsiniz. Yalnızca görsel görünümünü veya yalnızca XAML görünümünü görüntülemeyi seçebilirsiniz.

![IDE'de WPF projesi ve çözümü](media/exploreide-wpfproject-cs.png "IDE 'deki WPF projesi ve çözümünün ekran görüntüsü")

> [!NOTE]
> XAML (eXtensible Uygulama Biçimlendirme Dili) hakkında daha fazla bilgi için WPF için [XAML'ye genel bakış sayfasına](/dotnet/framework/wpf/advanced/xaml-overview-wpf) bakın.

Projeyi oluşturduktan sonra özelleştirebilirsiniz. Bunu yapmak için Görünüm **menüsünden Özellikler Penceresi'ne** **tıklayın** veya **F4 tuşuna basın.** Ardından proje öğeleri, denetimler ve bir uygulamadaki diğer öğeler için seçenekleri görüntüp değiştirebilirsiniz.

   ![Özellik penceresi](../media/exploreide-hellowpfappfiles.png "WPF dosya uygulama adlarıyla Özellikler penceresi ekran görüntüsü")   

### <a name="change-the-name-of-mainwindowxaml"></a>MainWindow.xaml adını değiştirme

MainWindow'a daha belirli bir ad vealım. Bu **Çözüm Gezgini** *MainWindow.xaml'e* sağ tıklayın ve Yeniden Adlandır'ı **seçin.** Dosyayı *Greetings.xaml olarak yeniden adlandırır.*

## <a name="design-the-user-interface-ui"></a>Kullanıcı arabirimini (UI) tasarlama

Tasarımcı açık değilse *Greetings.xaml'i* seçin ve **Shift** + **F7** tuşuna basarak tasarımcıyı açın.

Bu uygulamaya üç denetim türü ekleyebilirsiniz: <xref:System.Windows.Controls.TextBlock> denetim, iki <xref:System.Windows.Controls.RadioButton> denetim ve <xref:System.Windows.Controls.Button> denetim.

### <a name="add-a-textblock-control"></a>TextBlock denetimi ekleme

1. Arama **kutusunu etkinleştirmek için Ctrl** + **Q** tuşlarına basın ve Araç Kutusu **yazın.** Sonuçlar **listesinden > Araç Kutusu'nı** seçin.

1. Araç **Kutusunda,** Ortak **WPF Denetimleri düğümünü genişletarak** TextBlock denetimine bakın.

     ![TextBlock denetimi vurgulanmış araç kutusu](../media/exploreide-textblocktoolbox.png "TextBlock denetimi vurgulanmış şekilde araç kutusu penceresinin ekran görüntüsü")

1. TextBlock öğesini seçerek ve tasarım yüzeyinde pencereye sürükleyerek tasarım yüzeyine bir **TextBlock** denetimi ekleyin. Denetimi pencerenin üst kısmında ortalar. 2019 Visual Studio sonraki bir yıl içinde kırmızı yönergeleri kullanarak denetimi ortalayabilirsiniz.

    Pencereniz aşağıdaki gösterime benzemelidir:

    ![Greetings formunda TextBlock denetimi](../media/exploreide-greetingswithtextblockonly.png "Tebrikler formundaki TextBlock denetiminin ekran görüntüsü")

   XAML işaretlemesi aşağıdaki örnekteki gibi gösterilsin:

    ```xaml
    <Grid>
        <TextBlock HorizontalAlignment="Left" Margin="387,60,0,0" TextWrapping="Wrap" Text="TextBlock" VerticalAlignment="Top"/>
    </Grid>
    ```

### <a name="customize-the-text-in-the-text-block"></a>Metin bloğunda metni özelleştirme

1. XAML görünümünde **TextBlock** işaretlemesini bulun ve Text **özniteliğini** olarak `TextBox` olarak değiştirme `Select a message option and then choose the Display button.`

   XAML işaretlemesi aşağıdaki örnekteki gibi gösterilsin:

   ```xaml
   <Grid>
       <TextBlock HorizontalAlignment="Left" Margin="387,60,0,0" TextWrapping="Wrap" Text="Select a message option and then choose the Display button." VerticalAlignment="Top"/>
   </Grid>
   ```

1. **Ctrl+S** tuşlarına basarak veya Dosya menü öğesini kullanarak TextBlock'un ortalarını yeniden açın ve **değişikliklerinizi** kaydedin.

Ardından forma iki [RadioButton](/dotnet/framework/wpf/controls/radiobutton) denetimi eksersiniz.

### <a name="add-radio-buttons"></a>Radyo düğmesi ekleme

1. Araç **Kutusunda** **RadioButton denetimi bulun.**

     ![RadioButton denetimi seçili araç kutusu penceresi](../media/exploreide-radiobuttontoolbox.png "RadioButton denetimi seçiliyken araç kutusu penceresinin ekran görüntüsü")

1. **RadioButton** öğesini seçerek ve tasarım yüzeyindeki pencereye sürükleyerek tasarım yüzeyine iki RadioButton denetimi ekleyin. Düğmelerin TextBlock denetimi altında yan yana görünmesi için düğmeleri (seçerek ve ok tuşlarını kullanarak) hareket ettirin. Denetimleri hizalamak için kırmızı yönergeleri kullanın.

   Pencerenizin şuna benzemesi gerekir:

   ![TextBlock ve iki radyo düğmesiyle karşılama formu](../media/exploreide-greetingswithradiobuttons.png "TextBlock ve iki radyo düğmesi ile Greetings formunun ekran görüntüsü")

1. Sol  RadioButton denetimine ait Özellikler penceresinde **Name** özelliğini (Özellikler penceresinin en üstünde yer alan **özellik) olarak** `HelloButton` değiştirin.

    ![RadioButton özellikleri penceresi](../media/exploreide-buttonproperties.png "RadioButton Özellikleri penceresinin ekran görüntüsü")

1. Sağ  RadioButton denetimi için Özellikler penceresinde Name özelliğini olarak **değiştirin** ve `GoodbyeButton` ardından değişikliklerinizi kaydedin.

Ardından, her RadioButton denetimi için görüntüleme metni eksersiniz. Aşağıdaki yordam, RadioButton denetimi için **Content** özelliğini günceller.

### <a name="add-display-text-for-each-radio-button"></a>Her radyo düğmesi için görüntüleme metni ekleme

1. XAML'de ve için **Content** `HelloButton` `GoodbyeButton` `"Hello"` `"Goodbye"` özniteliğini güncelleştirin. XAML işaretlemesi artık aşağıdaki örnekteki gibi görünüyor olabilir:

   ```xaml
   <Grid>
        <TextBlock HorizontalAlignment="Left" Margin="252,47,0,0" TextWrapping="Wrap" Text="Select a message option and then choose the Display button." VerticalAlignment="Top"/>
        <RadioButton x:Name="HelloButton" Content="Hello" HorizontalAlignment="Left" Margin="297,161,0,0" VerticalAlignment="Top"/>
        <RadioButton x:Name="GoodbyeButton" Content="Goodbye" HorizontalAlignment="Left" Margin="488,161,0,0" VerticalAlignment="Top"/>
   </Grid>
   ```

### <a name="set-a-radio-button-to-be-checked-by-default"></a>Radyo düğmesini varsayılan olarak denetlen olacak şekilde ayarlama

Bu adımda, iki radyo düğmesiden birinin her zaman seçili olması için HelloButton'ın varsayılan olarak denetlenmesi için ayarlayıyoruz.

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

    Çizgi `MessageBox.Show("Hello.")` sarı renkle vurgulanır. IDE 'nin en altında, oto, Yereller ve Watch pencereleri, sol tarafa birlikte yerleştirilir ve çağrı yığını, kesme noktaları, özel durum ayarları, komut, anlık ve çıkış pencereleri sağ tarafta birlikte yerleştirilir.

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
