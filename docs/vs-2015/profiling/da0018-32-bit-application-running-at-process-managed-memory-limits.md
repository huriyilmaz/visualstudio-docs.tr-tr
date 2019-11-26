---
title: DA0018:32 bit uygulama, işlem yönetilen bellek sınırlarında çalışıyor | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.performance.18
- vs.performance.DA0018
- vs.performance.rules.DA0018
ms.assetid: 98eb2d96-f92f-42f9-915c-e5ac2330ffbf
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 67589a04b8f3c39e442b596a7a41981825bd5aa5
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74301110"
---
# <a name="da0018-32-bit-application-running-at-process-managed-memory-limits"></a>DA0018: 32 bitlik Uygulama işlem tarafından yönetilen bellek sınırlarında çalışıyor
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kural kimliği | DA0018 |  
| Kategori | Profil Oluşturma Araçları kullanımı |  
| Profil oluşturma yöntemi | Örnekleme |  
| İleti | Yönetilen bellek ayırmaları, 32 bitlik bir işlem için varsayılan sınıra yaklaşmıştır. Uygulamanız bellek ile bağlantılı olabilir. |  
| Kural türü | Uyarı |  
  
 Örnekleme, .NET belleği veya kaynak çekişme yöntemlerini kullanarak profil oluşturduğunuzda, bu kuralı tetiklemek için en az 10 örnek toplamanız gerekir.  
  
## <a name="cause"></a>Nedeni  
 Profil oluşturma işlemi sırasında toplanan sistem verileri, .NET Framework bellek yığınlarının, yönetilen yığınlardaki 32 bitlik bir işlemde ulaşabileceği en büyük boyutu approached gösterir. Bu en büyük boyut, varsayılan değerdir. Özel baytlar için ayrılabilecek işlem adres alanının Toplam miktarına bağlıdır. Bildirilen değer, profili oluşturulmuş işlem etkinken Heap 'ler için gözlenen en yüksek değerdir. .NET bellek profili oluşturma yöntemini kullanarak profil oluşturmayı yeniden düşünün ve yönetilen kaynakların uygulama tarafından kullanımını en iyi duruma getirme işlemini yapın.  
  
 Yönetilen yığınlardaki boyut varsayılan sınıra yaklaşımında, otomatik atık toplama işleminin daha sık çağrılması gerekebilir. Bu, bellek yönetiminin ek yükünü artırır.  
  
 Kural yalnızca 32 bit makinelerde çalışan 32 bitlik uygulamalar için ateşlenir.  
  
## <a name="rule-description"></a>Kural Tanımı  
 Microsoft .NET ortak dil çalışma zamanı (CLR), uygulamanın artık kullandığı nesnelerden belleği geri kazanmak için çöp toplayıcı kullanan bir otomatik bellek yönetim mekanizması sağlar. Çöp toplayıcı, çok sayıda ayırmaların kısa süreli olduğu varsayımına bağlı olarak, oluşturma odaklı bir şekilde yapılır. Örneğin, yerel değişkenler kısa süreli olmalıdır. Yeni oluşturulan nesneler nesil 0 ' da (Gen 0) başlar ve sonra bir atık toplama çalıştırmasını sürdüren 1. nesil ve son olarak uygulama bunları kullanıyorsa 2. nesil 'e geçiş yapılır.  
  
 85 KB 'den büyük olan yönetilen nesneler büyük nesne yığınında ayrılır. Bunlar, daha az sıklıkta çöp toplamaya ve daha küçük nesnelerden daha küçük nesnelere tabidir. büyük nesneler, daha kalıcı oldukları ve en sık ayrılan küçük nesneler ile kalıcı ve büyük nesneleri karıştırmanın yığının en kötü saçılması durumunda olduğu varsayıldığı için ayrı olarak yönetilir.  
  
 Yönetilen yığınların toplam boyutu varsayılan sınıra yaklaşıyorsa, bellek yönetiminin ek yükü genellikle uygulamanın yanıt hızını ve ölçeklenebilirliğini etkilemek için başlayabileceği noktaya kadar artar.  
  
## <a name="how-to-investigate-a-warning"></a>Uyarı araştırma  
 [İşaretler](../profiling/marks-view.md) görünümüne gitmek için hata Listesi penceresindeki iletiye çift tıklayın. Tüm Heap 'ler ve **Toplam kaydedilmiş bayt** SÜTUNLARıNDA **.net clr belleği\\# bayt** bulun. Yönetilen bellek ayırmanın diğer aşamalara göre daha ağır olduğu program yürütmesinin belirli aşamaları olup olmadığını belirleme. **Tüm Heap sütunlarındaki # bytes** değerlerini, **.NET CLR\\bellekte**bildirilen çöp toplama hızına ve bu durumda, yönetilen bellek ayırmaları deseninin çöp toplama oranını etkileyip etkilemediğini tespit etmek için .NET CLR belleği\\# of gen **1**koleksiyonlarının, .NET CLR hafıza **\\ve net 2 koleksiyon** sütunlarının sayısını karşılaştırın.  
  
 .NET Framework bir uygulamada, ortak dil çalışma zamanı, yönetilen yığınların toplam boyutunu, bir işlem adres alanının özel alan boyutunun en büyük boyutundan biraz daha az bir olacak şekilde sınırlandırır. 32 bit makinede çalışan 32 bitlik işlemler için 2 GB, işlem adres alanının özel bölümünün üst sınırını temsil eder. Yönetilen yığınların toplam boyutu varsayılan sınırına yaklaşımak üzere başladığında, bellek yönetiminin ek yükü artabilir ve uygulama performansı azalabilir.  
  
 Aşırı yönetilen bellek ek yükü bir sorun ise, şu seçeneklerden birini göz önünde bulundurun:  
  
- Uygulamanın yönetilen bellek kaynakları kullanımını iyileştirme  
  
   veya  
  
- 32 bitlik bir işlem için maksimum sanal bellek boyutundaki mimari kısıtlamalarını hafifetmek için gereken adımları alma  
  
  Uygulamanın yönetilen bellek kaynakları kullanımını iyileştirmek için, yönetilen bellek ayırma verilerini bir .NET bellek ayırma profil oluşturma çalıştırmasında toplayın. Uygulamanın bellek ayırma düzenlerini anlamak için [.net bellek verileri görünümleri](../profiling/dotnet-memory-data-views.md) raporlarını gözden geçirin.  
  
  Programın veri nesnelerinin neslin oluşturulması ve daha sonra geri kazanılmakta olduğunu öğrenmek için [nesne ömrü görünümünü](../profiling/object-lifetime-view.md) kullanın.  
  
  Bu ayırmalara neden olan yürütme yolunu öğrenmek için [ayırmalar görünümünü](../profiling/dotnet-memory-allocations-view.md) kullanın.  
  
  Çöp toplama performansını geliştirme hakkında daha fazla bilgi için MSDN Web sitesindeki .NET Framework Teknik makale, [çöp toplayıcı temelleri ve performans ipuçları](https://go.microsoft.com/fwlink/?LinkId=177946) bölümüne bakın.  
  
  Bir işlem adres alanının özel bölümünün boyutundaki sanal bellek kısıtlamalarından mimari rahatını kazanmak için, bu 32 bit işlemi 64 bit bir makinede çalıştırmayı deneyin.  64 bit makinede 32 bitlik bir işlem, 4 GB 'a kadar özel sanal bellek elde edebilir.  
  
  64 bit makinede çalışan 64 bitlik bir işlem, 8 TB 'a kadar sanal bellek elde edebilir. Yerel bir 64 bit uygulama olarak yürütmek üzere uygulamayı yeniden derlemeyi düşünün. Bu kural yalnızca bilgi amaçlıdır ve düzeltici eylem gerektirmeyebilir.
