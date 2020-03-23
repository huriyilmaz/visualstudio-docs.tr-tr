---
title: Web performans testleri için İstek Düzeyi Eklentisi Oluşturma
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- request-level plug-in, creating
- Web performance tests, requests
ms.assetid: d0b5b23c-7e94-4637-be6c-2620a5442d46
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b6e57f92a3f45983321a866f3524974ea99dba82
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75589168"
---
# <a name="how-to-create-a-request-level-plug-in"></a>Nasıl yapilir: İstek düzeyi eklentisi oluşturma

*İstekler,* web performans testlerini oluşturan bildirimdeyimleridir. Web performans testi eklentileri, web performans testinizdeki ana bildirimekstifadelerin dışında kodu yalıtmanızı ve yeniden kullanmanıza olanak tanır. Eklentiler oluşturabilir ve bunları tek bir isteğe ve bunu içeren web performans testine ekleyebilirsiniz. Özelleştirilmiş *bir istek eklentisi,* web performans testinde belirli bir istek çalıştırılırken kod aramanız için bir yol sunar.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Her web performans testi isteği eklentisinde Bir PreRequest yöntemi ve PostRequest yöntemi vardır. Belirli bir http isteğine bir istek eklentisi iliştirdikten sonra, Istek yayınlanmadan önce Ön İstek olayı ateşlenir ve yanıt alındıktan sonra PostRequest ateşlenir.

<xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequestPlugin> Taban sınıftan kendi sınıfınızı türeterek özelleştirilmiş bir web performans testi isteği eklentisi oluşturabilirsiniz.

Kaydettiğiniz web performans testleri ile özelleştirilmiş web performans testi isteği eklentilerini kullanabilirsiniz. Özelleştirilmiş web performans testi isteği eklentileri, web performans testleriniz üzerinde daha fazla denetim düzeyielde etmek için en az miktarda kod yazmanıza olanak tanır. Ancak, kodlanmış web performans testleri ile de kullanabilirsiniz. Bkz. [Kodlanmış bir web performans testi oluşturun ve çalıştırın.](../test/generate-and-run-a-coded-web-performance-test.md)

## <a name="to-create-a-request-level-plug-in"></a>İstek düzeyi eklentisi oluşturmak için

1. **Çözüm Gezgini'nde,** çözüme sağ tıklayın, **Ekle'yi** seçin ve ardından **Yeni Proje'yi**seçin.

2. Yeni bir **Sınıf Kitaplığı** projesi oluşturun.

3. **Çözüm Gezgini'nde,** yeni sınıf kitaplığındaki **Başvurular** klasörüne sağ tıklayın ve **Başvuru Ekle'yi**seçin.

     **Başvuru Ekle** iletişim kutusu görüntülenir.

4. **.NET** sekmesini seçin, aşağı kaydırın, **Microsoft.VisualStudio.QualityTools.WebTestFramework'i** seçin ve ardından **Tamam'ı** seçin

     **Microsoft.VisualStudio.QualityTools.WebTestFramework** başvurusu **Solution Explorer'daki** **Başvuru** klasörüne eklenir.

5. **Çözüm Gezgini'nde,** web performans testi nin üst düğümve web performans testi isteği test eklentisini eklemek istediğiniz yük testi içeren yük testi projesinin üst düğüme sağ tıklayın. **Referans Ekle'yi**seçin.

     **Başvuru Ekle iletişim kutusu görüntülenir.**

6. **Projeler** sekmesini seçin, **Sınıf Kitaplığı Projesi'ni** seçin ve ardından **Tamam'ı** seçin.

7. Kod **Düzenleyicisi'nde**eklentinizin kodunu yazın. İlk olarak, türetilmiştir yeni bir <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequestPlugin>ortak sınıf oluşturun.

8. Ve <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequestPlugin.PostRequest*> olay işleyicilerinden <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequestPlugin.PreRequest*> birinin veya her ikisinin içinde kod uygulayın. Örnek uygulama için aşağıdaki Örnek bölümüne bakın.

9. Kodu yazdıktan sonra yeni projeyi oluşturun.

10. İstek eklentisini eklemek istediğiniz web performans testini açın.

11. İstek eklentisini eklemek istediğiniz isteğe sağ tıklayın ve **İstek Eklentisi Ekle'yi**seçin.

     **Web Test İsteği** Ekle Eklentisi iletişim kutusu görüntülenir.

12. **Bir eklenti seç'in**altında, yeni eklentinizi seçin.

13. **Seçili eklenti** bölmesinin Özellikleri'nde, eklentinin çalışma zamanında kullanması için ilk değerleri ayarlayın.

    > [!NOTE]
    > Eklentilerinizden istediğiniz kadar özellik ortaya çıkarabilirsiniz; onları herkese açık, ayarlanabilir ve Tamsayı, Boolean veya String gibi bir taban türüne ait hale getirin. Özellikler penceresini kullanarak web performans testi eklentiözelliklerini daha sonra değiştirebilirsiniz.

14. **Tamam'ı**seçin.

     Eklenti, HTTP isteğinin alt klasörü olan **İstek Eklentileri** klasörüne eklenir.

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

İki iletişim kutusu görüntüleyen özelleştirilmiş bir web performans testi eklentisi oluşturmak için aşağıdaki kodu kullanabilirsiniz. Bir iletişim kutusu, istek eklentisini iliştirdiğiniz istekle ilişkili URL'yi görüntüler. İkinci iletişim kutusu aracının bilgisayar adını görüntüler.

> [!NOTE]
> Aşağıdaki kod, System.Windows.Forms'a bir başvuru eklemenizi gerektirir.

```csharp
using System;
using System.Collections.Generic;
using System.Windows.Forms;
using Microsoft.VisualStudio.TestTools.WebTesting;

namespace RequestPluginNamespace
{
    public class MyWebRequestPlugin : WebTestRequestPlugin
    {
        public override void PostRequest(object sender, PostRequestEventArgs e)
        {
            MessageBox.Show(e.WebTest.Context.AgentName);
        }
        public override void PreRequest(object sender, PreRequestEventArgs e)
        {
            MessageBox.Show(e.Request.Url);
        }
    }
}
```

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequestPlugin>
- [Yük testleri için özel kod ve eklentiler oluşturma](../test/create-custom-code-and-plug-ins-for-load-tests.md)
- [Web performans testi için özel bir çıkarma kuralı kodlama](../test/code-a-custom-extraction-rule-for-a-web-performance-test.md)
- [Web performans testi için özel doğrulama kuralını kodlama](../test/code-a-custom-validation-rule-for-a-web-performance-test.md)
- [Nasıl yapılsın: Yük testi eklentisi oluşturma](../test/how-to-create-a-load-test-plug-in.md)
- [Kodlanmış web performans testi oluşturma](../test/generate-and-run-a-coded-web-performance-test.md)
