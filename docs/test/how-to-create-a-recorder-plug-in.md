---
title: Web performans testleri için Kaydedici Eklentisi Oluşturma
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- Web performance tests, recorder plug-in
ms.assetid: 6fe13be1-aeb5-4927-9bff-35950e194da9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5e32faa4525edc79da3d759d67ad2b5676f38fc2
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75589166"
---
# <a name="how-to-create-a-recorder-plug-in"></a>Nasıl yapilir: Kaydedici eklentisi oluşturma

Kaydedilen <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRecorderPlugin> bir web performans testini değiştirmenize olanak tanır. Değişiklik, **Web Performans Test Kaydedici** araç çubuğunda **Durdur'u** seçtikten sonra ancak testin kaydedilip Web Performans Testi Düzenleyicisi'nde sunulmasından önce oluşur.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Kaydedici eklentisi, dinamik parametreler üzerinde kendi özel bağıntınızı gerçekleştirmenizi sağlar. Yerleşik korelasyon işleviyle, web performans testleri tamamlandıktan sonra veya **Web Performans Testi Düzenleyicisi** araç çubuğunda **Dinamik Parametreleri Web Test Parametrelerine Yükselt'i** kullandığınızda web kaydındaki dinamik parametreleri algılar. Ancak, yerleşik algılama işlevselliği her zaman tüm dinamik parametreleri bulamaz. Örneğin, genellikle değerini 5 ila 30 dakika arasında değişen alır bir oturum kimliği bulamaz. Bu nedenle, korelasyon işlemini el ile gerçekleştirmeniz gerekir.

Kendi <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRecorderPlugin> özel eklentiniz için kod yazmanızı sağlar. Bu eklenti, web performans testi kaydedilmeden ve Web Performans Testi Düzenleyicisi'nde sunulmadan önce korelasyon yapabilir veya web performans testini birçok şekilde değiştirebilir. Bu nedenle, belirli bir dinamik değişkenin kayıtlarınızın çoğu için korelasyon olması gerektiğini belirlerseniz, işlemi otomatikleştirebilirsiniz.

Kaydedici eklentisi kullanılabilir diğer bazı yolları çıkarma ve doğrulama kuralları eklemek için, bağlam parametreleri ekleme veya bir web performans testinde hareketlere yorum dönüştürme.

Aşağıdaki yordamlar, kaydedici eklentisi için temel kodun nasıl oluşturulup, eklentiyi nasıl dağıtılanın ve eklentiyi nasıl çalıştırıştırılacak açıklanır. Yordamları izleyen örnek kod, özel dinamik parametre korelasyon kaydedici eklentisi oluşturmak için Visual C# nasıl kullanılacağını gösterir.

## <a name="create-a-recorder-plug-in"></a>Kaydedici eklentisi oluşturma

### <a name="to-create-a-recorder-plug-in"></a>Kaydedici eklentisi oluşturmak için

1. Bir kaydedici eklentisi oluşturmak istediğiniz web performans testi ile web performansı ve yükleme testi projesi içeren bir çözüm açın.

2. Çözüme yeni bir **Sınıf Kitaplığı** projesi ekleyin.

3. **Çözüm Gezgini'nde,** yeni sınıf kitaplığı proje klasöründe, **Başvurular** klasörüne sağ tıklayın ve **Başvuru Ekle'yi**seçin.

    > [!TIP]
    > Yeni bir sınıf kitaplık proje klasörüne örnek **RecorderPlugins**olduğunu.

     **Başvuru Ekle** iletişim kutusu görüntülenir.

4. **.NET** sekmesini seçin.

5. Aşağı kaydırın ve **Microsoft.VisualStudio.QualityTools.WebTestFramework** seçin ve sonra **Tamam**seçin.

     **Microsoft.VisualStudio.QualityTools.WebTestFramework** **Solution Explorer'daki** **Başvurular** klasörüne eklenir.

6. Kaydedici eklentinizin kodunu yazın. İlk olarak, türetilmiştir yeni bir <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRecorderPlugin>ortak sınıf oluşturun.

7. <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRecorderPlugin.PostWebTestRecording*> Yöntemi geçersiz kılın.

    ```csharp
    public class Class1 : WebTestRecorderPlugin
        {
            public override void PostWebTestRecording(object sender, PostWebTestRecordingEventArgs e)
            {
                base.PostWebTestRecording(sender, e);
            }
        }
    ```

     Olay bağımsız değişkenleri size çalışmanız gereken iki nesne verir: kaydedilen sonuç ve kaydedilen web performans testi. Bu, belirli değerleri ararken sonucu yinelemenize ve değişiklikler yapmak için web performans testinde aynı isteğe atlamanıza olanak sağlar. Bir bağlam parametresi eklemek veya URL'nin bölümlerini parametrelendirmek istiyorsanız, web performans testini de değiştirebilirsiniz.

    > [!NOTE]
    > Web performans testini değiştirirseniz, özelliği de <xref:Microsoft.VisualStudio.TestTools.WebTesting.PostWebTestRecordingEventArgs.RecordedWebTestModified*> doğru ayarlamanız gerekir:`e.RecordedWebTestModified = true;`

8. Web kaydı gerçekleştikten sonra kaydedici eklentisinin çalıştırmasını istediğiniz koda göre daha fazla kod ekleyin. Örneğin, aşağıdaki örnekte gösterildiği gibi özel korelasyon işlemek için kod ekleyebilirsiniz. Ayrıca, yorumları hareketlere dönüştürme veya web performans testine doğrulama kuralları ekleme gibi şeyler için bir kaydedici eklentisi oluşturabilirsiniz.

9. **Yapı** menüsünde, ** \<yapı sınıfı kitaplığı proje adını>** seçin.

Ardından, Visual Studio'ya kaydolması için kaydedici eklentisini dağıtın.

### <a name="deploy-the-recorder-plug-in"></a>Kaydedici eklentisini dağıtma

Kaydedici eklentisini derledikten sonra, ortaya çıkan DLL'yi iki konumdan birine yerleştirin:

- *%ProgramFiles(x86)%\Microsoft Visual\\Studio\\[sürüm] [edition]\Common7\IDE\PrivateAssemblies\WebTestPlugins*

- *%USERPROFILE%\Documents\Visual Studio [sürüm]\WebTestPlugins*

> [!WARNING]
> Kaydedici eklentisini iki konumdan birine kopyaladıktan sonra, kayıt cihazı eklentisinin kaydedilmesi için Visual Studio'yu yeniden başlatmanız gerekir.

### <a name="execute-the-recorder-plug-in"></a>Kaydedici eklentisini çalıştırma

1. Yeni bir web performans testi oluşturun.

     **WebTestRecordPlugins** iletişim kutusunu etkinleştirin görüntülenir.

2. Kaydedici eklentisi için onay kutusunu seçin ve **Tamam'ı**seçin.

     Web performans testi kaydı tamamladıktan sonra, yeni kaydedici eklentisi yürütülür.

    > [!WARNING]
    > Eklentinizi kullanan bir web performans testi veya yükleme testi çalıştırdığınızda aşağıdakilere benzer bir hata alabilirsiniz:
    >
    > **İstek başarısız oldu: Eklenti> olayında \<özel durum:\<Dosya veya derleme ' "Eklenti adı".dll dosyası>, Sürüm=\<n.n.n>, Culture=neutral, PublicKeyToken=null' veya bağımlılıklarından birini yükleyemedi. Sistem belirtilen dosyayı bulamıyor.**
    >
    > Bunun nedeni, eklentilerinizden herhangi birinde kod değişiklikleri yapar ve yeni bir DLL sürümü **(Sürüm=0.0.0.0)** oluşturursanız, ancak eklenti hala orijinal eklenti sürümüne başvurur. Bu sorunu gidermek için aşağıdaki adımları izleyin:
    >
    > 1. Web performansı ve yükleme testi projenizde, başvurularda bir uyarı görürsünüz. Başvuruyu çıkarın ve eklentiniz DLL'ye yeniden ekleyin.
    > 2. Eklentiyi testinizden veya uygun konumdan çıkarın ve sonra geri ekleyin.

## <a name="example"></a>Örnek

Bu örnek, özel dinamik parametre korelasyon gerçekleştirmek için özelleştirilmiş bir web performans test kaydedici eklentisi oluşturmak için nasıl gösterir.

> [!NOTE]
> Örnek kodun tam bir listesi bu konunun alt kısmında yer alır.

### <a name="iterate-through-the-result-to-find-first-page-with-reportsession"></a>ReportSession ile ilk sayfayı bulmak için sonucu yineleyin

Kod örneğinin bu bölümü, kaydedilen her nesne üzerinden yinelenir ve Yanıt Gövdesi'ni ReportSession için arar.

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

### <a name="add-an-extraction-rule"></a>Çıkarma kuralı ekleme

Bir yanıt bulunduğuna göre, bir çıkarma kuralı eklemeniz gerekir. Kod örneğinin bu bölümü <xref:Microsoft.VisualStudio.TestTools.WebTesting.ExtractionRuleReference> sınıfı kullanarak çıkarma kuralını oluşturur ve sonra çıkarma kuralını eklemek için web performans testinde doğru isteği bulur. Her sonuç nesnesi, web performans testinden doğru isteği almak için kodda kullanılan bildirimsel WebTestItemId adında yeni bir özelliğe sahiptir.

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

### <a name="replace-query-string-parameters"></a>Sorgu dize parametrelerini değiştirme

Şimdi kod, ReportSession'ı ad olarak içeren tüm sorgu dize parametrelerini bulur ve kod örneğinin bu bölümünde gösterildiği gibi değeri {{SessionId}} olarak değiştirir:

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
