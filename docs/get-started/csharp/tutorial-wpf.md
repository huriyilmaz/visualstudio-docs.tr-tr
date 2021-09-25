---
title: "Merhaba Dünya C'de WPF ile uygulama #"
description: Windows Windows Presentation Foundation (WPF) UI çerçevesini kullanarak C# Visual Studio basit bir Windows Presentation Foundation Masaüstü .NET uygulaması oluşturun.
ms.custom: vs-acquisition, get-started
ms.date: 09/14/2021
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
ms.openlocfilehash: 7627c96851133ba14f5fd3a2b59e3ca3f4e7e567
ms.sourcegitcommit: 8e74969ff61b609c89b3139434dff5a742c18ff4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2021
ms.locfileid: "128428557"
---
# <a name="tutorial-create-a-simple-application-with-c"></a>Öğretici: C ile basit bir uygulama oluşturma\#

Bu öğreticiyi tamamlayarak, bu öğreticiyle uygulama geliştirirken kullanabileceğiniz birçok araç, iletişim kutusu ve tasarımcı hakkında bilgi Visual Studio. Tümleşik geliştirme ortamında ([IDE)](visual-studio-ide.md)çalışma hakkında bilgi edinirken bir "Merhaba Dünya" uygulaması oluşturacak, kullanıcı arabirimini tasarlar, kod ekler ve hata ayıklarsınız.

## <a name="prerequisites"></a>Önkoşullar

::: moniker range="vs-2017"
Daha önce yüklememiş Visual Studio indirmeler [sayfasına Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?) ücretsiz olarak yükleyin.
::: moniker-end
::: moniker range=">=vs-2019"

- Daha önce yüklememiş Visual Studio indirmeler [sayfasına Visual Studio](https://visualstudio.microsoft.com/downloads/) ücretsiz olarak yükleyin.
- Bu öğretici için .NET Framework .NET Core kullanabilirsiniz. .NET Core, daha yeni ve daha modern bir çerçevedir. .NET Core için 2019 Visual Studio 16.3 veya sonraki bir sürümü gerekir.
::: moniker-end

## <a name="configure-the-ide"></a>IDE'yi yapılandırma

::: moniker range="vs-2017"

İlk Visual Studio için oturum açmanız istenir. Bu adım bu öğretici için isteğe bağlıdır. Ardından, geliştirme ayarlarınızı ve renk temanızı seçmenizi isteyen bir iletişim kutusu gösterebilirsiniz. Varsayılan değerleri tut ve Başlat'ı **Visual Studio.**

![Ayarları seç iletişim kutusu](../media/exploreide-settings.png)

Bu Visual Studio sonra araç pencerelerini, menüleri ve araç çubuklarını ve ana pencere boşluklarını görebilirsiniz. Araç pencereleri, uygulama penceresinin sol ve sağ kenarlarında, **Hızlı Başlat,** menü çubuğu ve standart araç çubuğu en üstte olacak şekilde yerleştirildi. Uygulama penceresinin merkezinde Başlangıç Sayfası **yer almaktadır.** Bir çözümü veya projeyi yükleyebilirsiniz. Düzenleyiciler ve tasarımcılar, Başlangıç Sayfasının bulunduğu **alanda** görünür. Bir uygulama geliştirirken, zaman çoğunu bu merkezi alanda geçireceksiniz.

![Visual Studio 2017 IDE genel Ayarlar uygulandı](../media/exploreide-idewithgeneralsettings.png "Visual Studio 2017 IDE'nin Genel Ayarlar ekran görüntüsü")

::: moniker-end

::: moniker range=">=vs-2019"

Uygulamayı Visual Studio önce başlangıç penceresi açılır. Geliştirme **ortamını açmak için Kod** olmadan devam'ı seçin. Araç pencerelerini, menüleri ve araç çubuklarını ve ana pencere boşluklarını görebilirsiniz. Araç pencereleri, uygulama penceresinin sol ve sağ tarafına yerleştirildi. Arama kutusu, menü çubuğu ve standart araç çubuğu en üstte bulunur. Bir çözümü veya projeyi yükleyemediniz mi, düzenleyiciler ve tasarımcılar uygulama penceresinin merkezi alanda görünür. Bir uygulama geliştirirken, zaman çoğunu bu merkezi alanda geçireceksiniz.

::: moniker-end

## <a name="create-the-project"></a>Proje oluşturma

Visual Studio'da bir uygulama oluştururken önce bir proje ve bir çözüm oluşturursunuz. Bu örnekte, bir Windows Presentation Foundation (WPF) projesi oluşturabilirsiniz.

::: moniker range="vs-2017"

1. Yeni bir proje oluşturma. Menü çubuğunda Dosya Yeni'yi **seçin**  >  **ve**  >  **Project.**

     ![Menü çubuğunda Dosya, Yeni ve Yeni'yi Project](../media/exploreide-filenewproject.png "Dosya, Yeni Visual Studio'yi seçtiğiniz menü çubuğunu gösteren ekran Project.")

1. Yeni **Project** iletişim kutusunda Yüklü Visual C# Windows Masaüstü kategorisini ve ardından WPF Uygulaması  >    >   **(.NET Framework) şablonunu** seçin. Projeye **HelloWPFApp adını girin ve** Tamam'ı **seçin.**

     ![Yeni uygulama iletişim kutusundaki Visual Studio WPF Project şablonu](media/exploreide-newprojectcsharp.png "Yeni Uygulama iletişim kutusundaki WPF Uygulaması şablonunun Project görüntüsü.")

::: moniker-end

::: moniker range="vs-2019"

1. Visual Studio'yu açın.

1. Başlangıç penceresinde Yeni proje **oluştur'a tıklayın.**

   !['Yeni proje oluştur' penceresini görüntüleme](../../get-started/media/vs-2019/start-window-create-new-project.png "'Yeni proje oluştur' Visual Studio 2022'de başlangıç penceresinin ekran görüntüsü.")

1. Yeni proje **oluştur ekranında** "WPF" araması ve **WPF Uygulaması'nın ardından** Sonraki'yi **seçin.**

   :::image type="content" source="media/vs-2019/explore-ide-new-project-csharp-vs-2019.png" alt-text="Arama kutusuna 'WPF' girildi ve 'WPF Uygulaması' proje şablonu vurgulanmış 'Yeni proje oluştur' iletişim kutusunun ekran görüntüsü.":::

1. Sonraki ekranda projeye **HelloWPFApp** adını girin ve Sonraki'yi **seçin.**

   :::image type="content" source="./media/vs-2019/explore-ide-name-project.png" alt-text="Uygulama adı alanına 'HelloWPFApp' girildi ve 'Yeni projenizi yapılandır' iletişim kutusunun Project görüntüsü.":::

1. Ek **bilgiler penceresinde** hedef **çerçeveniz için .NET Core 3.1** zaten seçilmiş olması gerekir. Yoksa **.NET Core 3.1'i seçin.** Ardından **Oluştur'a seçin.**

   :::image type="content" source="./media/vs-2019/wpf-target-framework.png" alt-text="'Ek bilgiler' penceresinde .NET Core 3.1'in seçili olduğundan emin olun":::

Visual Studio HelloWPFApp projesini ve çözümünü oluşturur **ve Çözüm Gezgini** dosyaları gösterir. **WPF Tasarımcısı,** bölünmüş görünümde *MainWindow.xaml'in* bir tasarım görünümünü ve XAML görünümünü gösterir. Görünümlerden birini daha fazla veya daha az göstermek için böleni kaydırabilirsiniz. Yalnızca görsel görünümünü veya yalnızca XAML görünümünü görüntülemeyi seçebilirsiniz.

![IDE'de WPF projesi ve çözümü](media/exploreide-wpfproject-cs.png "Visual Studio IDE'de Çözüm Gezgini açık HelloWPFApp projesinin ve çözümünün ve WPF Tasarımcısı'nda 'MainWindow.xaml' XAML ve tasarımcı görünümlerinin açık olduğu ekran görüntüsü.")

> [!NOTE]
> XAML (eXtensible Uygulama Biçimlendirme Dili) hakkında daha fazla bilgi için [WPF için XAML'ye genel bakış sayfasına](/dotnet/framework/wpf/advanced/xaml-overview-wpf) bakın.

Projeyi oluşturduktan sonra özelleştirebilirsiniz. Bunu yapmak için Görünüm **menüsünden Özellikler Penceresi'ne** **tıklayın** veya **F4 tuşuna basın.** Ardından proje öğeleri, denetimler ve bir uygulamadaki diğer öğeler için seçenekleri görüntüp değiştirebilirsiniz.

![Özellik penceresi](../media/exploreide-hellowpfappfiles.png "HelloWPF Çözüm Gezgini Özellikler, Başvurular ve dosyaları gösteren genel ekran görüntüsü.")

::: moniker-end

::: moniker range=">=vs-2022"

1. Visual Studio'yu açın.

1. Başlangıç penceresinde Yeni proje **oluştur'a tıklayın.**

   :::image type="content" source="media/vs-2022/start-window-create-new-project.png" alt-text="'Yeni proje oluştur' Visual Studio 2022'de başlangıç penceresinin ekran görüntüsü.":::

1. Yeni proje **oluştur ekranında** "WPF" araması ve **WPF Uygulaması'nın ardından** Sonraki'yi **seçin.**

   :::image type="content" source="media/vs-2022/explore-ide-new-project-csharp-wpf-vs-2022.png" alt-text="Arama kutusuna 'WPF' girildi ve 'WPF Uygulaması' proje şablonu vurgulanmış 'Yeni proje oluştur' iletişim kutusunun ekran görüntüsü.":::

1. Sonraki ekranda projeye **HelloWPFApp** adını girin ve Sonraki'yi **seçin.**

   :::image type="content" source="media/vs-2022/explore-ide-name-project.png" alt-text="Uygulama adı alanına 'HelloWPFApp' girildi ve 'Yeni projenizi yapılandır' iletişim kutusunun Project görüntüsü.":::

1. Ek **bilgiler penceresinde** hedef **çerçeveniz için .NET 6.0** zaten seçilmiş olması gerekir. Yoksa **.NET 6.0'ı seçin.** Ardından **Oluştur'a seçin.**

   :::image type="content" source="media/vs-2022/wpf-target-framework.png" alt-text="Çerçeve alanında '.NET 6.0'ın seçili olduğu Ek bilgiler penceresinin ekran görüntüsü.":::

Visual Studio HelloWPFApp projesini ve çözümünü oluşturur **ve Çözüm Gezgini** dosyaları gösterir. **WPF Tasarımcısı,** bölünmüş görünümde *MainWindow.xaml'in* bir tasarım görünümünü ve XAML görünümünü gösterir. Görünümlerden birini daha fazla veya daha az göstermek için böleni kaydırabilirsiniz. Yalnızca görsel görünümünü veya yalnızca XAML görünümünü görüntülemeyi seçebilirsiniz.

:::image type="content" source="media/vs-2022/explore-ide-wpf-project-cs.png" alt-text="Visual Studio IDE'de Çözüm Gezgini açık HelloWPFApp projesinin ve çözümünün ve WPF Tasarımcısı'nda 'MainWindow.xaml' XAML ve tasarımcı görünümlerinin açık olduğu ekran görüntüsü.":::

> [!NOTE]
> XAML (eXtensible Uygulama Biçimlendirme Dili) hakkında daha fazla bilgi için [WPF için XAML'ye genel bakış sayfasına](/dotnet/framework/wpf/advanced/xaml-overview-wpf) bakın.

Projeyi oluşturduktan sonra özelleştirebilirsiniz. Bunu yapmak için Görünüm **menüsünden Özellikler Penceresi'ne** **tıklayın** veya **F4 tuşuna basın.** Ardından proje öğeleri, denetimler ve bir uygulamadaki diğer öğeler için seçenekleri görüntüp değiştirebilirsiniz.

:::image type="content" source="media/vs-2022/explore-ide-hello-wpf-properties.png" alt-text="HelloWPFApp Özellikler penceresi Çözüm Özellikleri'nin Misc bölümünü gösteren ekran görüntüsü.":::

::: moniker-end

### <a name="change-the-name-of-mainwindowxaml"></a>MainWindow.xaml adını değiştirme

MainWindow'a daha belirli bir ad vealım. Bu **Çözüm Gezgini** *MainWindow.xaml'e sağ tıklayın ve* Yeniden Adlandır'ı **seçin.** Dosyayı *Greetings.xaml olarak yeniden adlandırır.*

## <a name="design-the-user-interface-ui"></a>Kullanıcı arabirimini (UI) tasarlama

Tasarımcı açık değilse *Greetings.xaml'i* seçin ve **Shift** + **F7** tuşuna basarak tasarımcıyı açın.

Bu uygulamaya üç denetim türü ekleyebilirsiniz: <xref:System.Windows.Controls.TextBlock> denetim, iki <xref:System.Windows.Controls.RadioButton> denetim ve <xref:System.Windows.Controls.Button> denetim.

### <a name="add-a-textblock-control"></a>TextBlock denetimi ekleme

::: moniker range="vs-2019"

1. Arama **kutusunu etkinleştirmek için Ctrl** + **Q** tuşlarına basın ve Araç Kutusu **yazın.** Sonuçlar **listesinden > Araç Kutusu'nı** seçin.

1. Araç **Kutusunda,** Ortak **WPF Denetimleri düğümünü genişletarak** TextBlock denetimine bakın.

     ![TextBlock denetimi vurgulanmış araç kutusu](../media/exploreide-textblocktoolbox.png "Ortak WPF Denetimleri listesinde TextBlock denetimi seçiliyken Araç Kutusu penceresinin ekran görüntüsü.")

1. TextBlock öğesini seçerek ve tasarım yüzeyinde pencereye sürükleyerek tasarım yüzeyine bir **TextBlock** denetimi ekleyin. Denetimi pencerenin üst kısmında ortalar. 2019 Visual Studio sonraki bir yıl içinde kırmızı yönergeleri kullanarak denetimi ortalayabilirsiniz.

    Pencereniz aşağıdaki gösterime benzemelidir:

    ![Greetings formunda TextBlock denetimi](../media/exploreide-greetingswithtextblockonly.png "Greetings formunun tasarım yüzeyindeki TextBlock denetimi ekran görüntüsü.")

   XAML işaretlemesi aşağıdaki örnekteki gibi gösterilsin:

    ```xaml
    <Grid>
        <TextBlock HorizontalAlignment="Left" Margin="387,60,0,0" TextWrapping="Wrap" Text="TextBlock" VerticalAlignment="Top"/>
    </Grid>
    ```

::: moniker-end

::: moniker range=">=vs-2022"

1. Arama **kutusunu etkinleştirmek için Ctrl** + **Q** tuşlarına basın ve Araç Kutusu **yazın.** Sonuçlar **listesinden > Araç Kutusu'nı** seçin.

1. Araç **Kutusunda,** Ortak **WPF Denetimleri düğümünü genişletarak** TextBlock denetimine bakın.

    :::image type="content" source="media/vs-2022/explore-ide-textblock-toolbox.png" alt-text="Ortak WPF Denetimleri listesinde TextBlock denetimi seçiliyken Araç Kutusu penceresinin ekran görüntüsü.":::

1. TextBlock öğesini seçerek ve tasarım yüzeyinde pencereye sürükleyerek tasarım yüzeyine bir **TextBlock** denetimi ekleyin. Denetimi pencerenin üst kısmında ortalar. Denetimi merkezi yapmak için yönergeleri kullanabilirsiniz.

    Pencereniz aşağıdaki görüntüye benzer:

    :::image type="content" source="media/vs-2022/explore-ide-greetings-with-textblock-only.png" alt-text="Tasarım yüzeyindeki TextBlock denetimi ekran görüntüsü. Denetimi konumlandırma ve yeniden boyutlandırma yönergeleri gösterilir.":::

   XAML işaretlemesi aşağıdaki örnekteki gibi gösterilsin:

    ```xaml
    <Grid>
        <TextBlock HorizontalAlignment="Left" Margin="387,60,0,0" TextWrapping="Wrap" Text="TextBlock" VerticalAlignment="Top"/>
    </Grid>
    ```

::: moniker-end

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

::: moniker range="vs-2019"

1. Araç **Kutusunda** **RadioButton denetimi bulun.**

     ![RadioButton denetimi seçili araç kutusu penceresi](../media/exploreide-radiobuttontoolbox.png "Ortak WPF Denetimleri listesinde RadioButton denetimi seçiliyken Araç Kutusu penceresinin ekran görüntüsü.")

1. **RadioButton** öğesini seçerek ve tasarım yüzeyindeki pencereye sürükleyerek tasarım yüzeyine iki RadioButton denetimi ekleyin. Düğmelerin TextBlock denetimi altında yan yana görünmesi için düğmeleri (seçerek ve ok tuşlarını kullanarak) hareket ettirin. Denetimleri hizalamak için kırmızı yönergeleri kullanın.

   Pencerenizin şuna benzemesi gerekir:

   ![TextBlock ve iki radyo düğmesiyle karşılama formu](../media/exploreide-greetingswithradiobuttons.png "Tasarım yüzeyinde bir TextBlock denetimi ve iki RadioButton denetimi gösteren Greetings.xaml için Tasarım penceresinin ekran görüntüsü.")

1. Sol  RadioButton denetimine ait Özellikler penceresinde **Name** özelliğini (Özellikler penceresinin en üstünde yer alan **özellik) olarak** `HelloButton` değiştirin.

    ![RadioButton özellikleri penceresi](../media/exploreide-buttonproperties.png "RadioButton denetimi Özellikler penceresi ekran görüntüsü. Name özelliğinin değeri 'HelloButton' olarak değiştirildi.")

1. Sağ  RadioButton denetimi için Özellikler penceresinde Name özelliğini olarak **değiştirin** ve `GoodbyeButton` ardından değişikliklerinizi kaydedin.

Ardından, her RadioButton denetimi için görüntüleme metni eksersiniz. Aşağıdaki yordam, RadioButton denetimi için **Content** özelliğini günceller.

::: moniker-end

::: moniker range=">=vs-2022"

1. Araç **Kutusunda** **RadioButton denetimi bulun.**

   :::image type="content" source="media/vs-2022/explore-ide-radiobutton-toolbox.png" alt-text="Ortak WPF Denetimleri listesinde RadioButton denetimi seçiliyken Araç Kutusu penceresinin ekran görüntüsü.":::

1. **RadioButton** öğesini seçerek ve tasarım yüzeyindeki pencereye sürükleyerek tasarım yüzeyine iki RadioButton denetimi ekleyin. Düğmelerin TextBlock denetimi altında yan yana görünmesi için düğmeleri (seçerek ve ok tuşlarını kullanarak) hareket ettirin. Denetimleri hizalamak için yönergeleri kullanabilirsiniz.

   Pencerenizin şuna benzemesi gerekir:

   :::image type="content" source="media/vs-2022/explore-ide-greetings-with-radiobuttons.png" alt-text="Tasarım yüzeyinde bir TextBlock denetimi ve iki RadioButton denetimi gösteren Greetings.xaml için Tasarım penceresinin ekran görüntüsü.":::

1. Sol  RadioButton denetimine ait Özellikler penceresinde **Name** özelliğini (Özellikler penceresinin en üstünde yer alan **özellik) olarak** `HelloButton` değiştirin.

   :::image type="content" source="media/vs-2022/explore-ide-button-properties.png" alt-text="RadioButton denetimi Özellikler penceresi ekran görüntüsü. Name özelliğinin değeri 'HelloButton' olarak değiştirildi.":::

1. Sağ  RadioButton denetimi için Özellikler penceresinde Name özelliğini olarak **değiştirin** ve `GoodbyeButton` ardından değişikliklerinizi kaydedin.

Ardından, her RadioButton denetimi için görüntüleme metni eksersiniz. Aşağıdaki yordam, RadioButton denetimi için **Content** özelliğini günceller.

::: moniker-end

### <a name="add-display-text-for-each-radio-button"></a>Her radyo düğmesi için görüntüleme metni ekleme

1. XAML'de ve için **Content** `HelloButton` `GoodbyeButton` `"Hello"` `"Goodbye"` özniteliğini güncelleştirin. XAML işaretlemesi artık aşağıdaki örnekteki gibi görünüyor olabilir:

   ```xaml
   <Grid>
        <TextBlock HorizontalAlignment="Left" Margin="252,47,0,0" TextWrapping="Wrap" Text="Select a message option and then choose the Display button." VerticalAlignment="Top"/>
        <RadioButton x:Name="HelloButton" Content="Hello" HorizontalAlignment="Left" Margin="297,161,0,0" VerticalAlignment="Top"/>
        <RadioButton x:Name="GoodbyeButton" Content="Goodbye" HorizontalAlignment="Left" Margin="488,161,0,0" VerticalAlignment="Top"/>
   </Grid>
   ```

### <a name="set-a-radio-button-to-be-checked-by-default"></a>Radyo düğmesini varsayılan olarak denetlenir olarak ayarlayın

Bu adımda, iki radyo düğmesiden birinin her zaman seçili olması için HelloButton'ın varsayılan olarak denetlenmesi için ayarlayıyoruz.

1. XAML görünümünde HelloButton işaretlemesi bulun.

1. **IsChecked özniteliğini** ekleyin ve True olarak **ayarlayın.** Özellikle `IsChecked="True"` ekleyin.

   XAML işaretlemesi artık aşağıdaki örnekteki gibi görünüyor olabilir:

   ```xaml
   <Grid>
        <TextBlock HorizontalAlignment="Left" Margin="252,47,0,0" TextWrapping="Wrap" Text="Select a message option and then choose the Display button." VerticalAlignment="Top"/>
        <RadioButton x:Name="HelloButton" Content="Hello" IsChecked="True" HorizontalAlignment="Left" Margin="297,161,0,0" VerticalAlignment="Top"/>
        <RadioButton x:Name="GoodbyeButton" Content="Goodbye" HorizontalAlignment="Left" Margin="488,161,0,0" VerticalAlignment="Top"/>
   </Grid>
   ```

Ekley istediğiniz son kullanıcı arabirimi öğesi düğme [denetimidir.](/dotnet/framework/wpf/controls/button)

### <a name="add-the-button-control"></a>Düğme denetimi ekleme

::: moniker range="vs-2019"

1. Araç **Kutusunda Düğme** **denetimi'ne** tıklayın ve ardından tasarım görünümünde forma sürükleyerek RadioButton denetimlerinin altındaki tasarım yüzeyine ekleyin. Visual Studio 2019 veya sonraki bir 2019 veya sonraki bir 2019 kullanıyorsanız kırmızı çizgi denetimi ortalar.

1. XAML görünümünde, Düğme denetimi **için İçerik** değerini olarak olarak `Content="Button"` `Content="Display"` değiştirerek değişiklikleri kaydedin.

     Pencereniz aşağıdaki gösterime benzemelidir.

     ![Denetim etiketleri içeren Greetings formu](media/exploreide-greetingswithcontrollabels-cs.png "TextBlock denetimi, 'Hello' ve 'Goodbye' etiketli iki RadioButton denetimi ve 'Display' etiketli bir düğmeyi gösteren Greetings.xaml için Tasarım penceresinin ekran görüntüsü.")

   XAML işaretlemesi artık aşağıdaki örnekteki gibi görünüyor olabilir:

   ```xaml
   <Grid>
        <TextBlock HorizontalAlignment="Left" Margin="252,47,0,0" TextWrapping="Wrap" Text="Select a message option and then choose the Display button." VerticalAlignment="Top"/>
        <RadioButton x:Name="HelloButton" Content="Hello" IsChecked="True" HorizontalAlignment="Left" Margin="297,161,0,0" VerticalAlignment="Top"/>
        <RadioButton x:Name="GoodbyeButton" Content="Goodbye" HorizontalAlignment="Left" Margin="488,161,0,0" VerticalAlignment="Top"/>
        <Button Content="Display" HorizontalAlignment="Left" Margin="377,270,0,0" VerticalAlignment="Top" Width="75"/>
   </Grid>
   ```

::: moniker-end

::: moniker range=">=vs-2022"

1. Araç **Kutusunda Düğme** **denetimi'ne** tıklayın ve ardından tasarım görünümünde forma sürükleyerek RadioButton denetimlerinin altındaki tasarım yüzeyine ekleyin. Yönergeler, denetimi merkezi bir şekilde ele alamanıza yardımcı olabilir.

1. XAML görünümünde, Düğme denetimi **için İçerik** değerini olarak olarak `Content="Button"` `Content="Display"` değiştirerek değişiklikleri kaydedin.

     Pencereniz aşağıdaki ekran görüntüsüne benzer.

     :::image type="content" source="media/vs-2022/explore-ide-greetings-with-control-labels-cs.png" alt-text="TextBlock denetimi, 'Hello' ve 'Goodbye' etiketli iki RadioButton denetimi ve 'Display' etiketli bir düğmeyi gösteren Greetings.xaml için Tasarım penceresinin ekran görüntüsü.":::

   XAML işaretlemesi artık aşağıdaki örnekteki gibi görünüyor olabilir:

   ```xaml
   <Grid>
        <TextBlock HorizontalAlignment="Left" Margin="252,47,0,0" TextWrapping="Wrap" Text="Select a message option and then choose the Display button." VerticalAlignment="Top"/>
        <RadioButton x:Name="HelloButton" Content="Hello" IsChecked="True" HorizontalAlignment="Left" Margin="297,161,0,0" VerticalAlignment="Top"/>
        <RadioButton x:Name="GoodbyeButton" Content="Goodbye" HorizontalAlignment="Left" Margin="488,161,0,0" VerticalAlignment="Top"/>
        <Button Content="Display" HorizontalAlignment="Left" Margin="377,270,0,0" VerticalAlignment="Top" Width="75"/>
   </Grid>
   ```

::: moniker-end

### <a name="add-code-to-the-display-button"></a>Görüntü düğmesine kod ekleme

::: moniker range="vs-2019"

Bu uygulama çalıştırıldığında, kullanıcı bir radyo düğmesi seçtikten sonra ve ardından Görüntüle düğmesini seçtikten sonra bir ileti **kutusu** görüntülenir. Merhaba için bir ileti kutusu ve Güle Güle için bir diğer ileti kutusu görünecektir. Bu davranışı oluşturmak için `Button_Click` *Greetings.xaml.cs içinde olayına kod eksersiniz.*

1. Tasarım yüzeyinde Görüntüle düğmesine **çift** tıklayın.

     *Greetings.xaml.cs* açılır ve olayda imleci `Button_Click` yer alır.

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

::: moniker-end

::: moniker range=">=vs-2022"

Bu uygulama çalıştırıldığında, kullanıcı bir radyo düğmesi seçtikten sonra ve ardından Görüntüle düğmesini seçtikten sonra bir ileti **kutusu** görüntülenir. Merhaba için bir ileti kutusu ve Güle Güle için bir diğer ileti kutusu görünecektir. Bu davranışı oluşturmak için `Button_Click` *Greetings.xaml.cs içinde olayına kod eksersiniz.*

1. Tasarım yüzeyinde Görüntüle düğmesine **çift** tıklayın.

     *Greetings.xaml.cs* açılır ve olayda imleci `Button_Click` yer alır.

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

::: moniker-end

## <a name="debug-and-test-the-application"></a>Uygulamanın hatalarını ayıklama ve test etme

Ardından, hataları araması ve her iki ileti kutusuyla da doğru şekilde görünp görünmey olmadığını test etmek için uygulamada hata ayıklayabilirsiniz. Aşağıdaki yönergeler hata ayıklayıcıyı derlemeyi ve başlatmayı söyler, ancak daha sonra daha fazla bilgi için WPF uygulaması [oluşturma (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf) ve [WPF'de](../../debugger/debugging-wpf.md) Hata Ayıklama makalelerini okuyabilirsiniz.

### <a name="find-and-fix-errors"></a>Hataları bulma ve düzeltme

Bu adımda, *MainWindow.xaml* dosyasının adını değiştirerek daha önce neden olduğu hatayı bulabilirsiniz.

#### <a name="start-debugging-and-find-the-error"></a>Hata ayıklamayı başlatma ve hatayı bulma

::: moniker range="vs-2019"

1. F5 tuşuna basarak veya **Hata Ayıkla'ya** ve ardından **Hata Ayıklamayı** **Başlat'ı seçerek hata ayıklayıcıyı başlatma.**

   Kesme **Modu penceresi** görüntülenir  ve Çıkış penceresi bir IOException olduğunu gösterir: 'mainwindow.xaml' kaynağı bulunamaz.

   ![IOException iletisi](../media/exploreide-ioexception.png "'Mainwindow.xaml kaynağı bulunamaz' iletisiyle System.IO.IOException'ı gösteren Çıkış penceresinin ekran görüntüsü.")

1. Hata Ayıklama Hata Ayıklamayı **Durdur'u** > **seçerek hata ayıklayıcıyı durdurun.**

Bu öğreticinin başında *MainWindow.xaml* adını *Greetings.xaml* olarak yeniden adlandırıldık, ancak kod yine de *mainWindow.xaml'i* uygulamanın başlangıç URI'si olarak ifade eder ve bu nedenle proje başlatılamaz.

::: moniker-end

::: moniker range=">=vs-2022"

1. F5 tuşuna basarak veya **Hata Ayıkla'ya** ve ardından **Hata Ayıklamayı** **Başlat'ı seçerek hata ayıklayıcıyı başlatma.**

   Kesme **Modu penceresi** görüntülenir  ve Çıkış penceresi bir IOException olduğunu gösterir: 'mainwindow.xaml' kaynağı bulunamaz.

   :::image type="content" source="media/vs-2022/explore-ide-ioexception.png" alt-text="'Mainwindow.xaml kaynağı bulunamaz' iletisiyle System.IO.IOException'ı gösteren Çıkış penceresinin ekran görüntüsü.":::

1. Hata Ayıklama Hata Ayıklamayı **Durdur'u** > **seçerek hata ayıklayıcıyı durdurun.**

Bu öğreticinin başında *MainWindow.xaml* adını *Greetings.xaml* olarak yeniden adlandırıldık, ancak kod yine de *mainWindow.xaml'i* uygulamanın başlangıç URI'si olarak ifade eder ve bu nedenle proje başlatılamaz.

::: moniker-end
#### <a name="specify-greetingsxaml-as-the-startup-uri"></a>Başlangıç URI'si olarak Greetings.xaml belirtin

1. Uygulama **Çözüm Gezgini** *App.xaml dosyasını* açın.

1. olarak `StartupUri="MainWindow.xaml"` `StartupUri="Greetings.xaml"` değişiklik yapın ve değişiklikleri kaydedin.

İsteğe bağlı bir adım olarak, uygulama pencerenizin başlığını bu yeni adla eş değiştirecek şekilde değiştirmek karışıklığı önlemektedir.

1. Bu **Çözüm Gezgini,** yeni yeniden *adlandırdınız Greetings.xaml* dosyasını açın.

1. **Window.Title özelliğinin değerini** olarak `Title="MainWindow"` değiştirebilir ve değişiklikleri `Title="Greetings"` kaydedebilirsiniz.

Hata ayıklayıcıyı yeniden başlatma **(F5 tuşuna basın).** Şimdi, uygulamanın **Greetings** penceresini görüyor gerekir.

::: moniker range="vs-2017"
![Çalışan uygulamanın ekran görüntüsü](media/exploreide-wpf-running-app.png "TextBlock, RadioButtons ve Button denetimlerinin görünür olduğu Greetings penceresinin ekran görüntüsü. 'Hello' radyo düğmesi seçilidir.")
::: moniker-end
::: moniker range="vs-2019"
![Çalışan uygulamanın ekran görüntüsü](media/vs-2019/exploreide-wpf-running-app.png "TextBlock, RadioButtons ve Button denetimlerinin görünür olduğu Greetings penceresinin ekran görüntüsü. 'Hello' radyo düğmesi seçilidir.")
::: moniker-end
::: moniker range=">=vs-2022"

:::image type="content" source="media/vs-2022/explore-ide-wpf-running-app.png" alt-text="TextBlock, RadioButtons ve Button denetimlerinin görünür olduğu Greetings penceresinin ekran görüntüsü. 'Hello' radyo düğmesi seçilidir.":::

::: moniker-end

Şimdi hata ayıklamayı durdurmak için uygulama penceresini kapatın.

### <a name="debug-with-breakpoints"></a>Kesme noktalarıyla hata ayıklama

Bazı kesme noktaları ekleyerek hata ayıklama sırasında kodu test etmek için kullanabilirsiniz. Kesme noktaları eklemek için Hata Ayıklama Kesme Noktası Geçişini Değiştir'i seçerek, kesmenin gerçekleşmesini istediğiniz kod çizgisinin yanındaki düzenleyicinin sol kenar boşluğuna tıklayarak veya  >  F9 tuşuna basarak **ebilirsiniz.**

#### <a name="add-breakpoints"></a>Kesme noktası ekleme

::: moniker range="vs-2019"

1. *Greetings.xaml.cs'yi* açın ve aşağıdaki satırı seçin:`MessageBox.Show("Hello.")`

1. Hata Ayıkla'ya ve ardından Kesme Noktası'nın geçişini **seçerek menüden bir kesme noktası ekleyin.**

     Düzenleyici penceresinin en sol kenar boşluğunda, kod satırının yanında kırmızı bir daire görünür.

1. Şu satırı seçin: `MessageBox.Show("Goodbye.")` .

1. Kesme noktası **eklemek için F9** tuşuna basın ve ardından hata ayıklamayı **başlatmak için F5** tuşuna basın.

1. Selamlama **penceresinde** Hello radyo **düğmesini** ve ardından Görüntüle **düğmesini** seçin.

    Satır `MessageBox.Show("Hello.")` sarıyla vurgulanır. IDE'nin alt kısmında, Sol tarafta Otomatikler, Yereller ve İzleme pencereleri bir araya, Çağrı Yığını, Kesme Noktaları, Özel Durum Ayarlar, Komut, Anlık ve Çıkış pencereleri de sağ tarafta bir araya yerleştirildi.

    ![Hata ayıklayıcıda kesme noktası](media/exploreide-debugbreakpoint.png "Visual Studio'da hata ayıklama oturumunun ekran görüntüsü. Greetings.xaml.cs için kod penceresi, yürütmenin bir kesme noktası sırasında durdurulmuş olduğunu ve sarıyla vurgulanmış bir satır olduğunu gösterir.")

1. Menü çubuğunda Hata Ayıkla **Adım Dışarı seçeneğini** > **belirleyin.**

     Uygulama yürütmeyi sürdürür ve "Hello" sözcüğüyle bir ileti kutusu görüntülenir.

1. kapatmak **için** ileti kutusunda Tamam düğmesini seçin.

1. Selamlama **penceresinde** Güle Güle radyo **düğmesini** ve ardından Görüntüle **düğmesini** seçin.

     Satır `MessageBox.Show("Goodbye.")` sarıyla vurgulanır.

1. Hata **ayıklamaya devam etmek** için F5 tuşuna basın. İleti kutusu görüntülendiğinde, kapatmak **için** ileti kutusunda Tamam düğmesini seçin.

1. Hata ayıklamayı durdurmak için uygulama penceresini kapatın.

1. Menü çubuğunda Hata Ayıkla Tüm **Kesme Noktaları'nın** > **Devre Dışı Bırak'ı seçin.**

::: moniker-end

::: moniker range=">=vs-2022"

1. *Greetings.xaml.cs'yi* açın ve aşağıdaki satırı seçin:`MessageBox.Show("Hello.")`

1. Hata Ayıkla'ya ve ardından Kesme Noktası'nın geçişini **seçerek menüden bir kesme noktası ekleyin.**

     Düzenleyici penceresinin en sol kenar boşluğunda, kod satırının yanında kırmızı bir daire görünür.

1. Şu satırı seçin: `MessageBox.Show("Goodbye.")` .

1. Kesme noktası **eklemek için F9** tuşuna basın ve ardından hata ayıklamayı **başlatmak için F5** tuşuna basın.

1. Selamlama **penceresinde** Hello radyo **düğmesini** ve ardından Görüntüle **düğmesini** seçin.
    
    Satır `MessageBox.Show("Hello.")` sarıyla vurgulanır. IDE'nin alt kısmında, Sol tarafta Otomatikler, Yereller ve İzleme pencereleri bir araya, Çağrı Yığını, Kesme Noktaları, Özel Durum Ayarlar, Komut, Anlık ve Çıkış pencereleri de sağ tarafta bir araya yerleştirildi.

    :::image type="content" source="media/vs-2022/explore-ide-debug-breakpoint.png" alt-text="Visual Studio'da hata ayıklama oturumunun ekran görüntüsü. Greetings.xaml.cs için kod penceresi, yürütmenin bir kesme noktası sırasında durdurulmuş olduğunu ve sarıyla vurgulanmış bir satır olduğunu gösterir.":::

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

Çalışan uygulamada, pencerenizin üst kısmında görünen bir pencere öğesi görüyor olun. Pencere öğesi, bazı yararlı hata ayıklama özelliklerine hızlı erişim sağlayan bir çalışma zamanı yardımcıdır. İlk düğme olan Canlı **Görsel Ağaç'a git'i seçin.** Sayfanın tüm görsel öğelerini içeren bir ağaç içeren bir pencere görüyor gerekir. Eklenen düğmeleri bulmak için düğümleri genişletin.

::: moniker range="vs-2019"
![Canlı Görsel Ağaç penceresinin ekran görüntüsü](media/vs-2019/exploreide-live-visual-tree.png "Çalışırken sayfada görsel öğeler ağacını gösteren Canlı Görsel Ağaç penceresinin ekran görüntüsü.")
::: moniker-end
::: moniker range=">=vs-2022"

:::image type="content" source="media/vs-2022/explore-ide-live-visual-tree.png" alt-text="Canlı Görsel Ağaç penceresinin, çalışırken görsel öğelerden HelloWPFApp.exe gösteren ekran görüntüsü.":::

::: moniker-end
### <a name="build-a-release-version-of-the-application"></a>Uygulamanın yayın sürümünü oluşturma

Her şeyin çalıştığını doğruladıktan sonra uygulamanın yayın derlemesi hazırlanabilir.

1. Ana menüde, önceki **derlemeler sırasında** oluşturulan ara dosyaları ve çıkış dosyalarını silmek için Derleme Temizleme  >   çözümü'ne tıklayın. Bu adım gerekli değildir, ancak hata ayıklama derleme çıkışlarını temizler.

1. Araç çubuğundaki açılır menü denetimiyle HelloWPFApp derleme yapılandırmasını Hata Ayıklama'dan Sürüm'e (şu anda "Hata Ayıkla" olarak görünür) değiştirebilirsiniz.  

1. Çözümü Derleme **Çözümü'dür'dür'**  >  **seçerek çözümü derleme.**

Tebrikler, bu öğreticiyi tamamladıktan sonra! Çözüm ve proje *.exe* (*...\HelloWPFApp\HelloWPFApp\bin\Release*) altında kendi.exedizininizi bulabilirsiniz.

## <a name="next-steps"></a>Sonraki adımlar

Tebrikler, bu öğreticiyi tamamladıktan sonra! Daha da fazla bilgi edinmek için aşağıdaki öğreticilerle devam edin.

> [!div class="nextstepaction"]
> [Daha fazla WPF öğreticisi ile devam edin](/dotnet/framework/wpf/getting-started/wpf-walkthroughs/)

## <a name="see-also"></a>Ayrıca bkz.

- [Üretkenlik ipuçları](../../ide/productivity-features.md)
