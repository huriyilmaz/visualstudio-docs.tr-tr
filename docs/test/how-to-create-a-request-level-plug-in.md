---
title: Web performans testleri için Istek düzeyi eklentisi oluşturma
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- request-level plug-in, creating
- Web performance tests, requests
ms.assetid: d0b5b23c-7e94-4637-be6c-2620a5442d46
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ce0a8030253e69b35deda379cffcf7475dc8bb62
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72653632"
---
# <a name="how-to-create-a-request-level-plug-in"></a>Nasıl yapılır: istek düzeyi eklentisi oluşturma

*İstekler* , Web performans testlerini oluşturan bildirime dayalı deyimlerdir. Web performans testi eklentileri, Web performans testinizde ana bildirim deyimleri dışında kodu yalıtmanızı ve yeniden kullanmanıza olanak tanır. Eklentiler oluşturabilir ve bunları içeren Web performans testine ve tek bir isteğe da ekleyebilirsiniz. Özelleştirilmiş bir *istek eklentisi* bir Web performans testinde belirli bir istek çalıştırıldığı için kodu çağırmak için bir yol sunar.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Her Web performansı test isteği eklentisinin bir Önkoşulcu yöntemi ve bir PostRequest yöntemi vardır. Belirli bir HTTP isteğine bir istek eklentisi iliştirdikten sonra, istek verildikten önce ön koşul olayı tetiklenir ve yanıt alındıktan sonra PostRequest tetiklenir.

@No__t_0 temel sınıfından kendi sınıfınızı türeterek, özelleştirilmiş bir Web başarım testi istek eklentisi oluşturabilirsiniz.

Özelleştirilmiş Web performansı test isteği eklentilerini, kaydettiğiniz Web performans testleri ile birlikte kullanabilirsiniz. Özelleştirilmiş Web performans testi istek eklentileri, Web performans testleriniz üzerinde daha yüksek düzeyde denetim elde etmek için en az miktarda kod yazmanızı sağlar. Ancak, bunları kodlanmış Web performans testleri ile de kullanabilirsiniz. Bkz. [kodlanmış Web performans testi oluşturma ve çalıştırma](../test/generate-and-run-a-coded-web-performance-test.md).

## <a name="to-create-a-request-level-plug-in"></a>İstek düzeyi eklentisi oluşturmak için

1. **Çözüm Gezgini**, çözüme sağ tıklayın, **Ekle** ' yi ve ardından **Yeni proje**' yi seçin.

2. Yeni bir **sınıf kitaplığı** projesi oluşturun.

3. **Çözüm Gezgini**' de, yeni sınıf kitaplığındaki **Başvurular** klasörüne sağ tıklayın ve **Başvuru Ekle**' yi seçin.

     **Başvuru Ekle** iletişim kutusu görüntülenir.

4. **.Net** sekmesini seçin, aşağı kaydırın, **Microsoft. VisualStudio. QualityTools. WebTestFramework** öğesini seçin ve ardından **Tamam** ' ı seçin.

     **Microsoft. VisualStudio. QualityTools. WebTestFramework** başvurusu **Çözüm Gezgini**içindeki **başvuru** klasörüne eklenir.

5. **Çözüm Gezgini**' de, Web performansı test isteği test eklentisini eklemek istediğiniz yük testini içeren Web performansının ve yük testi projesinin en üst düğümüne sağ tıklayın. **Başvuru Ekle**' yi seçin.

     **Başvuru Ekle iletişim kutusu görüntülenir**.

6. **Projeler** sekmesini seçin, **Sınıf Kitaplığı projesini** seçin ve ardından **Tamam** ' ı seçin.

7. **Kod düzenleyicisinde**, eklentinin kodunu yazın. İlk olarak, <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequestPlugin> türetilen yeni bir ortak sınıf oluşturun.

8. @No__t_0 ve <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequestPlugin.PostRequest*> olay işleyicilerinin bir veya her ikisinin içinde kod uygulayın. Örnek bir uygulama için aşağıdaki örnek bölümüne bakın.

9. Kodu yazdıktan sonra yeni projeyi derleyin.

10. İstek eklentisini eklemek istediğiniz Web performans testini açın.

11. İstek eklentisini eklemek istediğiniz isteğe sağ tıklayın ve **Istek eklentisi Ekle**' yi seçin.

     **Web test Isteği eklentisi Ekle** iletişim kutusu görüntülenir.

12. **Eklenti seçin**altında yeni eklentiyi seçin.

13. **Seçili eklenti bölmesinin Özellikler** bölümünde, çalışma zamanında kullanılacak eklentinin başlangıç değerlerini ayarlayın.

    > [!NOTE]
    > Eklentilerinizi istediğiniz kadar çok özelliği kullanıma sunabilirsiniz. bunları ortak, ayarlanabilir ve tamsayı, Boole veya dize gibi bir temel tür yapmanız yeterlidir. Web performans testi eklentisi özelliklerini daha sonra Özellikler penceresi kullanarak da değiştirebilirsiniz.

14. **Tamam ' ı**seçin.

     Eklenti, HTTP isteğinin bir alt klasörü olan **istek** eklentileri klasörüne eklenir.

    > [!WARNING]
    > Eklentiyi kullanan bir Web performans testi veya yük testi çalıştırdığınızda aşağıdakine benzer bir hata alabilirsiniz:
    >
    > **İstek başarısız: \<plug > olayında özel durum: dosya veya derleme ' \< "eklenti adı". dll dosyası >, sürüm = \<n. n. n. n >, kültür = neutral, PublicKeyToken = null ' veya bağımlılıklarından biri yüklenemedi. Sistem belirtilen dosyayı bulamıyor.**
    >
    > Bu, eklentilerinizin herhangi birine kod değişikliği yaptığınızda ve yeni bir DLL sürümü **(sürüm = 0.0.0.0)** oluşturuyorsanız, ancak eklentinin özgün eklenti sürümüne başvurmaya devam ediyorsa oluşur. Bu sorunu düzeltmek için aşağıdaki adımları izleyin:
    >
    > 1. Web performansı ve yük testi projenizde, başvurularda bir uyarı görürsünüz. Başvuruyu eklenti DLL 'nize kaldırın ve yeniden ekleyin.
    > 2. Testinizden veya uygun konumdan eklentiyi kaldırın ve ardından yeniden ekleyin.

## <a name="example"></a>Örnek

İki iletişim kutusu gösteren özelleştirilmiş bir Web başarım testi eklentisi oluşturmak için aşağıdaki kodu kullanabilirsiniz. Bir iletişim kutusu, istek eklentisini eklediğiniz istekle ilişkili URL 'YI görüntüler. İkinci iletişim kutusu, aracının bilgisayar adını görüntüler.

> [!NOTE]
> Aşağıdaki kod, System. Windows. Forms 'a bir başvuru eklemenizi gerektirir.

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
- [Web performans testi için özel bir ayıklama kuralı kodlayın](../test/code-a-custom-extraction-rule-for-a-web-performance-test.md)
- [Web performans testi için özel doğrulama kuralı kodu oluşturma](../test/code-a-custom-validation-rule-for-a-web-performance-test.md)
- [Nasıl yapılır: yük testi eklentisi oluşturma](../test/how-to-create-a-load-test-plug-in.md)
- [Kodlanmış Web performans testi oluşturma ve çalıştırma](../test/generate-and-run-a-coded-web-performance-test.md)