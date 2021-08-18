---
title: DA0024 - Aşırı GC CPU Süresi | Microsoft Docs
description: Profil oluşturma sırasında toplanan sistem performansı verileri, atık toplamada harcanan sürenin toplam uygulama işleme süresine kıyasla aşırı yüksek olduğunu gösterir.
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.performance.DA0024
- vs.performance.24
- vs.performance.rules.DA0024
ms.assetid: 228872da-77d0-4da5-b455-ac57fb1867c9
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 08f60c3c5e642c46394d44156d72548c1e35c98a
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122131748"
---
# <a name="da0024-excessive-gc-cpu-time"></a>DA0024: Aşırı GC CPU süresi

|Öğe|Değer|
|-|-|
|Kural Kimliği|DA0024|
|Kategori|.NET Framework Kullanım|
|Profil oluşturma yöntemi|Tümü|
|İleti|GC'de % Süre çok yüksektir. Aşırı miktarda çöp toplama yükü vardır.|
|Kural türü|Uyarı|

 Örnekleme, .NET belleği veya kaynak musiki yöntemlerini kullanarak profil 10 örnek toplayan bu kuralı tetiklemeniz gerekir.

## <a name="cause"></a>Nedeni
 Profil oluşturma sırasında toplanan sistem performansı verileri, atık toplamada harcanan sürenin toplam uygulama işleme süresine kıyasla aşırı yüksek olduğunu gösterir.

## <a name="rule-description"></a>Kural açıklaması
 Yaygın Microsoft .NET çalışma zamanı (CLR), uygulamanın artık kullanmama durumuna sahip nesnelerden belleği geri alan bir atık toplayıcı kullanan otomatik bir bellek yönetimi mekanizması sağlar. Atık toplayıcı, çok sayıda ayırmanın kısa süreli olduğu varsayımı üzerine oluşturma odaklıdır. Örneğin yerel değişkenler kısa süreli olmalı. Yeni oluşturulan nesneler nesil 0'da (0. nesil) başlar ve bir çöp toplama çalıştırması çalıştırılana kadar hayatta kalarak 1. nesile ilerler ve uygulama hala bunları kullanıyorsa son olarak 2. nesile geçişler.

 Nesil 0'daki nesneler sıklıkla ve genellikle çok verimli bir şekilde toplanır. Nesil 1'de nesneler daha az sıklıkta ve daha az verimli bir şekilde toplanır. Son olarak, nesil 2'de uzun süreli nesneler daha az sıklıkta toplanabilir. Tam çöp toplama çalıştırması olan 2. nesil toplama da en pahalı işlemdir.

 Bu kural, atık toplamada harcanan sürenin toplam uygulama işleme süresine kıyasla aşırı yüksek olmasıyla ortaya çıkan bir durumdur.

> [!NOTE]
> Atık toplamada harcanan sürenin oranı, toplam uygulama işleme süresine kıyasla önemli ancak aşırı değilken, bu kural yerine [DA0023: Yüksek GC CPU](../profiling/da0023-high-gc-cpu-time.md) süresi uyarısı ortaya çıktı.

## <a name="how-to-investigate-a-warning"></a>Uyarıyı araştırma
 Profil oluşturma verilerinin İşaretler Görünümüne gitmek için Hatalar Listesi [penceresindeki iletiye](../profiling/marks-view.md) çift tıklayın. GC sütununda **.NET CLR Bellek \\ % Saat'i** bulun. Yönetilen bellek çöp toplama yükünün diğer aşamalardan daha ağır olduğu belirli program yürütme aşamaları olup olmadığını belirler. GC değerindeki % Saat değerlerini **2.** Nesil Koleksiyon değerlerinin **0.** Nesil Koleksiyonları , **1.** Nesil Koleksiyonlar , # ile bildirilen çöp toplama oranıyla karşılaştırın.

 GC değerindeki % Time değeri, bir uygulamanın çöp toplama işlemini toplam işlem miktarıyla orantılı olarak gerçekleştirmek için harcadığı süre miktarını bildirmeye çalışır. GC değerindeki % Time değerinin yüksek bir değer raporlayanaları olduğunu, ancak bunun aşırı çöp toplama nedeniyle olmadığının farkında olmak gerekir. GC değerindeki %Time değerinin nasıl hesaplandığı hakkında daha fazla bilgi için **MSDN'de Maoni'nin Weblog'un** Farklı Araçlar tarafından Bildirilen Perf Verileri Arasındaki Fark [- 4](https://devblogs.microsoft.com/maoni/archive/difference-between-perf-data-reported-by-different-tools-4.aspx) girişine bakın. Sayfa hataları oluşuyorsa veya uygulama atık toplama sırasında makinede diğer yüksek öncelikli iş tarafından önceden boşaltılırsa, GC sayacında % Süresi bu ek gecikmeleri yansıtacak.
