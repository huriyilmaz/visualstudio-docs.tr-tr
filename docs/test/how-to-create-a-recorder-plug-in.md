---
title: Web performans testleri Plug-In Recorder uygulaması oluşturma
description: WebTestRecorderPlugin'in Web Performans Testi Kaydedicisi araç çubuğunda Durdur'ı seçtikten sonra kayıtlı bir web performans testini nasıl değiştirmenizi sağlar?
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- Web performance tests, recorder plug-in
ms.assetid: 6fe13be1-aeb5-4927-9bff-35950e194da9
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.openlocfilehash: 55a12f6ea6fb342adf3aacc8967f8fc62020696a
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122148590"
---
# <a name="how-to-create-a-recorder-plug-in"></a>Nasıl kullanılır: Kaydedici eklentisi oluşturma

, <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRecorderPlugin> kayıtlı bir web performans testini değiştirmenize olanak sağlar. Değişiklik, **Web** Performans Testi Kaydedicisi **araç** çubuğunda Durdur'ı seçtikten sonra, test kaydediledikten ve testte Web Performans Testi Düzenleyicisi.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Kaydedici eklentisi, dinamik parametreler üzerinde kendi özel bağıntınızı gerçekleştirmenize olanak sağlar. Yerleşik bağıntı işleviyle, web performans testleri tamamlandıktan sonra web kaydında dinamik parametreleri algılar veya web araç çubuğunda Dinamik Parametreleri **Web Testi** Parametrelerine **Yükselt'i Web Performans Testi Düzenleyicisi** algılar. Ancak, yerleşik algılama işlevi her zaman tüm dinamik parametreleri bulamaz. Örneğin, genellikle değerini 5 ile 30 dakika arasında değiştiren bir oturum kimliği bulamaz. Bu nedenle bağıntı işlemini el ile gerçekleştirmeniz gerekir.

, <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRecorderPlugin> kendi özel eklentiniz için kod yazmanızı sağlar. Bu eklenti, web performans testini kaydedilebilir ve web'de Web Performans Testi Düzenleyicisi. Bu nedenle, kayıtların büyük bir çoğu için belirli bir dinamik değişkenin arasında ilişki olması gerektirse de işlemi otomatikleştirmeniz gerekir.

Kaydedici eklentisinin kullanıla diğer yöntemlerden bazıları ayıklama ve doğrulama kuralları eklemek, bağlam parametreleri eklemek veya web performans testinde yorumları işlemlere dönüştürmektir.

Aşağıdaki yordamlar kaydedici eklentisi için ilkel kodun nasıl oluşturularak eklentinin nasıl dağıtıla ve eklentiyi yürütmeyi açıklar. Yordamları takip eden örnek kod, Özel dinamik parametre bağıntı kaydedici eklentisi oluşturmak için Visual C# kullanmayı gösterir.

## <a name="create-a-recorder-plug-in"></a>Kaydedici eklentisi oluşturma

### <a name="to-create-a-recorder-plug-in"></a>Kaydedici eklentisi oluşturmak için

1. Kaydedici eklentisi oluşturmak istediğiniz web performans testini içeren web performansı ve yük testi projesini içeren bir çözüm açın.

2. Çözüme **yeni bir Sınıf** Kitaplığı projesi ekleyin.

3. Yeni **Çözüm Gezgini** kitaplığı proje klasöründe Başvurular klasörüne sağ tıklayın ve **Başvuru** Ekle'yi **seçin.**

    > [!TIP]
    > **RecorderPlugins,** yeni bir sınıf kitaplığı proje klasörü örneğidir.

     Başvuru **Ekle** iletişim kutusu görüntülenir.

4. **.NET sekmesini** seçin.

5. Aşağı kaydırın ve **Microsoft.VisualStudio.QualityTools.WebTestFramework öğesini ve** ardından Tamam'ı **seçin.**

     **Microsoft.VisualStudio.QualityTools.WebTestFramework,**  **Çözüm Gezgini.**

6. Kaydedici eklentinizin kodunu yazın. İlk olarak, 'den türeten yeni bir genel sınıf <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRecorderPlugin> oluşturun.

7. yöntemini geçersiz <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRecorderPlugin.PostWebTestRecording*> kılın.

    ```csharp
    public class Class1 : WebTestRecorderPlugin
        {
            public override void PostWebTestRecording(object sender, PostWebTestRecordingEventArgs e)
            {
                base.PostWebTestRecording(sender, e);
            }
        }
    ```

     Olay bağımsız değişkenleri, çalışmak için size iki nesne verir: kaydedilen sonuç ve kaydedilen web performans testi. Bu, belirli değerleri arayan sonucu yineler ve ardından değişiklik yapmak için web performans testinde aynı itene atlar. Bağlam parametresi eklemek veya URL'nin bölümlerini parametreleştirmek için web performans testini de değiştirebilirsiniz.

    > [!NOTE]
    > Web performans testini değiştirirsanız özelliğini true olarak da <xref:Microsoft.VisualStudio.TestTools.WebTesting.PostWebTestRecordingEventArgs.RecordedWebTestModified*> ayarlamanız gerekir: `e.RecordedWebTestModified = true;`

8. Web kaydı olduktan sonra kaydedici eklentisinin yürütmesini istediğiniz koda göre daha fazla kod ekleyin. Örneğin, aşağıdaki örnekte gösterildiği gibi özel bağıntıyı işlemek için kod indirebilirsiniz. Ayrıca, yorumları işlemlere dönüştürme veya web performans testinde doğrulama kuralları ekleme gibi işlemler için bir kaydedici eklentisi de oluşturabilirsiniz.

9. Derleme **menüsünde,** Derleme'yi **seçin. \<class library project name>**

Ardından, kaydedicinin Visual Studio'a kaydolması için kaydedici eklentisini Visual Studio.

### <a name="deploy-the-recorder-plug-in"></a>Kaydedici eklentisini dağıtma

Kaydedici eklentiyi derledikten sonra, sonuçta elde edilen DLL'i iki konumdan biri olarak ekleyin:

- *%ProgramFiles(x86)%\Microsoft Visual Studio \\ \\ [version] [edition]\Common7\IDE\PrivateAssemblies\WebTestPlugins*

- *%USERPROFILE%\Documents\Visual Studio [version]\WebTestPlugins*

> [!WARNING]
> Kaydedici eklentiyi iki konumdan birinin üzerine kopyalayıp kaydedici eklentisinin Visual Studio için cihazı yeniden başlatmanız gerekir.

### <a name="execute-the-recorder-plug-in"></a>Kaydedici eklentiyi yürütme

1. Yeni bir web performans testi oluşturun.

     **WebTestRecordPlugins'i Etkinleştir** iletişim kutusu görüntülenir.

2. Kaydedici eklentisinin onay kutusunu işaretleyin ve Tamam'ı **seçin.**

     Web performans testi kaydı tamamlandıktan sonra yeni kaydedici eklentisi yürütülür.

    > [!WARNING]
    > Eklentinizi kullanan bir web performans testi veya yük testi çalıştırarak aşağıdakine benzer bir hata alabilirsiniz:
    >
    > **İstek başarısız oldu: Olayda özel durum: Dosya veya derleme \<plug-in> yüklenemedi ' \<"Plug-in name".dll file> , Version= , \<n.n.n.n> Culture=neutral, PublicKeyToken=null' veya bağımlılıklarından biri. Sistem belirtilen dosyayı bulamıyor.**
    >
    > Bunun nedeni, eklentilerinizin herhangi biri için kod değişiklikleri yapmak ve yeni bir DLL sürümü **(Version=0.0.0.0)** oluşturmaktır, ancak eklenti hala özgün eklenti sürümüne başvurur. Bu sorunu düzeltmek için şu adımları izleyin:
    >
    > 1. Web performansı ve yük testi projesinde başvurularda bir uyarı görüyorsunuz. Eklenti DLL'nize başvuru kaldırın ve yeniden ekleyin.
    > 2. Eklentiyi testten veya uygun konumdan kaldırın ve yeniden ekleyin.

## <a name="example"></a>Örnek

Bu örnekte, özel dinamik parametre bağıntısı gerçekleştirmek için özelleştirilmiş bir web performansı test kaydedici eklentisinin nasıl oluşturularak ilgili örnek gösterildi.

> [!NOTE]
> Örnek kodun tam listesi bu konunun en altında yer almaktadır.

### <a name="iterate-through-the-result-to-find-first-page-with-reportsession"></a>ReportSession ile ilk sayfayı bulmak için sonucun üzerinden geçebilirsiniz

Kod örneğinin bu bölümü, kaydedilen her nesnede aynı şekilde ilerler ve yanıt gövdesinde ReportSession aramalarını sağlar.

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

### <a name="add-an-extraction-rule"></a>Ayıklama kuralı ekleme

Artık bir yanıt bulunduğuna göre, bir ayıklama kuralı eklemeniz gerekir. Kod örneğinin bu bölümü sınıfını kullanarak ayıklama kuralını oluşturur ve ardından ayıklama kuralını eklemek için <xref:Microsoft.VisualStudio.TestTools.WebTesting.ExtractionRuleReference> web performans testinde doğru isteği bulur. Her sonuç nesnesine, web performans testinde doğru isteği almak için kodda kullanılan DeclarativeWebTestItemId adlı yeni bir özellik eklenir.

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

### <a name="replace-query-string-parameters"></a>Sorgu dizesi parametrelerini değiştirme

Kod artık ad olarak ReportSession içeren tüm sorgu dizesi parametrelerini bulur ve kod örneğinin bu bölümünde gösterildiği gibi değeri {{SessionId}} olarak değiştirir:

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
