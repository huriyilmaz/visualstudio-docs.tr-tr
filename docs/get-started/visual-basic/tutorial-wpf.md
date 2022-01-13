---
title: 'öğretici: Visual Basic Windows Presentation Foundation ile uygulama oluşturma'
description: bu öğreticide, Windows Presentation Foundation (WPF) kullanıcı arabirimi çerçevesini kullanarak Visual Studio ile Visual Basic bir Windows masaüstü .net uygulaması oluşturun.
author: anandmeg
ms.author: meghaanand
manager: jmartens
ms.technology: vs-ide-general
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.workload:
- dotnet
dev_langs:
- VB
ms.date: 01/07/2022
ms.custom: vs-acquisition, get-started
ms.openlocfilehash: b9382d659f5b90d957ff63307c050c6be219ecfb
ms.sourcegitcommit: 9b1c1cceab4c59f0b91e19ae46a51969f72fcc34
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/13/2022
ms.locfileid: "136801464"
---
# <a name="tutorial-create-a-wpf-application-with-visual-basic"></a>Öğretici: Visual Basic WPF uygulaması oluşturma

bu öğreticide, Visual Studio tümleşik geliştirme ortamında (ıde) Visual Basic kullanarak bir uygulama oluşturacaksınız.
programınız, Windows Presentation Foundation (WPF) kullanıcı arabirimi çerçevesini kullanacaktır.
Visual Studio 'de kullanabileceğiniz birçok araç, iletişim kutusu ve tasarımcı hakkında bilgi sahibi olmak için bu öğreticiyi kullanın.

Bu öğreticide şunların nasıl yapıldığını öğreneceksiniz:

> [!div class="checklist"]
> - Proje oluşturma
> - Pencereyi yapılandırma ve metin ekleme
> - Düğme ve kod ekleme
> - Uygulamanın hatalarını ayıklama ve test etme
> - Kesme noktalarıyla hata ayıkla
> - Yayın sürümü oluşturma

## <a name="prerequisites"></a>Önkoşullar

::: moniker range="vs-2017"
bu öğreticiyi tamamlayabilmeniz için Visual Studio gerekir.
ücretsiz sürüm için [Visual Studio indirmeleri sayfasını](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) ziyaret edin.
::: moniker-end
::: moniker range="vs-2019"
bu öğreticiyi tamamlayabilmeniz için Visual Studio gerekir.
ücretsiz sürüm için [Visual Studio indirmeleri sayfasını](https://visualstudio.microsoft.com/vs/) ziyaret edin.
::: moniker-end
::: moniker range=">=vs-2022"
bu öğreticiyi tamamlayabilmeniz için Visual Studio gerekir.
ücretsiz sürüm için [Visual Studio indirmeleri sayfasını](https://visualstudio.microsoft.com/downloads) ziyaret edin.
::: moniker-end

## <a name="create-the-project"></a>Proje oluşturma

Visual Studio bir uygulama oluşturduğunuzda, önce bir proje oluşturursunuz.
bu öğreticide bir Windows Presentation Foundation projesi oluşturun.

::: moniker range="vs-2017"
1. Visual Studio'yu açın.

1. menü çubuğunda **dosya** > **yeni** > **Project**' yi seçin.

   ![ekran görüntüsünde dosya ile Visual Studio ve ardından menüden Project seçili görüntülenir.](media/tutorial-wpf/visual-studio-create-project.png)

1. **yeni Project** iletişim kutusunda, Visual Basic yüklü olan   >    >  **Windows Desktop**' ı seçin ve ardından **WPF uygulaması (.NET Framework)** şablonunu seçin. Projeyi **HelloWPFApp** olarak adlandırın ve **Tamam**' ı seçin.

   ![ekran görüntüsünde, W P F uygulama şablonu seçiliyken yeni Project iletişim kutusu görüntülenir.](media/tutorial-wpf/create-desktop-project.png)

   Visual Studio hellowpfapp projesini ve çözümünü oluşturur.
   **Çözüm Gezgini** çeşitli dosyaları gösterir.

   ![Ekran görüntüsünde, Hello W P F App Files yüklü Çözüm Gezgini gösterilmektedir.](media/tutorial-wpf/solution-explorer.png)

**WPF Tasarımcısı** , bölünmüş bir görünümde *MainWindow. xaml* ' in BIR Tasarım görünümünü ve XAML görünümünü gösterir.
::: moniker-end
::: moniker range="vs-2019"
1. Visual Studio'yu açın.

1. **Yeni proje oluştur** ekranında, "WPF" araması yapın ve **WPF uygulaması (.NET Framework)** seçeneğini belirleyin. **İleri**’yi seçin.

   ![arama kutusuna ve w p f App (.NET Framework) proje şablonuna girilen w p f ile yeni proje oluştur iletişim kutusunun ekran görüntüsü.](media/tutorial-wpf/visual-studio-create-wpf-project.png)

1. Projeye *HelloWPFApp* adını verin ve **Oluştur**' u seçin.

   Visual Studio hellowpfapp projesini ve çözümünü oluşturur.
   **Çözüm Gezgini** çeşitli dosyaları gösterir.

   ![Ekran görüntüsünde, Merhaba W P F uygulama dosyası Çözüm Gezgini gösterilmektedir.](media/tutorial-wpf/solution-explorer.png)

**WPF Tasarımcısı** , bölünmüş bir görünümde *MainWindow. xaml* ' in BIR Tasarım görünümünü ve XAML görünümünü gösterir.
::: moniker-end

::: moniker range=">=vs-2022"
1. Visual Studio'yu açın.
 
1. Başlangıç penceresinde **Yeni proje oluştur**' u seçin.

   :::image type="content" source="media/vs-2022/start-window-create-new-project.png" alt-text="Visual Studio 2022 ' de ' yeni proje oluştur ' seçeneği vurgulanmış olarak başlangıç penceresinin ekran görüntüsü.":::

1. **yeni proje oluştur** penceresinde, "WPF" araması yapın ve **tüm diller** açılan listesinden **Visual Basic** seçin.
   **WPF uygulaması (.NET Framework)** öğesini seçin ve ardından **ileri**' yi seçin.

   :::image type="content" source="media/tutorial-wpf/visual-studio-create-wpf-project.png" alt-text="&quot;yeni proje oluştur&quot; iletişim kutusunda ' wpf ', diller listesinde seçilen ' Visual Basic ' ve ' wpf uygulaması (.NET Framework) ' proje şablonu vurgulanmış ' ' bir ekran görüntüsü.":::

1. Projeye **HelloWPFApp** adını verin ve **Oluştur**' u seçin.

   Visual Studio hellowpfapp projesini ve çözümünü oluşturur.
   **Çözüm Gezgini** çeşitli dosyaları gösterir.

   :::image type="content" source="media/vs-2022/explore-ide-hello-wpf-app-files.png" alt-text="Çözüm Gezgini HelloWPFApp projesinde ve çözümünde bulunan dosyaları gösteren ekran görüntüsü.":::

**WPF Tasarımcısı** , bölünmüş bir görünümde *MainWindow. xaml* ' in BIR Tasarım görünümünü ve XAML görünümünü gösterir.
::: moniker-end

> [!NOTE]
> Genişletilebilir Uygulama Biçimlendirme Dili (XAML) hakkında daha fazla bilgi için bkz. [WPF Için xaml 'ye genel bakış](/dotnet/framework/wpf/advanced/xaml-overview-wpf).

## <a name="configure-window-and-add-text"></a>Pencereyi yapılandırma ve metin ekleme

**Özellikler** penceresini kullanarak proje öğeleri, denetimler ve diğer öğeler için seçenekleri görüntüleyebilir ve değiştirebilirsiniz.

1. **Çözüm Gezgini**, *MainWindow. xaml*' yi açın.

1. XAML görünümünde, **Window. title** özelliğinin değerini title *= "MainWindow"* başlık *= "Greetings"* olarak değiştirin.

1. Visual Studio ıde 'nin sol tarafında **araç kutusu** sekmesini seçin. Bunu görmüyorsanız,  > menü çubuğundan veya **CTRL** alt X ' ten Görünüm **araç kutusunu** seçin +  + .

1. **TextBlock** bulmak IÇIN **ortak WPF denetimlerini** genişletin ya da arama çubuğuna *metin* girin.

   :::image type="content" source="media/tutorial-wpf/toolbox-tab-text-block.png" alt-text="Ortak WPF denetimleri listesinde TextBlock denetimiyle vurgulanmış araç kutusu penceresini gösteren ekran görüntüsü.":::

1. **TextBlock** öğesini seçin ve tasarım yüzeyinde pencereye sürükleyin.
   TextBlock denetimini sürükleyerek taşıyabilirsiniz.
   Denetimi yerleştirmek için yönergeleri kullanın.

   :::image type="content" source="media/tutorial-wpf/form-with-text-block.png" alt-text="Selamlamalar biçiminde bulunan ve görünen kılavuzlarla birlikte bulunan TextBlock denetimini gösteren ekran görüntüsü.":::

   XAML işaretlemesi aşağıdaki örnekteki gibi görünmelidir:

   ```xaml
   <TextBlock HorizontalAlignment="Left" Margin="381,100,0,0" TextWrapping="Wrap" Text="TextBlock" VerticalAlignment="Top"/>
   ```

1. XAML görünümünde TextBlock için biçimlendirmeyi bulun ve **metin** özniteliğini değiştirin:

   ```xaml
   Text="Select a message option and then choose the Display button."
   ```

   Gerekirse, TextBlock 'ı yeniden ortalayın

1. **Tümünü Kaydet** araç çubuğu düğmesini seçerek uygulamanızı kaydedin.
   Alternatif olarak, uygulamanızı kaydetmek için, **Dosya**  >  **Tümünü** menü çubuğundan Kaydet ' i seçin veya **CTRL** + **SHIFT** + **S** tuşuna basın.
   Bu, erken ve sık tasarrufu sağlamak için en iyi uygulamadır.

## <a name="add-buttons-and-code"></a>Düğme ve kod ekleme

Uygulamanız iki radyo düğmesi ve bir düğme kullanır.
Bunları eklemek için bu adımları kullanın.
düğmeye Visual Basic kod ekleyeceksiniz.
Bu kod, radyo düğmesi seçimine başvurur.

1. **Araç kutusunda** **RadioButton** bulun.

   :::image type="content" source="media/tutorial-wpf/toolbox-radio-button.png" alt-text="Ortak WPF denetimleri listesinde seçilmiş RadioButton denetimiyle araç kutusu penceresini gösteren ekran görüntüsü.":::

1. **RadioButton** öğesini seçip tasarım yüzeyine sürükleyerek tasarım yüzeyine iki RadioButton denetimi ekleyin.
   Düğmeleri seçip ok tuşlarını kullanarak düğmeleri taşıyın.
   Düğmeleri TextBlock denetiminin altına yan yana yerleştirin.

   :::image type="content" source="media/tutorial-wpf/greetings-form-radio-buttons.png" alt-text="Bir TextBlock denetimi ve iki radyo düğmesi ile Greetings formunu gösteren ekran görüntüsü.":::

1. Sol RadioButton denetimi için **Özellikler** penceresinde, **Özellikler** penceresinin üst kısmındaki **Name** özelliğini *hellobutton* olarak değiştirin.

   :::image type="content" source="media/tutorial-wpf/properties-radio-button-name.png" alt-text="' HelloButton ' RadioButton için Çözüm Gezgini Özellikler penceresi gösteren ekran görüntüsü.":::

1. Sağ RadioButton denetimi için **Özellikler** penceresinde, **ad** özelliğini *goodbyebutton* olarak değiştirin.

1. XAML içinde ve için **içerik** özniteliğini güncelleştirin `HelloButton` `GoodbyeButton` `"Hello"` `"Goodbye"` .

   ```xaml
   <Grid>
        <TextBlock HorizontalAlignment="Left" Margin="252,47,0,0" TextWrapping="Wrap" Text="Select a message option and then choose the Display button." VerticalAlignment="Top"/>
        <RadioButton x:Name="HelloButton" Content="Hello" HorizontalAlignment="Left" Margin="297,161,0,0" VerticalAlignment="Top"/>
        <RadioButton x:Name="GoodbyeButton" Content="Goodbye" HorizontalAlignment="Left" Margin="488,161,0,0" VerticalAlignment="Top"/>
   </Grid>
   ```

1. XAML görünümünde, Merhaba düğmesine yönelik biçimlendirmeyi bulun ve bir **IsChecked** özniteliği ekleyin:

   ```xaml
   IsChecked="True"
   ```

   **True** değeri olan **IsChecked** özniteliği, Merhaba düğmesinin varsayılan olarak denetlendiği anlamına gelir.
   Bu ayar, program başladığında bile radyo düğmesinin her zaman seçildiği anlamına gelir.

1. **Araç kutusu**' nda **düğme** denetimini bulun ve ardından bir düğmeyi RadioButton denetimlerinin altındaki tasarım yüzeyine sürükleyin.

1. XAML görünümünde düğme denetimi için **içerik** değerini `Content="Button"` olarak değiştirin `Content="Display"` .

   ```xaml
   <Button Content="Display" HorizontalAlignment="Left" VerticalAlignment="Top" Width="75" Margin="215,204,0,0"/>
   ```

   Pencereniz aşağıdaki görüntüye benzemelidir.

   :::image type="content" source="media/tutorial-wpf/greetings-buttons.png" alt-text="TextBlock ile Greetings formunu gösteren ekran görüntüsü, ' Merhaba ' ve ' güle ' etiketli RadioButtons ve ' Display ' etiketini içeren düğme denetimi, formda konumlandırılmış.":::

1. Tasarım yüzeyinde **görüntüle** düğmesine çift tıklayın.

   *Greetings. xaml. vb* , olayında imleç ile açılır `Button_Click` .

    ```vb
    Private Sub Button_Click(sender As Object, e As RoutedEventArgs)

    End Sub
    ```

1. Şu kodu ekleyin:

    ```vb
    If HelloButton.IsChecked = True Then
        MessageBox.Show("Hello.")
    ElseIf GoodbyeButton.IsChecked = True Then
        MessageBox.Show("Goodbye.")
    End If
    ```

## <a name="debug-and-test-the-application"></a>Uygulamanın hatalarını ayıklama ve test etme

Sonra, hataları bulmak ve her iki ileti kutusunun doğru şekilde göründüğünü sınamak için uygulamada hata ayıklaması yapacaksınız.
Bu işlemin nasıl çalıştığını görmek için, ilk adım programa bir hata tanıtır.

1. **Çözüm Gezgini**, *MainWindow. xaml* ' e sağ tıklayıp **Yeniden Adlandır**' ı seçin. Dosyayı *Greetings. xaml* olarak yeniden adlandırın.

1. **F5** tuşuna basarak veya **Hata Ayıkla**' yı seçerek hata ayıklayıcıyı başlatın ve ardından **hata ayıklamayı başlatın**.

   **Kesme modu** penceresi görünür ve **Çıkış** penceresi bir özel durumun oluştuğunu gösterir.

   :::image type="content" source="media/tutorial-wpf/exception-unhandled.png" alt-text="' Özel durum Işlenmemiş ' penceresini, ' ' MainWindow. xaml bulunamıyor ' kaynağını okuyan bir System. ıO. Exception iletisi ile gösteren ekran görüntüsü.":::

1. Hata ayıklamayı Durdur hata ayıklamayı **Durdur seçeneğini belirleyerek** durdurun  >  .

   Bu bölümün başlangıcında *MainWindow. xaml* ' i *Greetings. xaml* olarak yeniden adlandırdınız.
   Kod yine de uygulama için başlangıç URI 'SI olarak *MainWindow. xaml* anlamına gelir, bu nedenle proje başlayamaz.

1. **Çözüm Gezgini**, *Application. xaml* dosyasını açın.

1. Değiştir `StartupUri="MainWindow.xaml"``StartupUri="Greetings.xaml"`

1. Hata ayıklayıcıyı yeniden başlatın ( **F5** tuşuna basın). Artık uygulamanızın **Greetings** penceresini görmeniz gerekir.

   ::: moniker range="vs-2017"

   ![TextBlock, RadioButtons ve düğme denetimlerinin görünür olduğu Greetings penceresinin ekran görüntüsü. ' Merhaba ' radyo düğmesi seçildi.](media/exploreide-wpf-running-app.png)

   ::: moniker-end

   ::: moniker range="vs-2019"

   ![TextBlock, RadioButtons ve düğme denetimlerinin görünür olduğu Greetings penceresinin ekran görüntüsü. ' Merhaba ' radyo düğmesi seçildi.](media/vs-2019/exploreide-wpf-running-app.png)

   ::: moniker-end

   ::: moniker range=">=vs-2022"

   :::image type="content" source="media/vs-2022/explore-ide-wpf-running-app.png" alt-text="TextBlock, RadioButtons ve düğme denetimlerinin görünür olduğu Greetings penceresinin ekran görüntüsü. ' Merhaba ' radyo düğmesi seçildi.":::

   ::: moniker-end

1. **Merhaba** ve **görüntü** düğmesini seçin ve sonra da ekran **düğmesine basın** . 
   Hata ayıklamayı durdurmak için sağ üst köşedeki Kapat simgesini kullanın.

Daha fazla bilgi için bkz. [WPF uygulaması oluşturma (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf) ve [WPF hata ayıklama](../../debugger/debugging-wpf.md).

## <a name="debug-with-breakpoints"></a>Kesme noktalarıyla hata ayıkla

Hata ayıklama sırasında bazı kesme noktaları ekleyerek kodu test edebilirsiniz.

1. *Greetings. xaml. vb* dosyasını açın ve aşağıdaki satırı seçin:`MessageBox.Show("Hello.")`

1. **F9** tuşuna basarak veya **Hata Ayıkla**' yı seçerek **kesme noktası ekleyin.**

   Düzenleyici penceresinin sol kenar boşluğunda bulunan kod satırının yanında kırmızı bir daire görünür.

1. Aşağıdaki satırı seçin: `MessageBox.Show("Goodbye.")` .

1. Bir kesme noktası eklemek için **F9** tuşuna basın ve sonra hata ayıklamayı başlatmak için **F5** 'e basın.

1. **Tebrikler** penceresinde, **Merhaba** düğmesini seçin ve ardından **görüntüle**' yi seçin.

   Çizgi `MessageBox.Show("Hello.")` sarı renkle vurgulanır.
   IDE 'nin en altında, **oto**, **Yereller** ve **Watch** pencereleri sol tarafa birlikte yerleştirilir.
   **çağrı yığını**, **kesme noktaları**, **özel durum Ayarlar**, **komut**, **acil** ve **çıkış** pencereleri sağ tarafta bir araya yerleştirildi.

   :::image type="content" source="media/vs-2022/explore-ide-debug-breakpoint.png" alt-text="kod, tanılama ile Visual Studio bir hata ayıklama oturumunun gösterildiği ekran görüntüsü. Oto ve çağrı yığını pencereleri açık. Yürütme, Greetings. xaml. vb içindeki bir kesme noktasında durdurulur.":::

1. Menü çubuğunda **Hata Ayıkla**  >  **Step Out**' ı seçin.

   Uygulama yeniden başlatılır.
   "Hello" sözcüğünü içeren bir iletişim kutusu görünür.

1. İletişim kutusunu kapatmak için **Tamam** düğmesini seçin.

1. **Tebrikler** penceresinde, **güle** radyo düğmesini seçin ve ardından **görüntüle** düğmesini seçin.

   Çizgi `MessageBox.Show("Goodbye.")` sarı renkle vurgulanır.

1. Hata ayıklamaya devam etmek için **F5** tuşunu seçin.
   İletişim kutusu göründüğünde, iletişim kutusunu kapatmak için **Tamam** ' ı seçin.

1. Hata ayıklamayı durdurmak için uygulama penceresini kapatın.

1. Menü çubuğunda, **Hata Ayıkla**  >  **tüm kesme noktalarını devre dışı bırak**' ı seçin.

## <a name="build-a-release-version"></a>Yayın sürümü oluşturma

Her şeyin çalıştığından emin olduğunuza göre, uygulamanız için bir yayın derlemesi hazırlayabilirsiniz.

1.   >  Önceki derlemeler sırasında oluşturulan ara dosyaları ve çıktı dosyalarını silmek için derleme **temiz çözümünü** seçin.

1. Araç çubuğundaki DropDown denetimini kullanarak HelloWPFApp için derleme yapılandırmasını **hata ayıklamadan** **Yayınla** değiştirin.

1. Yapı   >  **Yapı çözümünü** seçin.

Tebrikler, bu öğreticiyi tamamlama!
Çözümünüz ve proje dizininiz (*. ..\Hellowpfapp\hellowpfapp\bin\release*) altında oluşturduğunuz *.exe* bulabilirsiniz.

## <a name="next-steps"></a>Sonraki adımlar

Visual Basic ile Visual Studio Windows Forms uygulamasının nasıl oluşturulacağını öğrenmek için sonraki makaleye ilerleyin.
> [!div class="nextstepaction"]
> [Windows Forms uygulaması oluşturma](../../ide/create-a-visual-basic-winform-in-visual-studio.md)

## <a name="see-also"></a>Ayrıca bkz.

Visual Studio hakkında daha fazla bilgi için şu kaynaklara bakın:

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
