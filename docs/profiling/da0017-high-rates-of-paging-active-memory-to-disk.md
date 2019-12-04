---
title: 'DA0017: yüksek oranda diske etkin bellek sayfalaması | Microsoft Docs'
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
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74779395"
---
# <a name="da0017-high-rates-of-paging-active-memory-to-disk"></a>DA0017: Yüksek oranda diske etkin bellek sayfalaması gerçekleşiyor.

|||
|-|-|
|Kural Kimliği|DA0017|
|Kategori|Bellek ve disk belleği|
|Profil oluşturma yöntemi|Tümü|
|İleti|Yüksek oranda diske etkin bellek sayfalaması gerçekleşiyor. Uygulamanız bellek ile bağlantılı olabilir.|
|Kural türü|Bilgisi|

 Örnekleme, .NET belleği veya kaynak çekişme yöntemlerini kullanarak profil oluşturduğunuzda, bu kuralı tetiklemek için en az 10 örnek toplamanız gerekir.

## <a name="cause"></a>Sebep
 Profil oluşturma çalıştırmasında toplanan sistem performansı verileri, profil oluşturma çalıştırmasında yüksek oranda diske ve diskten etkin bellek sayfalaması olduğunu gösterir. Bu düzeydeki disk belleği ücretleri normalde uygulama performansını ve yanıt hızını etkiler. Algoritmaların yeniden gözden geçirerek bellek ayırmalarını azaltmayı göz önünde bulundurun. Ayrıca, uygulamanızın bellek gereksinimlerini dikkate almanız gerekebilir.

## <a name="rule-description"></a>Kural açıklaması

> [!NOTE]
> Bu bilgilendirme kuralı, etkin belleğin sayfalama düzeyleri önemli bir miktara ulaştığında ateşlenir. Son derece yüksek düzeyde bir sayfalama gerçekleştiğinde, uyarı kuralı [DA0014: çok yüksek oranda diske etkin bellek sayfalaması](../profiling/da0014-extremely-high-rates-of-paging-active-memory-to-disk.md) , bunun yerine başlatılır.

 Disk üzerinde aşırı sayfalama, fiziksel belleğin yetersizliğinden kaynaklanabilir. Sayfalama işlemleri disk belleği dosyasının bulunduğu fiziksel disk kullanıyorsa, diğer uygulama odaklı disk işlemlerini aynı diske düşürebilir.

 Sayfalar çoğunlukla diskten okur veya toplu sayfalama işlemlerinde diske yazılır. Çıkış/sn sayısı, genellikle sayfa yazma/sn sayısından çok daha büyük (örneğin,). Sayfa çıktısı/sn aynı zamanda sistem dosyası önbelleğinden değiştirilen veri sayfalarını da içerdiğinden. Ancak, sayfalama veya neden tarafından hangi işlemin doğrudan sorumlu olduğunu belirlenmesi her zaman kolay değildir.

## <a name="how-to-fix-violations"></a>İhlalleri çözme
 [İşaretler](../profiling/marks-view.md) görünümüne gitmek için hata Listesi penceresindeki iletiye çift tıklayın. **Bellek \ Sayfa/sn** sütununu bulun. Sayfalama GÇ etkinliğinin diğerlerinden daha ağır olduğu belirli program yürütme aşamaları olup olmadığını belirleme.

 Yük testi senaryosunda bir ASP.NET uygulamasının profil verilerini topıyorsanız, yük testini ek fiziksel bellekle (veya RAM) yapılandırılmış bir makinede yeniden çalıştırmayı deneyin.

 Algoritmaları yeniden düzenleyerek ve String. Concat ve String. Substring gibi bellek kullanımı yoğun API 'lerden kaçınarak bellek ayırmalarını azaltmayı göz önünde bulundurun.
