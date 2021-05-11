---
title: Kullanmaya başlayın araçlarıyla birlikte kullanma
description: Verilerde bulunan farklı tanılama araçlarına kısa bir Visual Studio.
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
ms.openlocfilehash: b5fb35c1cd30f872d2a58504f73596357cc60025
ms.sourcegitcommit: a0f5e7188838c5989c9cc78d99fb29bb2813501e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/11/2021
ms.locfileid: "109729331"
---
# <a name="first-look-at-profiling-tools"></a>Profil oluşturma araçlarına ilk bakış

Visual Studio, uygulama türünüze bağlı olarak farklı performans sorunlarını tanılamanıza yardımcı olacak çeşitli profil oluşturma araçları sağlar. Bu makalede, en yaygın profil oluşturma araçlarına hızlı bir bakış sağlaruz.

Farklı uygulama türleri için profil oluşturma aracı desteğini görmek için bkz. [Hangi aracı kullan uygulamam gerekir?](#which-tool-should-i-use)

## <a name="measure-performance-while-debugging"></a>Hata ayıklama sırasında performansı ölçme

Hata ayıklama oturumu sırasında erişebilirsiniz profil oluşturma araçları, Tanılama Araçları kullanılabilir. Siz Tanılama Araçları pencere otomatik olarak görüntülenir. Pencereyi açmak için Hata Ayıkla / Windows / Tanılama Araçları **Göster'e tıklayın** (veya **Ctrl** Alt  +    +  **F2 tuşlarına basın).** Pencere açıkken, veri toplamak istediğiniz araçları seçin.

![Tanılama Araçları penceresi](../profiling/media/prof-tour-diagnostic-tools.png "Tanılama Araçları")

Hata ayıklarken, CPU ve **bellek Tanılama Araçları** analiz etmek için Tanılama Araçları penceresini kullanabilir ve performansla ilgili bilgileri göstermek üzere olayları görüntüebilirsiniz.

![Tanılama Araçları Özet görünümü](../profiling/media/prof-tour-cpu-and-memory-graph.gif "Tanılama Araçları Özeti")

Uygulama **Tanılama Araçları** profili oluşturmanın yaygın bir yolu vardır, ancak Yayın derlemeleri için bunun yerine uygulamanın son inceleme analizini de yapabiliriz. Farklı yaklaşımlar hakkında daha fazla bilgi için [bkz. Hata ayıklayıcı](../profiling/running-profiling-tools-with-or-without-the-debugger.md)ile veya hata ayıklayıcı olmadan profil oluşturma araçlarını çalıştırma. Farklı uygulama türleri için profil oluşturma aracı desteğini görmek için bkz. [Hangi aracı kullan uygulamam gerekir?](#which-tool-should-i-use)

Tanılama Araçları penceresinde veya hata ayıklama oturumu sırasında kullanılabilen araçlar şunlardır:
- [CPU kullanımı](../profiling/beginners-guide-to-performance-profiling.md)
- [Bellek kullanımı](../profiling/memory-usage.md)
- [PerfTips](../profiling/perftips.md)

> [!NOTE]
> Windows 8 aracılarını hata ayıklayıcısıyla **(profil** oluşturma penceresiyle) çalıştırmak için Tanılama Araçları gerekir. Son güncelleştirme araçlarını Windows 7 [ve](#post_mortem) sonraki bir sürümüyle kullanabilirsiniz. 

## <a name="measure-performance-in-release-builds"></a><a name="post_mortem"></a> Yayın derlemeleri performansını ölçme

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

![Profil oluşturma turu PerfTips](../profiling/media/prof-tour-perf-tips.png "Profil Oluşturma Turu PerfTips")

Bir kod bloğunun yürütülmesi için ne kadar sürdüğünü veya tek bir işlevin tamamlaması için ne kadar sürdüğünü incelemek için PerfTips 'ı kullanabilirsiniz.

PerfTips, aynı olayları aynı zamanda olay **görünümünün** Olaylar görünümünde Tanılama Araçları. Olaylar **görünümünde,** hata ayıklama sırasında oluşan kesme noktası veya kod adımlama işlemi gibi farklı olayları görüntüebilirsiniz.

![Tanılama Araçları Olayları görünümü](../profiling/media/prof-tour-events.png "Tanılama Araçları Görüntüleme")

 > [!NOTE]
 > Bu sekmede Visual Studio Enterprise [IntelliTrace olaylarını da](../debugger/intellitrace.md) görebilirsiniz.

## <a name="analyze-cpu-usage"></a>CPU kullanımını analiz etme

CPU Kullanımı aracı, uygulama performansını analiz etmek için iyi bir yerdir. Bu, uygulamanın tüketen CPU kaynakları hakkında daha fazla bilgi sağlar. Hata ayıklayıcısı [ile tümleşik CPU Kullanımı aracını veya](../profiling/beginners-guide-to-performance-profiling.md) son işlem sonrası CPU Kullanımı aracını [kullanabilirsiniz.](../profiling/cpu-usage.md)

Hata ayıklayıcısıyla tümleşik CPU Kullanımı aracını kullanırken Tanılama Aracı penceresini açın (kapalı ise Hata Ayıkla **/ Windows / Göster'i Tanılama Araçları).** Hata ayıklama sırasında Özet görünümünü **açın ve** CPU Profilini **Kayded'i seçin.**

![Ağ içinde CPU kullanımını Tanılama Araçları](../profiling/media/prof-tour-enable-cpu-profiling.png "Tanılama Araçları CPU Kullanımını Etkinleştirme")

Aracı kullanmanın bir yolu, kodunda biri başlangıçta, biri işlevin sonunda veya analiz etmek istediğiniz kod bölgesinde olmak üzere iki kesme noktası ayarlamaktır. İkinci kesme noktası duraklatılırken profil oluşturma verilerini inceleme.

**CPU Kullanımı görünümü,** en uzun çalışana göre sıra edilen işlevlerin listesini ve en üstte en uzun çalışan işlevi gösterir. Bu, performans sorunlarının ortaya çıktı olduğu işlevlerde size yol gösterir.

![Tanılama Araçları CPU Kullanımı görünümü](../profiling/media/prof-tour-cpu-usage.png "Tanılama Araçları CPU Kullanımı")

İlgilenen bir işleve çift tıklayın; pencerenin ortasında seçili işlevi, sol tarafta çağıran işlevi ve sağ tarafta işlevleri çağıran daha ayrıntılı bir üç bölmeli "yer" görünümü görüntülenir. İşlev **Gövdesi bölümünde,** çağrı yapılan ve çağrılan işlevlerde harcanan süre hariç olmak üzere işlev gövdesinde harcanan toplam süre (ve sürenin yüzdesi) yer almaktadır. Bu veriler, işlevin kendisi performans sorunu olup olmadığını değerlendirmeye yardımcı olabilir.

![Tanılama Araçları çağıran "yer" görünümü](../profiling/media/prof-tour-cpu-usage-caller-callee.png "Tanılama Araçları Çağıran Görünümü")

## <a name="analyze-memory-usage"></a>Bellek kullanımını analiz etme

**Tanılama araçları** penceresi, **bellek kullanımı** aracını kullanarak uygulamanızdaki bellek kullanımını değerlendirmenize de olanak tanır. Örneğin, yığındaki nesnelerin sayısına ve boyutuna bakabilirsiniz. Performans Profiler 'daki [hata ayıklayıcı ile tümleşik bellek kullanımı aracını](../profiling/memory-usage.md) veya [mortem bellek kullanımı aracını](../profiling/memory-usage-without-debugging2.md) kullanabilirsiniz.

.NET geliştiricileri, [.NET nesne ayırma aracı](../profiling/dotnet-alloc-tool.md) ya da [bellek kullanımı](../profiling/memory-usage.md) aracı arasında seçim gösterebilir.

- **.NET nesne ayırma** Aracı, .net kodunuzda ayırma düzenlerini ve anormallikleri belirlemenize yardımcı olur ve çöp toplama ile ilgili yaygın sorunları belirlemenize yardımcı olur. Bu araç yalnızca bir post-mordıtem aracı olarak çalışır. Bu aracı, yerel veya uzak makinelerde çalıştırabilirsiniz.
- **Bellek kullanımı** Aracı, genellikle .NET uygulamalarında yaygın olmayan bellek sızıntılarını tanımlamaya yardımcı olur. Bellek denetlenirken hata ayıklayıcı özelliklerini kod üzerinden atlama gibi kullanmanız gerekiyorsa, [hata ayıklayıcı ile tümleşik bellek kullanım](../profiling/beginners-guide-to-performance-profiling.md) aracı önerilir.

Bellek **kullanımı** aracı ile bellek kullanımını çözümlemek için en az bir bellek anlık görüntüsü yapmanız gerekir. Genellikle belleği çözümlemenin en iyi yolu iki anlık görüntü alma yöntemidir; bir şüpheli bellek sorunundan önceki ilk sağ tarafta ve bir şüpheli bellek sorunu oluştuktan sonra ikinci anlık görüntü. Daha sonra, iki anlık görüntüye ilişkin bir farkı görüntüleyebilir ve tam olarak nelerin değiştiğini görebilirsiniz. Aşağıdaki çizimde, hata ayıklayıcı ile tümleşik aracı ile anlık görüntü alma gösterilmektedir.

![Tanılama Araçları anlık görüntü alın](../profiling/media/prof-tour-take-snapshots.gif "Tanılama Araçları Anlık Görüntü Alma")

Ok bağlantılarından birini seçtiğinizde, yığının fark görünümü verilir (kırmızı yukarı ok ![bellek kullanımı artışı](../profiling/media/prof-tour-mem-usage-up-arrow.png "Bellek Kullanımı Artışı") , artan nesne sayısını (solda) veya artan yığın boyutunu (sağ) gösterir). Doğru bağlantıya tıklarsanız, yığın boyutunu en çok arttığı nesnelere göre sıralanmış bir fark yığın görünümü alırsınız. Bu, bellek sorunlarını belirlemenize yardımcı olabilir. Örneğin, aşağıdaki çizimde, nesneler tarafından kullanılan baytlar `ClassHandlersStore` ikinci anlık görüntüde 3.492 bayt artar.

![Tanılama Araçları yığın fark görünümü](../profiling/media/prof-tour-mem-usage-diff-heap.png "Tanılama Araçları Yığın Fark görünümü")

Bellek Kullanımı görünümünde bunun yerine sol  tarafta yer alan bağlantıya tıklarsanız yığın görünümü nesne sayısına göre düzenlenmiştir; Sayı olarak en fazla artıran belirli bir türdeki nesneler en üstte gösterilir (Sayı Fark **sütununa göre sıralanmış).**

## <a name="analyze-resource-consumption-xaml"></a>Kaynak tüketimini analiz etme (XAML)

Windows masaüstü WPF uygulamaları ve UWP uygulamaları gibi XAML uygulamaları için kaynak tüketimini analiz etmek için Uygulama Zaman Çizelgesi kullanabilirsiniz. Örneğin, kullanıcı arabirimi çerçeveleri (düzen ve işleme), ağ ve disk isteklerine hizmet verme ve uygulama başlatma, sayfa yükleme ve Pencere yeniden boyutlandırma gibi senaryolarda, uygulamanın kullanıcı arabirimi çerçevelerini hazırlaması için harcadığı zamanı analiz edebilirsiniz. Aracı kullanmak için, araç **Uygulama Zaman Çizelgesi'Performans Profili Oluşturucu** başlat'ı **seçin.** Uygulamanıza, şüpheli bir kaynak tüketimi sorunuyla ilgili senaryoyu gidin ve ardından Raporu oluşturmak için **Koleksiyonu durdur'a** seçin.

Görsel aktarım hızı **grafı'nın düşük kare** hızı, uygulamanızı çalıştırarak gördüğünüz görsel sorunlara karşılık gelir. Benzer şekilde, kullanıcı arabirimi iş parçacığı **kullanım grafı içinde yüksek** sayılar kullanıcı arabirimi yanıt verme sorunlarına da karşılık geliyor olabilir. Raporda, şüpheli performans sorunu olan bir zaman dönemi seçin ve ardından Zaman Çizelgesi ayrıntıları görünümünde (alt bölme) ayrıntılı kullanıcı arabirimi iş parçacığı etkinliklerini inceleyebilirsiniz.

![Uygulama Zaman Çizelgesi profili oluşturma aracı](../profiling/media/prof-tour-application-timeline.gif "Profil Oluşturma Turu Uygulama Zaman Çizelgesi")

Zaman çizelgesi ayrıntıları görünümünde etkinlik türü (veya dahil olan kullanıcı arabirimi öğesi) gibi bilgileri etkinliğin süresiyle birlikte bulabilirsiniz. Örneğin çizimde Bir Kılavuz denetimi **için Düzen** olayı 57,53 ms alır.

Daha fazla bilgi için [bkz. Uygulama Zaman Çizelgesi.](../profiling/application-timeline.md)

::: moniker range=">=vs-2019"

## <a name="examine-application-events"></a>Uygulama olaylarını inceleme

Genel olaylar [görüntüleyicisi,](../profiling/events-viewer.md) uygulamanın nasıl performans sergilemektedir? daha iyi tanılamaya yardımcı olmak için modül yükü, iş parçacığı başlatma ve sistem yapılandırmaları gibi olayların bir listesi aracılığıyla uygulama etkinliğini görüntülemenize olanak Visual Studio sağlar. Bu araç, performans Profilcisi ' nde kullanılabilir. **Hata ayıklama**  >  **performansı profil oluşturucuyu** (veya **alt + f2**) seçerek performans profil oluşturucuyu açın.

Araç, her olayı bir liste görünümünde gösterir. Sütunlar, her olay hakkında olay adı, zaman damgası ve işlem KIMLIĞI gibi bilgiler sağlar.

![Olay Görüntüleyicisi Izleme](../profiling/media/eventviewertrace.png "Olay Görüntüleyicisi İzleme")

## <a name="analyze-asynchronous-code-net"></a>Zaman uyumsuz kodu çözümleme (.NET)

[.Net Async aracı](../profiling/analyze-async.md) , uygulamanızda zaman uyumsuz kodun performansını analiz etmenizi sağlar. Bu araç, performans Profilcisi ' nde kullanılabilir. **Hata ayıklama**  >  **performansı profil oluşturucuyu** (veya **alt + f2**) seçerek performans profil oluşturucuyu açın.

Araç, her zaman uyumsuz işlemi bir liste görünümünde gösterir. Zaman uyumsuz bir işlem için başlangıç saati, bitiş saati ve toplam süre gibi bilgileri görebilirsiniz.

![.NET Async aracı durdu](../profiling/media/async-tool-opened.png ".NET Async Aracı Durduruldu")

## <a name="analyze-database-performance-net-core"></a>Veritabanı performansını çözümleme (.NET Core)

ADO.NET veya Entity Framework Core kullanan .NET Core uygulamaları için [veritabanı aracı](../profiling/analyze-database.md) , Tanılama oturumu sırasında uygulamanızın yaptığı veritabanı sorgularını kaydetmenize izin verir. Daha sonra, uygulamanızın performansının iyileştirilen yerleri bulmak için tek sorgular hakkındaki bilgileri çözümleyebilirsiniz. Bu araç, performans Profilcisi ' nde kullanılabilir. **Hata ayıklama**  >  **performansı profil oluşturucuyu** (veya **alt + f2**) seçerek performans profil oluşturucuyu açın.

Araç, her sorguyu bir liste görünümünde gösterir. Sorgu başlangıç saati ve süresi gibi bilgileri görebilirsiniz.

![Ayırmasını](./media/db-gotosource.png "Ayırma")

## <a name="visualize-net-counters-net-core"></a>.NET sayaçlarını görselleştirme (.NET Core)

2019 Visual Studio 16.7 sürümünden başlayarak, performans sayaçlarını görselleştirmek için [.NET](../profiling/dotnet-counters-tool.md) Sayaçları Visual Studio aracını kullanabilirsiniz. dotnet sayaçları kullanılarak oluşturulan [sayaçları görselleştirin.](/dotnet/core/diagnostics/dotnet-counters) dotnet sayaçları CPU kullanımı ve atık toplayıcı yığın boyutu gibi birçok sayacı destekler.

Araç, bir liste görünümünde her sayacın canlı değerlerini gösterir.

:::image type="content" source="../profiling/media/dotnet-counters-tool-collecting.png" alt-text=".NET Sayaç aracı toplama.":::

::: moniker-end

## <a name="examine-ui-performance-and-accessibility-events-uwp"></a>UI performans ve erişilebilirlik olaylarını inceleme (UWP)

UWP uygulamalarınız için Kullanıcı Arabirimi **Analizi'Tanılama Araçları** **etkinleştirebilirsiniz.** Araç, yaygın performans veya erişilebilirlik sorunlarını arar ve hata **ayıklarken** bunları Olaylar görünümünde görüntüler. Olay açıklamaları sorunları çözmenize yardımcı olacak bilgiler sağlar.

![Tanılama araçlarında kullanıcı arabirimi analizi olaylarını görüntüleme](../profiling/media/prof-tour-ui-analysis.png "Tanılama Araçları Ui Çözümleme Olaylarını Görüntüleme")

## <a name="analyze-gpu-usage-direct3d"></a>GPU Kullanımını Analiz Etme (Direct3D)

Direct3D uygulamaları içinde (Direct3D bileşenleri C++ içinde olmalı), GPU'daki etkinliği inceler ve performans sorunlarını analiz edersiniz. Daha fazla bilgi için bkz. [GPU Kullanımı.](./gpu-usage.md) Aracı kullanmak için grafikte **GPU Kullanımı'nı** Performans Profili Oluşturucu başlat'ı **seçin.** Uygulamanıza profil oluşturmak istediğiniz senaryoyu takip edin ve ardından Koleksiyonu **durdur'a** seçerek bir rapor oluşturabilirsiniz.

Grafiklerde bir zaman dönemi ve görünüm ayrıntılarını seçtiğiniz **zaman** alt bölmede ayrıntılı bir görünüm görünür. Ayrıntılı görünümde, her CPU ve GPU üzerinde ne kadar etkinlik olduğunu incelersiniz. Zaman çizelgesinde açılan pencereleri almak için en düşük bölmede olayları seçin. Örneğin, Çağrı açılır **pencerelerini** sun'ı **görüntülemek için Olayı** sun'ı seçin. (Açık gri dikey VSync çizgileri, belirli bir **mevcut** çağrının vsync kaçırılmadığını anlamak için başvuru olarak kullanılabilir. Uygulamanın artmasıyla ile 60 FPS 'e kadar olması için her iki VNET arasında bir tane **mevcut** çağrı olması gerekir.)

![GPU kullanımı profil oluşturma aracı](../profiling/media/prof-tour-gpu-usage.png "GPU Kullanımını Tanılama")

Ayrıca, CPU ile bağlantılı veya GPU ile sınırlı performans sorunları olup olmadığını anlamak için grafikleri de kullanabilirsiniz.

::: moniker range="vs-2017"
## <a name="analyze-performance-javascript-uwp"></a>Performansı çözümleme (JavaScript UWP)

UWP uygulamaları için JavaScript bellek aracını ve HTML UI yanıt verme aracı 'nı kullanabilirsiniz.

JavaScript bellek aracı, diğer uygulama türleri için kullanılabilir bellek kullanımı aracına benzer. Bu aracı, bellek kullanımını anlamak ve uygulamanızdaki bellek sızıntılarını bulmak için kullanabilirsiniz. Araç hakkında daha fazla ayrıntı için bkz. [JavaScript hafıza](../profiling/javascript-memory.md).

![JavaScript bellek profili oluşturma aracı](../profiling/media/diagjsmemory.png "DiagJSMemory")

UWP uygulamalarında UI yanıtlama hızı, yavaş yükleme süresi ve yavaş görsel güncelleştirmeleri tanılamak için HTML UI yanıtlama hızı aracını kullanın. Kullanım, diğer uygulama türleri için Uygulama Zaman Çizelgesi araca benzer. Daha fazla bilgi için bkz. [HTML UI yanıt hızı](../profiling/html-ui-responsiveness.md).

![HTML UI yanıtlama hızı profil oluşturma aracı](../profiling/media/diaghtmlresp.png "DiagHTMLResp")
::: moniker-end

::: moniker range="vs-2017"
## <a name="analyze-network-usage-uwp"></a>Ağ kullanımını analiz etme (UWP)

UWP uygulamalarında, API kullanarak gerçekleştirilen ağ işlemlerini çözümleyebilirsiniz `Windows.Web.Http` . Bu araç, erişim ve kimlik doğrulama sorunları, hatalı önbellek kullanımı ve kötü ekran ve indirme performansı gibi sorunları çözmenize yardımcı olabilir. Aracı kullanmak için, performans Profilcisi ' nde **ağ** ' ı seçin ve ardından **Başlat**' ı seçin. Uygulamanızda, tarafından kullanılan senaryoya gidin `Windows.Web.Http` ve sonra raporu oluşturmak için **koleksiyonu durdur** ' u seçin.

![Ağ kullanımı profil oluşturma aracı](../profiling/media/prof-tour-network-usage.png "Ağ Kullanımını Tanılama")

Daha fazla ayrıntı görüntülemek için Özet görünümünde bir işlem seçin.

![Ağ Kullanımı aracında ayrıntılı bilgiler](../profiling/media/prof-tour-network-usage-details.png "Ağ Kullanımı Ayrıntılarını Tanılama")

Daha fazla bilgi için [bkz. Ağ Kullanımı.](../profiling/network-usage.md)
::: moniker-end

## <a name="analyze-performance-legacy-tools"></a>Performansı analiz etme (eski araçlar)

::: moniker range="vs-2017"
Şu anda CPU Kullanımı veya Bellek Kullanımı araçlarında mevcut olan ve masaüstü veya ASP.NET uygulamaları kullanıyorsanız profil oluşturmak için Performans Gezgini kullanabilirsiniz. (UWP uygulamaları için desteklenmiyor). Daha fazla bilgi için [bkz. Performans Gezgini.](../profiling/performance-explorer.md)
::: moniker-end

::: moniker range=">=vs-2019"
Visual Studio 2019'da, eski Performans Gezgini ve Performans Sihirbazı gibi ilgili profil oluşturma araçları Performans Profili Oluşturucu'ye katlandı. Bu araçta hata ayıklamayı kullanarak   >  **Performans Profili Oluşturucu.** Bu Performans Profili Oluşturucu, kullanılabilir tanılama araçları seçilen hedefe ve geçerli, açık başlangıç projesine bağlıdır. CPU Kullanımı aracı, daha önce Performans Sihirbazı'nda desteklenen örnekleme özelliğini sağlar. Ölçüm aracı, Performans Sihirbazı'nda yer alan ölçümli profil oluşturma özelliğini (kesin çağrı sayıları ve süreler için) sağlar. Ek bellek araçları da Performans Profili Oluşturucu.
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
|[.NET Nesne Ayırma](../profiling/dotnet-alloc-tool.md)|evet (yalnızca .NET)|evet|evet|
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
|[JavaScript Belleği](../profiling/javascript-memory.md)|hayır|HTML için evet, XAML için hayır|hayır|
::: moniker-end


## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio'da Hata Ayıklama](../debugger/debugger-feature-tour.md)