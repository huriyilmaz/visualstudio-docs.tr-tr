---
title: Web performans Test Sonuçları Görüntüleyicisi için Add-In oluşturma
description: Web performans Test Sonuçları görüntüleyicisinin kullanıcı arabirimini genişletmek ve kullanıcı arabirimini genişletmek için gerekli olan sınıfları uygulamak için bir Visual Studio eklentisi oluşturmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 10/20/2016
ms.topic: how-to
helpviewer_keywords:
- Web performance tests, Visual Studio Add-in
- Visual Studio Add-in, Web performance tests
ms.assetid: 1118c604-4b1b-4b21-a04e-45995b676fa8
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.openlocfilehash: 10bab04db18962c592cac96eb707b0303874d5b3
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122135643"
---
# <a name="how-to-create-an-add-in-for-the-web-performance-test-results-viewer"></a>Nasıl yapılır: Web performans Test Sonuçları Görüntüleyicisi için eklenti oluşturma

Aşağıdaki ad alanlarını kullanarak **Web performans test sonuçları görüntüleyicisine** yönelik kullanıcı arabirimini genişletebilirsiniz:

- <xref:Microsoft.VisualStudio.TestTools.LoadTesting>

- <xref:Microsoft.VisualStudio.TestTools.WebTesting>

ayrıca, *% ProgramFiles (x86)% \ Microsoft Visual Studio \\ \<version> \ Enterprise \Common7\IDE\PrivateAssemblies* klasöründe bulunan loadtestpackage DLL dosyasına bir başvuru eklemeniz gerekir.

**Web performansı Test Sonuçları görüntüleyicisinin** kullanıcı arabirimini genişletmek için, bir Visual Studio eklentisi ve bir kullanıcı denetimi oluşturmanız gerekir. Aşağıdaki yordamlarda, eklentinin nasıl oluşturulacağı, Kullanıcı denetiminin ve **Web performans test sonuçları görüntüleyicisinin** Kullanıcı arabirimini genişletmek için gerekli sınıfların nasıl uygulanacağı açıklanmaktadır.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="create-or-open-a-solution-that-contains-an-aspnet-web-application-and-a-web-performance-and-load-test-project"></a>ASP.NET web uygulaması ve web performansı ve yük testi projesi içeren bir çözüm oluşturun veya açın

### <a name="to-prepare-for-extending-the-web-performance-test-results-viewer"></a>Web performans Test Sonuçları görüntüleyicisini genişletmeye hazırlanmak için

ASP.NET web uygulaması için bir veya daha fazla web performans testiyle bir ASP.NET web uygulaması ve bir web performansı ve yük testi projesi içeren deneyebilmeniz için bir üretim dışı çözümü oluşturun veya açın.

> [!NOTE]
> [nasıl yapılır: web hizmeti testi oluşturma](../test/how-to-create-a-web-service-test.md) ve [kodlanmış web performans testi oluşturma ve çalıştırma](../test/generate-and-run-a-coded-web-performance-test.md)konusundaki yordamları izleyerek web performans testlerini içeren bir ASP.NET web uygulaması ve web performansı ve yük testi projesi oluşturabilirsiniz.

## <a name="create-a-visual-studio-add-in"></a>Visual Studio eklentisi oluşturma

eklenti, Visual Studio tümleşik geliştirme ortamında (ıde) çalışan derlenmiş bir DLL 'dir. Derleme fikri mülkiyet bilgilerinizi korumanıza yardımcı olur ve performansı geliştirir. Eklentileri el ile oluşturabilseniz de, **Eklenti Sihirbazı**'nı kullanmayı daha kolay bulabilirsiniz. Bu sihirbaz, oluşturduktan hemen sonra çalıştırabileceğiniz bir işlevsel ancak temel bir eklenti oluşturur. **Eklenti Sihirbazı** temel programı oluşturduktan sonra, ona kod ekleyebilir ve onu özelleştirebilirsiniz.

Eklenti **Sihirbazı** , eklenti için bir görünen ad ve açıklama sağlamanıza olanak tanır. Her ikisi de **Eklenti Yöneticisi**'nde görünür. İsteğe bağlı olarak, sihirbazın, eklentiyi açmak için **Araçlar** menüsüne bir komut ekleyen kodu oluşturmasını sağlayabilirsiniz. Ayrıca, eklenti **için özel bir iletişim kutusu görüntülemeyi** de seçebilirsiniz. Sihirbaz tamamlandığında, eklentiyi uygulayan tek bir sınıfı olan yeni bir projeniz olur. bu sınıf Bağlan olarak adlandırılır.

Bu makalenin sonundaki **eklenti yöneticisini** kullanacaksınız.

### <a name="to-create-an-add-in-by-using-the-add-in-wizard"></a>Add-In Sihirbazı 'Nı kullanarak eklenti oluşturmak için

1. **Çözüm Gezgini**, çözüme sağ tıklayın, **Ekle**' yi seçin ve ardından **yeni Project**' yı seçin.

2. yeni bir **Visual Studio eklentisi** projesi oluşturun.

    Visual Studio **eklentisi sihirbazı** başlatılır.

3. **İleri**’yi seçin.

4. **Bir programlama dili seçin** sayfasında, eklentiyi yazmak için kullanmak istediğiniz programlama dilini seçin.

   > [!NOTE]
   > Bu konu, örnek kod Için Visual C# kullanır.

5. **bir uygulama ana bilgisayarı seçin** sayfasında **Visual Studio** seçin ve **makroları Visual Studio** temizleyin.

6. **İleri**’yi seçin.

7. **Bir ad ve açıklama girin** sayfasında, eklenti için bir ad ve açıklama yazın.

     Eklenti oluşturulduktan sonra, adı ve açıklaması **Eklenti Yöneticisi**' nde **kullanılabilir eklentiler** listesinde görüntülenir. Kullanıcılarınızın eklentisinin ne yaptığını, nasıl çalıştığını vb. öğrenmeleri için, eklenti açıklamasına yeterince ayrıntı ekleyin.

8. **İleri**’yi seçin.

9. **Add-In seçenekleri seçin** sayfasında, **ana bilgisayar uygulaması başladığında Eklentimin yüklenmesini istiyorum**' u seçin.

10. Kalan onay kutularını temizleyin.

11. **' Yardım hakkında ' bilgilerini seçme** sayfasında, eklenti hakkındaki bilgilerin **hakkında** iletişim kutusunda gösterilmesini isteyip istemediğinizi belirtebilirsiniz. Bilgilerin görüntülenmesini isterseniz, **Evet ' i seçin, Eklentimin ' hakkında ' kutusu bilgilerini sunmasını** istiyorum onay kutusunu işaretleyin.

     Visual Studio **hakkında** iletişim kutusuna eklenebilecek bilgiler, sürüm numarası, destek ayrıntıları, lisanslama verileri vb. içerir.

12. **İleri**’yi seçin.

13. Seçtiğiniz seçenekler, gözden geçirmeniz için **Özet** sayfasında görüntülenir. Memnun kaldıysanız, eklentiyi oluşturmak için **son** ' u seçin. Bir değişiklik yapmak istiyorsanız **geri** düğmesini seçin.

     yeni çözüm ve proje oluşturulur ve yeni eklenti için *Bağlan. cs* dosyası **kod düzenleyicisinde** görüntülenir.

     aşağıdaki yordamdan sonra *Bağlan. cs* dosyasına kod ekleyeceksiniz. bu işlem, bu webperftestresultsvieweraddin projesi tarafından başvurulacak bir kullanıcı denetimi oluşturur.

    bir eklenti oluşturulduktan sonra, **eklentiyi eklenti yöneticisi**'nde etkinleştirilmeden önce Visual Studio kaydetmeniz gerekir. Bunu, *. AddIn* dosya adı uzantısına sahıp bir XML dosyası kullanarak yapabilirsiniz.

    *. addin* dosyası, Visual Studio eklentisinin eklenti **yöneticisi**'nde gösterilmesi için gereken bilgileri açıklar. Visual Studio başladığında, kullanılabilir *. addin* dosyaları için *. addin* dosya konumuna bakar. Herhangi bir bulursa, XML dosyasını okur ve **Eklenti Yöneticisi** 'nin tıklandığında eklentiyi başlatması için ihtiyaç duyduğu bilgileri verir.

    *. Addin* dosyası, eklenti **Sihirbazı 'nı** kullanarak bir eklenti oluşturduğunuzda otomatik olarak oluşturulur.

### <a name="add-in-file-locations"></a>Eklenti dosyası konumları

*. Addin* dosyalarının iki kopyası, **Eklenti Sihirbazı** tarafından aşağıdaki gibi otomatik olarak oluşturulur:

|**. Eklenti dosyası konumu**|**Açıklama**|
|-|----------------------------|-|
|Kök proje klasörü|Eklenti projesinin dağıtımı için kullanılır. Proje, düzenlenecek ve XCopy stili dağıtım için yerel yola sahip olmak üzere kolayca bulunur.|
|Eklenti klasörü|Eklentiyi hata ayıklama ortamında çalıştırmak için kullanılır. Her zaman geçerli derleme yapılandırmasının çıkış yolunu işaret etmelidir.|

## <a name="create-a-windows-form-control-library-project"></a>Windows Form denetim kitaplığı projesi oluşturma

önceki yordamda oluşturulan Visual Studio eklentisi bir sınıfın örneğini oluşturmak için bir Windows Forms denetim kitaplığı projesine başvurur <xref:System.Windows.Forms.UserControl> .

### <a name="to-create-a-control-to-be-used-in-the-web-test-results-viewer"></a>Web Test Sonuçları görüntüleyicisinde kullanılacak bir denetim oluşturmak için

1. **Çözüm Gezgini**, çözüme sağ tıklayın, **Ekle**' yi seçin ve ardından **yeni Project**' yı seçin.

2. yeni bir **Windows Forms denetim kitaplığı** projesi oluşturun.

3. **Araç kutusundan**, <xref:System.Windows.Forms.DataGridView> UserControl1 yüzeyine sürükleyin.

4. Sağ üst köşesindeki eylem etiketi glifi ' ne ( ![ akıllı etiket karakter ](../test/media/vs_winformsmttagglyph.gif) ) tıklayın <xref:System.Windows.Forms.DataGridView> ve şu adımları izleyin:

    1. **Üst kapsayıcıda yerleştir '** i seçin.

    2. **Ekleme**, **düzenleme etkinleştirme**, **silme** ve **sütun yeniden sıralamayı** etkinleştirme için onay kutularını temizleyin.

    3. **Sütun Ekle**' yi seçin.

         **Sütun Ekle** iletişim kutusu görüntülenir.

    4. **Tür** açılan listesinde **DataGridViewTextBoxColumn**' ı seçin.

    5. **Üstbilgi metninde**"Sütun1" metnini temizleyin.

    6. **Ekle**' yi seçin.

    7. **Kapat**' ı seçin.

5. **Özellikler** penceresinde, ' ın **(Name)** özelliğini <xref:System.Windows.Forms.DataGridView> **resultControlDataGridView** olarak değiştirin.

6. Tasarım yüzeyine sağ tıklayın ve **kodu görüntüle**' yi seçin.

     *UserControl1. cs* dosyası **kod düzenleyicisinde** görüntülenir.

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

     bir sonraki yordamda, webperftestresultsvieweraddin projesinin *Bağlan. cs* dosyasına kod ekleyeceksiniz ve bu, resultcontrol sınıfına başvuracaktır.

     daha sonra *Bağlan. cs* dosyasına bazı ek kodlar ekleyirsiniz.

## <a name="add-code-to-the-webperftestresultsvieweraddin"></a>WebPerfTestResultsViewerAddin 'a kod ekleme

1. **Çözüm Gezgini**, WebPerfTestResultsViewerAddin projesindeki **Başvurular** düğümüne sağ tıklayın ve **Başvuru Ekle**' yi seçin.

2. **Başvuru Ekle** iletişim kutusunda **.net** sekmesini seçin.

3. Aşağı kaydırın ve **Microsoft. VisualStudio. QualityTools. WebTestFramework** ve **System. Windows öğesini seçin. Forms**.

4. **Tamam ' ı** seçin.

5. **Başvurular** düğümüne tekrar sağ tıklayın ve **Başvuru Ekle**' yi seçin.

6. **Başvuru Ekle** iletişim kutusunda, **Gözden** geçirme sekmesini seçin.

7. **ara '** yı seçin ve *% ProgramFiles (x86)% \ Microsoft Visual Studio \ 2017 \ Enterprise \Common7\IDE\PrivateAssemblies* adresine gidin ve *Microsoft.VisualStudio.QualityTools.LoadTestPackage.dll* dosyasını seçin.

8. **Tamam ' ı** seçin.

9. WebPerfTestResultsViewerAddin proje düğümüne sağ tıklayın ve **Başvuru Ekle**' yi seçin.

10. **Başvuru Ekle** iletişim kutusunda, **Projeler** sekmesini seçin.

11. **Project adı** altında **webperftestresultsviewercontrol** projesini seçin ve **tamam**' ı seçin.

12. *Bağlan. cs* dosyası hala açık değilse, **Çözüm Gezgini**' de webperftestresultsvieweraddin projesindeki **Bağlan. cs** dosyasına sağ tıklayın ve **kodu görüntüle**' yi seçin.

13. *Bağlan. cs* dosyasında aşağıdaki Using deyimlerini ekleyin:

    ```csharp
    using System.IO;
    using System.Windows.Forms;
    using System.Collections.Generic;
    using Microsoft.VisualStudio.TestTools.LoadTesting;
    using Microsoft.VisualStudio.TestTools.WebTesting;
    using WebPerfTestResultsViewerControl;
    ```

14. *Bağlan. cs* dosyasının en altına doğru kaydırın. Web Performansı Test Sonuçları Görüntüleyicisi'nin açık durumda olduğu durumlarda <xref:System.Windows.Forms.UserControl> **guid'ler listesi** eklemeniz gerekir. Daha sonra bu listeyi kullanan kodu eksersiniz.

     OnDiscconection yönteminde ikinci bir dize listesi kullanılır ve bu yöntemi daha sonra kodlayabilirsiniz.

    ```csharp
    private DTE2 _applicationObject;
    private AddIn _addInInstance;

    private Dictionary<Guid, List<UserControl>> m_controls = new Dictionary<Guid, List<UserControl>>();        private List<string> temporaryFilePaths = new List<string>();
    ```

15. *Bağlan.cs* dosyası sınıfından Bağlan adlı bir sınıfın örneğini sağlar ve aynı zamanda Visual Studio <xref:Extensibility.IDTExtensibility2> uygulamak için bazı yöntemler içerir. Yöntemlerden biri, eklentinin yükleniyor olduğunu bildirim alan OnConnection yöntemidir. OnConnection yönteminde, Web Performance Test Sonuçları Viewer için genişletilebilirlik paketinizi oluşturmak üzere LoadTestPackageExt **sınıfını kullanabilirsiniz.** Aşağıdaki kodu OnConnection yöntemine ekleyin:

    ```csharp
    public void OnConnection(object application, ext_ConnectMode connectMode, object addInInst, ref Array custom)
                {
                _applicationObject = (DTE2)application;
                _addInInstance = (AddIn)addInInst;

                // Create a load test packge extensibility class.            LoadTestPackageExt loadTestPackageExt = _applicationObject.GetObject("Microsoft.VisualStudio.TestTools.LoadTesting.LoadTestPackageExt") as LoadTestPackageExt;            // Process open windows.            foreach (WebTestResultViewer webTestResultViewer in loadTestPackageExt.WebTestResultViewerExt.ResultWindows)            {                WindowCreated(webTestResultViewer);            }            // Create event handlers.            loadTestPackageExt.WebTestResultViewerExt.WindowCreated += new EventHandler<WebTestResultViewerExt.WindowCreatedEventArgs>(WebTestResultViewerExt_WindowCreated);            loadTestPackageExt.WebTestResultViewerExt.WindowClosed += new EventHandler<WebTestResultViewerExt.WindowClosedEventArgs>(WebTesResultViewer_WindowClosed);            loadTestPackageExt.WebTestResultViewerExt.SelectionChanged += new EventHandler<WebTestResultViewerExt.SelectionChangedEventArgs>(WebTestResultViewer_SelectedChanged);
            }
    ```

16. LoadTestPackageExt.WebTestResultViewerExt.WindowCreated olay işleyicisi için onConnection yöntemine ve WebTestResultViewerExt_WindowCreated yönteminin çağırmış olduğu WindowCreated yöntemi için WebTestResultViewerExt_WindowCreated yöntemini oluşturmak için connect sınıfına aşağıdaki kodu ekleyin.

    ```csharp
            void WebTestResultViewerExt_WindowCreated(object sender, WebTestResultViewerExt.WindowCreatedEventArgs e)
            {
                // New control added to new result viewer window.
                WindowCreated(e.WebTestResultViewer);
            }

    private void WindowCreated(WebTestResultViewer viewer)        {            // Instantiate an instance of the resultControl referenced in the WebPerfTestResultsViewerControl project.
                resultControl resultControl = new resultControl();            // Add to the dictionary of open playback windows.            System.Diagnostics.Debug.Assert(!m_controls.ContainsKey(viewer.TestResultId));            List<UserControl> userControls = new List<UserControl>();            userControls.Add(resultControl);            // Add Guid to the m_control List to manage Result viewers and controls.            m_controls.Add(viewer.TestResultId, userControls);            // Add tabs to the playback control.            resultControl.Dock = DockStyle.Fill;            viewer.AddResultPage(new Guid(), "Sample", resultControl);        }
    ```

17. OnConnection yöntemine eklenen loadTestPackageExt.WebTestResultViewerExt.SelectionChanged olay işleyicisi için WebTestResultViewer_SelectedChanged yöntemini oluşturmak için connect sınıfına aşağıdaki kodu ekleyin:

    ```csharp
    void WebTestResultViewer_SelectedChanged(object sender, WebTestResultViewerExt.SelectionChangedEventArgs e)
    {
        foreach (UserControl userControl in m_controls[e.TestResultId])            {                // Update the userControl in each result viewer.                resultControl resultControl = userControl as resultControl;                if (resultControl != null)                    // Call the resultControl's Update method (This will be added in the next procedure).                    resultControl.Update(e.WebTestRequestResult);            }
    }
    ```

18. OnConnection yöntemine ekleyişle birlikte loadTestPackageExt.WebTestResultViewerExt.WindowClosed için olay işleyicisi için WebTesResultViewer_WindowClosed yöntemini oluşturmak için connect sınıfına aşağıdaki kodu ekleyin:

    ```csharp
    void WebTesResultViewer_WindowClosed(object sender, WebTestResultViewerExt.WindowClosedEventArgs e)
    {
        if (m_controls.ContainsKey(e.WebTestResultViewer.TestResultId))
        {
            m_controls.Remove(e.WebTestResultViewer.TestResultId);
        }
    }
    ```

     Visual Studio için kod tamamlandı. Artık WebPerfTestResultsViewerControl projesinde resultControl'a Update yöntemini eklemeniz gerekir.

## <a name="add-code-to-the-webperftestresultsviewercontrol"></a>WebPerfTestResultsViewerControl'a Kod Ekleme

1. Bu **Çözüm Gezgini** WebPerfTestResultsViewerControl proje düğümüne sağ tıklayın ve Özellikler'i **seçin.**

2. Uygulama sekmesini **ve** ardından Hedef çerçeve açılan **listesini** seçin ve **sonra da 4 (veya .NET Framework)** seçeneğini kullanın. Özellikler **penceresini** kapatın.

   Bu, Web Performansı Ve Görüntüleyicisi'ni genişletmek için gereken DLL başvurularını **desteklemek Test Sonuçları gereklidir.**

3. Bu **Çözüm Gezgini** WebPerfTestResultsViewerControl projesinde Başvurular düğümüne  sağ tıklayın ve Başvuru Ekle'yi **seçin.**

4. Başvuru **Ekle iletişim** kutusunda **.NET sekmesine** tıklayın.

5. Ekranı aşağı kaydırın ve **Microsoft.VisualStudio.QualityTools.WebTestFramework öğesini seçin.**

6. **Tamam'ı seçin.**

7. *UserControl1.cs dosyasına* aşağıdaki Using deyimlerini ekleyin:

    ```csharp
    using Microsoft.VisualStudio.TestTools.WebTesting;
    using Microsoft.VisualStudio.TestTools.WebTesting.Rules;
    ```

8. çağrılır ve *Bağlan.cs* dosyasındaki WebPerfTestResultsViewerAddin WebTestResultViewer_SelectedChanged yönteminden bir WebTestRequestResult geçirilen Update yöntemini ekleyin. Update yöntemi, DataGridView'u WebTestRequestResult içinde geçirilen çeşitli özelliklerle doldurmak için kullanılır.

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

- Derleme menüsünde **Çözümü** **Derleme'yi seçin.**

## <a name="register-the-webperftestresultsvieweraddin-add-in"></a>WebPerfTestResultsViewerAddin eklentisini kaydetme

1. Araçlar **menüsünde** Eklenti **Yöneticisi'ni seçin.**

2. **Eklenti Yöneticisi iletişim** kutusu görüntülenir.

3. Kullanılabilir Eklentiler sütununda WebPerfTestResultsViewerAddin eklentisini onay  kutusunu seçin ve **Başlangıç** ve Komut Satırı sütunlarının altındaki onay **kutularını** temizleyin.

4. **Tamam'ı seçin.**

## <a name="run-the-web-performance-test-using-the-web-test-results-viewer"></a>Web Sunucusu Görüntüleyicisi'ni kullanarak web Test Sonuçları testi çalıştırma

1. Web performans testini çalıştırın; WebPerfTestResultsViewerAddin eklentinin Web Performansı ve Görüntüleyicisi'nde Görüntülenen Örnek başlıklı yeni **sekmesini Test Sonuçları görürsünüz.**

2. DataGridView'da sunulan özellikleri görmek için sekmesini seçin.

## <a name="net-security"></a>.NET güvenliği

Kötü amaçlı eklentilerin otomatik olarak etkinleştirmesini engelerek güvenliği artırmak için  Visual Studio/Makrolar Güvenliği adlı bir Araç Seçenekleri sayfasında **ayarlar sağlar.**

Ayrıca, bu seçenekler sayfası, uygulamanın içinde arama yaptığı Visual Studio belirtmenize olanak *sağlar. AddIn* kayıt dosyaları. Bu, bulunduğu konumları sınırlamanıza olanak sağlayarak güvenliği *iyiler. AddIn* kayıt dosyaları okunabilir. Bu, kötü amaçlı yazılım önlemeye yardımcı *olur. AddIn* dosyaları, insoral olarak kullanılıyor.

**Eklenti Güvenlik Ayarlar**

Eklenti güvenliği için seçenekler sayfasındaki ayarlar aşağıdaki gibidir:

- **Eklenti bileşenlerinin yüklemesine izin ver.** Varsayılan olarak seçilidir. Bu seçildiğinde, eklentilerin Visual Studio. Seçili değilken, eklentilerin Visual Studio.

- **Eklenti bileşenlerinin BIR URL'den yüklemesine izin ver.** Varsayılan olarak seçili değildir. Seçildiğinde, eklentiler dış web sitelerinden yüklenebilir. Seçili değilken, uzak eklentilerin Visual Studio. Bir eklenti herhangi bir nedenle yüklenemiyorsa Web'den yüklenemiyor. Bu ayar yalnızca eklenti DLL'sini yüklemesini kontrol eder. . *Eklenti* kayıt dosyaları her zaman yerel sistemde yer alıyor olması gerekir.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.UserControl>
- <xref:Microsoft.VisualStudio.TestTools.LoadTesting>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.Rules>
- <xref:System.Windows.Forms.UserControl>
- <xref:System.Windows.Forms.DataGrid>
- [Yük testleri için özel kod ve eklentiler oluşturma](../test/create-custom-code-and-plug-ins-for-load-tests.md)
