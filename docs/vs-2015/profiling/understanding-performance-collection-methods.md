---
title: Performans toplama yöntemlerini anlama | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.wizard.methodpage
helpviewer_keywords:
- Profiling Tools, profiling methods
ms.assetid: ea4881fd-bd04-4875-9b7b-28490d6706f9
caps.latest.revision: 25
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e398d7e5e297daa68663902efb8a9fa0775c86fa
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64787267"
---
# <a name="understanding-performance-collection-methods"></a>Performans Bilgilerini Toplama Metotlarını Anlama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio Profil Oluşturma Araçları, performans verilerini toplamak için kullanabileceğiniz beş yöntem sağlar. Bu konu, farklı yöntemleri açıklar ve belirli bir yönteme sahip verilerin toplanması için bazı senaryolar önerir.  
  
> [!NOTE]
> Windows 8 ve Windows Server 2012 ' deki gelişmiş güvenlik özellikleri, Visual Studio Profiler 'ın bu platformlarda verileri nasıl topladığı konusunda önemli değişiklikler gerektirdi. Windows Mağazası uygulamaları da yeni koleksiyon teknikleri gerektirir. Bkz. [Windows 8 ve Windows Server 2012 uygulamalarında performans araçları](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[Örnekleme](#sampling)|Bir uygulama tarafından gerçekleştirilen iş hakkında istatistiksel verileri toplar.|  
|[Yapısı](#instrumentation)|Her işlev çağrısıyla ilgili ayrıntılı zamanlama bilgilerini toplar.|  
|[Eşzamanlılık](#concurrency)|Çok iş parçacıklı uygulamalarla ilgili ayrıntılı bilgi toplar.|  
|[.NET belleği](#net_memory)|.NET bellek ayırma ve çöp toplama hakkında ayrıntılı bilgiler toplar.|  
|[Katman etkileşimi](#tier_interaction)|Bir SqlServer veritabanına yönelik zaman uyumlu ADO.NET işlev çağrıları hakkında bilgi toplar.<br /><br /> Katman etkileşimi profili oluşturma,, veya kullanılarak toplanabilir [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)] [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)] [!INCLUDE[vs_pro_current_short](../includes/vs-pro-current-short-md.md)] . Ancak, katman etkileşimi profil oluşturma verileri yalnızca veya içinde görüntülenebilir [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)] [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)] .|  
  
 Profil oluşturma yöntemlerinden bazılarını kullanarak, yazılım ve donanım performans sayaçları gibi ek veriler de toplayabilirsiniz. Daha fazla bilgi için bkz. [ek performans verileri toplama](../profiling/collecting-additional-performance-data.md).  
  
## <a name="sampling"></a><a name="sampling"></a> Aşağıdakine  
 Örnekleme profili oluşturma yöntemi, bir profil oluşturma işlemi sırasında bir uygulama tarafından gerçekleştirilen iş hakkındaki istatistiksel verileri toplar. Örnekleme yöntemi hafif ve uygulama yöntemlerinin yürütülmesi üzerinde çok daha etkilidir.  
  
 Örnekleme, Visual Studio Profil Oluşturma Araçları varsayılan yöntemidir. Aşağıdakiler için yararlıdır:  
  
- Uygulamanızın performansının ilk araştırması.  
  
- İşlemcinin (CPU) kullanımı ile ilgili performans sorunlarını araştırma.  
  
  Örnekleme profili oluşturma yöntemi, bilgisayar işlemcisini ayarlanan aralıklarla keser ve işlev çağrı yığınını toplar. Dışlamalı örnek sayımlar, Çağrı yığınındaki tüm çağırma işlevleri için yürütülen ve kapsamlı sayımlar arttırılır. Örnekleme raporları, profili oluşturulmuş modül, işlev, kaynak kodu satırı ve yönerge için bu sayımların toplamlarını sunar.  
  
  Varsayılan olarak, profil oluşturucu örnekleme aralığını CPU döngüleri olarak ayarlar. Aralık türünü başka bir CPU performans sayacı olarak değiştirebilir ve zaman aralığı için sayaç olaylarının sayısını ayarlayabilirsiniz. Ayrıca, ADO.NET aracılığıyla bir SQL Server veritabanında yapılan sorgular hakkında bilgi sağlayan katman etkileşim profili oluşturma (tıp) verilerini toplayabilirsiniz.  
  
  [Örnekleme Kullanarak Performans İstatistikleri Toplama](../profiling/collecting-performance-statistics-by-using-sampling.md)  
  
  [Örnekleme veri değerlerini anlama](../profiling/understanding-sampling-data-values.md)  
  
  [Örnekleme Yöntemi Veri Görünümleri](../profiling/profiler-sampling-method-data-views.md)  
  
## <a name="instrumentation"></a><a name="instrumentation"></a> Yapısı  
 İzleme profili oluşturma yöntemi, profili oluşturulmuş bir uygulamadaki işlev çağrıları için ayrıntılı zamanlama toplar. İzleme profili oluşturma, aşağıdakiler için yararlıdır:  
  
- Disk g/ç gibi giriş/çıkış sorunlarını araştırma.  
  
- Belirli bir modülün veya işlev kümesinin incelemesini kapatın.  
  
  İzleme yöntemi, kodu, izlenen dosyadaki her bir işlev için zamanlama bilgilerini yakalayan bir ikili dosyaya ve bu işlevler tarafından yapılan her bir işlev çağrısına çıkartır. İzleme Ayrıca bir işlevin bir dosyaya yazma gibi işlemler için ne zaman çağrtığını tanımlar. İzleme raporları, bir işlevde veya kaynak kodu satırında harcanan toplam süreyi temsil etmek için dört değer kullanır:  
  
- Geçen kapsamlı-işlevi veya kaynak satırını yürütmek için harcanan toplam süre.  
  
- Uygulama kapsamlı-işlevi veya kaynak satırını yürütmek için harcanan zaman ve işletim sistemine yapılan çağrılarda harcanan zamanı hariç tutma süresi.  
  
- Özel olarak geçen süre-işlevin veya kaynak kodu satırının gövdesinde kod yürütmeyi harcanan zaman. İşlev veya kaynak satırı tarafından çağrılan işlevlerin yürütülmesi için harcanan süre dışarıda bırakılır.  
  
- Uygulama dışlamalı-işlevin veya kaynak kodu satırının gövdesinde kod yürütmeyi harcanan zaman. İşletim sistemine yapılan çağrıların yürütülmesi ve işlev veya kaynak satırı tarafından çağrılan işlevlerin yürütülmesi için harcanan süre hariç tutulur.  
  
  Ayrıca, izleme yöntemini kullanarak hem CPU hem de yazılım performans sayaçlarını toplayabilirsiniz.  
  
  [Izleme veri değerlerini anlama](../profiling/understanding-instrumentation-data-values.md)  
  
  [İzleme Kullanarak Ayrıntılı Zamanlama Verileri Toplama](../profiling/collecting-detailed-timing-data-by-using-instrumentation.md)  
  
  [İzleme Metodu Veri Görünümleri](../profiling/instrumentation-method-data-views.md)  
  
## <a name="concurrency"></a><a name="concurrency"></a> Zamanlı  
 Eşzamanlılık profili oluşturma, çok iş parçacıklı uygulamalar hakkında bilgi toplar. Kaynak çakışması profili, rekabet iş parçacıklarının paylaşılan bir kaynağa erişim için beklemeye zorlanması her seferinde ayrıntılı çağrı yığını bilgilerini toplar. Eşzamanlılık görselleştirmesi Ayrıca, çok iş parçacıklı uygulamanızın kendisiyle, donanım, işletim sistemi ve ana bilgisayardaki diğer işlemlerle nasıl etkileşime girdiği hakkında daha genel bilgiler de toplar:  
  
- Kaynak çekişmeleri, modüller, işlevler, kaynak kodu satırları ve bekleme gerçekleştiği yönergelerin bir kaynağı beklerken harcanan toplam çekişme sayısını ve toplam süreyi görüntüler. Zaman çizelgesi grafikleri de oluştuklar gibi çekişmeleri gösterir.  
  
- Eşzamanlılık görselleştiricisi performans sorunlarını, CPU kullanımını, iş parçacığı çekişmesini, iş parçacığı geçişini, eşitleme gecikmelerini, çakışan g/ç bölgelerini ve diğer bilgileri bulmak için kullanabileceğiniz grafik bilgileri görüntüler. Mümkün olduğunda, grafik çıkışı yığın ve kaynak kodu verilerini çağırmak için bağlantı sağlar. Eşzamanlılık görselleştirme verileri, yalnızca komut satırı ve Windows uygulamaları için toplanabilir.  
  
  [Kaynak çakışması veri değerlerini anlama](../profiling/understanding-resource-contention-data-values.md)  
  
  [İş Parçacığı ve İşlem Eşzamanlılık Verileri Toplama](../profiling/collecting-thread-and-process-concurrency-data.md)  
  
  [Kaynak Çakışması Veri Görünümleri](../profiling/resource-contention-data-views.md)  
  
  [Eşzamanlılık Görselleştiricisi](../profiling/concurrency-visualizer.md)  
  
## <a name="net-memory"></a><a name="net_memory"></a> .NET belleği  
 .NET bellek ayırma profil oluşturma yöntemi, profili oluşturulmuş bir uygulamadaki bir .NET Framework nesnesinin her ayırmada bilgisayar işlemcisini keser. Nesne ömür verileri de toplandığında, Profil Oluşturucu .NET Framework her bir çöp toplama işleminden sonra işlemciyi keser.  
  
 Profiler, bir ayırma içinde oluşturulan veya atık toplamada yok edilen nesnelerin türü, boyutu ve sayısı hakkında bilgi toplar.  
  
- Bir ayırma olayı gerçekleştiğinde, profil oluşturucu işlev çağrı yığını hakkında ek bilgiler toplar. Dışlamalı ayırma sayıları, şu anda yürütülmekte olan işlev için artırılır ve Çağrı yığınındaki tüm çağırma işlevleri için kapsamlı sayımlar artırılır. .NET raporları, profili oluşturulmuş türler, modüller, işlevler, kaynak kodu satırları ve yönergeler için bu sayımların toplamlarını sunar.  
  
- Bir çöp toplama gerçekleştiğinde, profil oluşturucu, yok edilen nesneler hakkında verileri ve her bir çöp toplama oluşturma içindeki nesneler hakkında bilgi toplar. Profil oluşturma çalıştırmasının sonunda, profil oluşturucu açıkça yok edilmedikleri nesneler hakkında verileri kaydeder. Nesne ömrü raporu, profil oluşturma çalıştırmasında ayrılan her bir türün toplamlarını görüntüler.  
  
  .NET bellek profili oluşturma, örnekleme veya izleme modunda kullanılabilir. Seçtiğiniz mod, benzersiz to.NET bellek profili oluşturma olan ayırma ve nesne yaşam süresi raporlarını etkilemez:  
  
- .NET bellek profili oluşturmayı örnekleme modunda çalıştırdığınızda, profiler.NET Aralık olarak bellek ayırma olaylarını kullanır ve ayrılan nesne sayısını ve raporlardaki dahil ve dışlamalı değerler olarak ayrılan toplam baytları görüntüler.  
  
- .NET bellek profili oluşturmayı izleme modunda çalıştırdığınızda, ayrıntılı zamanlama bilgileri kapsamlı ve dışlamalı ayırma değerleriyle birlikte toplanır.  
  
  [Bellek ayırmayı ve nesne yaşam süresi veri değerlerini anlama](../profiling/understanding-memory-allocation-and-object-lifetime-data-values.md)  
  
  [.NET Bellek Ayırma ve Yaşam Süresi Verilerini Toplama](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)  
  
  [.NET bellek verileri görünümleri](../profiling/dotnet-memory-data-views.md)  
  
## <a name="tier-interaction"></a><a name="tier_interaction"></a> Katman etkileşimi  
 Katman etkileşimi profili oluşturma [!INCLUDE[vstecado](../includes/vstecado-md.md)] [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] , bir sayfa veya başka bir uygulama ile veritabanı arasındaki zaman uyumlu çağrılar hakkında bir profil oluşturma veri dosyasına bilgi ekler [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] . Veriler, çağrıların sayısını ve zamanını, en fazla ve en az süreyi içerir. Katman etkileşim verileri, örnekleme, izleme, .NET belleği veya eşzamanlılık yöntemleriyle toplanan profil oluşturma verilerine eklenebilir.  
  
 ![Katman etkileşimi profil oluşturma verileri](../profiling/media/tierinteraction-profilingtools.png "TierInteraction_ProfilingTools")  
Profil Oluşturma Araçları tarafından toplanan katman etkileşim verileri  
  
 [Katman etkileşim verileri toplama](../profiling/collecting-tier-interaction-data.md)  
  
 [Etkileşim Görünümleri](../profiling/tier-interaction-views.md)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: bir Web sitesi için performans verilerini toplama](../profiling/how-to-collect-performance-data-for-a-web-site.md)   
 [Performans profili oluşturma için yeni başlayanlar kılavuzu](../profiling/beginners-guide-to-performance-profiling.md)
