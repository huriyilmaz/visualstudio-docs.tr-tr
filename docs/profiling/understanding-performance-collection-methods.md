---
title: Performans toplama yöntemlerini anlama | Microsoft Docs
description: Belirli bir yöntemle verilerin toplanması için uygun olabilecek farklı senaryolar hakkında bilgi edinin.
ms.date: 4/30/2020
ms.topic: conceptual
f1_keywords:
- vs.performance.wizard.methodpage
helpviewer_keywords:
- Profiling tools, profiling methods
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: b3bbbef2c6f7bb2ab02731bfbac0dc60d75a3437
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2021
ms.locfileid: "98722340"
---
# <a name="understand-performance-collection-methods"></a>Performans toplama yöntemlerini anlama

Visual Studio profil oluşturma araçları, performans verilerini toplamak için beş yöntem sağlar. Bu makalede, farklı yöntemler açıklanmakta ve belirli bir yöntemle verilerin toplanması için uygun olabilecek senaryolar önerilir.

> [!NOTE]
> Windows 8 ve Windows Server 2012 ' deki gelişmiş güvenlik özellikleri, Visual Studio Profiler 'ın bu platformlarda verileri nasıl topladığı konusunda önemli değişiklikler gerektirdi. UWP uygulamaları için de yeni koleksiyon teknikleri gerekir. Bkz. [Windows 8 ve Windows Server 2012 uygulamalarında performans araçları](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

|Yöntem|Açıklama|
|------------|-----------------|
|[Örnekleme](#sampling)|Bir uygulama tarafından gerçekleştirilen iş hakkında istatistiksel verileri toplar.|
|[Yapısı](#instrumentation)|Her işlev çağrısıyla ilgili ayrıntılı zamanlama bilgilerini toplar.|
|[Eşzamanlılık](#concurrency)|Çok iş parçacıklı uygulamalarla ilgili ayrıntılı bilgi toplar.|
|[.NET belleği](#net-memory)|.NET bellek ayırma ve çöp toplama hakkında ayrıntılı bilgiler toplar.|
|[Katman etkileşimi](#tier-interaction)|SQL Server veritabanına yönelik zaman uyumlu ADO.NET işlev çağrıları hakkında bilgi toplar.<br /><br /> Herhangi bir Visual Studio sürümü, katman etkileşimi profil verileri toplayabilir. Ancak, bu verileri yalnızca Visual Studio Enterprise görüntüleyebilirsiniz.|

Profil oluşturma yöntemlerinden bazılarını kullanarak, yazılım ve donanım performans sayaçları gibi ek veriler de toplayabilirsiniz. Daha fazla bilgi için bkz. [ek performans verileri toplama](../profiling/collecting-additional-performance-data.md).

## <a name="sampling"></a>Örnekleme

Örnekleme profili oluşturma yöntemi, bir uygulamanın profil oluşturma çalışması sırasında çalıştığı iş hakkındaki istatistiksel verileri toplar. Örnekleme yöntemi hafif ve uygulama yöntemlerinin yürütülmesi üzerinde çok daha etkilidir.

Örnekleme, Visual Studio profil oluşturma araçlarının varsayılan yöntemidir. Aşağıdaki görevler için kullanışlıdır:

- Uygulamanızın performansının ilk araştırması
- Mikro işlemcinin (CPU) kullanımı ile ilgili performans sorunlarını araştırma

Örnekleme profili oluşturma yöntemi, küme aralıklarında bilgisayar CPU 'sunu keser ve işlev çağrı yığınını toplar. Çalışan işlev için dışlamalı örnek sayımlar artırılır. Dahil edilen sayımlar, Çağrı yığınındaki tüm çağırma işlevleri için artırılır. Örnekleme raporları, profili oluşturulmuş modüller, işlevler, kaynak kodu satırları ve yönergeler için bu sayımların toplamlarını sunar.

Varsayılan olarak, profil oluşturucu örnekleme aralığını CPU döngüleri olarak ayarlar. Aralık türünü başka bir CPU performans sayacı olarak değiştirebilir veya Aralık için sayaç olaylarının sayısını ayarlayabilirsiniz. Katman etkileşimi profil oluşturma (tıp) verilerini de toplayabilirsiniz. Bu veriler, ADO.NET aracılığıyla SQL Server veritabanına yapılan sorgular hakkında bilgiler sağlar.

[Örnekleme kullanarak performans istatistikleri toplama](../profiling/collecting-performance-statistics-by-using-sampling.md)

[Örnekleme veri değerlerini anlama](../profiling/understanding-sampling-data-values.md)

[Örnek yöntem veri görünümleri](../profiling/profiler-sampling-method-data-views.md)

## <a name="instrumentation"></a>İzleme

İzleme profili oluşturma yöntemi, profili oluşturulmuş bir uygulamadaki işlev çağrıları için ayrıntılı zamanlama toplar. İzleme profili oluşturma bu görevler için yararlıdır:

- Disk g/ç gibi giriş/çıkış darboğazlarını araştırma
- Belirli bir modülün veya işlev kümesinin incelemesini kapatma

İzleme yöntemi kodu ikili bir dosyaya çıkarır. Kod, izlenen dosyadaki tüm işlevler için zamanlama bilgilerini yakalar ve her işlev bu işlevleri çağırır. İzleme Ayrıca bir işlevin bir dosyaya yazma gibi işlemler için işletim sistemine ne zaman çağrı yaptığı belirler.

İzleme raporları, bir işlev veya kaynak kodu satırında harcanan toplam süreyi göstermek için bu dört değeri kullanır:

- Geçen kapsamlı-işlevi veya kaynak kodu satırını çalıştırmak için harcanan toplam süre.

- Uygulama kapsamlı-işlevi veya kaynak kodu satırını çalıştırmak için harcanan süre. İşletim sistemine yapılan çağrılar hariç tutulur.

- Hariç geçen dışlamalı-işlev veya kaynak kodu satırını çalıştırmak için harcanan süre. Diğer işlevlere yapılan çağrılar hariç tutulur.

- Uygulama dışlamalı-işlevi veya kaynak kodu satırını çalıştırmak için harcanan süre. İşletim sistemine veya diğer işlevlere yapılan çağrılar hariç tutulur.

Ayrıca, izleme yöntemini kullanarak hem CPU hem de yazılım performans sayaçlarını toplayabilirsiniz.

[İzleme veri değerlerini anlama](../profiling/understanding-instrumentation-data-values.md)

[İzleme kullanarak ayrıntılı zamanlama verileri toplama](../profiling/collecting-detailed-timing-data-by-using-instrumentation.md)

[İzleme yöntemi veri görünümleri](../profiling/instrumentation-method-data-views.md)

## <a name="concurrency"></a>Eşzamanlılık

Eşzamanlılık profili oluşturma çok iş parçacıklı uygulamalar hakkında bilgi toplar. Kaynak çakışması profil oluşturma, rekabet iş parçacıklarının paylaşılan bir kaynağa erişimi beklediğinde ayrıntılı çağrı yığını bilgilerini toplar. Eşzamanlılık görselleştirmesi Ayrıca, çok iş parçacıklı uygulamanızın nasıl etkileşime girdiği hakkında daha genel bilgiler de toplar:

- İlişkilendirilemez.
- Donanım.
- İşletim sistemidir.
- Ana bilgisayardaki diğer süreçler.

Kaynak çekişme raporları toplam çekişmeler sayısını görüntüler. Ayrıca, modüller, işlevler, kaynak kodu satırları ve yönergelerin bir kaynak için bekledikleri toplam süreyi bildirir. Zaman çizelgesi grafikleri, oluştuklar sırasında çekişmeleri gösterir.

Eşzamanlılık görselleştiricisi şunları bulmanıza yardımcı olacak grafik bilgileri görüntüler:

- Performans sorunları.
- CPU az kullanımı.
- İş parçacığı çakışması.
- İş parçacığı geçişi.
- Eşitleme gecikmeleri.
- Çakışan g/ç 'nin alanı.

  Mümkün olduğunda, grafik çıkışı çağrı yığınından ve kaynak kodundaki verilere bağlantı sağlar. Eşzamanlılık görselleştirme verileri, yalnızca komut satırı uygulamaları ve Windows uygulamaları için toplanabilir.

[Kaynak çakışması veri değerlerini anlama](../profiling/understanding-resource-contention-data-values.md)

[İş parçacığı ve işlem eşzamanlılık verileri toplama](../profiling/collecting-thread-and-process-concurrency-data.md)

[Kaynak çakışması veri görünümleri](../profiling/resource-contention-data-views.md)

[Eşzamanlılık Görselleştiricisi](../profiling/concurrency-visualizer.md)

## <a name="net-memory"></a>.NET belleği

.NET bellek ayırma profil oluşturma yöntemi, profili oluşturulmuş bir uygulamadaki bir .NET Framework nesnesinin her ayırmada CPU 'YU keser. Profil Oluşturucu ayrıca nesne yaşam süresi verilerini toplarken, .NET Framework her bir çöp toplama işleminden sonra CPU 'YU keser.

Profiler, bir ayırma içinde oluşturulan veya atık toplamada yok edilen nesnelerin türü, boyutu ve sayısı hakkında bilgi toplar.

- Bir ayırma olayı gerçekleştiğinde, profil oluşturucu işlev çağrı yığını hakkında ek bilgiler toplar. Profiler, çalışmakta olan işlevin özel kullanım sayısını artırır. Ayrıca çağrı yığınındaki tüm çağırma işlevlerinin dahil olduğu sayıları artırır. .NET raporları, profili oluşturulmuş türler, modüller, işlevler, kaynak kodu satırları ve yönergeler için bu sayımların toplamlarını sunar.

- Çöp toplama gerçekleştiğinde, profil oluşturucu, yok etme nesneleri ve her çöp toplama oluşturma içindeki nesneler hakkında veri toplar. Profil oluşturma çalıştırmasının sonunda, profil oluşturucu açıkça yok edilen nesneler hakkında verileri kaydeder. Nesne ömrü raporu, profil oluşturma çalıştırmasında ayrılan her bir türün toplamlarını görüntüler.

.NET bellek profili oluşturmayı, örnekleme modunda veya izleme modunda kullanabilirsiniz. Seçtiğiniz mod, .NET bellek profili oluşturma için benzersiz olan ayırma ve nesne yaşam süresi raporlarını etkilemez.

- .NET bellek profili oluşturma 'yı örnekleme modunda çalıştırdığınızda, profil oluşturucu, bellek ayırma olaylarını Aralık olarak kullanır. Ayrıca, toplam ayrılan nesne sayısını ve baytların rapordaki dahil ve dışlamalı değerlerini görüntüler.

- .NET bellek profili oluşturmayı izleme modunda çalıştırdığınızda, profil oluşturucu ayrıntılı zamanlama bilgilerini kapsamlı ve dışlamalı ayırma değerleriyle birlikte toplar.

[Bellek ayırmayı ve nesne ömrü veri değerlerini anlama](../profiling/understanding-memory-allocation-and-object-lifetime-data-values.md)

[.NET bellek ayırma ve yaşam süresi verilerini toplama](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)

[.NET bellek verileri görünümleri](../profiling/dotnet-memory-data-views.md)

## <a name="tier-interaction"></a>Katman etkileşimi

Katman etkileşimi profili oluşturma [!INCLUDE[vstecado](../data-tools/includes/vstecado_md.md)] [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] , bir sayfa veya başka bir uygulama ile veritabanı arasındaki zaman uyumlu çağrılar hakkında bir profil oluşturma veri dosyasına bilgi ekler [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)] . Veriler, çağrıların sayısını ve zamanını ve en fazla ve en az süreyi içerir. Örnekleme, izleme, .NET bellek veya eşzamanlılık yöntemleriyle topladığınız profil oluşturma verilerine katman etkileşim verileri ekleyebilirsiniz.

![Katman etkileşimi profil oluşturma veri akışı](../profiling/media/tierinteraction_profilingtools.png "Katman etkileşimi profil oluşturma veri akışı")

Profil oluşturma araçları tarafından toplanan katman etkileşim verileri hakkında daha fazla bilgi için aşağıdaki makalelere bakın.

[Katman etkileşimi verilerini toplayın](../profiling/collecting-tier-interaction-data.md)

[Katman etkileşimi görünümleri](../profiling/tier-interaction-views.md)

## <a name="see-also"></a>Ayrıca bkz.

[Nasıl yapılır: bir Web sitesi için performans verilerini toplama](../profiling/how-to-collect-performance-data-for-a-web-site.md)

[Performans profili oluşturma Başlangıç kılavuzu](../profiling/beginners-guide-to-performance-profiling.md)
