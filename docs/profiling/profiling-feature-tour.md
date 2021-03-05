---
title: Profil oluşturma araçlarıyla çalışmaya başlama
description: Visual Studio 'da bulunan farklı tanılama araçlarına göz atın.
ms.custom: ''
ms.date: 02/18/2021
ms.topic: overview
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
ms.workload:
- multiple
ms.openlocfilehash: 855a04fae1d5b406019e758c6d6f931d6657bb4e
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102145384"
---
# <a name="first-look-at-profiling-tools"></a>Profil oluşturma araçlarına ilk bakış

Visual Studio, uygulama türüne bağlı olarak farklı türlerde performans sorunlarını tanılamanıza yardımcı olacak çeşitli profil araçları sağlar. Bu makalede, en yaygın profil oluşturma araçlarına hızlı bir bakış sunuyoruz.

Farklı uygulama türleri için profil oluşturma araç desteğini görmek için bkz. [hangi aracı kullanmalıyım?](#which-tool-should-i-use)

## <a name="measure-performance-while-debugging"></a>Hata ayıklarken performansı ölçme

Hata ayıklama oturumu sırasında erişebileceğiniz profil oluşturma araçları Tanılama Araçları penceresinde kullanılabilir. Tanılama Araçları penceresi devre dışı bırakılmadığı takdirde otomatik olarak görünür. Pencereyi getirmek için **Hata Ayıkla/Windows/tanılama araçları göster**' e tıklayın. Pencereyi açık olarak kullanarak veri toplamak istediğiniz araçları seçebilirsiniz.

![Tanılama Araçları penceresi](../profiling/media/prof-tour-diagnostic-tools.png "Tanılama Araçları")

Hata ayıklarken, CPU ve bellek kullanımını çözümlemek için **Tanılama araçları** penceresini kullanabilir ve performansla ilgili bilgileri gösteren olayları görüntüleyebilirsiniz.

![Tanılama Araçları Özet görünümü](../profiling/media/prof-tour-cpu-and-memory-graph.gif "Tanılama Araçları Özeti")

**Tanılama araçları** pencere, uygulamaları profil oluşturmanın yaygın bir yoludur, ancak yayın yapıları için bunun yerine uygulamanızın mordıtem analizini de yapabilirsiniz. Farklı yaklaşımlar hakkında daha fazla bilgi için bkz. [hata ayıklayıcı ile veya olmadan profil oluşturma araçlarını çalıştırma](../profiling/running-profiling-tools-with-or-without-the-debugger.md). Farklı uygulama türleri için profil oluşturma araç desteğini görmek için bkz. [hangi aracı kullanmalıyım?](#which-tool-should-i-use)

Tanılama Araçları penceresinde veya hata ayıklama oturumu sırasında bulunan araçlar şunları içerir:
- [CPU kullanımı](../profiling/beginners-guide-to-performance-profiling.md)
- [Bellek kullanımı](../profiling/memory-usage.md)
- [PerfTips](../profiling/perftips.md)

> [!NOTE]
> Hata ayıklayıcı (**Tanılama araçları** penceresi) ile profil oluşturma araçlarını çalıştırmak için Windows 8 ve üzeri gereklidir. Windows 7 ve sonraki sürümleri ile [mortem](#post_mortem) araçları 'nı kullanabilirsiniz. 

## <a name="measure-performance-in-release-builds"></a><a name="post_mortem"></a> Yayın yapılarında performansı ölçme

Performans Profiler 'daki Araçlar **yayın** derlemeleri için analiz sağlamak üzere tasarlanmıştır. Performans Profiler 'da, uygulama çalışırken tanılama bilgilerini toplayabilir ve ardından uygulama durdurulduktan sonra toplanan bilgileri inceleyebilirsiniz (bir post-mordıtem Analizi).

**Hata ayıklama**  >  **performansı profil oluşturucuyu** (veya **alt + f2**) seçerek performans profil oluşturucuyu açın.

![Performans Profili Oluşturucu](../profiling/media/prof-tour-performance-profiler.png "Performans Profili Oluşturucu")

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

![Profil oluşturma turu PerfTips](../profiling/media/prof-tour-perf-tips.png "Profil oluşturma turu PerfTips")

Bir kod bloğunun yürütülmesi için ne kadar sürdüğünü veya tek bir işlevin tamamlaması için ne kadar sürdüğünü incelemek için PerfTips 'ı kullanabilirsiniz.

PerfTips, Tanılama Araçları **Olaylar** görünümünde de görüntülenen olayları gösterir. **Olaylar** görünümünde, hata ayıklama sırasında oluşan farklı olayları (kesme noktası veya kod atlama işlemi gibi) görüntüleyebilirsiniz.

![Tanılama Araçları Olaylar görünümü](../profiling/media/prof-tour-events.png "Tanılama Araçları görüntüleme olayları")

 > [!NOTE]
 > Visual Studio Enterprise sahipseniz, bu sekmede [IntelliTrace olaylarını](../debugger/intellitrace.md) da görebilirsiniz.

## <a name="analyze-cpu-usage"></a>CPU kullanımını analiz etme

CPU kullanımı aracı, uygulamanızın performansını çözümlemeye başlamak için iyi bir yerdir. Uygulamanızın kullandığı CPU kaynakları hakkında daha fazla bilgi sağlayacaktır. [Hata ayıklayıcı ile TÜMLEŞIK CPU kullanımı aracını](../profiling/beginners-guide-to-performance-profiling.md) veya [mortem CPU kullanımı aracını](../profiling/cpu-usage.md)kullanabilirsiniz.

Hata ayıklayıcı ile tümleşik CPU kullanımı aracını kullanırken, tanılama araç penceresini açın (kapalıysa, **Hata Ayıkla/Windows/tanılama araçları göster**' i seçin). Hata ayıklama sırasında  **Özet** görünümünü açın ve **CPU profilini kaydet**' i seçin.

![Tanılama Araçları CPU kullanımını etkinleştir](../profiling/media/prof-tour-enable-cpu-profiling.png "CPU kullanımını etkinleştirmek Tanılama Araçları")

Araç kullanmanın bir yolu kodunuzda iki kesme noktası, bir diğeri de işlevin sonunda veya bir ya da analiz etmek istediğiniz kod bölgesi ayarlamak kullanmaktır. İkinci kesme noktasında durakladığınızda profil oluşturma verilerini inceleyin.

**CPU kullanımı** görünümü, en uzun çalışan bir işlevle en üstte bulunan işlevlerin bir listesini gösterir. Bu, performans sorunlarının gerçekleştiği işlevlerde size rehberlik etmenize yardımcı olabilir.

![Tanılama Araçları CPU kullanımı görünümü](../profiling/media/prof-tour-cpu-usage.png "Tanılama Araçları CPU kullanımı")

İlgilendiğiniz bir işleve çift tıklayın ve seçilen işlevle pencerenin ortasında, sol taraftaki çağırma işlevine ve sağ tarafta işlev olarak adlandırılan daha ayrıntılı üç bölmeli "kelebek" görünümü görürsünüz. **Işlev gövdesi** bölümü, işlev gövdesinde harcanan ve çağrılan işlevlerde harcanan süre hariç toplam süreyi (ve zaman yüzdesini) gösterir. Bu veriler, işlevin kendisinin performans sorunu olup olmadığını değerlendirmenize yardımcı olabilir.

![Tanılama Araçları arayan "kelebek" görünümü](../profiling/media/prof-tour-cpu-usage-caller-callee.png "Tanılama Araçları arayan görünümü")

## <a name="analyze-memory-usage"></a>Bellek kullanımını analiz etme

**Tanılama araçları** penceresi, **bellek kullanımı** aracını kullanarak uygulamanızdaki bellek kullanımını değerlendirmenize de olanak tanır. Örneğin, yığındaki nesnelerin sayısına ve boyutuna bakabilirsiniz. Performans Profiler 'daki [hata ayıklayıcı ile tümleşik bellek kullanımı aracını](../profiling/memory-usage.md) veya [mortem bellek kullanımı aracını](../profiling/memory-usage-without-debugging2.md) kullanabilirsiniz.

.NET geliştiricileri, [.NET nesne ayırma aracı](../profiling/dotnet-alloc-tool.md) ya da [bellek kullanımı](../profiling/memory-usage.md) aracı arasında seçim gösterebilir.

- **.NET nesne ayırma** Aracı, .net kodunuzda ayırma düzenlerini ve anormallikleri belirlemenize yardımcı olur ve çöp toplama ile ilgili yaygın sorunları belirlemenize yardımcı olur. Bu araç yalnızca bir post-mordıtem aracı olarak çalışır. Bu aracı, yerel veya uzak makinelerde çalıştırabilirsiniz.
- **Bellek kullanımı** Aracı, genellikle .NET uygulamalarında yaygın olmayan bellek sızıntılarını tanımlamaya yardımcı olur. Bellek denetlenirken hata ayıklayıcı özelliklerini kod üzerinden atlama gibi kullanmanız gerekiyorsa, [hata ayıklayıcı ile tümleşik bellek kullanım](../profiling/beginners-guide-to-performance-profiling.md) aracı önerilir.

Bellek **kullanımı** aracı ile bellek kullanımını çözümlemek için en az bir bellek anlık görüntüsü yapmanız gerekir. Genellikle belleği çözümlemenin en iyi yolu iki anlık görüntü alma yöntemidir; bir şüpheli bellek sorunundan önceki ilk sağ tarafta ve bir şüpheli bellek sorunu oluştuktan sonra ikinci anlık görüntü. Daha sonra, iki anlık görüntüye ilişkin bir farkı görüntüleyebilir ve tam olarak nelerin değiştiğini görebilirsiniz. Aşağıdaki çizimde, hata ayıklayıcı ile tümleşik aracı ile anlık görüntü alma gösterilmektedir.

![Tanılama Araçları anlık görüntü alın](../profiling/media/prof-tour-take-snapshots.gif "Tanılama Araçları anlık görüntü al")

Ok bağlantılarından birini seçtiğinizde, yığının fark görünümü verilir (kırmızı yukarı ok ![bellek kullanımı artışı](../profiling/media/prof-tour-mem-usage-up-arrow.png "Bellek kullanımı artışı") , artan nesne sayısını (solda) veya artan yığın boyutunu (sağ) gösterir). Doğru bağlantıya tıklarsanız, yığın boyutunu en çok arttığı nesnelere göre sıralanmış bir fark yığın görünümü alırsınız. Bu, bellek sorunlarını belirlemenize yardımcı olabilir. Örneğin, aşağıdaki çizimde, nesneler tarafından kullanılan baytlar `ClassHandlersStore` ikinci anlık görüntüde 3.492 bayt artar.

![Tanılama Araçları yığın farkı görünümü](../profiling/media/prof-tour-mem-usage-diff-heap.png "Tanılama Araçları yığın farkı görünümü")

**Bellek kullanımı** görünümünde, sol taraftaki bağlantıya tıklarsanız, yığın görünümü nesne sayısına göre düzenlenir; belirli bir türün en fazla sayıyı arttığı nesneler en üstte gösterilir ( **Count diff** sütununa göre sıralanır).

## <a name="analyze-resource-consumption-xaml"></a>Kaynak tüketimini analiz etme (XAML)

Windows Masaüstü WPF uygulamaları ve UWP uygulamaları gibi XAML uygulamalarında, Uygulama Zaman Çizelgesi aracını kullanarak kaynak tüketimini çözümleyebilirsiniz. Örneğin, uygulamanızın kullanıcı arabirimi çerçevelerini (düzen ve işleme) hazırlama, ağ ve disk isteklerine hizmet verme ve uygulama başlatma, sayfa yükleme ve pencere yeniden boyutlandırma gibi senaryolarda harcanan süreyi çözümleyebilirsiniz. Aracı kullanmak için, performans profil oluşturucusu 'nda **uygulama zaman çizelgesi** ' yi seçin ve ardından **Başlat**' ı seçin. Uygulamanızda, şüpheli kaynak tüketimi sorunu olan senaryoya gidin ve raporu oluşturmak için **koleksiyonu durdur** ' u seçin.

**Görsel işleme** grafiğindeki düşük framerates, uygulamanızı çalıştırırken gördüğünüz görsel sorunlara karşılık gelebilir. Benzer şekilde, **UI iş parçacığı kullanım** grafiğinde yüksek SAYıLAR da UI yanıtlama hızı sorunlarına karşılık gelebilir. Raporda, şüpheli performans sorunuyla bir zaman aralığı seçebilir ve ardından zaman çizelgesi ayrıntıları görünümündeki (alt bölme) ayrıntılı UI iş parçacığı etkinliklerini inceleyebilirsiniz.

![Uygulama Zaman Çizelgesi profil oluşturma aracı](../profiling/media/prof-tour-application-timeline.gif "Profil oluşturma turu Uygulama Zaman Çizelgesi")

Zaman çizelgesi ayrıntıları görünümünde etkinlik (veya dahil edilen kullanıcı arabirimi öğesi) gibi bilgileri etkinliğin süresiyle birlikte bulabilirsiniz. Örneğin, çizimde kılavuz denetimine yönelik bir **Düzen** olayı 57,53 MS alır.

Daha fazla bilgi için bkz. [uygulama zaman çizelgesi](../profiling/application-timeline.md).

::: moniker range=">=vs-2019"

## <a name="examine-application-events"></a>Uygulama olaylarını İnceleme

Genel [Olaylar Görüntüleyicisi](../profiling/events-viewer.md) , uygulamanızın Visual Studio Profiler içinde nasıl performans gösterdiğini daha iyi tanılamanıza yardımcı olması için modül yüklemesi, iş parçacığı başlatma ve sistem yapılandırması gibi olayların bir listesi aracılığıyla uygulamanızın etkinliğini görüntülemenize olanak sağlar. Bu araç, performans Profilcisi ' nde kullanılabilir. **Hata ayıklama**  >  **performansı profil oluşturucuyu** (veya **alt + f2**) seçerek performans profil oluşturucuyu açın.

Araç, her olayı bir liste görünümünde gösterir. Sütunlar, her olay hakkında olay adı, zaman damgası ve işlem KIMLIĞI gibi bilgiler sağlar.

![Olay Görüntüleyicisi Izleme](../profiling/media/eventviewertrace.png "Olay Görüntüleyicisi Izleme")

## <a name="analyze-asynchronous-code-net"></a>Zaman uyumsuz kodu çözümleme (.NET)

[.Net Async aracı](../profiling/analyze-async.md) , uygulamanızda zaman uyumsuz kodun performansını analiz etmenizi sağlar. Bu araç, performans Profilcisi ' nde kullanılabilir. **Hata ayıklama**  >  **performansı profil oluşturucuyu** (veya **alt + f2**) seçerek performans profil oluşturucuyu açın.

Araç, her zaman uyumsuz işlemi bir liste görünümünde gösterir. Zaman uyumsuz bir işlem için başlangıç saati, bitiş saati ve toplam süre gibi bilgileri görebilirsiniz.

![.NET Async aracı durdu](../profiling/media/async-tool-opened.png ".NET Async aracı durdu")

## <a name="analyze-database-performance-net-core"></a>Veritabanı performansını çözümleme (.NET Core)

ADO.NET veya Entity Framework Core kullanan .NET Core uygulamaları için [veritabanı aracı](../profiling/analyze-database.md) , Tanılama oturumu sırasında uygulamanızın yaptığı veritabanı sorgularını kaydetmenize izin verir. Daha sonra, uygulamanızın performansının iyileştirilen yerleri bulmak için tek sorgular hakkındaki bilgileri çözümleyebilirsiniz. Bu araç, performans Profilcisi ' nde kullanılabilir. **Hata ayıklama**  >  **performansı profil oluşturucuyu** (veya **alt + f2**) seçerek performans profil oluşturucuyu açın.

Araç, her sorguyu bir liste görünümünde gösterir. Sorgu başlangıç saati ve süresi gibi bilgileri görebilirsiniz.

![Ayırma](./media/db-gotosource.png "Ayırma")

## <a name="visualize-net-counters-net-core"></a>.NET sayaçlarını görselleştirme (.NET Core)

Visual Studio 2019 sürüm 16,7 ' den başlayarak, performans sayaçlarını görselleştirmek için Visual Studio 'daki [.net sayaçları aracını](../profiling/dotnet-counters-tool.md) kullanabilirsiniz. [DotNet sayaçları](/dotnet/core/diagnostics/dotnet-counters)kullanılarak oluşturulan sayaçları görselleştirebilirsiniz. DotNet sayaçları, CPU kullanımı ve çöp toplayıcı yığın boyutu gibi birçok sayacı destekler.

Araç, bir liste görünümündeki her sayaç için canlı değerleri gösterir.

:::image type="content" source="../profiling/media/dotnet-counters-tool-collecting.png" alt-text=".NET sayaç aracı toplanıyor.":::

::: moniker-end

## <a name="examine-ui-performance-and-accessibility-events-uwp"></a>UI performans ve erişilebilirlik olaylarını İnceleme (UWP)

UWP uygulamalarınızda **Tanılama araçları** penceresinde **UI analizini** etkinleştirebilirsiniz. Araç yaygın performans ve erişilebilirlik sorunlarını arar ve hata ayıklarken bunları **Olaylar** görünümünde görüntüler. Olay açıklamaları, sorunları çözmenize yardımcı olabilecek bilgiler sağlar.

![Tanılama araçları 'nda UI Analizi olaylarını görüntüleme](../profiling/media/prof-tour-ui-analysis.png "Tanılama Araçları Kullanıcı arabirimi analiz olaylarını görüntüleme")

## <a name="analyze-gpu-usage-direct3d"></a>GPU kullanımını analiz etme (Direct3D)

Direct3D uygulamalarında (Direct3D bileşenleri C++ ' da olmalıdır) GPU 'daki etkinliği inceleyebilir ve performans sorunlarını çözümleyebilirsiniz. Daha fazla bilgi için bkz. [GPU kullanımı](./gpu-usage.md). Aracı kullanmak için performans Profilcisi ' nde **GPU kullanımı** ' nı seçin ve ardından **Başlat**' ı seçin. Uygulamanızda, profil oluşturma konusunda ilgilendiğiniz senaryoya gidin ve ardından bir rapor oluşturmak için **toplamayı durdur** ' u seçin.

Grafiklerde bir zaman aralığı seçip **Ayrıntıları görüntüle**' yi seçtiğinizde, alt bölmede ayrıntılı bir görünüm görüntülenir. Ayrıntılı görünümde, her CPU ve GPU üzerinde ne kadar etkinlik olduğunu inceleyebilirsiniz. Zaman çizelgesinde açılan pencereleri almak için en düşük bölmedeki olayları seçin. Örneğin, **var** olan çağrı açılan pencere görüntülenecek **olan olayı seçin** . (Açık gri dikey VSync çizgileri, belirli bir **mevcut** çağrının vsync kaçırılmadığını anlamak için başvuru olarak kullanılabilir. Uygulamanın artmasıyla ile 60 FPS 'e kadar olması için her iki VNET arasında bir tane **mevcut** çağrı olması gerekir.)

![GPU kullanımı profil oluşturma aracı](../profiling/media/prof-tour-gpu-usage.png "Diag GPU kullanımı")

Ayrıca, CPU ile bağlantılı veya GPU ile sınırlı performans sorunları olup olmadığını anlamak için grafikleri de kullanabilirsiniz.

::: moniker range="vs-2017"
## <a name="analyze-performance-javascript-uwp"></a>Performansı çözümleme (JavaScript UWP)

UWP uygulamaları için JavaScript bellek aracını ve HTML UI yanıt verme aracı 'nı kullanabilirsiniz.

JavaScript bellek aracı, diğer uygulama türleri için kullanılabilir bellek kullanımı aracına benzer. Bu aracı, bellek kullanımını anlamak ve uygulamanızdaki bellek sızıntılarını bulmak için kullanabilirsiniz. Araç hakkında daha fazla ayrıntı için bkz. [JavaScript hafıza](../profiling/javascript-memory.md).

![JavaScript bellek profili oluşturma aracı](../profiling/media/diagjsmemory.png "DiagJSMemory")

UWP uygulamalarında UI yanıtlama hızı, yavaş yükleme süresi ve yavaş görsel güncelleştirmeleri tanılamak için HTML UI yanıtlama hızı aracını kullanın. Kullanım, diğer uygulama türleri için Uygulama Zaman Çizelgesi araca benzer. Daha fazla bilgi için bkz. [HTML UI yanıt hızı](../profiling/html-ui-responsiveness.md).

![HTML UI yanıtlama hızı profil oluşturma aracı](../profiling/media/diaghtmlresp.png "Diabir Mlyanıt")
::: moniker-end

::: moniker range="vs-2017"
## <a name="analyze-network-usage-uwp"></a>Ağ kullanımını analiz etme (UWP)

UWP uygulamalarında, API kullanarak gerçekleştirilen ağ işlemlerini çözümleyebilirsiniz `Windows.Web.Http` . Bu araç, erişim ve kimlik doğrulama sorunları, hatalı önbellek kullanımı ve kötü ekran ve indirme performansı gibi sorunları çözmenize yardımcı olabilir. Aracı kullanmak için, performans Profilcisi ' nde **ağ** ' ı seçin ve ardından **Başlat**' ı seçin. Uygulamanızda, tarafından kullanılan senaryoya gidin `Windows.Web.Http` ve sonra raporu oluşturmak için **koleksiyonu durdur** ' u seçin.

![Ağ kullanımı profil oluşturma aracı](../profiling/media/prof-tour-network-usage.png "Diag ağı kullanımı")

Daha fazla ayrıntı görüntülemek için Özet görünümünde bir işlem seçin.

![Ağ kullanımı aracında ayrıntılı bilgiler](../profiling/media/prof-tour-network-usage-details.png "Diag ağı kullanım ayrıntıları")

Daha fazla bilgi için bkz. [ağ kullanımı](../profiling/network-usage.md).
::: moniker-end

## <a name="analyze-performance-legacy-tools"></a>Performansı çözümleme (eski araçlar)

::: moniker range="vs-2017"
Şu anda CPU kullanımı veya bellek kullanımı araçlarında bulunmayan izleme gibi özelliklere ihtiyacınız varsa ve Masaüstü veya ASP.NET uygulamaları çalıştırıyorsanız, profil oluşturma için Performans Gezgini kullanabilirsiniz. (UWP uygulamalarında desteklenmez). Daha fazla bilgi için bkz. [Performans Gezgini](../profiling/performance-explorer.md).
::: moniker-end

::: moniker range=">=vs-2019"
Visual Studio 2019 ' de, performans Sihirbazı gibi eski performans Gezgini ve ilgili profil oluşturma araçları, **hata ayıklama**  >  **performansı profil oluşturucu** kullanarak açabileceğiniz performans profil oluşturucuya katlanmıştı. Performans Profiler 'da, kullanılabilir tanılama araçları, seçilen hedefe ve geçerli, açık başlangıç projesine bağlıdır. CPU kullanımı aracı, daha önce performans sihirbazında desteklenen örnekleme özelliğini sağlar. Izleme Aracı, performans sihirbazındaki belgelenmiş profil oluşturma özelliği (kesin çağrı sayısı ve süreler için) sağlar. Ayrıca, performans Profiler 'da ek bellek araçları da görünür.
::: moniker-end

![Performans Gezgini aracı](../profiling/media/prof-tour-performance-explorer.png "Performans Gezgini")

## <a name="which-tool-should-i-use"></a>Hangi aracı kullanmalıyım?

Aşağıda, Visual Studio tekliflerinin farklı araçları ve bunları kullanabileceğiniz farklı proje türlerini listeleyen bir tablo verilmiştir:

::: moniker range=">=vs-2019"
|Performans aracı|Windows masaüstü|UWP|ASP.NET/ASP.NET Core|
|----------------------|---------------------|-------------|-------------|
|[PerfTips](../profiling/perftips.md)|evet|evet|evet|
|[CPU kullanımı](../profiling/beginners-guide-to-performance-profiling.md)|evet|evet|evet|
|[Bellek kullanımı](../profiling/memory-usage.md)|evet|evet|evet|
|[.NET nesne ayırma](../profiling/dotnet-alloc-tool.md)|Evet (yalnızca .NET)|evet|evet|
|[GPU Kullanımı](./gpu-usage.md)|evet|evet|hayır|
|[Uygulama Zaman Çizelgesi](../profiling/application-timeline.md)|Evet (XAML)|evet|hayır|
|[Olay Görüntüleyicisi](../profiling/events-viewer.md)|evet|evet|evet|
|[.NET Async](../profiling/analyze-async.md)|Evet (yalnızca .NET)|evet|evet|
|[.NET Sayaçları](../profiling/dotnet-counters-tool.md)|Evet (yalnızca .NET Core)|hayır|Evet (yalnızca ASP.NET Core)|
|[Veritabanı](../profiling/analyze-database.md)|Evet (yalnızca .NET Core)|hayır|Evet (yalnızca ASP.NET Core)|
|[Performans Gezgini](#analyze-performance-legacy-tools)|hayır|hayır|hayır|
|[IntelliTrace](../debugger/intellitrace.md)|Yalnızca Visual Studio Enterprise .NET|Yalnızca Visual Studio Enterprise .NET|Yalnızca Visual Studio Enterprise .NET|
::: moniker-end

::: moniker range="vs-2017"
|Performans aracı|Windows masaüstü|UWP|ASP.NET/ASP.NET Core|
|----------------------|---------------------|-------------|-------------|
|[CPU kullanımı](../profiling/beginners-guide-to-performance-profiling.md)|evet|evet|evet|
|[Bellek kullanımı](../profiling/memory-usage.md)|evet|evet|evet|
|[GPU Kullanımı](./gpu-usage.md)|evet|evet|hayır|
|[Uygulama Zaman Çizelgesi](../profiling/application-timeline.md)|Evet (XAML)|evet|hayır|
|[PerfTips](../profiling/perftips.md)|evet|XAML için Evet, HTML için Hayır|evet|
|[Performans Gezgini](../profiling/performance-explorer.md)|evet|hayır|evet|
|[IntelliTrace](../debugger/intellitrace.md)|Yalnızca Visual Studio Enterprise .NET|Yalnızca Visual Studio Enterprise .NET|Yalnızca Visual Studio Enterprise .NET|
|[Ağ Kullanımı](../profiling/network-usage.md)|hayır|evet|hayır|
|[HTML kullanıcı arabirimi yanıt hızı](../profiling/html-ui-responsiveness.md)|hayır|HTML için Evet, XAML için Hayır|hayır|
|[JavaScript Belleği](../profiling/javascript-memory.md)|hayır|HTML için Evet, XAML için Hayır|hayır|
::: moniker-end


## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio'da Hata Ayıklama](../debugger/debugger-feature-tour.md)