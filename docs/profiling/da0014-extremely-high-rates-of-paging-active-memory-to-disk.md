---
title: DA0014 - Etkin belleği disk belleğine veya disk belleğine | Microsoft Docs
description: Profil oluşturma çalıştırması sırasında toplanan sistem performansı verileri, profil oluşturma çalıştırması boyunca diske gelen ve diskten çok yüksek bir disk belleği belleği oranı olduğunu gösterir.
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.performance.rules.DAMemoryBound
- vs.performance.DA0014
- vs.performance.14
- vs.performance.rules.DA0014
ms.assetid: a7fa3749-9191-437a-9331-9d917181e62f
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: ea42e94eab6c5da65e5e1d59e93f71680dea1500
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122131761"
---
# <a name="da0014-extremely-high-rates-of-paging-active-memory-to-disk"></a>DA0014: Çok yüksek oranda diske etkin bellek sayfalaması

|Öğe|Değer|
|-|-|
|Kural Kimliği|DA0014|
|Kategori|Bellek ve Disk Belleği|
|Profil oluşturma yöntemi|Tümü|
|İleti|Çok yüksek oranda diske etkin bellek diske disk belleği oluşuyor. Uygulamanız belleğe bağlı olabilir.|
|Kural türü|Uyarı|

 Örnekleme, .NET belleği veya kaynak musiki yöntemlerini kullanarak profil 25 örnek toplayan bu kuralı tetiklemeniz gerekir.

## <a name="cause"></a>Nedeni
 Profil oluşturma çalıştırması sırasında toplanan sistem performansı verileri, profil oluşturma çalıştırması boyunca diske gelen ve diskten çok yüksek bir disk belleği belleği oranı olduğunu gösterir. Bu düzeydeki disk belleği oranları genellikle uygulama performansını ve yanıt hızını etkiler. Algoritmaları gözden kullanarak bellek ayırmalarını azaltmayı göz önünde bulundurarak. Ayrıca, uygulamanın bellek gereksinimlerini de göz önünde bulundurabilirsiniz. daha fazla belleğe sahip bir bilgisayarda profil oluşturmayı yeniden çalıştırma.

## <a name="rule-description"></a>Kural açıklaması
 Diske aşırı disk belleği, fiziksel bellek yetersizliği neden olabilir. Disk belleği işlemlerinin disk belleği dosyasının bulunduğu fiziksel diskte baskın olması, diğer uygulama odaklı disk işlemlerini aynı diske yavaşlatır.

 Sayfalar genellikle diskten okunur veya toplu sayfalama işlemleriyle diske yazılır. Sayfa Çıkışı/sn sayısı, örneğin sayfa yazma/sn sayısından çok daha fazladır. Sayfalar Çıktı/sn, sistem dosyası önbelleğinden değiştirilen veri sayfalarını da içerir. Ancak, hangi sürecin disk belleğinden veya neden doğrudan sorumlu olduğunu belirlemek her zaman kolay değildir.

> [!NOTE]
> Bu kural, etkin bellek disk belleği düzeyleri çok yüksek bir hıza ulaştığında etkin olur. Disk belleği düzeyi önemli ancak aşırı değilken, [DA0017 bilgi kuralı:](../profiling/da0017-high-rates-of-paging-active-memory-to-disk.md) Bunun yerine diske etkin belleğin yüksek oranda diske atılıyor olması.

## <a name="how-to-fix-violations"></a>İhlalleri düzeltme
 İşaretler görünümüne gitmek için Hata Listesi penceresinde iletiye [çift](../profiling/marks-view.md) tıklayın. **Memory\Pages/sec sütununu** bulun. Disk belleği IO etkinliğinin diğerlerine göre daha ağır olduğu belirli program yürütme aşamaları olup olmadığını belirler.

 Bir yük testi senaryosunda bir ASP.NET uygulama için profil verileri topluyorsanız, yük testini ek fiziksel bellek (veya RAM) ile yapılandırılmış bir makinede yeniden çalıştırmayı deneyin.

 Algoritmaları yeniden değerlendirerek ve String.Concat ve String.Substring gibi yoğun bellek kullanımına sahip API'lerden kaçınarak bellek ayırmalarını azaltmayı göz önünde bulundurarak.
