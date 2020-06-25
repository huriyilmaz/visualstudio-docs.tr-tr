---
title: Web performans Test Sonuçları Görüntüleyicisi için eklenti oluşturma
ms.date: 10/20/2016
ms.topic: how-to
helpviewer_keywords:
- Web performance tests, Visual Studio Add-in
- Visual Studio Add-in, Web performance tests
ms.assetid: 1118c604-4b1b-4b21-a04e-45995b676fa8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 736c43a83a956c02b760b4909a427a82c6fa9e4c
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85287837"
---
# <a name="how-to-create-an-add-in-for-the-web-performance-test-results-viewer"></a>Nasıl yapılır: Web performans Test Sonuçları Görüntüleyicisi için eklenti oluşturma

Aşağıdaki ad alanlarını kullanarak **Web performans test sonuçları görüntüleyicisine** yönelik kullanıcı arabirimini genişletebilirsiniz:

- <xref:Microsoft.VisualStudio.TestTools.LoadTesting>

- <xref:Microsoft.VisualStudio.TestTools.WebTesting>

Ayrıca, *% ProgramFiles (x86)% \ Microsoft Visual Studio \\ \<version> \Enterprise\Common7\IDE\PrivateAssemblies* KLASÖRÜNDE bulunan LoadTestPackage dll dosyasına bir başvuru eklemeniz gerekir.

**Web performansı test sonuçları görüntüleyicisinin**Kullanıcı arabirimini genişletmek için, bir Visual Studio eklentisi ve bir kullanıcı denetimi oluşturmanız gerekir. Aşağıdaki yordamlarda, eklentinin nasıl oluşturulacağı, Kullanıcı denetiminin ve **Web performans test sonuçları görüntüleyicisinin**Kullanıcı arabirimini genişletmek için gerekli sınıfların nasıl uygulanacağı açıklanmaktadır.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="create-or-open-a-solution-that-contains-an-aspnet-web-application-and-a-web-performance-and-load-test-project"></a>ASP.NET Web uygulaması ve Web performansı ve yük testi projesi içeren bir çözüm oluşturun veya açın

### <a name="to-prepare-for-extending-the-web-performance-test-results-viewer"></a>Web performans Test Sonuçları görüntüleyicisini genişletmeye hazırlanmak için

ASP.NET Web uygulaması için bir veya daha fazla Web performans testine sahip bir ASP.NET Web uygulaması ve bir Web performansı ve yük testi projesi içeren deneydiğimiz bir üretim dışı çözümü oluşturun ya da açın.

> [!NOTE]
> [Nasıl yapılır: Web hizmeti testi oluşturma](../test/how-to-create-a-web-service-test.md) ve [kodlanmış Web performans testi oluşturma ve çalıştırma](../test/generate-and-run-a-coded-web-performance-test.md)konusundaki yordamları izleyerek Web performans testlerini içeren bir ASP.NET Web uygulaması ve Web performansı ve yük testi projesi oluşturabilirsiniz.

## <a name="create-a-visual-studio-add-in"></a>Visual Studio eklentisi oluşturma

Bir eklenti, Visual Studio tümleşik geliştirme ortamında (IDE) çalışan derlenmiş bir DLL 'dir. Derleme fikri mülkiyet bilgilerinizi korumanıza yardımcı olur ve performansı geliştirir. Eklentileri el ile oluşturabilseniz de, **Eklenti Sihirbazı**'nı kullanmayı daha kolay bulabilirsiniz. Bu sihirbaz, oluşturduktan hemen sonra çalıştırabileceğiniz bir işlevsel ancak temel bir eklenti oluşturur. **Eklenti Sihirbazı** temel programı oluşturduktan sonra, ona kod ekleyebilir ve onu özelleştirebilirsiniz.

Eklenti **Sihirbazı** , eklenti için bir görünen ad ve açıklama sağlamanıza olanak tanır. Her ikisi de **Eklenti Yöneticisi**'nde görünür. İsteğe bağlı olarak, sihirbazın, eklentiyi açmak için **Araçlar** menüsüne bir komut ekleyen kodu oluşturmasını sağlayabilirsiniz. Ayrıca, eklenti **için özel bir iletişim kutusu görüntülemeyi** de seçebilirsiniz. Sihirbaz tamamlandığında, eklentiyi uygulayan tek bir sınıfı olan yeni bir projeniz olur. Bu sınıf Connect olarak adlandırılır.

Bu makalenin sonundaki **eklenti yöneticisini** kullanacaksınız.

### <a name="to-create-an-add-in-by-using-the-add-in-wizard"></a>Eklenti Sihirbazı 'Nı kullanarak eklenti oluşturmak için

1. **Çözüm Gezgini**, çözüme sağ tıklayın, **Ekle**' yi seçin ve ardından **Yeni proje**' yi seçin.

2. Yeni bir **Visual Studio eklenti** projesi oluşturun.

    Visual Studio **Eklenti Sihirbazı** başlatılır.

3. **İleri**’yi seçin.

4. **Bir programlama dili seçin** sayfasında, eklentiyi yazmak için kullanmak istediğiniz programlama dilini seçin.

   > [!NOTE]
   > Bu konu, örnek kod Için Visual C# kullanır.

5. **Uygulama Konağı seçin** sayfasında, **Visual Studio** ' yı seçin ve **Visual Studio makrolarını**temizleyin.

6. **İleri**’yi seçin.

7. **Bir ad ve açıklama girin** sayfasında, eklenti için bir ad ve açıklama yazın.

     Eklenti oluşturulduktan sonra, adı ve açıklaması **Eklenti Yöneticisi**' nde **kullanılabilir eklentiler** listesinde görüntülenir. Kullanıcılarınızın eklentisinin ne yaptığını, nasıl çalıştığını vb. öğrenmeleri için, eklenti açıklamasına yeterince ayrıntı ekleyin.

8. **İleri**’yi seçin.

9. **Eklenti seçeneklerini seçin** sayfasında, **eklentinin konak uygulaması başladığında yüklenmesini istiyorum**' u seçin.

10. Kalan onay kutularını temizleyin.

11. **' Yardım hakkında ' bilgilerini seçme** sayfasında, eklenti hakkındaki bilgilerin **hakkında** iletişim kutusunda gösterilmesini isteyip istemediğinizi belirtebilirsiniz. Bilgilerin görüntülenmesini isterseniz, **Evet ' i seçin, Eklentimin ' hakkında ' kutusu bilgilerini sunmasını** istiyorum onay kutusunu işaretleyin.

     Visual Studio **hakkında** iletişim kutusuna eklenebilen bilgiler, sürüm numarası, destek ayrıntıları, lisanslama verileri vb. içerir.

12. **İleri**’yi seçin.

13. Seçtiğiniz seçenekler, gözden geçirmeniz için **Özet** sayfasında görüntülenir. Memnun kaldıysanız, eklentiyi oluşturmak için **son** ' u seçin. Bir değişiklik yapmak istiyorsanız **geri** düğmesini seçin.

     Yeni çözüm ve proje oluşturulur ve yeni eklenti için *Connect.cs* dosyası **kod düzenleyicisinde**görüntülenir.

     Aşağıdaki yordamdan sonra *Connect.cs* dosyasına kod ekleyeceksiniz. Bu, bu WebPerfTestResultsViewerAddin projesi tarafından başvurulacak bir kullanıcı denetimi oluşturur.

    Bir eklenti oluşturulduktan sonra, **Eklenti Yöneticisi**'nde etkinleştirilmeden önce Visual Studio ile kaydetmeniz gerekir. Bunu, *. AddIn* dosya adı uzantısına sahıp bir XML dosyası kullanarak yapabilirsiniz.

    *. Addin* dosyası, Visual Studio 'nun eklentiyi eklenti **Yöneticisi**'nde görüntülemesi için gereken bilgileri açıklar. Visual Studio başlatıldığında, kullanılabilir *. addin* dosyaları için *. addin* dosya konumuna bakar. Herhangi bir bulursa, XML dosyasını okur ve **Eklenti Yöneticisi** 'nin tıklandığında eklentiyi başlatması için ihtiyaç duyduğu bilgileri verir.

    *. Addin* dosyası, eklenti **Sihirbazı 'nı**kullanarak bir eklenti oluşturduğunuzda otomatik olarak oluşturulur.

### <a name="add-in-file-locations"></a>Eklenti dosyası konumları

*. Addin* dosyalarının iki kopyası, **Eklenti Sihirbazı**tarafından aşağıdaki gibi otomatik olarak oluşturulur:

|**. Eklenti dosyası konumu**|**Açıklama**|
|-|----------------------------|-|
|Kök proje klasörü|Eklenti projesinin dağıtımı için kullanılır. Proje, düzenlenecek ve XCopy stili dağıtım için yerel yola sahip olmak üzere kolayca bulunur.|
|Eklenti klasörü|Eklentiyi hata ayıklama ortamında çalıştırmak için kullanılır. Her zaman geçerli derleme yapılandırmasının çıkış yolunu işaret etmelidir.|

## <a name="create-a-windows-form-control-library-project"></a>Windows Form denetim kitaplığı projesi oluşturma

Önceki yordamda oluşturulan Visual Studio eklentisi bir sınıf örneği oluşturmak için bir Windows Forms denetim kitaplığı projesine başvurur <xref:System.Windows.Forms.UserControl> .

### <a name="to-create-a-control-to-be-used-in-the-web-test-results-viewer"></a>Web Test Sonuçları görüntüleyicisinde kullanılacak bir denetim oluşturmak için

1. **Çözüm Gezgini**, çözüme sağ tıklayın, **Ekle**' yi seçin ve ardından **Yeni proje**' yi seçin.

2. Yeni bir **Windows Forms denetim kitaplığı** projesi oluşturun.

3. **Araç kutusundan**, <xref:System.Windows.Forms.DataGridView> UserControl1 yüzeyine sürükleyin.

4. Sağ üst köşesindeki eylem etiketi glifi ' ne ( ![ akıllı etiket karakter ](../test/media/vs_winformsmttagglyph.gif) ) tıklayın <xref:System.Windows.Forms.DataGridView> ve şu adımları izleyin:

    1. **Üst kapsayıcıda yerleştir '** i seçin.

    2. **Ekleme**, **düzenleme etkinleştirme**, **silme** ve **sütun yeniden sıralamayı**etkinleştirme için onay kutularını temizleyin.

    3. **Sütun Ekle**' yi seçin.

         **Sütun Ekle** iletişim kutusu görüntülenir.

    4. **Tür** açılan listesinde **DataGridViewTextBoxColumn**' ı seçin.

    5. **Üstbilgi metninde**"Sütun1" metnini temizleyin.

    6. **Ekle**' yi seçin.

    7. **Kapat**' ı seçin.

5. **Özellikler** penceresinde, ' ın **(Name)** özelliğini <xref:System.Windows.Forms.DataGridView> **resultControlDataGridView**olarak değiştirin.

6. Tasarım yüzeyine sağ tıklayın ve **kodu görüntüle**' yi seçin.

     *UserControl1.cs* dosyası **kod düzenleyicisinde**görüntülenir.

7. Örneklenmiş <xref:System.Windows.Forms.UserControl> sınıfın adını UserContro1 öğesinden resultControl olarak değiştirin:

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

     Bir sonraki yordamda, WebPerfTestResultsViewerAddin projesinin *Connect.cs* dosyasına kod ekleyeceksiniz, bu da resultControl sınıfına başvurur.

     Daha sonra *Connect.cs* dosyasına bazı ek kodlar ekleyirsiniz.

## <a name="add-code-to-the-webperftestresultsvieweraddin"></a>WebPerfTestResultsViewerAddin 'a kod ekleme

1. **Çözüm Gezgini**, WebPerfTestResultsViewerAddin projesindeki **Başvurular** düğümüne sağ tıklayın ve **Başvuru Ekle**' yi seçin.

2. **Başvuru Ekle** iletişim kutusunda **.net** sekmesini seçin.

3. Aşağı kaydırın ve **Microsoft. VisualStudio. QualityTools. WebTestFramework** ve **System. Windows. Forms**öğesini seçin.

4. **Tamam ' ı**seçin.

5. **Başvurular** düğümüne tekrar sağ tıklayın ve **Başvuru Ekle**' yi seçin.

6. **Başvuru Ekle** iletişim kutusunda, **Gözden** geçirme sekmesini seçin.

7. **Ara '** yı seçin ve *% ProgramFiles (x86)% \ Microsoft Visual Studio\2017\Enterprise\Common7\IDE\PrivateAssemblies* ' a gidin ve *Microsoft.VisualStudio.QualityTools.LoadTestPackage.dll* dosyasını seçin.

8. **Tamam ' ı**seçin.

9. WebPerfTestResultsViewerAddin proje düğümüne sağ tıklayın ve **Başvuru Ekle**' yi seçin.

10. **Başvuru Ekle** iletişim kutusunda, **Projeler** sekmesini seçin.

11. **Proje adı**altında **WebPerfTestResultsViewerControl** projesini seçin ve **Tamam**' ı seçin.

12. *Connect.cs* dosyası hala açık değilse, **Çözüm Gezgini**' de WebPerfTestResultsViewerAddin projesindeki **Connect.cs** dosyasına sağ tıklayın ve **kodu görüntüle**' yi seçin.

13. *Connect.cs* dosyasında, aşağıdaki using deyimlerini ekleyin:

    ```csharp
    using System.IO;
    using System.Windows.Forms;
    using System.Collections.Generic;
    using Microsoft.VisualStudio.TestTools.LoadTesting;
    using Microsoft.VisualStudio.TestTools.WebTesting;
    using WebPerfTestResultsViewerControl;
    ```

14. *Connect.cs* dosyasının en altına doğru kaydırın. <xref:System.Windows.Forms.UserControl>Web performansının birden fazla örneği **test sonuçları görüntüleyicisinin** açık olması için GUID 'lerin bir listesini eklemeniz gerekir. Daha sonra bu listeyi kullanan kod ekleyeceksiniz.

     İkinci bir dize listesi, daha sonra kodlendirilecektir OnDiscconection yönteminde kullanılır.

    ```csharp
    private DTE2 _applicationObject;
    private AddIn _addInInstance;

    private Dictionary<Guid, List<UserControl>> m_controls = new Dictionary<Guid, List<UserControl>>();        private List<string> temporaryFilePaths = new List<string>();
    ```

15. *Connect.cs* dosyası, sınıftan Connect adlı bir sınıf oluşturur <xref:Extensibility.IDTExtensibility2> ve Visual Studio eklentisini uygulamak için bazı yöntemler içerir. Metotlardan biri, eklentinin yüklenmekte olduğu bildirimini alan OnConnection yöntemidir. OnConnection yönteminde, **Web performans test sonuçları görüntüleyicisine**yönelik genişletilebilirlik paketinizi oluşturmak Için LoadTestPackageExt sınıfını kullanacaksınız. OnConnection yöntemine aşağıdaki kodu ekleyin:

    ```csharp
    public void OnConnection(object application, ext_ConnectMode connectMode, object addInInst, ref Array custom)
                {
                _applicationObject = (DTE2)application;
                _addInInstance = (AddIn)addInInst;

                // Create a load test packge extensibility class.            LoadTestPackageExt loadTestPackageExt = _applicationObject.GetObject("Microsoft.VisualStudio.TestTools.LoadTesting.LoadTestPackageExt") as LoadTestPackageExt;            // Process open windows.            foreach (WebTestResultViewer webTestResultViewer in loadTestPackageExt.WebTestResultViewerExt.ResultWindows)            {                WindowCreated(webTestResultViewer);            }            // Create event handlers.            loadTestPackageExt.WebTestResultViewerExt.WindowCreated += new EventHandler<WebTestResultViewerExt.WindowCreatedEventArgs>(WebTestResultViewerExt_WindowCreated);            loadTestPackageExt.WebTestResultViewerExt.WindowClosed += new EventHandler<WebTestResultViewerExt.WindowClosedEventArgs>(WebTesResultViewer_WindowClosed);            loadTestPackageExt.WebTestResultViewerExt.SelectionChanged += new EventHandler<WebTestResultViewerExt.SelectionChangedEventArgs>(WebTestResultViewer_SelectedChanged);
            }
    ```

16. OnConnection yöntemine ve WebTestResultViewerExt_WindowCreated yönteminin çağırdığı WindowCreated yöntemine eklediğiniz loadTestPackageExt. WebTestResultViewerExt. WindowCreated olay işleyicisi için WebTestResultViewerExt_WindowCreated yöntemi oluşturmak üzere Connect sınıfına aşağıdaki kodu ekleyin.

    ```csharp
            void WebTestResultViewerExt_WindowCreated(object sender, WebTestResultViewerExt.WindowCreatedEventArgs e)
            {
                // New control added to new result viewer window.
                WindowCreated(e.WebTestResultViewer);
            }

    private void WindowCreated(WebTestResultViewer viewer)        {            // Instantiate an instance of the resultControl referenced in the WebPerfTestResultsViewerControl project.
                resultControl resultControl = new resultControl();            // Add to the dictionary of open playback windows.            System.Diagnostics.Debug.Assert(!m_controls.ContainsKey(viewer.TestResultId));            List<UserControl> userControls = new List<UserControl>();            userControls.Add(resultControl);            // Add Guid to the m_control List to manage Result viewers and controls.            m_controls.Add(viewer.TestResultId, userControls);            // Add tabs to the playback control.            resultControl.Dock = DockStyle.Fill;            viewer.AddResultPage(new Guid(), "Sample", resultControl);        }
    ```

17. OnConnection yöntemine eklediğiniz loadTestPackageExt. WebTestResultViewerExt. SelectionChanged olay işleyicisine yönelik WebTestResultViewer_SelectedChanged yöntemi oluşturmak için Connect sınıfına aşağıdaki kodu ekleyin:

    ```csharp
    void WebTestResultViewer_SelectedChanged(object sender, WebTestResultViewerExt.SelectionChangedEventArgs e)
    {
        foreach (UserControl userControl in m_controls[e.TestResultId])            {                // Update the userControl in each result viewer.                resultControl resultControl = userControl as resultControl;                if (resultControl != null)                    // Call the resultControl's Update method (This will be added in the next procedure).                    resultControl.Update(e.WebTestRequestResult);            }
    }
    ```

18. OnConnection yöntemine eklediğiniz loadTestPackageExt. WebTestResultViewerExt. WindowClosed için olay işleyicisi için WebTesResultViewer_WindowClosed yöntemi oluşturmak üzere Connect sınıfına aşağıdaki kodu ekleyin:

    ```csharp
    void WebTesResultViewer_WindowClosed(object sender, WebTestResultViewerExt.WindowClosedEventArgs e)
    {
        if (m_controls.ContainsKey(e.WebTestResultViewer.TestResultId))
        {
            m_controls.Remove(e.WebTestResultViewer.TestResultId);
        }
    }
    ```

     Artık Visual Studio eklentisi için kod tamamlandığına göre, WebPerfTestResultsViewerControl projesindeki resultControl öğesine Update yöntemini eklemeniz gerekir.

## <a name="add-code-to-the-webperftestresultsviewercontrol"></a>WebPerfTestResultsViewerControl 'a kod ekleme

1. **Çözüm Gezgini**, WebPerfTestResultsViewerControl proje düğümüne sağ tıklayın ve **Özellikler**' i seçin.

2. **Uygulama** sekmesini seçin ve ardından **hedef çerçeve** açılır listesini seçin ve **.NET Framework 4** (veya üzeri) seçeneğini belirleyin. **Özellikler** penceresini kapatın.

   **Web performans test sonuçları görüntüleyicisini**genişletmek IÇIN gereken DLL başvurularını desteklemek için bu gereklidir.

3. **Çözüm Gezgini**, WebPerfTestResultsViewerControl projesinde, **Başvurular** düğümüne sağ tıklayın ve **Başvuru Ekle**' yi seçin.

4. **Başvuru Ekle** iletişim kutusunda, **.net** sekmesine tıklayın.

5. Aşağı kaydırın ve **Microsoft. VisualStudio. QualityTools. WebTestFramework**öğesini seçin.

6. **Tamam ' ı**seçin.

7. *UserControl1.cs* dosyasında, aşağıdaki using deyimlerini ekleyin:

    ```csharp
    using Microsoft.VisualStudio.TestTools.WebTesting;
    using Microsoft.VisualStudio.TestTools.WebTesting.Rules;
    ```

8. Çağrılan ve *Connect.cs* dosyasındaki webperftestresultsvieweraddin WebTestResultViewer_SelectedChanged yönteminden bir WebTestRequestResult geçirilmiş güncelleştirme yöntemini ekleyin. Update yöntemi, DataGridView öğesini WebTestRequestResult içinde kendisine geçirilen çeşitli özelliklerle doldurur.

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

- **Build** menüsünde **Build Solution**' ı seçin.

## <a name="register-the-webperftestresultsvieweraddin-add-in"></a>WebPerfTestResultsViewerAddin Eklentisini kaydetme

1. **Araçlar** menüsünde, **Eklenti Yöneticisi**' ni seçin.

2. **Eklenti Yöneticisi** iletişim kutusu görüntülenir.

3. **Kullanılabilir eklentiler** sütununda WebPerfTestResultsViewerAddin eklentisinin onay kutusunu seçin ve **Başlangıç** ve **komut satırı** sütunlarının altındaki onay kutularını temizleyin.

4. **Tamam ' ı**seçin.

## <a name="run-the-web-performance-test-using-the-web-test-results-viewer"></a>Web Test Sonuçları görüntüleyicisini kullanarak Web performans testini çalıştırma

1. Web performans testinizi çalıştırın; WebPerfTestResultsViewerAddin eklentisinin **Web performans test sonuçları görüntüleyicisinde**gösterildiği örnek başlıklı yeni sekmesini görürsünüz.

2. DataGridView içinde sunulan özellikleri görmek için sekmeyi seçin.

## <a name="net-security"></a>.NET güvenliği

Kötü amaçlı eklentilerin otomatik olarak etkinleşmesini önlemeye karşı güvenliği artırmak için, Visual Studio, **eklenti/makro güvenliği**adlı bir **araç seçenekleri** sayfasında ayarlar sağlar.

Ayrıca, bu seçenekler sayfası, Visual Studio 'Nun arayacağı klasörleri belirtmenize olanak tanır *. Eklenti* kayıt dosyaları. Bu, konumunu nerede sınırlayabilmenizi sağlayarak güvenliği geliştirir *. Eklenti* kayıt dosyaları okunabilir. Bu, kötü amaçlı olarak önlemeye yardımcı olur *. *İstemeden kullanılan eklenti dosyaları.

**Eklenti güvenlik ayarları**

Eklenti güvenliği için seçenekler sayfasındaki ayarlar aşağıdaki gibidir:

- **Yüklenecek eklenti bileşenlerine izin ver.** Varsayılan olarak seçilidir. Seçildiğinde, eklentilerin Visual Studio 'da yüklenmesine izin verilir. Seçilmediğinde, eklentilerin Visual Studio 'Ya yüklenmesi yasaktır.

- **Bir URL 'den yüklenecek eklenti bileşenlerine izin ver.** Varsayılan olarak seçilmemiş. Seçildiğinde, eklentiler dış Web sitelerinden yüklenebilir. Seçilmediğinde, uzak eklentilerin Visual Studio 'Ya yüklenmesi yasaktır. Bir eklenti bazı nedenlerle yüklenebilecekse, Web 'den yüklenemez. Bu ayar yalnızca eklenti DLL 'sini yüklemeyi denetler. *. Eklenti* kayıt dosyaları her zaman yerel sistemde bulunmalıdır.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.UserControl>
- <xref:Microsoft.VisualStudio.TestTools.LoadTesting>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules>
- <xref:System.Windows.Forms.UserControl>
- <xref:System.Windows.Forms.DataGrid>
- [Yük testleri için özel kod ve eklentiler oluşturma](../test/create-custom-code-and-plug-ins-for-load-tests.md)
