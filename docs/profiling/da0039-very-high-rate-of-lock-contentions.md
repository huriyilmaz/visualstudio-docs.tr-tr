---
title: 'DA0039: Kilit çekişmeleri Çok Yüksek Oranda | Microsoft Dokümanlar'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.39
- vs.performance.DA0039
- vs.performance.rules.DA0039
ms.assetid: 5a9fc57d-9097-413b-af0c-8726b1a57048
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: f64f717bf87fb4636c7c2f4e6f11a08236d08ada
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779369"
---
# <a name="da0039-very-high-rate-of-lock-contentions"></a>DA0039: Kilit çekişmeleri çok yüksek oranda

|||
|-|-|
|Kural Id|DA0039|
|Kategori|.NET Çerçeve Kullanımı|
|Profil oluşturma yöntemleri|Örnekleme<br /><br /> İzleme<br /><br /> .NET Bellek|
|İleti|Çok yüksek bir .NET Kilit çekişmeoranı meydana geliyor. Lütfen bir Eşzamanlılık profili çalıştırarak bu kilit çekişmesinin nedenini araştırın.|
|Kural türü|Uyarı|

 Örnekleme, .NET bellek veya kaynak çekişme yöntemlerini kullanarak profil yaptığınızda, bu kuralı tetiklemek için en az 25 örnek toplamanız gerekir.

## <a name="cause"></a>Nedeni
 Profil oluşturma verileriyle toplanan sistem performans verileri, uygulama yürütme sırasında aşırı yüksek oranda kilit çekişmesi oluştuğunu gösterir. Çekişmenedenini bulmak için eşzamanlılık profil oluşturma yöntemini kullanarak yeniden profil oluşturmayı düşünün.

## <a name="rule-description"></a>Kural açıklaması
 Kilitler, çok iş parçacığı uygulamasında tek bir iş parçacığı tarafından seri olarak yürütülmesi gereken kodun kritik bölümlerini korumak için kullanılır. Microsoft .NET Ortak Dil Çalışma zamanı (CLR), ilkel leri tam bir eşitleme ve kilitleme kümesi sağlar. Örneğin, C# dili bir kilit deyimini destekler (Visual Basic'te SyncLock). Yönetilen bir uygulama, doğrudan bir kilit elde etmek ve serbest bırakmak için System.Threading ad alanında Monitor.Enter ve Monitor.Exit yöntemlerini arayabilir. .NET Framework, Mutexes, ReaderWriterLocks ve Semaforları destekleyen sınıflar da dahil olmak üzere ek senkronizasyon ve kilitleme ilkelleri destekler. Daha fazla bilgi için MSDN Web sitesindeki .NET Framework Developer Kılavuzu'ndaki [Senkronizasyon İlkellerine Genel Bakış](/dotnet/standard/threading/overview-of-synchronization-primitives) bölümüne bakın. .NET Framework sınıfları, Windows işletim sisteminde yerleşik olarak yerleşik alt düzey eşitleme hizmetleri üzerinde katmanlanır. Bunlar kritik bölüm nesneleri ve birçok farklı Bekle ve olay sinyali işlevleri içerir. Daha fazla bilgi için, MSDN Kitaplığı'ndaki Win32 ve COM Geliştirme'nin [Eşitleme](/windows/win32/sync/synchronization) bölümüne bakın.

 Eşitleme ve kilitleme için kullanılan .NET Framework sınıflarının ve yerel Windows nesnelerinin altında yatan ortak bellek konumları, birbirine kenetlenmiş işlemler kullanılarak değiştirilmesi gereken ortak bellek konumlarıdır. Birbirine kenetlenmiş işlemler, atomik işlemleri kullanarak durumlarını değiştirmek için paylaşılan bellek konumlarında çalışan donanıma özgü yönergeler kullanır. Atomik işlemlerin makinedeki tüm işlemciler arasında tutarlı olacağı garanti edilir. Kilitler ve Bekleme Tutamaçları, ayarlandığında veya sıfırlandığında kilitli işlemleri otomatik olarak kullanan .NET nesneleridir. Uygulamanızda iş parçacığı güvenli bir şekilde güncelleştirilmek üzere kilitli işlemleri kullanmanızı gerektiren başka paylaşılan bellek veri yapıları da olabilir. Daha fazla bilgi için MSDN Kitaplığı'nın .NET Framework bölümünde [Kilitli İşlemler](/dotnet/api/system.threading.interlocked) bölümüne bakın.

 Eşitleme ve kilitleme, çoklu iş parçacığı uygulamalarının doğru yürütülmesini sağlamak için kullanılan mekanizmalardır. Çok iş parçacığı uygulamasının her iş parçacığı, işletim sistemi tarafından bağımsız olarak zamanlanan bağımsız bir yürütme birimidir. Başka bir iş parçacığı kilidi tuttuğundan, kilit elde etmeye çalışan bir iş parçacığı geciktiğinde kilit çekişmesi oluşur.

 Kilitler sık sık iç içe dir. İç içe geçme, kritik bir bölümü çalıştıran bir iş parçacığı daha sonra başka bir kilit gerektiren bir işlev gerçekleştirdiğinde oluşur. Kilit yuvalama bir miktar kaçınılmazdır. Kritik bölümünüz, iş parçacığının güvenli olduğundan emin olmak için kilitlere dayanan bir .NET Framework yöntemi ni çağırabilir. Uygulamanızdaki bazı kritik bölümden farklı bir kilit tutamacı kullanarak kilitleyen bir Framework yöntemine yapılan çağrı, kilitleri yuvaya yerleştirmeye neden olur. İç içe kilitleme koşulları, çözülmesi ve düzeltilmesi çok zor olan performans sorunlarına yol açabilir.

 Profil oluşturma çalışması sırasında alınan ölçümler aşırı yüksek miktarda kilit çekişmesi olduğunu gösterdiğinde bu kural yangınları. Kilit çekişmeleri kilit bekleyen iş parçacıklarının yürütülmesini geciktirir. Birim testlerinde veya alt uç donanımüzerinde çalışan yük testlerinde bile oldukça az miktarda kilit çekişmesi araştırılmalıdır.

> [!NOTE]
> Profil oluşturma verilerinde bildirilen kilit çekişmelerinin oranı önemli ancak aşırı olmadığında, [DA0038:](../profiling/da0038-high-rate-of-lock-contentions.md) Bu uyarı iletisi yerine yüksek oranda kilit çekişmeleri bilgi iletisi ateşlenir.

## <a name="how-to-investigate-a-warning"></a>Bir uyarı nasıl araştırılı
 Profil oluşturma verilerinin [Markalar](../profiling/marks-view.md) görünümüne gitmek için iletiyi çift tıklatın.  **.NET CLR LocksAndThreads\Çekişme Oranı / sn** sütununu bulun. Kilit çekişmesinin diğer aşamalardan daha ağır olduğu program yürütmebelirli aşamaları olup olmadığını belirleyin.

 Bu kural yalnızca eşzamanlılık profil oluşturma yöntemini kullanmadığınızda çalınır. Eşzamanlılık profil oluşturma yöntemi, uygulamanızdaki kilit çekişmesi ile ilgili performans sorunlarını tanılamak için kullanılacak en iyi araçtır. Uygulamanızın kilitleme davranışını anlamak için eşzamanlılık profil oluşturma verileri toplayın. Bu, hangi kilitlerin yoğun olarak engellendiği, iş parçacığı yürütme süresinin ne kadar geciktiğini ve hangi belirli kodun karıştığını anlamayı içerir. Eşzamanlılık profilleri, yerel Windows tesislerinin kilitleme davranışı, .NET Framework sınıfları ve uygulama başvurularınızın diğer üçüncü taraf kitaplıkları da dahil olmak üzere tüm kilit çekişmeleri hakkında veri toplar. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE'den eşzamanlılık profil oluşturma hakkında bilgi için [bkz.](../profiling/collecting-thread-and-process-concurrency-data.md) Komut satırından eşzamanlılık profiloluşturma yla ilgili bilgilere bağlantılar için, komut satırından **kaynak çekişmesi ve iş parçacığı etkinlik verisi toplamak için eşzamanlılık yöntemini kullanın** [yöntemine](../profiling/using-profiling-methods-to-collect-performance-data-from-the-command-line.md)bakın.
