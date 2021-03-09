---
title: DA0023-yüksek GC CPU süresi | Microsoft Docs
description: Profil oluşturma sırasında toplanan sistem performansı verileri, atık toplamada harcanan sürenin toplam uygulama işleme süresi ile karşılaştırıldığında önemli olduğunu gösterir.
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.performance.DA0023
- vs.performance.23
- vs.performance.rules.DA0023
ms.assetid: aba875fe-9cbc-418d-a2c4-6eb47519a5bb
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: eccf44528b18d43a97a5a9c202c72b59abbdf431
ms.sourcegitcommit: 8590cf6b3351e82827fd21159beefef0c02bf162
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2021
ms.locfileid: "102466085"
---
# <a name="da0023-high-gc-cpu-time"></a>DA0023: Yüksek GC CPU süresi

|Öğe|Değer|
|-|-|
|Kural kimliği|DA0023|
|Kategori|.NET Framework kullanımı|
|Profil oluşturma yöntemi|Tümü|
|İleti|GC 'de% Time oldukça yüksektir. Bu aşırı miktarda çöp toplama ek yükünün, uygulamanızın yanıt hızını etkileme göstergesi olabilir. Uygulamanızın daha iyi kullandığı bellek ayırma modelini anlamak için .NET bellek ayırma verilerini ve nesne yaşam süresi bilgilerini toplayabilirsiniz.|
|Kural türü|Bilgilendirici|

 Örnekleme, .NET belleği veya kaynak çekişme yöntemlerini kullanarak profil oluşturduğunuzda, bu kuralı tetiklemek için en az 10 örnek toplamanız gerekir.

## <a name="cause"></a>Nedeni
 Profil oluşturma sırasında toplanan sistem performansı verileri, atık toplamada harcanan sürenin toplam uygulama işleme süresi ile karşılaştırıldığında önemli olduğunu gösterir.

## <a name="rule-description"></a>Kural açıklaması
 Microsoft .NET ortak dil çalışma zamanı (CLR), uygulamanın artık kullandığı nesnelerden belleği geri kazanmak için çöp toplayıcı kullanan bir otomatik bellek yönetim mekanizması sağlar. Çöp toplayıcı, çok sayıda ayırmaların kısa süreli olduğu varsayımına bağlı olarak, oluşturma odaklı bir şekilde yapılır. Örneğin, yerel değişkenler kısa süreli olmalıdır. Yeni oluşturulan nesneler nesil 0 ' da (Gen 0) başlar ve sonra bir atık toplama çalıştırmasını sürdüren 1. nesil ve son olarak uygulama bunları kullanıyorsa 2. nesil 'e geçiş yapılır.

 Nesil 0 içindeki nesneler sıklıkla ve verimli bir şekilde toplanır. 1. nesil nesneler daha az ve daha az verimli bir şekilde toplanır. Son olarak, kuşak 2 ' deki uzun süreli nesneler daha az sıklıkta toplanmalıdır. Eksiksiz bir atık toplama çalıştırması olan 2. nesil koleksiyon, ayrıca en pahalı işlemdir.

 Bu kural, atık toplamada harcanan zaman miktarı Toplam uygulama işleme süresi ile karşılaştırıldığında önemli olduğunda ateşlenir.

> [!NOTE]
> Çöp toplamadan harcanan sürenin oranı Toplam uygulama işleme süresine göre çok fazla olduğunda, bu kural yerine [DA0024: AŞıRı GC CPU süresi](../profiling/da0024-excessive-gc-cpu-time.md) uyarısı ateşlenir.

## <a name="how-to-investigate-a-warning"></a>Uyarı araştırma
 Profil oluşturma verilerinin [Işaretler görünümüne](../profiling/marks-view.md) gitmek Için hatalar Listesi penceresinde iletiye çift tıklayın. GC sütununda **.NET CLR bellek \\ % zamanını** bulun. Yönetilen bellek çöp toplamanın yükünün diğer aşamalardan daha ağır olduğu, program yürütmesinin belirli aşamaları olup olmadığını belirleme. GC değerindeki% değerinin değerlerini, **# of Gen 0 koleksiyonlarında**, **Gen 1 koleksiyonlardan** oluşan #/ **Gen 2 koleksiyon** değerlerinin sayısı ile bildirilen çöp toplama hızına göre karşılaştırın.

 GC değerindeki% süresi, bir uygulamanın çöp toplama işlemini gerçekleştirirken harcadığı süreyi toplam işleme miktarına göre rapor etmeye çalışır. GC değerindeki% zamanının yüksek bir değeri bildirebildiği, ancak aşırı atık toplama nedeniyle olmadığı durumlar olduğunu unutmayın. GC değerindeki% zamanının hesaplanma şekli hakkında daha fazla bilgi için, MSDN 'de **Maonı 'Nin Web günlüğü** ' nin [farklı araçları-4 girişi Ile raporlanan performans verileri arasındaki farka](https://devblogs.microsoft.com/maoni/archive/difference-between-perf-data-reported-by-different-tools-4.aspx) bakın. Sayfa hataları oluşmakta veya uygulama çöp toplama sırasında makinede daha yüksek öncelikli iş tarafından önayarlanırsa, GC sayacında% süre bu ek gecikmeleri yansıtır.
