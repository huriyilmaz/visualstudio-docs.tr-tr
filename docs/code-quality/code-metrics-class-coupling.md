---
title: Kod ölçümleri - Sınıf bağlantısı
ms.date: 1/8/2021
description: Visual Studio'da kod ölçümleri için sınıf eşleştirme ölçümü hakkında bilgi Visual Studio.
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-code-analysis
ms.workload:
- multiple
ms.openlocfilehash: 6c9ff474cfdc8c572143145c642bc42e899b6516
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126632072"
---
# <a name="code-metrics---class-coupling"></a>Kod ölçümleri - Sınıf bağlantısı

Sınıf eşleştirmesi, başlangıçta [CK94](#ck94)tarafından tanımlandığı gibi Nesneler Arasında Eşleştirme (CBO) adıyla da gider. Temel olarak, sınıf eşleştirmesi tek bir sınıfın kaç sınıf kullandığına bir ölçüdür. Yüksek bir sayı kötüdür ve düşük bir sayı genellikle bu ölçümde iyidir. Sınıf bağlantısı, yazılım hatasına yönelik doğru bir tahmin olarak gösterilmiştir ve son çalışmalar 9 üst sınır değerinin en verimli [S2010](#s2010)olduğunu göstermiştir.

Microsoft belgelerine göre, sınıf eşleştirmesi "parametreler, yerel değişkenler, dönüş türleri, yöntem çağrıları, genel veya şablon örneklemeleri, temel sınıflar, arabirim uygulamaları, dış türlerde tanımlanan alanlar ve öznitelik süslemesi aracılığıyla benzersiz sınıflarla eşleşmeyi ölçür. İyi yazılım tasarımı, türlerin ve yöntemlerin yüksek uyum ve düşük eşleşmeye sahip olması gerektiğini dikte ediyor. Yüksek bağlantı, diğer türlerde birçok bağımlılıkları nedeniyle yeniden kullanılması ve korunması zor bir tasarım olduğunu gösterir."

Eşleştirme ve uyum kavramları net bir şekilde ilişkilidir. Bu tartışmayı konu başlığında tutmak için [KKLS2000'den](#kkls2000)kısa bir tanım vermekten başka bir uyumla daha derine ineriz:

"Modül uyumu Yourdon ve Constantine tarafından 'bir modülün iç öğelerinin ne kadar sıkı bir şekilde bağlı olduğu veya ilişkili olduğu' [YC79 olarak tanıtıldı.](#yc79) Bir modülün tam olarak tek bir görevi temsil ettiği ve tüm öğelerinin bu tek göreve katkıda bulunan güçlü bir uyumu vardır. Bunlar, uyumu kod yerine tasarım özniteliği ve yeniden kullanılabilirlik, bakım ve değişiklikle ilgili tahminde kullanılacak bir öznitelik olarak tanımlar."

## <a name="class-coupling-example"></a>Sınıf Eşleştirme Örneği

Şimdi sınıf eşleştirmenin nasıl bir işlemde olduğunu bakalım. İlk olarak yeni bir konsol uygulaması oluşturun ve içinde bazı özellikler bulunan Person adlı yeni bir sınıf oluşturun ve ardından kod ölçümlerini hemen hesap edin:

![Sınıf eşleştirme örneği 1](media/class-coupling-example-1.png)

Bu sınıf başka sınıf kullanmaz, çünkü sınıf eşleştirmesi 0'dır. Şimdi personstuff adlı başka bir sınıf oluşturmak için Person örneği oluşturan ve özellik değerlerini ayaran bir yöntem kullanın. Kod ölçümlerini yeniden hesapla:

![Sınıf eşleştirme örneği 2](media/class-coupling-example-2.png)

Sınıf eşleştirme değerinin ne kadar yüksek olduğunu görüyor musunuz? Ayrıca, kaç özellik ayarlansa da sınıf eşleştirme değerinin başka bir değere göre değil yalnızca 1'e kadar ilerler. Sınıf eşleştirmesi, ne kadar kullanılır olursa olsun bu ölçüm için her sınıfı yalnızca bir kez ölçür. Ayrıca, değerinin 1 olduğunu ancak oluşturucus unda 0 olduğunu `DoSomething()` `PersonStuff()` görüyor musunuz? Şu anda oluşturucuda başka bir sınıf kullanan bir kod yoktur.

Başka bir sınıf kullanılan oluşturucuya kod koysanız ne olur? Elde şunları elde ettiysiniz:

![Sınıf eşleştirme örneği 3](media/class-coupling-example-3.png)

Oluşturucu artık açıkça başka bir sınıf kullanan koda sahip ve sınıf eşleştirme ölçümü bu durumu gösteriyor. Yine için genel sınıf eşleştirmenin 1 olduğunu ve ayrıca 1 olduğunu görebilir ve bunu kullanan iç kodunuz ne kadar olursa olsun yalnızca bir dış sınıfın `PersonStuff()` `DoSomething()` kullan olduğunu gösterir.

Ardından, başka bir yeni sınıf oluşturun. Bu sınıfa bir ad girin ve içinde bazı özellikler oluşturun:

![Sınıf eşleştirme örneği - yeni sınıf ekleme](media/class-coupling-example-add-new-class.png)

Şimdi sınıfındaki yöntemimizde `DoSomething()` sınıfını kullanın `PersonStuff` ve kod ölçümlerini yeniden hesaplayın:

![Sınıf eşleştirme örneği 4](media/class-coupling-example-4.png)

Gördüğünüz gibi PersonStuff sınıfı için sınıf eşleştirmesi 2'ye kadar gider ve sınıfta detaya gidersiniz, yöntemin içinde en çok eşleşmeye sahip olduğunu, ancak oluşturucu hala 1 sınıf `DoSomething()` tüketir.  Bu ölçümleri kullanarak, bir sınıfın genel maksimum sayısını görebilir ve üye başına ayrıntıya inebilirsiniz.

## <a name="the-magic-number"></a>Sihirli Sayı

Cyclomatic karmaşıklığında olduğu gibi, tüm kuruluşlara uyan bir sınır yoktur. Ancak [S2010,](#s2010) 9 sınırının en uygun olduğunu gösteriyor:

"Bu nedenle eşik değerlerini dikkate alırz . en etkilisi olarak. Bu eşik değerleri (tek bir üye için) CBO = 9 şeklindedir." (vurgu eklendi)

## <a name="code-analysis"></a>Kod Çözümleme

Kod analizi, Bakım kuralları kategorisini içerir. Daha fazla bilgi için [bkz. Bakım kuralları.](/dotnet/fundamentals/code-analysis/quality-rules/maintainability-warnings) Eski kod analizini kullanırken, Genişletilmiş Tasarım Kılavuzu kural kümesi bir bakım alanı içerir:

![Sınıf eşleştirme Genişletilmiş Tasarım Kılavuzu kuralları](media/class-coupling-extended-design-guideline-rules.png)

Bakım alanı, sınıf eşleştirmesi için bir kuraldır:

![Sınıf eşleştirme kuralı](media/class-coupling-maintainability-area-rules.png)

Bu kural, sınıf bağlantısı aşırı olduğunda bir uyarı sağlar. Daha fazla bilgi için bkz. [CA1506: Aşırı sınıf bağlantısından kaçının.](/dotnet/fundamentals/code-analysis/quality-rules/ca1506)

## <a name="citations"></a>Alıntı

### <a name="ck94"></a>CK94

Chidamber, S. R. & ZamanEr, C. F. (1994). Nesne Odaklı Tasarım için Ölçüm Paketi (Yazılım Mühendisliğinde IEEE İşlemleri, Vol. 20, Hayır. 6). 14 Mayıs 2011, University of Pittsburgh web sitesinden alındı: [http://www.pitt.edu/~ckemerer/CK%20research%20papers/MetricForOOD_ChidamberKemerer94.pdf](http://www.pitt.edu/~ckemerer/CK%20research%20papers/MetricForOOD_ChidamberKemerer94.pdf)

### <a name="kkls2000"></a>KKLS2000

Kabaili, H., Keller, R., Saintman, F., and Saint-Denis, G. (2000). Sınıf Uyumu Yeniden Değerlendirildi: Endüstriyel Sistemlerle ilgili Ampirik Bir Çalışma (Object-Oriented Yazılım Mühendisliğinde Nicel Yaklaşımlar Atölyesinde Proceedings of the Workshop). 20 Mayıs 2011 tarihindeKiré de Montréal web sitesinden alındı [http://www.iro.umontreal.ca/~sahraouh/qaoose/papers/Kabaili.pdf](http://www.iro.umontreal.ca/~sahraouh/qaoose/papers/Kabaili.pdf)

### <a name="sk2003"></a>SK2003

Subramanyam, R. & Ancak, M. S. (2003). Object-Oriented Tasarım Karmaşıklığı için CK Ölçümlerinin Ampirik Analizi: Yazılım Hatalarının Etkileri (Yazılım Mühendisliğinde IEEE İşlemleri, Vol. 29, Hayır. 4). 14 Mayıs 2011 tarihinde, University of University of Sonadea web sitesinden alındı [http://moosehead.cis.umassd.edu/cis580/readings/OO_Design_Complexity_Metrics.pdf](http://moosehead.cis.umassd.edu/cis580/readings/OO_Design_Complexity_Metrics.pdf)

### <a name="s2010"></a>S2010

Shatnawi, R. (2010). Open-Source Sistemlerindeki Object-Oriented Ölçümlerinin Kabul Edilebilir Risk Düzeylerinin Nicel Bir Araştırma (Yazılım Mühendisliğinde IEEE İşlemleri, Vol. 36, Hayır. 2).

### <a name="yc79"></a>YC79

Edward Yourdon ve Angeles L. Constantine. Yapılandırılmış Tasarım. Prentice Hall, Englewood Cliffs, N.J., 1979.