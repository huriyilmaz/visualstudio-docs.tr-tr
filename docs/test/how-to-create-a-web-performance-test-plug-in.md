---
title: Web Performans Testi Eklentisi Oluşturma
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75589116"
---
# <a name="how-to-create-a-web-performance-test-plug-in"></a>Nasıl yapilir: Web performans testi eklentisi oluşturma

Web performans testleri eklentileri, web performans testinizdeki ana bildirimekst ifadelerinin dışında kodu yalıtmanızı ve yeniden kullanmanıza olanak tanır. Özelleştirilmiş bir web performans testi eklentisi, web performans testi çalıştırılırken bazı kodları aramanın bir yolunu sunar. Web performans testi eklentisi, her test yinelemesi için bir kez çalıştırılır. Ayrıca, test eklentisinde Ön İstek veya PostRequest yöntemlerini geçersiz kılarsanız, bu istek eklentileri sırasıyla her istekten önce veya sonra çalışır.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

<xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestPlugin> Taban sınıftan kendi sınıfınızı türeterek özelleştirilmiş bir web performans testi eklentisi oluşturabilirsiniz.

Kaydettiğiniz web performans testleri ile özelleştirilmiş web performans testi eklentileri kullanabilirsiniz, bu da web performans testleriniz üzerinde daha fazla denetim düzeyi elde etmek için en az miktarda kod yazmanıza olanak tanır. Ancak, kodlanmış web performans testleri ile de kullanabilirsiniz. Daha fazla bilgi için [bkz.](../test/generate-and-run-a-coded-web-performance-test.md)

> [!NOTE]
> Ayrıca yük testi eklentileri oluşturabilirsiniz. [Bkz. Nasıl: Yük testi eklentisi oluşturun.](../test/how-to-create-a-load-test-plug-in.md)

## <a name="to-create-a-custom-web-performance-test-plug-in"></a>Özel bir web performans testi eklentisi oluşturmak için

1. Web performans testi içeren bir web performansı ve yükleme testi projesi açın.

2. **Çözüm Gezgini'nde,** çözüme sağ tıklayın ve **Ekle'yi** seçin ve ardından **Yeni Proje'yi**seçin.

3. Yeni bir **Sınıf Kitaplığı** projesi oluşturun.

   Yeni sınıf kitaplık projesi **Solution Explorer'a** eklenir ve kod **düzenleyicisinde**yeni sınıf görüntülenir.

4. **Çözüm Gezgini'nde,** yeni sınıf kitaplığındaki **Başvurular** klasörüne sağ tıklayın ve **Başvuru Ekle'yi**seçin.

   **Başvuru Ekle** iletişim kutusu görüntülenir.

5. **.NET** sekmesini seçin, aşağı kaydırın ve **Microsoft.VisualStudio.QualityTools.WebTestFramework'i** seçin

6. **Tamam'ı**seçin.

     **Microsoft.VisualStudio.QualityTools.WebTestFramework** başvurusu **Solution Explorer'daki** **Başvuru** klasörüne eklenir.

7. **Çözüm Gezgini'nde,** web performans testi eklentisini eklemek istediğiniz yük testive yükleme testi projesinin üst düğümüne sağ tıklayın ve **Referans Ekle'yi**seçin.

8. **Başvuru Ekle iletişim kutusu görüntülenir.**

9. **Projeler** sekmesini seçin ve **Sınıf Kitaplığı Projesi'ni**seçin.

10. **Tamam'ı**seçin.

11. Kod **Düzenleyicisi'nde**eklentinizin kodunu yazın. İlk olarak, türetilmiştir yeni bir <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestPlugin>ortak sınıf oluşturun.

12. Olay işleyicilerinden biri veya daha fazlası içinde kod uygulayın. Örnek uygulama için aşağıdaki Örnek bölümüne bakın.

    - <xref:Microsoft.VisualStudio.TestTools.WebTesting.PostWebTestRecordingEventArgs>

    - <xref:Microsoft.VisualStudio.TestTools.WebTesting.PostWebTestEventArgs>

    - <xref:Microsoft.VisualStudio.TestTools.WebTesting.PreRequestEventArgs>

    - <xref:Microsoft.VisualStudio.TestTools.WebTesting.PostRequestEventArgs>

    - <xref:Microsoft.VisualStudio.TestTools.WebTesting.PrePageEventArgs>

    - <xref:Microsoft.VisualStudio.TestTools.WebTesting.PostPageEventArgs>

    - <xref:Microsoft.VisualStudio.TestTools.WebTesting.PreTransactionEventArgs>

    - <xref:Microsoft.VisualStudio.TestTools.WebTesting.PostTransactionEventArgs>

13. Kodu yazdıktan sonra yeni projeyi oluşturun.

14. Web performans testi açın.

15. Web performans testi eklentisini eklemek için araç çubuğuna **Web Testi Eklentisi Ekle'yi** seçin.

     **Web Test Eklentisi Eklentisi** iletişim kutusu görüntülenir.

16. **Eklenti seç'in**altında, web performans testi eklentisi sınıfınızı seçin.

17. **Seçili eklenti** bölmesinin Özellikleri'nde, eklentinin çalışma zamanında kullanması için ilk değerleri ayarlayın.

    > [!NOTE]
    > Eklentilerinizden istediğiniz kadar özellik ortaya çıkarabilirsiniz; onları herkese açık, ayarlanabilir ve Tamsayı, Boolean veya String gibi bir taban türüne ait hale getirin. Özellikler penceresini kullanarak web performans testi eklentiözelliklerini daha sonra değiştirebilirsiniz.

18. **Tamam'ı**seçin.

     Eklenti, **Web Test Eklentileri** klasörüne eklenir.

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

Aşağıdaki kod, test yinelemesini temsil <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestContext> eden öğeye bir öğe ekleyen özelleştirilmiş bir web performans testi eklentisi oluşturur.

Web performans testini çalıştırdıktan sonra, bu eklentiyi kullanarak **Web Performans Sonuçları Görüntüleyici'de** **Bağlam** sekmesinde **TestIteratnionNumber** adlı eklenen öğeyi görebilirsiniz.

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
- [Nasıl yapilir: İstek düzeyi eklentisi oluşturma](../test/how-to-create-a-request-level-plug-in.md)
- [Web performans testi için özel bir çıkarma kuralı kodlama](../test/code-a-custom-extraction-rule-for-a-web-performance-test.md)
- [Web performans testi için özel doğrulama kuralını kodlama](../test/code-a-custom-validation-rule-for-a-web-performance-test.md)
- [Nasıl yapılsın: Yük testi eklentisi oluşturma](../test/how-to-create-a-load-test-plug-in.md)
- [Kodlanmış web performans testi oluşturma](../test/generate-and-run-a-coded-web-performance-test.md)
