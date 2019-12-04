---
title: Performans toplama yöntemlerini anlama | Microsoft Docs
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
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74778095"
---
# <a name="understand-performance-collection-methods"></a>Performans toplama yöntemlerini anlama

Visual Studio Profil Oluşturma Araçları, performans verilerini toplamak için kullanabileceğiniz beş yöntem sağlar. Bu konu, farklı yöntemleri açıklar ve belirli bir yönteme sahip verilerin toplanması için bazı senaryolar önerir.

> [!NOTE]
> Windows 8 ve Windows Server 2012 ' deki gelişmiş güvenlik özellikleri, Visual Studio Profiler 'ın bu platformlarda verileri nasıl topladığı konusunda önemli değişiklikler gerektirdi. UWP uygulamaları için de yeni koleksiyon teknikleri gerekir. Bkz. [Windows 8 ve Windows Server 2012 uygulamalarında performans araçları](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

|Yöntem|Açıklama|
|------------|-----------------|
|[Aşağıdakine](#sampling)|Bir uygulama tarafından gerçekleştirilen iş hakkında istatistiksel verileri toplar.|
|[Yapısı](#instrumentation)|Her işlev çağrısıyla ilgili ayrıntılı zamanlama bilgilerini toplar.|
|[Eşzamanlılık](#concurrency)|Çok iş parçacıklı uygulamalarla ilgili ayrıntılı bilgi toplar.|
|[.NET belleği](#net-memory)|.NET bellek ayırma ve çöp toplama hakkında ayrıntılı bilgiler toplar.|
|[Katman etkileşimi](#tier-interaction)|Bir SqlServer veritabanına yönelik zaman uyumlu ADO.NET işlev çağrıları hakkında bilgi toplar.<br /><br /> Katman etkileşimi profili oluşturma, herhangi bir Visual Studio sürümü kullanılarak toplanabilir. Ancak, katman etkileşimi profil oluşturma verileri yalnızca Visual Studio Enterprise görüntülenebilir.|

Profil oluşturma yöntemlerinden bazılarını kullanarak, yazılım ve donanım performans sayaçları gibi ek veriler de toplayabilirsiniz. Daha fazla bilgi için bkz. [ek performans verileri toplama](../profiling/collecting-additional-performance-data.md).

## <a name="sampling"></a>Aşağıdakine

Örnekleme profili oluşturma yöntemi, bir profil oluşturma işlemi sırasında bir uygulama tarafından gerçekleştirilen iş hakkındaki istatistiksel verileri toplar. Örnekleme yöntemi hafif ve uygulama yöntemlerinin yürütülmesi üzerinde çok daha etkilidir.

Örnekleme, Visual Studio Profil Oluşturma Araçları varsayılan yöntemidir. Aşağıdakiler için yararlıdır:

- Uygulamanızın performansının ilk araştırması.
- İşlemcinin (CPU) kullanımı ile ilgili performans sorunlarını araştırma.

Örnekleme profili oluşturma yöntemi, bilgisayar işlemcisini ayarlanan aralıklarla keser ve işlev çağrı yığınını toplar. Dışlamalı örnek sayımlar, Çağrı yığınındaki tüm çağırma işlevleri için yürütülen ve kapsamlı sayımlar arttırılır. Örnekleme raporları, profili oluşturulmuş modül, işlev, kaynak kodu satırı ve yönerge için bu sayımların toplamlarını sunar.

Varsayılan olarak, profil oluşturucu örnekleme aralığını CPU döngüleri olarak ayarlar. Aralık türünü başka bir CPU performans sayacı olarak değiştirebilir ve zaman aralığı için sayaç olaylarının sayısını ayarlayabilirsiniz. Ayrıca, ADO.NET aracılığıyla bir SQL Server veritabanında yapılan sorgular hakkında bilgi sağlayan katman etkileşim profili oluşturma (tıp) verilerini toplayabilirsiniz.

[Örnekleme kullanarak performans istatistikleri toplama](../profiling/collecting-performance-statistics-by-using-sampling.md)

[Örnekleme veri değerlerini anlama](../profiling/understanding-sampling-data-values.md)

[Örnek yöntem veri görünümleri](../profiling/profiler-sampling-method-data-views.md)

## <a name="instrumentation"></a>İzleme

İzleme profili oluşturma yöntemi, profili oluşturulmuş bir uygulamadaki işlev çağrıları için ayrıntılı zamanlama toplar. İzleme profili oluşturma, aşağıdakiler için yararlıdır:

- Disk g/ç gibi giriş/çıkış sorunlarını araştırma.
- Belirli bir modülün veya işlev kümesinin incelemesini kapatın.

İzleme yöntemi, kodu, izlenen dosyadaki her bir işlev için zamanlama bilgilerini yakalayan bir ikili dosyaya ve bu işlevler tarafından yapılan her bir işlev çağrısına çıkartır. İzleme Ayrıca bir işlevin bir dosyaya yazma gibi işlemler için ne zaman çağrtığını tanımlar. İzleme raporları, bir işlevde veya kaynak kodu satırında harcanan toplam süreyi temsil etmek için dört değer kullanır:

- Geçen kapsamlı-işlevi veya kaynak satırını yürütmek için harcanan toplam süre.

- Uygulama kapsamlı-işlevi veya kaynak satırını yürütmek için harcanan zaman ve işletim sistemine yapılan çağrılarda harcanan zamanı hariç tutma süresi.

- Özel olarak geçen süre-işlevin veya kaynak kodu satırının gövdesinde kod yürütmeyi harcanan zaman. İşlev veya kaynak satırı tarafından çağrılan işlevlerin yürütülmesi için harcanan süre dışarıda bırakılır.

- Uygulama dışlamalı-işlevin veya kaynak kodu satırının gövdesinde kod yürütmeyi harcanan zaman. İşletim sistemine yapılan çağrıların yürütülmesi ve işlev veya kaynak satırı tarafından çağrılan işlevlerin yürütülmesi için harcanan süre hariç tutulur.

Ayrıca, izleme yöntemini kullanarak hem CPU hem de yazılım performans sayaçlarını toplayabilirsiniz.

[İzleme veri değerlerini anlama](../profiling/understanding-instrumentation-data-values.md)

[İzleme kullanarak ayrıntılı zamanlama verileri toplama](../profiling/collecting-detailed-timing-data-by-using-instrumentation.md)

[İzleme yöntemi veri görünümleri](../profiling/instrumentation-method-data-views.md)

## <a name="concurrency"></a>Eşzamanlılık

Eşzamanlılık profili oluşturma, çok iş parçacıklı uygulamalar hakkında bilgi toplar. Kaynak çakışması profili, rekabet iş parçacıklarının paylaşılan bir kaynağa erişim için beklemeye zorlanması her seferinde ayrıntılı çağrı yığını bilgilerini toplar. Eşzamanlılık görselleştirmesi Ayrıca, çok iş parçacıklı uygulamanızın kendisiyle, donanım, işletim sistemi ve ana bilgisayardaki diğer işlemlerle nasıl etkileşime girdiği hakkında daha genel bilgiler de toplar:

- Kaynak çekişmeleri, modüller, işlevler, kaynak kodu satırları ve bekleme gerçekleştiği yönergelerin bir kaynağı beklerken harcanan toplam çekişme sayısını ve toplam süreyi görüntüler. Zaman çizelgesi grafikleri de oluştuklar gibi çekişmeleri gösterir.

- Eşzamanlılık görselleştiricisi performans sorunlarını, CPU kullanımını, iş parçacığı çekişmesini, iş parçacığı geçişini, eşitleme gecikmelerini, çakışan g/ç bölgelerini ve diğer bilgileri bulmak için kullanabileceğiniz grafik bilgileri görüntüler. Mümkün olduğunda, grafik çıkışı yığın ve kaynak kodu verilerini çağırmak için bağlantı sağlar. Eşzamanlılık görselleştirme verileri, yalnızca komut satırı ve Windows uygulamaları için toplanabilir.

[Kaynak çakışması veri değerlerini anlama](../profiling/understanding-resource-contention-data-values.md)

[İş parçacığı ve işlem eşzamanlılık verileri toplama](../profiling/collecting-thread-and-process-concurrency-data.md)

[Kaynak çakışması veri görünümleri](../profiling/resource-contention-data-views.md)

[Eşzamanlılık görselleştiricisi](../profiling/concurrency-visualizer.md)

## <a name="net-memory"></a>.NET belleği

.NET bellek ayırma profil oluşturma yöntemi, profili oluşturulmuş bir uygulamadaki bir .NET Framework nesnesinin her ayırmada bilgisayar işlemcisini keser. Nesne ömür verileri de toplandığında, Profil Oluşturucu .NET Framework her bir çöp toplama işleminden sonra işlemciyi keser.

Profiler, bir ayırma içinde oluşturulan veya atık toplamada yok edilen nesnelerin türü, boyutu ve sayısı hakkında bilgi toplar.

- Bir ayırma olayı gerçekleştiğinde, profil oluşturucu işlev çağrı yığını hakkında ek bilgiler toplar. Dışlamalı ayırma sayıları, şu anda yürütülmekte olan işlev için artırılır ve Çağrı yığınındaki tüm çağırma işlevleri için kapsamlı sayımlar artırılır. .NET raporları, profili oluşturulmuş türler, modüller, işlevler, kaynak kodu satırları ve yönergeler için bu sayımların toplamlarını sunar.

- Bir çöp toplama gerçekleştiğinde, profil oluşturucu, yok edilen nesneler hakkında verileri ve her bir çöp toplama oluşturma içindeki nesneler hakkında bilgi toplar. Profil oluşturma çalıştırmasının sonunda, profil oluşturucu açıkça yok edilmedikleri nesneler hakkında verileri kaydeder. Nesne ömrü raporu, profil oluşturma çalıştırmasında ayrılan her bir türün toplamlarını görüntüler.

.NET bellek profili oluşturma, örnekleme veya izleme modunda kullanılabilir. Seçtiğiniz mod, benzersiz to.NET bellek profili oluşturma olan ayırma ve nesne yaşam süresi raporlarını etkilemez:

- .NET bellek profili oluşturmayı örnekleme modunda çalıştırdığınızda, profiler.NET Aralık olarak bellek ayırma olaylarını kullanır ve ayrılan nesne sayısını ve raporlardaki dahil ve dışlamalı değerler olarak ayrılan toplam baytları görüntüler.

- .NET bellek profili oluşturmayı izleme modunda çalıştırdığınızda, ayrıntılı zamanlama bilgileri kapsamlı ve dışlamalı ayırma değerleriyle birlikte toplanır.

[Bellek ayırmayı ve nesne yaşam süresi veri değerlerini anlama](../profiling/understanding-memory-allocation-and-object-lifetime-data-values.md)

[.NET bellek ayırma ve yaşam süresi verilerini toplama](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)

[.NET bellek verileri görünümleri](../profiling/dotnet-memory-data-views.md)

## <a name="tier-interaction"></a>Katman etkileşimi

Katman etkileşimi profili oluşturma, bir [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] sayfası veya diğer uygulama ile [!INCLUDE[ssNoVersion](../data-tools/includes/ssnoversion_md.md)] veritabanı arasındaki zaman uyumlu [!INCLUDE[vstecado](../data-tools/includes/vstecado_md.md)] çağrıları hakkında bir profil oluşturma veri dosyasına bilgi ekler. Veriler, çağrıların sayısını ve zamanını, en fazla ve en az süreyi içerir. Katman etkileşim verileri, örnekleme, izleme, .NET belleği veya eşzamanlılık yöntemleriyle toplanan profil oluşturma verilerine eklenebilir.

![Katman etkileşimi profil verileri](../profiling/media/tierinteraction_profilingtools.png "TierInteraction_ProfilingTools")

Profil Oluşturma Araçları tarafından toplanan katman etkileşim verileri

[Katman etkileşim verileri toplama](../profiling/collecting-tier-interaction-data.md)

[Katman etkileşimi görünümleri](../profiling/tier-interaction-views.md)

## <a name="see-also"></a>Ayrıca bkz.

[Nasıl yapılır: bir Web sitesi için performans verilerini toplama](../profiling/how-to-collect-performance-data-for-a-web-site.md)
[Başlangıç Kılavuzu, performans profili oluşturma kılavuzu](../profiling/beginners-guide-to-performance-profiling.md)
