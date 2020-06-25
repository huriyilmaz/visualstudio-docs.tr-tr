---
title: XAML uygulamalarında kaynak tüketimini analiz etme
ms.custom: seodec18
ms.date: 11/01/2018
ms.topic: conceptual
ms.assetid: df7d854b-0a28-45a9-8a64-c015a4327701
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- uwp
ms.openlocfilehash: 26da567918ea25f212c4c03e87e81d5cc18b60ab
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85285992"
---
# <a name="analyze-resource-consumption-and-ui-thread-activity-xaml"></a>Kaynak tüketimini ve UI iş parçacığı etkinliğini çözümleme (XAML)

XAML uygulamalarında uygulamayla ilgili etkileşime ilişkin performans sorunlarını bulmak ve gidermek için **uygulama zaman çizelgesi** Profiler 'ı kullanın. Bu araç, uygulamaların kaynak tüketiminin ayrıntılı bir görünümünü göstererek XAML uygulama performansının artırılmasına yardımcı olur. Uygulamanızın Kullanıcı arabirimi çerçevelerini hazırlama (düzen ve oluşturma), ağ ve disk isteklerine hizmet verme ve uygulama başlatma, sayfa yükleme ve Windows yeniden boyutlandırma gibi senaryolarda harcanan süreyi çözümleyebilirsiniz.

**Uygulama zaman çizelgesi** , **hata ayıklama**  >  **performansı profil oluşturucu** komutuyla başlayabilmeniz için kullanabileceğiniz araçlardan biridir.

Bu araç, Visual Studio 2013 için tanılama araç takımının parçası olan **XAML UI yanıt verme** aracının yerini alır.

Bu aracı aşağıdaki platformlarda kullanabilirsiniz:

- Evrensel Windows uygulamaları (Windows 10 ' da)
- Windows 8.1
- Windows Presentation Foundation (.NET 4,0 ve üzeri)
- Windows 7

> [!NOTE]
> **Uygulama zaman çizelgesi** VERILERIYLE birlikte CPU kullanım verilerini ve enerji tüketimi verilerini toplayıp analiz edebilirsiniz. Bkz. [hata ayıklayıcı ile veya olmayan profil oluşturma araçlarını çalıştırma](../profiling/running-profiling-tools-with-or-without-the-debugger.md).

## <a name="collect-application-timeline-data"></a>Uygulama zaman çizelgesi verilerini topla

Uygulamanızın yanıt verme hızını yerel makinenizde, bağlı cihazınızda, Visual Studio benzeticisinde veya Öykünücülerde veya uzak bir cihazda profilin profilini oluşturabilirsiniz. Bkz. [hata ayıklayıcı ile veya olmayan profil oluşturma araçlarını çalıştırma](../profiling/running-profiling-tools-with-or-without-the-debugger.md).

> [!TIP]
> Mümkünse uygulamayı doğrudan cihazda çalıştırın. Simülatör üzerinde veya uzak masaüstü bağlantısıyla gözlemlendiği uygulama performansı, cihazdaki gerçek performansla aynı olmayabilir. Öte yandan, Visual Studio uzak araçları kullanılarak verilerin toplanması performans verilerini etkilemez.

Temel adımlar şunlardır:

1. XAML uygulamanızı açın.

2. **Hata ayıklama/performans profil Oluşturucu ' ya**tıklayın. . Diagsession penceresinde profil oluşturma araçlarının bir listesini görmeniz gerekir.

3. **Uygulama zaman çizelgesi** öğesini seçin ve ardından pencerenin alt kısmındaki **Başlat** ' a tıklayın.

   ![Uygulama Zaman Çizelgesi araç seçildi](../profiling/media/apptimelineselect.png "Uygulama Zaman Çizelgesi Aracı")

   > [!NOTE]
   > *VsEtwCollector.exe*çalıştırmak için izninizi ısteyen bir kullanıcı hesabı denetim penceresi görebilirsiniz. **Evet**' e tıklayın.

4. Performans verilerini toplamak için uygulamanızdaki profil oluşturma konusunda ilgilendiğiniz senaryoyu çalıştırın.

5. Profil oluşturmayı durdurmak için,. diagsession penceresine dönün ve pencerenin en üstünde **Durdur** ' a tıklayın.

   Visual Studio toplanan verileri analiz eder ve sonuçları görüntüler.

   ![Zaman çizelgesi profil Oluşturucu raporu](../profiling/media/timeline_base.png "TIMELINE_Base")

## <a name="analyze-timeline-profiling-data"></a>Zaman çizelgesi profil oluşturma verilerini çözümle

Profil oluşturma verilerini topladıktan sonra analizinizi başlatmak için aşağıdaki adımları kullanabilirsiniz:

1. **UI iş parçacığı kullanımı** ve **görsel ÜRETILEN iş (fps)** grafiklerinde bilgileri görüntüleyin ve ardından zaman çizelgesi gezinti çubuklarını kullanarak çözümlemek istediğiniz zaman aralığını seçin.

2. **UI iş parçacığı kullanımı** veya **Görsel aktarım hızı (fps)** grafiklerde bulunan bilgileri kullanarak, yanıt verme için olası nedenleri öğrenmek için **zaman çizelgesi ayrıntıları** görünümündeki ayrıntıları inceleyin.

### <a name="report-scenarios-categories-and-events"></a><a name="BKMK_Report_scenarios_categories_and_events"></a>Rapor senaryoları, Kategoriler ve olaylar

**Uygulama zaman çizelgesi** Aracı, XAML performansıyla ilgili senaryolar, Kategoriler ve olaylar için zamanlama verilerini görüntüler.

### <a name="diagnostic-session-timeline"></a><a name="BKMK_Diagnostic_session_timeline"></a>Tanılama oturumu zaman çizelgesi

![Performans ve tanılama zaman çizelgesi](../profiling/media/diaghub_timelinewithusermarks.png "DIAGHUB_TimelineWithUserMarks")

Sayfanın üst kısmındaki cetvel profili oluşturulmuş bilgiler için zaman çizelgesini gösterir. Bu zaman çizelgesi hem **UI iş parçacığı kullanımı** grafiği hem de **görsel işleme** grafiği için geçerlidir. Zaman çizelgesinin bir bölümü seçmek için, zaman çizelgesindeki gezinti çubuklarını sürükleyerek raporun kapsamını daraltabilirsiniz.

Zaman çizelgesi, eklediğiniz tüm Kullanıcı işaretlerini ve uygulamanın etkinleştirme yaşam döngüsü olaylarını da görüntüler.

### <a name="ui-thread-utilization-graph"></a><a name="BKMK_UI_thread_utilization_graph"></a>UI iş parçacığı kullanım grafiği

![CPU Kullanım Grafiği](../profiling/media/timeline_cpuutilization.png "TIMELINE_CpuUtilization")

**Kullanıcı arabirimi iş parçacığı kullanımı (%)** Graph, bir koleksiyon yayılması sırasında bir kategoride harcanan sürenin göreli miktarını görüntüleyen bir çubuk grafiktir.

### <a name="visual-throughput-fps-graph"></a><a name="BKMK_Visual_throughput_FPS_graph"></a>Görsel üretilen iş (FPS) grafiği

![Görsel üretilen iş grafiği](../profiling/media/timeline_visualthroughput.png "TIMELINE_VisualThroughput")

**Görsel üretilen iş (fps)** çizgi grafiğinde, uygulama için Kullanıcı arabirimi ve bileşim iş parçacığında saniye başına çerçeve (fps) gösterilir.

### <a name="timeline-details"></a><a name="BKMK_Timeline_details_"></a>Zaman çizelgesi ayrıntıları

Ayrıntılar görünümü, raporu analiz ettiğiniz zamandan çok zaman harcamanızı ister. Uygulamanız tarafından Kullanıcı arabirimi çerçevesi alt sistemi veya CPU kullanan sistem bileşeni tarafından kategorilere ayrılan CPU kullanımını gösterir.

Aşağıdaki olaylar desteklenir:

|||
|-|-|
|**SDP**|XAML dosyalarını ayrıştırmak ve nesne oluşturmak için harcanan süre.<br /><br /> **Zaman çizelgesi ayrıntılarında** **ayrıştırma** düğümünü genişletme, kök olay nedeniyle ayrıştırılmış tüm XAML dosyalarının bağımlılık zincirini görüntüler. Bu ipucu, performans duyarlı senaryolarda gereksiz dosya ayrıştırmayı ve nesne oluşturmayı belirlemenize ve bunları en iyi hale getirmenize olanak tanır.|
|**Layout**|Büyük uygulamalarda, ekran üzerinde aynı anda binlerce öğe görüntülenebilir. Bu görüntü, düşük bir kullanıcı arabirimi kare hızına ve buna karşılık gelen kötü uygulama yanıt verme hızına yol açabilir. Düzen olayı her bir öğenin (yani, düzenleme, ölçü, ApplyTemplate, ArrangeOverride ve MeasureOverride) nasıl yerleştirmekte olan maliyeti doğru şekilde belirler. Ayrıca, düzen geçişinin parçası olan görsel ağaçlar da oluşturur. Bu görselleştirmeyi, hangi mantıksal ağaçların çıkartarken veya diğer erteleme mekanizmalarının düzen geçişini iyileştirmek için değerlendirmek için kullanabilirsiniz.|
|**İşleme**|Ekrana XAML öğeleri çizilirken geçen süre.|
|**G/0**|Yerel diskten veya [Microsoft Windows Internet (Winınet) API 'si](/windows/desktop/WinInet/portal)üzerinden erişilen ağ kaynaklarından veri alınırken harcanan süre.|
|**Uygulama kodu**|Ayrıştırma veya düzenleme ile ilgili olmayan uygulama (Kullanıcı) kodunu yürütmek için harcanan süre.|
|**Xaml diğer**|XAML çalışma zamanı kodunu yürütmek için harcanan süre.|

> [!TIP]
> Kullanıcı arabirimi iş parçacığında yürütülen uygulama yöntemlerini görüntülemek için profil oluşturmaya başladığınızda **uygulama zaman çizelgesi** aracı Ile birlikte **CPU kullanımı** aracını seçin. Uzun süre çalışan uygulama kodunun bir arka plan iş parçacığına taşınması, UI yanıt hızını iyileştirebilir.

#### <a name="customizing-timeline-details"></a><a name="BKMK_Customizing_Timeline_details_"></a>Zaman çizelgesi ayrıntılarını özelleştirme

**Zaman çizelgesi ayrıntıları** görünümü girişlerinin ek açıklamalarını sıralamak, filtrelemek ve belirtmek Için **zaman çizelgesi ayrıntıları** araç çubuğunu kullanın.

|||
|-|-|
|**Sıralama ölçütü**|Başlangıç zamanına veya olay uzunluğuna göre sıralayın.|
|![Olayları çerçeveye göre Gruplandır](../profiling/media/timeline_groupbyframes.png "TIMELINE_GroupByFrames")|Olayları çerçeveye göre gruplandıran üst düzey bir **çerçeve** kategorisini ekler veya kaldırır.|
|![Zaman çizelgesi ayrıntı listesini filtrele](../profiling/media/timeline_filter.png "TIMELINE_Filter")|Listenin seçili kategorilere ve olay uzunluğuna göre filtreleyeceğini.|
|![Zaman çizelgesi ayrıntıları bilgilerini Özelleştir](../profiling/media/timeline_viewsettings.png "TIMELINE_ViewSettings")|Olaylara ek açıklamaları belirtmenize izin verir.|

## <a name="see-also"></a>Ayrıca bkz.

- [WPF ekibi blogu: WPF uygulamaları için yeni UI performans Analizi Aracı](https://blogs.msdn.microsoft.com/wpf/2015/01/16/new-ui-performance-analysis-tool-for-wpf-applications/)
- [C++, C# ve Visual Basic kullanarak UWP uygulamaları için en iyi performans uygulamaları](/previous-versions/windows/apps/hh750313\(v\=win.10\))
- [WPF uygulama performansını iyileştirme](/dotnet/framework/wpf/advanced/optimizing-wpf-application-performance)
- [Visual Studio 'da profil oluşturma](../profiling/index.yml)
- [Profil oluşturma araçlarına ilk bakış](../profiling/profiling-feature-tour.md)
