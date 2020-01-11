---
title: 'İzlenecek yol: kodlanmış bir UI testi oluşturma, düzenlememe ve sürdürme | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: f7c25ba7-5c9c-455b-9242-701cda56f90c
caps.latest.revision: 43
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d14de396e24874f39a09172a483ebef81a5886f2
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/10/2020
ms.locfileid: "75851226"
---
# <a name="walkthrough-creating-editing-and-maintaining-a-coded-ui-test"></a>İzlenecek yol: Kodlanmış Bir UI Testi Oluşturmak Düzenlemek ve Sürdürmek
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu yönergede kodlanmış UI testinin nasıl oluşturulduğunu, düzenlendiğini ve korunduğunu göstermek üzere basit bir Windows Presentation Foundation (WPF) oluşturacaksınız. İzlenecek yol çeşitli zamanlama sorunları ve yeniden düzenlemeyi denetleme tarafından kırılan testleri düzeltmeye ilişkin çözümler sağlar.

## <a name="prerequisites"></a>Prerequisites
 Bu örnek için şunlar gerekir:

- Visual Studio Enterprise

### <a name="create-a-simple-wpf-application"></a>Basit WPF Uygulaması Oluşturma

1. **Dosya** menüsünde, **Yeni**' nin üzerine gelin ve ardından **Proje**' yi seçin.

     **Yeni proje** iletişim kutusu görüntülenir.

2. **Yüklü** bölmesinde, **C#görsel**' i genişletin ve ardından **Windows Masaüstü**' nü seçin.

3. Orta bölmede, hedef Framework açılan listesinin **.NET Framework 4,5**olarak ayarlandığını doğrulayın.

4. Orta bölmede **WPF uygulama** şablonunu seçin.

5. **Ad** metin kutusuna **SimpleWPFApp**yazın.

6. Projeyi kaydetmek için bir klasör seçin. **Konum** metin kutusuna klasörün adını yazın.

7. **Tamam**’ı seçin.

     Visual Studio için WPF Tasarımcısı açılır ve projenin MainWindow öğesini görüntüler.

8. Araç kutusu açık değilse, açın. **Görünüm** menüsünü ve ardından **araç kutusu**' nu seçin.

9. **Tüm WPF denetimleri** bölümünün altında, Tasarım yüzeyinde bir **düğme**, **onay kutusu** ve **ProgressBar** denetimini MainWindow üzerine sürükleyin.

10. Düğme denetimini seçin. Özellikler penceresi, **ad** özelliğinin değerini button1 olarak \<ad > olarak değiştirin. Ardından **içerik** özelliğinin değerini düğme ' den Başlat ' a değiştirin.

11. ProgressBar denetimini seçin. Özellikler penceresi, **ad** \<özelliği için değer değerini progressBar1 > ad olarak değiştirin. Daha sonra **100** olan **maksimum** özellik değerini **10000**olarak değiştirin.

12. Onay kutusu denetimini seçin. Özellikler penceresi, **ad** \<özelliğinin değerini checkBox1 yok > olarak değiştirin ve **IsEnabled** özelliğini temizleyin.

     ![Basit WPF uygulaması](../test/media/codedui-wpfapp.png "CodedUI_WPFApp")

13. Tıklama olayı işleyicisi eklemek için düğme denetimine çift tıklayın.

     MainWindow.xmal.cs, yeni button1_Click yönteminde imleç ile Kod Düzenleyicisi'nde görüntülenir.

14. MainWindow sınıfının en üstünde bir temsilci ekleyin. Temsilci ilerleme çubuğu için kullanılacaktır. Temsilci eklemek için aşağıdaki kodu ekleyin:

    ```csharp
    public partial class MainWindow : Window
    {
            private delegate void ProgressBarDelegate(System.Windows.DependencyProperty dp, Object value);

        public MainWindow()
        {

            InitializeComponent();
        }

    ```

15. button1_Click yöntemine aşağıdaki kodu ekleyin:

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

16. Dosyayı kaydedin.

### <a name="verify-the-wpf-application-runs-correctly"></a>WPF Uygulamasının Düzgün Çalıştığını Doğrulama

1. **Hata Ayıkla** menüsünde, **hata ayıklamayı Başlat** ' ı seçin veya **F5**tuşuna basın.

2. Onay kutusu denetiminin devre dışı olduğuna dikkat edin. **Başlat**' ı seçin.

     Birkaç saniye içinde ilerleme çubuğu tam %100 bitmiş olmalıdır.

3. Artık onay kutusu denetimini seçebilirsiniz.

4. SimpleWPFApp Uygulamasını Kapatın.

### <a name="create-and-run-a-coded-ui-test-for-simplewpfapp"></a>SimpleWPFApp için Kodlanmış Kullanıcı Arabirimi Testi Oluşturma ve Çalıştırma

1. Daha önce oluşturduğunuz SimpleWPFApp uygulamasını bulun. Varsayılan olarak, uygulama C:\Users\\< Kullanıcı adı\>\\Projects\SimpleWPFApp\SimpleWPFApp\bin\Debug\SimpleWPFApp.exe Studio \<sürüm >

2. SimpleWPFApp uygulaması için bir masaüstü kısayolu oluşturun. SimpleWPFApp. exe ' ye sağ tıklayın ve **Kopyala**' yı seçin. Masaüstünüzde sağ tıklayıp **kısayolu Yapıştır**' ı seçin.

    > [!TIP]
    > Uygulamaya bir kısayol eklenmesi, uygulamayı hızlıca başlatmanızı sağladığından uygulamanız açısından Kodlanmış UI testleri ekleyip değiştirmenizi kolaylaştırır.

3. Çözüm Gezgini, çözüme sağ tıklayın, **Ekle** ' yi ve ardından **Yeni proje**' yi seçin.

     **Yeni Proje Ekle** iletişim kutusu görüntülenir.

4. **Yüklü** bölmesinde, **görsel C#** ' i genişletin ve ardından **Test**' i seçin.

5. Orta bölmede, **KODLANMıŞ UI testi proje** şablonunu seçin.

6. **Tamam**’ı seçin.

     Çözüm Gezgini, **CodedUITestProject1** adlı yenı kodlanmış UI test projesi çözümünüze eklenir.

     **KODLANMıŞ UI testi Için kod üret** iletişim kutusu görüntülenir.

7. **Eylemleri Kaydet, UI haritasını Düzenle veya onaylama Ekle** seçeneğini belirleyin ve **Tamam**' ı seçin.

     UIMap – Kodlanmış UI Test Oluşturucusu görüntülenir ve Visual Studio penceresi simge durumuna küçültülür.

     İletişim kutusundaki seçenekler hakkında daha fazla bilgi için bkz. [KODLANMıŞ UI testleri oluşturma](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeUsingCUITCreate).

8. UIMap – Kodlanmış UI Test Oluşturucusu 'nda **kaydı Başlat** ' ı seçin.

     ![Kaydı Başlat](../test/media/cuit-builder-record.png "CUIT_Builder_Record")

     Gerekirse, örneğin, gelen posta ile uğraşmanız gerekiyorsa kaydı duraklatabilirsiniz.

     ![Kaydı Duraklat](../test/media/cuit.png "CUIT_")

    > [!WARNING]
    > Masaüstünde gerçekleştirilen tüm eylemler kaydedilir. Kayıt sırasında hassas verilerin oluşmasına neden olabilecek eylemler gerçekleştiriyorsanız kaydı duraklatın.

9. Masaüstü kısayolunu kullanarak SimpleWPFApp öğesini başlatın.

     Daha önce olduğu gibi, onay kutusu denetiminin devre dışı olduğuna dikkat edin.

10. SimpleWPFApp üzerinde **Başlat**' ı seçin.

     Birkaç saniye içinde ilerleme çubuğu tam %100 bitmiş olmalıdır.

11. Artık etkin olan onay kutusu denetimini kontrol edin.

12. SimpleWPFApp uygulamasını kapatın.

13. UIMap-Kodlanmış UI Test Oluşturucusu 'nda **kod oluştur**' u seçin.

14. Yöntem adı ' nda **SimpleAppTest** yazın ve **Ekle ve Oluştur '** u seçin. Birkaç saniye içinde Kodlanmış UI testi görünür ve Çözüm'e eklenir.

15. UIMap – Kodlanmış Kullanıcı Arabirimi Test Oluşturucusu uygulamasını kapatın.

     Kod Düzenleyicisi'nde CodedUITest1.cs dosyası görüntülenir.

16. Projenizi kaydedin.

### <a name="run-the-coded-ui-test"></a>Kodlanmış UI Testi Çalıştırma

1. **Test** menüsünde **Windows** ' u ve ardından **Test Gezgini**' ni seçin.

2. **Build** menüsünde **Build Solution**öğesini seçin.

3. CodedUITest1.cs dosyasında, **CodedUITestMethod** metodunu bulun, **Testleri Çalıştır**' ı sağ tıklatın veya test Gezgini ' nden testi çalıştırın.

     Kodlanmış UI testi çalışırken, SimpleWPFApp görülebilir. Bir önceki yordamda yaptığınız adımları oluşturur. Ancak, test onay kutusu denetimi için onay kutusunu seçme girişiminde bulunduğunda, Test Sonuçları pencere testin başarısız olduğunu gösterir. Bunun nedeni, testin onay kutusunu seçmesini dene, ancak ilerleme çubuğu %100 tamamlanana kadar onay kutusu denetiminin devre dışı bırakıldığını unutmayın. Bu ve benzer sorunları, kodlanmış UI testi için kullanılabilen çeşitli `UITestControl.WaitForControlXXX()` yöntemlerini kullanarak düzeltebilirsiniz. Sonraki yordam, bu testin başarısız olmasına neden olan sorunu düzeltmek için `WaitForControlEnabled()` yöntemini kullanmayı gösterir. Daha fazla bilgi için bkz. [kayıttan yürütme sırasında belirli olaylar Için KODLANMıŞ UI testlerini bekleme](../test/making-coded-ui-tests-wait-for-specific-events-during-playback.md).

### <a name="edit-and-rerun-the-coded-ui-test"></a>Kodlanmış Kullanıcı Arabirimi Testini Düzenleme ve Yeniden Çalıştırma

1. Test Gezgini penceresinde, başarısız testi seçin ve **StackTrace** bölümünde **UIMap. SimpleAppTest ()** için ilk bağlantıyı seçin.

2. Kodda vurgulanan hata noktasını içeren UIMap.Designer.cs dosyası açılır:

    ```csharp

    // Select 'CheckBox' check box
    uICheckBoxCheckBox.Checked = this.SimpleAppTestParams.UICheckBoxCheckBoxChecked;
    ```

3. Bu sorunu düzeltmek için, `WaitForControlEnabled()` yöntemi kullanılarak bu satıra devam etmeden önce, kodlanmış UI testinin onay kutusu denetiminin etkinleştirilmesini beklemesini sağlayabilirsiniz.

    > [!WARNING]
    > UIMap.Designer.cs dosyasını değiştirmeyin. UIMap - Kodlanmış UI Test Oluşturucusu kullanarak kodu her oluşturduğunuzda, UIMapDesigner.cs dosyasında yaptığınız herhangi bir kod değişikliğinin üzerine yazılır. Kayıtlı bir yöntemi değiştirmeniz gerekiyorsa, yöntemi UIMap.cs dosyasına kopyalayıp yeniden adlandırmanız gerekir. UIMap.cs dosyası, UIMapDesigner.cs dosyasındaki yöntemleri ve özellikleri geçersiz kılmak için kullanılabilir. Kodlanmış UITest.cs dosyasındaki orijinal yönteme başvuruyu kaldırıp yeniden adlandırılan yöntem adıyla değiştirmelisiniz.

4. Çözüm Gezgini ' de, kodlanmış UI test projenizde **UIMap. UITest** ' i bulun.

5. **UIMap. UITest** için kısayol menüsünü açın ve **Aç**' ı seçin.

     Kodlanmış UI testi kodlanmış UI Test Düzenleyicisi'nde görüntülenir. Şimdi, görüntüleyebilir ve kodlanmış UI testi düzenleyebilirsiniz.

6. **Kullanıcı Arabirimi eylem** bölmesinde, test kodu yeniden derlenme sırasında üzerine yazılmayacak özel kod işlevselliğini kolaylaştırmak için UIMap.cs veya umap. vb dosyasına taşımak istediğiniz test yöntemini (SimpleAppTest) seçin.

7. Kodlanmış UI Test Düzenleyicisi araç çubuğundaki **kodu taşı** düğmesini seçin.

8. Microsoft Visual Studio iletişim kutusu görüntülenir. Yöntem UIMap.uitest dosyasından UIMap.cs dosyasına taşınması için ve artık kodlanmış UI Test Düzenleyicisi'ni kullanarak yöntemi düzenlemenin mümkün olmayacağı konusunda uyarır. Seçin **Evet**.

     Test yöntemi UIMap.uitest dosyasından kaldırılır ve artık UI Eylemler bölmesinde görüntülenmez. Taşınan test dosyasını düzenlemek için Çözüm Gezgini'nden UIMap.cs dosyasını açın.

9. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] araç çubuğunda **Kaydet**' i seçin.

     Test yöntemi güncelleştirmeleri UIMap.Designer dosyasında kaydedilir.

    > [!CAUTION]
    > Yöntemi taşıdığınızda Kodlanmış UI Test Düzenleyicisi'ni kullanarak artık düzenleyemezsiniz. Özel kodunuzu eklemeli ve Kod Düzenleyicisi'ni kullanarak korumalısınız.

10. Yöntemi `SimpleAppTest()` `ModifiedSimpleAppTest()` olarak yeniden adlandırın

11. Aşağıdaki kullanım deyimini dosyaya ekleyin:

    ```csharp

    using Microsoft.VisualStudio.TestTools.UITesting.WpfControls;

    ```

12. Şu `WaitForControlEnabled()` yöntemi, daha önce tanımlanan sorunlu kod satırı önüne ekleyin:

    ```csharp

              uICheckBoxCheckBox.WaitForControlEnabled();

    // Select 'CheckBox' check box
    uICheckBoxCheckBox.Checked = this.SimpleAppTestParams.UICheckBoxCheckBoxChecked;

    ```

13. CodedUITest1.cs dosyasında **CodedUITestMethod** yöntemini bulun, ya da özgün SimpleAppTest () yöntemine olan başvuruyu yeniden adlandırın veya yeni ModifiedSimpleAppTest () ile değiştirin:

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

14. **Build** menüsünde **Build Solution**öğesini seçin.

15. **CodedUITestMethod** yöntemine sağ tıklayın ve **Testleri Çalıştır**' ı seçin.

16. Bu kez, kodlanmış UI testi testteki tüm adımları başarıyla tamamlar ve **geçirilen** test Gezgini penceresinde görüntülenir.

### <a name="refactor-a-control-in-the-simplewpfapp"></a>SimpleWPFApp içinde Denetimi Yeniden Düzenleme

1. MainWindow.xaml dosyasındaki Tasarımcı'da düğme denetimini seçin.

2. Özellikler penceresi en üstünde, button1 olarak **Name** özellik değerini buttonA olarak değiştirin.

3. **Build** menüsünde **Build Solution**öğesini seçin.

4. Test Gezgini 'nde **CodedUITestMethod1**çalıştırın.

     Kodlanmış UI testi button1 olarak UIMap öğesinde başlangıçta eşlenen düğme denetimini konumlandıramadığından test başarısız olur. Yeniden düzenleme kodlanmış UI testlerini bu anlamda etkileyebilir.

5. Test Gezgini penceresinde, **StackTrace** bölümünde, **uıımpa. ModifiedSimpleAppTest ()** yanındaki ilk bağlantıyı seçin.

     UIMap.cs dosyası açılır. Hata noktası kodda vurgulanır:

    ```csharp

    // Click 'Start' button
    Mouse.Click(uIStartButton, new Point(27, 10));
    ```

     Bu yordamda daha önce gelen kod satırının, yeniden düzenlenmiş Before Umap adı olan `UiStartButton`kullandığından emin olun.

     Sorunu düzeltmek için UIMap'e yeniden işlenmiş denetimi Kodlanmış UI Test Oluşturucusu kullanarak ekleyebilirsiniz. Testin kodunu, kodu kullanmak için sonraki yordamda gösterildiği şekilde güncelleştirebilirsiniz.

### <a name="map-refactored-control-and-edit-and-rerun-the-coded-ui-test"></a>Yeniden Düzenlenmiş Denetimi Eşleme ve Kodlanmış UI Testini Düzenleme ve Yeniden Çalıştırma

1. CodedUITest1.cs dosyasında, **CodedUITestMethod1 ()** yönteminde, **kodlanmış UI testi için kod üret** ' i seçin ve **kodlanmış UI Test Oluşturucusu kullan**' ı seçin.

     UIMap – Kodlanmış UI Test Oluşturucusu görünür.

2. Daha önce oluşturduğunuz masaüstü kısayolunu kullanarak, daha önce oluşturduğunuz SimpleWPFApp uygulamasını çalıştırın.

3. UIMap – Kodlanmış UI Test Oluşturucusu 'nda, ince artı aracını SimpleWPFApp üzerindeki **Başlat** düğmesine sürükleyin.

     **Başlat** düğmesi mavi bir kutu içine alınır ve kodlanmış UI test oluşturucusunun, seçili denetim için verileri işlemesi birkaç saniye sürer ve denetimlerin özelliklerini görüntüler. **Automationuid** 'in **buttonA**olarak adlandırıldığına dikkat edin.

4. Denetimin özelliklerinden, UI Denetim Eşlemesi'ni genişletmek için sol üst köşedeki oku seçin. **UIStartButton1** seçili olduğuna dikkat edin.

5. Araç çubuğunda, **UI Denetim Haritasına denetim Ekle**' yi seçin.

     Pencerenin alt kısmındaki durum, **Seçilen DENETIM UI denetim haritasına eklenmiş şekilde**eylemi doğrular.

6. UIMap – Kodlanmış UI Test Oluşturucusu 'nda **kod oluştur**' u seçin.

     Kodlanmış UI Test Oluşturucu – Kod Oluştur yeni bir yönteme gerek olmadığı notuyla görüntülenir ve bu kod yalnızca UI kontrol haritasında değişiklikler olduğunda oluşturulacaktır.

7. **Oluştur**' a tıklayın.

8. SimpleWPFApp.exe uygulamasını kapatın.

9. UIMap – Kodlanmış Kullanıcı Arabirimi Test Oluşturucusu uygulamasını kapatın.

     UIMap – Kodlanmış UI Test Oluşturucusunun UI kontrol eşlemesi değişikliklerini işlemesi bir kaç saniye alır.

10. Çözüm Gezgini'nde, UIMap.Designer.cs dosyasını açın.

11. UIMap.Designer.cs dosyasında Uıstartbutton1 özelliğini bulun. `SearchProperties` `"buttonA"`olarak ayarlandığını unutmayın:

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

     Şimdi yeni eşlenen denetimi kullanmak için kodlanmış kullanıcı arabirimini değiştirebilirsiniz. Önceki yordamda işaret edildiği gibi, kodlanmış UI testindeki herhangi bir yöntemi ya da özelliği geçersiz kılmak istiyorsanız, bunu UIMap.cs dosyasında yapmalısınız.

12. UIMap.cs dosyasında bir Oluşturucu ekleyin ve `UIStartButton` özelliğinin `SearchProperties` özelliğini, `"buttonA":` bir değeriyle `AutomationID` özelliğini kullanacak şekilde belirtin

    ```csharp

    public UIMap()
            {
                this.UIMainWindowWindow.UIStartButton.SearchProperties[WpfButton.PropertyNames.AutomationId] = "buttonA";
            }

    ```

13. **Build** menüsünde **Build Solution**öğesini seçin.

14. Test Gezgini 'nde CodedUITestMethod1 çalıştırın.

     Bu kez, kodlanmış UI testi testteki tüm adımları başarıyla tamamlar.  Test Sonuçları penceresinde **geçildi**durumunu görürsünüz.

## <a name="external-resources"></a>Dış Kaynaklar

### <a name="videos"></a>Videolar
 ![video](../data-tools/media/playvideo.gif "PlayVideo") [kodlu UI testlerine bağlantı-derin Dive-Episode1-gettingstarted](https://skydrive.live.com/?cid=2db0e1efe1c1d3b8&id=2DB0E1EFE1C1D3B8%21118)

 ![video](../data-tools/media/playvideo.gif "PlayVideo") [kodlu UI testlerine bağlantı-derin Dive-episode2-bakım kimliği ve hata ayıklama](https://skydrive.live.com/?cid=2db0e1efe1c1d3b8&id=2DB0E1EFE1C1D3B8%21116)

 ![video](../data-tools/media/playvideo.gif "PlayVideo") [kodlu UI testlerine bağlantı-derin bakış-Episode3-handkodlamaya](https://skydrive.live.com/?cid=2db0e1efe1c1d3b8&id=2DB0E1EFE1C1D3B8%21117)

### <a name="hands-on-lab"></a>Laboratuvarda eller
 [MSDN sanal Laboratuvarı: Visual Studio 2010 ile kodlanmış UI testleri oluşturmaya giriş](https://windows.microsoft.com/en-US/windows/products/windows-media-player)

### <a name="faq"></a>SSS
 [Kodlanmış UI testleri SSS-1](https://blogs.msdn.com/b/mathew_aniyan/archive/tags/faq/)

 [Kodlanmış UI testleri SSS-2](https://social.msdn.microsoft.com/Forums/en-US/vsautotest/thread/3a74dd2c-cef8-4923-abbf-7a91f489e6c4)

### <a name="forum"></a>Forum
 [Visual Studio UI Otomasyon testi (CodedUI içerir)](https://social.msdn.microsoft.com/Forums/en-US/vsautotest)

## <a name="see-also"></a>Ayrıca Bkz.
 [UI otomasyonunu kullanarak kodunuzu test](../test/use-ui-automation-to-test-your-code.md) etme [kodlanmış UI testleri ve eylem kayıtları Için](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md) kodlanmış UI [Testi Düzenleyicisi 'ni kullanarak](../test/editing-coded-ui-tests-using-the-coded-ui-test-editor.md) kodlanmış UI testlerini düzenleme [ile çalışmaya](https://msdn.microsoft.com/18e61d03-b96a-4058-a166-8ec6b3f6116b) başlama
