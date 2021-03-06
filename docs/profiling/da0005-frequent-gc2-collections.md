---
description: 2. nesil atık toplamada yüksek sayıda .NET bellek nesnesi geri kazanılır.
title: DA0005-sık kullanılan kullanılan GC2 koleksiyonları | Microsoft Docs
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
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 73b24eba94791a9a24b80898fb7333665ed13caf
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102221034"
---
# <a name="da0005-frequent-gc2-collections"></a>DA0005: Sık kullanılan GC2 koleksiyonları

|Öğe|Değer|
|-|-|
|RuleId|DA0005|
|Kategori|.NET Framework kullanımı|
|Profil oluşturma yöntemi|.NET belleği|
|İleti|Nesnelerinizin birçoğu 2. nesil atık toplamada toplanır.|
|Mesaj türü|Uyarı|

## <a name="cause"></a>Nedeni
 2. nesil atık toplamada yüksek sayıda .NET bellek nesnesi geri kazanılır.

## <a name="rule-description"></a>Kural açıklaması
 Microsoft .NET ortak dil çalışma zamanı (CLR), uygulamanın artık kullandığı nesnelerden belleği geri kazanmak için çöp toplayıcı kullanan bir otomatik bellek yönetim mekanizması sağlar. Çöp toplayıcı, çok sayıda ayırmaların kısa süreli olduğu varsayımına bağlı olarak, oluşturma odaklı bir şekilde yapılır. Örneğin, yerel değişkenler kısa süreli olmalıdır. Yeni oluşturulan nesneler nesil 0 ' da (Gen 0) başlar ve sonra bir atık toplama çalıştırmasını sürdüren 1. nesil ve son olarak uygulama bunları kullanıyorsa 2. nesil 'e geçiş yapılır.

 Nesil 0 içindeki nesneler sık ve genellikle çok verimli bir şekilde toplanır. 1. nesil nesneler daha az ve daha az verimli bir şekilde toplanır. Son olarak, kuşak 2 ' deki uzun süreli nesneler daha az sıklıkta toplanmalıdır. Eksiksiz bir atık toplama çalıştırması olan 2. nesil koleksiyon, ayrıca en pahalı işlemdir.

 Bu kural, çok fazla 2. nesil atık toplama işlemi meydana geldiğinde ateşlenir. Çok fazla sayıda kısa süreli nesne, 1. kuşak ve daha sonra 2. nesil bir tam koleksiyonda toplanabiliyor ise, bellek yönetiminin maliyeti kolayca aşırı kullanılabilir hale gelebilir. Daha fazla bilgi için, MSDN Web sitesindeki Riko [maridın](/archive/blogs/ricom/mid-life-crisis) performans katmanını ' na bakın.

## <a name="how-to-investigate-a-warning"></a>Uyarı araştırma
 Uygulamanın bellek ayırma düzenlerini anlamak için [.net bellek verileri görünümleri](../profiling/dotnet-memory-data-views.md) raporlarını gözden geçirin. Programın veri nesnelerinin hangisinin 2. nesil ve sonra geri kazanılır olduğunu anlamak için [nesne ömrü görünümünü](../profiling/object-lifetime-view.md) kullanın. Bu ayırmalara neden olan yürütme yolunu öğrenmek için [ayırmalar görünümünü](../profiling/dotnet-memory-allocations-view.md) kullanın.

 Çöp toplama performansını geliştirme hakkında daha fazla bilgi için bkz. Microsoft Web sitesinde [çöp toplayıcı temelleri ve performans ipuçları](/previous-versions/dotnet/articles/ms973837(v=msdn.10)) . Otomatik atık toplama ek yükü hakkında daha fazla bilgi için bkz. [büyük nesne yığını kapsanmamış](/archive/msdn-magazine/2008/june/clr-inside-out-large-object-heap-uncovered).
