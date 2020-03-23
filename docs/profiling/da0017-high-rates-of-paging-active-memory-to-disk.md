---
title: 'DA0017: Diske aktif bellek sayfalama yüksek oranları | Microsoft Dokümanlar'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.17
- vs.performance.rules.DA0017
- vs.performance.DA0017
ms.assetid: 01011eec-5930-43b3-980d-2cb01e2ca7f6
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 87e7c6b2d94602eca9e81098bb50bd0330b2bcd9
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779395"
---
# <a name="da0017-high-rates-of-paging-active-memory-to-disk"></a>DA0017: Yüksek oranda diske etkin bellek sayfalaması gerçekleşiyor.

|||
|-|-|
|Kural Id|DA0017|
|Kategori|Bellek ve Sayfalama|
|Profil oluşturma yöntemi|Tümü|
|İleti|Diske yüksek bir arama etkin bellek oranı oluşuyor. Uygulamanız belleğe bağlı olabilir.|
|Kural türü|Bilgi|

 Örnekleme, .NET bellek veya kaynak çekişme yöntemlerini kullanarak profil yaptığınızda, bu kuralı tetiklemek için en az 10 örnek toplamanız gerekir.

## <a name="cause"></a>Nedeni
 Profil oluşturma çalışmasında toplanan sistem performans verileri, profil oluşturma çalışması boyunca diske ve diskten gelen yüksek oranda etkin bellek oluşturma nın gerçekleştiğini gösterir. Bu düzeyde ki sayfalama oranları normalde uygulama performansını ve yanıt verme yeteneğini etkileyecektir. Algoritmaları gözden geçirerek bellek ayırmalarını azaltmayı düşünün. Uygulamanızın bellek gereksinimlerini de göz önünde bulundurmanız gerekebilir.

## <a name="rule-description"></a>Kural açıklaması

> [!NOTE]
> Etkin belleğin sayfalama düzeyleri önemli miktarda ulaştığında bu bilgilendirme kuralı yangınları. Son derece yüksek düzeyde sayfalama oluştuğunda, uyarı kuralı [DA0014: Bunun yerine disk yangınlarına etkin bellek sayfalama son derece yüksek oranlarda.](../profiling/da0014-extremely-high-rates-of-paging-active-memory-to-disk.md)

 Diske aşırı çağrıda lama, fiziksel bellek yetersizliğinden kaynaklanabilir. Sayfalama işlemleri, sayfalama dosyasının bulunduğu fiziksel diskin kullanımına hakimse, uygulama yönelimli diğer disk işlemlerini aynı diske yavaşlatabilir.

 Sayfalar genellikle diskten okunur veya toplu sayfalama işlemlerinde diske yazılır. Sayfa Çıktısı/sn sayısı genellikle Sayfa Yazma/sn sayısından çok daha büyüktür. Çünkü Pages Output/sn, sistem dosyası önbelleğinden değiştirilen veri sayfalarını da içerir. Ancak, hangi işlemin doğrudan sayfalama veya neden sorumlu olduğunu belirlemek her zaman kolay değildir.

## <a name="how-to-fix-violations"></a>İhlalleri düzeltme
 [Markalar](../profiling/marks-view.md) görünümüne gitmek için Hata Listesi penceresindeki iletiyi çift tıklatın. **Bellek\Sayfalar/sn** sütununa bakın. Sayfalama IO etkinliğinin diğerlerinden daha ağır olduğu program yürütmesinin belirli aşamaları olup olmadığını belirleyin.

 Bir ASP.NET uygulaması için profil verilerini bir yük testi senaryosunda topluyorsanız, ek fiziksel bellekle (veya RAM) yapılandırılan bir makinede yük testini yeniden çalıştırmayı deneyin.

 Algoritmaları gözden geçirerek ve String.Concat ve String.Substring gibi bellek yoğun API'lerden kaçınarak bellek ayırmalarını azaltmayı düşünün.
