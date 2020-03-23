---
title: 'DA0018: 32 bit Uygulama işlem yönetilen bellek sınırları | Microsoft Dokümanlar'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.18
- vs.performance.DA0018
- vs.performance.rules.DA0018
ms.assetid: 98eb2d96-f92f-42f9-915c-e5ac2330ffbf
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: d7bebd25f499131b4beda109ebb9ac468c2435b1
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74780071"
---
# <a name="da0018-32-bit-application-running-at-process-managed-memory-limits"></a>DA0018: İşlem tarafından yönetilen bellek sınırlarında çalışan 32 bit Uygulama

|||
|-|-|
|Kural Id|DA0018|
|Kategori|Profil Oluşturma Araçları Kullanımı|
|Profil oluşturma yöntemi|Örnekleme|
|İleti|32 bit işlem için varsayılan sınıra yaklaşan yönetilen bellek ayırmaları. Başvurunuz belleğe bağlı olabilir.|
|Kural türü|Uyarı|

 Örnekleme, .NET bellek veya kaynak çekişme yöntemlerini kullanarak profil yaptığınızda, bu kuralı tetiklemek için en az 10 örnek toplamanız gerekir.

## <a name="cause"></a>Nedeni
 Profil oluşturma işlemi sırasında toplanan sistem verileri,.NET Framework bellek yığınlarının yönetilen yığınların 32 bitlik bir işlemde ulaşabileceği maksimum boyuta yaklaştığını gösterir. Bu maksimum boyut varsayılan bir değerdir. Özel baytlar için ayrılabilen işlem adresi alanının toplam tutarıesas alınarak belirlenir. Bildirilen değer, profilli işlem etkinken yığınların en yüksek gözlenen değeridir. .NET bellek profil oluşturma yöntemini kullanarak yeniden profil oluşturmayı ve yönetilen kaynakların uygulama tarafından kullanımını en iyi duruma çıkarmayı düşünün.

 Yönetilen Yığınlar'ın boyutu varsayılan sınıra yaklaştığında, otomatik çöp toplama işleminin daha sık çağrılması gerekebilir. Bu, bellek yönetiminin genel ini artırır.

 Kural yalnızca 32 bit makinelerde çalışan 32 bit uygulamalar için yangınlar.

## <a name="rule-description"></a>Kural açıklaması
 Microsoft .NET ortak dil çalışma zamanı (CLR), uygulamanın artık kullanmadığı nesnelerden bellek geri almak için bir çöp toplayıcısı kullanan otomatik bir bellek yönetim mekanizması sağlar. Çöp toplayıcı, birçok ayırmanın kısa ömürlü olduğu varsayımına dayanarak nesil odaklıdır. Yerel değişkenler, örneğin, kısa ömürlü olmalıdır. Yeni oluşturulan nesneler nesil 0 'da (gen 0) başlar ve çöp toplama çalışmasından sağ kurtulduklarında nesil 1'e doğru ilerlerler ve uygulama hala kullanıyorsa nesil 2'ye geçiş yaparlar.

 85 KB'den büyük yönetilen nesneler, daha küçük nesnelere göre daha az sıklıkta çöp toplama ve sıkıştırmatabi oldukları Büyük Nesne Yığını'na ayrılır. daha kalıcı oldukları ve kalıcı ve büyük nesneleri sık ayrılan küçük nesnelerle karıştırmanın yığının en kötü döküm parçalanmasına neden olabileceği nden, büyük nesneler ayrı ayrı yönetilir.

 Yönetilen yığınların toplam boyutu varsayılan sınıra yaklaştıkça, bellek yönetiminin yükü genellikle uygulamanın yanıt verme yeteneğini ve ölçeklenebilirliğini etkilemeye başlabildiği noktaya yükselir.

## <a name="how-to-investigate-a-warning"></a>Bir uyarı nasıl araştırılı
 [Markalar](../profiling/marks-view.md) görünümüne gitmek için Hata Listesi penceresindeki iletiyi çift tıklatın. Tüm Yığınlar ve **# Toplam taahhüt bayt** **sütunlarında\\.NET CLR Bellek # Bayt** bulun. Yönetilen bellek ayırmanın diğer aşamalardan daha ağır olduğu program yürütmesinin belirli aşamaları olup olmadığını belirleyin. **Tüm Heaps sütunundaki # Bayt** değerlerini Gen **0 Koleksiyonlarının .NET CLR\\Bellek # (Gen 0 Koleksiyonlarının .NET CLR Bellek #**) ve .NET CLR Bellek # gen 1 Koleksiyonları'nda bildirilen çöp toplama oranıyla karşılaştırın ve yönetilen bellek ayırmalarının deseninin çöp toplama oranını etkileyip etkilemediğini belirlemek için Gen 2 Collections sütunlarının **.NET\\CLR** **Belleklerini\\**karşılaştırın.

 Bir .NET Framework uygulamasında, ortak dil çalışma süresi yönetilen yığınların toplam boyutunu, bir işlem adresi alanının özel alan bölümünün maksimum boyutunun yarısından biraz daha azıyla sınırlar. 32 bit makinede çalışan 32 bit işlem için 2 GB, işlem adresi alanının özel bölümünün üst sınırını temsil eder. Yönetilen Yığınlar'ın toplam boyutu varsayılan sınırına yaklaşmaya başladığında, belleği yönetme yükü artabilir ve uygulama performansı düşebilir.

 Aşırı yönetilen bellek yükü bir sorunsa, aşağıdaki seçeneklerden birini göz önünde bulundurun:

- uygulamanın yönetilen bellek kaynaklarını kullanımını optimize etme

   -veya-

- 32 bit lik bir işlem için sanal belleğin maksimum boyutundaki mimari kısıtlamaları hafifletmek için adımlar atmak

  Uygulamanın yönetilen bellek kaynaklarını kullanımını en iyi duruma getirmek için ,.NET Bellek Ayırma profil oluşturma çalışmasında yönetilen bellek ayırma verilerini toplayın. Uygulamanın bellek ayırma desenini anlamak için [.NET Bellek Veri Görünümleri](../profiling/dotnet-memory-data-views.md) raporlarını gözden geçirin.

  Programın veri nesnelerinden hangisinin nesile aktarıldığını ve oradan geri alındığını belirlemek için [Nesne Yaşam Boyu Görünümü'ni](../profiling/object-lifetime-view.md) kullanın.

  Bu [ayırmalarla](../profiling/dotnet-memory-allocations-view.md) sonuçlanan yürütme yolunu belirlemek için Ayırmalar Görünümünü kullanın.

  Çöp toplama performansını nasıl artırılabilenler hakkında daha fazla bilgi için MSDN Web sitesindeki .NET Framework teknik makalesi, [Çöp Toplayıcı Temelleri ve Performans İpuçları'na](/previous-versions/dotnet/articles/ms973837(v=msdn.10)) bakın.

  İşlem adres alanının özel bölümünün boyutundaki sanal bellek kısıtlamalarından mimari rahatlama sağlamak için, bu 32 bit işlemi 64 bit makinede çalıştırmayı deneyin.  64 bit makinedeki 32 bit işlem, 4 GB'a kadar özel sanal bellek elde edebilir.

  64 bit bir makinede çalışan 64 bit işlem, 8 TB'a kadar sanal bellek elde edebilir. Uygulamayı yerel 64 bit uygulama olarak yürütmek üzere yeniden derlemeyi düşünün. Bu kural yalnızca bilgi içindir ve düzeltici eylem gerektirmeyebilir.
