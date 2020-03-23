---
title: Performans Toplama Yöntemlerini Anlama | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.wizard.methodpage
helpviewer_keywords:
- Profiling Tools, profiling methods
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: ad451c6146593713b02901ac43423c76174d0684
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778095"
---
# <a name="understand-performance-collection-methods"></a>Performans toplama yöntemlerini anlama

Visual Studio Profil Oluşturma Araçları, performans verileri toplamak için kullanabileceğiniz beş yöntem sağlar. Bu konu farklı yöntemleri açıklar ve belirli bir yöntemle veri toplamanın uygun olabileceği bazı senaryolar önerir.

> [!NOTE]
> Windows 8 ve Windows Server 2012'deki gelişmiş güvenlik özellikleri, Visual Studio profil oluşturucusu bu platformlarda veri toplama şeklinde önemli değişiklikler gerektiriyordu. UWP uygulamaları da yeni toplama teknikleri gerektirir. [Windows 8 ve Windows Server 2012 uygulamalarında Performans Araçları'na](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)bakın.

|Yöntem|Açıklama|
|------------|-----------------|
|[Örnekleme](#sampling)|Bir uygulama tarafından gerçekleştirilen çalışma hakkında istatistiksel veriler toplar.|
|[Araçları](#instrumentation)|Her işlev çağrısı hakkında ayrıntılı zamanlama bilgileri toplar.|
|[Eşzamanlılık](#concurrency)|Çok iş parçacığı uygulamaları hakkında ayrıntılı bilgi toplar.|
|[.NET bellek](#net-memory)|.NET bellek ayırma ve çöp toplama hakkında ayrıntılı bilgi toplar.|
|[Katman etkileşimi](#tier-interaction)|SqlServer veritabanına senkron ADO.NET işlev çağrıları hakkında bilgi toplar.<br /><br /> Seviye etkileşimi profiloluşturma Visual Studio herhangi bir sürümü kullanılarak toplanabilir. Ancak, katman etkileşimprofilleme verileri yalnızca Visual Studio Enterprise'da görüntülenebilir.|

Profil oluşturma yöntemlerinden bazılarını kullanarak, yazılım ve donanım performans sayaçları gibi ek veriler de toplayabilirsiniz. Daha fazla bilgi için bkz. [ek performans verileri topla.](../profiling/collecting-additional-performance-data.md)

## <a name="sampling"></a>Örnekleme

Örnekleme profil oluşturma yöntemi, profil oluşturma çalışması sırasında bir uygulama tarafından gerçekleştirilen çalışma hakkında istatistiksel veriler toplar. Örnekleme yöntemi hafiftir ve uygulama yöntemlerinin yürütülmesi üzerinde çok az etkisi vardır.

Örnekleme, Visual Studio Profil Oluşturma Araçları'nın varsayılan yöntemidir. Aşağıdakiler için yararlıdır:

- Uygulamanızın performansının ilk keşifleri.
- İşlemcinin (CPU) kullanımını içeren performans sorunlarını araştırma.

Örnekleme profil oluşturma yöntemi, bilgisayar işlemcisini belirli aralıklarla keser ve işlev çağrı yığınını toplar. Yürütülen işlev için özel örnek sayıları artımlanır ve çağrı yığınındaki tüm arama işlevleri için kapsayıcı sayımlar artımlanır. Örnekleme raporları, profilli modül, işlev, kaynak kod satırı ve yönerge için bu sayıların toplamlarını sunar.

Varsayılan olarak, profil oluşturucu örnekleme aralığını CPU döngülerine ayarlar. Aralık türünü başka bir CPU performans sayacıyla değiştirebilir ve aralık için sayaç olaylarının sayısını ayarlayabilirsiniz. Ayrıca, ADO.NET aracılığıyla bir SQL sunucu veritabanına yapılan sorgular hakkında bilgi sağlayan katman etkileşimprofiloluşturma (TIP) verilerini de toplayabilirsiniz.

[Örnekleme kullanarak performans istatistikleri toplama](../profiling/collecting-performance-statistics-by-using-sampling.md)

[Örnekleme veri değerlerini anlama](../profiling/understanding-sampling-data-values.md)

[Örnek yöntem veri görünümleri](../profiling/profiler-sampling-method-data-views.md)

## <a name="instrumentation"></a>İzleme

Instrumentation profil oluşturma yöntemi, profilli bir uygulamada işlev çağrıları için ayrıntılı zamanlama toplar. Enstrümantasyon profilleme aşağıdakiler için yararlıdır:

- Disk G/Ç gibi giriş/çıkış darboğazlarını araştırma.
- Belirli bir modülün veya fonksiyon kümesinin yakın incelenmesi.

Enstrümantasyon yöntemi, enstrümantasyon dosyasındaki her işlevin zamanlama bilgilerini ve bu işlevler tarafından yapılan her işlev çağrısını yakalayan bir ikili dosyaya kod enjekte eder. Enstrümantasyon, bir işlevin bir dosyaya yazma gibi işlemler için işletime çağrı lettiğinde de tanımlar. Araçlama raporları, bir işlev veya kaynak kod satırında harcanan toplam zamanı temsil etmek için dört değer kullanır:

- Geçen Kapsayıcı - İşlev veya kaynak satırı yürütülmesi için harcanan toplam süre.

- Application Inclusive - İşlev veya kaynak satırının yürütülmesi için harcanan, ancak işletim sistemine yapılan aramalarda harcanan süre hariç olmak üzere harcanan süre.

- Geçen Exclusive - Işlev veya kaynak kod satırının gövdesinde kod yürütme harcanan süre. İşlev veya kaynak satırı tarafından çağrılan işlevleri yürütme için harcanan süre dışlanır.

- Uygulama Özel - işlev veya kaynak kod satırının gövdesinde kod yürütme harcanan zaman. İşletim sistemine yapılan çağrıları yürütmek için harcanan süre ve işlev veya kaynak satırı tarafından çağrılan işlevleri yürütmek için harcanan süre dışlanır.

Ayrıca enstrümantasyon yöntemini kullanarak hem CPU hem de yazılım performans sayaçları toplayabilirsiniz.

[Enstrümantasyon veri değerlerini anlama](../profiling/understanding-instrumentation-data-values.md)

[İzleme kullanarak ayrıntılı zamanlama verileri toplama](../profiling/collecting-detailed-timing-data-by-using-instrumentation.md)

[Enstrümantasyon yöntemi veri görünümleri](../profiling/instrumentation-method-data-views.md)

## <a name="concurrency"></a>Eşzamanlılık

Eşzamanlılık profil oluşturma, çok iş parçacığı uygulamaları hakkında bilgi toplar. Kaynak çekişmesi profil oluşturma, rakip iş parçacıkları paylaşılan bir kaynağa erişmek için beklemek zorunda her zaman ayrıntılı arama yığını bilgileri toplar. Eşzamanlılık görselleştirme, çok iş parçacığı uygulamanızın kendisiyle, donanımla, işletim sistemiyle ve ana bilgisayardaki diğer işlemlerle nasıl etkileştiği hakkında daha genel bilgiler de toplar:

- Kaynak çekişme raporları, toplam çekişme sayısını ve beklemenin gerçekleştiği modüller, işlevler, kaynak kodu satırları ve yönergeleri için kaynak beklerken harcanan toplam zamanı görüntüler. Zaman çizelgesi grafikleri de oluştukları gibi çekişmeleri gösterir.

- Eşzamanlılık görselleştiricisi, performans darboğazlarını, CPU az kullanımı, iş parçacığı çekişmesini, iş parçacığı geçişini, eşitleme gecikmelerini, çakışan G/Ç alanlarını ve diğer bilgileri bulmak için kullanabileceğiniz grafik bilgileri görüntüler. Mümkün olduğunda, grafik çıktı bağlantıları yığın ve kaynak kodu verileri aramak için. Eşzamanlılık görselleştirme verileri yalnızca komut satırı ve Windows uygulamaları için toplanabilir.

[Kaynak çekişme veri değerlerini anlama](../profiling/understanding-resource-contention-data-values.md)

[İş parçacığı ve işlem eşzamanlılık verileri toplama](../profiling/collecting-thread-and-process-concurrency-data.md)

[Kaynak çekişme veri görünümleri](../profiling/resource-contention-data-views.md)

[Eşzamanlılık görselleştiricisi](../profiling/concurrency-visualizer.md)

## <a name="net-memory"></a>.NET bellek

.NET bellek ayırma profiloluşturma yöntemi, profilli bir uygulamada bir .NET Framework nesnesinin her tahsisinde bilgisayar işlemcisini keser. Nesne yaşam boyu verileri de toplandığında, profiloluşturucu her .NET Framework çöp koleksiyonundan sonra işlemciyi keser.

Profil oluşturucu, ayırmada oluşturulan veya çöp koleksiyonunda yok edilen nesnelerin türü, boyutu ve sayısı hakkında bilgi toplar.

- Bir ayırma olayı oluştuğunda, profil oluşturucu işlev çağrı yığını hakkında ek bilgiler toplar. Şu anda yürütülmakta olan işlev için özel ayırma sayıları artar ve çağrı yığınındaki tüm arama işlevleri için kapsayıcı sayımlar artar. .NET raporları, profilli türleri, modülleri, işlevleri, kaynak kod satırları ve yönergeleri için bu sayıların toplamlarını sunar.

- Bir çöp toplama oluştuğunda, profil oluşturucu yok edilen nesneler ve her çöp toplama oluşturma daki nesneler hakkında bilgi toplar. Profil oluşturma çalışmasının sonunda, profil oluşturucu açıkça yok olmayan nesnelerle ilgili verileri kaydeder. Object Lifetime raporu, profil oluşturma çalışmasında ayrılan her tür için toplamları görüntüler.

.NET bellek profilleme örnekleme veya enstrümantasyon modunda kullanılabilir. Seçtiğiniz mod, bellek profil oluşturma to.NET benzersiz olan Ayırma ve Nesne Yaşam Süresi raporlarını etkilemez:

- .NET bellek profil oluşturmayı örnekleme modunda çalıştırdığınızda, profiler.NET bellek ayırma olaylarını aralık olarak kullanır ve ayrılan nesne sayısını ve raporlardaki kapsayıcı ve münhasır değerler olarak ayrılan toplam bayt sayısını görüntüler.

- .NET bellek profil oluşturmayı enstrümantasyon modunda çalıştırdığınızda, ayrıntılı zamanlama bilgileri kapsayıcı ve özel ayırma değerleriyle birlikte toplanır.

[Bellek ayırma ve nesne yaşam boyu veri değerlerini anlama](../profiling/understanding-memory-allocation-and-object-lifetime-data-values.md)

[.NET bellek ayırma ve yaşam süresi verilerini toplama](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)

[.NET bellek veri görünümleri](../profiling/dotnet-memory-data-views.md)

## <a name="tier-interaction"></a>Katman etkileşimi

Katman etkileşimi profil oluşturma, bir [!INCLUDE[vstecado](../data-tools/includes/vstecado_md.md)] [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] sayfa veya diğer uygulama ve [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)] veritabanı arasındaki eşzamanlı aramalarla ilgili bir profil oluşturma veri dosyasına bilgi ekler. Veriler, aramaların sayısını ve zamanını ve maksimum ve minimum sürelerini içerir. Katman etkileşimi verileri örnekleme, enstrümantasyon, .NET bellek veya eşzamanlılık yöntemleriyle toplanan profil oluşturma verilerine eklenebilir.

![Katman etkileşim profili verileri](../profiling/media/tierinteraction_profilingtools.png "TierInteraction_ProfilingTools")

Profil Oluşturma Araçları tarafından toplanan katman etkileşim verileri

[Katman etkileşim verileri toplama](../profiling/collecting-tier-interaction-data.md)

[Katman etkileşim görünümleri](../profiling/tier-interaction-views.md)

## <a name="see-also"></a>Ayrıca bkz.

[Nasıl kullanılır: Bir web sitesi](../profiling/how-to-collect-performance-data-for-a-web-site.md)
için performans verileri toplama[Başlangıç kılavuzu performans profilleme](../profiling/beginners-guide-to-performance-profiling.md)
