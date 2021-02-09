---
title: Web performans testleri için bir kaydedici Plug-In oluşturma
description: Web performans testi Kaydedicisi araç çubuğunda Durdur seçeneğini belirledikten sonra, türünde webtestrecorderpluginexception 'in kayıtlı bir Web performans testini değiştirmenize nasıl izin sağladığını öğrenin.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- Web performance tests, recorder plug-in
ms.assetid: 6fe13be1-aeb5-4927-9bff-35950e194da9
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: da17af68f7aebe52ad208bf2b83d3221a0640be6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99877986"
---
# <a name="how-to-create-a-recorder-plug-in"></a>Nasıl yapılır: Kaydedici eklentisi oluşturma

, <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRecorderPlugin> Kayıtlı bir Web performans testini değiştirmenize izin verir. Değişiklik, **Web performans testi kaydedici** araç çubuğunda **Durdur** ' ı seçtikten sonra, test kaydedilmeden ve Web Performans Testi Düzenleyicisi sunulmadan önce oluşur.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Bir kaydedici eklentisi, dinamik parametrelerde kendi özel bağıntılarınızı gerçekleştirmenize olanak sağlar. Yerleşik bağıntı işlevselliğiyle, Web performans testleri tamamlandığında Web kaydındaki dinamik parametreleri veya **Web Performans Testi Düzenleyicisi** araç çubuğundaki **Web testi parametrelerini Yükselt** ' i kullanarak algılar. Ancak, yerleşik algılama işlevi tüm dinamik parametreleri her zaman bulamaz. Örneğin, genellikle değerini 5 ile 30 dakika arasında değiştiren bir oturum KIMLIĞI bulmaz. Bu nedenle, bağıntı işlemini el ile gerçekleştirmeniz gerekir.

<xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRecorderPlugin>Kendi özel eklentiniz için kod yazmanızı sağlar. Bu eklenti, bağıntı gerçekleştirebilir veya Web performans testini, kaydedilmeden ve Web Performans Testi Düzenleyicisi sunulmadan önce birçok şekilde değiştirebilir. Bu nedenle, belirli bir dinamik değişkenin kayıtlarınızın çok fazla olması gerektiğini belirlerseniz, işlemi otomatikleştirebilirsiniz.

Bir kaydedici eklentisinin kullanılabileceği bazı diğer yollar, ayıklama ve doğrulama kuralları eklemek, bağlam parametreleri eklemek veya açıklamaları bir Web performans testinde işlemlere dönüştürmek içindir.

Aşağıdaki yordamlarda, kaydedici eklentisi için ilkel kodu oluşturma, eklentiyi dağıtma ve eklentiyi yürütme açıklanır. Yordamlardan sonraki örnek kod, özel bir dinamik parametre bağıntı Kaydedici eklentisi oluşturmak Için Visual C# ' nin nasıl kullanılacağını göstermektedir.

## <a name="create-a-recorder-plug-in"></a>Kaydedici eklentisi oluşturma

### <a name="to-create-a-recorder-plug-in"></a>Kaydedici eklentisi oluşturmak için

1. Web performans ve yük testi projesini içeren bir çözümü, kaydedici eklentisi oluşturmak istediğiniz Web performans testini kullanarak açın.

2. Çözüme yeni bir **sınıf kitaplığı** projesi ekleyin.

3. **Çözüm Gezgini**, yeni sınıf kitaplığı proje klasöründe, **Başvurular** klasörüne sağ tıklayın ve **Başvuru Ekle**' yi seçin.

    > [!TIP]
    > Yeni bir sınıf kitaplığı proje klasörü örneği, **Recordereklentiler**.

     **Başvuru Ekle** iletişim kutusu görüntülenir.

4. **.Net** sekmesini seçin.

5. Aşağı kaydırın ve **Microsoft. VisualStudio. QualityTools. WebTestFramework** öğesini seçin ve ardından **Tamam**' ı seçin.

     **Microsoft. VisualStudio. QualityTools. WebTestFramework** , **Çözüm Gezgini** **Başvurular** klasörüne eklenir.

6. Kaydedici eklentiniz için kodu yazın. İlk olarak, öğesinden türetilen yeni bir ortak sınıf oluşturun <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRecorderPlugin> .

7. Yöntemini geçersiz kılın <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRecorderPlugin.PostWebTestRecording*> .

    ```csharp
    public class Class1 : WebTestRecorderPlugin
        {
            public override void PostWebTestRecording(object sender, PostWebTestRecordingEventArgs e)
            {
                base.PostWebTestRecording(sender, e);
            }
        }
    ```

     Olay bağımsız değişkenleri, birlikte çalışmak için iki nesne verecektir: kayıtlı sonuç ve kayıtlı Web performans testi. Bu, belirli değerleri bulmak için sonuç boyunca yineleme yapmanızı sağlar ve sonra değişiklik yapmak için Web performans testinde aynı isteğe atlayın. Web performans testini de yalnızca bir bağlam parametresi eklemek veya URL 'nin parçalarını parametreleştirmek istediğinizde değiştirebilirsiniz.

    > [!NOTE]
    > Web performans testini değiştirirseniz, <xref:Microsoft.VisualStudio.TestTools.WebTesting.PostWebTestRecordingEventArgs.RecordedWebTestModified*> özelliği de true olarak ayarlamanız gerekecektir: `e.RecordedWebTestModified = true;`

8. Web kaydı oluştuktan sonra kaydedici eklentisinin yürütmesini istediğiniz koda göre daha fazla kod ekleyin. Örneğin, aşağıdaki örnekte gösterildiği gibi özel bağıntıyı işleyecek bir kod ekleyebilirsiniz. Ayrıca, yorumları işlemlere dönüştürme veya Web başarım testine doğrulama kuralları ekleme gibi şeyler için bir kaydedici eklentisi de oluşturabilirsiniz.

9. **Yapı** menüsünde, **Oluştur \<class library project name>**' u seçin.

Sonra, Kaydedici eklentisini Visual Studio 'ya kaydolmaları için dağıtın.

### <a name="deploy-the-recorder-plug-in"></a>Kaydedici eklentisini dağıtma

Kaydedici eklentisini derledikten sonra, sonuçta elde edilen DLL 'yi iki konumdan birine yerleştirin:

- *% ProgramFiles (x86)% \ Microsoft Visual Studio \\ [sürüm] \\ [Edition] \Common7\IDE\PrivateAssemblies\WebTestPlugins*

- *%Userprofile%\, Studio [sürüm] \WebTestPlugins*

> [!WARNING]
> Kaydedici eklentisini iki konumdan birine kopyaladıktan sonra, kaydedici eklentisinin kaydedilmesi için Visual Studio 'Yu yeniden başlatmanız gerekir.

### <a name="execute-the-recorder-plug-in"></a>Kaydedici eklentisini yürütme

1. Yeni bir Web performans testi oluşturun.

     **Enable WebTestRecordPlugins 'i** iletişim kutusu görüntülenir.

2. Kaydedici eklentisinin onay kutusunu seçin ve **Tamam**' ı seçin.

     Web performans testi kaydetmeyi tamamladıktan sonra yeni Kaydedici eklentisi yürütülür.

    > [!WARNING]
    > Eklentiyi kullanan bir Web performans testi veya yük testi çalıştırdığınızda aşağıdakine benzer bir hata alabilirsiniz:
    >
    > **İstek başarısız oldu: olayda özel durum \<plug-in> : dosya veya derleme ' \<"Plug-in name".dll file> , sürüm = \<n.n.n.n> , kültür = neutral, PublicKeyToken = null ' veya bağımlılıklarından biri yüklenemedi. Sistem belirtilen dosyayı bulamıyor.**
    >
    > Bu, eklentilerinizin herhangi birine kod değişikliği yaptığınızda ve yeni bir DLL sürümü **(sürüm = 0.0.0.0)** oluşturuyorsanız, ancak eklentinin özgün eklenti sürümüne başvurmaya devam ediyorsa oluşur. Bu sorunu düzeltmek için aşağıdaki adımları izleyin:
    >
    > 1. Web performansı ve yük testi projenizde, başvurularda bir uyarı görürsünüz. Başvuruyu eklenti DLL 'nize kaldırın ve yeniden ekleyin.
    > 2. Testinizden veya uygun konumdan eklentiyi kaldırın ve ardından yeniden ekleyin.

## <a name="example"></a>Örnek

Bu örnek, özel dinamik parametre bağıntısını gerçekleştirmek için özelleştirilmiş bir Web başarım testi Kaydedicisi eklentisinin nasıl oluşturulacağını gösterir.

> [!NOTE]
> Örnek kodun tüm listesi bu konunun en altında bulunur.

### <a name="iterate-through-the-result-to-find-first-page-with-reportsession"></a>ReportSession ile ilk sayfayı bulmak için sonucu yineleyin

Kod örneğinin bu bölümü, kaydedilen her nesne boyunca yinelenir ve ReportSession için yanıt gövdesini arar.

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

### <a name="add-an-extraction-rule"></a>Ayıklama kuralı ekle

Artık bir yanıt bulunmuştur, bir ayıklama kuralı eklemeniz gerekir. Kod örneğinin bu bölümü, sınıfını kullanarak ayıklama kuralı oluşturur <xref:Microsoft.VisualStudio.TestTools.WebTesting.ExtractionRuleReference> ve ardından, ayıklama kuralını eklemek için Web performans testinde doğru isteği bulur. Her sonuç nesnesinin, Web performans testinin doğru isteği almak için kodda kullanılan DeclarativeWebTestItemId adlı yeni bir özelliği eklenmiştir.

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

Artık kod, ReportSession adlı tüm sorgu dizesi parametrelerini ad olarak bulur ve değeri kod örneğinin bu bölümünde gösterildiği gibi {{SessionID}} olarak değiştirir:

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
- [Yük testleri için özel kod ve eklentiler oluşturma](../test/create-custom-code-and-plug-ins-for-load-tests.md)
- [Kodlanmış web performans testi oluşturma](../test/generate-and-run-a-coded-web-performance-test.md)
