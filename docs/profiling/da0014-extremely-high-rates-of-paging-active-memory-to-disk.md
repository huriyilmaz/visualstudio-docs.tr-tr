---
title: 'DA0014: Diske aktif bellek sayfalama son derece yüksek oranları | Microsoft Dokümanlar'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.rules.DAMemoryBound
- vs.performance.DA0014
- vs.performance.14
- vs.performance.rules.DA0014
ms.assetid: a7fa3749-9191-437a-9331-9d917181e62f
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: e068771ba0fcc9b044ba7ff5243a75ceb3161e03
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779421"
---
# <a name="da0014-extremely-high-rates-of-paging-active-memory-to-disk"></a>DA0014: Aşırı yüksek oranda diske etkin bellek sayfalaması gerçekleşiyor.

|||
|-|-|
|Kural Id|DA0014|
|Kategori|Bellek ve Sayfalama|
|Profil oluşturma yöntemi|Tümü|
|İleti|Diske son derece yüksek bir arama etkin bellek oranı oluşuyor. Uygulamanız belleğe bağlı olabilir.|
|Kural türü|Uyarı|

 Örnekleme, .NET bellek veya kaynak çekişme yöntemlerini kullanarak profil yaptığınızda, bu kuralı tetiklemek için en az 25 örnek toplamanız gerekir.

## <a name="cause"></a>Nedeni
 Profil oluşturma çalışmasında toplanan sistem performans verileri, profil oluşturma çalışması boyunca diske ve diskten gelen son derece yüksek bir sayfalama oranının oluştuğunu gösterir. Bu düzeyde ki sayfalama oranları genellikle uygulama performansını ve yanıt verme yeteneğini etkiler. Algoritmaları gözden geçirerek bellek ayırmalarını azaltmayı düşünün. Uygulamanızın bellek gereksinimlerini de göz önünde bulundurmanız gerekebilir. daha fazla belleğe sahip bir bilgisayarda profil oluşturmayı yeniden çalıştırıyor.

## <a name="rule-description"></a>Kural açıklaması
 Diske aşırı çağrıda lama, fiziksel bellek yetersizliğinden kaynaklanabilir. Sayfalama işlemleri, sayfalama dosyasının bulunduğu fiziksel diskin kullanımına hakimse, uygulama yönelimli diğer disk işlemlerini aynı diske yavaşlatabilir.

 Sayfalar sık sık diskten okunur veya toplu sayfalama işlemlerinde diske yazılır. Sayfa Çıktısı/sn sayısı genellikle Sayfa Yazma/sn sayısından çok daha büyüktür. Çünkü Pages Output/sn, sistem dosyası önbelleğinden değiştirilen veri sayfalarını da içerir. Ancak, hangi işlemin doğrudan sayfalama veya neden sorumlu olduğunu belirlemek her zaman kolay değildir.

> [!NOTE]
> Bu kural, etkin bellek sayfalama düzeyleri çok yüksek bir orana ulaştığında yangınlar. Sayfalama düzeyi önemli olduğunda, ancak aşırı değil, bilgi kuralı [DA0017: Disk yangınları için aktif bellek arama yüksek oranları.](../profiling/da0017-high-rates-of-paging-active-memory-to-disk.md)

## <a name="how-to-fix-violations"></a>İhlalleri düzeltme
 [Markalar](../profiling/marks-view.md) görünümüne gitmek için Hata Listesi penceresindeki iletiyi çift tıklatın. **Bellek\Sayfalar/sn** sütununa bakın. Sayfalama IO etkinliğinin diğerlerinden daha ağır olduğu program yürütmesinin belirli aşamaları olup olmadığını belirleyin.

 Bir ASP.NET uygulaması için profil verilerini bir yük testi senaryosunda topluyorsanız, ek fiziksel bellekle (veya RAM) yapılandırılan bir makinede yük testini yeniden çalıştırmayı deneyin.

 Algoritmaları gözden geçirerek ve String.Concat ve String.Substring gibi bellek yoğun API'lerden kaçınarak bellek ayırmalarını azaltmayı düşünün.
