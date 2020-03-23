---
title: Kodlu UI Testi Oluşturma
ms.date: 11/04/2016
ms.topic: conceptual
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: f1e22a39035e5d3500f4dd45481319e1daecfa04
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75592067"
---
# <a name="walkthrough-create-edit-and-maintain-a-coded-ui-test"></a>Walkthrough: Kodlanmış bir UI testi oluşturun, edin ve koruyun

Bu izne, windows sunu çerçevesi (WPF) uygulamasını sınamak için kodlanmış bir ui testi oluşturmayı, nasıl değiştireceğinizi ve koruyacağınızı öğreneceksiniz. Bu izim, çeşitli zamanlama sorunları tarafından bozulan testleri düzeltmek ve denetimleri yeniden düzenlemek için çözümler sağlar.

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

## <a name="create-a-wpf-app"></a>WPF uygulaması oluşturma

1. Yeni bir **WPF Uygulaması (.NET Framework)** projesi oluşturun ve **adını SimpleWPFApp.**

     **WPF Tasarımcısı** projenin Ana Penceresini açar ve görüntüler.

2. Araç kutusu açık değilse, açın. **Görünüm** menüsünü seçin ve ardından **Araç Kutusu'nu**seçin.

3. Tüm **WPF Denetimleri** bölümünün altında, bir **Düğme,** **CheckBox** ve **ProgressBar** denetimini tasarım yüzeyindeki Ana Pencereye sürükleyin.

4. **Düğme** denetimini seçin. **Özellikler** penceresinde, **Ad** özelliğinin değerini Ad \<>'dan button1'e değiştirin. Ardından **İçerik** özelliğinin değerini Düğme'den Başlangıç ekranına değiştirin.

5. **ProgressBar** denetimini seçin. **Özellikler** penceresinde, **Ad** özelliğinin değerini Ad \<yok>'den ilerlemeÇubuğu1'a değiştirin. Ardından **Maksimum** özelliğin değerini **100'den** **10000'e**değiştirin.

6. Onay **Kutusu** denetimini seçin. **Özellikler** penceresinde, **Ad** özelliğinin değerini No \<Name>'dan onay Kutusu1'e çevirin ve **IsEnabled** özelliğini temizleyin.

     ![Basit WPF Uygulaması](../test/media/codedui_wpfapp.png)

7. Tıklatma olayı işleyicisi eklemek için düğme denetimini çift tıklatın.

     *MainWindow.xmal.cs,* kod düzenleyicisinde yeni button1_Click yönteminde imleçle birlikte görüntülenir.

8. MainWindow sınıfının en üstünde bir temsilci ekleyin. Temsilci ilerleme çubuğu için kullanılacaktır. Temsilci eklemek için aşağıdaki kodu ekleyin:

    ```csharp
    public partial class MainWindow : Window
    {
            private delegate void ProgressBarDelegate(System.Windows.DependencyProperty dp, Object value);

        public MainWindow()
        {

            InitializeComponent();
        }
    ```

9. button1_Click yöntemine aşağıdaki kodu ekleyin:

    ```csharp
    private void button1_Click(object sender, RoutedEventArgs e)
    {
        double progress = 0;

        ProgressBarDelegate updatePbDelegate =
            new ProgressBarDelegate(progressBar1.SetValue);

        do
        {
            progress ++;

            Dispatcher.Invoke(updatePbDelegate,
                System.Windows.Threading.DispatcherPriority.Background,
                new object[] { ProgressBar.ValueProperty, progress });
            progressBar1.Value = progress;
        }
        while (progressBar1.Value != progressBar1.Maximum);

        checkBox1.IsEnabled = true;
    }
    ```

10. Dosyayı kaydedin.

### <a name="run-the-wpf-app"></a>WPF uygulamasını çalıştırın

1. Hata **Ayıklama** menüsünde **Hata Ayıklama'yı Başlat'ı** seçin veya **F5 tuşuna**basın.

2. Onay kutusu denetiminin devre dışı bırakıldığına dikkat edin. **Başlangıç'ı**seçin.

     Birkaç saniye içinde ilerleme çubuğu tam %100 bitmiş olmalıdır.

3. Artık onay kutusu denetimini seçebilirsiniz.

4. SimpleWPFApp Uygulamasını Kapatın.

## <a name="create-a-shortcut-to-the-wpf-app"></a>WPF uygulamasıiçin bir kısayol oluşturma

1. Daha önce oluşturduğunuz SimpleWPFApp uygulamasını bulun.

2. SimpleWPFApp uygulaması için bir masaüstü kısayolu oluşturun. *SimpleWPFApp.exe'ye* sağ tıklayın ve **Kopyala'yı**seçin. Masaüstünüzde sağ tıklatın ve **Yapıştır kısayolu**seçin.

    > [!TIP]
    > Uygulamanın kısayolu, uygulamayı hızlı bir şekilde başlatmanızı sağlar, çünkü uygulamanız için kodlanmış Kullanıcı Arabirimi testleri eklemeyi veya değiştirmeyi kolaylaştırır.

## <a name="create-a-coded-ui-test-for-simplewpfapp"></a>SimpleWPFApp için kodlanmış bir Kullanıcı Arabirimi testi oluşturma

1. **Çözüm Gezgini'nde,** çözüme sağ tıklayın ve**Yeni Proje** **Ekle'yi** > seçin.

2. **Kodlanmış UI Test Project** proje şablonunu arayın ve seçin ve proje oluşturulana kadar adımlar boyunca devam edin.

   > [!NOTE]
   > **Kodlanmış UI Test Project** şablonunu görmüyorsanız, [kodlanmış UI test bileşenini yüklemeniz](../test/use-ui-automation-to-test-your-code.md#install-the-coded-ui-test-component)gerekir.

     **CodedUITestProject1** adlı yeni kodlanmış UI test projesi çözümünüze eklenir ve **Kodlanmış UI Testi** için Kod Oluştur iletişim kutusu görüntülenir.

1. Eylemleri **Kaydet'i seçin, UI haritasını düzeltin veya iddialar** seçeneği ekleyin ve **Tamam'ı**seçin.

     **UIMap - Kodlu UI Test Builder** iletişim kutusu görüntülenir ve Visual Studio penceresi en aza indirilir.

     İletişim kutusundaki seçenekler hakkında daha fazla bilgi için [kodlanmış Kullanıcı Arabirimi testleri oluştur'a](../test/use-ui-automation-to-test-your-code.md)bakın.

1. UIMap ' da **Kayda Başla** ' yu seçin **- Kodlu UI Test Builder** iletişim kutusunu.

     ![Kaydı başlat](../test/media/cuit_builder_record.png)

     Gerekirse kaydı duraklatabilirsiniz, örneğin gelen postayla ilgilenmeniz gerekiyorsa.

     ![Kaydı duraklatma](../test/media/cuit_.png)

    > [!WARNING]
    > Masaüstünde gerçekleştirilen tüm eylemler kaydedilir. Kayda hassas verilerin eklenmesine neden olabilecek eylemler gerçekleştirecekseniz kaydı duraklatın.

1. Masaüstü kısayolu kullanarak SimpleWPFApp'ı başlatın.

     Daha önce olduğu gibi, onay kutusu denetiminin devre dışı bırakıldığını unutmayın.

1. SimpleWPFApp'ta **Başlat'ı**seçin.

     Birkaç saniye içinde ilerleme çubuğu tam %100 bitmiş olmalıdır.

1. Şimdi etkinleştirilen onay kutusu denetimini denetleyin.

1. SimpleWPFApp uygulamasını kapatın.

1. **UIMap 'de - Kodlanmış UI Test Builder** iletişim kutusunda Kod **Oluştur'u**seçin.

1. Yöntem **Adı** kutusunda **SimpleAppTest** yazın ve **Ekle ve Oluştur'u**seçin. Birkaç saniye içinde, kodlanmış UI testi görüntülenir ve çözüme eklenir.

1. **UIMap'ı kapat - Kodlu UI Test Oluşturucu.**

     CodedUITest1.cs *CodedUITest1.cs* dosyası kod düzenleyicisinde görünür.

1. Projenizi kaydedin.

### <a name="run-the-test"></a>Testi çalıştırma

1. **Test** menüsünden **Windows'u** seçin ve ardından **Sına Gezgini'ni**seçin.

2. **Yapı** menüsünden **Çözüm Oluştur'u**seçin.

3. *CodedUITest1.cs* dosyasında, **CodedUITestMethod** yöntemini bulun, Testleri **Çalıştır'ı**sağ tıklatın ve seçin veya Testi **Test Gezgini'nden çalıştırın.**

   Kodlanmış UI testi çalışırken, SimpleWPFApp görülebilir. Bir önceki yordamda yaptığınız adımları oluşturur. Ancak, test onay kutusu denetimi için onay kutusunu seçmeye çalıştığında, **Test Sonuçları** penceresi testin başarısız olduğunu gösterir. Bunun nedeni, testin onay kutusunu seçmeye çalışması, ancak ilerleme çubuğu %100 tamamlanana kadar onay kutusu denetiminin devre dışı bırakıldığının farkında olmamasıdır. Kodlanmış UI testi için kullanılabilen çeşitli `UITestControl.WaitForControlXXX()` yöntemleri kullanarak bu ve benzeri sorunları düzeltebilirsiniz. Sonraki yordam, bu `WaitForControlEnabled()` testin başarısız olması için neden olan sorunu düzeltmek için yöntem kullanılarak gösterecektir. Daha fazla bilgi için bkz. [Kodlanmış Kullanıcı Arabirimi testleri oynatma sırasında belirli olayları bekletin.](../test/making-coded-ui-tests-wait-for-specific-events-during-playback.md)

## <a name="edit-and-rerun-the-coded-ui-test"></a>Kodlanmış UI testini edin ve yeniden çalıştırın

1. Test **Gezgini** penceresinde, başarısız testi seçin ve **StackTrace** bölümünde, **UIMap.SimpleAppTest()** için ilk bağlantıyı seçin.

2. UIMap.Designer.cs *UIMap.Designer.cs* dosyası, kodda vurgulanan hata noktasıyla açılır:

    ```csharp
    // Select 'CheckBox' check box
    uICheckBoxCheckBox.Checked = this.SimpleAppTestParams.UICheckBoxCheckBoxChecked;
    ```

3. Bu sorunu gidermek için, yöntemi kullanarak bu satıra devam etmeden önce onay kutusu denetiminin etkinleştirilmesi için kodlanmış UI testini `WaitForControlEnabled()` bekletebilirsiniz.

    > [!WARNING]
    > *UIMap.Designer.cs* dosyayı değiştirmeyin. Yaptığınız tüm kod değişiklikleri UIMap kullanarak kod oluşturmak her zaman overwritten olacak **- Kodlu UI Test Builder**. Kaydedilmiş bir yöntemi değiştirmeniz gerekiyorsa, *UIMap.cs* dosyasına kopyalayın ve yeniden adlandırın. *UIMap.cs* *dosyası, UIMapDesigner.cs* dosyasındaki yöntemleri ve özellikleri geçersiz kılmak için kullanılabilir. *başvuruyu CodedUITest.cs* dosyasındaki özgün yönteme kaldırmanız ve yeniden adlandırılmış yöntem adı ile değiştirmeniz gerekir.

4. **Solution**Explorer'da, kodlanmış UI test projenizde *UIMap.uitest'i* bulun.

5. *UIMap.uitest* için kısayol menüsünü açın ve **Aç'ı**seçin.

     Kodlanmış UI testi kodlanmış UI Test Düzenleyicisi'nde görüntülenir. Şimdi, görüntüleyebilir ve kodlanmış UI testi düzenleyebilirsiniz.

6. Kullanıcı **Birleyeti Eylem** bölmesinde, *UIMap.cs* veya *UIMap.vb* dosyasına taşımak istediğiniz test yöntemini (SimpleAppTest) seçin. Yöntemin farklı bir dosyaya taşınması, test kodu yeniden derlendiğinde üzerine yazılmayan özel kod eklenmesine olanak tanır.

7. **Kodlanmış UI Test Düzenleyicisi** araç çubuğundaki **Kodu Taşı** düğmesini seçin.

8. Microsoft Visual Studio iletişim kutusu görüntülenir. Yöntemin *UIMap.uitest* dosyasından *UIMap.cs* dosyasına taşınacağı ve artık kodlanmış UI Test Düzenleyicisi'ni kullanarak yöntemi değiştiremeyeceğiniz konusunda sizi uyarır. **Evet'i**seçin.

     Test yöntemi *UIMap.uitest* dosyasından kaldırılır ve artık UI Eylemleri bölmesinde görüntülenmez. Taşınan test dosyasını yeniden UIMap.cs *UIMap.cs* dosyayı **Solution Explorer'dan**açın.

9. Visual Studio araç çubuğunda **Kaydet'i**seçin.

     Test yönteminin güncelleştirmeleri *UIMap.Designer* dosyasına kaydedilir.

    > [!WARNING]
    > Yöntemi taşıdığınızda Kodlanmış UI Test Düzenleyicisi'ni kullanarak artık düzenleyemezsiniz. Özel kodunuzu eklemeli ve Kod Düzenleyicisi'ni kullanarak korumalısınız.

10. Yöntemi `SimpleAppTest()` yeniden adlandırma`ModifiedSimpleAppTest()`

11. Aşağıdaki kullanım deyimini dosyaya ekleyin:

    ```csharp
    using Microsoft.VisualStudio.TestTools.UITesting.WpfControls;
    ```

12. Daha önce `WaitForControlEnabled()` tanımlanan kusurlu kod satırından önce aşağıdaki yöntemi ekleyin:

    ```csharp
    uICheckBoxCheckBox.WaitForControlEnabled();

    // Select 'CheckBox' check box
    uICheckBoxCheckBox.Checked = this.SimpleAppTestParams.UICheckBoxCheckBoxChecked;
    ```

13. *CodedUITest1.cs* dosyasında, **CodedUITestMethod** yöntemini bulun ve orijinal SimpleAppTest() yöntemine başvuruyu yorumlayın veya yeniden adlandırın ve ardından yeni ModifiedSimpleAppTest(:

    ```csharp
    [TestMethod]
            public void CodedUITestMethod1()
            {
                // To generate code for this test, select "Generate Code for Coded UI Test" from the shortcut menu and select one of the menu items.
                // For more information on generated code, see http://go.microsoft.com/fwlink/?LinkId=179463
                //this.UIMap.SimpleAppTest();
                this.UIMap.ModifiedSimpleAppTest();
            }
    ```

14. **Yapı** menüsünde **Çözüm Oluştur'u**seçin.

15. **CodedUITestMethod** yöntemini sağ tıklatın ve **Testleri Çalıştır'ı**seçin.

16. Bu kez kodlanmış UI testi testteki tüm adımları başarıyla tamamlar ve **Geçti** **Test Gezgini** penceresinde görüntülenir.

## <a name="refactor-a-control-in-simplewpfapp"></a>SimpleWPFApp'ta kontrolü yeniden düzenleme

1. *MainWindow.xaml* dosyasında, tasarımcıda düğme denetimini seçin.

2. **Özellikler** penceresinin üst kısmında, **Ad** özelliği değerini **button1'den** **buttonA'ya**değiştirin.

3. **Yapı** menüsünde **Çözüm Oluştur'u**seçin.

4. **Test Gezgini'nde** **CodedUITestMethod1**çalıştırın.

     Kodlanmış UI testi button1 olarak UIMap öğesinde başlangıçta eşlenen düğme denetimini konumlandıramadığından test başarısız olur. Yeniden düzenleme kodlanmış UI testlerini bu anlamda etkileyebilir.

5. **Test Gezgini'nde** **StackTrace** bölümünde, **UIMpa.ModifiedSimpleAppTest()** yanındaki ilk bağlantıyı seçin.

     *UIMap.cs* dosyası açılır. Hata noktası kodda vurgulanır:

    ```csharp
    // Click 'Start' button
    Mouse.Click(uIStartButton, new Point(27, 10));
    ```

     Bu yordamda daha önceki kod satırının, yeniden düzene girmeden önce UIMap adı olan kodu kullandığına `UiStartButton`dikkat edin.

     Sorunu gidermek için, **Kodlanmış UI Test Builder'ı**kullanarak yeniden düzenleme denetimini UIMap'e ekleyebilirsiniz. Sonraki yordamda gösterildiği gibi, kodu kullanmak için test kodunu güncelleştirebilirsiniz.

## <a name="map-refactored-control-rerun-the-test"></a>Harita refactored denetimi testi yeniden

1. *CodedUITest1.cs* dosyasında, **CodedUITestMethod1()** yönteminde, sağ tıklatın, **Kodlu UI Testi için Kod Oluştur'u** seçin ve ardından **Kodlu UI Test Oluşturucusu'nu kullanın'ı**seçin.

     **UIMap - Kodlu UI Test Builder** görüntülenir.

2. Daha önce oluşturduğunuz masaüstü kısayolu kullanarak, daha önce oluşturduğunuz SimpleWPFApp uygulamasını çalıştırın.

3. **UIMap - Kodlu Kullanıcı Arabirimi Test Oluşturucu** iletişim kutusunda, crosshair aracını SimpleWPFApp'taki **Başlat** düğmesine sürükleyin.

     **Başlat** düğmesi mavi bir kutuya eklenir. **Kodlanmış UI Test Builder** seçili denetim için verileri işlemek ve denetimözelliklerini görüntülemek için birkaç saniye sürer. **AutomationUId** değerinin **buttonA**olduğuna dikkat edin.

4. Denetimin özelliklerinden, UI Denetim Eşlemesi'ni genişletmek için sol üst köşedeki oku seçin. **UIStartButton1'in** seçildiğine dikkat edin.

5. Araç çubuğunda, **UI Denetim Haritasına Ekle denetimini**seçin.

     Pencerenin altındaki durum, **ÖSY denetim haritasına Seçili denetimi**görüntüleyerek eylemi doğrular.

6. **UIMap 'de - Kodlanmış UI Test Builder** iletişim kutusunda Kod **Oluştur'u**seçin.

     **Kodlanmış UI Test Builder - Code oluşturucu** oluşturucu sulandırma, yeni bir yöntem gerekmediğini ve bu kodun yalnızca UI denetim haritasındaki değişiklikler için oluşturulacağını belirten bir notla birlikte görüntülenir.

7. **Oluştur'u**seçin.

8. SimpleWPFApp Uygulamasını Kapatın.

9. **UIMap'ı kapat - Kodlu UI Test Oluşturucu.**

10. **Çözüm Gezgini'nde** *UIMap.Designer.cs* dosyasını açın.

11. *UIMap.Designer.cs* **dosyasında, UIStartButton1** özelliğini bulun. Aşağıdakilere `SearchProperties` `"buttonA"`dikkat edin:

    ```csharp
    public WpfButton UIStartButton1
            {
                get
                {
                    if ((this.mUIStartButton1 == null))
                    {
                        this.mUIStartButton1 = new WpfButton(this);
                        #region Search Criteria
                        this.mUIStartButton1.SearchProperties[WpfButton.PropertyNames.AutomationId] = "buttonA";
                        this.mUIStartButton1.WindowTitles.Add("MainWindow");
                        #endregion
                    }
                    return this.mUIStartButton1;
                }
            }
    ```

     Şimdi yeni eşlenen denetimi kullanmak için kodlanmış kullanıcı arabirimini değiştirebilirsiniz. Önceki yordamda belirtildiği gibi, kodlanmış UI testinde herhangi bir yöntem veya özellikleri geçersiz kılmak istiyorsanız, *bunu UIMap.cs* dosyasında yapmanız gerekir.

12. *UIMap.cs* dosyasında, bir oluşturucu ekleyin `SearchProperties` ve `UIStartButton` özelliğin özelliğini `AutomationID``"buttonA":`

    ```csharp
    public UIMap()
            {
                this.UIMainWindowWindow.UIStartButton.SearchProperties[WpfButton.PropertyNames.AutomationId] = "buttonA";
            }
    ```

13. **Yapı** menüsünde **Çözüm Oluştur'u**seçin.

14. **Test Gezgini'nde** **CodedUITestMethod1**çalıştırın.

     Bu kez, kodlanmış UI testi testteki tüm adımları başarıyla tamamlar. Test **Sonuçları** penceresinde, **Geçti'nin**durumunu görürsünüz.

## <a name="videos"></a>Videolar

![video](../data-tools/media/playvideo.gif) bağlantısı [Kodlu UI testleri ile başlayın](https://onedrive.live.com/?id=2DB0E1EFE1C1D3B8%21110&cid=2DB0E1EFE1C1D3B8)

## <a name="faq"></a>SSS

[Kodlu UI testleri SSS](https://social.msdn.microsoft.com/Forums/vsautotest/3a74dd2c-cef8-4923-abbf-7a91f489e6c4/faqs)

## <a name="see-also"></a>Ayrıca bkz.

- [Kodunuzu test etmek için UI otomasyonunu kullanma](../test/use-ui-automation-to-test-your-code.md)
- [Kodlanmış UI testleri ve eylem kayıtları için desteklenen yapılandırmalar ve platformlar](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)
- [Kodlanmış UI test düzenleyicisini kullanarak kodlanmış UI testlerini edin](../test/editing-coded-ui-tests-using-the-coded-ui-test-editor.md)
