---
title: Kod ölçümleri-sınıf bağlantısı
ms.date: 1/8/2021
description: Visual Studio 'da kod ölçümleri için bir ders ölçüm sınıfı hakkında bilgi edinin.
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: db1308843cb3c4fe8fb0a4aa32300e545e5e3a7c
ms.sourcegitcommit: b1f7e7d7a0550d5c6f46adff3bddd44bc1d6ee1c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/11/2021
ms.locfileid: "98069645"
---
# <a name="code-metrics---class-coupling"></a>Kod ölçümleri-sınıf bağlantısı

Sınıf bağlantısı, ilk olarak [CK94](#ck94)tarafından tanımlanan nesneler (CBO) arasında bir ad ile geçer. Temel olarak sınıf bağlantısı, tek bir sınıfın kaç sınıf kullandığını gösteren bir ölçüdür. Yüksek bir sayı hatalı ve bu ölçümle genellikle düşük bir sayı vardır. Sınıf bağlantısı, yazılım hatasının doğru bir öngörüsi olacak şekilde gösterilmiştir ve son çalışmalar en verimli [S2010](#s2010)bir 9 üst sınır değeri olduğunu göstermiştir.

Sınıf bağlantısı, Microsoft belgelerine göre parametreler, yerel değişkenler, dönüş türleri, Yöntem çağrıları, genel veya şablon örneklemeleri, temel sınıflar, arabirim uygulamaları, dış türlerde tanımlı alanlar ve öznitelik dekorasyonu aracılığıyla benzersiz sınıflara yapılan eşlenenleri ölçer. İyi yazılım tasarımı, türlerin ve yöntemlerin yüksek düzeyde ve düşük bir eşlencede sahip olması gerektiğini belirler. Yüksek bağlantı, diğer türler üzerinde birçok bağımlılığı nedeniyle yeniden kullanılması zor olan bir tasarımın olduğunu gösterir. "

Eşlenme ve cohema kavramlarının kavramları net bir şekilde ilgilidir. Bu tartışmayı konu başlığı altında tutmak için, [KKLS2000](#kkls2000)adresinden kısa bir tanım vermek yerine, bir kaplama ile ilgili derinliğe karşılaşamayız:

"Modül cohema, bir modülün iç öğelerinin bire bir ' [YC79](#yc79)ne kadar sıkı bir şekilde bağlandığını veya ilgili olduğunu olarak, Yourdon ve Constantine tarafından tanıtılmıştı. Bir modülün tam olarak bir görevi (...]) temsil ediyorsa ve tüm öğeleri bu tek göreve katkıda bulunursa güçlü bir cohemi vardır. Bunlar, kod yerine tasarımın bir özniteliği olarak ve yeniden kullanılabilirlik, bakım ve değişiklik sağlamak için kullanılabilecek bir öznitelik olarak birlikte tanımlanır. "

## <a name="class-coupling-example"></a>Sınıf kuponu örneği

Şimdi sınıf bağlantısı ' na bakın. İlk olarak, yeni bir konsol uygulaması oluşturun ve içinde bazı özelliklere sahip kişi adlı yeni bir sınıf oluşturun ve ardından kod ölçümlerini hemen hesaplayın:

![Sınıf bağlantısı örnek 1](media/class-coupling-example-1.png)

Bu sınıf başka bir sınıf kullanmıyorsa, bu sınıf Şimdi, bir kişi örneği oluşturan ve özellik değerlerini ayarlayan bir yöntemle Personça adlı başka bir sınıf oluşturun. Kod ölçümlerini yeniden hesaplayın:

![Sınıf bağlantısı örneği 2](media/class-coupling-example-2.png)

Sınıf bağlantısı nasıl çalışır? Aynı zamanda, kaç özellik ayarlandığına bakılmaksızın, bir sınıf bağlantısı değeri başka bir değer tarafından değil, yalnızca 1 ' den yukarı gider. Sınıf bağlantısı, ne kadar kullanıldıklarından bağımsız olarak, her sınıfı bu ölçüm için yalnızca bir kez ölçer. Buna ek olarak, `DoSomething()` 1, ancak oluşturucusunun `PersonStuff()` değeri için 0 olduğunu görebilirsiniz. Şu anda oluşturucuda başka bir sınıf kullanan bir kod yoktur.

Kodu başka bir sınıf kullanan oluşturucuya yerleştirirseniz ne yapabilirsiniz? Aldığınız özellikler şunlardır:

![Sınıf bağlantısı örnek 3](media/class-coupling-example-3.png)

Artık oluşturucunun başka bir sınıfı kullanan kodu açık bir şekilde ve bu olguyu ölçüsüne gösterdiği. Ayrıca, için genel olan tüm sınıf bağlantısı ' nı görebilir `PersonStuff()` ve `DoSomething()` yalnızca bir dış sınıfın, ne kadar dahili kod kullandığını anlamak için de 1 olduğunu gösterir.

Sonra, başka bir yeni sınıf oluşturun. Bu sınıfa bir ad verin ve içinde bazı özellikler oluşturun:

![Sınıf bağlantısı örneği-yeni sınıf Ekle](media/class-coupling-example-add-new-class.png)

Şimdi sınıf `DoSomething()` içindeki yöntemizdeki sınıfı tükettin `PersonStuff` ve kod ölçümlerini yeniden hesaplayın:

![Sınıf bağlantısı örnek 4](media/class-coupling-example-4.png)

Gördüğünüz gibi, Personça sınıfı için bir sınıf bağlantısı 2 ' ye kadar gider ve sınıfa göz atadıysanız, `DoSomething()` yöntemin içinde en çok eşlenmeye sahip olduğunu ancak oluşturucunun yalnızca 1 sınıf tükettiğini görebilirsiniz.  Bu ölçümleri kullanarak, belirli bir sınıf için genel en büyük sayıyı görebilir ve her üye için ayrıntıların ayrıntılarına gidebilirsiniz.

## <a name="the-magic-number"></a>Sihirli sayı

Döngüsel karmaşıklıkta olduğu gibi, tüm kuruluşlara uyan bir sınır yoktur. Ancak [S2010](#s2010) , 9 sınırının en iyi olduğunu belirtir:

"Bu nedenle, [...] eşik değerlerini göz önünde bulunduruyoruz en etkili şekilde. Bu eşik değerleri (tek bir üye için), BHA = 9 [...]. " (vurgu eklendi)

## <a name="code-analysis"></a>Kod Çözümleme

Kod Analizi bir bakım kuralları kategorisi içerir. Daha fazla bilgi için bkz. [Bakımlamama kuralları](/dotnet/fundamentals/code-analysis/quality-rules/maintainability-warnings). Eski Kod analizini kullanırken, genişletilmiş tasarım kılavuz kuralı kümesi bir bakım alanı içerir:

![Sınıf eşlenmiş tasarım kılavuzu kuralları](media/class-coupling-extended-design-guideline-rules.png)

Bakım alanının içinde, sınıf bağlantısı için bir kuraldır:

![Sınıf bağlantısı](media/class-coupling-maintainability-area-rules.png)

Bu kural, bir sınıf bağlantısı aşırı olduğunda bir uyarı verir. Daha fazla bilgi için bkz. [CA1506: aşırı sınıf bağlantısından kaçının](/dotnet/fundamentals/code-analysis/quality-rules/ca1506).

Bu kuralın açıklaması için bkz. arşivlenmiş kod analizi Web günlüğü gönderisi: [Iade ilkesi olarak kod ölçümleri](/archive/blogs/codeanalysis/code-metrics-as-check-in-policy) ve *sınıf için 80 ve üzeri bir yöntemde* eşik açıklaması uyarısı.  Bu değerler anormal ölçüde yüksek görünüyor, ancak en azından aşırı büyük bir üst sınır sağlar. Bu uyarıya ulaşırsanız, bir şey neredeyse kesinlikle yanlış olur.

## <a name="citations"></a>Alıntı

### <a name="ck94"></a>CK94

Oyduklik, S. R. & Kemerer, C. F. (1994). Nesne odaklı tasarıma yönelik bir ölçüm paketi (yazılım mühendisliğinde IEEE Işlemleri, Vol. 20, hayır. 6). University of the Yatsburgh Web sitesinden 14 Mayıs 2011 ' den alınır: [http://www.pitt.edu/~ckemerer/CK%20research%20papers/MetricForOOD_ChidamberKemerer94.pdf](http://www.pitt.edu/~ckemerer/CK%20research%20papers/MetricForOOD_ChidamberKemerer94.pdf)

### <a name="kkls2000"></a>KKLS2000

Kabaili, H., Keller, R., Lustman, F. ve Saint-deno, G. (2000). Sınıf Cohemi yeniden ziyaret: endüstriyel sistemlerde Empırical bir araştırma (Object-Oriented yazılım mühendisliğinde nicelik yaklaşımları üzerinde atölyenin çalışma yordamı). Üniversıté de Montréal Web sitesinden 20 Mayıs 2011 tarihi alındı [http://www.iro.umontreal.ca/~sahraouh/qaoose/papers/Kabaili.pdf](http://www.iro.umontreal.ca/~sahraouh/qaoose/papers/Kabaili.pdf)

### <a name="sk2003"></a>SK2003

Subkmanyam, R. & Krishnan, M. S. (2003). Object-Oriented tasarım karmaşıklığı için CK ölçüm Analizi: yazılım bozuklukları (yazılım mühendisliğinde IEEE Işlemleri, ses. 29, hayır) için etkiler. 4). Massachusetts Dartağız Web sitesinin University 'den 14 Mayıs 2011 ' den itibaren alındı [http://moosehead.cis.umassd.edu/cis580/readings/OO_Design_Complexity_Metrics.pdf](http://moosehead.cis.umassd.edu/cis580/readings/OO_Design_Complexity_Metrics.pdf)

### <a name="s2010"></a>S2010

Shatnawi, R. (2010). Open-Source sistemlerdeki Object-Oriented ölçümlerinin kabul edilebilir risk düzeyleri (yazılım mühendisliğinde IEEE Işlemleri, Vol. 36, hayır) için bir nicel araştırması. 2).

### <a name="yc79"></a>YC79

Edward Yourdon ve Larry L. Constantine. Yapılandırılmış tasarım. Prikna salonu, Engliwood Cliffs, N.J., 1979.