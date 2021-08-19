---
title: Kullanmaya başlayın araçlarıyla birlikte kullanma
description: Verilerde kullanılabilen farklı tanılama araçlarına kısa bir Visual Studio.
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
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: c0b3bb8102020e7b091ea7c6127f449b4ef70eca
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122038701"
---
# <a name="first-look-at-profiling-tools"></a>Profil oluşturma araçlarına ilk bakış

Visual Studio, uygulama türünüze bağlı olarak farklı performans sorunlarını tanılamanıza yardımcı olacak çeşitli profil oluşturma araçları sağlar. Bu makalede, en yaygın profil oluşturma araçlarına hızlı bir bakış sağlaruz.

Farklı uygulama türleri için profil oluşturma aracı desteğini görmek için bkz. [Hangi aracı kullan uygulamam gerekir?](#which-tool-should-i-use)

## <a name="measure-performance-while-debugging"></a>Hata ayıklama sırasında performansı ölçme

Hata ayıklama oturumu sırasında erişebilirsiniz profil oluşturma araçları, Tanılama Araçları kullanılabilir. Siz Tanılama Araçları pencere otomatik olarak görüntülenir. Pencereyi açmak için Hata Ayıkla **/ Windows / Tanılama Araçları Göster'e tıklayın** (veya **Ctrl** Alt  +    +  **F2 tuşlarına basın).** Pencere açıkken, veri toplamak istediğiniz araçları seçin.

![Tanılama Araçları penceresi](../profiling/media/prof-tour-diagnostic-tools.png "Tanılama Araçları")

Hata ayıklarken, CPU ve **bellek Tanılama Araçları** analiz etmek için Tanılama Araçları penceresini kullanabilir ve performansla ilgili bilgileri göstermek üzere olayları görüntüebilirsiniz.

![Tanılama Araçları Özet görünümü](../profiling/media/prof-tour-cpu-and-memory-graph.gif "Tanılama Araçları Özeti")

Uygulama **Tanılama Araçları** profili oluşturmanın yaygın bir yolu vardır, ancak Yayın derlemeleri için bunun yerine uygulamanın son inceleme analizini de yapabiliriz. Farklı yaklaşımlar hakkında daha fazla bilgi için [bkz. Hata ayıklayıcı](../profiling/running-profiling-tools-with-or-without-the-debugger.md)ile veya hata ayıklayıcı olmadan profil oluşturma araçlarını çalıştırma. Farklı uygulama türleri için profil oluşturma aracı desteğini görmek için bkz. [Hangi aracı kullan uygulamam gerekir?](#which-tool-should-i-use)

Tanılama Araçları penceresinde veya hata ayıklama oturumu sırasında kullanılabilen araçlar şunlardır:
- [CPU kullanımı](../profiling/beginners-guide-to-performance-profiling.md)
- [Bellek kullanımı](../profiling/memory-usage.md)
- [PerfTips](../profiling/perftips.md)

> [!NOTE]
> Windows 8 aracı ( hata ayıklayıcısı ) ile profil oluşturma araçlarını **çalıştırmak** için Tanılama Araçları gerekir. 7. [ve sonraki bir sonraki bir](#post_mortem) Windows sonrası araçlarını kullanabilirsiniz. 

## <a name="measure-performance-in-release-builds"></a><a name="post_mortem"></a> Yayın derlemeleri performansını ölçme

Yayın derlemeleri Performans Profili Oluşturucu için analiz sağlamak **üzere** tasarlanmıştır. Bu Performans Profili Oluşturucu, uygulama çalışırken tanılama bilgilerini toplayabilirsiniz ve ardından uygulama durdurulduktan sonra toplanan bilgileri incelersiniz (son inceleme analizi).

Hata ayıkla Performans Profili Oluşturucu **(veya**  >  Alt + F2)**Performans Profili Oluşturucu** **seçerek dosyayı açın.**

![Performans Profili Oluşturucu](../profiling/media/prof-tour-performance-profiler.png "Performans Profili Oluşturucu")

Performans Profili Oluşturucu'da CPU Kullanımı veya Bellek kullanım aracının hata ayıklayıcısıyla tümleştirilmiş araçlarla karşılaştırması hakkında daha fazla bilgi için bkz. Hata ayıklayıcı ile veya hata ayıklayıcı olmadan profil oluşturma [araçlarını çalıştırma.](../profiling/running-profiling-tools-with-or-without-the-debugger.md) 

Aşağıdaki araçlar Performans Profili Oluşturucu:

- [CPU kullanımı](../profiling/cpu-usage.md)
- [.NET nesne ayırma](../profiling/dotnet-alloc-tool.md)
- [Bellek kullanımı](../profiling/memory-usage-without-debugging2.md)
- [.NET zaman uyumsuz aracı](../profiling/analyze-async.md)
- [Veritabanı aracı](../profiling/analyze-database.md)
- [GPU kullanımı](../profiling/gpu-usage.md)

Farklı uygulama türleri için profil oluşturma aracı desteğini görmek için bkz. [Hangi aracı kullan uygulamam gerekir?](#which-tool-should-i-use)

Bazı senaryolarda pencere birden çok profil oluşturma aracı [seçmenize olanak sağlar.](../profiling/use-multiple-profiler-tools-simultaneously.md) CPU Kullanımı gibi araçlar, analizinize yardımcı olmak için kullanabileceğiniz tamamlayıcı veriler sağlar. Birden çok profil oluşturma [aracı içeren senaryoları etkinleştirmek](../profiling/profile-apps-from-command-line.md) için komut satırı profilleyiciyi de kullanabilirsiniz.

## <a name="examine-performance-using-perftips"></a>PerfTips kullanarak performansı inceleme

Performans bilgilerini görüntülemenin en kolay yolu genellikle [PerfTips kullanmaktır.](../profiling/perftips.md) PerfTips'i kullanarak, kodunuzla etkileşime çalışırken performans bilgilerini görüntüebilirsiniz. Olayın süresi (hata ayıklayıcının en son ne zaman duraklatılmış olduğu veya uygulamanın ne zaman başlatılmış olduğuyla ölçülen) gibi bilgileri kontrol edin. Örneğin, kodda (F10, F11) adım adım ilerlersanız, PerfTips önceki adımdan geçerli adıma kadar olan uygulama çalışma zamanı süresini gösterir.

![Profil Oluşturma Turu PerfTips](../profiling/media/prof-tour-perf-tips.png "Profil Oluşturma Turu PerfTips")

PerfTips'i kullanarak bir kod bloğu için yürütmenin ne kadar zaman veya tek bir işlevin tamamlanmasının ne kadar zaman alır olduğunu inceebilirsiniz.

PerfTips, aynı olayları aynı zamanda olay **görünümünün** Olaylar görünümünde de Tanılama Araçları. Olaylar **görünümünde,** hata ayıklama sırasında oluşan kesme noktası veya kod adımlama işlemi gibi farklı olayları görüntüebilirsiniz.

![Tanılama Araçları Olayları görünümü](../profiling/media/prof-tour-events.png "Tanılama Araçları Görüntüleme")

 > [!NOTE]
 > Bu sekmede Visual Studio Enterprise [IntelliTrace olaylarını da](../debugger/intellitrace.md) görebilirsiniz.

## <a name="analyze-cpu-usage"></a>CPU kullanımını analiz etme

CPU Kullanımı aracı, uygulama performansını analiz etmek için iyi bir yerdir. Bu, uygulamanın tüketen CPU kaynakları hakkında daha fazla bilgi sağlar. Hata [ayıklayıcısıyla tümleşik CPU Kullanımı aracını veya](../profiling/beginners-guide-to-performance-profiling.md) son işlem sonrası CPU Kullanımı aracını [kullanabilirsiniz.](../profiling/cpu-usage.md)

Hata ayıklayıcısıyla tümleşik CPU Kullanımı aracını kullanırken Tanılama Aracı penceresini açın (kapalı ise Hata ayıkla / Windows **/ Göster'i Tanılama Araçları).** Hata ayıklama sırasında Özet görünümünü **açın ve** CPU Profilini **Kayded'i seçin.**

![Ağ içinde CPU kullanımını Tanılama Araçları](../profiling/media/prof-tour-enable-cpu-profiling.png "Tanılama Araçları CPU Kullanımını Etkinleştirme")

Aracı kullanmanın bir yolu, kodunda biri başlangıçta, biri işlevin sonunda veya analiz etmek istediğiniz kod bölgesinde olmak üzere iki kesme noktası ayarlamaktır. İkinci kesme noktası duraklatılırken profil oluşturma verilerini inceler.

**CPU Kullanımı görünümü,** en uzun çalışana göre sıra edilen işlevlerin listesini ve en üstte en uzun çalışan işlevi gösterir. Bu, performans sorunlarının ortaya çıktı olduğu işlevlerde size yol gösterir.

![Tanılama Araçları CPU Kullanımı görünümü](../profiling/media/prof-tour-cpu-usage.png "Tanılama Araçları CPU Kullanımı")

İlgilenen bir işleve çift tıklayın; pencerenin ortasında seçili işlevi, sol tarafta çağıran işlevi ve sağ tarafta işlevleri çağıran daha ayrıntılı bir üç bölmeli "yer" görünümü görüntülenir. İşlev **Gövdesi bölümünde,** çağrı yapılan ve çağrılan işlevlerde harcanan süre hariç olmak üzere işlev gövdesinde harcanan toplam süre (ve sürenin yüzdesi) yer almaktadır. Bu veriler, işlevin kendisi performans sorunu olup olmadığını değerlendirmeye yardımcı olabilir.

![Tanılama Araçları çağıran "yer" görünümü](../profiling/media/prof-tour-cpu-usage-caller-callee.png "Tanılama Araçları Çağıran Görünümü")

## <a name="analyze-memory-usage"></a>Bellek kullanımını analiz etme

Bu **Tanılama Araçları,** Uygulamanıza Bellek Kullanımı aracını kullanarak bellek kullanımını **değerlendirmenize de olanak** sağlar. Örneğin, yığındaki nesnelerin sayısına ve boyutuna bakabilirsiniz. Hata ayıklayıcısı [ile tümleşik Bellek Kullanımı aracını veya](../profiling/memory-usage.md) son işlem sonrası Bellek Kullanımı [aracını](../profiling/memory-usage-without-debugging2.md) Performans Profili Oluşturucu.

.NET geliştiricileri [.NET](../profiling/dotnet-alloc-tool.md) Nesne Ayırma aracı veya Bellek kullanım [aracı arasında seçim](../profiling/memory-usage.md) olabilir.

- **.NET Nesne Ayırma aracı,** .NET kodundaki ayırma desenlerini ve anomalilerini tanımlamanıza yardımcı olur ve atık toplama ile ilgili yaygın sorunların belirlenmesine yardımcı olur. Bu araç yalnızca son bir son durum aracı olarak çalışır. Bu aracı yerel veya uzak makinelerde çalıştırabilirsiniz.
- Bellek **kullanım aracı,** genellikle .NET uygulamalarıyla sık karşılaşılan bellek sızıntılarını tanımlamaya yardımcı olur. Kodda adımlama gibi bellek denetimi sırasında hata ayıklayıcı özelliklerini kullanmak gerekirse hata [ayıklayıcı ile tümleşik Bellek](../profiling/beginners-guide-to-performance-profiling.md) kullanım aracı önerilir.

Bellek Kullanımı aracıyla bellek **kullanımını analiz etmek** için en az bir bellek anlık görüntüsü al gerekir. Genellikle, belleği analiz etmek için en iyi yol iki anlık görüntü almaktır; şüpheli bellek sorunundan hemen önce ilk anlık görüntü ve şüpheli bellek sorunundan hemen sonra ikinci anlık görüntü. Ardından iki anlık görüntü farkını görüntüp tam olarak nelerin değiştiğini görüntüln. Aşağıdaki çizimde hata ayıklayıcısıyla tümleşik araçla anlık görüntü alma adımları gösterilmiştir.

![Sanal makinede anlık görüntü Tanılama Araçları](../profiling/media/prof-tour-take-snapshots.gif "Tanılama Araçları Anlık Görüntü Alma")

Ok bağlantılarından birini seçerek yığının fark görünümünü alırsınız (kırmızı ![](../profiling/media/prof-tour-mem-usage-up-arrow.png "Bellek Kullanımı Artışı") yukarı ok Bellek Kullanımı Artışı artan nesne sayısını (sol) veya artan yığın boyutunu (sağ) gösterir). Doğru bağlantıya tıklarsanız, yığın boyutu en fazla artan nesnelere göre sıraılmış fark yığın görünümü elde edersiniz. Bu, bellek sorunlarını tespit etmeye yardımcı olabilir. Örneğin, aşağıdaki çizimde, nesneler tarafından kullanılan baytlar ikinci anlık `ClassHandlersStore` görüntüde 3.492 bayt artmıştır.

![Tanılama Araçları yığın fark görünümü](../profiling/media/prof-tour-mem-usage-diff-heap.png "Tanılama Araçları Yığın Fark görünümü")

Bellek Kullanımı görünümünde bunun yerine sol  tarafta yer alan bağlantıya tıklarsanız yığın görünümü nesne sayısına göre düzenlenmiştir; Sayı olarak en fazla artıran belirli bir türdeki nesneler en üstte gösterilir **(Count Diff sütununa göre sıralanmış).**

## <a name="analyze-resource-consumption-xaml"></a>Kaynak tüketimini analiz etme (XAML)

Windows masaüstü WPF uygulamaları ve UWP uygulamaları gibi XAML uygulamalarında kaynak tüketimini analiz etmek için Uygulama Zaman Çizelgesi kullanabilirsiniz. Örneğin, kullanıcı arabirimi çerçeveleri (düzen ve işleme), ağ ve disk isteklerine hizmet verme ve uygulama başlatma, sayfa yükleme ve Pencere yeniden boyutlandırma gibi senaryolarda, uygulamanın kullanıcı arabirimi çerçevelerini hazırlaması için harcadığı zamanı analiz edebilirsiniz. Aracı kullanmak için, araç **Uygulama Zaman Çizelgesi'Performans Profili Oluşturucu** ve ardından Başlat'ı **seçin.** Uygulamanıza, şüpheli bir kaynak tüketimi sorunuyla ilgili senaryoyu gidin ve ardından Raporu oluşturmak için **Koleksiyonu durdur'a** seçin.

Görsel aktarım hızı **grafı'nın düşük** kare hızı, uygulamanızı çalıştırarak gördüğünüz görsel sorunlara karşılık gelir. Benzer şekilde, kullanıcı arabirimi iş parçacığı **kullanım grafı içinde yüksek** sayılar kullanıcı arabirimi yanıt verme sorunlarına da karşılık geliyor olabilir. Raporda, şüpheli performans sorunu olan bir zaman dönemi seçin ve ardından Zaman Çizelgesi ayrıntıları görünümünde (alt bölme) ayrıntılı kullanıcı arabirimi iş parçacığı etkinliklerini inceleyebilirsiniz.

![Uygulama Zaman Çizelgesi profili oluşturma aracı](../profiling/media/prof-tour-application-timeline.gif "Profil Oluşturma Turu Uygulama Zaman Çizelgesi")

Zaman çizelgesi ayrıntıları görünümünde etkinlik türü (veya dahil olan kullanıcı arabirimi öğesi) gibi bilgileri etkinliğin süresiyle birlikte bulabilirsiniz. Örneğin çizimde Bir Kılavuz denetimi **için Düzen** olayı 57,53 ms alır.

Daha fazla bilgi için [bkz. Uygulama Zaman Çizelgesi.](../profiling/application-timeline.md)

::: moniker range=">=vs-2019"

## <a name="examine-application-events"></a>Uygulama olaylarını inceleme

Genel olaylar [görüntüleyicisi,](../profiling/events-viewer.md) uygulamanın tam olarak Visual Studio profiler'da nasıl performans sergilemektedir olduğunu daha iyi tanılamanıza yardımcı olmak için modül yükü, iş parçacığı başlatma ve sistem yapılandırmaları gibi olayların bir listesi aracılığıyla uygulama etkinliğini görüntülemenize olanak sağlar. Bu araç, Performans Profili Oluşturucu. Hata ayıkla Performans Profili Oluşturucu **(veya**  >  Alt + **F2)****Performans Profili Oluşturucu** seçerek dosyayı açın.

Araç, her olayı bir liste görünümünde gösterir. Sütunlar olay adı, zaman damgası ve işlem kimliği gibi her olay hakkında bilgi sağlar.

![Olay Görüntüleyicisi İzleme](../profiling/media/eventviewertrace.png "Olay Görüntüleyicisi İzleme")

## <a name="analyze-asynchronous-code-net"></a>Zaman uyumsuz kodu analiz etme (.NET)

.NET Async [aracı,](../profiling/analyze-async.md) uygulamanıza zaman uyumsuz kodun performansını analiz etmenize olanak sağlar. Bu araç, Performans Profili Oluşturucu. Hata ayıkla Performans Profili Oluşturucu **(veya**  >  Alt + **F2)****Performans Profili Oluşturucu** seçerek dosyayı açın.

Araç, zaman uyumsuz her işlemi bir liste görünümünde gösterir. Zaman uyumsuz bir işlem için başlangıç saati, bitiş saati ve toplam süre gibi bilgileri görebilir.

![.NET Async Araç Durduruldu](../profiling/media/async-tool-opened.png ".NET Async Araç Durduruldu")

## <a name="analyze-database-performance-net-core"></a>Veritabanı performansını analiz etme (.NET Core)

Veritabanı aracı, ADO.NET veya Entity Framework Core kullanan .NET Core [](../profiling/analyze-database.md) uygulamaları için, tanılama oturumu sırasında uygulamanıza yapılan veritabanı sorgularını kaydetmenize olanak sağlar. Daha sonra, tek tek sorgularla ilgili bilgileri analiz edip uygulama performansınızı geliştirebilirsiniz. Bu araç, Performans Profili Oluşturucu. Hata ayıkla Performans Profili Oluşturucu **(veya**  >  Alt + **F2)****Performans Profili Oluşturucu** seçerek dosyayı açın.

Araç, her sorguyu bir liste görünümünde gösterir. Sorgu başlangıç zamanı ve süresi gibi bilgileri görebilir.

![Ayırma](./media/db-gotosource.png "Ayırma")

## <a name="visualize-net-counters-net-core"></a>.NET sayaçlarını görselleştirme (.NET Core)

2019 Visual Studio 16.7 sürümünden başlayarak, performans sayaçlarını görselleştirmek için [.NET](../profiling/dotnet-counters-tool.md) Sayaçları Visual Studio aracını kullanabilirsiniz. dotnet sayaçları kullanılarak oluşturulan [sayaçları görselleştirin.](/dotnet/core/diagnostics/dotnet-counters) dotnet sayaçları CPU kullanımı ve atık toplayıcı yığın boyutu gibi birçok sayacı destekler.

Araç, bir liste görünümünde her sayacın canlı değerlerini gösterir.

:::image type="content" source="../profiling/media/dotnet-counters-tool-collecting.png" alt-text=".NET Sayaç aracı toplama.":::

::: moniker-end

## <a name="examine-ui-performance-and-accessibility-events-uwp"></a>UI performans ve erişilebilirlik olaylarını inceleme (UWP)

UWP uygulamalarınız için kullanıcı arabirimi **analizini** **Tanılama Araçları.** Araç, yaygın performans veya erişilebilirlik sorunlarını arar ve hata **ayıklarken** bunları Olaylar görünümünde görüntüler. Olay açıklamaları sorunları çözmenize yardımcı olacak bilgiler sağlar.

![Tanılama araçlarında kullanıcı arabirimi analizi olaylarını görüntüleme](../profiling/media/prof-tour-ui-analysis.png "Tanılama Araçları Ui Çözümleme Olaylarını Görüntüleme")

## <a name="analyze-gpu-usage-direct3d"></a>GPU Kullanımını Analiz Etme (Direct3D)

Direct3D uygulamaları içinde (Direct3D bileşenleri C++ içinde olmalı), GPU'daki etkinliği inceler ve performans sorunlarını analiz edersiniz. Daha fazla bilgi için bkz. [GPU Kullanımı.](./gpu-usage.md) Aracı kullanmak için, grafikte **GPU Kullanımı'nı** Performans Profili Oluşturucu başlat'ı **seçin.** Uygulamanıza profil oluşturmak istediğiniz senaryoyu takip edin ve ardından Koleksiyonu **durdur'a** seçerek bir rapor oluşturabilirsiniz.

Grafiklerde bir zaman dönemi ve görünüm ayrıntılarını seçtiğiniz **zaman** alt bölmede ayrıntılı bir görünüm görünür. Ayrıntılı görünümde, her CPU ve GPU üzerinde ne kadar etkinlik olduğunu incelersiniz. Zaman çizelgesinde açılan pencereleri almak için en düşük bölmede olayları seçin. Örneğin, Çağrı açılır **pencerelerini** sun'ı **görüntülemek için Olayı** sun'ı seçin. (Açık gri dikey VSync satırları, belirli Mevcut çağrıların VSync'i kaçırıp kaçırmamalarını anlamak **için** başvuru olarak kullanılabilir. Uygulamanın kararlı **bir şekilde** 60 KARE/sn'ye isabet etmek için her iki VSync arasında bir Mevcut çağrısı olmalıdır.)

![GPU Kullanımı profil oluşturma aracı](../profiling/media/prof-tour-gpu-usage.png "GPU Kullanımını Tanılama")

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

UWP uygulamaları içinde, API kullanılarak gerçekleştirilen ağ işlemlerini analiz `Windows.Web.Http` edersiniz. Bu araç, erişim ve kimlik doğrulama sorunları, yanlış önbellek kullanımı, düşük görüntü ve indirme performansı gibi sorunları çözmenize yardımcı olabilir. Aracı kullanmak için ağ iletişim **kutusu'Performans Profili Oluşturucu** ve ardından Başlat'ı **seçin.** Uygulamanıza, kullanan senaryoyu gidin ve ardından `Windows.Web.Http` Raporu oluşturmak için Koleksiyonu **durdur'a** seçin.

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