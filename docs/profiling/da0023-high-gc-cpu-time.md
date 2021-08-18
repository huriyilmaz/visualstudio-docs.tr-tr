---
title: DA0023 - Yüksek GC CPU süresi | Microsoft Docs
description: Profil oluşturma sırasında toplanan sistem performansı verileri, çöp toplamada harcanan sürenin toplam uygulama işleme süresine kıyasla önemli olduğunu gösterir.
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
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 859c0cb12e76b5e6a12235a51e01efdc8449e207
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122131781"
---
# <a name="da0023-high-gc-cpu-time"></a>DA0023: Yüksek GC CPU süresi

|Öğe|Değer|
|-|-|
|Kural Kimliği|DA0023|
|Kategori|.NET Framework Kullanım|
|Profil oluşturma yöntemi|Tümü|
|İleti|GC'de % süresi oldukça yüksektir. Aşırı miktarda çöp toplama ek yükü göstergesi, uygulamanıza yanıt verme hızını etkiliyor olabilir. Uygulamanıza daha iyi kullandığı bellek ayırma desenini anlamak için .NET bellek ayırma verileri ve nesne yaşam süresi bilgilerini topabilirsiniz.|
|Kural türü|Bilgilendirici|

 Örnekleme, .NET belleği veya kaynak musiki yöntemlerini kullanarak profil 10 örnek toplayan bu kuralı tetiklemeniz gerekir.

## <a name="cause"></a>Nedeni
 Profil oluşturma sırasında toplanan sistem performansı verileri, çöp toplamada harcanan sürenin toplam uygulama işleme süresine kıyasla önemli olduğunu gösterir.

## <a name="rule-description"></a>Kural açıklaması
 Yaygın Microsoft .NET çalışma zamanı (CLR), uygulamanın artık kullanmama durumuna sahip nesnelerden belleği geri alan bir atık toplayıcı kullanan otomatik bir bellek yönetimi mekanizması sağlar. Atık toplayıcı, çok sayıda ayırmanın kısa süreli olduğu varsayımı üzerine oluşturma odaklıdır. Örneğin yerel değişkenler kısa süreli olmalı. Yeni oluşturulan nesneler nesil 0'da (0. nesil) başlar ve bir çöp toplama çalıştırması çalıştırılana kadar hayatta kalarak 1. nesile ilerler ve uygulama hala bunları kullanıyorsa son olarak 2. nesile geçişler.

 Nesil 0'daki nesneler sık ve verimli bir şekilde toplanır. Nesil 1'de nesneler daha az sıklıkta ve daha az verimli bir şekilde toplanır. Son olarak, nesil 2'de uzun süreli nesneler daha az sıklıkta toplanabilir. Tam çöp toplama çalıştırması olan 2. nesil toplama da en pahalı işlemdir.

 Bu kural, çöp toplamada harcanan sürenin toplam uygulama işleme süresiyle karşılaştırıldığında önemli olduğu zamanları karşılar.

> [!NOTE]
> Atık toplamada harcanan sürenin oranı, toplam uygulama işleme süresiyle karşılaştırıldığında aşırı olduğunda, [DA0024: Aşırı GC CPU](../profiling/da0024-excessive-gc-cpu-time.md) Süresi uyarısı bu kural yerine sıcalık olur.

## <a name="how-to-investigate-a-warning"></a>Uyarıyı araştırma
 Profil oluşturma verilerinin İşaretler Görünümüne gitmek için Hatalar Listesi [penceresindeki iletiye](../profiling/marks-view.md) çift tıklayın. GC sütununda **.NET CLR Bellek \\ % Saat'i** bulun. Yönetilen bellek çöp toplama yükünün diğer aşamalardan daha ağır olduğu belirli program yürütme aşamaları olup olmadığını belirler. GC değerindeki % Saat değerlerini **2.** Nesil Koleksiyon değerlerinin **0.** Nesil Koleksiyonları , **1.** Nesil Koleksiyonlar , # ile bildirilen çöp toplama oranıyla karşılaştırın.

 GC değerindeki % Time değeri, bir uygulamanın çöp toplama işlemini toplam işlem miktarıyla orantılı olarak gerçekleştirmek için harcadığı süre miktarını bildirmeye çalışır. GC değerindeki % Saat değerinin yüksek bir değer raporlayanaları olduğunu ama bunun aşırı çöp toplama nedeniyle olmadığının farkında olmak gerekir. GC değerindeki %Time değerinin nasıl hesaplandığı hakkında daha fazla bilgi için **MSDN'de Maoni'nin Weblog'un** Farklı Araçlar tarafından Bildirilen Perf Verileri Arasındaki Fark [- 4](https://devblogs.microsoft.com/maoni/archive/difference-between-perf-data-reported-by-different-tools-4.aspx) girişine bakın. Sayfa hataları oluşuyorsa veya uygulama atık toplama sırasında makinede diğer yüksek öncelikli iş tarafından önsese, GC sayacında % Süresi bu ek gecikmeleri yansıtacak.
