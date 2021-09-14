---
title: DA0017 - Yüksek oranda etkin belleği disk belleğine | Microsoft Docs
description: Profil oluşturma çalıştırması sırasında toplanan sistem performansı verileri, profil oluşturma çalıştırması boyunca diske gelen ve diskten yüksek oranda disk belleği etkin belleği olduğunu gösterir.
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.performance.17
- vs.performance.rules.DA0017
- vs.performance.DA0017
ms.assetid: 01011eec-5930-43b3-980d-2cb01e2ca7f6
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 6c55c58cbe214b3411ab22e8543763c7f0310776
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126637134"
---
# <a name="da0017-high-rates-of-paging-active-memory-to-disk"></a>DA0017: Yüksek oranda diske etkin bellek sayfalaması

|Öğe|Değer|
|-|-|
|Kural Kimliği|DA0017|
|Kategori|Bellek ve Disk Belleği|
|Profil oluşturma yöntemi|Tümü|
|İleti|Yüksek oranda diske etkin bellek diske disk belleği oluşuyor. Uygulamanız belleğe bağlı olabilir.|
|Kural türü|Bilgi|

 Örnekleme, .NET belleği veya kaynak musiki yöntemlerini kullanarak profil 7'niz olduğunda, bu kuralı tetiklemek için en az 10 örnek toplamanız gerekir.

## <a name="cause"></a>Nedeni
 Profil oluşturma çalıştırması sırasında toplanan sistem performansı verileri, profil oluşturma çalıştırması boyunca diske gelen ve diskten yüksek oranda disk belleği etkin belleği olduğunu gösterir. Bu düzeydeki disk belleği hızları normalde uygulama performansını ve yanıt hızını etkiler. Algoritmaları gözden kullanarak bellek ayırmalarını azaltmayı göz önünde bulundurarak. Ayrıca, uygulamanın bellek gereksinimlerini de göz önünde bulundurabilirsiniz.

## <a name="rule-description"></a>Kural açıklaması

> [!NOTE]
> Bu bilgi kuralı, etkin bellek disk belleği düzeyleri önemli bir miktara ulaştığında etkin olur. Çok yüksek bir disk belleği düzeyi [oluştuğunda, DA0014 uyarı kuralı:](../profiling/da0014-extremely-high-rates-of-paging-active-memory-to-disk.md) Bunun yerine etkin belleği diske çok yüksek oranda diske aşırı yüksek oranda diske aşırı yüksek oranda yüksek oranda diske yükleme oranı çok yüksek olur.

 Diske aşırı disk belleği, fiziksel bellek yetersizliği neden olabilir. Disk belleği işlemlerinin disk belleği dosyasının bulunduğu fiziksel diskte baskın olması, diğer uygulama odaklı disk işlemlerini aynı diske yavaşlatır.

 Sayfalar genellikle diskten okunur veya toplu sayfalama işlemleriyle diske yazılır. Örneğin, Sayfa Çıkışı/sn sayısı genellikle Sayfa Yazma/sn sayısından çok daha büyüktür. Sayfalar Çıktı/sn, sistem dosyası önbelleğinden değiştirilen veri sayfalarını da içerir. Ancak, hangi sürecin disk belleğinden veya neden doğrudan sorumlu olduğunu belirlemek her zaman kolay değildir.

## <a name="how-to-fix-violations"></a>İhlalleri düzeltme
 İşaretler görünümüne gitmek için Hata Listesi penceresinde iletiye [çift](../profiling/marks-view.md) tıklayın. **Memory\Pages/sec sütununu** bulun. Disk belleği IO etkinliğinin diğerlerine göre daha ağır olduğu belirli program yürütme aşamaları olup olmadığını belirler.

 Bir yük testi senaryosunda bir ASP.NET uygulama için profil verileri topluyorsanız, yük testini ek fiziksel bellek (veya RAM) ile yapılandırılmış bir makinede yeniden çalıştırmayı deneyin.

 Algoritmaları yeniden değerlendirerek ve String.Concat ve String.Substring gibi yoğun bellek kullanımına sahip API'lerden kaçınarak bellek ayırmalarını azaltmayı göz önünde bulundurarak.
