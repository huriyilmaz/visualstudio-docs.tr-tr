---
title: 'DA0039: çok yüksek oranda kilit çekişmeleri | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.performance.39
- vs.performance.DA0039
- vs.performance.rules.DA0039
ms.assetid: 5a9fc57d-9097-413b-af0c-8726b1a57048
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7fcb38184a1d432ca036be88c4d957c0e4d4f419
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/13/2020
ms.locfileid: "75917160"
---
# <a name="da0039-very-high-rate-of-lock-contentions"></a>DA0039: Çok Yüksek Oranda Kilit çakışmaları
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio ile ilgili en son belgeler için bkz. [DA0039: çok yüksek oranda kilit çekişmeleri](/visualstudio/profiling/da0039-very-high-rate-of-lock-contentions).  
  
|||  
|-|-|  
|Kural Kimliği|DA0039|  
|Kategori|.NET Framework kullanımı|  
|Profil oluşturma yöntemleri|Örnekleme<br /><br /> İzleme<br /><br /> .NET belleği|  
|İleti|Çok yüksek oranda .NET kilit çekişmeleri meydana geldiğini belirtir. Lütfen eşzamanlılık profilini çalıştırarak bu kilit çakışmasının nedenini araştırın.|  
|Kural türü|Uyarı|  
  
 Örnekleme, .NET belleği veya kaynak çekişme yöntemlerini kullanarak profil oluşturduğunuzda, bu kuralı tetiklemek için en az 25 örnek toplamanız gerekir.  
  
## <a name="cause"></a>Sebep  
 Profil oluşturma verileriyle toplanan sistem performansı verileri, uygulama yürütme sırasında aşırı yüksek bir kilit çekişmesinin gerçekleştiğini gösterir. Çekişmenin nedenini bulmak için eşzamanlılık profil oluşturma yöntemini kullanarak profil oluşturmayı yeniden düşünün.  
  
## <a name="rule-description"></a>Kural Tanımı  
 Kilitler, çok iş parçacıklı bir uygulamada tek seferde bir iş parçacığı tarafından yürütülmesi gereken önemli kod bölümlerini korumak için kullanılır. Microsoft .NET ortak dil çalışma zamanı (CLR), tam bir eşitleme ve kilitleme temelleri kümesi sağlar. Örneğin, C# dil bir kilit ifadesini (Visual Basic 'de SyncLock) destekler. Yönetilen bir uygulama, doğrudan bir kilit edinmek ve serbest bırakmak için System. Threading ad alanındaki `Monitor.Enter` ve `Monitor.Exit` yöntemleri çağırabilir. .NET Framework, zaman uyumu sağlayıcılar, Readerwriterkilitleri ve semaforları destekleyen sınıflar da dahil olmak üzere ek eşitleme ve kilitleme temel öğelerini destekler. Daha fazla bilgi için, MSDN Web sitesindeki .NET Framework Geliştirici kılavuzundaki [eşitleme temel bilgilerine genel bakış](https://msdn.microsoft.com/library/ms228964.aspx) konusuna bakın. .NET Framework sınıfları, Windows işletim sisteminde yerleşik olarak bulunan alt düzey Eşitleme Hizmetleri üzerinde katmanlıdır. Bunlar, kritik bölüm nesnelerini ve birçok farklı bekleme ve olay sinyali işlevini içerir. Daha fazla bilgi için, MSDN Kitaplığı 'nda Win32 ve COM Geliştirme 'nin [eşitleme](https://msdn.microsoft.com/library/ms686353.aspx) bölümüne bakın.  
  
 Hem .NET Framework sınıfları hem de eşitleme ve kilitleme için kullanılan yerel Windows nesnelerini temel alan, birbirine kenetlenmiş işlemler kullanılarak değiştirilmesi gereken paylaşılan bellek konumlarıdır. Birbirine kenetlenmiş işlemler, Atomik işlemler kullanılarak durumlarını değiştirmek üzere paylaşılan bellek konumlarında çalışan donanıma özgü yönergeler kullanır. Atomik işlemlerin makinedeki tüm işlemciler arasında tutarlı olması garanti edilir. Kilitler ve WaitHandle, otomatik olarak karşılıklı kilitleme işlemlerini ayarlanan veya sıfırlanan zaman kullanan .NET nesneleridir. Uygulamanızda, iş parçacığı güvenli bir biçimde güncelleştirilmesini sağlamak için birbirine kenetlenmiş işlemleri de kullanmanızı gerektiren başka paylaşılan bellek veri yapıları olabilir. Daha fazla bilgi için bkz. MSND kitaplığı 'nın .NET Framework bölümünde, [birbirine kenetlenmiş işlemler](https://msdn.microsoft.com/library/sbhbke0y.aspx)  
  
 Eşitleme ve kilitleme, çok iş parçacıklı uygulamaların doğru şekilde yürütmesini sağlamak için kullanılan mekanizmalarda bulunur. Çok iş parçacıklı bir uygulamanın her iş parçacığı, işletim sistemi tarafından bağımsız olarak zamanlanan bağımsız bir yürütme birimidir. Bir kilit elde edilmeye çalışan bir iş parçacığı gecikmeli tutulduğu için kilit çakışması oluşur.  
  
 Kilitler genellikle iç içe geçmiş. İç içe geçme, kritik bir bölümü yürüten bir iş parçacığı daha sonra başka bir kilit gerektiren bir işlev gerçekleştirdiğinde oluşur. Kilit iç içe geçme miktarı kaçınılmaz. Kritik bölüm, iş parçacığı açısından güvenli olduğundan emin olmak için kilitlerin kullanıldığı bir .NET Framework yöntemi çağırabilir. Uygulamanızdaki bazı kritik bölümden, farklı bir kilit tanıtıcısı kullanarak da kilitleyen bir çerçeve yöntemine yapılan çağrı, kilitlerin iç içe geçmesine neden olur. İç içe kilitleme koşulları, kaçınılması ve düzeltilmesi açısından önemli bir şekilde zor olan performans sorunlarına neden olabilir.  
  
 Bu kural, bir profil oluşturma çalışması sırasında alınan ölçümler, aşırı yüksek miktarda kilit çakışması olduğunu gösteriyorsa ateşlenir. Kilit çekişmeleri, kilidi bekleyen iş parçacıklarının yürütülmesini geciktirecek. Birim testlerinde veya daha düşük bir uçta çalışan yük testlerinde çok az miktarda kilit çakışması araştırılmalıdır.  
  
> [!NOTE]
> Profil oluşturma verilerinde raporlanan kilit çekişmelerinin oranı önemli ancak aşırı olmadığında, bu uyarı iletisi yerine [DA0038: yüksek oranda kilit çekişmeleri](../profiling/da0038-high-rate-of-lock-contentions.md) bilgi iletisi tetiklenir.  
  
## <a name="how-to-investigate-a-warning"></a>Uyarı araştırma  
 Profil oluşturma verilerinin [işaretler](../profiling/marks-view.md) görünümüne gitmek için iletiye çift tıklayın.  **.NET CLR Locksandthreads\çekişme hız/sn** sütununu bulun. Kilit çekişmesinin diğer aşamalara göre daha ağır olduğu program yürütmesinin belirli aşamaları olup olmadığını belirleme.  
  
 Bu kural yalnızca eşzamanlılık profil oluşturma yöntemini kullanmadığınız durumlarda ateşlenir. Eşzamanlılık profili oluşturma yöntemi, uygulamanızdaki kilit çakışması ile ilgili performans sorunlarını tanılamak için kullanılan en iyi araçtır. Uygulamanızın kilitleme davranışını anlamak için eşzamanlılık profili oluşturma verileri toplayın. Bu, hangi kilitlerin çok fazla sürdüğünü, iş parçacığı yürütme zamanının, contenerme kilitleri için ne kadar gecikdiğini ve belirli kodun ne tür bir şekilde olduğunu anlamayı içerir. Eşzamanlılık profilleri, yerel Windows tesislerinin kilitleme davranışı, .NET Framework sınıfları ve uygulamanızın başvurduğu diğer üçüncü taraf kitaplıkları da dahil olmak üzere tüm kilit çekişmeleri üzerinde veri toplar. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] IDE 'den eşzamanlılık profili oluşturma hakkında daha fazla bilgi için bkz. [Iş parçacığı toplama ve eşzamanlılık verilerini işleme](../profiling/collecting-thread-and-process-concurrency-data.md). Komut satırından eşzamanlılık profili oluşturma hakkındaki bilgilerin bağlantıları için, [komut satırından profil oluşturma yöntemlerini kullanma](../profiling/using-profiling-methods-to-collect-performance-data-from-the-command-line.md)konusunun **kaynak çekişmesini ve Iş parçacığı etkinlik verilerini toplamak Için eşzamanlılık yöntemini kullanma** bölümüne bakın.
