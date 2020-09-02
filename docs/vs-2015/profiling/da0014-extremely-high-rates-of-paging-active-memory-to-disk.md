---
title: 'DA0014: çok yüksek oranda diske etkin bellek sayfalaması | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.performance.rules.DAMemoryBound
- vs.performance.DA0014
- vs.performance.14
- vs.performance.rules.DA0014
ms.assetid: a7fa3749-9191-437a-9331-9d917181e62f
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: dbf391f96cd21f0c473589d4992083963ff65d55
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64813396"
---
# <a name="da0014-extremely-high-rates-of-paging-active-memory-to-disk"></a>DA0014: Çok yüksek oranda diske etkin bellek sayfalaması
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kural kimliği | DA0014 |  
| Kategori | Bellek ve sayfalama |  
| Profil oluşturma yöntemi | Tümü |  
| İleti | Son derece yüksek oranda diske etkin bellek sayfalaması gerçekleşiyor. Uygulamanız bellek ile bağlantılı olabilir. |  
| Kural türü | Uyarı |  
  
 Örnekleme, .NET belleği veya kaynak çekişme yöntemlerini kullanarak profil oluşturduğunuzda, bu kuralı tetiklemek için en az 25 örnek toplamanız gerekir.  
  
## <a name="cause"></a>Nedeni  
 Profil oluşturma çalıştırmasında toplanan sistem performansı verileri, profil oluşturma çalıştırmasının tamamında son derece yüksek oranda disk belleği üzerinde etkin bellek olduğunu gösterir. Bu düzeydeki disk belleği ücretleri genellikle uygulama performansını ve yanıt hızını etkiler. Algoritmaların yeniden gözden geçirerek bellek ayırmalarını azaltmayı göz önünde bulundurun. Ayrıca, uygulamanızın bellek gereksinimlerini dikkate almanız gerekebilir. daha fazla belleğe sahip bir bilgisayarda profil oluşturma yeniden çalıştırılıyor.  
  
## <a name="rule-description"></a>Kural Tanımı  
 Disk üzerinde aşırı sayfalama, fiziksel belleğin yetersizliğinden kaynaklanabilir. Sayfalama işlemleri disk belleği dosyasının bulunduğu fiziksel disk kullanıyorsa, diğer uygulama odaklı disk işlemlerini aynı diske düşürebilir.  
  
 Genellikle, sayfalar diskten okunmakta veya toplu sayfalama işlemlerinde diske yazılır. Çıkış/sn sayısı, örneğin sayfa yazma/sn sayısından çok daha büyük. Sayfa çıktısı/sn aynı zamanda sistem dosyası önbelleğinden değiştirilen veri sayfalarını da içerdiğinden. Ancak, sayfalama veya neden tarafından hangi işlemin doğrudan sorumlu olduğunu belirlenmesi her zaman kolay değildir.  
  
> [!NOTE]
> Bu kural, etkin belleğin sayfalama düzeyleri çok yüksek bir hıza ulaştığında ateşlenir. Sayfalama düzeyi önemli olduğunda, ancak aşırı olmasa da bilgilendirme kuralı [DA0017: yüksek oranda diske etkin bellek sayfalaması](../profiling/da0017-high-rates-of-paging-active-memory-to-disk.md) , bunun yerine.  
  
## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?  
 [İşaretler](../profiling/marks-view.md) görünümüne gitmek için hata Listesi penceresindeki iletiye çift tıklayın. **Bellek \ Sayfa/sn** sütununu bulun. Sayfalama GÇ etkinliğinin diğerlerinden daha ağır olduğu belirli program yürütme aşamaları olup olmadığını belirleme.  
  
 Yük testi senaryosunda bir ASP.NET uygulamasının profil verilerini topıyorsanız, yük testini ek fiziksel bellekle (veya RAM) yapılandırılmış bir makinede yeniden çalıştırmayı deneyin.  
  
 Algoritmaları yeniden düzenleyerek ve String. Concat ve String. Substring gibi bellek kullanımı yoğun API 'lerden kaçınarak bellek ayırmalarını azaltmayı göz önünde bulundurun.
