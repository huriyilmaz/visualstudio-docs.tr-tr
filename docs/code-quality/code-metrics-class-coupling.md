---
title: Kod ölçümleri-sınıf bağlantısı
ms.date: 1/8/2021
description: Visual Studio 'da kod ölçümleri için bir ders ölçüm sınıfı hakkında bilgi edinin.
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0853b807d3287eb584e76d9640ac98f930edb1a7
ms.sourcegitcommit: cc66c898ce82f9f1159bd505647f315792cac9fc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/10/2021
ms.locfileid: "109666815"
---
# <a name="code-metrics---class-coupling"></a>Kod ölçümleri-sınıf bağlantısı

Sınıf bağlantısı, ilk olarak [CK94](#ck94)tarafından tanımlanan nesneler (CBO) arasında bir ad ile geçer. Temel olarak sınıf bağlantısı, tek bir sınıfın kaç sınıf kullandığını gösteren bir ölçüdür. Yüksek bir sayı hatalı ve bu ölçümle genellikle düşük bir sayı vardır. Sınıf bağlantısı, yazılım hatasının doğru bir öngörüsi olacak şekilde gösterilmiştir ve son çalışmalar en verimli [S2010](#s2010)bir 9 üst sınır değeri olduğunu göstermiştir.

Sınıf bağlantısı, Microsoft belgelerine göre parametreler, yerel değişkenler, dönüş türleri, Yöntem çağrıları, genel veya şablon örneklemeleri, temel sınıflar, arabirim uygulamaları, dış türlerde tanımlı alanlar ve öznitelik dekorasyonu aracılığıyla benzersiz sınıflara yapılan eşlenenleri ölçer. İyi yazılım tasarımı, türlerin ve yöntemlerin yüksek düzeyde ve düşük bir eşlencede sahip olması gerektiğini belirler. Yüksek bağlantı, diğer türler üzerinde birçok bağımlılığı nedeniyle yeniden kullanılması zor olan bir tasarımın olduğunu gösterir. "

Eşlenme ve cohema kavramlarının kavramları net bir şekilde ilgilidir. Bu tartışmayı konu başlığı altında tutmak için, [KKLS2000](#kkls2000)adresinden kısa bir tanım vermek yerine, bir kaplama ile ilgili derinliğe karşılaşamayız:

"Modül cohema, bir modülün iç öğelerinin bire bir ' [YC79](#yc79)ne kadar sıkı bir şekilde bağlandığını veya ilgili olduğunu olarak, Yourdon ve Constantine tarafından tanıtılmıştı. Bir modülün tam olarak bir görevi (...]) temsil ediyorsa ve tüm öğeleri bu tek göreve katkıda bulunursa güçlü bir cohemi vardır. Bunlar, kod yerine tasarımın bir özniteliği olarak ve yeniden kullanılabilirlik, bakım ve değişiklik sağlamak için kullanılabilecek bir öznitelik olarak birlikte tanımlanır. "

## <a name="class-coupling-example"></a>Sınıf kuponu örneği

Şimdi sınıf bağlantısı ' na bakın. İlk olarak, yeni bir konsol uygulaması oluşturun ve içinde bazı özelliklere sahip kişi adlı yeni bir sınıf oluşturun ve ardından kod ölçümlerini hemen hesaplayın:

![Sınıf bağlantısı örnek 1](media/class-coupling-example-1.png)

Bu sınıf başka sınıf kullanmaz çünkü sınıf eşleştirmesi 0'dır. Şimdi personstuff adlı başka bir sınıf oluşturmak için Person örneği oluşturan ve özellik değerlerini ayaran bir yöntem kullanın. Kod ölçümlerini yeniden hesapla:

![Sınıf eşleştirme örneği 2](media/class-coupling-example-2.png)

Sınıf eşleştirme değerinin nasıl daha yüksek olduğunu görüyor musunuz? Ayrıca, kaç özellik ayarlansa da sınıf eşleştirme değerinin başka bir değere göre değil yalnızca 1'e kadar ilerler. Sınıf eşleştirmesi, ne kadar kullanılır olursa olsun bu ölçüm için her sınıfı yalnızca bir kez ölçür. Ayrıca, değerinin 1 olduğunu ancak oluşturucus unda 0 olduğunu `DoSomething()` `PersonStuff()` görüyor musunuz? Şu anda oluşturucuda başka bir sınıf kullanan bir kod yoktur.

Başka bir sınıf kullanılan oluşturucuya kod koysanız ne olur? Elde şunları elde ettiysiniz:

![Sınıf eşleştirme örneği 3](media/class-coupling-example-3.png)

Oluşturucu artık açıkça başka bir sınıf kullanan koda sahip ve sınıf eşleştirme ölçümü bu durumu gösteriyor. Yine için genel sınıf eşleştirmenin 1 olduğunu ve aynı zamanda 1 olduğunu görebilir ve bunu kullanan iç kodunuz ne kadar olursa olsun yalnızca bir dış sınıfın `PersonStuff()` `DoSomething()` kullan olduğunu gösterir.

Ardından, başka bir yeni sınıf oluşturun. Bu sınıfa bir ad girin ve içinde bazı özellikler oluşturun:

![Sınıf eşleştirme örneği - yeni sınıf ekleme](media/class-coupling-example-add-new-class.png)

Şimdi sınıfındaki yöntemimizde `DoSomething()` sınıfını kullanın `PersonStuff` ve kod ölçümlerini yeniden hesaplayın:

![Sınıf eşleştirme örneği 4](media/class-coupling-example-4.png)

Gördüğünüz gibi PersonStuff sınıfı için sınıf eşleştirmesi 2'ye kadar gider ve sınıfa detaya gidersiniz, yöntemin içinde en çok eşleşmeye sahip olduğunu, ancak oluşturucu hala 1 sınıf `DoSomething()` tüketir.  Bu ölçümleri kullanarak, belirli bir sınıf için genel en büyük sayıyı görebilir ve her üye için ayrıntıların ayrıntılarına gidebilirsiniz.

## <a name="the-magic-number"></a>Sihirli sayı

Döngüsel karmaşıklıkta olduğu gibi, tüm kuruluşlara uyan bir sınır yoktur. Ancak [S2010](#s2010) , 9 sınırının en iyi olduğunu belirtir:

"Bu nedenle, [...] eşik değerlerini göz önünde bulunduruyoruz en etkili şekilde. Bu eşik değerleri (tek bir üye için), BHA = 9 [...]. " (vurgu eklendi)

## <a name="code-analysis"></a>Kod Çözümleme

Kod Analizi bir bakım kuralları kategorisi içerir. Daha fazla bilgi için bkz. [Bakımlamama kuralları](/dotnet/fundamentals/code-analysis/quality-rules/maintainability-warnings). Eski Kod analizini kullanırken, genişletilmiş tasarım kılavuz kuralı kümesi bir bakım alanı içerir:

![Sınıf eşlenmiş tasarım kılavuzu kuralları](media/class-coupling-extended-design-guideline-rules.png)

Bakım alanının içinde, sınıf bağlantısı için bir kuraldır:

![Sınıf bağlantısı](media/class-coupling-maintainability-area-rules.png)

Bu kural, bir sınıf bağlantısı aşırı olduğunda bir uyarı verir. Daha fazla bilgi için bkz. [CA1506: aşırı sınıf bağlantısından kaçının](/dotnet/fundamentals/code-analysis/quality-rules/ca1506).

## <a name="citations"></a>Alıntı

### <a name="ck94"></a>CK94

Oyduklik, S. R. & Kemerer, C. F. (1994). Nesne Odaklı Tasarım için Ölçüm Paketi (Yazılım Mühendisliğinde IEEE İşlemleri, Vol. 20, Hayır. 6). 14 Mayıs 2011, University of Pittsburgh web sitesinden alındı: [http://www.pitt.edu/~ckemerer/CK%20research%20papers/MetricForOOD_ChidamberKemerer94.pdf](http://www.pitt.edu/~ckemerer/CK%20research%20papers/MetricForOOD_ChidamberKemerer94.pdf)

### <a name="kkls2000"></a>KKLS2000

Kabaili, H., Keller, R., Saintman, F., and Saint-Denis, G. (2000). Sınıf Uyumu Yeniden Değerlendirildi: Endüstriyel Sistemlerle ilgili Ampirik Bir Çalışma (Object-Oriented Yazılım Mühendisliğinde Nicel Yaklaşımlar Atölyesinde Proceedings of the Workshop). 20 Mayıs 2011' tarihindeKiré de Montréal web sitesinden alındı [http://www.iro.umontreal.ca/~sahraouh/qaoose/papers/Kabaili.pdf](http://www.iro.umontreal.ca/~sahraouh/qaoose/papers/Kabaili.pdf)

### <a name="sk2003"></a>SK2003

Subramanyam, R. & Ancak, M. S. (2003). Object-Oriented Tasarım Karmaşıklığı için CK Ölçümlerinin Ampirik Analizi: Yazılım Hatalarının Etkileri (Yazılım Mühendisliğinde IEEE İşlemleri, Vol. 29, Hayır. 4). 14 Mayıs 2011, University of University of University Of Sonay web sitesinden alındı [http://moosehead.cis.umassd.edu/cis580/readings/OO_Design_Complexity_Metrics.pdf](http://moosehead.cis.umassd.edu/cis580/readings/OO_Design_Complexity_Metrics.pdf)

### <a name="s2010"></a>S2010

Shatnawi, R. (2010). Open-Source Sistemlerinde Object-Oriented Ölçümlerinin Kabul Edilebilir Risk Düzeylerinin Nicel Bir Araştırma (Yazılım Mühendisliğinde IEEE İşlemleri, Vol. 36, Hayır. 2).

### <a name="yc79"></a>YC79

Edward Yourdon ve Angeles L. Constantine. Yapılandırılmış Tasarım. Prentice Hall, Englewood Cliffs, N.J., 1979.