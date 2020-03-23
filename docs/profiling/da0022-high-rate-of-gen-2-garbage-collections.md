---
title: 'DA0022: Gen 2 çöp toplama yüksek oranda | Microsoft Dokümanlar'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.DA0022
- vs.performance.rules.DA0022
- vs.performance.22
ms.assetid: f871a547-0e6f-4b11-b2d7-174d30fc2ed8
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 4e1fa46162f2aea74c5b3cb8396ad5e8d4c9a4cf
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779382"
---
# <a name="da0022-high-rate-of-gen-2-garbage-collections"></a>DA0022: Yüksek oranda Gen 2 çöp koleksiyonları

|||
|-|-|
|Kural Id|DA0022|
|Kategori|.NET Çerçeve Kullanımı|
|Profil oluşturma yöntemi|Tümü|
|İleti|Gen 2 çöp toplama oldukça yüksek bir oranı meydana gelmektedir. Tasarım gereği, programınızın veri yapılarının çoğu uzun süre tahsis edilmiş ve kalıcıise, bu normalde bir sorun değildir. Ancak, bu davranış istenmeyen ise, uygulamanız nesneleri sabitleme olabilir. Emin değilseniz, uygulamanızın kullandığı bellek ayırma desenini anlamak için .NET bellek ayırma verilerini ve nesne yaşam boyu bilgilerini toplayabilirsiniz.|
|Kural türü|Uyarı|

 Örnekleme, .NET bellek veya kaynak çekişme yöntemlerini kullanarak profil yaptığınızda, bu kuralı tetiklemek için en az 10 örnek toplamanız gerekir.

## <a name="cause"></a>Nedeni
 Profil oluşturma sırasında toplanan sistem performans verileri, bellek for.NET Framework nesnelerinin önemli bir bölümünün nesil 0 ve nesil 1 çöp koleksiyonlarına kıyasla çöp toplamanın 2.

## <a name="rule-description"></a>Kural açıklaması
 Microsoft .NET ortak dil çalışma zamanı (CLR), uygulamanın artık kullanmadığı nesnelerden bellek geri almak için bir çöp toplayıcısı kullanan otomatik bir bellek yönetim mekanizması sağlar. Çöp toplayıcı, birçok ayırmanın kısa ömürlü olduğu varsayımına dayanarak nesil odaklıdır. Yerel değişkenler, örneğin, kısa ömürlü olmalıdır. Yeni oluşturulan nesneler nesil 0 'da (gen 0) başlar ve çöp toplama çalışmasından sağ kurtulduklarında nesil 1'e doğru ilerlerler ve uygulama hala kullanıyorsa nesil 2'ye geçiş yaparlar.

 Nesil 0'daki nesneler sık sık ve genellikle çok verimli bir şekilde toplanır. Nesil 1'deki nesneler daha az sıklıkta ve daha az verimli bir şekilde toplanır. Son olarak, nesil 2 uzun ömürlü nesneleri daha az sıklıkta toplanmalıdır. Tam bir çöp toplama çalışması olan Generation 2 koleksiyonu da en pahalı işlemdir.

 Orantılı olarak çok fazla nesil 2 çöp koleksiyonları meydana geldiğinde bu kural yangınları. İyi davrandı .NET Framework uygulamaları, nesil 2 koleksiyonlarının 5 katından daha fazla nesil 1 çöp koleksiyonuna sahip olacaktır. (10x faktörü muhtemelen idealdir.)

## <a name="how-to-investigate-a-warning"></a>Bir uyarı nasıl araştırılı
 Profil oluşturma verilerinin [İşaretler Görünümü'ne](../profiling/marks-view.md) gitmek için Hatalar Listesi penceresindeki iletiyi çift tıklatın. Gen **0 Koleksiyonlarının\\.NET CLR Bellek # ve** Gen 1 **Koleksiyonları sütunlarının .NET CLR Bellek\\#** ını bulun. Çöp toplamanın daha sık gerçekleştiği program yürütmesinin belirli aşamaları olup olmadığını belirleyin. Yönetilen bellek ayırmalarının deseninin aşırı bellek yönetimi yüküne neden olup olmadığını görmek için bu değerleri **GC sütunundaki % Zaman** ile karşılaştırın.

 Nesil 2 çöp koleksiyonlarının yüksek bir oranı her zaman bir sorun değildir. Tasarım gereği olabilir. Yürütme sırasında uzun süre etkin kalması gereken büyük veri yapıları ayıran bir uygulama bu kuralı tetikleyebilir. Böyle bir uygulama bellek baskısı altında olduğunda, sık sık çöp toplama yapmak zorunda kalabilir. Daha az pahalı Nesil 0 ve Nesil 1 çöp koleksiyonları yalnızca küçük bir miktar yönetilen bellek geri alabilir, daha sık Nesil 2 çöp koleksiyonları zamanlanır.

 İşaretler Görünümü'nde çöp toplama sorunlarını belirlemenize yardımcı olabilecek ek .NET CLR Bellek sütunları vardır. **GC sütunundaki % Zaman,** ne kadar bellek yönetimi ek yükü oluştuğunu anlamanıza yardımcı olur. Uygulamanız genellikle oldukça az sayıda büyük ama kalıcı nesne kullanıyorsa, sık sık nesil 2 koleksiyonları aşırı miktarda CPU zamanı tüketmemelidir. Daha fazla Fiziksel Bellek (RAM) gerektiğinden uygulama bellek baskısı altındaysa, **Bellek\Sayfa/sn** sütun değerlerini değerlendiren ilgili kurallar da çalışabilir.

 Uygulamanın yönetilen bellek kullanım modelini anlamak için, bellek ayırma profili a.NET yeniden çalışan profili ve Object Lifetime profil oluşturma seçeneğini seçin.

 Çöp toplama performansını nasıl artırılabildiğini öğrenmek için Microsoft Web [sitesindeki Çöp Toplayıcı Temelleri ve Performans İpuçları'na](/previous-versions/dotnet/articles/ms973837(v=msdn.10)) bakın. Otomatik çöp toplama nın ek yükü hakkında bilgi için [bkz.](https://msdn.microsoft.com/magazine/cc534993.aspx)
