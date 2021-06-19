---
title: XAML uygulamalarına kaynak tüketimini analiz etme
description: XAML Uygulama Zaman Çizelgesi sorunlarını bulmak için Uygulama Zaman Çizelgesi profilleyiciyi kullanın. Çeşitli senaryolarda çeşitli görevler için harcanan zamanı analiz edersiniz.
ms.custom: SEO-VS-2020
ms.date: 11/01/2018
ms.topic: conceptual
ms.assetid: df7d854b-0a28-45a9-8a64-c015a4327701
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- uwp
ms.openlocfilehash: d352c118bd8b21b9dcbf62f7dd32eaf2999ed471
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112388028"
---
# <a name="analyze-resource-consumption-and-ui-thread-activity-xaml"></a>Kaynak tüketimini ve kullanıcı arabirimi iş parçacığı etkinliğini analiz etme (XAML)

XAML **Uygulama Zaman Çizelgesi** uygulama etkileşimiyle ilgili performans sorunlarını bulmak ve düzeltmek için Uygulama Zaman Çizelgesi profilleyiciyi kullanın. Bu araç, uygulamaların kaynak tüketiminin ayrıntılı bir görünümünü göstererek XAML uygulama performansının iyileştirilmesine yardımcı olur. Kullanıcı arabirimi çerçeveleri (düzen ve işleme), ağ ve disk isteklerine hizmet verme ve Uygulama Başlatma, Sayfa Yükleme ve Windows yeniden boyutlandırma gibi senaryolarda, uygulamanıza harcanan zamanı analiz edebilirsiniz.

**Uygulama Zaman Çizelgesi,** Hata Ayıkla komutuyla başlatabilirsiniz   >  **araçlardan Performans Profili Oluşturucu** olur.

Bu araç, kullanıcı arabirimi için tanılama araç takımına bir parçası olan **XAML** UI Yanıt Hızı aracının Visual Studio 2013.

Bu aracı aşağıdaki platformlarda kullanabilirsiniz:

- Evrensel Windows uygulamaları (Windows 10)
- Windows 8.1
- Windows Presentation Foundation (.Net 4.0 ve üzeri)
- Windows 7

> [!NOTE]
> **ApplicationTimeline** verileriyle birlikte CPU kullanım verilerini ve enerji tüketimi verilerini toplayıp analiz edin. Bkz. [Hata ayıklayıcı ile veya hata ayıklayıcı olmadan profil oluşturma araçlarını çalıştırma.](../profiling/running-profiling-tools-with-or-without-the-debugger.md)

## <a name="collect-application-timeline-data"></a>Uygulama zaman çizelgesi verilerini toplama

Yerel makineniz, bağlı cihaz, sanal simülatör veya öykünücüler Visual Studio uzak bir cihazda uygulamanın yanıt verme hızının profilini oluşturun. Bkz. [Hata ayıklayıcı ile veya hata ayıklayıcı olmadan profil oluşturma araçlarını çalıştırma.](../profiling/running-profiling-tools-with-or-without-the-debugger.md)

> [!TIP]
> Mümkünse uygulamayı doğrudan cihazda çalıştırın. Simülatörde veya uzak masaüstü bağlantısı üzerinden gözlemlenen uygulama performansı, cihaz gerçek performansıyla aynı olmayacaktır. Öte yandan, Uzak Araçlar'ın Visual Studio verileri toplamak performans verilerini etkilemez.

Temel adımlar şunlardır:

1. XAML uygulamanızı açın.

2. Hata **ayıkla / Performans Profili Oluşturucu.** .diagsession penceresinde profil oluşturma araçlarının listesini görüyor gerekir.

3. İlk **Uygulama Zaman Çizelgesi'ı** seçin **ve ardından pencerenin** alt kısmında Başlat'a tıklayın.

   ![Uygulama Zaman Çizelgesi Aracı Seçildi](../profiling/media/apptimelineselect.png "Uygulama Zaman Çizelgesi Aracı")

   > [!NOTE]
   > bir kullanıcı hesabı denetimi çalıştırmak için izninizi istenen bir Kullanıcı Hesabı Denetimi *VsEtwCollector.exe.* **Evet**'e tıklayın.

4. Performans verilerini toplamak için uygulamanıza profil oluşturmayla ilgilendiğiniz senaryoyu çalıştırın.

5. Profil oluşturmayı durdurmak için .diagsession penceresine geri dönüp pencerenin üst **kısmında** Durdur'a tıklayın.

   Visual Studio toplanan verileri analiz eder ve sonuçları görüntüler.

   ![Zaman çizelgesi profil oluşturma raporu](../profiling/media/timeline_base.png "TIMELINE_Base")

## <a name="analyze-timeline-profiling-data"></a>Zaman çizelgesi profil oluşturma verilerini analiz etme

Profil oluşturma verilerini topladıktan sonra analizinizi başlatmak için aşağıdaki adımları kullanabilirsiniz:

1. Kullanıcı arabirimi iş parçacığı **kullanımı ve** Görsel aktarım hızı **(DLL)** graflarında bilgileri görüntüleyin ve ardından zaman çizelgesi gezinti çubuklarını kullanarak analiz etmek istediğiniz zaman aralığını seçin.

2. Kullanıcı arabirimi iş parçacığı **kullanımı veya** Görsel aktarım hızı **(DLL)**  grafiklerdeki bilgileri kullanarak, yanıt verme hızının eksik olduğu durumların olası nedenlerini bulmak için Zaman Çizelgesi ayrıntıları görünümündeki ayrıntıları inceler.

### <a name="report-scenarios-categories-and-events"></a><a name="BKMK_Report_scenarios_categories_and_events"></a> Rapor senaryoları, kategorileri ve olayları

Bu **Uygulama Zaman Çizelgesi,** XAML performansıyla ilgili senaryolar, kategoriler ve olaylar için zamanlama verilerini görüntüler.

### <a name="diagnostic-session-timeline"></a><a name="BKMK_Diagnostic_session_timeline"></a> Tanılama oturumu zaman çizelgesi

![Performans ve Tanılama zaman çizelgesi](../profiling/media/diaghub_timelinewithusermarks.png "DIAGHUB_TimelineWithUserMarks")

Sayfanın üst kısmında yer alan cetvel, profili oluşturulurken alınan bilgilerin zaman çizelgesini gösterir. Bu zaman çizelgesi hem kullanıcı arabirimi iş **parçacığı kullanım grafiği hem** de Görsel aktarım hızı grafiği **için** geçerlidir. Zaman çizelgesinin bir bölümü seçmek için, zaman çizelgesindeki gezinti çubuklarını sürükleyerek raporun kapsamını daraltabilirsiniz.

Zaman çizelgesi ayrıca, eklenen tüm kullanıcı işaretlerini ve uygulamanın etkinleştirme yaşam döngüsü olaylarını da görüntüler.

### <a name="ui-thread-utilization-graph"></a><a name="BKMK_UI_thread_utilization_graph"></a> UI iş parçacığı kullanım grafiği

![CPU Kullanım Grafiği](../profiling/media/timeline_cpuutilization.png "TIMELINE_CpuUtilization")

UI **iş parçacığı kullanımı (%)** grafiği, bir koleksiyon aralığı boyunca bir kategoriye harcanan göreli zaman miktarını gösteren bir çubuk grafiktir.

### <a name="visual-throughput-fps-graph"></a><a name="BKMK_Visual_throughput_FPS_graph"></a> Görsel aktarım hızı (GRAPH) grafiği

![Görsel aktarım hızı grafiği](../profiling/media/timeline_visualthroughput.png "TIMELINE_VisualThroughput")

Görsel **aktarım hızı (DLL)** çizgi grafiği, uygulamanın kullanıcı arabiriminde ve oluşturma iş parçacığında saniye başına kareleri (DLL) gösterir.

### <a name="timeline-details"></a><a name="BKMK_Timeline_details_"></a> Zaman çizelgesi ayrıntıları

Ayrıntılar görünümü, zaman harcamanın çoğunu raporu analiz etmek için harcadığınız yerdir. Ui Framework alt sistemine veya CPU'yu kullanan sistem bileşenine göre kategorilere ayrılmış, uygulamanıza göre CPU kullanımını gösterir.

Aşağıdaki olaylar de destekler:

|Ad|Açıklama|
|-|-|
|**Ayrıştı -rma**|XAML dosyalarını ayrıştırmaya ve nesne oluşturmaya harcanan zaman.<br /><br /> Zaman **Çizelgesi ayrıntılarında ayrıştırma** düğümünü **genişletmek,** kök olay nedeniyle ayrıştırıldı olan tüm XAML dosyalarının bağımlılık zincirini görüntüler. Bu ipucu, performansa duyarlı senaryolarda gereksiz dosya ayrıştırmayı ve nesne oluşturmayı tanımlamanıza ve bunları iyileştirmenizi sağlar.|
|**Düzen**|Büyük uygulamalarda, ekranda aynı anda binlerce öğe gösterebilirsiniz. Bu görüntü, düşük kullanıcı arabirimi kare hızına ve buna karşılık gelen uygulama yanıt hızının düşüklüğüne neden olabilir. Düzen olayı, her bir öğenin (Düzenleme, Ölçü, ApplyTemplate, ArrangeOverride ve MeasureOverride içinde harcanan süre) maliyetini doğru şekilde belirler. Ayrıca Bir Düzen geçişinin parçası olan görsel ağaçlarını da derleme. Bu görselleştirmeyi kullanarak hangi mantıksal ağaçları ayıklamanız veya düzen geçişini iyileştirmek için diğer erteleme mekanizmalarını değerlendirmeniz gerekir.|
|**İşleme**|XAML öğelerini ekrana çizmek için harcanan zaman.|
|**I/0**|Yerel diskten veya Microsoft Windows Internet [(WinINet) API'si](/windows/desktop/WinInet/portal)aracılığıyla erişilen ağ kaynaklarından veri almak için harcanan süre.|
|**Uygulama Kodu**|Ayrıştırma veya düzenle ilgili olmayan uygulama (kullanıcı) kodunu yürütmek için harcanan süre.|
|**Xaml Diğer**|XAML çalışma zamanı kodunu yürütmek için harcanan süre.|

> [!TIP]
> Kullanıcı arabirimi **iş parçacığında** yürütülen **uygulama yöntemlerini görüntülemek için** profil oluşturmayı Uygulama Zaman Çizelgesi CPU Kullanımı aracını ve kullanıcı arabirimi aracını seçin. Uzun süre çalışan uygulama kodunu bir arka plan iş parçacığına taşıma, kullanıcı arabirimi yanıt hızını geliştirebilir.

#### <a name="customizing-timeline-details"></a><a name="BKMK_Customizing_Timeline_details_"></a> Zaman Çizelgesi ayrıntılarını özelleştirme

Zaman Çizelgesi **ayrıntıları görünüm** girişlerinin ek açıklamalarını sıralamak, filtrelemek ve belirtmek için Zaman Çizelgesi **ayrıntıları araç** çubuğunu kullanın.

|Ad|Açıklama|
|-|-|
|**Sıralamaya göre**|Başlangıç saat veya olayların uzunluğuna göre sırala.|
|![Olayları kareye göre grupla](../profiling/media/timeline_groupbyframes.png "TIMELINE_GroupByFrames")|Olayları çerçeveye göre grupleyen üst **düzey bir** Çerçeve kategorisi ekler veya kaldırır.|
|![Zaman çizelgesi ayrıntıları listesini filtreleme](../profiling/media/timeline_filter.png "TIMELINE_Filter")|Listeyi seçilen kategorilere ve olayların uzunluğuna göre filtreler.|
|![Zaman çizelgesi ayrıntıları bilgilerini özelleştirme](../profiling/media/timeline_viewsettings.png "TIMELINE_ViewSettings")|Olaylara ek açıklamaları belirtmenize olanak sağlar.|

## <a name="see-also"></a>Ayrıca bkz.

- [WPF ekip blogu: WPF uygulamaları için yeni kullanıcı arabirimi performans analizi aracı](/archive/blogs/wpf/new-ui-performance-analysis-tool-for-wpf-applications)
- [C++, C# ve Visual Basic kullanarak UWP uygulamaları için performansa yönelik en iyi Visual Basic](/previous-versions/windows/apps/hh750313\(v\=win.10\))
- [WPF uygulama performansını iyileştirme](/dotnet/framework/wpf/advanced/optimizing-wpf-application-performance)
- [Visual Studio'da profil oluşturma](../profiling/index.yml)
- [Profil oluşturma araçlarına ilk bakış](../profiling/profiling-feature-tour.md)