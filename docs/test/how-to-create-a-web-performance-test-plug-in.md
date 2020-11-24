---
title: Web başarım testi oluşturma Plug-In
description: Web performans testi eklentilerinin, Web performans testinizde ana bildirim deyimleri dışında kodu yeniden kullanmanıza nasıl olanak sağladığını öğrenin.
ms.custom: SEO-VS-2020
ms.date: 10/03/2016
ms.topic: how-to
f1_keywords:
- vs.test.web.webtestplugin
helpviewer_keywords:
- Web performance tests, creating plug-ins
- plug-ins, creating in Web performance tests
ms.assetid: a612f2d2-9806-477d-a126-12842f07da6e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5ddb46b3e83c86396dfea6fbcdb3584882591fce
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2020
ms.locfileid: "95442348"
---
# <a name="how-to-create-a-web-performance-test-plug-in"></a>Nasıl yapılır: Web başarım testi eklentisi oluşturma

Web performans testleri eklentileri, Web performans testinizde ana bildirim deyimleri dışında kodu yalıtmanızı ve yeniden kullanmanıza olanak tanır. Özelleştirilmiş bir Web performans testi eklentisi, Web performans testi çalıştırıldığında bazı kodları çağırmak için bir yol sunar. Web performans testi eklentisi her test yinelemesi için bir kez çalıştırılır. Ayrıca, test eklentisindeki ön koşul veya PostRequest yöntemlerini geçersiz kılarsınız, bu istek eklentileri sırasıyla her istekten önce veya sonra çalışır.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Temel sınıftan kendi sınıfınızı türeterek özelleştirilmiş bir Web başarım testi eklentisi oluşturabilirsiniz <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestPlugin> .

Web performans testleriniz üzerinde daha fazla denetim elde etmek için en az miktarda kod yazmanızı sağlayan, kaydettiğiniz Web performans testleriyle özelleştirilmiş Web performans testi eklentilerini kullanabilirsiniz. Ancak, bunları kodlanmış Web performans testleri ile de kullanabilirsiniz. Daha fazla bilgi için bkz. [kodlanmış Web performans testi oluşturma ve çalıştırma](../test/generate-and-run-a-coded-web-performance-test.md).

> [!NOTE]
> Ayrıca, yük testi eklentileri de oluşturabilirsiniz. Bkz. [nasıl yapılır: yük testi eklentisi oluşturma](../test/how-to-create-a-load-test-plug-in.md).

## <a name="to-create-a-custom-web-performance-test-plug-in"></a>Özel bir Web başarım testi eklentisi oluşturmak için

1. Web performans testi içeren bir Web performans ve yük testi projesi açın.

2. **Çözüm Gezgini**, çözüme sağ tıklayın ve **Ekle** ' yi seçin ve ardından **Yeni proje**' yi seçin.

3. Yeni bir **sınıf kitaplığı** projesi oluşturun.

   Yeni sınıf kitaplığı projesi **Çözüm Gezgini** eklenir ve yeni sınıf **kod düzenleyicisinde** görüntülenir.

4. **Çözüm Gezgini**' de, yeni sınıf kitaplığındaki **Başvurular** klasörüne sağ tıklayın ve **Başvuru Ekle**' yi seçin.

   **Başvuru Ekle** iletişim kutusu görüntülenir.

5. **.Net** sekmesini seçin, aşağı kaydırın ve **Microsoft. VisualStudio. QualityTools. WebTestFramework** öğesini seçin

6. **Tamam ' ı** seçin.

     **Microsoft. VisualStudio. QualityTools. WebTestFramework** başvurusu **Çözüm Gezgini** içindeki **başvuru** klasörüne eklenir.

7. **Çözüm Gezgini**' de, Web performans testi eklentisini eklemek istediğiniz yük testini içeren Web performansı ve yük testi projesinin üst düğümüne sağ tıklayın ve **Başvuru Ekle**' yi seçin.

8. **Başvuru Ekle iletişim kutusu görüntülenir**.

9. **Projeler** sekmesini seçin ve **Sınıf Kitaplığı projesini** seçin.

10. **Tamam ' ı** seçin.

11. **Kod düzenleyicisinde**, eklentinin kodunu yazın. İlk olarak, öğesinden türetilen yeni bir ortak sınıf oluşturun <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestPlugin> .

12. Kodu bir veya daha fazla olay işleyicisinin içinde uygulayın. Örnek bir uygulama için aşağıdaki örnek bölümüne bakın.

    - <xref:Microsoft.VisualStudio.TestTools.WebTesting.PostWebTestRecordingEventArgs>

    - <xref:Microsoft.VisualStudio.TestTools.WebTesting.PostWebTestEventArgs>

    - <xref:Microsoft.VisualStudio.TestTools.WebTesting.PreRequestEventArgs>

    - <xref:Microsoft.VisualStudio.TestTools.WebTesting.PostRequestEventArgs>

    - <xref:Microsoft.VisualStudio.TestTools.WebTesting.PrePageEventArgs>

    - <xref:Microsoft.VisualStudio.TestTools.WebTesting.PostPageEventArgs>

    - <xref:Microsoft.VisualStudio.TestTools.WebTesting.PreTransactionEventArgs>

    - <xref:Microsoft.VisualStudio.TestTools.WebTesting.PostTransactionEventArgs>

13. Kodu yazdıktan sonra yeni projeyi derleyin.

14. Web performans testini açın.

15. Web performans testi eklentisini eklemek için araç çubuğunda **Web testi eklentisi Ekle** ' yi seçin.

     **Web testi eklentisi Ekle** iletişim kutusu görüntülenir.

16. **Eklenti seçin** altında Web başarım testi eklenti sınıfınızı seçin.

17. **Seçili eklenti bölmesinin Özellikler** bölümünde, çalışma zamanında kullanılacak eklentinin başlangıç değerlerini ayarlayın.

    > [!NOTE]
    > Eklentilerinizi istediğiniz kadar çok özelliği kullanıma sunabilirsiniz. bunları ortak, ayarlanabilir ve tamsayı, Boole veya dize gibi bir temel tür yapmanız yeterlidir. Web performans testi eklentisi özelliklerini daha sonra Özellikler penceresi kullanarak da değiştirebilirsiniz.

18. **Tamam ' ı** seçin.

     Eklenti, **Web testi eklentileri** klasörüne eklenir.

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

Aşağıdaki kod, <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestContext> Test yinelemesini temsil eden öğesine bir öğe ekleyen özelleştirilmiş bir Web performans testi eklentisi oluşturur.

Web performans testini çalıştırdıktan sonra, bu eklentiyi kullanarak, **Web performans sonuçları görüntüleyicisinde** **bağlam** sekmesinde **Testeratnionnumber** adlı eklenen öğeyi görebilirsiniz.

```csharp
using System;
using System.Collections.Generic;
using System.Text;
using System.ComponentModel;
using Microsoft.VisualStudio.TestTools.WebTesting;

namespace SampleRules
{
    [Description("This plugin can be used to set the ParseDependentsRequests property for each request")]
    public class SampleWebTestPlugin : WebTestPlugin
    {
        private bool m_parseDependents = true;

        public override void PreWebTest(object sender, PreWebTestEventArgs e)
        {
            // TODO: Add code to execute before the test.
        }

        public override void PostWebTest(object sender, PostWebTestEventArgs e)
        {
            // TODO: Add code to execute after the test.
        }

        public override void PreRequest(object sender, PreRequestEventArgs e)
        {
            // Code to execute before each request.
            // Set the ParseDependentsRequests value on the request
            e.Request.ParseDependentRequests = m_parseDependents;
        }

        // Properties for the plugin.
        [DefaultValue(true)]
        [Description("All requests will have their ParseDependentsRequests property set to this value")]
        public bool ParseDependents
        {
            get
            {
                return m_parseDependents;
            }
            set
            {
                m_parseDependents = value;
            }
        }
    }
}
```

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequestPlugin>
- [Yük testleri için özel kod ve eklentiler oluşturma](../test/create-custom-code-and-plug-ins-for-load-tests.md)
- [Nasıl yapılır: istek düzeyi eklentisi oluşturma](../test/how-to-create-a-request-level-plug-in.md)
- [Web performans testi için özel bir ayıklama kuralı kodlayın](../test/code-a-custom-extraction-rule-for-a-web-performance-test.md)
- [Web performans testi için özel doğrulama kuralı kodu oluşturma](../test/code-a-custom-validation-rule-for-a-web-performance-test.md)
- [Nasıl yapılır: yük testi eklentisi oluşturma](../test/how-to-create-a-load-test-plug-in.md)
- [Kodlanmış web performans testi oluşturma](../test/generate-and-run-a-coded-web-performance-test.md)
