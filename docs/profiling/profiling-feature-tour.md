---
title: Profil oluşturma araçlarıyla performansı ölçün
description: Visual Studio'da bulunan farklı tanı lama araçlarına kısa bir göz atın.
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
ms.openlocfilehash: b1ee476a518444bfff7a97a12c9fd814e9509239
ms.sourcegitcommit: 0ba0cbff77eac15feab1a73eeee3667006794b29
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/31/2020
ms.locfileid: "80412031"
---
# <a name="quickstart-first-look-at-profiling-tools"></a>Hızlı başlangıç: Profil oluşturma araçlarına ilk bakış

Visual Studio, uygulama türüne bağlı olarak farklı performans sorunlarını tanılamanıza yardımcı olacak çeşitli profil oluşturma araçları sağlar.

Hata ayıklama oturumu sırasında erişebileceğiniz profil oluşturma araçları Tanılama Araçları penceresinde kullanılabilir. Tanılama Araçları penceresi, siz kapatmadığınız sürece otomatik olarak görüntülenir. Pencereyi açmak için **Hata Ayıklama / Windows / Tanılama Araçlarını Göster'i**tıklatın. Pencere açıkken, veri toplamak istediğiniz araçları seçebilirsiniz.

![Tanıaraçları penceresi](../profiling/media/prof-tour-diagnostic-tools.png "Tanı Araçları")

Hata ayıklama yaparken, CPU ve bellek kullanımını çözümlemek için **Tanılama Araçları** penceresini kullanabilir ve performansla ilgili bilgileri gösteren olayları görüntüleyebilirsiniz.

![Tanılama Araçları Özet görünümü](../profiling/media/prof-tour-cpu-and-memory-graph.gif "Tanı araçları Özeti")

**Tanılama Araçları** penceresi genellikle profil uygulamaları için tercih edilen bir yoldur, ancak Sürüm oluşturur için uygulamanızın ölüm sonrası analizini de yapabilirsiniz. Farklı yaklaşımlar hakkında daha fazla bilgi istiyorsanız, [hata ayıklayıcılı veya hata ayıklayıcısız profil oluşturma araçlarını çalıştır'a](../profiling/running-profiling-tools-with-or-without-the-debugger.md)bakın. Farklı uygulama türleri için profil oluşturma aracı desteğini görmek için [bkz.](#which-tool-should-i-use)

> [!NOTE]
> Windows 7 ve sonraki lerle post-mortem araçlarını kullanabilirsiniz. Windows 8 ve daha sonra hata ayıklama **(Tanılama Araçları** penceresi) ile profil oluşturma araçları çalıştırmak için gereklidir.

## <a name="examine-performance-using-perftips"></a>PerfTips'i kullanarak performansı inceleyin

Genellikle, performans bilgilerini görüntülemek için en kolay yolu [PerfTips](../profiling/perftips.md)kullanmaktır. PerfTips'i kullanarak, kodunuzla etkileşimde bulunduktan sonra performans bilgilerini görüntüleyebilirsiniz. Olayın süresi (hata ayıklayıcının en son duraklatıldığından veya uygulamanın ne zaman başlatıldığa göre ölçülür) gibi bilgileri kontrol edebilirsiniz. Örneğin, kod (F10, F11) ile adım atarsanız, PerfTips size bir önceki adım işleminden geçerli adıma kadar uygulama çalışma süresini gösterir.

![Profil Oluşturma Turu PerfTips](../profiling/media/prof-tour-perf-tips.png "Profil Oluşturma Turu PerfTips")

Bir kod bloğunun yürütülmesinin ne kadar sürdüğünü veya tek bir işlevin tamamlanmasının ne kadar sürdüğünü incelemek için PerfTips'i kullanabilirsiniz.

PerfTips, Tanılama Araçlarının **Olaylar** görünümünde de görünen aynı olayları gösterir. **Olaylar** görünümünde, ara verme noktası nın ayarlanması veya kod adımlama işlemi gibi hata ayıklama sırasında meydana gelen farklı olayları görüntüleyebilirsiniz.

![Tanılama Araçları Etkinlikler görünümü](../profiling/media/prof-tour-events.png "Tanılama Araçları Olayları Görüntüleme")

 > [!NOTE]
 > Visual Studio Enterprise'ınız varsa, bu sekmede [IntelliTrace olaylarını](../debugger/intellitrace.md) da görebilirsiniz.

## <a name="analyze-cpu-usage"></a>CPU Kullanımını Analiz Etme

CPU Kullanımı aracı, uygulamanızın performansını analiz etmeye başlamak için iyi bir yerdir. Uygulamanızın tüketen CPU kaynakları hakkında daha fazla şey söyleyecektir. CPU Kullanım aracının daha ayrıntılı bir gözden geçirme için [bkz.](../profiling/beginners-guide-to-performance-profiling.md)

Tanılama Araçları'nın **Özet** görünümünden, **CPU Profil Oluşturmayı Etkinleştir'i** seçin (hata ayıklama oturumunda olmalısınız).

![Tanılama Araçlarında CPU kullanımını etkinleştirme](../profiling/media/prof-tour-enable-cpu-profiling.png "Tanılama Araçları CPU Kullanımını Etkinleştirin")

Aracı en etkili şekilde kullanmak için, kodunuzda biri başlangıçta, diğeri işlevin sonunda veya çözümlemek istediğiniz kod bölgesine olmak üzere iki kesme noktası ayarlayın. İkinci kesme noktasında duraklatıldığında profil oluşturma verilerini inceleyin.

**CPU Kullanım** görünümü, en uzun süre çalışan ve en üstte en uzun süre çalışan işlevler tarafından sıralanan işlevlerin bir listesini gösterir. Bu, performans darboğazlarının yaşandığı işlevlere yol gösterebilirsiniz.

![Tanılama Araçları CPU Kullanım görünümü](../profiling/media/prof-tour-cpu-usage.png "Tanı Araçları CPU Kullanımı")

İlgilendiğiniz bir işleve çift tıklayın ve pencerenin ortasında seçili işlev, solda arama işlevi ve sağda çağrılan işlevler ile daha ayrıntılı bir üç bölmeli "kelebek" görünümü görürsünüz. **İşlev Gövdesi** bölümü, çağrı ve çağrılan işlevler dışında işlev gövdesinde harcanan toplam süreyi (ve zaman yüzdesini) gösterir. Bu veriler, işlevin kendisinin bir performans darboğaz olup olmadığını değerlendirmenize yardımcı olabilir.

![Tanılama Araçları arayan callee "kelebek" görünümü](../profiling/media/prof-tour-cpu-usage-caller-callee.png "Tanılama Araçları Arayan Callee Görünümü")

## <a name="analyze-memory-usage"></a>Bellek kullanımını analiz etme

**Tanılama Araçları** penceresi, **Bellek Kullanımı** aracını kullanarak uygulamanızdaki bellek kullanımını değerlendirmenize de olanak tanır. Örneğin, yığındaki nesnelerin sayısına ve boyutuna bakabilirsiniz. Belleği çözümlemek için daha ayrıntılı yönergeler için [bkz.](../profiling/memory-usage.md) Başka bir bellek çözümleme aracı, [.NET Nesne Ayırma aracı,](../profiling/dotnet-alloc-tool.md).NET kodunuzdaki ayırma desenlerini ve anormallikleri belirlemenize yardımcı olur.

Hata ayıklama tümleşik Bellek Kullanımı ile de bellek kullanımını analiz etmek için en az bir bellek anlık görüntüsü almanız gerekir. Çoğu zaman, belleği çözümlemenin en iyi yolu iki anlık görüntü almaktır; şüpheli bir bellek sorunundan hemen önce ilk ve şüpheli bir bellek sorunu oluştuktan hemen sonra ikinci anlık görüntü. Ardından, iki anlık görüntünün bir kısmını görüntüleyebilir ve tam olarak neyin değiştiğini görebilirsiniz.

![Tanılama Araçlarında anlık görüntü alma](../profiling/media/prof-tour-take-snapshots.gif "Tanılama Araçları Anlık Görüntü Alır")

Ok bağlantılarından birini seçtiğinizde, yığın (kırmızı yukarı ok ![Bellek Kullanım Artışı](../profiling/media/prof-tour-mem-usage-up-arrow.png "Bellek Kullanımı Nın Artması") artan nesne sayısı (sol) veya artan bir yığın boyutu (sağ) gösterir) bir diferansiyel görünümü verilir. Doğru bağlantıyı tıklattığınızda, yığın boyutunda en çok artış gösteren nesneler tarafından sıralanan bir diferansiyel yığın görünümü elde elabilirsiniz. Bu, bellek sorunlarını belirlemenize yardımcı olabilir. Örneğin, aşağıdaki resimde, nesneler tarafından `ClassHandlersStore` kullanılan baytlar ikinci anlık görüntüde 3.492 bayt artmıştır.

![Tanı Araçları yığın diff görünümü](../profiling/media/prof-tour-mem-usage-diff-heap.png "Tanı araçları Yığın Diff görünümü")

**Bellek Kullanımı** görünümünde soldaki bağlantıyı tıklattığınızda, yığın görünümü nesne sayısına göre düzenlenir; en çok artan belirli bir türdeki nesneler üstte gösterilir **(Count Diff** sütununa göre sıralanır).

## <a name="profile-release-builds-without-the-debugger"></a><a name="post_mortem"></a>Profil sürümü hata ayıklama olmadan oluşturur

CPU Kullanımı ve Bellek Kullanımı gibi profil oluşturma araçları hata ayıklayıcıyla kullanılabilir (önceki bölümlere bakın) veya **Sürüm** oluşturmaları için çözümleme sağlamak amacıyla Performans Profiloluşturucusu'nu kullanarak profil oluşturma araçlarını öldükten sonra çalıştırabilirsiniz. Performans Profilcisi'nde, uygulama çalışırken tanılama bilgilerini toplayabilir ve uygulama durdurulduktan sonra toplanan bilgileri inceleyebilirsiniz. Bu farklı yaklaşımlar hakkında daha fazla bilgi için [bkz.](../profiling/running-profiling-tools-with-or-without-the-debugger.md) .NET Nesne [Ayırma aracı](../profiling/dotnet-alloc-tool.md) gibi ek araçlar da Performans Profilleyicisi'nde kullanılabilir.

![Performans Profili Oluşturucu](../profiling/media/prof-tour-performance-profiler.png "Performans Profili Oluşturucu")

**Hata Ayıklama** > Performans Profilcisi'ni seçerek Performans**Profilleyicisini**açın.

Pencere, bazı senaryolarda birden çok profil oluşturma aracı seçmenize olanak sağlar. CPU Kullanımı gibi araçlar, çözümlemenizde yardımcı olmak için kullanabileceğiniz tamamlayıcı veriler sağlayabilir. Birden çok profil oluşturma aracı içeren senaryoları etkinleştirmek için [komut satırı profilleyicisini](../profiling/profile-apps-from-command-line.md) de kullanabilirsiniz.

## <a name="examine-ui-performance-and-accessibility-events-uwp"></a>UI performansını ve erişilebilirlik olaylarını inceleyin (UWP)

UWP uygulamalarınızda **Tanılama Araçları** penceresinde **UI Çözümlemesini** etkinleştirebilirsiniz. Araç, sık karşılaşılan performans veya erişilebilirlik sorunlarını arar ve siz hata ayıklarken **bunları Olaylar** görünümünde görüntüler. Olay açıklamaları, sorunları çözmeye yardımcı olabilecek bilgiler sağlar.

![Tanılama araçlarında UI çözümleme olaylarını görüntüleyin](../profiling/media/prof-tour-ui-analysis.png "Tanıaraçları Görünüm UI Analiz Olayları")

## <a name="analyze-resource-consumption-xaml"></a>Kaynak tüketimini analiz etme (XAML)

Windows masaüstü WPF uygulamaları ve UWP uygulamaları gibi XAML uygulamalarında, Uygulama Zaman Çizelgesi aracını kullanarak kaynak tüketimini analiz edebilirsiniz. Örneğin, uygulamanızın Kullanıcı Arabirimi çerçeveleri (düzen ve işleme), servis ağı ve disk istekleri ni hazırlamave uygulama başlatma, sayfa yüklemesi ve Pencere yeniden boyutlandırma gibi senaryolarda harcadığı zamanı çözümleyebilirsiniz. Aracı kullanmak için Performans Profiloluşturucu'da **Uygulama Zaman Çizelgesi'ni** seçin ve ardından **Başlat'ı**seçin. Uygulamanızda, şüpheli bir kaynak tüketimi sorunuyla senaryoyu gözden geçirin ve ardından raporu oluşturmak için **Koleksiyonu Durdur'u** seçin.

**Görsel iş verme** grafiğindeki düşük kare hızları, uygulamanızı çalıştırırken gördüğünüz görsel sorunlara karşılık gelebilir. Benzer şekilde, **UI iş parçacığı kullanım** grafiğindeki yüksek sayılar da UI yanıt verme sorunlarına karşılık gelebilir. Raporda, şüpheli bir performans sorunu olan bir zaman dilimi seçebilir ve ardından Zaman Çizelgesi ayrıntıları görünümünde (alt bölme) ayrıntılı UI iş parçacığı etkinliklerini inceleyebilirsiniz.

![Uygulama Zaman Çizelgesi profil oluşturma aracı](../profiling/media/prof-tour-application-timeline.gif "Profil Oluşturma Turu Uygulama Zaman Çizelgesi")

Zaman Çizelgesi ayrıntıları görünümünde, etkinlik süresiyle birlikte etkinlik türü (veya ilgili Kullanıcı Arabirimi öğesi) gibi bilgileri bulabilirsiniz. Örneğin, resimde, Bir Izgara denetimi için **Düzen** olayı 57,53 ms alır.

Daha fazla bilgi için [Uygulama Zaman Çizelgesi'ne](../profiling/application-timeline.md)bakın.

## <a name="analyze-gpu-usage-direct3d"></a>GPU kullanımını analiz et (Direct3D)

Direct3D uygulamalarında (Direct3D bileşenleri C++'da olmalıdır), GPU'daki etkinliği inceleyebilir ve performans sorunlarını çözümleyebilirsiniz. Daha fazla bilgi için [GPU Kullanımı'na](/visualstudio/debugger/graphics/gpu-usage)bakın. Aracı kullanmak için Performans Profilleyicisi'nde **GPU Kullanımı'nı** seçin ve ardından **Başlat'ı**seçin. Uygulamanızda, profil oluşturmayla ilgilendiğiniz senaryoyu gözden geçirin ve ardından bir rapor oluşturmak için **Koleksiyonu Durdur'u** seçin.

Grafiklerde bir zaman dilimi seçip **görünüm ayrıntılarını**seçtiğinizde, alt bölmede ayrıntılı bir görünüm görüntülenir. Ayrıntılı görünümde, her CPU ve GPU'da ne kadar etkinlik olduğunu inceleyebilirsiniz. Zaman çizelgesinde açılır pencereler için en düşük bölmedeki olayları seçin. Örneğin, **Çağrı** açılır pencerelerini görüntülemek için **Şimdiki Zaman** olayını seçin. (Açık gri dikey Vsync çizgileri, bazı **Present** çağrılarının Vsync'i kaçırıp kaçırmadığını anlamak için bir referans olarak kullanılabilir. Uygulamanın sürekli olarak 60 FPS'ye ulaşabilmesi için her iki Vsync arasında bir **Hediye** çağrısı olmalıdır.)

![GPU Kullanım profilleme aracı](../profiling/media/prof-tour-gpu-usage.png "Diag GPU Kullanımı")

CPU bağlı mı yoksa GPU'ya bağlı performans darboğazları mı olduğunu belirlemek için grafikleri de kullanabilirsiniz.

::: moniker range="vs-2017"
## <a name="analyze-performance-javascript-uwp"></a>Performansı analiz et (JavaScript UWP)

UWP uygulamaları için JavaScript Bellek aracını ve HTML UI Yanıt Verme aracını kullanabilirsiniz.

JavaScript Bellek aracı, diğer uygulama türleri için kullanılabilen Bellek Kullanımı aracına benzer. Bellek kullanımını anlamak ve uygulamanızdaki bellek sızıntılarını bulmak için bu aracı kullanabilirsiniz. Araç hakkında daha fazla bilgi için [JavaScript Memory'e](../profiling/javascript-memory.md)bakın.

![JavaScript Bellek profil oluşturma aracı](../profiling/media/diagjsmemory.png "DiagJSMemory")

UWP uygulamalarında UI yanıt verme, yavaş yükleme süresi ve yavaş görsel güncelleştirmeleri tanılamak için HTML UI Responsiveness aracını kullanın. Kullanım, diğer uygulama türleri için Uygulama Zaman Çizelgesi aracına benzer. Daha fazla bilgi için [HTML Kullanıcı Arabirimi yanıt verme](../profiling/html-ui-responsiveness.md)bilgisine bakın.

![HTML UI Responsiveness profil oluşturma aracı](../profiling/media/diaghtmlresp.png "DiagHTMLResp")
::: moniker-end

::: moniker range="vs-2017"
## <a name="analyze-network-usage-uwp"></a>Ağ kullanımını analiz etme (UWP)

UWP uygulamalarında, `Windows.Web.Http` API kullanılarak gerçekleştirilen ağ işlemlerini çözümleyebilirsiniz. Bu araç, erişim ve kimlik doğrulama sorunları, yanlış önbellek kullanımı ve düşük görüntüleme ve indirme performansı gibi sorunları çözmenize yardımcı olabilir. Aracı kullanmak için Performans Profilleyicisi'nde **Ağ'ı** seçin ve ardından **Başlat'ı**seçin. Uygulamanızda, raporu kullanan `Windows.Web.Http`senaryoyu gözden geçirin ve ardından raporu oluşturmak için Koleksiyonu **Durdur'u** seçin.

![Ağ Kullanımı profil oluşturma aracı](../profiling/media/prof-tour-network-usage.png "Diag Ağ Kullanımı")

Daha fazla ayrıntı görüntülemek için özet görünümünde bir işlem seçin.

![Ağ Kullanımı aracında ayrıntılı bilgi](../profiling/media/prof-tour-network-usage-details.png "Diag Network Kullanım Detayları")

Daha fazla bilgi için [Ağ Kullanımı'na](../profiling/network-usage.md)bakın.
::: moniker-end

## <a name="analyze-performance-legacy-tools"></a>Performansı analiz et (eski araçlar)

::: moniker range="vs-2017"
CPU Kullanımı veya Bellek Kullanımı araçlarında şu anda bulunmayan enstrümantasyon gibi özelliklere ihtiyacınız varsa ve masaüstü veya ASP.NET uygulamaları çalıştırıyorsanız, profil oluşturma için Performans Gezgini'ni kullanabilirsiniz. (UWP uygulamalarında desteklenmez). Daha fazla bilgi için [Performans Gezgini'ne](../profiling/performance-explorer.md)bakın.
::: moniker-end

::: moniker range=">=vs-2019"
Visual Studio 2019'da, eski Performans Gezgini ve Performans Sihirbazı gibi ilgili profil oluşturma araçları, **Hata Ayıklama** > **Performans Profilleyicisi'ni**kullanarak açabileceğiniz Performans Profilleyicisi'ne katlandı. Performans Profilcisi'nde, kullanılabilir tanılama araçları seçilen hedefe ve geçerli, açık başlangıç projesine bağlıdır. CPU Kullanımı aracı, Performans Sihirbazı'nda daha önce desteklenen örnekleme yeteneğini sağlar. Instrumentation aracı, Performans Sihirbazı'nda bulunan enstrümantasyonlu profil oluşturma özelliğini (hassas çağrı sayıları ve süreler için) sağlar. Performans Profilcisi'nde ek bellek araçları da görünür.
::: moniker-end

![Performans Gezgini aracı](../profiling/media/prof-tour-performance-explorer.png "Performans Gezgini")

## <a name="which-tool-should-i-use"></a>Hangi aracı kullanmalıyım?

Visual Studio'nun sunduğu farklı araçları ve bunları kullanabileceğiniz farklı proje türlerini listeleyen bir tablo aşağıda verilmiştir:

::: moniker range=">=vs-2019"
|Performans Aracı|Windows masaüstü|UWP|ASP.NET/ASP.NET Çekirdek|
|----------------------|---------------------|-------------|-------------|
|[CPU Kullanımı](../profiling/cpu-usage.md)|evet|evet|evet|
|[Bellek Kullanımı](../profiling/memory-usage.md)|evet|evet|evet|
|[.NET Nesne Tahsisi](../profiling/dotnet-alloc-tool.md)|evet (.NET sadece)|evet|evet|
|[GPU Kullanımı](/visualstudio/debugger/graphics/gpu-usage)|evet|evet|hayır|
|[Uygulama Zaman Çizelgesi](../profiling/application-timeline.md)|evet|evet|hayır|
|[PerfTips](../profiling/perftips.md)|evet|Evet XAML için, HTML için hayır|evet|
|[Performans Gezgini](../profiling/performance-explorer.md)|evet|hayır|evet|
|[IntelliTrace](../debugger/intellitrace.md)|.NET sadece Visual Studio Enterprise ile|.NET sadece Visual Studio Enterprise ile|.NET sadece Visual Studio Enterprise ile|
::: moniker-end

::: moniker range="vs-2017"
|Performans Aracı|Windows masaüstü|UWP|ASP.NET/ASP.NET Çekirdek|
|----------------------|---------------------|-------------|-------------|
|[CPU Kullanımı](../profiling/cpu-usage.md)|evet|evet|evet|
|[Bellek Kullanımı](../profiling/memory-usage.md)|evet|evet|evet|
|[GPU Kullanımı](/visualstudio/debugger/graphics/gpu-usage)|evet|evet|hayır|
|[Uygulama Zaman Çizelgesi](../profiling/application-timeline.md)|evet|evet|hayır|
|[PerfTips](../profiling/perftips.md)|evet|Evet XAML için, HTML için hayır|evet|
|[Performans Gezgini](../profiling/performance-explorer.md)|evet|hayır|evet|
|[IntelliTrace](../debugger/intellitrace.md)|.NET sadece Visual Studio Enterprise ile|.NET sadece Visual Studio Enterprise ile|.NET sadece Visual Studio Enterprise ile|
|[Ağ Kullanımı](../profiling/network-usage.md)|hayır|evet|hayır|
|[HTML kullanıcı arabirimi yanıt hızı](../profiling/html-ui-responsiveness.md)|hayır|HTML için evet, XAML için hayır|hayır|
|[JavaScript Belleği](../profiling/javascript-memory.md)|hayır|HTML için evet, XAML için hayır|hayır|
::: moniker-end


## <a name="see-also"></a>Ayrıca bkz.
- [Visual Studio’da hata ayıklama](../debugger/debugger-feature-tour.md)
