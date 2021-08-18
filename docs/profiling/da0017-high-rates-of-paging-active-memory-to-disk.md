---
title: DA0017-yüksek oranda diske etkin bellek sayfalaması | Microsoft Docs
description: Profil oluşturma çalıştırmasında toplanan sistem performansı verileri, profil oluşturma çalıştırmasında yüksek oranda diske ve diskten etkin bellek sayfalaması olduğunu gösterir.
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
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122093274"
---
# <a name="da0017-high-rates-of-paging-active-memory-to-disk"></a>DA0017: Yüksek oranda diske etkin bellek sayfalaması

|Öğe|Değer|
|-|-|
|Kural kimliği|DA0017|
|Kategori|Bellek ve disk belleği|
|Profil oluşturma yöntemi|Tümü|
|İleti|Yüksek oranda diske etkin bellek sayfalaması gerçekleşiyor. Uygulamanız bellek ile bağlantılı olabilir.|
|Kural türü|Bilgi|

 Örnekleme, .NET belleği veya kaynak çekişme yöntemlerini kullanarak profil oluşturduğunuzda, bu kuralı tetiklemek için en az 10 örnek toplamanız gerekir.

## <a name="cause"></a>Nedeni
 Profil oluşturma çalıştırmasında toplanan sistem performansı verileri, profil oluşturma çalıştırmasında yüksek oranda diske ve diskten etkin bellek sayfalaması olduğunu gösterir. Bu düzeydeki disk belleği ücretleri normalde uygulama performansını ve yanıt hızını etkiler. Algoritmaların yeniden gözden geçirerek bellek ayırmalarını azaltmayı göz önünde bulundurun. Ayrıca, uygulamanızın bellek gereksinimlerini dikkate almanız gerekebilir.

## <a name="rule-description"></a>Kural açıklaması

> [!NOTE]
> Bu bilgilendirme kuralı, etkin belleğin sayfalama düzeyleri önemli bir miktara ulaştığında ateşlenir. Son derece yüksek düzeyde bir sayfalama gerçekleştiğinde, uyarı kuralı [DA0014: çok yüksek oranda diske etkin bellek sayfalaması](../profiling/da0014-extremely-high-rates-of-paging-active-memory-to-disk.md) , bunun yerine başlatılır.

 Disk üzerinde aşırı sayfalama, fiziksel belleğin yetersizliğinden kaynaklanabilir. Sayfalama işlemleri disk belleği dosyasının bulunduğu fiziksel disk kullanıyorsa, diğer uygulama odaklı disk işlemlerini aynı diske düşürebilir.

 Sayfalar çoğunlukla diskten okur veya toplu sayfalama işlemlerinde diske yazılır. Çıkış/sn sayısı, genellikle sayfa yazma/sn sayısından çok daha büyük (örneğin,). Sayfa çıktısı/sn aynı zamanda sistem dosyası önbelleğinden değiştirilen veri sayfalarını da içerdiğinden. Ancak, sayfalama veya neden tarafından hangi işlemin doğrudan sorumlu olduğunu belirlenmesi her zaman kolay değildir.

## <a name="how-to-fix-violations"></a>İhlalleri çözme
 [İşaretler](../profiling/marks-view.md) görünümüne gitmek için hata Listesi penceresindeki iletiye çift tıklayın. **Bellek \ Sayfa/sn** sütununu bulun. Sayfalama GÇ etkinliğinin diğerlerinden daha ağır olduğu belirli program yürütme aşamaları olup olmadığını belirleme.

 yük testi senaryosunda bir ASP.NET uygulama için profil verileri topıyorsanız, yük testini ek fiziksel bellekle (veya RAM) yapılandırılmış bir makinede yeniden çalıştırmayı deneyin.

 Algoritmaları yeniden düzenleyerek ve String. Concat ve String. Substring gibi bellek kullanımı yoğun API 'lerden kaçınarak bellek ayırmalarını azaltmayı göz önünde bulundurun.
