---
title: Kodlanmış UI testi oluşturma
description: Windows Presentation Framework uygulaması için kodlanmış uı testinin nasıl kullanılacağını öğrenin ve zamanlama sorunları ve denetimleri yeniden düzenleme ile testlerin çözümlerini görün.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 70324bc1f96ca0396b3cca1b5c713a448105554001c9ec71957180dcc5afe991
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121384651"
---
# <a name="walkthrough-create-edit-and-maintain-a-coded-ui-test"></a>İzlenecek yol: kodlanmış bir UI testi oluşturma, düzenleme ve sürdürme

bu kılavuzda, bir Windows Presentation Framework (WPF) uygulamasını test etmek için kodlanmış uı testi oluşturmayı, düzenlemeyi ve bakımını yapmayı öğreneceksiniz. İzlenecek yol çeşitli zamanlama sorunları ve denetimlerin yeniden düzenlemesi tarafından kesilmiş testleri düzeltmeye yönelik çözümler sağlar.

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

## <a name="create-a-wpf-app"></a>WPF uygulaması oluşturma

1. yeni bir **WPF uygulaması (.NET Framework)** projesi oluşturun ve **SimpleWPFApp** olarak adlandırın.

     **WPF Tasarımcısı** açılır ve projenin MainWindow öğesini görüntüler.

2. Araç kutusu açık değilse, açın. **Görünüm** menüsünü ve ardından **araç kutusu**' nu seçin.

3. **Tüm WPF denetimleri** bölümünün altında, Tasarım yüzeyinde bir **düğme**, **onay kutusu** ve **ProgressBar** denetimini MainWindow üzerine sürükleyin.

4. **Düğme** denetimini seçin. **Özellikler** penceresinde, **ad** özelliğinin değerini \<No Name> button1 olarak değiştirin. Ardından **içerik** özelliğinin değerini düğme ' den Başlat ' a değiştirin.

5. **ProgressBar** denetimini seçin. **Özellikler** penceresinde, **ad** özelliğinin değerini \<No Name> progressBar1 olarak değiştirin. Daha sonra **100** olan **maksimum** özellik değerini **10000** olarak değiştirin.

6. **Onay kutusu** denetimini seçin. **Özellikler** penceresinde, **ad** özelliğinin değerini \<No Name> CheckBox1 olarak değiştirin ve **IsEnabled** özelliğini temizleyin.

     ![Basit WPF uygulaması](../test/media/codedui_wpfapp.png)

7. Tıklama olayı işleyicisi eklemek için düğme denetimine çift tıklayın.

     *MainWindow. xlen. cs* , kod düzenleyicisinde yeni button1_Click yönteminde imleç ile görüntülenir.

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

### <a name="run-the-wpf-app"></a>WPF uygulamasını çalıştırma

1. **Hata Ayıkla** menüsünde, **hata ayıklamayı Başlat** ' ı seçin veya **F5** tuşuna basın.

2. Onay kutusu denetiminin devre dışı olduğuna dikkat edin. **Başlat**' ı seçin.

     Birkaç saniye içinde ilerleme çubuğu tam %100 bitmiş olmalıdır.

3. Artık onay kutusu denetimini seçebilirsiniz.

4. SimpleWPFApp Uygulamasını Kapatın.

## <a name="create-a-shortcut-to-the-wpf-app"></a>WPF uygulaması için kısayol oluşturma

1. Daha önce oluşturduğunuz SimpleWPFApp uygulamasını bulun.

2. SimpleWPFApp uygulaması için bir masaüstü kısayolu oluşturun. *SimpleWPFApp.exe* sağ tıklayın ve **Kopyala**' yı seçin. Masaüstünüzde sağ tıklayıp **kısayolu Yapıştır**' ı seçin.

    > [!TIP]
    > Uygulamanın bir kısayolu uygulamayı hızlı bir şekilde başlatabilmenizi sağladığından, uygulamanız için kodlanmış UI testlerini eklemenizi veya değiştirmenizi kolaylaştırır.

## <a name="create-a-coded-ui-test-for-simplewpfapp"></a>SimpleWPFApp için kodlanmış UI testi oluşturma

1. **Çözüm Gezgini**, çözüme sağ tıklayın ve   >  **yeni Project** ekle ' yi seçin.

2. **kodlanmış uı testi Project** proje şablonunu arayıp seçin ve proje oluşturuluncaya kadar adımlarla devam edin.

   > [!NOTE]
   > **kodlanmış uı testi Project** şablonu görmüyorsanız, [kodlanmış uı test bileşenini yüklemeniz](../test/use-ui-automation-to-test-your-code.md#install-the-coded-ui-test-component)gerekir.

     **CodedUITestProject1** adlı yenı kodlanmış UI test projesi çözümünüze eklenir ve **kodlanmış UI testi için kod oluştur** iletişim kutusu görüntülenir.

1. **Eylemleri Kaydet, UI haritasını Düzenle veya onaylama Ekle** seçeneğini belirleyin ve **Tamam**' ı seçin.

     **uımap-kodlanmış uı Test oluşturucusu** iletişim kutusu görüntülenir ve Visual Studio penceresi simge durumuna küçültülür.

     İletişim kutusundaki seçenekler hakkında daha fazla bilgi için bkz. [KODLANMıŞ UI testleri oluşturma](../test/use-ui-automation-to-test-your-code.md).

1. **UIMap-KODLANMıŞ UI Test Oluşturucusu** Iletişim kutusunda **kaydı Başlat** ' ı seçin.

     ![Kaydı başlat](../test/media/cuit_builder_record.png)

     Gerekirse, örneğin, gelen posta ile uğraşmanız gerekiyorsa kaydı duraklatabilirsiniz.

     ![Kaydı Duraklat](../test/media/cuit_.png)

    > [!WARNING]
    > Masaüstünde gerçekleştirilen tüm eylemler kaydedilir. Kayıt sırasında hassas verilerin oluşmasına neden olabilecek eylemler gerçekleştiriyorsanız kaydı duraklatın.

1. Masaüstü kısayolunu kullanarak SimpleWPFApp öğesini başlatın.

     Daha önce olduğu gibi, onay kutusu denetiminin devre dışı olduğuna dikkat edin.

1. SimpleWPFApp üzerinde **Başlat**' ı seçin.

     Birkaç saniye içinde ilerleme çubuğu tam %100 bitmiş olmalıdır.

1. Artık etkin olan onay kutusu denetimini kontrol edin.

1. SimpleWPFApp uygulamasını kapatın.

1. **UIMap-KODLANMıŞ UI Test Oluşturucusu** Iletişim kutusunda **kod oluştur**' u seçin.

1. **Yöntem adı** kutusunda, **SimpleAppTest** yazın ve **Ekle ve oluştur**' u seçin. Birkaç saniye içinde kodlanmış UI testi görünür ve çözüme eklenir.

1. **UIMap-KODLANMıŞ UI Test Oluşturucusu 'nu** kapatın.

     *CodedUITest1. cs* dosyası kod düzenleyicisinde görüntülenir.

1. Projenizi kaydedin.

### <a name="run-the-test"></a>Testi çalıştırma

1. **test** menüsünde **Windows** öğesini seçin ve ardından **test gezgini**' ni seçin.

2. **Build** menüsünde **Build Solution** öğesini seçin.

3. *CodedUITest1. cs* dosyasında, **CodedUITestMethod** metodunu bulun, **Testleri Çalıştır**' ı sağ tıklatın veya test **Gezgini**' nden testi çalıştırın.

   Kodlanmış UI testi çalışırken, SimpleWPFApp görülebilir. Bir önceki yordamda yaptığınız adımları oluşturur. Ancak, test onay kutusu denetimi için onay kutusunu seçme girişiminde bulunduğunda, **test sonuçları** pencere testin başarısız olduğunu gösterir. Bunun nedeni, testin onay kutusunu seçmesini dene, ancak ilerleme çubuğu %100 tamamlanana kadar onay kutusu denetiminin devre dışı bırakıldığını unutmayın. Bu ve benzer sorunları, `UITestControl.WaitForControlXXX()` KODLANMıŞ UI testi için kullanılabilen çeşitli yöntemleri kullanarak düzeltebilirsiniz. Sonraki yordam, `WaitForControlEnabled()` Bu testin başarısız olmasına neden olan sorunu düzeltmek için yöntemini kullanmayı gösterir. Daha fazla bilgi için bkz. [kayıttan yürütme sırasında belirli olaylar için KODLANMıŞ UI testlerinin beklemesini sağlama](../test/making-coded-ui-tests-wait-for-specific-events-during-playback.md).

## <a name="edit-and-rerun-the-coded-ui-test"></a>Kodlanmış UI testini düzenleyin ve yeniden çalıştırın

1. **Test Gezgini** penceresinde, başarısız testi seçin ve **StackTrace** bölümünde **UIMap. SimpleAppTest ()** için ilk bağlantıyı seçin.

2. *UIMap. Designer. cs* dosyası kodda vurgulanan hata noktasıyla açılır:

    ```csharp
    // Select 'CheckBox' check box
    uICheckBoxCheckBox.Checked = this.SimpleAppTestParams.UICheckBoxCheckBoxChecked;
    ```

3. Bu sorunu düzeltmek için, yöntemi kullanarak bu satıra devam etmeden önce, kodlanmış UI testinin CheckBox denetiminin etkinleştirilmesini beklemesini sağlayabilirsiniz `WaitForControlEnabled()` .

    > [!WARNING]
    > *UIMap. Designer. cs* dosyasını değiştirmeyin. **UIMap – KODLANMıŞ UI Test Oluşturucusu** kullanarak her kod oluşturduğunuzda yaptığınız tüm kod değişikliklerinin üzerine yazılır. Kayıtlı bir yöntemi değiştirmeniz gerekiyorsa, *Umap. cs* dosyasına kopyalayın ve yeniden adlandırın. *UIMap. cs* dosyası *UIMapDesigner. cs* dosyasındaki yöntemleri ve özellikleri geçersiz kılmak için kullanılabilir. *CodedUITest. cs* dosyasındaki özgün yönteme başvuruyu kaldırmanız ve yeniden adlandırılmış yöntem adıyla değiştirmeniz gerekir.

4. **Çözüm Gezgini**' de, kodlanmış UI test projenizde *UIMap. UITest* ' i bulun.

5. *UIMap. UITest* için kısayol menüsünü açın ve **Aç**' ı seçin.

     Kodlanmış UI testi kodlanmış UI Test Düzenleyicisi'nde görüntülenir. Şimdi, görüntüleyebilir ve kodlanmış UI testi düzenleyebilirsiniz.

6. **UI eylemi** bölmesinde, *UIMap. cs* veya *UIMap. vb* dosyasına taşımak Istediğiniz test yöntemini (SimpleAppTest) seçin. Yöntemi farklı bir dosyaya taşımak, test kodu yeniden derlenmeye başlatıldığında üzerine yazılmayacak özel kodun eklenmesine izin verir.

7. **KODLANMıŞ UI Test Düzenleyicisi** araç çubuğundaki **kodu taşı** düğmesini seçin.

8. Microsoft Visual Studio iletişim kutusu görüntülenir. Yöntemin *umap. UITest* dosyasından *UIMap. cs* dosyasına TAŞıNACAĞıNı ve artık kodlanmış UI Test Düzenleyicisi 'ni kullanarak yöntemi düzenleyemeyeceksiniz olduğunu uyarır. **Evet**' i seçin.

     Test yöntemi *UIMap. UITest* dosyasından kaldırılır ve artık UI eylemleri bölmesinde görüntülenmez. Taşınan test dosyasını düzenlemek için **Çözüm Gezgini**' den *UIMap. cs* dosyasını açın.

9. Visual Studio araç çubuğunda **kaydet**' i seçin.

     Test yönteminde yapılan güncelleştirmeler *UIMap. Designer* dosyasına kaydedilir.

    > [!WARNING]
    > Yöntemi taşıdığınızda Kodlanmış UI Test Düzenleyicisi'ni kullanarak artık düzenleyemezsiniz. Özel kodunuzu eklemeli ve Kod Düzenleyicisi'ni kullanarak korumalısınız.

10. yöntemi olarak yeniden `SimpleAppTest()` adlandır `ModifiedSimpleAppTest()`

11. Aşağıdaki kullanım deyimini dosyaya ekleyin:

    ```csharp
    using Microsoft.VisualStudio.TestTools.UITesting.WpfControls;
    ```

12. Daha önce tanımlanan `WaitForControlEnabled()` ve rahatsız eden kod satırına önce aşağıdaki yöntemi ekleyin:

    ```csharp
    uICheckBoxCheckBox.WaitForControlEnabled();

    // Select 'CheckBox' check box
    uICheckBoxCheckBox.Checked = this.SimpleAppTestParams.UICheckBoxCheckBoxChecked;
    ```

13. *CodedUITest1.cs* dosyasında **CodedUITestMethod** yöntemini bulun ve özgün SimpleAppTest() yöntemine yapılan başvuruyu açıklama olarak değiştirin veya yeniden adlandırarak yeni ModifiedSimpleAppTest() yöntemiyle değiştirin:

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

14. Derleme menüsünde **Çözümü** **Derleme'yi seçin.**

15. **CodedUITestMethod yöntemine sağ tıklayın ve** Testleri **Çalıştır'ı seçin.**

16. Bu kez kodlanmış UI testi testte tüm adımları başarıyla tamamlar ve Test **Gezgini** penceresinde Başarılı **görüntülenir.**

## <a name="refactor-a-control-in-simplewpfapp"></a>SimpleWPFApp'te denetimi yeniden düzenleme

1. *MainWindow.xaml* dosyasındaki tasarımcıda düğme denetimi seçin.

2. Özellikler penceresinin üst **kısmında,** **Button1** olan **Name** özellik değerini **buttonA olarak değiştirin.**

3. Derleme menüsünde **Çözümü** **Derleme'yi seçin.**

4. **Test Gezgini'nde** **CodedUITestMethod1 çalıştırın.**

     Kodlanmış UI testi button1 olarak UIMap öğesinde başlangıçta eşlenen düğme denetimini konumlandıramadığından test başarısız olur. Yeniden düzenleme kodlanmış UI testlerini bu anlamda etkileyebilir.

5. **Test Gezgini'nde** **StackTrace** bölümünde **UIMpa.ModifiedSimpleAppTest()** işlevinin yanındaki ilk bağlantıyı seçin.

     *UIMap.cs* dosyası açılır. Hata noktası kodda vurgulanır:

    ```csharp
    // Click 'Start' button
    Mouse.Click(uIStartButton, new Point(27, 10));
    ```

     Bu yordamda daha önce kod satırı, yeniden düzenleme öncesinde `UiStartButton` UIMap adı olan kullanarak dikkat edin.

     Sorunu düzeltmek için Kodlanmış UI Test Oluşturucusu'nu kullanarak uimap'e **yeniden düzenleme denetimi ebilirsiniz.** Sonraki yordamda da olduğu gibi kodu kullanmak için testin kodunu güncelleştirebilirsiniz.

## <a name="map-refactored-control-rerun-the-test"></a>Yeniden düzenleme denetimi eşleme testi yeniden çalıştırma

1. *CodedUITest1.cs* **dosyasındaki CodedUITestMethod1()** yöntemine sağ tıklayın, Kodlanmış **UI Testi** için Kod Oluştur'u seçin ve ardından Kodlanmış UI Test Oluşturucusu Kullan'ı **seçin.**

     **UIMap - Kodlanmış UI Test Oluşturucusu** görüntülenir.

2. Daha önce oluşturduğunuz masaüstü kısayolunu kullanarak, daha önce oluşturduğunuz SimpleWPFApp uygulamasını çalıştırın.

3. **UIMap - Kodlanmış UI Test Oluşturucusu** iletişim kutusunda çapraz geçiş aracını SimpleWPFApp'in Başlat düğmesine sürükleyin. 

     Başlat **düğmesi** mavi bir kutu içine alınır. **Kodlanmış UI Test** Oluşturucusu'nun seçilen denetime göre verileri işlemesi ve denetimin özelliklerini görüntülemesi birkaç saniye sürer. **AutomationUId** değerinin buttonA olduğunu **fark vardır.**

4. Denetimin özelliklerinden, UI Denetim Eşlemesi'ni genişletmek için sol üst köşedeki oku seçin. **UIStartButton1'in seçili olduğunu** fark edildi.

5. Araç çubuğunda Kullanıcı Arabirimi Denetim **Eşlemesi'ne denetim ekle'yi seçin.**

     Pencerenin en altındaki durum, Seçili denetimi görüntüleyerek eylemi **doğrular ve kullanıcı arabirimi denetim haritasına eklendi.**

6. **UIMap - Kodlanmış UI Test Oluşturucusu iletişim kutusunda** Kod **Oluştur'u seçin.**

     Kodlanmış **UI Test Oluşturucusu -** Kod Oluştur iletişim kutusu, yeni yöntem gerek olmadığını belirten bir notla görüntülenir ve bu kod yalnızca KULLANıCı arabirimi denetim haritasındaki değişiklikler için oluşturulur.

7. **Oluştur'a seçin.**

8. SimpleWPFApp Uygulamasını Kapatın.

9. UIMap **- Kodlanmış UI Test Oluşturucusu'nu kapatın.**

10. Bu **Çözüm Gezgini** *UIMap.Designer.cs dosyasını* açın.

11. *UIMap.Designer.cs dosyasında* **UIStartButton1 özelliğini** bulun. olarak `SearchProperties` `"buttonA"` ayarlanmıştır:

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

     Şimdi yeni eşlenen denetimi kullanmak için kodlanmış kullanıcı arabirimini değiştirebilirsiniz. Önceki yordamda da işaret ettiği gibi, kodlanmış UI testinde herhangi bir yöntemi veya özelliği geçersiz kılmak için *uimap.cs* dosyasında bunu yapmak gerekir.

12. *UIMap.cs* dosyasında, bir oluşturucu ekleyin ve özelliğinin değerini kullanarak `SearchProperties` `UIStartButton` `AutomationID` özelliğinin özelliğini belirtin`"buttonA":`

    ```csharp
    public UIMap()
            {
                this.UIMainWindowWindow.UIStartButton.SearchProperties[WpfButton.PropertyNames.AutomationId] = "buttonA";
            }
    ```

13. Derleme menüsünde **Çözümü** **Derleme'yi seçin.**

14. **Test Gezgini'nde** **CodedUITestMethod1 çalıştırın.**

     Bu kez, kodlanmış UI testi testteki tüm adımları başarıyla tamamlar. Test Sonuçları **penceresinde** Geçirilen durumunu **görebilirsiniz.**

## <a name="videos"></a>Videolar

![kodlanmış ](../data-tools/media/playvideo.gif) [UI Kullanmaya başlayın video bağlantısı](https://onedrive.live.com/?id=2DB0E1EFE1C1D3B8%21110&cid=2DB0E1EFE1C1D3B8)

## <a name="faq"></a>SSS

[Kodlanmış UI testleri hakkında SSS](https://social.msdn.microsoft.com/Forums/vsautotest/3a74dd2c-cef8-4923-abbf-7a91f489e6c4/faqs)

## <a name="see-also"></a>Ayrıca bkz.

- [Kodunuzu test etmek için UI otomasyonunu kullanma](../test/use-ui-automation-to-test-your-code.md)
- [Kodlanmış UI testleri ve eylem kayıtları için desteklenen yapılandırmalar ve platformlar](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)
- [Kodlanmış UI test düzenleyicisini kullanarak kodlanmış UI testlerini düzenleme](../test/editing-coded-ui-tests-using-the-coded-ui-test-editor.md)
