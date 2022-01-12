---
title: Profil oluşturma araçlarına ilk bakış
description: Visual Studio ' de bulunan farklı tanılama araçlarına kısa bir bakış göz atın.
ms.date: 12/22/2021
ms.topic: conceptual
f1_keywords:
- vs.diagnosticshub.overview
dev_langs:
- CSharp
helpviewer_keywords:
- diagnostic tools
ms.assetid: d2ee0301-ea78-43d8-851a-71b7b2043d73
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 7c27902bfe4d59667d1ea852589d07358ff16662
ms.sourcegitcommit: ffd1bea76b51fd6b43d484a30bbd1e674f0ae49b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/27/2021
ms.locfileid: "135563837"
---
# <a name="first-look-at-profiling-tools"></a>Profil oluşturma araçlarına ilk bakış

Visual Studio, uygulama türüne bağlı olarak farklı türlerde performans sorunlarını tanılamanıza yardımcı olacak çeşitli profil araçları sağlar. Bu makalede, en yaygın profil oluşturma araçlarına hızlı bir bakış sunuyoruz.

Farklı uygulama türleri için profil oluşturma araç desteğini görmek için bkz. [hangi aracı kullanmalıyım?](#which-tool-should-i-use)

## <a name="measure-performance-while-debugging"></a>Hata ayıklarken performansı ölçme

Hata ayıklama oturumu sırasında erişebileceğiniz profil oluşturma araçları Tanılama Araçları penceresinde kullanılabilir. Tanılama Araçları penceresi devre dışı bırakılmadığı takdirde otomatik olarak görünür. pencereyi getirmek için **hata ayıkla/Windows/göster Tanılama Araçları** (veya **Ctrl**  +  **Alt**  +  **F2** tuşlarına basın) seçeneğine tıklayın. Pencereyi açık olarak kullanarak veri toplamak istediğiniz araçları seçebilirsiniz.

::: moniker range=">=vs-2022"
![Tanılama Araçları penceresi](../profiling/media/vs-2022/prof-tour-diagnostic-tools.png "Tanılama Araçları")
::: moniker-end
::: moniker range="<=vs-2019"
![Tanılama Araçları penceresi](../profiling/media/prof-tour-diagnostic-tools.png "Tanılama Araçları")
::: moniker-end

Hata ayıklarken, CPU ve bellek kullanımını çözümlemek için **Tanılama araçları** penceresini kullanabilir ve performansla ilgili bilgileri gösteren olayları görüntüleyebilirsiniz.

::: moniker range=">=vs-2022"
![Tanılama Araçları Özet görünümü](../profiling/media/vs-2022/prof-tour-cpu-and-memory-graph.png "Tanılama Araçları Özeti")
::: moniker-end
::: moniker range="<=vs-2019"
![Tanılama Araçları Özet görünümü](../profiling/media/prof-tour-cpu-and-memory-graph.gif "Tanılama Araçları Özeti")
::: moniker-end

**Tanılama araçları** pencere, uygulamaları profil oluşturmanın yaygın bir yoludur, ancak yayın yapıları için bunun yerine uygulamanızın mordıtem analizini de yapabilirsiniz. Farklı yaklaşımlar hakkında daha fazla bilgi için bkz. [hata ayıklayıcı ile veya olmadan profil oluşturma araçlarını çalıştırma](../profiling/running-profiling-tools-with-or-without-the-debugger.md). Farklı uygulama türleri için profil oluşturma araç desteğini görmek için bkz. [hangi aracı kullanmalıyım?](#which-tool-should-i-use)

Tanılama Araçları penceresinde veya hata ayıklama oturumu sırasında bulunan araçlar şunları içerir:
- [CPU kullanımı](../profiling/beginners-guide-to-performance-profiling.md)
- [Bellek kullanımı](../profiling/memory-usage.md)
- [PerfTips](../profiling/perftips.md)

> [!NOTE]
> hata ayıklayıcı (**Tanılama Araçları** penceresi) ile profil oluşturma araçlarını çalıştırmak için Windows 8 ve üzeri gereklidir. Windows 7 ve sonraki sürümleri ile [mortem](#post_mortem) araçları 'nı kullanabilirsiniz. 

## <a name="measure-performance-in-release-builds"></a><a name="post_mortem"></a> Yayın yapılarında performansı ölçme

Performans Profiler 'daki Araçlar **yayın** derlemeleri için analiz sağlamak üzere tasarlanmıştır. Performans Profiler 'da, uygulama çalışırken tanılama bilgilerini toplayabilir ve ardından uygulama durdurulduktan sonra toplanan bilgileri inceleyebilirsiniz (bir post-mordıtem Analizi).

**Hata ayıklama**  >  **performansı profil oluşturucuyu** (veya **alt + f2**) seçerek performans profil oluşturucuyu açın.

::: moniker range=">=vs-2022"
![Performans Profili Oluşturucu](../profiling/media/vs-2022/prof-tour-performance-profiler.png "Performans Profili Oluşturucu")
::: moniker-end
::: moniker range="<=vs-2019"
![Performans Profili Oluşturucu](../profiling/media/prof-tour-performance-profiler.png "Performans Profili Oluşturucu")
::: moniker-end

Performans Profiler 'da CPU kullanımı veya bellek kullanımı aracını kullanma hakkında daha fazla bilgi için bkz. hata ayıklayıcı ile tümleşik araçlar, bkz. [profil oluşturma araçlarını hata ayıklayıcı ile veya olmadan çalıştırma](../profiling/running-profiling-tools-with-or-without-the-debugger.md). 

Performans Profiler 'da bulunan araçlar şunları içerir:

- [CPU kullanımı](../profiling/cpu-usage.md)
- [.NET nesne ayırma](../profiling/dotnet-alloc-tool.md)
- [Bellek kullanımı](../profiling/memory-usage-without-debugging2.md)
- [.NET Async aracı](../profiling/analyze-async.md)
- [Veritabanı aracı](../profiling/analyze-database.md)
- [GPU kullanımı](../profiling/gpu-usage.md)

Farklı uygulama türleri için profil oluşturma araç desteğini görmek için bkz. [hangi aracı kullanmalıyım?](#which-tool-should-i-use)

Bazı senaryolarda, pencere [birden çok profil oluşturma aracı](../profiling/use-multiple-profiler-tools-simultaneously.md)seçmenize olanak sağlar. CPU kullanımı gibi araçlar, analizinizdeki yardım için kullanabileceğiniz tamamlayıcı veriler sağlayabilir. Birden çok profil oluşturma aracı içeren senaryoları etkinleştirmek için [komut satırı profil oluşturucuyu](../profiling/profile-apps-from-command-line.md) de kullanabilirsiniz.

## <a name="examine-performance-using-perftips"></a>PerfTips kullanarak performansı inceleyin

Genellikle, performans bilgilerini görüntülemenin en kolay yolu [PerfTips](../profiling/perftips.md)kullanmaktır. PerfTips kullanarak, kodunuzla etkileşim kurarken performans bilgilerini görüntüleyebilirsiniz. Olayın süresi (hata ayıklayıcının en son ne zaman duraklatıldığı veya uygulama başlatıldığında ölçülür) gibi bilgileri denetleyebilirsiniz. Örneğin, kod (F10, F11) ile adımlayın, PerfTips, önceki adım işleminden geçerli adıma uygulama çalışma zamanı süresini gösterir.

::: moniker range=">=vs-2022"
![Profil oluşturma turu PerfTips](../profiling/media/vs-2022/prof-tour-perf-tips.png "Profil Oluşturma Turu PerfTips")
::: moniker-end
::: moniker range="<=vs-2019"
![Profil oluşturma turu PerfTips](../profiling/media/prof-tour-perf-tips.png "Profil Oluşturma Turu PerfTips")
::: moniker-end

Bir kod bloğunun yürütülmesi için ne kadar sürdüğünü veya tek bir işlevin tamamlaması için ne kadar sürdüğünü incelemek için PerfTips 'ı kullanabilirsiniz.

PerfTips, Tanılama Araçları **Olaylar** görünümünde de görüntülenen olayları gösterir. **Olaylar** görünümünde, hata ayıklama sırasında oluşan farklı olayları (kesme noktası veya kod atlama işlemi gibi) görüntüleyebilirsiniz.

::: moniker range=">=vs-2022"
![Tanılama Araçları Olaylar görünümü](../profiling/media/vs-2022/prof-tour-events.png "Tanılama Araçları Görüntüleme")
::: moniker-end
::: moniker range="<=vs-2019"
![Tanılama Araçları Olaylar görünümü](../profiling/media/prof-tour-events.png "Tanılama Araçları Görüntüleme")
::: moniker-end

 > [!NOTE]
 > Visual Studio Enterprise sahipseniz, bu sekmede [ıntellitrace olaylarını](../debugger/intellitrace.md) da görebilirsiniz.

## <a name="analyze-cpu-usage"></a>CPU kullanımını analiz etme

CPU kullanımı aracı, uygulamanızın performansını çözümlemeye başlamak için iyi bir yerdir. Uygulamanızın kullandığı CPU kaynakları hakkında daha fazla bilgi sağlayacaktır. [Hata ayıklayıcı ile TÜMLEŞIK CPU kullanımı aracını](../profiling/beginners-guide-to-performance-profiling.md) veya [mortem CPU kullanımı aracını](../profiling/cpu-usage.md)kullanabilirsiniz.

hata ayıklayıcı ile tümleşik CPU kullanımı aracını kullanırken, tanılama araç penceresini açın (kapalıysa, **hata ayıkla/Windows/Tanılama Araçları göster**' i seçin). Hata ayıklama sırasında  **Özet** görünümünü açın ve **CPU profilini kaydet**' i seçin.

::: moniker range=">=vs-2022"
![Tanılama Araçları CPU kullanımını etkinleştir](../profiling/media/vs-2022/prof-tour-enable-cpu-profiling.png "Tanılama Araçları CPU Kullanımını Etkinleştirme")
::: moniker-end
::: moniker range="<=vs-2019"
![Tanılama Araçları CPU kullanımını etkinleştir](../profiling/media/prof-tour-enable-cpu-profiling.png "Tanılama Araçları CPU Kullanımını Etkinleştirme")
::: moniker-end

Araç kullanmanın bir yolu kodunuzda iki kesme noktası, bir diğeri de işlevin sonunda veya bir ya da analiz etmek istediğiniz kod bölgesi ayarlamak kullanmaktır. İkinci kesme noktasında durakladığınızda profil oluşturma verilerini inceleyin.

::: moniker range=">=vs-2022"
**CPU kullanımı** görünümü, en üst **işlevlerde** en üstte çalışan işlev ile en uzun çalışan tarafından sıralanan işlevlerin bir listesini gösterir. **Etkin yol** bölümü, en fazla CPU kullanan işlevler için çağrı yığınını gösterir. Bu listeler, performans sorunlarının gerçekleştiği işlevlerde size rehberlik etmenize yardımcı olabilir.

![Tanılama Araçları CPU kullanımı görünümü](../profiling/media/vs-2022/prof-tour-cpu-usage.png "Tanılama Araçları CPU Kullanımı")
::: moniker-end
::: moniker range="<=vs-2019"

**CPU kullanımı** görünümü, en uzun çalışan bir işlevle en üstte bulunan işlevlerin bir listesini gösterir. Bu, performans sorunlarının gerçekleştiği işlevlerde size rehberlik etmenize yardımcı olabilir.

![Tanılama Araçları CPU kullanımı görünümü](../profiling/media/prof-tour-cpu-usage.png "Tanılama Araçları CPU Kullanımı")
::: moniker-end

::: moniker range=">=vs-2022"
İlgilendiğiniz bir işleve çift tıklayın ve seçilen işlevin vurgulandığı daha ayrıntılı bir "çağrı ağacı" görünümü görürsünüz. Tablo, çağrılan işlevler (**toplam CPU**) dahil olmak üzere, işlevde harcanan süre ve çağrılan Işlevler (**self CPU**) hariç olmak üzere bir işlevde harcanan süreyi gösteren ikinci bir sütun gibi verileri içeren sütunları gösterir. Bu veriler, işlevin kendisinin performans sorunu olup olmadığını değerlendirmenize yardımcı olabilir.

![Tanılama Araçları arayan "kelebek" görünümü](../profiling/media/vs-2022/prof-tour-call-tree-view.png "Tanılama Araçları Çağıran Görünümü")
::: moniker-end
::: moniker range="<=vs-2019"
İlgilendiğiniz bir işleve çift tıklayın ve seçilen işlevle pencerenin ortasında, sol taraftaki çağırma işlevine ve sağ tarafta işlev olarak adlandırılan daha ayrıntılı üç bölmeli "kelebek" görünümü görürsünüz. **Işlev gövdesi** bölümü, işlev gövdesinde harcanan ve çağrılan işlevlerde harcanan süre hariç toplam süreyi (ve zaman yüzdesini) gösterir. Bu veriler, işlevin kendisinin performans sorunu olup olmadığını değerlendirmenize yardımcı olabilir.

![Tanılama Araçları arayan "kelebek" görünümü](../profiling/media/prof-tour-cpu-usage-caller-callee.png "Tanılama Araçları Çağıran Görünümü")
::: moniker-end

## <a name="analyze-memory-usage"></a>Bellek kullanımını analiz etme

**Tanılama araçları** penceresi, **bellek kullanımı** aracını kullanarak uygulamanızdaki bellek kullanımını değerlendirmenize de olanak tanır. Örneğin, yığındaki nesnelerin sayısına ve boyutuna bakabilirsiniz. Performans Profiler 'daki [hata ayıklayıcı ile tümleşik bellek kullanımı aracını](../profiling/memory-usage.md) veya [mortem bellek kullanımı aracını](../profiling/memory-usage-without-debugging2.md) kullanabilirsiniz.

.NET geliştiricileri, [.NET nesne ayırma aracı](../profiling/dotnet-alloc-tool.md) ya da [bellek kullanımı](../profiling/memory-usage.md) aracı arasında seçim gösterebilir.

- **.NET nesne ayırma** Aracı, .net kodunuzda ayırma düzenlerini ve anormallikleri belirlemenize yardımcı olur ve çöp toplama ile ilgili yaygın sorunları belirlemenize yardımcı olur. Bu araç yalnızca bir post-mordıtem aracı olarak çalışır. Bu aracı, yerel veya uzak makinelerde çalıştırabilirsiniz.
- **Bellek kullanımı** Aracı, genellikle .NET uygulamalarında yaygın olmayan bellek sızıntılarını tanımlamaya yardımcı olur. Bellek denetlenirken hata ayıklayıcı özelliklerini kod üzerinden atlama gibi kullanmanız gerekiyorsa, [hata ayıklayıcı ile tümleşik bellek kullanım](../profiling/beginners-guide-to-performance-profiling.md) aracı önerilir.

Bellek **kullanımı** aracı ile bellek kullanımını çözümlemek için en az bir bellek anlık görüntüsü yapmanız gerekir. Genellikle belleği çözümlemenin en iyi yolu iki anlık görüntü alma yöntemidir; bir şüpheli bellek sorunundan önceki ilk sağ tarafta ve bir şüpheli bellek sorunu oluştuktan sonra ikinci anlık görüntü. Daha sonra, iki anlık görüntüye ilişkin bir farkı görüntüleyebilir ve tam olarak nelerin değiştiğini görebilirsiniz. Aşağıdaki çizimde, hata ayıklayıcı ile tümleşik aracı ile anlık görüntü alma gösterilmektedir.

::: moniker range=">=vs-2022"
![Tanılama Araçları anlık görüntü alın](../profiling/media/vs-2022/prof-tour-take-snapshot.png "Tanılama Araçları Anlık Görüntü Alma")
::: moniker-end
::: moniker range="<=vs-2019"
![Tanılama Araçları anlık görüntü alın](../profiling/media/prof-tour-take-snapshots.gif "Tanılama Araçları Anlık Görüntü Alma")
::: moniker-end

Ok bağlantılarından birini seçtiğinizde, yığının fark görünümü verilir (kırmızı yukarı ok ![bellek kullanımı artışı](../profiling/media/prof-tour-mem-usage-up-arrow.png "Bellek Kullanımı Artışı") , artan nesne sayısını (solda) veya artan yığın boyutunu (sağ) gösterir). Doğru bağlantıya tıklarsanız, yığın boyutunu en çok arttığı nesnelere göre sıralanmış bir fark yığın görünümü alırsınız. Bu, bellek sorunlarını belirlemenize yardımcı olabilir. Örneğin, aşağıdaki çizimde, nesneler tarafından kullanılan baytlar ikinci anlık `ClassHandlersStore` görüntüde 3.492 bayt artmıştır.

::: moniker range=">=vs-2022"
![Tanılama Araçları yığın fark görünümü](../profiling/media/vs-2022/prof-tour-mem-usage-diff-heap.png "Tanılama Araçları Yığın Fark görünümü")
::: moniker-end
::: moniker range="<=vs-2019"
![Tanılama Araçları yığın fark görünümü](../profiling/media/prof-tour-mem-usage-diff-heap.png "Tanılama Araçları Yığın Fark görünümü")
::: moniker-end

Bellek Kullanımı görünümünde bunun yerine sol  tarafta yer alan bağlantıya tıklarsanız yığın görünümü nesne sayısına göre düzenlenmiştir; Sayı olarak en fazla artıran belirli bir türdeki nesneler en üstte gösterilir (Sayı Fark **sütununa göre sıralanmış).**

## <a name="analyze-resource-consumption-xaml"></a>Kaynak tüketimini analiz etme (XAML)

Masaüstü WPF uygulamaları Windows UWP uygulamaları gibi XAML uygulamalarında kaynak tüketimini analiz etmek için Uygulama Zaman Çizelgesi kullanabilirsiniz. Örneğin, kullanıcı arabirimi çerçeveleri (düzen ve işleme), ağ ve disk isteklerine hizmet verme ve uygulama başlatma, sayfa yükleme ve Pencere yeniden boyutlandırma gibi senaryolarda, uygulamanın kullanıcı arabirimi çerçevelerini hazırlaması için harcadığı zamanı analiz edebilirsiniz. Aracı kullanmak için, araç **Uygulama Zaman Çizelgesi'Performans Profili Oluşturucu** başlat'ı **seçin.** Uygulamanıza, şüpheli bir kaynak tüketimi sorunuyla ilgili senaryoyu gidin ve ardından Raporu oluşturmak için **Koleksiyonu durdur'a** seçin.

Görsel aktarım hızı **grafı'nın düşük** kare hızı, uygulamanızı çalıştırarak gördüğünüz görsel sorunlara karşılık gelir. Benzer şekilde, kullanıcı arabirimi iş parçacığı **kullanım grafı içinde yüksek** sayılar kullanıcı arabirimi yanıt verme sorunlarına da karşılık geliyor olabilir. Raporda, şüpheli performans sorunu olan bir zaman dönemi seçin ve ardından Zaman Çizelgesi ayrıntıları görünümünde (alt bölme) ayrıntılı kullanıcı arabirimi iş parçacığı etkinliklerini inceleyebilirsiniz.

::: moniker range=">=vs-2022"
![Uygulama Zaman Çizelgesi profili oluşturma aracı](../profiling/media/vs-2022/prof-tour-application-timeline.png "Profil Oluşturma Turu Uygulama Zaman Çizelgesi")
::: moniker-end
::: moniker range="<=vs-2019"
![Uygulama Zaman Çizelgesi profili oluşturma aracı](../profiling/media/prof-tour-application-timeline.gif "Profil Oluşturma Turu Uygulama Zaman Çizelgesi")
::: moniker-end

Zaman çizelgesi ayrıntıları görünümünde etkinlik türü (veya dahil olan kullanıcı arabirimi öğesi) gibi bilgileri etkinliğin süresiyle birlikte bulabilirsiniz. Örneğin çizimde Bir Kılavuz denetimi **için Düzen** olayı 57,53 ms alır.

Daha fazla bilgi için [bkz. Uygulama Zaman Çizelgesi.](../profiling/application-timeline.md)

::: moniker range=">=vs-2022"
## <a name="analyze-asynchronous-code-net"></a>Zaman uyumsuz kodu analiz etme (.NET)

.NET Async [aracı,](../profiling/analyze-async.md) uygulamanıza zaman uyumsuz kodun performansını analiz etmenize olanak sağlar. Bu araç, Performans Profili Oluşturucu. Hata ayıkla Performans Profili Oluşturucu **(veya**  >  Alt + F2)**Performans Profili Oluşturucu** **seçerek dosyayı açın.**

Araç, zaman uyumsuz her işlemi bir liste görünümünde gösterir. Zaman uyumsuz bir işlem için başlangıç saati, bitiş saati ve toplam süre gibi bilgileri görebilir.

![.NET Async Aracı Durduruldu](../profiling/media/vs-2022/prof-tour-async-tool.png ".NET Async Aracı Durduruldu")
::: moniker-end

::: moniker range="vs-2019"
## <a name="analyze-asynchronous-code-net"></a>Zaman uyumsuz kodu analiz etme (.NET)

.NET Async [aracı,](../profiling/analyze-async.md) uygulamanıza zaman uyumsuz kodun performansını analiz etmenize olanak sağlar. Bu araç, Performans Profili Oluşturucu. Hata ayıkla Performans Profili Oluşturucu **(veya**  >  Alt + F2)**Performans Profili Oluşturucu** **seçerek dosyayı açın.**

Araç, zaman uyumsuz her işlemi bir liste görünümünde gösterir. Zaman uyumsuz bir işlem için başlangıç saati, bitiş saati ve toplam süre gibi bilgileri görebilir.

![.NET Async Aracı Durduruldu](../profiling/media/async-tool-opened.png ".NET Async Aracı Durduruldu")
::: moniker-end

::: moniker range=">=vs-2019"

## <a name="examine-application-events"></a>Uygulama olaylarını inceleme

Genel olaylar [görüntüleyicisi,](../profiling/events-viewer.md) uygulamanın etkinliklerini modül yükü, iş parçacığı başlatma ve sistem yapılandırmaları gibi olayların bir listesi aracılığıyla görüntülemenize olanak tanılar ve bu sayede uygulamanın profil Visual Studio tanılar. Bu araç, Performans Profili Oluşturucu. Hata ayıkla Performans Profili Oluşturucu **(veya**  >  Alt + F2)**Performans Profili Oluşturucu** **seçerek dosyayı açın.**

Araç, her olayı bir liste görünümünde gösterir. Sütunlar olay adı, zaman damgası ve işlem kimliği gibi her olay hakkında bilgi sağlar.

![Olay Görüntüleyicisi İzleme](../profiling/media/prof-tour-events-viewer.png "Olay Görüntüleyicisi İzleme")

## <a name="analyze-database-performance-net-core"></a>Veritabanı performansını analiz etme (.NET Core)

Veritabanı aracı, ADO.NET veya Entity Framework Core kullanan .NET Core [](../profiling/analyze-database.md) uygulamaları için, tanılama oturumu sırasında uygulamanıza yapılan veritabanı sorgularını kaydetmenize olanak sağlar. Ardından tek tek sorgularla ilgili bilgileri analiz edip, uygulama performansının geliştirilebilir olduğu yerleri bulabilirsiniz. Bu araç, Performans Profili Oluşturucu. Hata ayıkla Performans Profili Oluşturucu **(veya**  >  Alt + F2)**Performans Profili Oluşturucu** **seçerek dosyayı açın.**

Araç, her sorguyu bir liste görünümünde gösterir. Sorgu başlangıç zamanı ve süresi gibi bilgileri görebilir.

![Ayırma](./media/db-gotosource.png "Ayırma")

## <a name="visualize-net-counters-net-core"></a>.NET sayaçlarını görselleştirme (.NET Core)

2019 Visual Studio 16.7 sürümünden başlayarak, performans sayaçlarını görselleştirmek için [.NET](../profiling/dotnet-counters-tool.md) Sayaçları Visual Studio aracını kullanabilirsiniz. dotnet sayaçları kullanılarak oluşturulan [sayaçları görselleştirin.](/dotnet/core/diagnostics/dotnet-counters) dotnet sayaçları CPU kullanımı ve atık toplayıcı yığın boyutu gibi birçok sayacı destekler.

Araç, bir liste görünümünde her sayacın canlı değerlerini gösterir.

:::image type="content" source="../profiling/media/dotnet-counters-tool-collecting.png" alt-text=".NET Sayaç aracı toplama.":::

::: moniker-end

## <a name="examine-ui-performance-and-accessibility-events-uwp"></a>UI performans ve erişilebilirlik olaylarını inceleme (UWP)

UWP uygulamalarınız için Kullanıcı Arabirimi **Analizi'Tanılama Araçları** **etkinleştirebilirsiniz.** Araç, yaygın performans veya erişilebilirlik sorunlarını arar ve hata **ayıklarken** bunları Olaylar görünümünde görüntüler. Olay açıklamaları sorunları çözmenize yardımcı olacak bilgiler sağlar.

::: moniker range=">=vs-2022"
![Tanılama araçlarında kullanıcı arabirimi analizi olaylarını görüntüleme](../profiling/media/vs-2022/prof-tour-ui-analysis.png "Tanılama Araçları Ui Çözümleme Olaylarını Görüntüleme")
::: moniker-end
::: moniker range="<=vs-2019"
![Tanılama araçlarında kullanıcı arabirimi analizi olaylarını görüntüleme](../profiling/media/prof-tour-ui-analysis.png "Tanılama Araçları Ui Çözümleme Olaylarını Görüntüleme")
::: moniker-end

## <a name="analyze-gpu-usage-direct3d"></a>GPU Kullanımını Analiz Etme (Direct3D)

Direct3D uygulamaları içinde (Direct3D bileşenleri C++ içinde olmalı), GPU'daki etkinliği inceler ve performans sorunlarını analiz edersiniz. Daha fazla bilgi için bkz. [GPU Kullanımı.](./gpu-usage.md) Aracı kullanmak için grafikte **GPU Kullanımı'nı** Performans Profili Oluşturucu başlat'ı **seçin.** Uygulamanıza profil oluşturmak istediğiniz senaryoyu takip edin ve ardından Koleksiyonu **durdur'a** seçerek bir rapor oluşturabilirsiniz.

Grafiklerde bir zaman dönemi ve görünüm ayrıntılarını seçtiğiniz **zaman** alt bölmede ayrıntılı bir görünüm görünür. Ayrıntılı görünümde, her CPU ve GPU üzerinde ne kadar etkinlik olduğunu incelersiniz. Zaman çizelgesinde açılan pencereleri almak için en düşük bölmede olayları seçin. Örneğin, Çağrı açılır **pencerelerini** sun'ı **görüntülemek için Olayı** sun'ı seçin. (Açık gri dikey VSync satırları, belirli Mevcut çağrıların VSync'i kaçırıp kaçırmamalarını anlamak **için** başvuru olarak kullanılabilir. Uygulamanın kararlı **bir şekilde** 60 KARE/sn'ye isabet etmek için her iki VSync arasında bir Mevcut çağrısı olmalıdır.)

::: moniker range=">=vs-2022"
![GPU Kullanımı profil oluşturma aracı](../profiling/media/vs-2022/prof-tour-gpu-usage.png "GPU Kullanımını Tanılama")
::: moniker-end
::: moniker range="<=vs-2019"
![GPU Kullanımı profil oluşturma aracı](../profiling/media/prof-tour-gpu-usage.png "GPU Kullanımını Tanılama")
::: moniker-end

Grafikleri ayrıca CPU'ya bağlı veya GPU'ya bağlı performans sorunları olup olmadığını belirlemek için de kullanabilirsiniz.

::: moniker range="vs-2017"
## <a name="analyze-performance-javascript-uwp"></a>Performansı analiz etme (JavaScript UWP)

UWP uygulamaları için JavaScript Bellek aracını ve HTML KULLANıCı Arabirimi Yanıt Hızı aracını kullanabilirsiniz.

JavaScript Bellek aracı, diğer uygulama türleri için kullanılabilen Bellek Kullanımı aracına benzer. Uygulamanıza bellek kullanımını anlamak ve bellek sızıntılarını bulmak için bu aracı kullanabilirsiniz. Araç hakkında daha fazla ayrıntı için bkz. [JavaScript Belleği.](../profiling/javascript-memory.md)

![JavaScript Bellek profili oluşturma aracı](../profiling/media/diagjsmemory.png "DiagJSMemory")

UWP uygulamalarında kullanıcı arabirimi yanıt hızını, yavaş yükleme süresi ve yavaş görsel güncelleştirmelerini tanılamak için HTML UI Yanıt Hızı aracını kullanın. Kullanım, diğer uygulama Uygulama Zaman Çizelgesi aracına benzer. Daha fazla bilgi için bkz. [HTML kullanıcı arabirimi yanıt hızı.](../profiling/html-ui-responsiveness.md)

![HTML Kullanıcı Arabirimi Yanıt Hızı profil oluşturma aracı](../profiling/media/diaghtmlresp.png "DiagHTMLResp")
::: moniker-end

::: moniker range="vs-2017"
## <a name="analyze-network-usage-uwp"></a>Ağ kullanımını analiz etme (UWP)

UWP uygulamaları içinde, API kullanılarak gerçekleştirilen ağ işlemlerini analiz `Windows.Web.Http` edersiniz. Bu araç, erişim ve kimlik doğrulama sorunları, yanlış önbellek kullanımı ve düşük görüntü ve indirme performansı gibi sorunları çözmenize yardımcı olabilir. Aracı kullanmak için, ağ **iletişim kutusu'Performans Profili Oluşturucu** ve ardından Başlat'ı **seçin.** Uygulamanıza, kullanan senaryoyu gidin ve ardından `Windows.Web.Http` Raporu oluşturmak için Koleksiyonu **durdur'a** seçin.

![Ağ Kullanımı profil oluşturma aracı](../profiling/media/prof-tour-network-usage.png "Ağ Kullanımını Tanılama")

Daha fazla ayrıntı görüntülemek için özet görünümünde bir işlem seçin.

![Ağ Kullanımı aracında ayrıntılı bilgiler](../profiling/media/prof-tour-network-usage-details.png "Ağ Kullanımı Ayrıntılarını Tanılama")

Daha fazla bilgi için [bkz. Ağ Kullanımı.](../profiling/network-usage.md)
::: moniker-end

## <a name="analyze-performance-legacy-tools"></a>Performansı analiz etme (eski araçlar)

::: moniker range="vs-2017"
Şu anda CPU Kullanımı veya Bellek Kullanımı araçlarında mevcut olan ölçüm araçları gibi özelliklere ihtiyacınız varsa ve masaüstü veya ASP.NET uygulamaları kullanıyorsanız profil oluşturmak için Performans Gezgini kullanabilirsiniz. (UWP uygulamaları için desteklenmiyor). Daha fazla bilgi için [bkz. Performans Gezgini.](../profiling/performance-explorer.md)
::: moniker-end

::: moniker range=">=vs-2019"
2019'Visual Studio'de, eski Performans Gezgini ve Performans Sihirbazı gibi ilgili profil oluşturma araçları Performans Profili Oluşturucu'ye katlandı. Bu araçları  >  Performans Profili Oluşturucu. Bu Performans Profili Oluşturucu, kullanılabilir tanılama araçları seçilen hedefe ve geçerli, açık başlangıç projesine bağlıdır. CPU Kullanımı aracı, daha önce Performans Sihirbazı'nda desteklenen örnekleme özelliğini sağlar. Ölçüm aracı, Performans Sihirbazı'nda yer alan ölçümli profil oluşturma özelliğini (kesin çağrı sayıları ve süreler için) sağlar. Ek bellek araçları da Performans Profili Oluşturucu.
::: moniker-end

![Performans Gezgini aracı](../profiling/media/prof-tour-performance-explorer.png "Performans Gezgini")

## <a name="which-tool-should-i-use"></a>Hangi aracı kullan gerekir?

Aşağıdaki tabloda, tekliflerde kullanabileceğiniz Visual Studio araçları ve bunları kullanabileceğiniz farklı proje türleri listele...

::: moniker range=">=vs-2019"
|Performans Aracı|Windows masaüstü|UWP|ASP.NET/ASP.NET Core|
|----------------------|---------------------|-------------|-------------|
|[PerfTips](../profiling/perftips.md)|evet|evet|evet|
|[CPU Kullanımı](../profiling/beginners-guide-to-performance-profiling.md)|evet|evet|evet|
|[Bellek Kullanımı](../profiling/memory-usage.md)|evet|evet|evet|
|[.NET Nesne Ayırma](../profiling/dotnet-alloc-tool.md)|evet (yalnızca.NET)|evet|evet|
|[GPU Kullanımı](./gpu-usage.md)|evet|evet|hayır|
|[Uygulama Zaman Çizelgesi](../profiling/application-timeline.md)|evet (XAML)|evet|hayır|
|[Olay görüntüleyicisi](../profiling/events-viewer.md)|evet|evet|evet|
|[.NET Async](../profiling/analyze-async.md)|evet (yalnızca.NET)|evet|evet|
|[.NET Sayaçları](../profiling/dotnet-counters-tool.md)|evet (yalnızca .NET Core)|hayır|evet (yalnızca ASP.NET Core)|
|[Veritabanı](../profiling/analyze-database.md)|evet (yalnızca .NET Core)|hayır|evet (yalnızca ASP.NET Core)|
|[Performans Gezgini](#analyze-performance-legacy-tools)|hayır|hayır|hayır|
|[IntelliTrace](../debugger/intellitrace.md)|Yalnızca Visual Studio Enterprise .NET|Yalnızca Visual Studio Enterprise .NET|Yalnızca Visual Studio Enterprise .NET|
::: moniker-end

::: moniker range="vs-2017"
|Performans Aracı|Windows masaüstü|UWP|ASP.NET/ASP.NET Core|
|----------------------|---------------------|-------------|-------------|
|[CPU Kullanımı](../profiling/beginners-guide-to-performance-profiling.md)|evet|evet|evet|
|[Bellek Kullanımı](../profiling/memory-usage.md)|evet|evet|evet|
|[GPU Kullanımı](./gpu-usage.md)|evet|evet|hayır|
|[Uygulama Zaman Çizelgesi](../profiling/application-timeline.md)|evet (XAML)|evet|hayır|
|[PerfTips](../profiling/perftips.md)|evet|evet XAML için, HTML için hayır|evet|
|[Performans Gezgini](../profiling/performance-explorer.md)|evet|hayır|evet|
|[IntelliTrace](../debugger/intellitrace.md)|Yalnızca Visual Studio Enterprise .NET|Yalnızca Visual Studio Enterprise .NET|Yalnızca Visual Studio Enterprise .NET|
|[Ağ Kullanımı](../profiling/network-usage.md)|hayır|evet|hayır|
|[HTML kullanıcı arabirimi yanıt hızı](../profiling/html-ui-responsiveness.md)|hayır|HTML için evet, XAML için hayır|hayır|
|[JavaScript Belleği](../profiling/javascript-memory.md)|hayır|HTML için evet, XAML için hayır|hayır|
::: moniker-end


## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio'da Hata Ayıklama](../debugger/debugger-feature-tour.md)