---
title: Kod ölçümleri - Cyclomatic karmaşıklığı
ms.date: 5/7/2021
description: Veri kaynaklarında kod ölçümleri için cyclomatic karmaşıklık ölçümü Visual Studio.
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 1798b0faa1b0cf44ae490f5b27571e5466b82ca9
ms.sourcegitcommit: cc66c898ce82f9f1159bd505647f315792cac9fc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/10/2021
ms.locfileid: "109682691"
---
# <a name="code-metrics---cyclomatic-complexity"></a>Kod ölçümleri - Cyclomatic karmaşıklığı

Kod ölçümleriyle çalışırken, en az anlaşılan öğelerden biri cyclomatic karmaşıklık gibi görünüyor. Temelde, cyclomatic karmaşıklığıyla, yüksek sayılar kötüdür ve düşük sayılar iyidir. Herhangi bir kodun test, bakım veya sorun gidermenin ne kadar zor olduğunu ve ayrıca kodun hata üretme olasılığına dair bir gösterge elde etmek için cyclomatic karmaşıklığını kullanabilirsiniz. Yüksek bir düzeyde, kaynak kodunda verilen karar sayısını sayarak cyclomatic karmaşıklığının değerini belirleriz. Bu makalede, kavramı hızlı bir şekilde anlamak için cyclomatic karmaşıklığının basit bir örneğiyle başlayacak, ardından gerçek kullanım ve önerilen sınırlar hakkında bazı ek bilgilere göz atacağız. Son olarak, bu konuda daha derine inen alıntıların bir bölümü vardır.

## <a name="example"></a>Örnek

Cyclomatic complexity is defined as measuring "the amount of decision logic function" [NIST235](#nist235). Basitçe ifade etmek gerekirse, kodda ne kadar çok karar almak gerekirse o kadar karmaşıktır.

Şimdi nasıl bir işlemde olduğunu göreceğiz. Yeni bir konsol uygulaması oluşturun ve Çözüm için Kod Ölçümlerini Hesapla'ya gidip **> ölçümlerinizi hemen hesap edin.**

![Cyclomatic karmaşıklık örneği 1](media/cyclomatic-complexity-example-1.png)

Cyclomatic karmaşıklığının 2 (mümkün olan en düşük değer) olduğunu fark edersiniz. Karar olmayan kod eklersanız karmaşıklığın değişmey olduğunu fark edersiniz:

![Cyclomatic karmaşıklık örneği 2](media/cyclomatic-complexity-example-2.png)

Bir karar eklersanız, cyclomatic karmaşıklık değeri 1'e kadar gider:

![Cyclomatic karmaşıklık örneği 3](media/cyclomatic-complexity-example-3.png)

If deyimini, daha sonra 4 karara sahip bir switch deyimine değiştir0000000000000000000000000000000000000000000000000000000000000000000000000000

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

En iyi kod kalitesi olan çok büyük bir tahmine sahip olan kodun tek başına satır sayısına bakmanız yeterlidir. Bir işlevde kod satırı sayısı ne kadar fazla ise hata olma olasılığı da o kadar fazladır. Ancak, cyclomatic karmaşıklığını kod satırlarıyla birleştirin, hata potansiyeline çok daha net bir şekilde bakabilirsiniz.

NASA'daki Yazılım Güvencesi Merkezi'nde (SATC) açıklandığı gibi:

"SATC, en etkili değerlendirmenin boyut ve (Cyclomatic) karmaşıklık bileşimi olduğunu buldu. Hem yüksek karmaşıklık hem de büyük boyutlu modüller en düşük güvenilirlik düzeyine sahiptir. Boyutu düşük ve karmaşıklık düzeyi yüksek modüller de güvenilirlik riskiyle karşı karşıyadır çünkü bunlar genellikle kodda değişiklik yapmak veya değiştirmek zordur." [SATC](#satc)

## <a name="code-analysis"></a>Kod Çözümleme

Kod analizi, Bakım kuralları kategorisini içerir. Daha fazla bilgi için [bkz. Bakım kuralları.](/dotnet/fundamentals/code-analysis/quality-rules/maintainability-warnings) Eski kod analizini kullanırken, Genişletilmiş Tasarım Kılavuzu kural kümesi bir bakım alanı içerir:

![Cyclomatic karmaşıklık tasarım yönergeleri kural kümeleri](media/cyclomatic-complexity-design-guidelines.png)

Bakım alanı karmaşıklık kuralıdır:

![Cyclomatic karmaşıklık bakım kuralı](media/cyclomatic-complexity-maintainability-rule.png)

Bu kural, cyclomatic karmaşıklık 25'e ulaştığında bir uyarı sağlar, bu nedenle aşırı karmaşıklıktan kaçınmanıza yardımcı olabilir. Kural hakkında daha fazla bilgi edinmek için bkz. [CA1502](/dotnet/fundamentals/code-analysis/quality-rules/ca1502)

## <a name="putting-it-all-together"></a>Hepsini Bir Araya Koyma

Sonuçta yüksek karmaşıklık sayısı, bakım ve sorun giderme sürelerinin artmış olmasıyla hataların olasılığının daha yüksek olduğu anlamına gelir. Karmaşıklık düzeyi yüksek olan işlevlere daha yakından bakın ve bunları daha az karmaşık hale getirirken yeniden düzenlemeye karar verin.

## <a name="citations"></a>Alıntı

### <a name="mccabe5"></a>MCCABE5

McCabe, T. ve A. Watson (1994), yazılım karmaşıklığı (CrossTalk: savunma yazılım mühendisliği günlüğü).

### <a name="nist235"></a>NIST235

Watson, A. H., & McCabe, T. J. (1996). Yapılandırılmış test: döngüsel karmaşıklık ölçümünü (NıST özel yayını 500-235) kullanan bir test yöntemi. Mccaof Software Web sitesinden 14 Mayıs 2011 ' den alınan: [http://www.mccabe.com/pdf/mccabe-nist235r.pdf](http://www.mccabe.com/pdf/mccabe-nist235r.pdf)

### <a name="satc"></a>SATC

Rosenberg, L., Hakökü, T., Shaw, J. (1998). Yazılım ölçümleri ve güvenilirliği (Yazılım güvenilirlik mühendisliği üzerinde IEEE International Symposium 'ın devam eden yordamı). , Penn State Üniversitesi web sitesinden 14 Mayıs 2011 ' den itibaren alınır: [http://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.104.4041&rep=rep1&type=pdf](http://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.104.4041&rep=rep1&type=pdf)