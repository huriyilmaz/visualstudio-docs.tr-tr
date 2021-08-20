---
description: Nesil 2 çöp toplamada çok sayıda .NET bellek nesnesi geri istenıyor.
title: DA0005 - Sık kullanılan GC2 koleksiyonları | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.performance.DA0005
- vs.performance.rules.DAManyGC2Collections
- vs.performance.5
- vs.performance.rules.DA0005
ms.assetid: 8d3f267c-8a74-4cf4-91a5-0b06a76dc2bd
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: b2e98e7212a1ed5441b2c1ccc779f9e5afff20ff
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122093287"
---
# <a name="da0005-frequent-gc2-collections"></a>DA0005: Sık kullanılan GC2 koleksiyonları

|Öğe|Değer|
|-|-|
|RuleId|DA0005|
|Kategori|.NET Framework Kullanım|
|Profil oluşturma yöntemi|.NET Belleği|
|İleti|Nesnelerinizin çoğu nesil 2 çöp toplamada toplanıyor.|
|Mesaj türü|Uyarı|

## <a name="cause"></a>Nedeni
 Nesil 2 çöp toplamada çok sayıda .NET bellek nesnesi geri istenıyor.

## <a name="rule-description"></a>Kural açıklaması
 Ortak Microsoft .NET çalışma zamanı (CLR), uygulamanın artık kullanmayacağı nesnelerden belleği geri alan bir atık toplayıcı kullanan otomatik bir bellek yönetim mekanizması sağlar. Atık toplayıcı, çok sayıda ayırmanın kısa süreli olduğu varsayımı üzerine oluşturma odaklıdır. Örneğin yerel değişkenler kısa süreli olmalı. Yeni oluşturulan nesneler nesil 0'da (0. nesil) başlar ve bir çöp toplama çalıştırması çalıştırılana kadar hayatta kalarak 1. nesile ilerler ve uygulama hala bunları kullanıyorsa son olarak 2. nesile geçişler.

 Nesil 0'daki nesneler sıklıkla ve genellikle çok verimli bir şekilde toplanır. Nesil 1'de nesneler daha az sıklıkta ve daha az verimli bir şekilde toplanır. Son olarak, nesil 2'de uzun süreli nesneler daha az sıklıkta toplanabilir. Tam çöp toplama çalıştırması olan 2. nesil toplama da en pahalı işlemdir.

 Bu kural, orantılı olarak çok fazla nesil 2 çöp toplaması meydana geldiğinde sızıyor. Çok fazla sayıda görece kısa süreli nesne 1. nesil koleksiyonda hayatta kalırsa ancak 2. nesil tam koleksiyonda tolere edilebilirse, bellek yönetiminin maliyeti kolayca aşırıya inebilir. Daha fazla bilgi [](/archive/blogs/ricom/mid-life-crisis) için MSDN Web sitesinde, Mariani'nin Performans Tidbit'leri ile ilgili Orta yaş kriz gönderisine bakın.

## <a name="how-to-investigate-a-warning"></a>Uyarıyı araştırma
 Uygulamanın [bellek ayırma desenini](../profiling/dotnet-memory-data-views.md) anlamak için .NET Bellek Veri Görünümleri raporlarını gözden geçirme. Programın [veri nesnelerinden hangilerinin](../profiling/object-lifetime-view.md) 2. nesilde hayatta kalarak daha sonra geri alınarak geri alınarak olduğunu belirlemek için Nesne Yaşam Süresi Görünümünü kullanın. Bu [ayırmalara neden](../profiling/dotnet-memory-allocations-view.md) olan yürütme yolunu belirlemek için Ayırmalar Görünümünü kullanın.

 Atık toplama performansını geliştirme hakkında daha fazla bilgi için Microsoft Web sitesinde Atık Toplayıcı temel bilgileri [ve](/previous-versions/dotnet/articles/ms973837(v=msdn.10)) Performans İpuçları makalesine bakın. Otomatik çöp toplamanın ek yükü hakkında bilgi için bkz. [Büyük Nesne Yığını Bulundu.](/archive/msdn-magazine/2008/june/clr-inside-out-large-object-heap-uncovered)
