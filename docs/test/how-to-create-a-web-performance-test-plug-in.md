---
title: Bir Web performans testi eklentisi oluşturma
ms.date: 10/03/2016
ms.topic: conceptual
f1_keywords:
- vs.test.web.webtestplugin
helpviewer_keywords:
- Web performance tests, creating plug-ins
- plug-ins, creating in Web performance tests
ms.assetid: a612f2d2-9806-477d-a126-12842f07da6e
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: cc2eeafa41b953f9d853c7ff435a6a9706ae73ca
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75589116"
---
# <a name="how-to-create-a-web-performance-test-plug-in"></a>Nasıl yapılır: web performans testi eklentisi oluşturma

Web performans testleri eklentileri yalıtmak ve ana bildirim deyimleri, web performans testinde dışındaki kod yeniden kullanımını etkinleştirin. Özelleştirilmiş web performans testi eklentisi web performans testini çalıştırma gibi bazı kod çağırmak için bir yol sunar. Web performans testi eklentisi, her test yinelemesi için bir kez çalıştırılır. Testi Eklentisi PreRequest veya PostRequest yöntemlerini geçersiz kılarsanız, ayrıca, bu istek eklentileri önce veya sonra her bir istek sırasıyla çalışır.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Kendi sınıftan türetme tarafından özelleştirilmiş web performans testi eklentisi oluşturabilirsiniz <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestPlugin> temel sınıfı.

Özelleştirilmiş web performans testi eklentileri en az miktarda bir büyük bir web performans testleri üzerinde denetim düzeyini elde etmek için kod yazmanızı sağlayan bir web performans testleri kaydetmiş olduğunuz kullanabilirsiniz. Ancak, bunları kodlanmış web performans testleri ile de kullanabilirsiniz. Daha fazla bilgi için [oluştur ve Çalıştır kodlanmış web performans testi](../test/generate-and-run-a-coded-web-performance-test.md).

> [!NOTE]
> Ayrıca, yük testi eklentileri de oluşturabilirsiniz. Bkz. [nasıl yapılır: yük testi eklentisi oluşturma](../test/how-to-create-a-load-test-plug-in.md).

## <a name="to-create-a-custom-web-performance-test-plug-in"></a>Özel bir web performans testi eklentisi oluşturmak için

1. Bir web performansı ve bir web performans testi içeren bir yük testi projesi açın.

2. İçinde **Çözüm Gezgini**, çözüme sağ tıklayın ve seçin **Ekle** seçip **yeni proje**.

3. Yeni bir **sınıf kitaplığı** projesi oluşturun.

   Yeni sınıf kitaplığı projesi eklenir **Çözüm Gezgini** ve yeni bir sınıf görünür **Kod Düzenleyicisi**.

4. İçinde **Çözüm Gezgini**, sağ **başvuruları** seçin ve yeni sınıf kitaplığı klasöründe **Başvuru Ekle**.

   **Başvuru Ekle** iletişim kutusu görüntülenir.

5. Seçin **.NET** sekmesinde, aşağı kaydırın ve seçin **Microsoft.VisualStudio.QualityTools.WebTestFramework**

6. **Tamam**’ı seçin.

     Başvuru **Microsoft.VisualStudio.QualityTools.WebTestFramework** eklenir **başvuru** klasöründe **Çözüm Gezgini**.

7. İçinde **Çözüm Gezgini**, web performans en üst düğüme sağ tıklayın ve web performans testi seçin ve eklentisini eklemek istediğiniz yük testini içeren test projesi yük **Add Reference**.

8. **Başvuru Ekle iletişim kutusu görüntülenir**.

9. Seçin **projeleri** sekmenize **sınıf kitaplığı projesi**.

10. **Tamam**’ı seçin.

11. İçinde **Kod Düzenleyicisi**, eklentinizin kodunu yazın. İlk olarak, türetilen yeni bir ortak sınıf oluşturun <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestPlugin>.

12. Bir veya daha fazla olay işleyicileri içinde kod uygulayın. Örnek uygulama için aşağıdaki örnek bölümüne bakın.

    - <xref:Microsoft.VisualStudio.TestTools.WebTesting.PostWebTestRecordingEventArgs>

    - <xref:Microsoft.VisualStudio.TestTools.WebTesting.PostWebTestEventArgs>

    - <xref:Microsoft.VisualStudio.TestTools.WebTesting.PreRequestEventArgs>

    - <xref:Microsoft.VisualStudio.TestTools.WebTesting.PostRequestEventArgs>

    - <xref:Microsoft.VisualStudio.TestTools.WebTesting.PrePageEventArgs>

    - <xref:Microsoft.VisualStudio.TestTools.WebTesting.PostPageEventArgs>

    - <xref:Microsoft.VisualStudio.TestTools.WebTesting.PreTransactionEventArgs>

    - <xref:Microsoft.VisualStudio.TestTools.WebTesting.PostTransactionEventArgs>

13. Kodu yazdıktan sonra yeni projeyi derleyin.

14. Bir web performans testi açın.

15. Web performans testi eklentisini eklemek için **Web Testi Eklentisi Ekle** araç.

     **Web Testi Eklentisi Ekle** iletişim kutusu görüntülenir.

16. Altında **bir eklenti seçin**seçin, web performans testi eklentisi sınıfı.

17. İçinde **özelliklerini çili eklenti** bölmesinde, çalışma zamanında kullanmak eklenti için başlangıç değerlerini ayarlayın.

    > [!NOTE]
    > Eklentilerinizi istediğiniz sayıda özelliği getirebilir; bunları yalnızca genel, ayarlanabilir ve tam sayı, Boole veya dize gibi bir temel türden yapın. Özellikler penceresini kullanarak web başarım testi eklentisi özelliklerini daha sonra da değiştirebilirsiniz.

18. **Tamam**’ı seçin.

     Eklenti eklenir **Web testi eklentileri** klasör.

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

Aşağıdaki kod, bir öğe ekleyen bir özelleştirilmiş web performans testi eklentisi oluşturur <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestContext> temsil eden test yinelemesi.

Web performans testi çalıştırdıktan sonra bunu kullanarak eklenti adlı eklenen öğeyi gördüğünüz **TestIteratnionNumber** içinde **bağlam** sekmesinde **Web Performans Sonuçları Görüntüleyicisi** .

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
- [Özel kod ve yük testleri için eklentiler oluşturma](../test/create-custom-code-and-plug-ins-for-load-tests.md)
- [Nasıl yapılır: istek düzeyi eklentisi oluşturma](../test/how-to-create-a-request-level-plug-in.md)
- [Kodu bir web performans testi için özel bir ayıklama kuralı](../test/code-a-custom-extraction-rule-for-a-web-performance-test.md)
- [Kodu bir web performans testi için özel doğrulama kuralı](../test/code-a-custom-validation-rule-for-a-web-performance-test.md)
- [Nasıl yapılır: bir yük testi eklentisi oluşturma](../test/how-to-create-a-load-test-plug-in.md)
- [Oluşturma ve bir kodlanmış web performans testini çalıştırma](../test/generate-and-run-a-coded-web-performance-test.md)
