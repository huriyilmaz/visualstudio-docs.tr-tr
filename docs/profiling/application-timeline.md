---
title: XAML uygulamalarında kaynak tüketimini analiz edin
ms.custom: seodec18
ms.date: 11/01/2018
ms.topic: conceptual
ms.assetid: df7d854b-0a28-45a9-8a64-c015a4327701
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- uwp
ms.openlocfilehash: a368a9b8f6d25753993a2cc10ea9ca94734d6709
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "71128284"
---
# <a name="analyze-resource-consumption-and-ui-thread-activity-xaml"></a>Kaynak tüketimini ve UI iş parçacığı etkinliğini (XAML) analiz edin

XAML uygulamalarında uygulama etkileşimi ile ilgili performans sorunlarını bulmak ve düzeltmek için **Uygulama Zaman Çizelgesi** profiloluşturcını kullanın. Bu araç, uygulamaların kaynak tüketiminin ayrıntılı bir görünümünü göstererek XAML uygulama performansını artırmaya yardımcı olur. Uygulamanızın Kullanıcı Arabirimi çerçeveleri (düzen ve işleme), servis ağı ve disk istekleri ni hazırlamave Uygulama Başlatma, Sayfa Yükleme ve Windows yeniden boyutlandırma gibi senaryolarda harcadığı zamanı çözümleyebilirsiniz.

**Uygulama Zaman Çizelgesi** **Hata Ayıklama** > **Performans Profilleyici** komutu ile başlatabileceğiniz araçlardan biridir.

Bu araç, Visual Studio 2013 tanı aracının bir parçası olan **XAML UI Responsiveness** aracının yerini alır.

Bu aracı aşağıdaki platformlarda kullanabilirsiniz:

- Evrensel Windows uygulamaları (Windows 10'da)
- Windows 8.1
- Windows Sunum Vakfı (.Net 4.0 ve üzeri)
- Windows 7

> [!NOTE]
> **ApplicationTimeline** verileriyle birlikte CPU kullanım verilerini ve enerji tüketim verilerini toplayabilir ve analiz edebilirsiniz. Bkz. [Hata ayıklayıcılı veya hata ayıklayıcısız profil oluşturma araçlarını çalıştırın.](../profiling/running-profiling-tools-with-or-without-the-debugger.md)

## <a name="collect-application-timeline-data"></a>Uygulama zaman çizelgesi verilerini toplama

Uygulamanızın yanıt verme yeteneğini yerel makinenizde, bağlı cihazınızda, Visual Studio simülatörünüzde veya emülatörlerinde veya uzak bir cihazda profilleyebilirsiniz. Bkz. [Hata ayıklayıcılı veya hata ayıklayıcısız profil oluşturma araçlarını çalıştırın.](../profiling/running-profiling-tools-with-or-without-the-debugger.md)

> [!TIP]
> Mümkünse uygulamayı doğrudan cihazda çalıştırın. Simülatörde veya uzak bir masaüstü bağlantısı nda gözlenen uygulama performansı, aygıttaki gerçek performansla aynı olmayabilir. Öte yandan, Visual Studio Remote Tools'u kullanarak veri toplamak performans verilerini etkilemez.

Temel adımlar şunlardır:

1. XAML uygulamanızı açın.

2. **Hata Ayıklama / Performans Profiloluştur'u**tıklatın. .diagsession penceresinde profil oluşturma araçlarının listesini görmeniz gerekir.

3. **Uygulama Zaman Çizelgesi'ni** seçin ve ardından pencerenin altındaki **Başlat'ı** tıklatın.

   > [!NOTE]
   > *VsEtwCollector.exe'yi*çalıştırmak için izninizi isteyen bir Kullanıcı Hesabı Denetimi penceresi görebilirsiniz. **Evet'i**tıklatın.

4. Performans verileri toplamak için uygulamanızda profil oluşturmayla ilgilendiğiniz senaryoyu çalıştırın.

5. Profil oluşturmayı durdurmak için .diagsession penceresine geri dön ve pencerenin üst kısmında **Dur'u** tıklatın.

   Visual Studio toplanan verileri analiz eder ve sonuçları görüntüler.

   ![Zaman çizelgesi profilleyici raporu](../profiling/media/timeline_base.png "TIMELINE_Base")

## <a name="analyze-timeline-profiling-data"></a>Zaman çizelgesi profil oluşturma verilerini analiz etme

Profil oluşturma verilerini topladıktan sonra analizinizi başlatmak için aşağıdaki adımları kullanabilirsiniz:

1. **Kullanıcı Arabirimi iş parçacığı kullanımı** ve Görsel iş gücü **(FPS)** grafiklerinde bilgileri görüntüleyin ve ardından çözümlemek istediğiniz bir zaman aralığı seçmek için zaman çizelgesi gezinti çubuklarını kullanın.

2. **Kullanıcı Arabirimi iş parçacığı kullanımı** veya Görsel iş parçacığı **(FPS)** grafiklerinde yer alan bilgileri kullanarak, yanıt verme eksikliğinin olası nedenlerini bulmak için **Zaman Çizelgesi ayrıntıları** görünümündeki ayrıntıları inceleyin.

### <a name="report-scenarios-categories-and-events"></a><a name="BKMK_Report_scenarios_categories_and_events"></a>Senaryoları, kategorileri ve olayları bildirme

**Uygulama Zaman Çizelgesi** aracı, XAML performansıyla ilgili senaryolar, kategoriler ve olaylar için zamanlama verilerini görüntüler.

### <a name="diagnostic-session-timeline"></a><a name="BKMK_Diagnostic_session_timeline"></a>Tanılama oturumu zaman çizelgesi

![Performans ve Tanılama zaman çizelgesi](../profiling/media/diaghub_timelinewithusermarks.png "DIAGHUB_TimelineWithUserMarks")

Sayfanın üst kısmındaki cetvel, profilli bilgilerin zaman çizelgesini gösterir. Bu zaman çizelgesi hem **UI iş parçacığı kullanım** grafiği hem de Görsel iş parçacığı **grafiği** için geçerlidir. Zaman çizelgesinin bir bölümü seçmek için, zaman çizelgesindeki gezinti çubuklarını sürükleyerek raporun kapsamını daraltabilirsiniz.

Zaman çizelgesi, eklediğiniz kullanıcı işaretlerini ve uygulamanın etkinleştirme yaşam döngüsü etkinliklerini de görüntüler.

### <a name="ui-thread-utilization-graph"></a><a name="BKMK_UI_thread_utilization_graph"></a>UI iş parçacığı kullanım grafiği

![CPU Kullanım Grafiği](../profiling/media/timeline_cpuutilization.png "TIMELINE_CpuUtilization")

**UI iş parçacığı kullanımı (%)** grafiği, bir toplama aralığı sırasında bir kategoride harcanan zaman miktarını gösteren bir çubuk grafiğidir.

### <a name="visual-throughput-fps-graph"></a><a name="BKMK_Visual_throughput_FPS_graph"></a>Görsel iş artışı (FPS) grafiği

![Görsel iş elde grafiği](../profiling/media/timeline_visualthroughput.png "TIMELINE_VisualThroughput")

**Visual throughput (FPS)** çizgi grafiği, ui'deki saniye karelerini (FPS) ve uygulamanın kompozisyon iş parçacığını gösterir.

### <a name="timeline-details"></a><a name="BKMK_Timeline_details_"></a>Zaman çizelgesi ayrıntıları

Ayrıntılar görünümü, zamanınızın çoğunu raporu analiz ederek harcadığınız yerdir. Kullanıcı-ı Oi Framework alt sistemi veya CPU'yu tüketen sistem bileşeni tarafından kategorize edilen uygulamanızın CPU kullanımını gösterir.

Aşağıdaki olaylar desteklenir:

|||
|-|-|
|**Ayrıştı -rma**|XAML dosyalarını ayrıştarak ve nesneleri oluşturmak için harcanan zaman.<br /><br /> **Zaman Çizelgesi ayrıntılarındaki** **Ayrıştırma** düğümünü genişletmek, kök olayı nedeniyle ayrıştırılan tüm XAML dosyalarının bağımlılık zincirini görüntüler. Bu ipucu, performansa duyarlı senaryolarda gereksiz dosya ayrıştırma ve nesne oluşturma belirlemenizi ve bunları en iyi duruma getirmenizi sağlar.|
|**Düzen**|Büyük uygulamalarda, binlerce öğe aynı anda ekranda gösterilebilir. Bu ekran, düşük kullanıcı bir Kullanıcı-ı Oi kare hızına ve buna bağlı olarak kötü uygulama yanıt verme oranına neden olabilir. Düzen olayı, her öğeyi (yani Düzenleme, Ölçü, ApplyTemplate, ArrangeOverride ve MeasureOverride'da harcanan süre) düzenlemenin maliyetini doğru bir şekilde belirler. Ayrıca, Düzen geçişinde yer alan görsel ağaçları da oluşturur. Bu görselleştirmeyi, hangi mantıksal ağaçları budamak için belirleyebileceğinizi belirlemek veya düzen geçişinizi optimize etmek için diğer erteleme mekanizmalarını değerlendirmek için kullanabilirsiniz.|
|**İşleme**|XAML öğelerini ekrana çizmek için harcanan süre.|
|**I/0**|Yerel diskten veya [Microsoft Windows Internet (WinINet) API'si](/windows/desktop/WinInet/portal)aracılığıyla erişilen ağ kaynaklarından veri almak için harcanan zaman.|
|**Uygulama Kodu**|Ayrıştırma veya düzenle ilgili olmayan uygulama (kullanıcı) kodunu yürütmek için harcanan süre.|
|**Xaml Diğer**|XAML çalışma zamanı kodunu yürütmek için harcanan süre.|

> [!TIP]
> Kullanıcı Arabirimi iş parçacığında çalıştırılabilen uygulama yöntemlerini görüntülemek için profil oluşturmayı **başlattığınızda, Uygulama Zaman Çizelgesi** aracıyla birlikte CPU **Kullanımı** aracını seçin. Uzun süredir çalışan uygulama kodunu arka plan iş parçacığına taşımak UI yanıt verme yeteneğini artırabilir.

#### <a name="customizing-timeline-details"></a><a name="BKMK_Customizing_Timeline_details_"></a>Zaman Çizelgesi ayrıntılarını özelleştirme

Zaman **Çizelgesi** **ayrıntıları** görüntüleme girişlerini sıralamak, filtrelemek ve belirtmeleri için Zaman Çizelgesi ayrıntıları araç çubuğunu kullanın.

|||
|-|-|
|**Göre Sırala**|Başlangıç saatine veya olayların uzunluğuna göre sıralayın.|
|![Olayları çerçeveye göre gruplandırma](../profiling/media/timeline_groupbyframes.png "TIMELINE_GroupByFrames")|Olayları çerçeveye göre gruplayan üst düzey bir **Çerçeve** kategorisi ekler veya kaldırır.|
|![Filtre zaman çizelgesi ayrıntıları listesi](../profiling/media/timeline_filter.png "TIMELINE_Filter")|Listeyi seçili kategorilere ve olayların uzunluğuna göre filtreler.|
|![Zaman çizelgesi ayrıntılarını özelleştir](../profiling/media/timeline_viewsettings.png "TIMELINE_ViewSettings")|Olaylara ek açıklamaları belirtmenizi sağlar.|

## <a name="see-also"></a>Ayrıca bkz.

- [WPF takım günlüğü: WPF uygulamaları için yeni kullanıcı arabirimi performans analizi aracı](https://blogs.msdn.microsoft.com/wpf/2015/01/16/new-ui-performance-analysis-tool-for-wpf-applications/)
- [C++, C#ve Visual Basic kullanarak UWP uygulamaları için en iyi performans uygulamaları](/previous-versions/windows/apps/hh750313\(v\=win.10\))
- [WPF uygulama performansını optimize edin](/dotnet/framework/wpf/advanced/optimizing-wpf-application-performance)
- [Visual Studio'da Profil Oluşturma](../profiling/index.yml)
- [Profil oluşturma araçlarına ilk bakış](../profiling/profiling-feature-tour.md)
