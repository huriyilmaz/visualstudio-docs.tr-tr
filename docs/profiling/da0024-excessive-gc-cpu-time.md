---
title: 'DA0024: Aşırı GC CPU Süresi | Microsoft Dokümanlar'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.DA0024
- vs.performance.24
- vs.performance.rules.DA0024
ms.assetid: 228872da-77d0-4da5-b455-ac57fb1867c9
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 3b8352095bcf31c137d391c2ed2e832d34e0ec7b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779356"
---
# <a name="da0024-excessive-gc-cpu-time"></a>DA0024: Aşırı GC CPU süresi

|||
|-|-|
|Kural Id|DA0024|
|Kategori|.NET Çerçeve Kullanımı|
|Profil oluşturma yöntemi|Tümü|
|İleti|% GC'de süre çok yüksektir. Aşırı miktarda çöp toplama yükü vardır.|
|Kural türü|Uyarı|

 Örnekleme, .NET bellek veya kaynak çekişme yöntemlerini kullanarak profil yaptığınızda, bu kuralı tetiklemek için en az 10 örnek toplamanız gerekir.

## <a name="cause"></a>Nedeni
 Profil oluşturma sırasında toplanan sistem performans verileri, çöp toplamada harcanan sürenin toplam uygulama işleme süresiyle karşılaştırıldığında aşırı derecede yüksek olduğunu gösterir.

## <a name="rule-description"></a>Kural açıklaması
 Microsoft .NET ortak dil çalışma zamanı (CLR), uygulamanın artık kullanmadığı nesnelerden bellek geri almak için bir çöp toplayıcısı kullanan otomatik bir bellek yönetim mekanizması sağlar. Çöp toplayıcı, birçok ayırmanın kısa ömürlü olduğu varsayımına dayanarak nesil odaklıdır. Yerel değişkenler, örneğin, kısa ömürlü olmalıdır. Yeni oluşturulan nesneler nesil 0 'da (gen 0) başlar ve çöp toplama çalışmasından sağ kurtulduklarında nesil 1'e doğru ilerlerler ve uygulama hala kullanıyorsa nesil 2'ye geçiş yaparlar.

 Nesil 0'daki nesneler sık sık ve genellikle çok verimli bir şekilde toplanır. Nesil 1'deki nesneler daha az sıklıkta ve daha az verimli bir şekilde toplanır. Son olarak, nesil 2 uzun ömürlü nesneleri daha az sıklıkta toplanmalıdır. Tam bir çöp toplama çalışması olan Generation 2 koleksiyonu da en pahalı işlemdir.

 Bu kural, çöp toplamada harcanan süre toplam uygulama işleme süresiyle karşılaştırıldığında aşırı yüksek olduğunda yangınlar.

> [!NOTE]
> Çöp toplamada harcanan sürenin toplam uygulama işleme süresiyle karşılaştırıldığında önemli ancak aşırı olmadığı durumlarda, [DA0023:](../profiling/da0023-high-gc-cpu-time.md) Bu kural yerine Yüksek GC CPU zamanı uyarısı yangınları.

## <a name="how-to-investigate-a-warning"></a>Bir uyarı nasıl araştırılı
 Profil oluşturma verilerinin [İşaretler Görünümü'ne](../profiling/marks-view.md) gitmek için Hatalar Listesi penceresindeki iletiyi çift tıklatın. **GC sütununda\\.NET CLR Bellek % Süresini** bulun. Yönetilen bellek çöp toplama ek yükü diğer aşamalardan daha ağır olduğu program yürütme belirli aşamaları olup olmadığını belirleyin. GC değerindeki % Zaman değerlerini **Gen 0 Koleksiyonları**# nda bildirilen çöp toplama oranıyla karşılaştırın , # gen 1 **Koleksiyonları**, # gen **2 Koleksiyonları** değerleri.

 GC değerindeki % Zaman, bir uygulamanın çöp toplama işlemini gerçekleştirme de toplam işlem miktarıyla orantılı olarak harcadığı süreyi bildirmeye çalışır. GC değerinin % Zamanı'nın yüksek bir değeri bildirebileceği durumlar olduğunu unutmayın, ancak bunun nedeni aşırı çöp toplama değildir. GC değerinin % Zamanı'nın hesaplanma şekli hakkında daha fazla bilgi için, [Farklı Araçlar Tarafından Bildirilen Perf Verileri Arasındaki Farka](https://devblogs.microsoft.com/maoni/archive/difference-between-perf-data-reported-by-different-tools-4.aspx) bakın - **MAoni'nin Weblog'unun** MSDN'deki 4 girişi. Sayfa hataları oluşuyorsa veya uygulama çöp toplama sırasında makinedeki diğer yüksek öncelikli çalışmalar tarafından önceden engellenmişse, GC sayacındaki % Süre bu ek gecikmeleri yansıtacaktır.
