---
title: Web Performans Testi oluşturma Plug-In
description: Web performans testi eklentilerinin kodu web performans testinde ana bildirim deyimleri dışında yeniden kullanmanıza nasıl olanak olduğunu öğrenin.
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
manager: jmartens
ms.technology: vs-ide-test
ms.openlocfilehash: b3134ab644ec378c5c2869c5eb35a40c119e48dabb210a0dbf552c04d51eb8ba
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121395219"
---
# <a name="how-to-create-a-web-performance-test-plug-in"></a>Nasıl: Web performans testi eklentisi oluşturma

Web performans testleri eklentileri, web performans testinde kodu ana bildirim deyimlerinin dışında yalıtmanıza ve yeniden kullanmanıza olanak sağlar. Özelleştirilmiş web performansı testi eklentisi, web performans testi çalıştırıldıklarında kod çağırmanın bir yolunu sunar. Web performans testi eklentisi her test yinelemesi için bir kez sınanıyor. Ayrıca, test eklentisinde PreRequest veya PostRequest yöntemlerini geçersiz kılarsanız, bu istek eklentileri sırasıyla her istekten önce veya sonra çalıştırılmaz.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Kendi sınıfınızı temel sınıftan türeterek özelleştirilmiş bir web performansı testi eklentisi <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestPlugin> oluşturabilirsiniz.

Web performans testleri üzerinde daha yüksek bir denetim düzeyi elde etmek için az miktarda kod yazmanıza olanak sağlayan, kaydedilmiş web performans testleri ile özelleştirilmiş web performansı testi eklentilerini kullanabilirsiniz. Ancak, bunları kodlu web performans testleriyle de kullanabilirsiniz. Daha fazla bilgi için [bkz. Kodlu web performansı testi oluşturma ve çalıştırma.](../test/generate-and-run-a-coded-web-performance-test.md)

> [!NOTE]
> Yük testi eklentileri de oluşturabilirsiniz. Bkz. [Nasıl? Yük testi eklentisi oluşturma.](../test/how-to-create-a-load-test-plug-in.md)

## <a name="to-create-a-custom-web-performance-test-plug-in"></a>Özel web performansı testi eklentisi oluşturmak için

1. Web performans testi içeren bir web performansı ve yük testi projesi açın.

2. Bu **Çözüm Gezgini,** çözüme sağ tıklayın ve Ekle'yi **ve** ardından Yeni **giriş'i Project.**

3. Yeni bir Sınıf **Kitaplığı projesi** oluşturun.

   Yeni sınıf kitaplığı projesi Çözüm Gezgini **ve** yeni sınıf Kod Düzenleyicisi'nde **görünür.**

4. Yeni **Çözüm Gezgini** kitaplığında Başvurular **klasörüne** sağ tıklayın ve Başvuru Ekle'yi **seçin.**

   Başvuru **Ekle** iletişim kutusu görüntülenir.

5. **.NET sekmesini seçin,** ekranı aşağı kaydırın ve **Microsoft.VisualStudio.QualityTools.WebTestFramework öğesini seçin**

6. **Tamam'ı seçin.**

     **Microsoft.VisualStudio.QualityTools.WebTestFramework** başvurusu, **Çözüm Gezgini.** 

7. Bu **Çözüm Gezgini,** web performansı ve yük testi projesinin web performans testi eklentisini eklemek istediğiniz yük testini içeren en üst düğüme sağ tıklayın ve Başvuru **Ekle'yi seçin.**

8. Başvuru **Ekle iletişim kutusu görüntülenir.**

9. Projeler sekmesini **seçin** ve Sınıf **Kitaplığı'Project.**

10. **Tamam'ı seçin.**

11. Kod **Düzenleyicisi'nde** eklentinizin kodunu yazın. İlk olarak, 'den türeten yeni bir genel sınıf <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestPlugin> oluşturun.

12. Bir veya daha fazla olay işleyicisi içinde kod uygulama. Örnek uygulama için aşağıdaki Örnek bölümüne bakın.

    - <xref:Microsoft.VisualStudio.TestTools.WebTesting.PostWebTestRecordingEventArgs>

    - <xref:Microsoft.VisualStudio.TestTools.WebTesting.PostWebTestEventArgs>

    - <xref:Microsoft.VisualStudio.TestTools.WebTesting.PreRequestEventArgs>

    - <xref:Microsoft.VisualStudio.TestTools.WebTesting.PostRequestEventArgs>

    - <xref:Microsoft.VisualStudio.TestTools.WebTesting.PrePageEventArgs>

    - <xref:Microsoft.VisualStudio.TestTools.WebTesting.PostPageEventArgs>

    - <xref:Microsoft.VisualStudio.TestTools.WebTesting.PreTransactionEventArgs>

    - <xref:Microsoft.VisualStudio.TestTools.WebTesting.PostTransactionEventArgs>

13. Kodu yazdıktan sonra yeni projeyi derlemeniz gerekir.

14. Bir web performans testi açın.

15. Web performans testi eklentisini eklemek için araç çubuğunda **Web Testi Eklentisi Ekle'yi** seçin.

     **Web Testi Eklentisi Ekle** iletişim kutusu görüntülenir.

16. Eklenti **seçin altında web** performans testi eklenti sınıfınızı seçin.

17. Seçili **eklentinin Özellikler bölmesinde,** eklentinin çalışma zamanında kullanmak üzere başlangıç değerlerini ayarlayın.

    > [!NOTE]
    > Eklentilerinizin istediğiniz sayıda özelliği ortaya çıkarabilirsiniz; yalnızca bunları public, settable ve Integer, Boole veya String gibi bir temel türe göre ayarlayın. Daha sonra web performans testi eklenti özelliklerini değiştirmek için aşağıdaki Özellikler penceresi.

18. **Tamam'ı seçin.**

     Eklenti Web Testi Eklentileri **klasörüne** eklenir.

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

Aşağıdaki kod, test yinelemesini temsil eden öğesine bir öğe ekleyen özelleştirilmiş bir web <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestContext> performansı testi eklentisi oluşturur.

Web performans testini çalıştırdıktan sonra, bu eklentiyi kullanarak Web Performansı Sonuçları Görüntüleyicisi'nin Bağlam sekmesinde **TestIteratnionNumber** adlı eklenen **öğeyi görebilirsiniz.** 

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
- [Nasıl: İstek düzeyi eklenti oluşturma](../test/how-to-create-a-request-level-plug-in.md)
- [Web performans testi için özel ayıklama kuralı kodla](../test/code-a-custom-extraction-rule-for-a-web-performance-test.md)
- [Web performans testi için özel doğrulama kuralı kodla](../test/code-a-custom-validation-rule-for-a-web-performance-test.md)
- [Nasıl: Yük testi eklentisi oluşturma](../test/how-to-create-a-load-test-plug-in.md)
- [Kodlanmış web performans testi oluşturma](../test/generate-and-run-a-coded-web-performance-test.md)
