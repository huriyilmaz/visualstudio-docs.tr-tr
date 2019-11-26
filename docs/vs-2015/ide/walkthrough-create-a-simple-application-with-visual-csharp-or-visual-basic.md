---
title: 'İzlenecek yol: Visual C# veya Visual Basic ile basit bir uygulama oluşturma | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: f84339c7-d617-4f56-bfcd-af2215c347ba
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d5e41dbf3422374add68e351da1e4b703772a3a4
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74296864"
---
# <a name="walkthrough-create-a-simple-application-with-visual-c-or-visual-basic"></a>İzlenecek yol: Visual C# veya Visual Basic ile Basit Uygulama Oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu izlenecek yolu tamamlayarak, Visual Studio ile uygulamalar geliştirirken kullanabileceğiniz birçok araç, iletişim kutusu ve tasarımcı hakkında bilgi sahibi olacaksınız. Tümleşik geliştirme ortamında (IDE) çalışma hakkında daha fazla bilgi edinirken, basit bir "Merhaba Dünya" stili uygulama oluşturacak, kullanıcı arabirimini tasarlayacak, kod ekleyecek ve hataları ayıklayacaksınız.

 Bu konu aşağıdaki bölümleri içermektedir:

 [IDE 'yi yapılandırma](../ide/walkthrough-create-a-simple-application-with-visual-csharp-or-visual-basic.md#BKMK_ConfigureIDE)

 [Basit bir uygulama oluşturma](../ide/walkthrough-create-a-simple-application-with-visual-csharp-or-visual-basic.md#BKMK_CreateApp)

 [Uygulamanın hatalarını ayıklama ve test etme](../ide/walkthrough-create-a-simple-application-with-visual-csharp-or-visual-basic.md#BKMK_DebugTest)

> [!NOTE]
> Bu izlenecek yol, Visual Studio Prosessional sürümünü temel almaktadır ve bu sürüm, bu izlenecek yol için projeyi oluştururken temel olarak kullanacağınız WPF Uygulaması şablonunu sunar. Windows Masaüstü için Visual Studio Express sürümü de bu şablonu sağlar, ancak Windows için Visual Studio Express ve Web için Visual Studio Express sağlamaz. Windows için Visual Studio Express kullanma hakkında giriş bilgileri için bkz. [Windows Mağazası uygulamaları Için Geliştirici Merkezi](https://msdn.microsoft.com/windows/apps/br229519). Web için Visual Studio Express kullanma hakkında giriş bilgileri için bkz. [ASP.net Ile çalışmaya başlama](https://dotnet.microsoft.com/learn/aspnet/hello-world-tutorial/intro). Ayrıca, Visual Studio sürümünüz ve kullandığınız ayarlar, kullanıcı arabiriminin bazı öğelerinin adlarını ve bulundukları yerleri belirler. Bkz. [Visual Studio 'Da geliştirme ayarlarını özelleştirme](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

## <a name="BKMK_ConfigureIDE"></a>IDE 'yi yapılandırma
 Visual Studio 'Yu ilk kez başlattığınızda, Visual Studio Microsoft hizmet hesabıyla (MSA) oturum açmanızı, [Visual Studio 'Da oturum](https://devblogs.microsoft.com/visualstudio/welcome-sign-in-to-visual-studio/)açmanızı ister. Oturum açmanız ve daha sonra bunu yapabilmeniz gerekmez.

 Visual Studio lansman 'da, bir sonraki adımda IDE 'ye önceden tanımlanmış bir özelleştirmeler kümesi uygulayan bir ayarlar birleşimi seçmeniz gerekir. Her bir ayarlar bileşimi, uygulamaları geliştirmenizi kolaylaştırmak amacıyla tasarlanmıştır.

 Bu izlenecek yol, IDE 'ye en az özelleştirme miktarını uygulayan **genel geliştirme ayarlarını**uyguladığınızı varsaymaktadır. Zaten seçtiğiniz C# veya Visual Basic (her ikisi de iyi seçeneklerdir), ayarlarınızı değiştirmeniz gerekmez.  Ayarlarınızı değiştirmek istiyorsanız, **Ayarları içeri ve dışarı aktarma Sihirbazı 'nı**kullanabilirsiniz. Bkz. [Visual Studio 'Da geliştirme ayarlarını özelleştirme](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

 Visual Studio'yu açtıktan sonra araç pencerelerini, menüleri ve araç çubuklarını ve ana pencere alanını tanıyabilirsiniz. Araç pencereleri, **Hızlı Başlat**, menü çubuğu ve en üstteki Standart araç çubuğu ile uygulama penceresinin sol ve sağ taraflarına yerleştirilir. Uygulama penceresinin merkezinde **Başlangıç sayfası**bulunur. Bir çözüm veya proje yüklediğinizde, düzenleyiciler ve tasarımcılar **Başlangıç sayfasının** bulunduğu alanda görüntülenir. Uygulama geliştirirken zamanınızın çoğunu bu orta alanda geçireceksiniz.

 Şekil 2: Visual Studio IDE'si

 ![Genel ayarlar uygulanmış IDE](../ide/media/exploreide-idewithgeneralsettings.png "ExploreIDE-ıdewithgeneralsettings")

 **Seçenekler** iletişim kutusunu kullanarak, Visual Studio 'da, düzenleyicide metnin yazı tipi yüzünü ve boyutunu DEĞIŞTIRME veya IDE 'nin renk teması gibi ek özelleştirmeler yapabilirsiniz. Uyguladığınız ayarlar bileşimine bağlı olarak, bu iletişim kutusundaki bazı öğeler otomatik olarak görünmeyebilir. Tüm olası seçeneklerin göründüğünden emin olmak için **tüm ayarları göster** onay kutusunu seçin.

 Şekil 3: Seçenekler iletişim kutusu

 ![Seçenekler iletişim kutusu wirh tüm ayarları göster seçeneği](../ide/media/exploreide-optionsdialogbox.png "ExploreIDE-Options Iletişimkutusu")

 Bu örnekte, IDE'nin renk temasını açıktan koyuya değiştireceksiniz.  İsterseniz bir proje oluşturmak için ilergeçebilirsiniz.

#### <a name="to-change-the-color-theme-of-the-ide"></a>IDE'nin renk temasını değiştirmek için

1. Üstteki **Araçlar** menüsünü ve ardından Seçenekler ' i seçerek **Seçenekler** iletişim kutusunu açın **...** maddesinin.

    ![Araçlar menüsünde Seçenekler komutu](../ide/media/exploreide-toolsoptionsmenu.png "ExploreIDE-araçları Seçenekseçenekleri menüsü")

2. **Renk temasını** **koyu**olarak değiştirin ve ardından **Tamam**' a tıklayın.

    ![Koyu renkli tema seçildi](../ide/media/exploreide-darkthemeoptionsdlgbox.png "ExploreIDE-koyu Themeoptionsdlgbox")

   Visual Studio'daki renkler aşağıdaki görüntüyle aynı olmalıdır:

   ![Koyu tema uygulanmış IDE](../ide/media/exploreide-darkthemeide.png "ExploreIDE-koyu Themeıde")

   Bu izlenecek yolun geri kalanında bulunan resimler için kullanılan renk teması açık temadır. IDE 'yi özelleştirme hakkında daha fazla bilgi için bkz. [Visual Studio 'Da geliştirme ayarlarını özelleştirme](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

## <a name="BKMK_CreateApp"></a>Basit bir uygulama oluşturma

### <a name="create-the-project"></a>Proje oluşturma
 Visual Studio'da bir uygulama oluştururken önce bir proje ve bir çözüm oluşturursunuz. Bu örnekte, bir Windows Presentation Foundation (WPF) projesi oluşturacaksınız.

##### <a name="to-create-the-wpf-project"></a>WPF projesini oluşturmak için

1. Yeni bir proje oluşturun. Menü çubuğunda **Dosya**, **Yeni**, **proje..** . öğesini seçin.

    ![Menü çubuğunda dosya, yeni, proje ' yi seçin.](../ide/media/exploreide-filenewproject.png "ExploreIDE-FileNewProject")

    Aynı şeyi yapmak için **Hızlı Başlat** kutusuna **Yeni proje** de yazabilirsiniz.

    ![Hızlı Başlat kutusunda yeni proje ' yi belirtin](../ide/media/exploreide-quicklaunchnewprojectsmall.png "ExploreIDE-QuickLaunchNewProjectsmall")

2. Sol bölmedeki **yüklü**, **Şablonlar**, C# **Visual C#** , **Windows**, örneğin, orta bölmedeki WPF uygulaması ' nı seçerek Visual Basic veya Visual WPF uygulaması şablonunu seçin.  Projeyi yeni proje iletişim kutusunun alt kısmındaki HelloWPFApp olarak adlandırın.

    ![Visual Basic WPF projesi oluşturma, HelloWPFApp](../ide/media/exploreide-newprojectvb.png "ExploreIDE-NewProjectVB")

    OR

    ![Bir Visual C&#35; WPF projesi oluşturun, HelloWPFApp](../ide/media/exploreide-newprojectcsharp.png "ExploreIDE-NewProjectcsharp")

   Visual Studio HelloWPFApp projesini ve çözümünü oluşturur ve **Çözüm Gezgini** çeşitli dosyaları gösterir. WPF Tasarımcısı, bölünmüş bir görünümde MainWindow. xaml ' in bir tasarım görünümünü ve XAML görünümünü gösterir. Herhangi bir görünümden daha fazla veya daha az görünmesi için Bölümlendirici slaytı gösterebilirsiniz.  Yalnızca görsel görünümü veya yalnızca XAML görünümünü görmeyi seçebilirsiniz. (Daha fazla bilgi için bkz. [Windows Forms geliştiricileri Için WPF Tasarımcısı](https://msdn.microsoft.com/47ad0909-e89b-4996-b4ac-874d929f94ca)). Aşağıdaki öğeler **Çözüm Gezgini**görüntülenir:

   Şekil 5: Proje öğeleri

   ![HelloWPFApp dosyaları yüklü Çözüm Gezgini](../ide/media/exploreide-hellowpfappfiles.png "ExploreIDE-HelloWPFAppFiles")

   Projeyi oluşturduktan sonra özelleştirebilirsiniz. **Özellikler** penceresini kullanarak ( **Görünüm** menüsünde bulunur), bir uygulamadaki proje öğeleri, denetimler ve diğer öğeler için seçenekleri görüntüleyebilir ve değiştirebilirsiniz. Proje özellikleri ve özellik sayfalarını kullanarak projelere ve çözümlere ilişkin seçenekleri görüntüleyebilir ve değiştirebilirsiniz.

##### <a name="to-change-the-name-of-mainwindowxaml"></a>MainWindow.xaml adını değiştirmek için

1. Aşağıdaki yordamda MainWindow'a daha belirleyici bir ad vereceksiniz. **Çözüm Gezgini**, MainWindow. xaml ' i seçin. **Özellikler** penceresini görmeniz gerekir, ancak bunu yapmazsanız **Görünüm** menüsünü ve **özellik penceresi** öğesini seçin. **Dosya adı** özelliğini `Greetings.xaml`olarak değiştirin.

    ![Dosya adı vurgulanmış Özellikler penceresi](../ide/media/exploreide-filenameinpropertieswindow.png "ExploreIDE-Filenameınpropertieswindow")

    **Çözüm Gezgini** , dosyanın adının artık Greetings. xaml olduğunu gösterir ve MainWindow. xaml düğümünü genişletirseniz (odağı düğüme yerleştirerek ve doğru Tarrow anahtarına basarak), MainWindow. xaml. vb veya MainWindow.xaml.cs 'nin adı artık Greetings. xaml. vb veya Greetings.xaml.cs olduğunu görürsünüz. Bu kod dosyası, birbirleriyle çok daha yakından ilgili olduğunu göstermek için. xaml dosya düğümünün altına yuvalanmıştır.

   > [!WARNING]
   > Bu değişiklik, ayıklamayı ve düzeltmeyi sonraki adımlarda öğreneceğiniz bir hataya neden olur.

2. **Çözüm Gezgini**, tasarımcı görünümünde Greetings. xaml ' i açın (düğüm odağa sahip olduğunda ENTER tuşuna basarak) ve fareyi kullanarak pencerenin başlık çubuğunu seçin.

3. **Özellikler** penceresinde **Title** özelliğinin değerini `Greetings`olarak değiştirin.

   MainWindow.xaml için başlık çubuğunda artık Greetings ifadesi görünür.

### <a name="design-the-user-interface-ui"></a>Kullanıcı arabirimini (UI) tasarlama
 Bu uygulamaya üç tür denetim ekleyeceğiz: TextBlock denetimi, iki RadioButton denetimi ve bir Button denetimi.

##### <a name="to-add-a-textblock-control"></a>TextBlock denetimi eklemek için

1. **Görünüm** menüsünü ve **araç kutusu** öğesini seçerek **araç kutusu** penceresini açın.

2. **Araç kutusunda**TextBlock denetimini arayın.

    ![TextBlock denetimi vurgulanmış olan araç kutusu](../ide/media/exploreide-textblocktoolbox.png "ExploreIDE-Textblockaraç kutusu")

3. TextBlock öğesini seçerek ve tasarım yüzeyinde pencereye sürükleyerek tasarım yüzeyine bir TextBlock denetimi ekleyin.  Pencerenin üst kısmına yakın olan denetimi ortalayın.

   Pencereniz aşağıdaki gösterime benzemelidir:

   Şekil 7: TextBlock denetimini içeren Greetings penceresi

   ![Greetings formundaki TextBlock denetimi](../ide/media/exploreide-greetingswithtextblockonly.png "ExploreIDE-Alaingswithtextblockonly")

   XAML işaretlemesi aşağıdaki gibi görünmelidir:

```
<TextBlock HorizontalAlignment="Center" TextWrapping="Wrap" VerticalAlignment="Center" RenderTransformOrigin="4.08,2.312" Margin="237,57,221,238"><Run Text="TextBlock"/><InlineUIContainer><TextBlock TextWrapping="Wrap" Text="TextBlock"/>
```

##### <a name="to-customize-the-text-in-the-text-block"></a>Metin bloğu içindeki metni özelleştirmek için

1. XAML görünümünde TextBlock için biçimlendirmeyi bulun ve metin özniteliğini değiştirin: `Text=”Select a message option and then choose the Display button.”`

2. TextBlock, Tasarım görünümü uyacak şekilde genişlemezse, tüm metni görüntüleyecek şekilde TextBlock denetimini (kenarlardaki alma tutamaçlarını kullanarak) genişletin.

3. CTRL-s tuşlarına basarak veya **Dosya** menü öğesini kullanarak yaptığınız değişiklikleri kaydedin.

   Ardından, forma iki [RadioButton](https://msdn.microsoft.com/library/6c9ba847-eab7-4bba-9c74-6b56ef72067b) denetimi ekleyeceksiniz.

##### <a name="to-add-radio-buttons"></a>Radyo düğmeleri eklemek için

1. **Araç kutusunda**RadioButton denetimini arayın.

    ![RadioButton denetimi seçiliyken araç kutusu penceresi](../ide/media/exploreide-radiobuttontoolbox.png "ExploreIDE-RadioButtonToolbox")

2. RadioButton öğesini seçerek ve tasarım yüzeyindeki pencereye sürükleyerek tasarım yüzeyine iki RadioButton denetimi ekleyin ve düğmelerin, TextBlock altında yan yana görünmesi için düğmeleri (onları seçerek ve ok tuşlarını kullanarak) taşıyın denetimle.

    Pencerenizin şuna benzemesi gerekir:

    Şekil 8: Greetings penceresinde RadioButton denetimleri.

    ![TextBlock ve iki RadioButton ile Greetings formu](../ide/media/exploreide-greetingswithradiobuttons.png "ExploreIDE-Alaingswithradiobuttons")

3. Sol RadioButton denetimi için **Özellikler** penceresinde, **ad** özelliğini ( **Özellikler** penceresinin üst kısmındaki özellik) `RadioButton1`olarak değiştirin.  Form üzerinde arka plan kılavuzunu değil, RadioButton 'ı seçtiğinizden emin olun; Ad alanı altındaki özellik penceresinin tür alanı RadioButton olmalıdır.

4. Sağ RadioButton denetimi için **Özellikler** penceresinde, **ad** özelliğini `RadioButton2`olarak değiştirin ve ardından CTRL-s tuşlarına basarak veya **Dosya** menü öğesini kullanarak yaptığınız değişiklikleri kaydedin.  Değiştirmeden ve kaydetmeden önce RadioButton 'ı seçtiğinizden emin olun.

   Artık her bir RadioButton denetimi için görüntü metni ekleyebilirsiniz. Aşağıdaki yordam bir RadioButton denetimi için **içerik** özelliğini güncelleştirir.

##### <a name="to-add-display-text-for-each-radio-button"></a>Her bir radyo düğmesine görüntü metni eklemek için

1. Tasarım yüzeyinde, RadioButton1 ' yi seçerken sağ fare düğmesine basarak RadioButton1 için kısayol menüsünü açın, **Metni Düzenle**' yi seçin ve ardından `Hello`girin.

2. RadioButton2 ' ı seçerken sağ fare düğmesine basarak RadioButton2 için kısayol menüsünü açın, **Metni Düzenle**' yi seçin ve ardından `Goodbye`girin.

   Ekleyeceğiniz son UI öğesi bir [düğme](https://msdn.microsoft.com/library/a9d8f5a5-c98c-463e-808a-5a4e63173098) denetimidir.

##### <a name="to-add-the-button-control"></a>Düğme denetimini eklemek için

1. **Araç kutusunda** **düğme** denetimini arayın ve ardından düğme ' yi seçerek ve Tasarım görünümündeki forma sürükleyerek RadioButton denetimlerinin altındaki tasarım yüzeyine ekleyin.

2. XAML görünümünde, düğme denetimi için **içerik** değerini `Content=”Display”``Content=”Button”` değiştirin ve ardından değişiklikleri kaydedin (Ctrl-s veya **Dosya** menüsünü kullanın).

    Biçimlendirme aşağıdaki örneğe benzemelidir: `<Button Content="Display" HorizontalAlignment="Left" VerticalAlignment="Top" Width="75" Margin="215,204,0,0"/>`

   Pencereniz aşağıdaki gösterime benzemelidir.

   Şekil 9: Son Greetings Kullanıcı Arabirimi

   ![Denetim etiketleriyle Greetings formu](../ide/media/exploreide-greetingswithconrollabels.png "ExploreIDE-Alaingswithconrollabels")

### <a name="add-code-to-the-display-button"></a>Görüntüle Düğmesine kod ekleme
 Bu uygulama çalıştığında, Kullanıcı ilk olarak bir radyo düğmesini seçtikten sonra **görüntüle** düğmesini seçtiğinde bir ileti kutusu görünür. Merhaba için bir ileti kutusu ve Güle Güle için bir diğer ileti kutusu görünecektir. Bu davranışı oluşturmak için Greetings.xaml.vb veya Greetings.xaml.cs içinde Button_Click olayına kod ekleyeceksiniz.

##### <a name="add-code-to-display-message-boxes"></a>İleti kutularını görüntülemek için kod ekleme

1. Tasarım yüzeyinde **görüntüle** düğmesine çift tıklayın.

     Greetings.xaml.vb veya Greetings.xaml.cs açılır ve imleç Button_Click olayının içinde olur. Ayrıca, aşağıdaki gibi bir tıklama olayı işleyicisi ekleyebilirsiniz (yapıştırılan kodun herhangi bir ad altında kırmızı bir dalgalı çizgi varsa, büyük olasılıkla tasarım yüzeyinde RadioButton denetimlerini seçmediyseniz ve yeniden adlandırmanız gerekir):

     Visual Basic için olay işleyicisi aşağıdaki gibi görünmelidir:

    ```vb
    Private Sub Button_Click_1(sender As Object, e As RoutedEventArgs)

    End Sub
    ```

     Visual C# için olay işleyicisi aşağıdaki gibi görünmelidir:

    ```csharp
    private void Button_Click_1(object sender, RoutedEventArgs e)
    {

    }
    ```

2. Visual Basic için şu kodu girin:

    ```vb
    If RadioButton1.IsChecked = True Then
        MessageBox.Show("Hello.")
    Else RadioButton2.IsChecked = True
        MessageBox.Show("Goodbye.")
    End If

    ```

     Visual C# için şu kodu girin:

    ```
    if (RadioButton1.IsChecked == true)
    {
        MessageBox.Show("Hello.");
    }
    else
    {
        RadioButton2.IsChecked = true;
        MessageBox.Show("Goodbye.");
    }
    ```

3. Uygulamayı kaydedin.

## <a name="BKMK_DebugTest"></a>Uygulamanın hatalarını ayıklama ve test etme
 Şimdi, hatalara bakmak için uygulamadan hata ayıklayacak ve her iki ileti kutusunun da doğru görünüp görünmediğini test edeceksiniz. Aşağıdaki yönergelerde hata ayıklayıcıyı nasıl derleyip başlatacağınız, ancak daha sonra daha fazla bilgi için WPF [uygulaması (WPF)](https://msdn.microsoft.com/library/a58696fd-bdad-4b55-9759-136dfdf8b91c) ve [WPF](../debugger/debugging-wpf.md) oluşturma hakkında bilgi edinebilirsiniz.

### <a name="find-and-fix-errors"></a>Hataları bulma ve düzeltme
 Bu adımda, daha önce XAML dosyası ana penceresinin adını değiştirerek sebep olduğumuz hatayı bulacaksınız.

##### <a name="to-start-debugging-and-find-the-error"></a>Hata ayıklamayı başlatmak ve hatayı bulmak için

1. Hata **Ayıkla**' yı seçip hata **ayıklamayı başlatın**.

    ![Hata ayıklama menüsünde hata ayıklamayı Başlat komutu](../ide/media/exploreide-startdebugging.png "ExploreIDE-StartDebugging")

    Bir ileti kutusu görüntülenerek IOException hatası oluştuğu belirtilir: 'mainwindow.xaml' kaynağının yeri belirlenemiyor.

2. **Tamam** düğmesini seçin ve ardından hata ayıklayıcıyı durdurun.

    ![Hata ayıklama menüsünde hata ayıklamayı Durdur komutu](../ide/media/exploreide-stopdebugging.png "ExploreIDE-StopDebugging")

   Bu izlenecek yolun başlangıcında MainWindow. xaml ' i Greetings. xaml olarak yeniden adlandırdık, ancak kod yine de uygulama için başlangıç URI 'SI olarak MainWindow. xaml 'e başvuruyor, bu nedenle proje başlatılamıyor.

##### <a name="to-specify-greetingsxaml-as-the-startup-uri"></a>Başlangıç URI'si olarak Greetings.xaml öğesini belirtmek için

1. **Çözüm Gezgini**, XAML görünümündeki App. xaml dosyasını ( C# projede) veya Application. xaml dosyasını (Visual Basic projesinde) açın (Tasarım görünümü), dosyayı seçip ENTER tuşuna basarak veya çift tıklayarak.

2. `StartupUri="MainWindow.xaml"` `StartupUri="Greetings.xaml"`olarak değiştirin ve ardından CTRL-s ile değişiklikleri kaydedin.

   Hata ayıklayıcıyı yeniden başlatın (F5 tuşuna basın). Uygulamanın Greetings penceresini görmeniz gerekir.

### <a name="to-debug-with-breakpoints"></a>Kesme noktaları ile hata ayıklamak için
 Birkaç kesme noktası ekleyerek, hata ayıklama sırasında kodu test edebilirsiniz. Ana menüdeki **Hata Ayıkla** ' yı seçip **kesme noktası** ' nı seçerek veya kesmenin gerçekleşmesini istediğiniz kod satırının yanındaki düzenleyicinin sol kenar boşluğuna tıklayarak kesme noktaları ekleyebilirsiniz.

##### <a name="to-add-breakpoints"></a>Kesme noktaları eklemek için

1. Greetings. xaml. vb veya Greetings.xaml.cs açın ve aşağıdaki satırı seçin: `MessageBox.Show("Hello.")`

2. Menüden **Hata Ayıkla**' yı ve ardından **kesme noktasını aç**' ı seçerek bir kesme noktası ekleyin.

     ![Hata ayıklama menüsünde kesme noktasını Aç komutu](../ide/media/exploreide-togglebreakpoint.png "ExploreIDE-ToggleBreakpoint")

     Düzenleyici penceresinin en sol kenar boşluğunda, kod satırının yanında kırmızı bir daire görünür.

3. Aşağıdaki satırı seçin: `MessageBox.Show("Goodbye.")`.

4. Bir kesme noktası eklemek için F9 tuşuna basın ve sonra hata ayıklamayı başlatmak için F5 tuşuna basın.

5. **Tebrikler** penceresinde, **Merhaba** radyo düğmesini seçin ve ardından **görüntüle** düğmesini seçin.

     Satır `MessageBox.Show("Hello.")` sarı renkle vurgulanır. IDE 'nin en altında, oto, Yereller ve Watch pencereleri, sol tarafa birlikte yerleştirilir ve çağrı yığını, kesme noktaları, komut, anlık ve çıkış pencereleri sağ tarafta birlikte yerleştirilir.

6. Menü çubuğunda **Hata Ayıkla**, **Step Out**seçeneklerini belirleyin.

     Uygulama yürütmeyi devam ettirir ve "Merhaba" sözcüğünü içeren bir ileti kutusu görünür.

7. İletiyi kapatmak için ileti kutusunda **Tamam** düğmesini seçin.

8. **Tebrikler** penceresinde, **güle** radyo düğmesini seçin ve ardından **görüntüle** düğmesini seçin.

     Satır `MessageBox.Show("Goodbye.")` sarı renkle vurgulanır.

9. Hata ayıklamaya devam etmek için F5 tuşuna basın. İleti kutusu göründüğünde kapatmak için ileti kutusunda **Tamam** düğmesini seçin.

10. Hata ayıklamayı durdurmak için SHIFT + F5 tuşlarına basın (önce SHIFT tuşuna basın ve basılı tutarken F5 tuşuna basın).

11. Menü çubuğunda **Hata Ayıkla**, **tüm kesme noktalarını devre dışı bırak**' ı seçin.

### <a name="build-a-release-version-of-the-application"></a>Uygulamanın yayın sürümünü oluşturma
 Her şeyin çalıştığını doğruladığınıza göre artık, uygulamanın bir yayın derlemesini hazırlayabilirsiniz.

##### <a name="to-clean-the-solution-files-and-build-a-release-version"></a>Çözüm dosyalarını temizlemek ve yayın sürümünü oluşturmak için

1. Ana menüde **Oluştur**' u ve ardından önceki derlemeler sırasında oluşturulan ara dosyaları ve çıktı dosyalarını silmek Için **Çözümü Temizle** ' yi seçin.  Bu gerekli değildir, ancak hata ayıklama oluşturma çıkışlarını temizler.

    ![Derleme menüsündeki Çözümü Temizle komutu](../ide/media/exploreide-cleansolution.png "ExploreIDE-CleanSolution")

2. Araç çubuğundaki DropDown denetimini kullanarak HelloWPFApp için derleme yapılandırmasını **hata ayıklamadan** **Yayınla** değiştirin (Şu anda "hata ayıkla" ifadesini alır).

    ![Yayın seçiliyken Standart araç çubuğu](../ide/media/exploreide-releaseversion.png "ExploreIDE-ReleaseVersion")

3. **Build**' i seçip **çözüm derle** ' yi seçerek çözümü oluşturun veya F6 tuşuna basın.

    ![Build menüsünde çözüm komutu oluştur](../ide/media/exploreide-buildsolution.png "ExploreIDE-BuildSolution")

   Tebrikler, bu izlenecek yolu tamamladınız! Çözümünüz ve proje dizininiz (. ..\HelloWPFApp\HelloWPFApp\bin\Release\\) altında oluşturduğunuz. exe dosyasını bulabilirsiniz. Daha fazla örnek araştırmak isterseniz bkz. [Visual Studio örnekleri](../ide/visual-studio-samples.md).

## <a name="see-also"></a>Ayrıca Bkz.
 [Visual studio 2015 ' deki](../what-s-new-in-visual-studio-2015.md) Yenilikler Visual Studio [üretkenlik Ipuçları](../ide/productivity-tips-for-visual-studio.md) [ile geliştirmeye başlama](../ide/get-started-developing-with-visual-studio.md)
