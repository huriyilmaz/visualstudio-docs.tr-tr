---
title: İstek düzeyinde eklenti oluşturma (web performans testleri)
description: Tek bir istekte web performans testi eklentilerini kullanarak kodu web performans testinde ana bildirim deyimleri dışında nasıl yeniden kullanmanıza olanak olduğunu öğrenin.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- request-level plug-in, creating
- Web performance tests, requests
ms.assetid: d0b5b23c-7e94-4637-be6c-2620a5442d46
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.openlocfilehash: a50d16a98f6a504e845fcc54ae750ba65e58fc6a
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122047484"
---
# <a name="how-to-create-a-request-level-plug-in"></a>Nasıl: İstek düzeyi eklenti oluşturma

*İstekler,* web performans testlerini oluşturan bildirim deyimleridir. Web performans testi eklentileri, web performans testinde kodu ana bildirim deyimleri dışında yalıtmanıza ve yeniden kullanmanıza olanak sağlar. Eklentileri oluşturabilir ve bunları tek bir i isteğin yanı sıra bu eklentiyi içeren web performans testlerine eklemek için kullanabilirsiniz. Özelleştirilmiş istek  *eklentisi, belirli bir* istek web performans testinde çalıştırıldıklarında kodu çağırmanın bir yolunu sunar.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Her web performansı test isteği eklentisinin bir PreRequest yöntemi ve bir PostRequest yöntemi vardır. Belirli bir http isteğine istek eklentisini iliştirdikten sonra, istek yayından önce PreRequest olayı ve yanıt alındıktan sonra PostRequest başlatıldı.

Kendi sınıfınızı temel sınıftan türeterek özelleştirilmiş bir web performansı test isteği eklentisi <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequestPlugin> oluşturabilirsiniz.

Kaydettiğiniz web performans testleri ile özelleştirilmiş web performansı test isteği eklentilerini kullanabilirsiniz. Özelleştirilmiş web performansı test isteği eklentileri, web performans testleri üzerinde daha yüksek bir denetim düzeyi elde etmek için minimum miktarda kod yazmanızı sağlar. Ancak, bunları kodlu web performans testleriyle de kullanabilirsiniz. Bkz. [Kodlu web performans testi oluşturma ve çalıştırma.](../test/generate-and-run-a-coded-web-performance-test.md)

## <a name="to-create-a-request-level-plug-in"></a>İstek düzeyi eklenti oluşturmak için

1. Bu **Çözüm Gezgini,** çözüme sağ tıklayın, Ekle'yi **ve** ardından Yeni **giriş'Project.**

2. Yeni bir Sınıf **Kitaplığı projesi** oluşturun.

3. Yeni **Çözüm Gezgini** kitaplığında Başvurular **klasörüne** sağ tıklayın ve Başvuru Ekle'yi **seçin.**

     Başvuru **Ekle** iletişim kutusu görüntülenir.

4. **.NET sekmesini seçin,** aşağı kaydırın, **Microsoft.VisualStudio.QualityTools.WebTestFramework** öğesini seçin ve ardından Tamam'ı **seçin.**

     **Microsoft.VisualStudio.QualityTools.WebTestFramework** başvurusu, **Çözüm Gezgini.** 

5. Bu **Çözüm Gezgini,** web performansı ve yük testi projesinin web performansı test eklentisini eklemek istediğiniz yük testini içeren en üst düğüme sağ tıklayın. Başvuru **Ekle'yi seçin.**

     Başvuru **Ekle iletişim kutusu görüntülenir.**

6. Projeler sekmesini **seçin,** Sınıf Kitaplığı **kitaplığını seçin Project** tamam'ı **seçin.**

7. Kod **Düzenleyicisi'nde** eklentinizin kodunu yazın. İlk olarak, 'den türeten yeni bir genel sınıf <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequestPlugin> oluşturun.

8. Ve olay işleyicilerinden birinin veya her <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequestPlugin.PreRequest*> ikisinin <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequestPlugin.PostRequest*> içinde kod uygulama. Örnek uygulama için aşağıdaki Örnek bölümüne bakın.

9. Kodu yazdıktan sonra yeni projeyi derlemeniz gerekir.

10. İstek eklentisini eklemek istediğiniz web performans testini açın.

11. İstek eklentiyi eklemek istediğiniz itene sağ tıklayın ve İstek Eklentisi **Ekle'yi seçin.**

     **Web Testi İsteği Eklentisi Ekle** iletişim kutusu görüntülenir.

12. Eklenti **seçin altında yeni** eklentinizi seçin.

13. Seçili **eklentinin Özellikler bölmesinde,** eklentinin çalışma zamanında kullanmak üzere başlangıç değerlerini ayarlayın.

    > [!NOTE]
    > Eklentilerinizin istediğiniz sayıda özelliği ortaya çıkarabilirsiniz; yalnızca bunları public, settable ve Integer, Boole veya String gibi bir temel türe göre ayarlayın. Daha sonra web performans testi eklenti özelliklerini daha sonra aşağıdaki Özellikler penceresi.

14. **Tamam'ı seçin.**

     Eklenti, HTTP isteğinin alt **klasörü** olan İstek Eklentileri klasörüne eklenir.

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

İki iletişim kutusu görüntüleyen özelleştirilmiş bir web performansı testi eklentisi oluşturmak için aşağıdaki kodu kullanabilirsiniz. Bir iletişim kutusu, istek eklentisini iliştirmek istediğiniz istekle ilişkili URL'yi görüntüler. İkinci iletişim kutusu, aracı için bilgisayar adını görüntüler.

> [!NOTE]
> Aşağıdaki kod, Sistem'e bir başvuru eklemenizi gerektirir. Windows. Forms.

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
- [Web performans testi için özel ayıklama kuralı kodla](../test/code-a-custom-extraction-rule-for-a-web-performance-test.md)
- [Web performans testi için özel doğrulama kuralı kodla](../test/code-a-custom-validation-rule-for-a-web-performance-test.md)
- [Nasıl: Yük testi eklentisi oluşturma](../test/how-to-create-a-load-test-plug-in.md)
- [Kodlanmış web performans testi oluşturma](../test/generate-and-run-a-coded-web-performance-test.md)
