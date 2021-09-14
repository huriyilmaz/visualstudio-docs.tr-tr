---
title: DA0039 - Çok Yüksek Oranda Kilit | Microsoft Docs
description: Profil oluşturma verileriyle toplanan sistem performansı verileri, uygulama yürütme sırasında aşırı yüksek bir kilit tartışma oranının meydana geldiğine işaret ediyor.
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.performance.39
- vs.performance.DA0039
- vs.performance.rules.DA0039
ms.assetid: 5a9fc57d-9097-413b-af0c-8726b1a57048
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 00befa5108828b115cf3e69a5f82e3cdf31682cd
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126635782"
---
# <a name="da0039-very-high-rate-of-lock-contentions"></a>DA0039: Çok yüksek oranda kilit içeriği

|Öğe|Değer|
|-|-|
|Kural Kimliği|DA0039|
|Kategori|.NET Framework Kullanım|
|Profil oluşturma yöntemleri|Örnekleme<br /><br /> İzleme<br /><br /> .NET Belleği|
|İleti|Çok yüksek bir .NET Kilidi içeriği oluşuyor. Lütfen bir Eşzamanlılık profili çalıştırarak bu kilit kilitlenmesinin nedenini araştırın.|
|Kural türü|Uyarı|

 Örnekleme, .NET belleği veya kaynak musiki yöntemlerini kullanarak profil 25 örnek toplayan bu kuralı tetiklemeniz gerekir.

## <a name="cause"></a>Nedeni
 Profil oluşturma verileriyle toplanan sistem performansı verileri, uygulama yürütme sırasında aşırı yüksek bir kilit tartışma oranının meydana geldiğine işaret ediyor. İçeriğin nedenini bulmak için eşzamanlılık profil oluşturma yöntemini kullanarak profil oluşturmayı yeniden düşünün.

## <a name="rule-description"></a>Kural açıklaması
 Kilitler, çok iş parçacıklı bir uygulamada aynı anda bir iş parçacığı tarafından seri olarak yürütülebilir kod bölümlerini korumak için kullanılır. Ortak Microsoft .NET Çalışma Zamanı (CLR) tam eşitleme ve kilitleme temelleri kümesi sağlar. Örneğin, C# dili bir kilit deyimini destekler (Visual Basic). Yönetilen bir uygulama, kilidi doğrudan almak ve serbest bırakmak için System.Threading ad alanı içinde Monitor.Enter ve Monitor.Exit yöntemlerini çağırabilirsiniz. Bu .NET Framework, Mutex'leri, ReaderWriterLock'ları ve Semaforları destekleyen sınıflar da dahil olmak üzere ek eşitleme ve kilitleme temellerini destekler. Daha fazla bilgi için MSDN Web [sitesinde .NET Framework](/dotnet/standard/threading/overview-of-synchronization-primitives) Geliştirici Kılavuzu'nun Eşitleme Temellerine Genel Bakış konusuna bakın. Bu .NET Framework sınıfları, işletim sisteminde yerleşik olarak yer alan alt düzey eşitleme Windows katmana sahiptir. Bunlar kritik bölüm nesnelerini ve birçok farklı Bekleme ve olay sinyal işlevlerini içerir. Daha fazla bilgi için MSDN [Kitaplığı'nın](/windows/win32/sync/synchronization) Win32 ve COM Geliştirme'nin Eşitleme bölümüne bakın.

 Eşitleme ve .NET Framework için kullanılan .NET Framework yerel Windows nesneleri, birbirine bağlı işlemler kullanılarak değiştir gereken paylaşılan bellek konumlarıdır. Birbirine bağlı işlemler, atomik işlemler kullanarak durumlarını değiştirmek için paylaşılan bellek konumlarında çalışan donanıma özgü yönergeler kullanır. Atomik işlemlerin makinede tüm işlemcilerde tutarlı olması garantidir. Kilitler ve WaitHandles, ayarlanmış veya sıfırlandıklarında otomatik olarak kilitli işlemler kullanan .NET nesneleridir. Uygulamanıza iş parçacığı güvenli bir şekilde güncelleştirilecek şekilde kilitli işlemler kullanmanızı gerektiren başka paylaşılan bellek veri yapıları da olabilir. Daha fazla bilgi için MSDN [Kitaplığı'nın](/dotnet/api/system.threading.interlocked) .NET Framework Kilitli İşlemler bölümüne bakın.

 Eşitleme ve kilitleme, çok iş parçacıklı uygulamaların doğru şekilde yürütülebilir olmasını sağlamak için kullanılan mekanizmalardır. Çok iş parçacıklı bir uygulamanın her iş parçacığı, işletim sistemi tarafından bağımsız olarak zamanlanan bağımsız bir yürütme birimidir. Kilidi almaya çalışan bir iş parçacığı, kilidi başka bir iş parçacığı tuttuğu için geciktirilirken bir kilit kilitlenmesi oluşur.

 Kilitler sıklıkla iç içe geçmiştir. İç içe yerleştirme, kritik bölümü yürüten bir iş parçacığı başka bir kilit gerektiren bir işlev gerçekleştiriyorsa gerçekleşir. İç içe yerleştirme için bir miktar kilit kaçınılmazdır. Kritik bölümünüz, .NET Framework güvenli olduğundan emin olmak için kilitlere dayanan bir .NET Framework yöntemini çağırabilirsiniz. Uygulamanıza farklı bir kilit tanıtıcısı kullanarak kilitleyen bir Framework yöntemine yapılan bir çağrı, kilitlerin iç içe kilitlenmesine neden olur. İç içe kilitleme koşulları, çözmesi ve çözmesi zor olan performans sorunlarına yol açabilir.

 Profil oluşturma çalıştırması sırasında alınan ölçümler, aşırı yüksek miktarda kilit tartışması olduğunu gösteriyor olduğunda bu kural ortaya çıkar. Kilit içeriği, kilidi bekleyen iş parçacıklarının yürütülmesini geciktirir. Birim testlerinde veya alt uç donanımlarda çalıştırılan yük testlerinde bile oldukça küçük miktarlarda kilit sorunu araştırılması gerekir.

> [!NOTE]
> Profil oluşturma verisinde bildirilen kilit içeriklerinin oranı önemli ancak aşırı [değilken, DA0038:](../profiling/da0038-high-rate-of-lock-contentions.md) Bu uyarı iletisi yerine yüksek oranda kilit içeriği bilgi iletisi çıkar.

## <a name="how-to-investigate-a-warning"></a>Uyarıyı araştırma
 Profil oluşturma verilerinin İşaretler [görünümüne gitmek](../profiling/marks-view.md) için iletiye çift tıklayın.  **.NET CLR LocksAndThreads\Contention Rate / sec sütununu** bulun. Kilitte yer alan ve diğer aşamalardan daha ağır olan belirli program yürütme aşamaları olup olmadığını belirler.

 Bu kural yalnızca eşzamanlılık profil oluşturma yöntemini kullanmamasanız ürkür. Eşzamanlılık profili oluşturma yöntemi, uygulamanıza kilitlemeyle ilgili performans sorunlarını tanılamak için en iyi araçtır. Uygulamanın kilitleme davranışını anlamak için eşzamanlılık profili oluşturma verileri toplayın. Bu, hangi kilitlerin yoğun bir şekilde zorlanan olduğunu, iş parçacığı yürütmenin ne kadar süreyle gecikmiş olduğunu ve hangi kodun örtülü olduğunu anlamayı içerir. Eşzamanlılık profilleri yerel Windows tesislerinin, .NET Framework sınıflarının ve uygulama başvurularının diğer üçüncü taraf kitaplıklarının kilitleme davranışı da dahil olmak üzere tüm kilit içeriklerinde veri toplar. IDE'den eşzamanlılık profili oluşturma hakkında bilgi için bkz. İş [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] [parçacığı toplama ve eşzamanlılık verilerini işleme.](../profiling/collecting-thread-and-process-concurrency-data.md) Komut satırdan eşzamanlılık profili oluşturma hakkında bilgi için,  Komut satırı profil oluşturma yöntemlerini kullanma bölümünün Kaynak ve iş parçacığı etkinlik verilerini toplamak için eşzamanlılık yöntemini kullanma bölümüne [bakın.](../profiling/using-profiling-methods-to-collect-performance-data-from-the-command-line.md)
