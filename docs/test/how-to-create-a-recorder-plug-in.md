---
title: Kaydedici eklentisi web performans testleri için oluşturma
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- Web performance tests, recorder plug-in
ms.assetid: 6fe13be1-aeb5-4927-9bff-35950e194da9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5e32faa4525edc79da3d759d67ad2b5676f38fc2
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75589166"
---
# <a name="how-to-create-a-recorder-plug-in"></a>Nasıl yapılır: kaydedici eklentisi oluşturma

<xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRecorderPlugin> Kayıtlı web performans testini değiştirmenize olanak tanır. Değişiklik seçtiğiniz sonra gerçekleşir **Durdur** içinde **Web Performans Testi Kaydedicisi** araç ancak önceki test kaydedildi ve Web Performans Testi Düzenleyicisi'nde gösterilir.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Bir kaydedici eklentisi, kendi özel korelasyon Dinamik parametrelere ilişkin gerçekleştirmenizi sağlar. Yerleşik bağıntı işlevi ile web performans testleri web tamamlandıktan sonra veya kullandığınızda kaydı dinamik parametreleri algılamak **dinamik parametreleri Web Test Parametrelerine Yükselt** üzerinde **Web Performans Testi Düzenleyicisi** araç çubuğu. Ancak dahili algılama işlevselliği tüm dinamik parametreleri her zaman bulmaz. Örneğin, genellikle 5 ila 30 dakika arasında bir değer alır oturum kimliği bulmaz. Bu nedenle, bağıntı işlemini el ile yapmanız gerekir.

<xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRecorderPlugin> Kendi özel eklentiniz için kod yazmanıza olanak sağlar. Bu eklenti bağıntı yapabilir veya kaydedilip Web Performans Test Düzenleyicisi'nde sunulmadan önce birçok yönden web performans testini değiştirme. Bu nedenle, belirli bir dinamik değişkenin kayıtlarınızın için çok büyük olduğunu belirlerseniz, işlemi otomatikleştirebilirsiniz.

Bir kaydedici eklentisi kullanılan bazı diğer yollar ekleme ayıklama ve doğrulama kuralları, bağlam parametreleri ekleme için veya dönüştürme yorumları işlemlere bir web performans testi.

Aşağıdaki yordamlar nasıl ilkel kodunun bir kaydedici eklentisi oluşturmak, eklenti dağıtma ve yürütüldüğünü açıklar. Yordamları izleyen örnek kod, Visual C# özel dinamik parametre bağıntı kaydedici eklentisi oluşturmak için nasıl kullanılacağını gösterir.

## <a name="create-a-recorder-plug-in"></a>Kaydedici eklentisi oluşturma

### <a name="to-create-a-recorder-plug-in"></a>Bir kaydedici eklentisi oluşturmak için

1. Web performans testi kaydedici eklentisi oluşturmak istediğiniz web performansı ve yük testi projesi içeren bir çözüm açın.

2. Çözüme yeni bir **sınıf kitaplığı** projesi ekleyin.

3. İçinde **Çözüm Gezgini**, yeni sınıf kitaplığı proje klasöründe, sağ **başvuruları** klasörü ve select **Başvuru Ekle**.

    > [!TIP]
    > Yeni bir sınıf kitaplığı projesi klasörüne örnektir **RecorderPlugins**.

     **Başvuru Ekle** iletişim kutusu görüntülenir.

4. Seçin **.NET** sekmesi.

5. Aşağı kaydırın ve select **Microsoft.VisualStudio.QualityTools.WebTestFramework** seçip **Tamam**.

     **Microsoft.VisualStudio.QualityTools.WebTestFramework** eklenir **başvuruları** klasöründe **Çözüm Gezgini**.

6. Kaydedici eklentiniz için kodu yazın. İlk olarak, türetilen yeni bir ortak sınıf oluşturun <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRecorderPlugin>.

7. Geçersiz kılma <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRecorderPlugin.PostWebTestRecording*> yöntemi.

    ```csharp
    public class Class1 : WebTestRecorderPlugin
        {
            public override void PostWebTestRecording(object sender, PostWebTestRecordingEventArgs e)
            {
                base.PostWebTestRecording(sender, e);
            }
        }
    ```

     Olay bağımsız değişkenleri ile çalışmak için iki nesne verecektir: kaydedilen sonuç ve kaydedilen web performansı testi. Bu, belirli değerleri ve sonra aynı istekte değişiklikler yapmak için web performans testinde arayarak sonuçlar yinelemek olanak tanır. Bir bağlam parametresini eklemek veya URL'nin parçalarını parametreleştirmek isterseniz yalnızca web performans testini değiştirebilirsiniz.

    > [!NOTE]
    > Web performans testini değiştirirseniz, ayrıca ayarlamanız gerekir <xref:Microsoft.VisualStudio.TestTools.WebTesting.PostWebTestRecordingEventArgs.RecordedWebTestModified*> özelliği true: `e.RecordedWebTestModified = true;`

8. Kaydedici eklentisi web kaydı gerçekleştikten sonra yürütmek için istediğinize göre daha fazla kod ekleyin. Örneğin, aşağıdaki örnekte gösterildiği gibi özel korelasyon işleyecek bir kod ekleyebilirsiniz. Yorumları işlemlere dönüştürme veya doğrulama kuralları ekleme web performansı test ayrıca bir kaydedici eklentisi gibi şeyler için oluşturabilirsiniz.

9. Üzerinde **derleme** menüsünde seçin **derleme \<sınıf kitaplığı proje adı >** .

Sonra, Kaydedici eklentisini Visual Studio 'ya kaydolmaları için dağıtın.

### <a name="deploy-the-recorder-plug-in"></a>Kaydedici eklentisini dağıtın

Kaydedici eklentisini derledikten sonra ortaya çıkan DLL'yi iki konumdan birinde yerleştirin:

- *% ProgramFiles (x86) %\Microsoft Visual Studio\\[sürüm]\\[sürüm] \Common7\IDE\PrivateAssemblies\WebTestPlugins*

- *%USERPROFILE%\Documents\Visual studio [sürüm] \WebTestPlugins*

> [!WARNING]
> Kaydedici eklentisini iki konumdan birine kopyaladıktan sonra kaydedici eklentisinin kaydedilmesi için için Visual Studio'yu yeniden başlatmanız gerekir.

### <a name="execute-the-recorder-plug-in"></a>Kaydedici eklentisini yürütme

1. Yeni bir web performans testi oluşturun.

     **WebTestRecordPlugins'i Etkinleştir** iletişim kutusu görüntüler.

2. Kaydedici eklentisi onay kutusunu seçip **Tamam**.

     Web performans testi, kaydı tamamladıktan sonra yeni Kaydedici eklenti yürütülecektir.

    > [!WARNING]
    > Bir web performans testi ya da eklentisini kullanan yük testi çalıştırdığınızda aşağıdakine benzer bir hata alabilirsiniz:
    >
    > **İstek başarısız: \<eklenti > olayında özel durum: dosya veya derleme '\<"eklenti adı". dll dosyası >, sürüm =\<n. n. n. n >, kültür = neutral, PublicKeyToken = null ' veya bağımlılıklarından biri yüklenemedi. Sistem belirtilen dosyayı bulamıyor.**
    >
    > Eklentilerinizi birine kod değişikliği yapmanız ve yeni bir DLL sürümü oluşturursanız Bunun nedeni **(sürüm = 0.0.0.0)** , ancak eklenti hala özgün eklenti sürümüne başvuruyor. Bu sorunu gidermek için şu adımları izleyin:
    >
    > 1. Web performansı ve yük testi projesi içinde başvurularda bir uyarı görürsünüz. Kaldırın ve Başvuruyu eklenti DLL'nizden yeniden ekleyin.
    > 2. Test veya uygun konumdan eklentiyi kaldırın ve yeniden ekleyin.

## <a name="example"></a>Örnek

Bu örnek, özelleştirilmiş web Performans Testi Kaydedicisi özel dinamik parametre bağıntısı yapmak için eklenti oluşturma işlemini gösterir.

> [!NOTE]
> Örnek kod tam listesi, bu konunun altında bulunur.

### <a name="iterate-through-the-result-to-find-first-page-with-reportsession"></a>ReportSession ilk sayfayı bulmak için sonuç üzerinden yineleme yapma

Kod örneğinin bu parçası, her bir kaydedilmiş nesne boyunca yinelenir ve rapor oturumu için yanıt gövdesini arar.

```csharp
foreach (WebTestResultUnit unit in e.RecordedWebTestResult.Children)
 {
     WebTestResultPage page = unit as WebTestResultPage;
     if (page != null)
     {
         if (!foundId)
         {
             int indexOfReportSession = page.RequestResult.Response.BodyString.IndexOf("ReportSession");
             if (indexOfReportSession > -1)
             {
```

### <a name="add-an-extraction-rule"></a>Bir ayıklama kuralı ekleme

Bir yanıt bulunduktan sonra bir çıkarma kuralı eklemeniz gerekir. Kod örneğinin bu parçası kullanarak ayıklama kuralını oluşturur <xref:Microsoft.VisualStudio.TestTools.WebTesting.ExtractionRuleReference> sınıfı ve ardından ayıklama kuralını eklemek için web performans testindeki doğru isteği bulur. Her sonuç nesnesi yeni bir sahip çağrılır, hangi kod içinde web performans testinden doğru istekleri almak için kullanılan, DeclarativeWebTestItemId özelliği eklendi.

```csharp
ExtractionRuleReference ruleReference = new ExtractionRuleReference();
     ruleReference.Type = typeof(ExtractText);
     ruleReference.ContextParameterName = "SessionId";
     ruleReference.Properties.Add(new PluginOrRuleProperty("EndsWith", "&ControlID="));
     ruleReference.Properties.Add(new PluginOrRuleProperty("HtmlDecode", "True"));
     ruleReference.Properties.Add(new PluginOrRuleProperty("IgnoreCase", "True"));
     ruleReference.Properties.Add(new PluginOrRuleProperty("Index", "0"));
     ruleReference.Properties.Add(new PluginOrRuleProperty("Required", "True"));
     ruleReference.Properties.Add(new PluginOrRuleProperty("StartsWith", "ReportSession="));
     ruleReference.Properties.Add(new PluginOrRuleProperty("UseRegularExpression", "False"));

     WebTestRequest requestInWebTest = e.RecordedWebTest.GetItem(page.DeclarativeWebTestItemId) as WebTestRequest;
     if (requestInWebTest != null)
     {
         requestInWebTest.ExtractionRuleReferences.Add(ruleReference);
         e.RecordedWebTestModified = true;
     }
```

### <a name="replace-query-string-parameters"></a>Sorgu dizesi parametrelerini değiştir

Artık kod tüm sorgu adı ReportSession ve değer {{SessionID}}, kod örneğinin bu parçasında gösterilen şekilde değiştirin. dize parametreleri bulur:

```csharp
WebTestRequest requestInWebTest = e.RecordedWebTest.GetItem(page.DeclarativeWebTestItemId) as WebTestRequest;
if (requestInWebTest != null)
{
    foreach (QueryStringParameter param in requestInWebTest.QueryStringParameters)
    {
         if (param.Name.Equals("ReportSession"))
         {
             param.Value = "{{SessionId}}";
         }
     }
 }
```

```csharp
using System.ComponentModel;
using Microsoft.VisualStudio.TestTools.WebTesting;
using Microsoft.VisualStudio.TestTools.WebTesting.Rules;

namespace RecorderPlugin
{
    [DisplayName("Correlate ReportSession")]
    [Description("Adds extraction rule for Report Session and binds this to querystring parameters that use ReportSession")]
    public class CorrelateSessionId : WebTestRecorderPlugin
    {
        public override void PostWebTestRecording(object sender, PostWebTestRecordingEventArgs e)
        {
            //first find the session id
            bool foundId = false;
            foreach (WebTestResultUnit unit in e.RecordedWebTestResult.Children)
            {
                WebTestResultPage page = unit as WebTestResultPage;
                if (page != null)
                {
                    if (!foundId)
                    {
                        int indexOfReportSession = page.RequestResult.Response.BodyString.IndexOf("ReportSession");
                        if (indexOfReportSession > -1)
                        {
                            //add an extraction rule to this request
                            // Get the corresponding request in the Declarative Web performance test
                            ExtractionRuleReference ruleReference = new ExtractionRuleReference();

                            ruleReference.Type = typeof(ExtractText);
                            ruleReference.ContextParameterName = "SessionId";
                            ruleReference.Properties.Add(new PluginOrRuleProperty("EndsWith", "&ControlID="));
                            ruleReference.Properties.Add(new PluginOrRuleProperty("HtmlDecode", "True"));
                            ruleReference.Properties.Add(new PluginOrRuleProperty("IgnoreCase", "True"));
                            ruleReference.Properties.Add(new PluginOrRuleProperty("Index", "0"));
                            ruleReference.Properties.Add(new PluginOrRuleProperty("Required", "True"));
                            ruleReference.Properties.Add(new PluginOrRuleProperty("StartsWith", "ReportSession="));
                            ruleReference.Properties.Add(new PluginOrRuleProperty("UseRegularExpression", "False"));

                            WebTestRequest requestInWebTest = e.RecordedWebTest.GetItem(page.DeclarativeWebTestItemId) as WebTestRequest;
                            if (requestInWebTest != null)
                            {
                                requestInWebTest.ExtractionRuleReferences.Add(ruleReference);
                                e.RecordedWebTestModified = true;
                            }
                            foundId = true;

                        }
                    }
                    else
                    {
                        //now update query string parameters
                        WebTestRequest requestInWebTest = e.RecordedWebTest.GetItem(page.DeclarativeWebTestItemId) as WebTestRequest;
                        if (requestInWebTest != null)
                        {
                            foreach (QueryStringParameter param in requestInWebTest.QueryStringParameters)
                            {
                                if (param.Name.Equals("ReportSession"))
                                {
                                    param.Value = "{{SessionId}}";
                                }
                            }
                        }
                    }
                }
            }
        }
    }
}
```

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequestPlugin>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRecorderPlugin.PostWebTestRecording*>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.ExtractionRuleReference>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRecorderPlugin.PostWebTestRecording*>
- [Özel kod ve yük testleri için eklentiler oluşturma](../test/create-custom-code-and-plug-ins-for-load-tests.md)
- [Oluşturma ve bir kodlanmış web performans testini çalıştırma](../test/generate-and-run-a-coded-web-performance-test.md)
