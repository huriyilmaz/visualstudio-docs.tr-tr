---
title: DA0018 - 32 bit Uygulama, işlem tarafından yönetilen bellek sınırlarında | Microsoft Docs
description: Profil oluşturma çalıştırması sırasında toplanan sistem verileri, .NET Framework yığınların 32 bitlik bir işlemde ulaşacak en büyük boyuta yaklaştığını gösterir.
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.performance.18
- vs.performance.DA0018
- vs.performance.rules.DA0018
ms.assetid: 98eb2d96-f92f-42f9-915c-e5ac2330ffbf
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: e407b4273bceb7d8df7478fb518bf952bf5d822c
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126637142"
---
# <a name="da0018-32-bit-application-running-at-process-managed-memory-limits"></a>DA0018: İşlem tarafından yönetilen bellek sınırlarında çalışan 32 bit uygulama

|Öğe|Değer|
|-|-|
|Kural Kimliği|DA0018|
|Kategori|Profil Oluşturma Araçları Kullanımı|
|Profil oluşturma yöntemi|Örnekleme|
|İleti|32 bit işlem için varsayılan sınıra yaklaşan yönetilen bellek ayırmaları. Uygulamanız belleğe bağlı olabilir.|
|Kural türü|Uyarı|

 Örnekleme, .NET belleği veya kaynak musiki yöntemlerini kullanarak profil 7'niz olduğunda, bu kuralı tetiklemek için en az 10 örnek toplamanız gerekir.

## <a name="cause"></a>Nedeni
 Profil oluşturma çalıştırması sırasında toplanan sistem verileri, .NET Framework yığınların 32 bitlik bir işlemde ulaşacak en büyük boyuta yaklaştığını gösterir. Bu en büyük boyut varsayılan değerdir. Özel baytlar için ayırabilirsiniz işlem adres alanı toplam miktarını temel alan. Bildirilen değer, profili yapılan işlem etkinken yığınların gözlemlenen en yüksek değeridir. .NET bellek profili oluşturma yöntemini kullanarak ve uygulama tarafından yönetilen kaynakların kullanımını en iyi duruma getirerek profil oluşturmayı yeniden göz önünde bulundurabilirsiniz.

 Yönetilen Yığınların boyutu varsayılan sınıra yaklaştığında, otomatik çöp toplama işleminin daha sık çağrılmış olması gerekir. Bu, bellek yönetimi yükünü artırır.

 Kural yalnızca 32 bit makinelerde çalışan 32 bit uygulamalar için kullanılmaktadır.

## <a name="rule-description"></a>Kural açıklaması
 Yaygın Microsoft .NET çalışma zamanı (CLR), uygulamanın artık kullanmama durumuna sahip nesnelerden belleği geri alan bir atık toplayıcı kullanan otomatik bir bellek yönetim mekanizması sağlar. Atık toplayıcı, çok sayıda ayırmanın kısa süreli olduğu varsayımı üzerine oluşturma odaklıdır. Örneğin yerel değişkenler kısa süreli olmalı. Yeni oluşturulan nesneler nesil 0'da (0. nesil) başlar ve bir çöp toplama çalıştırması çalıştırılana kadar hayatta kalarak 1. nesile ilerler ve uygulama hala bunları kullanıyorsa son olarak 2. nesile geçişler.

 85 KB'den büyük yönetilen nesneler, daha küçük nesnelere göre daha az sıklıkta çöp toplama ve sıkıştırmaya tabi olan Büyük Nesne Yığınında ayrılır. büyük nesneler daha kalıcı olduğu varsayılır ve kalıcı ve büyük nesneleri sık ayrılan küçük nesnelerle karıştırmak yığının en kötü döküm parçalanmasına neden olabilir çünkü ayrı yönetilir.

 Yönetilen yığınların toplam boyutu varsayılan sınıra yaklaştıkça, bellek yönetimi yükü genellikle uygulamanın yanıt hızını ve ölçeklenebilirliğini etkilemeye başlanabilir noktaya kadar artar.

## <a name="how-to-investigate-a-warning"></a>Uyarıyı araştırma
 İşaretler görünümüne gitmek için Hata Listesi penceresinde iletiye [çift](../profiling/marks-view.md) tıklayın. Tüm **Yığınlarda .NET CLR Bellek \\ # Bayt sayısı ve** # Toplam işlenen bayt **sütunlarını** bulun. Yönetilen bellek ayırmanın diğer aşamalardan daha ağır olduğu belirli program yürütme aşamaları olup olmadığını belirler. Yönetilen bellek ayırma desenlerinin çöp toplama oranını etkip etkilemeyeceğini belirlemek için tüm Yığınlar sütunundaki **#** Bayt değerlerini **\\ 0.** Nesil Koleksiyonlar , **.NET CLR Bellek # \\ 1.** Nesil Koleksiyonlar ve **.NET CLR Bellek \\ # 2.** Nesil Koleksiyonlar sütunlarında bildirilen çöp toplama oranıyla karşılaştırın.

 Bir .NET Framework ortak dil çalışma zamanı, yönetilen yığınların toplam boyutunu bir işlem adres alanı özel alan bölümünün en büyük boyutunun bir yarısından biraz daha az olacak şekilde sınırlar. 32 bit makinede çalışan 32 bit işlemler için 2 GB, işlem adres alanı özel bölümünün üst sınırını temsil eder. Yönetilen Yığınların toplam boyutu varsayılan sınırına yaklaşmaya başladığından, bellek yönetimi yükü artabilir ve uygulama performansı düşebilir.

 Aşırı yönetilen bellek ek yükü bir sorunsa şu seçeneklerden birini göz önünde önünden belirleyin:

- uygulamanın yönetilen bellek kaynakları kullanımını iyileştirme

   -veya-

- 32 bit işlem için en büyük sanal bellek boyutu üzerinde mimari kısıtlamaları hafifletmek için gerekli adımların atılması

  Uygulamanın yönetilen bellek kaynakları kullanımını iyileştirmek için, bir .NET Bellek Ayırma profil oluşturma çalıştırması içinde yönetilen bellek ayırma verilerini toplayın. Uygulamanın [bellek ayırma desenini anlamak](../profiling/dotnet-memory-data-views.md) için .NET Bellek Veri Görünümleri raporlarını gözden geçirme.

  Programın [veri nesnelerinden](../profiling/object-lifetime-view.md) hangilerinin nesil içinde hayatta kalarak daha sonra geri alınarak geri alınarak olduğunu belirlemek için Nesne Yaşam Süresi Görünümünü kullanın.

  Bu [ayırmalara neden](../profiling/dotnet-memory-allocations-view.md) olan yürütme yolunu belirlemek için Ayırmalar Görünümünü kullanın.

  Çöp toplama performansını geliştirme hakkında daha fazla bilgi için [](/previous-versions/dotnet/articles/ms973837(v=msdn.10)) MSDN Web .NET Framework Çöp Toplayıcısı Temel Bilgileri ve Performans İpuçları teknik makalesine bakın.

  Bir işlem adres alanı özel bölümünün boyutuyla ilgili sanal bellek kısıtlamalarından mimari açıdan yardım almak için bu 32 bit işlemi 64 bit makinede çalıştırmayı deneyin.  64 bit makinede 32 bit işlem 4 GB'a kadar özel sanal bellek edinebiliyor.

  64 bit makinede çalışan 64 bit işlem 8 TB'a kadar sanal bellek elde ediyor olabilir. Yerel bir 64 bit uygulama olarak yürütmek için uygulamayı yeniden derlemeyi göz önünde bulundurabilirsiniz. Bu kural yalnızca bilgi içindir ve düzeltici eylem gerektirmeyebilirsiniz.
