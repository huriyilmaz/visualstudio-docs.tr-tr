---
title: Kod ölçümleri-döngüsel karmaşıklığı
ms.date: 5/7/2021
description: Visual Studio kod ölçümleri için döngüsel karmaşıklık ölçümünü öğrenin.
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-code-analysis
ms.workload:
- multiple
ms.openlocfilehash: b8de7119eb232afb904896cfedbbece9bbf2f8d5
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126632067"
---
# <a name="code-metrics---cyclomatic-complexity"></a>Kod ölçümleri-döngüsel karmaşıklığı

Kod ölçümleri ile çalışırken, en az anlaşılan öğelerden biri döngüsel karmaşıklık gibi görünüyor. Temelde, döngüsel karmaşıklıkla, daha yüksek sayılar hatalı ve daha düşük sayılardır. Belirli bir kodun ne kadar zor olduğunun nasıl test, bakım veya sorun giderebileceği hakkında bir fikir sahibi olmak için döngüsel karmaşıklığını kullanabilir ve kodun hata üretmesinin ne olacağı hakkında bir gösterge elde edebilirsiniz. Yüksek düzeyde, kaynak kodunuzda yapılan kararların sayısını sayarak döngüsel karmaşıklığı değerini saptadık. Bu makalede, kavramı hızla anlamak için döngüsel karmaşıklığın basit bir örneği ile çalışmaya başladığınızda, gerçek kullanımla ilgili bazı ek bilgilere ve önerilen sınırlara göz atın. Son olarak, bu konuyu daha ayrıntılı bir şekilde incelemek için kullanılabilen alıntılar 'in bir bölümü vardır.

## <a name="example"></a>Örnek

Döngüsel karmaşıklığı " [NIST235](#nist235)kaynak kodu işlevindeki karar mantığı miktarı" olarak tanımlanır. Kodda yapılması gereken daha fazla kararı, ne kadar karmaşık olduğunu basitçe yapmanız yeterlidir.

Şimdi bunu bir işlem halinde görelim. Yeni bir konsol uygulaması oluşturun ve **çözüm Için kod ölçümlerini hesaplamak > analiz** ederek kod ölçümlerinizi hemen hesaplayın.

![Döngüsel karmaşıklık örneği 1](media/cyclomatic-complexity-example-1.png)

Döngüsel karmaşıklığının 2 ' de (mümkün olan en düşük değer) olduğuna dikkat edin. Karar verme dışı kod eklerseniz karmaşıklığın değişmediğine dikkat edin:

![Döngüsel karmaşıklık örneği 2](media/cyclomatic-complexity-example-2.png)

Bir karar eklerseniz, döngüsel karmaşıklık değeri 1 ' den geçer:

![Döngüsel karmaşıklık örneği 3](media/cyclomatic-complexity-example-3.png)

If ifadesini 4 kararının yapıldığı bir switch ifadesine değiştirdiğinizde, özgün 2 ' den 6 ' a gider:

![Döngüsel karmaşıklık örnek 4](media/cyclomatic-complexity-example-4.png)

Bir (kuramsal) daha büyük bir kod tabanına göz atalım.

![Döngüsel karmaşıklığı örnek 5](media/cyclomatic-complexity-example-5.png)

Öğelerin çoğunun, Products_Related sınıfının bir değerinin 1 olduğuna, ancak birkaç farklı değerin 5 karmaşıklığıyla karşılaşdığına dikkat edin. Bu, büyük bir anlaşma olmayabilir, ancak diğer birçok üyenin aynı sınıfta 1 ' i vardır, bu iki öğeye kesinlikle yaklaşmanız ve bunların içinde neler olduğunu görmeniz gerekir. Bunu, öğeye sağ tıklayıp bağlam menüsünden **kaynak koduna git** ' i seçerek yapabilirsiniz. Daha yakından göz atın `Product.set(Product)` :

![Döngüsel karmaşıklık örneği 6](media/cyclomatic-complexity-example-6.png)

Tüm if deyimleri verildiğinde, döngüsel karmaşıklığının neden 5 ' te olduğunu görebilirsiniz. Bu noktada, kabul edilebilir bir karmaşıklık düzeyi olduğuna karar verebilir veya karmaşıklığı azaltmak için yeniden düzenleme yapabilirsiniz.

## <a name="the-magic-number"></a>Sihirli sayı

Bu sektördeki birçok ölçümde olduğu gibi, tüm kuruluşlara uygun bir döngüsel karmaşıklık sınırı yoktur. Ancak [NIST235](#nist235) , 10 sınırının iyi bir başlangıç noktası olduğunu belirtir:

"Sınır olarak kullanılacak kesin numara, biraz controversıal olarak kalır. McCain tarafından önerildiği şekilde 10 ' un orijinal sınırının önemli destekleyici kanıtları vardır, ancak 15 ' in de başarılı bir şekilde kullanıldığı sınırlandırmalar. 10 ' dan fazla sınır, tipik projeler üzerinde birkaç işlem avantajı olan projeler (örneğin, deneyimli personel, resmi tasarım, modern programlama dili, yapılandırılmış programlama, kod talimatları ve kapsamlı bir test planı) için ayrılmalıdır. Diğer bir deyişle, bir kuruluş 10 ' dan büyük bir karmaşıklık sınırı seçebilir, ancak bunun ne yaptığını bildiğinden ve daha karmaşık modüller için gereken ek test çabasını ayırmak ister. " [NIST235](#nist235)

## <a name="cyclomatic-complexity-and-line-numbers"></a>Döngüsel karmaşıklık ve satır numaraları

En iyi kod kalitesi olan çok büyük bir tahmine sahip olan kodun tek başına satır sayısına bakmanız yeterlidir. Bir işlevde daha fazla kod satırı olması için bazı temel gerçeği vardır. Bu, büyük olasılıkla hatalara sahip olma nedenidir. Ancak, döngüsel karmaşıklığını kod satırları ile birleştirdiğinizde, hatalara yönelik potansiyel olarak çok daha net bir resim görürsünüz.

NASA 'da yazılım güvencesi Teknoloji Merkezi (SATC) tarafından açıklandığı gibi:

"SATC, en etkili değerlendirmenin boyut ve (döngüsel) karmaşıklığın bir birleşimi olduğunu saptadı. Hem yüksek karmaşıklığa hem de büyük boyuta sahip modüller en düşük güvenilirliğe sahiptir. Düşük boyutlu ve yüksek karmaşıklığa sahip modüller de bir güvenilirlik riski olduğundan, çok terse kodu olduğu ve bu sayede değiştirilmesi veya değiştirilmesi zor. " [SATC](#satc)

## <a name="code-analysis"></a>Kod Çözümleme

Kod Analizi bir bakım kuralları kategorisi içerir. Daha fazla bilgi için bkz. [Bakımlamama kuralları](/dotnet/fundamentals/code-analysis/quality-rules/maintainability-warnings). Eski Kod analizini kullanırken, genişletilmiş tasarım kılavuz kuralı kümesi bir bakım alanı içerir:

![Döngüsel karmaşıklık tasarım yönergeleri kural kümeleri](media/cyclomatic-complexity-design-guidelines.png)

Bakım alanının içinde, karmaşıklık için bir kuraldır:

![Döngüsel karmaşıklık bakım kuralı](media/cyclomatic-complexity-maintainability-rule.png)

Bu kural, döngüsel karmaşıklığı 25 ' i aştığında bir uyarı verir, bu sayede aşırı karmaşıklıktan kaçınmanıza yardımcı olabilir. Kural hakkında daha fazla bilgi edinmek için bkz. [CA1502](/dotnet/fundamentals/code-analysis/quality-rules/ca1502)

## <a name="putting-it-all-together"></a>Tümünü bir araya getirme

En alttaki satır, yüksek karmaşıklığa sahip bir sayının, bakım ve sorun giderme süresi arttığı zaman daha büyük bir olasılık anlamına gelir. Yüksek karmaşıklığa sahip tüm işlevlere daha yakından göz atın ve bunların daha az karmaşık hale gelmesi için yeniden düzenlenmiş olup olmadığına karar verin.

## <a name="citations"></a>Alıntı

### <a name="mccabe5"></a>MCCABE5

McCabe, T. ve A. Watson (1994), yazılım karmaşıklığı (CrossTalk: savunma yazılım mühendisliği günlüğü).

### <a name="nist235"></a>NIST235

Watson, A. H., & McCabe, T. J. (1996). Yapılandırılmış test: döngüsel karmaşıklık ölçümünü (NıST özel yayını 500-235) kullanan bir test yöntemi. Mccaof Software Web sitesinden 14 Mayıs 2011 ' den alınan: [http://www.mccabe.com/pdf/mccabe-nist235r.pdf](http://www.mccabe.com/pdf/mccabe-nist235r.pdf)

### <a name="satc"></a>SATC

Rosenberg, L., Hakökü, T., Shaw, J. (1998). Yazılım ölçümleri ve güvenilirliği (Yazılım güvenilirlik mühendisliği üzerinde IEEE International Symposium 'ın devam eden yordamı). , Penn State Üniversitesi web sitesinden 14 Mayıs 2011 ' den itibaren alınır: [http://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.104.4041&rep=rep1&type=pdf](http://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.104.4041&rep=rep1&type=pdf)