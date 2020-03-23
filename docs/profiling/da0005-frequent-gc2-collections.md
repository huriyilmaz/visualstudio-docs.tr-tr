---
title: 'DA0005: Sık GC2 koleksiyonları | Microsoft Dokümanlar'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.DA0005
- vs.performance.rules.DAManyGC2Collections
- vs.performance.5
- vs.performance.rules.DA0005
ms.assetid: 8d3f267c-8a74-4cf4-91a5-0b06a76dc2bd
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: a50567a101d77ed6498aaae13a5fe5556d9c1056
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74777718"
---
# <a name="da0005-frequent-gc2-collections"></a>DA0005: Sık kullanılan GC2 koleksiyonları

|||
|-|-|
|RuleId|DA0005|
|Kategori|.NET Çerçeve Kullanımı|
|Profil oluşturma yöntemi|.NET Bellek|
|İleti|Nesnelerinizin çoğu nesil 2 çöp toplama toplanmaktadır.|
|Mesaj türü|Uyarı|

## <a name="cause"></a>Nedeni
 Nesil 2 çöp toplamada çok sayıda .NET bellek nesnesi geri kazanılıyor.

## <a name="rule-description"></a>Kural açıklaması
 Microsoft .NET ortak dil çalışma süresi (CLR), uygulamanın artık kullanmadığı nesnelerden bellek geri almak için bir çöp toplayıcısı kullanan otomatik bir bellek yönetim mekanizması sağlar. Çöp toplayıcı, birçok ayırmanın kısa ömürlü olduğu varsayımına dayanarak nesil odaklıdır. Yerel değişkenler, örneğin, kısa ömürlü olmalıdır. Yeni oluşturulan nesneler nesil 0 'da (gen 0) başlar ve çöp toplama çalışmasından sağ kurtulduklarında nesil 1'e doğru ilerlerler ve uygulama hala kullanıyorsa nesil 2'ye geçiş yaparlar.

 Nesil 0'daki nesneler sık sık ve genellikle çok verimli bir şekilde toplanır. Nesil 1'deki nesneler daha az sıklıkta ve daha az verimli bir şekilde toplanır. Son olarak, nesil 2 uzun ömürlü nesneleri daha az sıklıkta toplanmalıdır. Tam bir çöp toplama çalışması olan Generation 2 koleksiyonu da en pahalı işlemdir.

 Orantılı olarak çok fazla nesil 2 çöp toplama oluştuğunda bu kural yangınları. Çok fazla nispeten kısa ömürlü nesneler nesil 1 koleksiyonu hayatta ama sonra bir nesil 2 tam toplama toplanabilir edebiliyoruz, bellek yönetimi maliyeti kolayca aşırı olabilir. Daha fazla bilgi için, MSDN Web sitesinde Rico Mariani's Performance Tidbits orta [yaş kriz](https://blogs.msdn.microsoft.com/ricom/2003/12/04/mid-life-crisis/) sonrası bakın.

## <a name="how-to-investigate-a-warning"></a>Bir uyarı nasıl araştırılı
 Uygulamanın bellek ayırma desenini anlamak için [.NET Bellek Veri Görünümleri](../profiling/dotnet-memory-data-views.md) raporlarını gözden geçirin. Programın veri nesnelerinden hangisinin nesil 2'de hayatta kalarak oradan geri alındığını belirlemek için [Nesne Yaşam Boyu Görünümü'ni](../profiling/object-lifetime-view.md) kullanın. Bu [ayırmalarla](../profiling/dotnet-memory-allocations-view.md) sonuçlanan yürütme yolunu belirlemek için Ayırmalar Görünümünü kullanın.

 Çöp toplama performansını nasıl artırılabildiğini öğrenmek için Microsoft Web [sitesindeki Çöp Toplayıcı Temelleri ve Performans İpuçları'na](/previous-versions/dotnet/articles/ms973837(v=msdn.10)) bakın. Otomatik çöp toplama nın ek yükü hakkında bilgi için [bkz.](https://msdn.microsoft.com/magazine/cc534993.aspx)
