---
title: 'DA0021: Gen 1 çöp toplama yüksek oranda | Microsoft Dokümanlar'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.21
- vs.performance.DA0021
- vs.performance.rules.DA0021
ms.assetid: ebf5d9b3-a1ac-4688-8f0f-39a85f4dd15f
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 36350b59a3d70f8553fddc5f58bf5c79716fa3aa
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74777666"
---
# <a name="da0021-high-rate-of-gen-1-garbage-collections"></a>DA0021: Yüksek oranda Gen 1 çöp koleksiyonları

|||
|-|-|
|Kural Id|DA0021|
|Kategori|.NET Çerçeve Kullanımı|
|Profil oluşturma yöntemleri|Tümü|
|İleti|Gen 1 çöp toplama oldukça yüksek bir oranı meydana gelmektedir. Tasarım gereği, programınızın veri yapılarının çoğu uzun süre tahsis edilmiş ve kalıcıise, bu normalde bir sorun değildir. Ancak, bu davranış istenmeyen ise, uygulamanız nesneleri sabitleme olabilir. Emin değilseniz, uygulamanızın kullandığı bellek ayırma desenini anlamak için .NET bellek ayırma verilerini ve nesne yaşam boyu bilgilerini toplayabilirsiniz.|
|Kural türü|Bilgi|

 Örnekleme, .NET bellek veya kaynak çekişme yöntemlerini kullanarak profil yaptığınızda, bu kuralı tetiklemek için en az 10 örnek toplamanız gerekir.

## <a name="cause"></a>Nedeni
 Profil oluşturma sırasında toplanan sistem performans verileri, bellek for.NET Framework nesnelerinin önemli bir bölümünün, nesil 0 veri toplamaile karşılaştırıldığında çöp toplamanın 1.

## <a name="rule-description"></a>Kural açıklaması
 Microsoft .NET ortak dil çalışma zamanı (CLR), uygulamanın artık kullanmadığı nesnelerden bellek geri almak için bir çöp toplayıcısı kullanan otomatik bir bellek yönetim mekanizması sağlar. Çöp toplayıcı, birçok ayırmanın kısa ömürlü olduğu varsayımına dayanarak nesil odaklıdır. Yerel değişkenler, örneğin, kısa ömürlü olmalıdır. Yeni oluşturulan nesneler nesil 0 'da (gen 0) başlar ve çöp toplama çalışmasından sağ kurtulduklarında nesil 1'e doğru ilerlerler ve uygulama hala kullanıyorsa nesil 2'ye geçiş yaparlar.

 Nesil 0'daki nesneler sık sık ve genellikle çok verimli bir şekilde toplanır. Nesil 1'deki nesneler daha az sıklıkta ve daha az verimli bir şekilde toplanır. Son olarak, nesil 2 uzun ömürlü nesneleri daha az sıklıkta toplanmalıdır. Tam bir çöp toplama çalışması olan Generation 2 koleksiyonu da en pahalı işlemdir.

 Orantılı olarak çok fazla nesil 1 çöp toplama oluştuğunda bu kural yangınları. Çok fazla oldukça kısa ömürlü nesneler nesil 0 koleksiyonu hayatta ama sonra bir nesil 1 toplama toplanabilir, bellek yönetimi maliyeti aşırı olabilir. Daha fazla bilgi için, MSDN Web sitesinde Rico Mariani's Performance Tidbits orta [yaş kriz](https://blogs.msdn.microsoft.com/ricom/2003/12/04/mid-life-crisis/) sonrası bakın.

## <a name="how-to-investigate-a-warning"></a>Bir uyarı nasıl araştırılı
 Profil oluşturma verilerinin [İşaretler Görünümü'ne](../profiling/marks-view.md) gitmek için Hatalar Listesi penceresindeki iletiyi çift tıklatın. Gen **0 Koleksiyonlarının\\.NET CLR Bellek # ve** Gen 1 **Koleksiyonları sütunlarının .NET CLR Bellek\\#** ını bulun. Çöp toplamanın daha sık gerçekleştiği program yürütmesinin belirli aşamaları olup olmadığını belirleyin. Yönetilen bellek ayırmalarının deseninin aşırı bellek yönetimi yüküne neden olup olmadığını görmek için bu değerleri **GC sütunundaki % Zaman** ile karşılaştırın.

 Uygulamanın yönetilen bellek kullanım desenini anlamak için, yeniden çalışan a.NET Bellek ayırma profili ve Object Lifetime ölçümleri isteyin.

 Çöp toplama performansını nasıl artırılabildiğini öğrenmek için Microsoft Web [sitesindeki Çöp Toplayıcı Temelleri ve Performans İpuçları'na](/previous-versions/dotnet/articles/ms973837(v=msdn.10)) bakın. Otomatik çöp toplama nın ek yükü hakkında bilgi için [bkz.](https://msdn.microsoft.com/magazine/cc534993.aspx)
