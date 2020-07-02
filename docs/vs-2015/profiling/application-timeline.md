---
title: Uygulama Zaman Çizelgesi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: df7d854b-0a28-45a9-8a64-c015a4327701
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0f899e081377ecc1a56e141f8793d6f707df2b69
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85534088"
---
# <a name="application-timeline"></a>Uygulama Zaman Çizelgesi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

XAML uygulamalarında uygulamayla ilgili etkileşime ilişkin performans sorunlarını bulmak ve gidermek için **uygulama zaman çizelgesi** Profiler 'ı kullanın. Bu araç, uygulamaların kaynak tüketiminin ayrıntılı bir görünümünü sağlayarak XAML uygulamalarının performansının artırılmasına yardımcı olur. Uygulamanızın Kullanıcı arabirimi çerçevelerini hazırlama (düzen ve oluşturma), ağ ve disk isteklerine hizmet verme ve uygulama başlatma, sayfa yükleme ve Windows yeniden boyutlandırma gibi senaryolarda harcanan süreyi çözümleyebilirsiniz.  
  
 **Uygulama zaman çizelgesi** , **Debug/Performance Profiler...** komutuyla başlayabilmeniz için kullanabileceğiniz araçlardan biridir.  
  
 Bu araç, Visual Studio 2013 için tanılama araç takımının parçası olan **XAML UI yanıt verme** aracının yerini alır.  
  
 Bu aracı aşağıdaki platformlarda kullanabilirsiniz:  
  
1. Evrensel Windows uygulamaları (Windows 10 ' da)  
  
2. Windows Mağazası 8,1  
  
3. Windows Phone 8,1 (Genel XAML platformu)  
  
4. Windows Presentation Foundation (.NET 4,0 ve üzeri)  
  
5. Windows 7  
  
> [!NOTE]
> **Uygulama zaman çizelgesi** VERILERIYLE birlikte CPU kullanım verilerini ve enerji tüketimi verilerini toplayıp analiz edebilirsiniz. Bkz. [profil oluşturma araçlarını hata ayıklama olmadan çalıştırma](https://msdn.microsoft.com/library/e97ce1a4-62d6-4b8e-a2f7-61576437ff01)  
  
## <a name="collect-application-timeline-data"></a><a name="BKMK_Collect_Timeline_data_for_your_app"></a>Uygulama Zaman Çizelgesi verilerini topla  
 Uygulamanızın yanıt verme hızını yerel makinenizde, bağlı cihazınızda, Visual Studio benzeticisinde veya Öykünücülerde veya uzak bir cihazda profilin profilini oluşturabilirsiniz. Bkz. [profil oluşturma araçlarını hata ayıklama olmadan çalıştırma](https://msdn.microsoft.com/library/e97ce1a4-62d6-4b8e-a2f7-61576437ff01).  
  
> [!TIP]
> Mümkünse uygulamayı doğrudan cihazda çalıştırın. Simülatör üzerinde veya uzak masaüstü bağlantısıyla gözlemlendiği uygulama performansı, cihazdaki gerçek performansla aynı olmayabilir. Öte yandan, Visual Studio uzak araçları kullanılarak verilerin toplanması performans verilerini etkilemez.  
  
 Temel adımlar şunlardır:  
  
1. XAML uygulamanızı açın.  
  
2. **Hata ayıklama/performans profili Oluşturucu...** öğesine tıklayın. . Diagsession penceresinde profil oluşturma araçlarının bir listesini görmeniz gerekir.  
  
3. **Uygulama zaman çizelgesi** öğesini seçin ve ardından pencerenin alt kısmındaki **Başlat** ' a tıklayın.  
  
    > [!NOTE]
    > VsEtwCollector.exe çalıştırmak için izninizi isteyen bir kullanıcı hesabı denetim penceresi görebilirsiniz. **Evet**' e tıklayın.  
  
4. Performans verilerini toplamak için uygulamanızdaki profil oluşturma konusunda ilgilendiğiniz senaryoyu çalıştırın.  
  
5. Profil oluşturmayı durdurmak için,. diagsession penceresine dönün ve pencerenin en üstünde **Durdur** ' a tıklayın.  
  
     Visual Studio toplanan verileri analiz eder ve sonuçları görüntüler.  
  
     ![Zaman çizelgesi profil Oluşturucu raporu](../profiling/media/timeline-base.png "TIMELINE_Base")  
  
## <a name="analyze-timeline-profiling-data"></a><a name="BKMK_Analyze_Timeline_profiling_data"></a>Zaman çizelgesi profil oluşturma verilerini çözümle  
 Profil oluşturma verilerini topladıktan sonra analizinizi başlatmak için aşağıdaki adımları kullanabilirsiniz:  
  
1. **UI iş parçacığı kullanımı** ve **görsel ÜRETILEN iş (fps)** grafiklerde bulunan bilgileri inceleyin ve ardından zaman çizelgesi gezinti çubuklarını kullanarak analiz etmek istediğiniz zaman aralığını seçin.  
  
2. **UI iş parçacığı kullanımı** veya **Görsel aktarım hızı (fps)** grafiklerde bulunan bilgileri kullanarak, herhangi bir yanıt verme için olası nedenleri öğrenmek üzere **zaman çizelgesi ayrıntıları** görünümündeki ayrıntıları inceleyin.  
  
### <a name="report-scenarios-categories-and-events"></a><a name="BKMK_Report_scenarios_categories_and_events"></a>Rapor senaryoları, Kategoriler ve olaylar  
 **Uygulama zaman çizelgesi** Aracı, XAML performansıyla ilgili senaryolar, Kategoriler ve olaylar için zamanlama verilerini görüntüler.  
  
### <a name="diagnostic-session-timeline"></a><a name="BKMK_Diagnostic_session_timeline"></a>Tanılama oturumu zaman çizelgesi  
 ![Performans ve tanılama zaman çizelgesi](../profiling/media/diaghub-timelinewithusermarks.png "DIAGHUB_TimelineWithUserMarks")  
  
 Sayfanın üst kısmındaki cetvel profili oluşturulmuş bilgiler için zaman çizelgesini gösterir. Bu zaman çizelgesi hem **UI iş parçacığı kullanımı** grafiği hem de **görsel işleme** grafiği için geçerlidir. Zaman çizelgesinin bir bölümü seçmek için, zaman çizelgesindeki gezinti çubuklarını sürükleyerek raporun kapsamını daraltabilirsiniz.  
  
 Zaman çizelgesi ayrıca, eklediğiniz kullanıcı işaretlerini ve uygulamanın etkinleştirme yaşam döngüsü olaylarını da görüntüler.  
  
### <a name="ui-thread-utilization-graph"></a><a name="BKMK_UI_thread_utilization_graph"></a>UI iş parçacığı kullanım grafiği  
 ![CPU Kullanım Grafiği](../profiling/media/timeline-cpuutilization.png "TIMELINE_CpuUtilization")  
  
 **Kullanıcı arabirimi iş parçacığı kullanımı (%)** Graph, bir koleksiyon yayılması sırasında bir kategoride harcanan sürenin göreli miktarını görüntüleyen bir çubuk grafiktir.  
  
### <a name="visual-throughput-fps-graph"></a><a name="BKMK_Visual_throughput_FPS_graph"></a>Görsel üretilen iş (FPS) grafiği  
 ![Görsel üretilen iş grafiği](../profiling/media/timeline-visualthroughput.png "TIMELINE_VisualThroughput")  
  
 **Görsel üretilen iş (fps)** çizgi grafiğinde, uygulama için Kullanıcı arabirimi ve bileşim iş parçacığında saniye başına çerçeve (fps) gösterilir.  
  
### <a name="timeline-details"></a><a name="BKMK_Timeline_details_"></a>Zaman çizelgesi ayrıntıları  
 Ayrıntılar görünümü, raporu analiz ettiğiniz zamandan büyük bir süre içinde ücretlendirilecektir. Uygulamanızın Kullanıcı arabirimi çerçevesi alt sistemi veya CPU 'YU kullanan sistem bileşeni tarafından kategorilere ayrılması için ayrıntılı bir görünümünü gösterir.  
  
 Aşağıdaki olaylar desteklenir:  
  
|Name|Açıklama|  
|-|-|  
|**SDP**|XAML dosyalarını ayrıştırmak ve nesne oluşturmak için harcanan süre.<br /><br /> **Zaman çizelgesi ayrıntılarında** **ayrıştırma** düğümünün genişletilmesi, kök olayın sonucu olarak ayrıştırılmış tüm XAML dosyalarının bağımlılık zincirini görüntüler. Bu, performans duyarlı senaryolarda gereksiz dosya ayrıştırmayı ve nesne oluşturmayı tanımlamanızı ve bunları en iyi hale getirmenize olanak tanır.|  
|**Layout**|Büyük uygulamalarda, ekran üzerinde aynı anda binlerce öğe görüntülenebilir. Bu, düşük bir kullanıcı arabirimi kare hızına ve buna karşılık gelen kötü uygulama yanıt verme hızına yol açabilir. Düzen olayı her bir öğenin (örneğin, düzenleme, ölçü, ApplyTemplate, ArrangeOverride ve ArrangeOverride) nasıl düzenlenmesinin maliyetini doğru şekilde belirler ve bir düzen geçişinde bir bölümü alan görsel ağaçları oluşturur. Bu görselleştirmeyi, mantıksal Ağaçlarınızdan hangilerinin ayıklanmayı gerektiğini tespit etmek veya Düzen geçişinizi iyileştirmek için diğer erteleme mekanizmalarını değerlendirmek için kullanabilirsiniz.|  
|**İşleme**|Ekrana XAML öğeleri çizilirken geçen süre.|  
|**G/0**|Yerel diskten veya [Microsoft Windows Internet (Winınet) API 'si](https://msdn.microsoft.com/library/windows/desktop/aa385331.aspx)üzerinden erişilen ağ kaynaklarından veri alınırken harcanan süre.|  
|**Uygulama kodu**|Ayrıştırma veya düzenleme ile ilgili olmayan uygulama (Kullanıcı) kodunu yürütmek için harcanan süre.|  
|**Xaml diğer**|XAML çalışma zamanı kodunu yürütmek için harcanan süre.|  
  
> [!TIP]
> Kullanıcı arabirimi iş parçacığında yürütülen uygulama yöntemlerini görüntülemek için profil oluşturmaya başladığınızda **uygulama zaman çizelgesi** aracı Ile birlikte **CPU kullanımı** aracını seçin. Uzun süre çalışan uygulama kodunun bir arka plan iş parçacığına taşınması, UI yanıt hızını iyileştirebilir.  
  
#### <a name="customizing-timeline-details"></a><a name="BKMK_Customizing_Timeline_details_"></a>Zaman çizelgesi ayrıntılarını özelleştirme  
 **Zaman çizelgesi ayrıntıları** görünümü girişlerinin ek açıklamalarını sıralamak, filtrelemek ve belirtmek Için **zaman çizelgesi ayrıntıları** araç çubuğunu kullanın.  
  
|Name|Açıklama|  
|-|-|  
|**Sıralama ölçütü**|Başlangıç zamanına veya olay uzunluğuna göre sıralayın.|  
|![Olayları çerçeveye göre Gruplandır](../profiling/media/timeline-groupbyframes.png "TIMELINE_GroupByFrames")|Olayları çerçeveye göre gruplandıran üst düzey bir **çerçeve** kategorisini ekler veya kaldırır.|  
|![Zaman çizelgesi ayrıntı listesini filtrele](../profiling/media/timeline-filter.png "TIMELINE_Filter")|Listenin seçili kategorilere ve olay uzunluğuna göre filtreleyeceğini.|  
|![Zaman çizelgesi ayrıntıları bilgilerini Özelleştir](../profiling/media/timeline-viewsettings.png "TIMELINE_ViewSettings")|Olaylara ek açıklamaları belirtmenize izin verir.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WPF ekibi blogu: WPF uygulamaları için yeni UI performans Analizi Aracı](https://devblogs.microsoft.com/wpf/new-ui-performance-analysis-tool-for-wpf-applications/)   
 [C++, C# ve Visual Basic kullanarak Windows Mağazası uygulamaları için en iyi performans uygulamaları](https://msdn.microsoft.com/567bcefa-5da5-4e42-a4b8-1358c71adfa2)   
 [WPF Uygulama Performansını İyileştirme](https://msdn.microsoft.com/library/ac8c6aa3-3c68-4a24-9827-3b6c829c1ebf)
