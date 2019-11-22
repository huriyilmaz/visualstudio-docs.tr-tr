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
ms.openlocfilehash: 63673dd42987154d69346505c8e1f80b3b4789e8
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74297745"
---
# <a name="application-timeline"></a>Uygulama Zaman Çizelgesi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kullanım **uygulama zaman çizelgesi** ilgili XAML uygulamalarında performans sorunlarını bulup düzeltme uygulama etkileşimi profil oluşturucu. Bu araç, uygulamaların kaynak tüketiminin ayrıntılı bir görünümünü sağlayarak XAML uygulamalarının performansının artırılmasına yardımcı olur. Uygulamanızın Kullanıcı arabirimi çerçevelerini hazırlama (düzen ve oluşturma), ağ ve disk isteklerine hizmet verme ve uygulama başlatma, sayfa yükleme ve Windows yeniden boyutlandırma gibi senaryolarda harcanan süreyi çözümleyebilirsiniz.  
  
 **Uygulama zaman çizelgesi** , **Debug/Performance Profiler...** komutuyla başlayabilmeniz için kullanabileceğiniz araçlardan biridir.  
  
 Bu aracının yerini alır **XAML UI yanıtlama hızı** tanılama araç takımı Visual Studio 2013'ün bir parçası olan aracı.  
  
 Aşağıdaki platformlarda bu aracı kullanabilirsiniz:  
  
1. Evrensel Windows uygulamaları (üzerinde Windows 10)  
  
2. Windows Mağazası 8,1  
  
3. Windows Phone 8,1 (Genel XAML platformu)  
  
4. Windows Presentation Foundation (.Net 4.0 ve üzeri)  
  
5. Windows 7  
  
> [!NOTE]
> Toplama ve CPU kullanım verileri ve enerji tüketimi verilerini ile birlikte analiz **ApplicationTimeline** veri. Bkz. [profil oluşturma araçlarını hata ayıklama olmadan çalıştırma](https://msdn.microsoft.com/library/e97ce1a4-62d6-4b8e-a2f7-61576437ff01)  
  
## <a name="BKMK_Collect_Timeline_data_for_your_app"></a>Uygulama Zaman Çizelgesi verilerini topla  
 Yerel makinenize, bağlı cihaz, Visual Studio simulatorunda veya öykünücüleri veya uzak cihaz üzerinde uygulamanızın yanıt verme hızı profilini oluşturabilirsiniz. Bkz. [profil oluşturma araçlarını hata ayıklama olmadan çalıştırma](https://msdn.microsoft.com/library/e97ce1a4-62d6-4b8e-a2f7-61576437ff01).  
  
> [!TIP]
> Mümkünse, uygulamayı doğrudan cihazda çalıştırın. Uygulama performansı gözlenen veya bir Uzak Masaüstü Bağlantısı cihazdaki gerçek performansın aynı olmayabilir. Öte yandan, Visual Studio uzak araçları kullanılarak verilerin toplanması performans verilerini etkilemez.  
  
 Temel adımlar şunlardır:  
  
1. XAML uygulamanızı açın.  
  
2. **Hata ayıklama/performans profili Oluşturucu...** öğesine tıklayın. . Diagsession penceresinde profil oluşturma araçlarının bir listesini görmeniz gerekir.  
  
3. Seçin **uygulama zaman çizelgesi** ve ardından **Başlat** pencerenin alt kısmındaki.  
  
    > [!NOTE]
    > VsEtwCollector. exe ' yi çalıştırmak için izninizi isteyen bir kullanıcı hesabı denetim penceresi görebilirsiniz. **Evet**'i tıklayın.  
  
4. Uygulamanızda performans verilerini toplamak için profil oluşturma ilgilendiğiniz senaryonun çalıştırın.  
  
5. Profil oluşturmayı durdurmak için .diagsession penceresine geçin ve **Durdur** pencerenin üst kısmındaki.  
  
     Visual Studio toplanan verileri analiz eder ve sonuçları görüntüler.  
  
     ![Zaman çizelgesi profil Oluşturucu raporu](../profiling/media/timeline-base.png "TIMELINE_Base")  
  
## <a name="BKMK_Analyze_Timeline_profiling_data"></a>Zaman çizelgesi profil oluşturma verilerini çözümle  
 Profil oluşturma verilerini topladıktan sonra analizinizi başlatmak için aşağıdaki adımları kullanabilirsiniz:  
  
1. **UI iş parçacığı kullanımı** ve **görsel ÜRETILEN iş (fps)** grafiklerde bulunan bilgileri inceleyin ve ardından zaman çizelgesi gezinti çubuklarını kullanarak analiz etmek istediğiniz zaman aralığını seçin.  
  
2. **UI iş parçacığı kullanımı** veya **Görsel aktarım hızı (fps)** grafiklerde bulunan bilgileri kullanarak, herhangi bir yanıt verme için olası nedenleri öğrenmek üzere **zaman çizelgesi ayrıntıları** görünümündeki ayrıntıları inceleyin.  
  
### <a name="BKMK_Report_scenarios_categories_and_events"></a> Rapor senaryoları, kategoriler ve olaylar  
 **Uygulama zaman çizelgesi** araç senaryoları, kategoriler ve XAML performansıyla ilgili olayları için zamanlama verileri görüntüler.  
  
### <a name="BKMK_Diagnostic_session_timeline"></a> Tanılama oturumu zaman çizelgesi  
 ![Performans ve tanılama zaman çizelgesi](../profiling/media/diaghub-timelinewithusermarks.png "DIAGHUB_TimelineWithUserMarks")  
  
 Sayfanın üst cetvel profili oluşturulan bilgiler için zaman çizelgesini gösterir. Bu zaman çizelgesi hem de geçerli **UI iş parçacığı kullanımı** grafiği ve **görsel üretilen iş** grafiği. Zaman çizelgesinin bir bölümü seçmek için, zaman çizelgesindeki gezinti çubuklarını sürükleyerek raporun kapsamını daraltabilirsiniz.  
  
 Zaman çizelgesi ayrıca, eklediğiniz kullanıcı işaretlerini ve uygulamanın etkinleştirme yaşam döngüsü olaylarını da görüntüler.  
  
### <a name="BKMK_UI_thread_utilization_graph"></a> UI iş parçacığı kullanım grafiği  
 ![CPU Kullanım Grafiği](../profiling/media/timeline-cpuutilization.png "TIMELINE_CpuUtilization")  
  
 **UI iş parçacığı kullanımı (%)** grafiğidir göreli harcanan süreyi bir kategori için bir koleksiyon aralığı sırasında görüntüleyen bir çubuk grafiği.  
  
### <a name="BKMK_Visual_throughput_FPS_graph"></a> Görsel üretilen iş (FPS) grafiği  
 ![Görsel üretilen iş grafiği](../profiling/media/timeline-visualthroughput.png "TIMELINE_VisualThroughput")  
  
 **Görsel üretilen iş (FPS)** çizgi grafiği, uygulama için kullanıcı Arabirimi ve kompozisyon iş parçacığında saniyedeki kare sayısını (FPS) gösterir.  
  
### <a name="BKMK_Timeline_details_"></a> Zaman Çizelgesi ayrıntıları  
 Ayrıntılar görünümü, raporu analiz ettiğiniz zamandan büyük bir süre içinde ücretlendirilecektir. Uygulamanızın Kullanıcı arabirimi çerçevesi alt sistemi veya CPU 'YU kullanan sistem bileşeni tarafından kategorilere ayrılması için ayrıntılı bir görünümünü gösterir.  
  
 Aşağıdakiler desteklenir:  
  
|||  
|-|-|  
|**Ayrıştırma**|XAML dosyaları ayrıştırma ve oluşturma nesneleri için harcanan süre.<br /><br /> **Zaman çizelgesi ayrıntılarında** **ayrıştırma** düğümünün genişletilmesi, kök olayın sonucu olarak ayrıştırılmış tüm XAML dosyalarının bağımlılık zincirini görüntüler. Bu, performans duyarlı senaryolarda gereksiz dosya ayrıştırmayı ve nesne oluşturmayı tanımlamanızı ve bunları en iyi hale getirmenize olanak tanır.|  
|**Düzen**|Büyük uygulamalar, öğeleri binlerce aynı anda ekranda gösterilebilir. Bu, düşük bir kullanıcı arabirimi kare hızına ve buna karşılık gelen kötü uygulama yanıt verme hızına yol açabilir. Düzen olayı her bir öğenin (örneğin, düzenleme, ölçü, ApplyTemplate, ArrangeOverride ve ArrangeOverride) nasıl düzenlenmesinin maliyetini doğru şekilde belirler ve bir düzen geçişinde bir bölümü alan görsel ağaçları oluşturur. Bu görselleştirmeyi, mantıksal Ağaçlarınızdan hangilerinin ayıklanmayı gerektiğini tespit etmek veya Düzen geçişinizi iyileştirmek için diğer erteleme mekanizmalarını değerlendirmek için kullanabilirsiniz.|  
|**İşleme**|Ekranda çizim XAML öğeleri için geçen süre.|  
|**BEN / 0**|Harcanan süre yerel diskten veya erişilir ağ kaynaklarına veri alma [Microsoft Windows Internet (WinINet) API](https://msdn.microsoft.com/library/windows/desktop/aa385331.aspx).|  
|**Uygulama kodu**|Ayrıştırma veya düzenleme ile ilgili olmayan uygulama (Kullanıcı) kodunu yürütmek için harcanan süre.|  
|**XAML diğer**|XAML çalışma zamanı kodu yürütürken harcanan süre.|  
  
> [!TIP]
> Seçin **CPU kullanımı** ile birlikte aracı **uygulama zaman çizelgesi** aracı, UI iş parçacığında yürütülen görünümü uygulama yöntemler için profil oluşturmayı başlat. Uzun süre çalışan uygulama kodu taşımak için bir arka plan iş parçacığı UI yanıtlama hızını artırabilir.  
  
#### <a name="BKMK_Customizing_Timeline_details_"></a> Zaman Çizelgesi ayrıntıları özelleştirme  
 Kullanım **zaman çizelgesi ayrıntıları** sıralama, filtreleme ve açıklamalarını belirtmek için araç **zaman çizelgesi ayrıntıları** girişleri görüntüleyin.  
  
|||  
|-|-|  
|**Sıralama ölçütü**|Başlangıç zamanı veya olayları uzunluğunu göre sıralayın.|  
|![Olayları çerçeveye göre Gruplandır](../profiling/media/timeline-groupbyframes.png "TIMELINE_GroupByFrames")|Ekler veya bir üst düzey kaldırır **çerçeve** olayları çerçeve tarafından gruplandırır kategorisi.|  
|![Zaman çizelgesi ayrıntı listesini filtrele](../profiling/media/timeline-filter.png "TIMELINE_Filter")|Listeyi seçili kategorilerdeki ve olayları uzunluğunu göre filtreler.|  
|![Zaman çizelgesi ayrıntıları bilgilerini Özelleştir](../profiling/media/timeline-viewsettings.png "TIMELINE_ViewSettings")|Ek açıklamalar olayları belirtmenize olanak sağlar.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WPF ekibi blogu: WPF uygulamaları Için yenı UI performans analizi aracı](https://devblogs.microsoft.com/wpf/new-ui-performance-analysis-tool-for-wpf-applications/)   
 [ C++, C#Ve Visual Basic kullanarak Windows Mağazası uygulamaları için en iyi performans uygulamaları](https://msdn.microsoft.com/567bcefa-5da5-4e42-a4b8-1358c71adfa2)   
 [WPF Uygulama Performansını İyileştirme](https://msdn.microsoft.com/library/ac8c6aa3-3c68-4a24-9827-3b6c829c1ebf)
