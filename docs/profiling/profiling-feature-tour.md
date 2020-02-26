---
title: Profil oluşturma araçlarıyla performansı ölçme
description: Visual Studio 'da bulunan farklı tanılama araçlarına göz atın.
ms.custom: mvc
ms.date: 05/18/2018
ms.topic: quickstart
helpviewer_keywords:
- diagnostic tools
ms.assetid: d2ee0301-ea78-43d8-851a-71b7b2043d73
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8e4868899af67ebeb25ae508cbe7e5b0c83137bf
ms.sourcegitcommit: 2ae2436dc3484b9dfa10e0483afba1e5a02a52eb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/25/2020
ms.locfileid: "77578086"
---
# <a name="quickstart-first-look-at-profiling-tools"></a>Hızlı başlangıç: profil oluşturma araçlarına Ilk bakış

Visual Studio, uygulama türüne bağlı olarak farklı türlerde performans sorunlarını tanılamanıza yardımcı olacak çeşitli profil araçları sağlar.

Hata ayıklama oturumu sırasında erişebileceğiniz profil oluşturma araçları Tanılama Araçları penceresinde kullanılabilir. Tanılama Araçları penceresi devre dışı bırakılmadığı takdirde otomatik olarak görünür. Pencereyi getirmek için **Hata Ayıkla/Windows/tanılama araçları göster**' e tıklayın. Pencereyi açık olarak kullanarak veri toplamak istediğiniz araçları seçebilirsiniz.

![Tanılama Araçları penceresi](../profiling/media/prof-tour-diagnostic-tools.png "Tanılama Araçları")

Hata ayıklarken, CPU ve bellek kullanımını çözümlemek için **Tanılama araçları** penceresini kullanabilir ve performansla ilgili bilgileri gösteren olayları görüntüleyebilirsiniz.

![Tanılama Araçları Özet görünümü](../profiling/media/prof-tour-cpu-and-memory-graph.gif "Tanılama Araçları Özeti")

**Tanılama araçları** pencere, genellikle uygulamaları profil oluşturmanın tercih edilen yoludur, ancak yayın yapıları için bunun yerine uygulamanızın bir sonrası analizini de yapabilirsiniz. Farklı yaklaşımlar hakkında daha fazla bilgi istiyorsanız bkz. [hata ayıklayıcı ile veya olmayan profil oluşturma araçlarını çalıştırma](../profiling/running-profiling-tools-with-or-without-the-debugger.md). Farklı uygulama türleri için profil oluşturma araç desteğini görmek için bkz. [hangi aracı kullanmalıyım?](#which-tool-should-i-use).

> [!NOTE]
> Windows 7 ve sonraki sürümleri ile mortem araçları 'nı kullanabilirsiniz. Hata ayıklayıcı (**Tanılama araçları** penceresi) ile profil oluşturma araçlarını çalıştırmak için Windows 8 ve üzeri gereklidir.

## <a name="analyze-cpu-usage"></a>CPU Kullanımını Analiz Etme

CPU kullanımı aracı, uygulamanızın performansını çözümlemeye başlamak için iyi bir yerdir. Uygulamanızın kullandığı CPU kaynakları hakkında daha fazla bilgi sağlayacaktır. CPU kullanımı aracı hakkında daha ayrıntılı bir anlatım için bkz. [CPU kullanımını çözümleyerek uygulama performansını ölçme](../profiling/beginners-guide-to-performance-profiling.md).

Tanılama Araçları **Özet** görünümünden **CPU profilini etkinleştir** ' i seçin (bir hata ayıklama oturumunda olması gerekir).

![Tanılama Araçları CPU kullanımını etkinleştir](../profiling/media/prof-tour-enable-cpu-profiling.png "CPU kullanımını etkinleştirmek Tanılama Araçları")

Aracı en etkili şekilde kullanmak için kodunuzda iki kesme noktası, bir diğeri de işlevin sonunda ve biri veya çözümlemek istediğiniz kod bölgesi ayarlayın. İkinci kesme noktasında durakladığınızda profil oluşturma verilerini inceleyin.

**CPU kullanımı** görünümü, en uzun çalışan bir işlevle en üstte bulunan işlevlerin bir listesini gösterir. Bu, performans sorunlarının gerçekleştiği işlevlerde size rehberlik etmenize yardımcı olabilir.

![Tanılama Araçları CPU kullanımı görünümü](../profiling/media/prof-tour-cpu-usage.png "Tanılama Araçları CPU kullanımı")

İlgilendiğiniz bir işleve çift tıklayın ve seçilen işlevle pencerenin ortasında, sol taraftaki çağırma işlevine ve sağ tarafta işlev olarak adlandırılan daha ayrıntılı üç bölmeli "kelebek" görünümü görürsünüz. **Işlev gövdesi** bölümü, işlev gövdesinde harcanan ve çağrılan işlevlerde harcanan süre hariç toplam süreyi (ve zaman yüzdesini) gösterir. Bu veriler, işlevin kendisinin performans sorunu olup olmadığını değerlendirmenize yardımcı olabilir.

![Tanılama Araçları arayan "kelebek" görünümü](../profiling/media/prof-tour-cpu-usage-caller-callee.png "Tanılama Araçları arayan görünümü")

## <a name="analyze-memory-usage"></a>Bellek kullanımını analiz etme

**Tanılama araçları** penceresi, uygulamanızdaki bellek kullanımını değerlendirmenize de olanak tanır. Örneğin, yığındaki nesnelerin sayısına ve boyutuna bakabilirsiniz. Belleği çözümlemeye yönelik daha ayrıntılı yönergeler için bkz. [bellek kullanımını analiz etme](../profiling/memory-usage.md).

Hata ayıklama sırasında bellek kullanımını çözümlemek için en az bir bellek anlık görüntüsü yapmanız gerekir. Genellikle belleği çözümlemenin en iyi yolu iki anlık görüntü alma yöntemidir; bir şüpheli bellek sorunundan önceki ilk sağ tarafta ve bir şüpheli bellek sorunu oluştuktan sonra ikinci anlık görüntü. Daha sonra, iki anlık görüntüye ilişkin bir farkı görüntüleyebilir ve tam olarak nelerin değiştiğini görebilirsiniz.

![Tanılama Araçları anlık görüntü alın](../profiling/media/prof-tour-take-snapshots.gif "Tanılama Araçları anlık görüntü al")

Ok bağlantılarından birini seçtiğinizde, yığının fark görünümü verilir (kırmızı yukarı ok ![bellek kullanımı artışı](../profiling/media/prof-tour-mem-usage-up-arrow.png "Bellek kullanımı artışı") , artan nesne sayısını (solda) veya artan yığın boyutunu (sağ) gösterir). Doğru bağlantıya tıklarsanız, yığın boyutunu en çok arttığı nesnelere göre sıralanmış bir fark yığın görünümü alırsınız. Bu, bellek sorunlarını belirlemenize yardımcı olabilir. Örneğin, aşağıdaki çizimde, `ClassHandlersStore` nesneleri tarafından kullanılan baytlar ikinci anlık görüntüde 3.492 bayt artar.

![Tanılama Araçları yığın farkı görünümü](../profiling/media/prof-tour-mem-usage-diff-heap.png "Tanılama Araçları yığın farkı görünümü")

**Bellek kullanımı** görünümünde, sol taraftaki bağlantıya tıklarsanız, yığın görünümü nesne sayısına göre düzenlenir; belirli bir türün en fazla sayıyı arttığı nesneler en üstte gösterilir ( **Count diff** sütununa göre sıralanır).

## <a name="examine-performance-events"></a>Performans olaylarını İnceleme

Tanılama Araçları **olay** görünümü, bir kesme noktası veya kod atlama işlemi gibi hata ayıklarken oluşan farklı olayları gösterir. Olayın süresi (hata ayıklayıcının en son ne zaman duraklatıldığı veya uygulama başlatıldığında ölçülür) gibi bilgileri denetleyebilirsiniz. Örneğin, kod (F10, F11) ile karşılaşırsanız, **Olaylar** görünümü önceki adım işleminden geçerli adıma uygulama çalışma zamanı süresini gösterir.

![Tanılama Araçları Olaylar görünümü](../profiling/media/prof-tour-events.png "Tanılama Araçları görüntüleme olayları")

 > [!NOTE]
 > Visual Studio Enterprise sahipseniz, bu sekmede [IntelliTrace olaylarını](../debugger/intellitrace.md) da görebilirsiniz.

Aynı olaylar aynı zamanda, PerfTips olarak görüntüleyebileceğiniz kod düzenleyicisinde de görünür.

![Profil oluşturma turu PerfTips](../profiling/media/prof-tour-perf-tips.png "Profil oluşturma turu PerfTips")

## <a name="post_mortem"></a>Hata ayıklayıcı olmadan yayın derlemelerini profili

CPU kullanımı ve bellek kullanımı gibi profil oluşturma araçları, hata ayıklayıcıyla kullanılabilir (önceki bölümlere bakın) veya **yayın** yapıları için analiz sağlamak üzere tasarlanan performans profil oluşturucuyu kullanarak profil oluşturma araçları 'nı çalıştırabilirsiniz. Performans Profiler 'da, uygulama çalışırken tanılama bilgilerini toplayabilir ve ardından uygulama durdurulduktan sonra toplanan bilgileri inceleyebilirsiniz. Bu farklı yaklaşımlar hakkında daha fazla bilgi için bkz. [hata ayıklayıcı ile veya olmadan profil oluşturma araçlarını çalıştırma](../profiling/running-profiling-tools-with-or-without-the-debugger.md). Performans profil oluşturucusu 'nda [.NET nesne ayırma aracı](../profiling/dotnet-alloc-tool.md) gibi ek araçlar da mevcuttur.

![Performans profili Oluşturucu](../profiling/media/prof-tour-performance-profiler.png "Performans Profili Oluşturucu")

**Hata ayıkla** > **performans profil oluşturucu**' yı seçerek performans profil oluşturucuyu açın.

Pencere, bazı senaryolarda birden çok profil oluşturma aracı seçmenizi sağlayacak. CPU kullanımı gibi araçlar, analizinizdeki yardım için kullanabileceğiniz tamamlayıcı veriler sağlayabilir. Birden çok profil oluşturma aracı içeren senaryoları etkinleştirmek için [komut satırı profil oluşturucuyu](../profiling/profile-apps-from-command-line.md) de kullanabilirsiniz.

## <a name="examine-ui-performance-and-accessibility-events-uwp"></a>UI performans ve erişilebilirlik olaylarını İnceleme (UWP)

UWP uygulamalarınızda **Tanılama araçları** penceresinde **UI analizini** etkinleştirebilirsiniz. Araç yaygın performans ve erişilebilirlik sorunlarını arar ve hata ayıklarken bunları **Olaylar** görünümünde görüntüler. Olay açıklamaları, sorunları çözmenize yardımcı olabilecek bilgiler sağlar.

![Tanılama araçları 'nda UI Analizi olaylarını görüntüleme](../profiling/media/prof-tour-ui-analysis.png "Tanılama Araçları Kullanıcı arabirimi analiz olaylarını görüntüleme")

## <a name="analyze-resource-consumption-xaml"></a>Kaynak tüketimini analiz etme (XAML)

Windows Masaüstü WPF uygulamaları ve UWP uygulamaları gibi XAML uygulamalarında, Uygulama Zaman Çizelgesi aracını kullanarak kaynak tüketimini çözümleyebilirsiniz. Örneğin, uygulamanızın kullanıcı arabirimi çerçevelerini (düzen ve işleme) hazırlama, ağ ve disk isteklerine hizmet verme ve uygulama başlatma, sayfa yükleme ve pencere yeniden boyutlandırma gibi senaryolarda harcanan süreyi çözümleyebilirsiniz. Aracı kullanmak için, performans profil oluşturucusu 'nda **uygulama zaman çizelgesi** ' yi seçin ve ardından **Başlat**' ı seçin. Uygulamanızda, şüpheli kaynak tüketimi sorunu olan senaryoya gidin ve raporu oluşturmak için **koleksiyonu durdur** ' u seçin.

**Görsel işleme** grafiğindeki düşük framerates, uygulamanızı çalıştırırken gördüğünüz görsel sorunlara karşılık gelebilir. Benzer şekilde, **UI iş parçacığı kullanım** grafiğinde yüksek SAYıLAR da UI yanıtlama hızı sorunlarına karşılık gelebilir. Raporda, şüpheli performans sorunuyla bir zaman aralığı seçebilir ve ardından zaman çizelgesi ayrıntıları görünümündeki (alt bölme) ayrıntılı UI iş parçacığı etkinliklerini inceleyebilirsiniz.

![Uygulama Zaman Çizelgesi profil oluşturma aracı](../profiling/media/prof-tour-application-timeline.gif "Profil oluşturma turu Uygulama Zaman Çizelgesi")

Zaman çizelgesi ayrıntıları görünümünde etkinlik (veya dahil edilen kullanıcı arabirimi öğesi) gibi bilgileri etkinliğin süresiyle birlikte bulabilirsiniz. Örneğin, çizimde kılavuz denetimine yönelik bir **Düzen** olayı 57,53 MS alır.

Daha fazla bilgi için bkz. [uygulama zaman çizelgesi](../profiling/application-timeline.md).

## <a name="analyze-gpu-usage-direct3d"></a>(Direct3D) GPU kullanımını analiz etme

Direct3D uygulamalarında (Direct3D bileşenleri içinde C++OLMALıDıR) GPU 'daki etkinliği inceleyebilir ve performans sorunlarını çözümleyebilirsiniz. Daha fazla bilgi için bkz. [GPU kullanımı](/visualstudio/debugger/graphics/gpu-usage). Aracı kullanmak için performans Profilcisi ' nde **GPU kullanımı** ' nı seçin ve ardından **Başlat**' ı seçin. Uygulamanızda, profil oluşturma konusunda ilgilendiğiniz senaryoya gidin ve ardından bir rapor oluşturmak için **toplamayı durdur** ' u seçin.

Grafiklerde bir zaman aralığı seçip **Ayrıntıları görüntüle**' yi seçtiğinizde, alt bölmede ayrıntılı bir görünüm görüntülenir. Ayrıntılı görünümde, her CPU ve GPU üzerinde ne kadar etkinlik olduğunu inceleyebilirsiniz. Zaman çizelgesinde açılan pencereleri almak için en düşük bölmedeki olayları seçin. Örneğin, **var** olan çağrı açılan pencere görüntülenecek **olan olayı seçin** . (Açık gri dikey vsync çizgileri, belirli bir **mevcut** çağrının vsync kaçırılmadığını anlamak için başvuru olarak kullanılabilir. Uygulamanın artmasıyla ile 60 FPS 'e kadar olması için her iki VNET arasında bir tane **mevcut** çağrı olması gerekir.)

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

UWP uygulamalarında, `Windows.Web.Http` API kullanarak gerçekleştirilen ağ işlemlerini çözümleyebilirsiniz. Bu araç, erişim ve kimlik doğrulama sorunları, hatalı önbellek kullanımı ve kötü ekran ve indirme performansı gibi sorunları çözmenize yardımcı olabilir. Aracı kullanmak için, performans Profilcisi ' nde **ağ** ' ı seçin ve ardından **Başlat**' ı seçin. Uygulamanızda, `Windows.Web.Http`kullanan senaryoya gidin ve sonra raporu oluşturmak için **koleksiyonu durdur** ' u seçin.

![Ağ kullanımı profil oluşturma aracı](../profiling/media/prof-tour-network-usage.png "Diag ağı kullanımı")

Bir işlem içinde Özet görünümünü için daha fazla ayrıntı'ı seçin.

![Ağ kullanımı aracında ayrıntılı bilgiler](../profiling/media/prof-tour-network-usage-details.png "Diag ağı kullanım ayrıntıları")

Daha fazla bilgi için bkz. [ağ kullanımı](../profiling/network-usage.md).
::: moniker-end

## <a name="analyze-performance-legacy-tools"></a>Performansı çözümleme (eski araçlar)

::: moniker range="vs-2017"
Şu anda CPU kullanımı veya bellek kullanımı araçlarında bulunmayan izleme gibi özelliklere ihtiyacınız varsa ve Masaüstü veya ASP.NET uygulamaları çalıştırıyorsanız, profil oluşturma için Performans Gezgini kullanabilirsiniz. (UWP uygulamalarında desteklenmez). Daha fazla bilgi için bkz. [Performans Gezgini](../profiling/performance-explorer.md).
::: moniker-end

::: moniker range=">=vs-2019"
Visual Studio 2019 ' de, performans Sihirbazı gibi eski Performans Gezgini ve ilgili profil oluşturma araçları, **hata ayıklama** > **performans profil oluşturucu**kullanarak açabileceğiniz performans profil oluşturucuya katlanmıştı. Performans Profiler 'da, kullanılabilir tanılama araçları, seçilen hedefe ve geçerli, açık başlangıç projesine bağlıdır. CPU kullanımı aracı, daha önce performans sihirbazında desteklenen örnekleme özelliğini sağlar. Izleme Aracı, performans sihirbazındaki belgelenmiş profil oluşturma özelliği (kesin çağrı sayısı ve süreler için) sağlar. Ayrıca, performans Profiler 'da ek bellek araçları da görünür.
::: moniker-end

![Performans Gezgini aracı](../profiling/media/prof-tour-performance-explorer.png "Performans Gezgini")

## <a name="which-tool-should-i-use"></a>Hangi aracı kullanmalıyım?

Aşağıda, Visual Studio tekliflerinin farklı araçları ve bunları kullanabileceğiniz farklı proje türlerini listeleyen bir tablo verilmiştir:

::: moniker range=">=vs-2019"
|Performans aracı|Windows masaüstü|UWP|ASP.NET/ASP.NET Core|
|----------------------|---------------------|-------------|-------------|
|[CPU Kullanımı](../profiling/cpu-usage.md)|evet|evet|evet|
|[Bellek Kullanımı](../profiling/memory-usage.md)|evet|evet|evet|
|[.NET nesne ayırma](../profiling/dotnet-alloc-tool.md)|Evet (yalnızca .NET)|evet|evet|
|[GPU Kullanımı](/visualstudio/debugger/graphics/gpu-usage)|evet|evet|hayır|
|[Uygulama Zaman Çizelgesi](../profiling/application-timeline.md)|evet|evet|hayır|
|[PerfTips](../profiling/perftips.md)|evet|XAML için Evet, HTML için Hayır|evet|
|[Performans Gezgini](../profiling/performance-explorer.md)|evet|hayır|evet|
|[IntelliTrace](../debugger/intellitrace.md)|Yalnızca Visual Studio Enterprise .NET|Yalnızca Visual Studio Enterprise .NET|Yalnızca Visual Studio Enterprise .NET|
::: moniker-end

::: moniker range="vs-2017"
|Performans aracı|Windows masaüstü|UWP|ASP.NET/ASP.NET Core|
|----------------------|---------------------|-------------|-------------|
|[CPU Kullanımı](../profiling/cpu-usage.md)|evet|evet|evet|
|[Bellek Kullanımı](../profiling/memory-usage.md)|evet|evet|evet|
|[GPU Kullanımı](/visualstudio/debugger/graphics/gpu-usage)|evet|evet|hayır|
|[Uygulama Zaman Çizelgesi](../profiling/application-timeline.md)|evet|evet|hayır|
|[PerfTips](../profiling/perftips.md)|evet|XAML için Evet, HTML için Hayır|evet|
|[Performans Gezgini](../profiling/performance-explorer.md)|evet|hayır|evet|
|[IntelliTrace](../debugger/intellitrace.md)|Yalnızca Visual Studio Enterprise .NET|Yalnızca Visual Studio Enterprise .NET|Yalnızca Visual Studio Enterprise .NET|
|[Ağ Kullanımı](../profiling/network-usage.md)|hayır|evet|hayır|
|[HTML kullanıcı arabirimi yanıt hızı](../profiling/html-ui-responsiveness.md)|hayır|HTML için Evet, XAML için Hayır|hayır|
|[JavaScript Belleği](../profiling/javascript-memory.md)|hayır|HTML için Evet, XAML için Hayır|hayır|
::: moniker-end


## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio’da hata ayıklama](../debugger/debugger-feature-tour.md)
