---
title: 'DA0023: Yüksek GC CPU zamanı | Microsoft Dokümanlar'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.DA0023
- vs.performance.23
- vs.performance.rules.DA0023
ms.assetid: aba875fe-9cbc-418d-a2c4-6eb47519a5bb
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: f0dd45486f526954d7dfce45cd607ff6196eae00
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74777653"
---
# <a name="da0023-high-gc-cpu-time"></a>DA0023: Yüksek GC CPU süresi

|||
|-|-|
|Kural Id|DA0023|
|Kategori|.NET Çerçeve Kullanımı|
|Profil oluşturma yöntemi|Tümü|
|İleti|% GC'de zaman oldukça yüksektir. Aşırı miktarda çöp toplama yükü ne kadar olduğunu gösteren bu gösterge, uygulamanızın yanıt verme yeteneğini etkileyebilir. Uygulamanızın daha iyi kullandığı bellek ayırma desenini anlamak için .NET bellek ayırma verilerini ve nesne yaşam boyu bilgilerini toplayabilirsiniz.|
|Kural türü|Bilgilendirici|

 Örnekleme, .NET bellek veya kaynak çekişme yöntemlerini kullanarak profil yaptığınızda, bu kuralı tetiklemek için en az 10 örnek toplamanız gerekir.

## <a name="cause"></a>Nedeni
 Profil oluşturma sırasında toplanan sistem performans verileri, çöp toplamada harcanan sürenin toplam uygulama işleme süresiyle karşılaştırıldığında önemli olduğunu gösterir.

## <a name="rule-description"></a>Kural açıklaması
 Microsoft .NET ortak dil çalışma zamanı (CLR), uygulamanın artık kullanmadığı nesnelerden bellek geri almak için bir çöp toplayıcısı kullanan otomatik bir bellek yönetim mekanizması sağlar. Çöp toplayıcı, birçok ayırmanın kısa ömürlü olduğu varsayımına dayanarak nesil odaklıdır. Yerel değişkenler, örneğin, kısa ömürlü olmalıdır. Yeni oluşturulan nesneler nesil 0 'da (gen 0) başlar ve çöp toplama çalışmasından sağ kurtulduklarında nesil 1'e doğru ilerlerler ve uygulama hala kullanıyorsa nesil 2'ye geçiş yaparlar.

 Nesil 0'daki nesneler sık sık ve verimli bir şekilde toplanır. Nesil 1'deki nesneler daha az sıklıkta ve daha az verimli bir şekilde toplanır. Son olarak, nesil 2 uzun ömürlü nesneleri daha az sıklıkta toplanmalıdır. Tam bir çöp toplama çalışması olan Generation 2 koleksiyonu da en pahalı işlemdir.

 Bu kural, çöp toplamada harcanan süre toplam uygulama işleme süresiyle karşılaştırıldığında önemli olduğunda yangınlar.

> [!NOTE]
> Çöp toplamada harcanan sürenin toplam uygulama işleme süresiyle karşılaştırıldığında aşırı olduğunda, [DA0024:](../profiling/da0024-excessive-gc-cpu-time.md) Bu kural yerine Aşırı GC CPU Zamanı uyarısı yangınları.

## <a name="how-to-investigate-a-warning"></a>Bir uyarı nasıl araştırılı
 Profil oluşturma verilerinin [İşaretler Görünümü'ne](../profiling/marks-view.md) gitmek için Hatalar Listesi penceresindeki iletiyi çift tıklatın. **GC sütununda\\.NET CLR Bellek % Süresini** bulun. Yönetilen bellek çöp toplama ek yükü diğer aşamalardan daha ağır olduğu program yürütme belirli aşamaları olup olmadığını belirleyin. GC değerindeki % Zaman değerlerini **Gen 0 Koleksiyonları**# nda bildirilen çöp toplama oranıyla karşılaştırın , # gen 1 **Koleksiyonları**, # gen **2 Koleksiyonları** değerleri.

 GC değerindeki % Zaman, bir uygulamanın çöp toplama işlemini gerçekleştirme de toplam işlem miktarıyla orantılı olarak harcadığı süreyi bildirmeye çalışır. GC değerinin % Zamanı'nın yüksek bir değeri bildirebileceği durumlar olduğunu unutmayın, ancak bunun nedeni aşırı çöp toplama değildir. GC değerinin % Zamanı'nın hesaplanma şekli hakkında daha fazla bilgi için, [Farklı Araçlar Tarafından Bildirilen Perf Verileri Arasındaki Farka](https://devblogs.microsoft.com/maoni/archive/difference-between-perf-data-reported-by-different-tools-4.aspx) bakın - **MAoni'nin Weblog'unun** MSDN'deki 4 girişi. Sayfa hataları oluşuyorsa veya uygulama çöp toplama sırasında makinedeki diğer yüksek öncelikli çalışmalar tarafından engellenmişse, GC sayacındaki % Süre bu ek gecikmeleri yansıtacaktır.
