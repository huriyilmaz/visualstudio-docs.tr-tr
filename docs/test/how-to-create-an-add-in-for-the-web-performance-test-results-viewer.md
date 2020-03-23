---
title: Web Performans Testi Sonuçları Görüntüleyici için Eklenti Oluşturma
ms.date: 10/20/2016
ms.topic: conceptual
helpviewer_keywords:
- Web performance tests, Visual Studio Add-in
- Visual Studio Add-in, Web performance tests
ms.assetid: 1118c604-4b1b-4b21-a04e-45995b676fa8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a6da2686a5a68325101e7161a51a8144e7ef42b6
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75589090"
---
# <a name="how-to-create-an-add-in-for-the-web-performance-test-results-viewer"></a>Nasıl yapilir: Web Performans Testi Sonuçları Görüntüleyicisi için eklenti oluşturma

Web Performans Testi Sonuçları **Görüntüleyicisi** için kullanıcı arasını aşağıdaki ad alanlarını kullanarak genişletebilirsiniz:

- <xref:Microsoft.VisualStudio.TestTools.LoadTesting>

- <xref:Microsoft.VisualStudio.TestTools.WebTesting>

Ayrıca, *%ProgramFiles(x86)%\Microsoft Visual Studio\\\<sürümü nde* bulunan LoadTestPackage DLL'ye bir başvuru eklemeniz gerekir>\Enterprise\Common7\IDE\PrivateAssemblies klasöründe.

**Web Performans Testi Sonuçları Görüntüleyen'in**Kullanıcı Arama Bilgi Sini'ni genişletmek için bir Visual Studio eklentisi ve kullanıcı denetimi oluşturmanız gerekir. Aşağıdaki yordamlar eklentinin nasıl oluşturulacağını, kullanıcı denetiminin nasıl oluşturulacağını ve **Web Performans Testi Sonuçları Görüntüleyen'in**Kullanıcı UI'sini genişletmek için gereken sınıfların nasıl uygulanacağını açıklar.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="create-or-open-a-solution-that-contains-an-aspnet-web-application-and-a-web-performance-and-load-test-project"></a>ASP.NET web uygulaması ve web performansı ve yük testi projesi içeren bir çözüm oluşturma veya açma

### <a name="to-prepare-for-extending-the-web-performance-test-results-viewer"></a>Web Performans Testi Sonuçları Görüntüleyici'yi genişletmeye hazırlanmak için

ASP.NET web uygulaması için bir veya daha fazla web performans testi ile ASP.NET bir web uygulaması ve web performansı ve yük testi projesi içeren deneme yapabileceğiniz üretim dışı bir çözüm oluşturun veya açın.

> [!NOTE]
> [Nasıl Yapılır: Web hizmeti testi oluşturma](../test/how-to-create-a-web-service-test.md) ve kodlanmış bir web performans testi oluştur ve [çalıştırın](../test/generate-and-run-a-coded-web-performance-test.md)yordamları izleyerek web performans testleri içeren ASP.NET bir web uygulaması ve yük testi projesi oluşturabilirsiniz.

## <a name="create-a-visual-studio-add-in"></a>Visual Studio eklentisi oluşturma

Eklenti, Visual Studio tümleşik geliştirme ortamında (IDE) çalışan derlenmiş bir DLL'dir. Derleme fikri mülkiyetkorumanıza yardımcı olur ve performansı artırır. Eklentileri el ile oluşturabiliyor olsanız da, **Eklenti Sihirbazı'nı**kullanmayı daha kolay bulabilirsiniz. Bu sihirbaz, oluşturduktan hemen sonra çalıştırabileceğiniz işlevsel ama temel bir eklenti oluşturur. Eklenti **Sihirbazı** temel programı oluşturduktan sonra, temel programı kod ekleyebilir ve özelleştirebilirsiniz.

**Eklenti Sihirbazı,** eklentiniz için bir görüntü adı ve açıklama sağlamanıza olanak tanır. Her ikisi de **Eklenti Yöneticisi'nde**görünür. İsteğe bağlı olarak, eklentiyi açmak için **Araçlar** menüsüne bir komut ekleyen kod oluşturma sihirbazı olabilir. Eklentiniz için özel Bir **Hakkında** iletişim kutusu görüntülemeyi de seçebilirsiniz. Sihirbaz bittiğinde, eklentiyi uygulayan yalnızca bir sınıfa sahip yeni bir projeniz vardır. Bu sınıfın adı Connect.

Bu makalenin sonunda **Eklenti Yöneticisi'ni** kullanacaksınız.

### <a name="to-create-an-add-in-by-using-the-add-in-wizard"></a>Eklenti Sihirbazı'nı kullanarak eklenti oluşturmak için

1. **Çözüm Gezgini'nde,** çözüme sağ tıklayın, **Ekle'yi**seçin ve ardından **Yeni Proje'yi**seçin.

2. Yeni bir **Visual Studio Eklenti** projesi oluşturun.

    Visual Studio **Eklenti Sihirbazı** başlar.

3. **İleri**’yi seçin.

4. Programlama **Dili Seç** sayfasında, eklentiyi yazmak için kullanmak istediğiniz programlama dilini seçin.

   > [!NOTE]
   > Bu konu örnek kod için Visual C# kullanır.

5. Uygulama **Ana Bilgisayar Seç** sayfasında **Visual Studio'yu** seçin ve Visual **Studio Makrolarını**temizleyin.

6. **İleri**’yi seçin.

7. Ad ve Açıklama Gir sayfasında eklentiniz için **bir ad ve** açıklama yazın.

     Eklenti oluşturulduktan sonra, adı ve açıklaması **Ekle Yöneticisi'ndeki** **Kullanılabilir Eklentiler** listesinde görüntülenir. Kullanıcıların eklentinizin ne işe yaradığını, nasıl çalıştığını ve daha önce öğrenebilmeleri için eklentinizin açıklamasına yeterli ayrıntı ekleyin.

8. **İleri**’yi seçin.

9. Ekle **Seçenekleri** seç sayfasında, **ana bilgisayar uygulaması başladığında Eklentimin yüklenmesini istiyorum'u**seçin.

10. Kalan onay kutularını temizleyin.

11. **'Hakkında Yardım' Bilgileri** seç sayfasında, eklentiniz hakkındaki bilgilerin **Hakkında** iletişim kutusunda görüntülenmesini isteyip istemediğiniz belirtebilirsiniz. Bilgilerin görüntülenmesini istiyorsanız, Evet'i **seçin, Eklentimin 'Hakkında' kutu bilgileri** onay kutusunu sunmasını istiyorum.

     Visual Studio **About** iletişim kutusuhakkında eklenebilir bilgiler sürüm numarası, destek ayrıntıları, lisans verileri ve benzeri içerir.

12. **İleri**’yi seçin.

13. Seçtiğiniz seçenekler, gözden geçirmeniz için **Özet** sayfasında görüntülenir. Memnun sanız, eklentiyi oluşturmak için **Finish'i** seçin. Bir şeyi değiştirmek istiyorsanız, **Geri Düğmesini** seçin.

     Yeni çözüm ve proje oluşturulur ve yeni eklenti için *Connect.cs* dosyası **Kod Düzenleyicisi**görüntülenir.

     Bu WebPerfTestResultsViewerAddin projesi tarafından başvurulacak bir kullanıcı denetimi oluşturur aşağıdaki yordamdan sonra *Connect.cs* dosyasına kod eklersiniz.

    Eklenti oluşturulduktan sonra, **Eklenti Yöneticisi'nde**etkinleştirilmeden önce eklentiyi Visual Studio'ya kaydetmeniz gerekir. *Bunu,.addin* dosya adı uzantısı olan bir XML dosyası kullanarak yaparsınız.

    *.addin* dosyası, Visual Studio eklentisini **Add-In Manager'da**görüntülemek için gereken bilgileri açıklar. Visual Studio başladığında, kullanılabilir *.addin* dosyaları için *.addin* dosya konumunda görünür. Herhangi bir bulursa, XML dosyasını okur ve **Add-In Manager'a** tıklatıldığında eklentiyi başlatmak için gereken bilgileri verir.

    *.addin* dosyası, **Eklenti Sihirbazı**kullanılarak bir eklenti oluşturduğunuzda otomatik olarak oluşturulur.

### <a name="add-in-file-locations"></a>Eklenti dosya konumları

*.addin* dosyalarının iki kopyası **Ekle Sihirbazı**tarafından otomatik olarak oluşturulur ve aşağıdaki gibi:

|**. Dosya Konumunu Ekle**|**Açıklama**|
|-|----------------------------|-|
|Kök proje klasörü|Eklenti projesinin dağıtımı için kullanılır. Düzenleme kolaylığı için projeye dahil ve XCopy tarzı dağıtım için yerel bir yol vardır.|
|Eklenti klasörü|Hata ayıklama ortamında eklentiyi çalıştırmak için kullanılır. Her zaman geçerli yapı yapılandırmasının çıkış yolunu işaret etmelidir.|

## <a name="create-a-windows-form-control-library-project"></a>Windows Form Denetim Kitaplığı projesi oluşturma

Önceki yordamda oluşturulan Visual Studio eklentisi, bir <xref:System.Windows.Forms.UserControl> sınıfın örneğini oluşturmak için Windows Forms Control Library projesine başvurur.

### <a name="to-create-a-control-to-be-used-in-the-web-test-results-viewer"></a>Web Test Sonuçları Görüntüleyici'nde kullanılacak bir denetim oluşturmak için

1. **Çözüm Gezgini'nde,** çözüme sağ tıklayın, **Ekle'yi**seçin ve ardından **Yeni Proje'yi**seçin.

2. Yeni bir **Windows Forms Denetim Kitaplığı** projesi oluşturun.

3. Araç **Kutusundan,** kullanıcıDenetimi1 yüzeyine bir <xref:System.Windows.Forms.DataGridView> sürükleyin.

4. Sağ üst köşesindeki eylem![etiketi glyph 'yi (Smart Tag Glyph)](../test/media/vs_winformsmttagglyph.gif)tıklatın <xref:System.Windows.Forms.DataGridView> ve aşağıdaki adımları izleyin:

    1. **Üst Kapsayıcıda Dock'u**seçin.

    2. **Eklemeyi Etkinleştir**, **Düzenlemeyi Etkinleştir,** **Silmeyi Etkinleştir** ve **Sütun Yeniden Sıralama'yı Etkinleştirme**için onay kutularını temizleyin.

    3. **Sütun Ekle'yi**seçin.

         **Sütun Ekle** iletişim kutusu görüntülenir.

    4. **Tür** açılır listesinde **DataGridViewTextBoxColumn'u**seçin.

    5. **Üstbilgi metnindeki**"Sütun1" metnini temizleyin.

    6. **Ekle'yi**seçin.

    7. **Kapat'ı**seçin.

5. **Özellikler** penceresinde, **resultControlDataGridView**için <xref:System.Windows.Forms.DataGridView> **(Ad)** özelliğini değiştirin.

6. Tasarım yüzeyine sağ tıklayın ve **Kodu Görüntüle'yi**seçin.

     UserControl1.cs *UserControl1.cs* dosyası Kod Düzenleyicisi'nde görüntülenir. **Code Editor**

7. Anında alınan <xref:System.Windows.Forms.UserControl> sınıfın adını UserContro1'den sonuçDenetimi'ne değiştirin:

    ```csharp
    namespace WebPerfTestResultsViewerControl
    {
        public partial class resultControl : UserControl
        {
            public resultControl()
            {
                InitializeComponent();
            }
    ```

     Sonraki yordamda, webperfTestResultsViewerAddin projenin *Connect.cs* dosyasına kod eklersiniz, bu da sonuçDenetim sınıfına başvurur.

     Daha sonra *Connect.cs* dosyasına bazı ek kodlar ekleyeceğiz.

## <a name="add-code-to-the-webperftestresultsvieweraddin"></a>WebPerfTestResultsViewerAddin kod ekle

1. **Çözüm Gezgini'nde,** WebPerfTestResultsViewerAddin projesindeki **Başvuru** düğümüne sağ tıklayın ve **Referans Ekle'yi**seçin.

2. Başvuru **Ekle** iletişim kutusunda **.NET** sekmesini seçin.

3. Aşağı kaydırın ve **Microsoft.VisualStudio.QualityTools.WebTestFramework** ve **System.Windows.Forms**seçin.

4. **Tamam'ı**seçin.

5. **Başvurular** düğümünü yeniden sağ tıklatın ve **Başvuru Ekle'yi**seçin.

6. Başvuru **Ekle** iletişim kutusunda **Gözat** sekmesini seçin.

7. **Görünüm** için açılır menüden seçeneği belirleyin ve *%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\PrivateAssemblies'e* gidin ve *Microsoft.VisualStudio.QualityTools.LoadTestPackage.dll* dosyasını seçin.

8. **Tamam'ı**seçin.

9. WebPerfTestResultsViewerAddin proje düğümüne sağ tıklayın ve **Referans Ekle'yi**seçin.

10. Başvuru **Ekle** iletişim kutusunda **Projeler** sekmesini seçin.

11. **Proje Adı**altında, **WebPerfTestResultsViewerControl** projesini seçin ve **Tamam'ı**seçin.

12. *Connect.cs* dosyası hala açık değilse, **Solution Explorer'da,** WebPerfTestResultsViewerAddin projesindeki **Connect.cs** dosyayı sağ tıklatın ve **Kodu Görüntüle'yi**seçin.

13. *Connect.cs* dosyasına aşağıdaki ifadeleri ekleyin:

    ```csharp
    using System.IO;
    using System.Windows.Forms;
    using System.Collections.Generic;
    using Microsoft.VisualStudio.TestTools.LoadTesting;
    using Microsoft.VisualStudio.TestTools.WebTesting;
    using WebPerfTestResultsViewerControl;
    ```

14. *Connect.cs* dosyasının altına doğru ilerleyin. Web Performans Testi Sonuçları <xref:System.Windows.Forms.UserControl> **Görüntüleyicisi'nin** birden fazla örneğinin açık olması durumunda GUI'lerin bir listesini eklemeniz gerekir. Daha sonra bu listeyi kullanan kod eklersiniz.

     Daha sonra kodlayacağınız OnDiscconection yönteminde ikinci bir string Listesi kullanılır.

    ```csharp
    private DTE2 _applicationObject;
    private AddIn _addInInstance;

    private Dictionary<Guid, List<UserControl>> m_controls = new Dictionary<Guid, List<UserControl>>();        private List<string> temporaryFilePaths = new List<string>();
    ```

15. *Connect.cs* dosyası, <xref:Extensibility.IDTExtensibility2> sınıftan Bağlan adlı bir sınıfı anlık olarak kullanır ve Visual Studio eklentisini uygulamak için bazı yöntemler de içerir. Yöntemlerden biri, eklentinin yüklendiğine dair bildirim alan OnConnection yöntemidir. OnConnection yönteminde, **Web Performans Testi Sonuçları Görüntüleyici**için genişletilebilirlik paketinizi oluşturmak için LoadTestPackageExt sınıfını kullanacaksınız. OnConnection yöntemine aşağıdaki kodu ekleyin:

    ```csharp
    public void OnConnection(object application, ext_ConnectMode connectMode, object addInInst, ref Array custom)
                {
                _applicationObject = (DTE2)application;
                _addInInstance = (AddIn)addInInst;

                // Create a load test packge extensibility class.            LoadTestPackageExt loadTestPackageExt = _applicationObject.GetObject("Microsoft.VisualStudio.TestTools.LoadTesting.LoadTestPackageExt") as LoadTestPackageExt;            // Process open windows.            foreach (WebTestResultViewer webTestResultViewer in loadTestPackageExt.WebTestResultViewerExt.ResultWindows)            {                WindowCreated(webTestResultViewer);            }            // Create event handlers.            loadTestPackageExt.WebTestResultViewerExt.WindowCreated += new EventHandler<WebTestResultViewerExt.WindowCreatedEventArgs>(WebTestResultViewerExt_WindowCreated);            loadTestPackageExt.WebTestResultViewerExt.WindowClosed += new EventHandler<WebTestResultViewerExt.WindowClosedEventArgs>(WebTesResultViewer_WindowClosed);            loadTestPackageExt.WebTestResultViewerExt.SelectionChanged += new EventHandler<WebTestResultViewerExt.SelectionChangedEventArgs>(WebTestResultViewer_SelectedChanged);
            }
    ```

16. OnConnection yöntemine ve WindowCreated yöntemine eklediğiniz loadTestPackageExt.WebTestResultViewerExt.WindowCreated olay işleyicisi için WebTestResultViewerExt_WindowCreated yöntemini oluşturmak için connect sınıfına aşağıdaki kodu ekleyin WebTestResultViewerExt_WindowCreated yöntemi çağırır.

    ```csharp
            void WebTestResultViewerExt_WindowCreated(object sender, WebTestResultViewerExt.WindowCreatedEventArgs e)
            {
                // New control added to new result viewer window.
                WindowCreated(e.WebTestResultViewer);
            }

    private void WindowCreated(WebTestResultViewer viewer)        {            // Instantiate an instance of the resultControl referenced in the WebPerfTestResultsViewerControl project.
                resultControl resultControl = new resultControl();            // Add to the dictionary of open playback windows.            System.Diagnostics.Debug.Assert(!m_controls.ContainsKey(viewer.TestResultId));            List<UserControl> userControls = new List<UserControl>();            userControls.Add(resultControl);            // Add Guid to the m_control List to manage Result viewers and controls.            m_controls.Add(viewer.TestResultId, userControls);            // Add tabs to the playback control.            resultControl.Dock = DockStyle.Fill;            viewer.AddResultPage(new Guid(), "Sample", resultControl);        }
    ```

17. OnConnection yöntemine eklediğiniz loadTestPackageExt.WebTestResultViewerExt.SelectionChanged olay işleyicisi için WebTestResultViewer_SelectedChanged yöntemini oluşturmak için connect sınıfına aşağıdaki kodu ekleyin:

    ```csharp
    void WebTestResultViewer_SelectedChanged(object sender, WebTestResultViewerExt.SelectionChangedEventArgs e)
    {
        foreach (UserControl userControl in m_controls[e.TestResultId])            {                // Update the userControl in each result viewer.                resultControl resultControl = userControl as resultControl;                if (resultControl != null)                    // Call the resultControl's Update method (This will be added in the next procedure).                    resultControl.Update(e.WebTestRequestResult);            }
    }
    ```

18. OnConnection yöntemine eklediğiniz loadTestPackageExt.WebTestResultViewerExt.WindowClosed için olay işleyicisi için WebTesResultViewer_WindowClosed yöntemini oluşturmak için connect sınıfına aşağıdaki kodu ekleyin:

    ```csharp
    void WebTesResultViewer_WindowClosed(object sender, WebTestResultViewerExt.WindowClosedEventArgs e)
    {
        if (m_controls.ContainsKey(e.WebTestResultViewer.TestResultId))
        {
            m_controls.Remove(e.WebTestResultViewer.TestResultId);
        }
    }
    ```

     Artık Visual Studio eklentisi için kod tamamlandığından, WebPerfTestResultsViewerControl projesinde sonuçDenetimi'ne Güncelleştirme yöntemini eklemeniz gerekir.

## <a name="add-code-to-the-webperftestresultsviewercontrol"></a>WebPerfTestResultsViewerControl kodu ekle

1. **Çözüm Gezgini'nde,** WebPerfTestResultsViewerControl proje düğümüne sağ tıklayın ve **Özellikleri**seçin.

2. **Uygulama** sekmesini seçin ve ardından **Hedef çerçeve** açılır listesini seçin ve **.NET Framework 4** (veya sonraki) seçeneğini belirleyin. **Özellikler** penceresini kapatın.

   Bu, **Web Performans Testi Sonuçları Görüntüleyicisi'ni**genişletmek için gereken DLL başvurularını desteklemek için gereklidir.

3. **Solution Explorer'da,** WebPerfTestResultsViewerControl projesinde, **Referans** düğümünü sağ tıklatın ve Referans **Ekle'yi**seçin.

4. Başvuru **Ekle** iletişim kutusunda **.NET** sekmesini tıklatın.

5. Aşağı kaydırın ve **Microsoft.VisualStudio.QualityTools.WebTestFramework**seçin.

6. **Tamam'ı**seçin.

7. *UserControl1.cs* dosyasına aşağıdaki ifadeleri ekleyin:

    ```csharp
    using Microsoft.VisualStudio.TestTools.WebTesting;
    using Microsoft.VisualStudio.TestTools.WebTesting.Rules;
    ```

8. *Connect.cs* dosyasında WebPerfTestResultsViewerAddin WebTestResultViewer_SelectedChanged yönteminden webTestRequestResult olarak adlandırılan ve geçirilen Güncelleştirme yöntemini ekleyin. Güncelleştirme yöntemi, DataGridView'ı WebTestRequestResult'da çeşitli özelliklerle doldurur.

    ```csharp
    public void Update(WebTestRequestResult WebTestResults)
            {
                // Clear the DataGridView when a request is selected.
                resultControlDataGridView.Rows.Clear();
                // Populate the DataGridControl with properties from the WebTestResults.
                this.resultControlDataGridView.Rows.Add("Request: " + WebTestResults.Request.Url.ToString());
                this.resultControlDataGridView.Rows.Add("Response: " + WebTestResults.Response.ResponseUri.ToString());
                foreach (RuleResult ruleResult in WebTestResults.ExtractionRuleResults)
                {
                    this.resultControlDataGridView.Rows.Add("Extraction rule results: " + ruleResult.Message.ToString());
                }
                foreach (RuleResult ruleResult in WebTestResults.ValidationRuleResults)
                {
                    this.resultControlDataGridView.Rows.Add("Validation rule results: " + ruleResult.Message.ToString());
                }
                foreach (WebTestError webTestError in WebTestResults.Errors)
                {
                    this.resultControlDataGridView.Rows.Add("Error: " + webTestError.ErrorType.ToString() + " " + webTestError.ErrorSubtype.ToString() + " " + webTestError.ExceptionText.ToString());
                }
            }
    ```

## <a name="build-the-solution"></a>Çözümü derleme

- **Yapı** menüsünde **Çözüm Oluştur'u**seçin.

## <a name="register-the-webperftestresultsvieweraddin-add-in"></a>WebPerfTestResultsViewerAddin eklentisini kaydedin

1. **Araçlar** menüsünde **Add-in Manager'ı**seçin.

2. **Add-in Manager** iletişim kutusu görüntülenir.

3. **Kullanılabilir Eklentiler** sütunundaki WebPerfTestResultsViewerAddin eklentisinin onay kutusunu seçin ve **Başlangıç** ve Komut **Satırı** sütunlarının altındaki onay kutularını temizleyin.

4. **Tamam'ı**seçin.

## <a name="run-the-web-performance-test-using-the-web-test-results-viewer"></a>Web Test Sonuçları Görüntüleyici'yi kullanarak web performans testini çalıştırın

1. Web performans testi çalıştırın ve WebPerfTestResultsViewerAddin eklentisi yeni sekmesi Örnek **Web Performans Testi Sonuçları Görüntüleyici**görüntülenen göreceksiniz.

2. DataGridView'da sunulan özellikleri görmek için sekmeyi seçin.

## <a name="net-security"></a>.NET güvenlik

Kötü amaçlı eklentilerin otomatik olarak etkinleştirmesini önleyerek güvenliği artırmak için Visual Studio, **Eklenti/Makrolar Güvenliği**adlı **araç seçenekleri** sayfasında ayarlar sağlar.

Buna ek olarak, bu seçenekler sayfası Visual Studio'nun aradığı klasörleri belirtmenize olanak *tanır. AddIn* kayıt dosyaları. Bu, konumları sınırlamanıza izin vererek güvenliği *artırır. AddIn* kayıt dosyaları okunabilir. Bu kötü amaçlı önlemeye yardımcı *olur. AddIn* dosyaları istemeden kullanılıyor.

**Eklenti Güvenlik Ayarları**

Eklenti güvenliği için seçenekler sayfasındaki ayarlar aşağıdaki gibidir:

- **Eklenti bileşenlerinin yüklenmesine izin verin.** Varsayılan olarak seçilidir. Seçildiğinde Visual Studio'da eklentilerin yüklenmesine izin verilir. Seçilmediğinde, Visual Studio'da eklentilerin yüklenmesi yasaktır.

- **Eklenti bileşenlerinin URL'den yüklenmesine izin verin.** Varsayılan olarak seçilmedi. Seçildiğinde, eklentiler harici web sitelerinden yüklenebilir. Seçilmediğinde, uzaktan eklentilerin Visual Studio'da yüklenmesi yasaktır. Bir eklenti nedense yüklenemıyorsa, Web'den yüklenemez. Bu ayar yalnızca eklenti DLL yükleme denetler. *Şey. Addin* kayıt dosyaları her zaman yerel sistemde bulunmalıdır.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.UserControl>
- <xref:Microsoft.VisualStudio.TestTools.LoadTesting>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules>
- <xref:System.Windows.Forms.UserControl>
- <xref:System.Windows.Forms.DataGrid>
- [Yük testleri için özel kod ve eklentiler oluşturma](../test/create-custom-code-and-plug-ins-for-load-tests.md)
