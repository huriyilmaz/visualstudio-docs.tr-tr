---
title: İş parçacıkları görünümü (paralel performans) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.view.threadblocking
helpviewer_keywords:
- Concurrency Visualizer, Threads View (Parallel Performance)
ms.assetid: 2e441103-a266-407b-88c3-fb58716257a3
caps.latest.revision: 26
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0d685dc39f5e07840a5995f7fe67988840c3f50a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64821980"
---
# <a name="threads-view-parallel-performance"></a>İş Parçacıkları Görünümü (Paralel Performans)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

İş parçacıkları görünümü Eşzamanlılık Görselleştiricisinin en ayrıntılı ve özellik açısından zengin görünümüdür. Bu görünümü kullanarak, iş parçacıklarının eşitleme, g/ç veya başka bir nedenden dolayı yürütülmesini veya engellenip engellenmeyeceğini belirleyebilirsiniz.  
  
 Profil analizi sırasında eşzamanlılık görselleştiricisi her bir uygulama iş parçacığı için tüm işletim sistemi içerik anahtarı olaylarını inceler. Bağlam anahtarları şunlar gibi birçok nedenden kaynaklanabilir:  
  
- Eşitleme temel alınarak bir iş parçacığı engellenir.  
  
- Bir iş parçacığının hisse süresi dolar.  
  
- Bir iş parçacığı engelleyici g/ç isteği yapar.  
  
  İş parçacığı görünümü, bir iş parçacığı yürütmeyi durduğunda her bağlam anahtarına bir kategori atar. Kategoriler, görünümün sol alt kısmındaki göstergede gösterilir. Eşzamanlılık görselleştiricisi, iyi bilinen engelleme API 'Leri için iş parçacığının çağrı yığınını arayarak bağlam anahtarı olaylarını kategorilere ayırır. Çağrı yığını eşleşmesi yoksa tarafından sağlanmış olan bekleme nedeni [!INCLUDE[TLA#tla_mswin](../includes/tlasharptla-mswin-md.md)] kullanılır. Ancak, [!INCLUDE[TLA#tla_mswin](../includes/tlasharptla-mswin-md.md)] Kategori bir uygulama ayrıntısı temelinde olabilir ve kullanıcının amacını yansıtmayabilir. Örneğin, [!INCLUDE[TLA#tla_mswin](../includes/tlasharptla-mswin-md.md)] yerel bir ince okuyucu-yazıcı kilidinde, eşitleme yerine g/ç olarak engelleme bekleme nedenini raporlar. Çoğu durumda, bağlam anahtarı olaylarına karşılık gelen çağrı yığınlarını inceleyerek engelleyici bir olayın kök nedenini belirleyebilirsiniz.  
  
  Iş parçacıkları görünümü iş parçacıkları arasındaki bağımlılıkları da gösterir. Örneğin, bir eşitleme nesnesi üzerinde engellenmiş bir iş parçacığını belirlerseniz, onu engellenmemiş iş parçacığını arayabilir ve bu iş parçacığının çağrı yığınında etkinliği, diğerinin engellemesini kaldırdığınızda izleyebilirsiniz.  
  
  İş parçacıkları yürütürken Eşzamanlılık Görselleştiricisi örnekleri toplar. Iş parçacıkları görünümünde, bir yürütme kesimi sırasında bir veya daha fazla iş parçacığı tarafından hangi kodun yürütüleceğini çözümleyebilirsiniz. Ayrıca, engelleme raporlarını ve çağrı yığını ağacının yürütülmesi profilini oluşturan raporları inceleyebilirsiniz.  
  
## <a name="usage"></a>Kullanım  
 Iş parçacıkları görünümünü kullanabileceğiniz bazı yollar şunlardır:  
  
- Uygulamanın kullanıcı arabiriminin (UI) belirli yürütme aşamaları sırasında yanıt vermemesine neden olan nedenleri belirler.  
  
- Eşitleme, g/ç, sayfa hataları ve diğer olaylar üzerinde engellemeyi geçen süreyi belirler.  
  
- Sistemde yürütülen diğer işlemlerden girişim derecesini belirler.  
  
- Paralel yürütme için Yük Dengeleme sorunlarını belirler.  
  
- Tam veya varolmayan ölçeklenebilirlik için nedenleri (örneğin, paralel uygulama performansının neden daha fazla mantıksal çekirdek kullanılabilir olduğunda geliştirmediğini) belirler.  
  
- Paralelleştirme konusunda yardımcı olmak için uygulamadaki eşzamanlılık derecesini anlayın.  
  
- Çalışan iş parçacıkları ve yürütmenin kritik yolları arasındaki bağımlılıkları anlayın.  
  
## <a name="examining-specific-time-intervals-and-threads"></a>Belirli zaman aralıklarını ve Iş parçacıklarını İnceleme  
 Iş parçacıkları görünümü bir zaman çizelgesi gösterir. Uygulamanızın belirli aralıklarını ve iş parçacıklarını incelemek için zaman çizelgesi içinde yakınlaştırıp kaydırma yapabilirsiniz. X ekseninde zaman ve y ekseni üzerinde birçok kanal vardır:  
  
- Sistemdeki her disk sürücüsü için iki g/ç kanalı, okuma için bir kanal ve yazma işlemleri için bir kanal.  
  
- İşlemdeki her iş parçacığı için bir kanal.  
  
- İzlemede işaret olayları varsa işaretçi kanalları. İşaretçi kanalları başlangıçta bu olayları oluşturan iş parçacığı kanalları altında görünür.  
  
- GPU kanalları.  
  
  Aşağıda, Iş parçacıkları görünümü gösterilmektedir:  
  
  ![İş Parçacıkları Görünümü](../profiling/media/threadsviewnarrowing.png "Threadsviewdaraltma")  
  İş Parçacıkları Görünümü  
  
  İlk olarak, iş parçacıkları oluşturuldukları sırada sıralanır, böylece ana uygulama iş parçacığı ilk olarak olur. İş parçacıklarını başka bir ölçüte göre sıralamak için görünümün sol üst köşesindeki sıralama seçeneğini kullanabilirsiniz (örneğin, çoğu yürütme işi tarafından gerçekleştirilir).  
  
  Soldaki sütunda adlarını seçerek ve ardından araç çubuğunda **Seçili Iş parçacıklarını Gizle** düğmesini seçerek, iş gerçekleştirmeyen iş parçacıklarını gizleyebilirsiniz. İstatistikleri ilgisiz olduğu ve raporları günlüğe koyabileceği için tamamen engellenen iş parçacıklarını gizlemeniz önerilir.  
  
  Gizlenecek ek iş parçacıklarını belirlemek için, etkin göstergede, **profil raporu** sekmesinde **Iş parçacığı başına Özet** raporunu seçin. Bu, şu anda seçili olan zaman aralığı için iş parçacıklarının durumunu gösteren yürütme dökümü grafiğini görüntüler. Bazı yakınlaştırma düzeylerinde bazı iş parçacıkları görüntülenmeyebilir. Bu gerçekleştiğinde, üç nokta sağ tarafta görüntülenir.  
  
  Bir zaman aralığı seçtiğinizde ve içindeki bazı iş parçacıkları için performans analizinizi başlatabilirsiniz.  
  
## <a name="analysis-tools"></a>Analiz araçları  
 Bu bölümde raporlar ve diğer analiz araçları açıklanmaktadır.  
  
### <a name="thread-blocking-details"></a>İş parçacığı engelleme ayrıntıları  
 Bir iş parçacığında belirli bir bölgedeki engelleyici bir olay hakkında bilgi almak için, bir araç ipucunu göstermek üzere bu bölgedeki işaretçiyi bekletin. Kategori, bölge başlangıç saati, engelleme süresi ve bir tane varsa engelleme API 'SI gibi bilgileri içerir. Engelleme bölgesini seçerseniz o zaman içindeki yığın alt bölmede görüntülenir ve araç ipucunda görüntülenen bilgilerle birlikte görüntülenir. Çağrı yığınını inceleyerek, iş parçacığı engelleme olayının temel nedenini belirleyebilirsiniz. Segmenti seçerek ve geçerli sekmeyi inceleyerek ek işlem ve iş parçacığı bilgileri bulabilirsiniz.  
  
 Yürütmenin bir yolu birden çok engelleme olayına sahip olabilir. Sorun bölgelerini daha hızlı bulabilmeniz için kategoriyi engelleyerek bunları inceleyebilirsiniz. Sol taraftaki göstergedeki engelleme kategorisinden birini seçmeniz yeterlidir.  
  
### <a name="dependencies-between-threads"></a>Iş parçacıkları arasındaki bağımlılıklar  
 Eşzamanlılık görselleştiricisi, engellenen bir iş parçacığının ne yaptığını belirleyebilmeniz ve başka bir iş parçacığının yürütmek için ne yaptığını öğrenmeniz için, işlem sürecinde iş parçacıkları arasındaki bağımlılıkları gösterebilir. Hangi iş parçacığının başka bir iş parçacığının engellemesini kaldırmasını belirlemek için ilgili engelleme segmentini seçin. Eşzamanlılık görselleştiricisi engellemeyi kaldırma iş parçacığını belirleyebiliyorsanız, engellemeyi kaldırma iş parçacığı ve engelleme segmentini izleyen yürütme segmenti arasına bir çizgi çizer. Ayrıca, **engellemeyi kaldırma yığını** sekmesi ilgili çağrı yığınını gösterir.  
  
### <a name="thread-execution-details"></a>İş parçacığı yürütme ayrıntıları  
 Bir iş parçacığının zaman çizelgesi grafiğinde yeşil segmentler, ne zaman kod yürüttüğünü gösterir. Bir yürütme segmenti hakkında daha ayrıntılı bilgi edinebilirsiniz.  
  
 Bir yürütme segmentinde bir nokta seçtiğinizde, eşzamanlılık görselleştiricisi ilgili çağrı yığınında o zaman için arama yapar ve ardından yürütme segmentinde seçili noktanın üzerinde siyah bir giriş işareti görüntüler ve çağrı yığınını **geçerli yığın** sekmesinde görüntüler. Yürütme segmentinde birden çok noktayı seçebilirsiniz.  
  
> [!NOTE]
> Eşzamanlılık görselleştiricisi bir yürütme segmentinde bir seçimi çözemeyebilir. Genellikle bu durum, segmentin süresi bir milisaniyeye eşit olduğunda meydana gelir.  
  
 Şu anda seçili olan zaman aralığındaki tüm etkin (gizli olmayan) iş parçacıkları için bir yürütme profili almak üzere etkin göstergedeki **yürütme** düğmesini seçin.  
  
### <a name="timeline-graph"></a>Zaman çizelgesi grafiği  
 Zaman çizelgesi grafiğinde, işlemdeki tüm iş parçacıklarının ve ana bilgisayardaki tüm fiziksel disk cihazlarının etkinliği gösterilmektedir. Ayrıca GPU etkinliklerini ve işaret olaylarını görüntüler.  Daha uzun bir zaman aralığını görüntülemek için daha fazla ayrıntı veya çıkış görmek üzere yakınlaştırabilirsiniz. Kategoriler, başlangıç zamanları, süreler ve çağrı yığını durumları hakkındaki ayrıntıları almak için grafikteki noktaları da seçebilirsiniz.  
  
 Zaman çizelgesi grafiğinde, bir renk, belirli bir zamanda bir iş parçacığının durumunu gösterir. Örneğin, yeşil kesimler yürütülülüyor, kırmızı kesimlerin eşitleme için engellenmiş olması, sarı kesimlerin önceden yapılmış olması ve mor kesimlerin cihaz g/ç 'ye bağlı olması. Bu görünümü, paralel bir döngüde veya eşzamanlı görevlerde yer alan iş parçacıkları arasındaki iş dengesini incelemek için kullanabilirsiniz. Bir iş parçacığının tamamlaması daha uzun sürüyorsa, iş dengesiz olabilir. İş parçacıkları arasında daha eşit bir şekilde dağıtarak programınızın performansını geliştirmek için bu bilgileri kullanabilirsiniz.  
  
 Bir zaman noktasında yalnızca bir iş parçacığı yeşil (yürütülüyor) ise uygulama, sistem üzerindeki eşzamanlılık özelliğinden tam olarak yararlanmayabilir. Zaman çizelgesi grafiğini, iş parçacıkları ve engelleme ve engellenen iş parçacıkları arasındaki zamana bağlı ilişkiler arasındaki bağımlılıkları incelemek için kullanabilirsiniz. İş parçacıklarını yeniden düzenlemek için bir iş parçacığı seçin ve ardından araç çubuğunda yukarı veya aşağı düğmesini seçin. İş parçacıklarını gizlemek için, bunları seçin ve sonra **Iş parçacıklarını Gizle** düğmesini seçin.  
  
### <a name="profile-reports"></a>Profil raporları  
 Zaman çizelgesi grafiğinin altında, bir zaman çizelgesi profili ve çeşitli raporlar için sekmeler içeren bir bölme bulunur. Raporları, Iş parçacıkları görünümünü değiştirirken otomatik olarak güncelleştirir. Büyük izlemeler için, güncelleştirmeler hesaplanırken raporlar bölmesi kullanılamayabilir. Her raporda iki filtre ayarlaması vardır: gürültü azaltma ve Yalnızca kendi kodum. Az zaman harcanması gereken çağrı ağacı girişlerini filtrelemek için gürültü azaltma kullanın. Varsayılan filtre değeri yüzde 2 ' dir, ancak yüzde 0 ' dan yüzde 99 ' e ayarlayabilirsiniz. Yalnızca kodunuzun çağrı ağacını görüntülemek için **yalnızca kendi kodum** onay kutusunu seçin. Tüm çağrı ağaçlarını görüntülemek için, temizleyin.  
  
#### <a name="profile-report"></a>Profil raporu  
 Bu sekmede, etkin göstergedeki girişlere karşılık gelen raporlar gösterilmektedir. Bir raporu göstermek için girdilerden birini seçin.  
  
#### <a name="current-stack"></a>Geçerli yığın  
 Bu sekme, zaman çizelgesi grafiğindeki iş parçacığı kesimindeki seçili bir nokta için çağrı yığınını gösterir. Çağrı yığınları, yalnızca programınızdaki ilgili etkinlikleri gösterecek şekilde kırpılır.  
  
#### <a name="unblocking-stack"></a>Yığın Engellemesini Kaldırma  
 Hangi iş parçacığının seçili iş parçacığının engellemesini ve kod satırını görmek için **yığın engellemesini** Kaldır sekmesini seçin.  
  
#### <a name="execution"></a>Yürütme  
 Yürütme raporu, uygulamanın yürütülürken harcadığı sürenin dökümünü gösterir.  
  
 Yürütme zamanının harcadığı kod satırını bulmak için çağrı ağacını genişletin ve ardından çağrı ağacı girişinin kısayol menüsünde **kaynağı görüntüle** veya **çağrı sitelerini görüntüle**' yi seçin. **Kaynağı görüntüle** yürütülen kod satırını konumlandırır. **Çağrı sitelerini görüntüle** , yürütülen kod satırını çağıran kod satırını konumlandırır. Yalnızca bir çağrı sitesi varsa, kendi kod satırı vurgulanır. Birden çok çağrı sitesi varsa, görüntülenen iletişim kutusunda istediğiniz birini seçebilir ve ardından çağrı sitesi kodunu vurgulamak için **Kaynağa Git** düğmesini seçebilirsiniz. En çok örnek olan çağrı sitesini, en son saati veya her ikisini de bulmak en iyi seçenektir. Daha fazla bilgi için bkz. [yürütme profili raporu](../profiling/execution-profile-report.md).  
  
#### <a name="synchronization"></a>Eşitleme  
 Eşitleme raporu, her çağrı yığınının toplam engellenme süreleriyle birlikte eşitleme bloklarından sorumlu çağrıları gösterir. Daha fazla bilgi için bkz. [eşitleme süresi](../profiling/synchronization-time.md).  
  
#### <a name="io"></a>G/Ç  
 G/ç raporu, her çağrı yığınının toplam engellenme süreleriyle birlikte g/ç bloklarından sorumlu olan çağrıları gösterir. Daha fazla bilgi için bkz. [g/ç zamanı (Iş parçacıkları görünümü)](../profiling/i-o-time-threads-view.md).  
  
#### <a name="sleep"></a>Uyku  
 Uyku raporu, her çağrı yığınının toplam engellenme süreleriyle birlikte, uyku bloklarında sorumlu olan çağrıları gösterir. Daha fazla bilgi için bkz. [uyku süresi](../profiling/sleep-time.md).  
  
#### <a name="memory-management"></a>Bellek Yönetimi  
 Bellek yönetimi raporu, her çağrı yığınının toplam engellenme süreleriyle birlikte bellek yönetimi bloklarının gerçekleştiği çağrıları gösterir. Bu bilgileri, aşırı sayfalama veya atık toplama sorunları olan bölgeleri belirlemek için kullanabilirsiniz.  Daha fazla bilgi için bkz. [bellek yönetimi zamanı](../profiling/memory-management-time.md).  
  
#### <a name="preemption"></a>Önalım  
 Önalım raporu, sistemdeki işlemlerin geçerli işlemi ve geçerli işlemde iş parçacıklarının değiştirdikleri bireysel iş parçacıklarını önişlediği örnekleri gösterir. Bu bilgileri, önalım için en çok sorumlu olan işlem ve iş parçacıklarını belirlemek için kullanabilirsiniz. Daha fazla bilgi için bkz. [önalım Time](../profiling/preemption-time.md).  
  
#### <a name="ui-processing"></a>UI Işleme  
 UI işleme raporu, her bir çağrı yığınının toplam engellenme süreleriyle birlikte UI işleme bloklarında sorumlu olan çağrıları gösterir. Daha fazla bilgi için bkz. [UI Işleme süresi](../profiling/ui-processing-time.md).  
  
#### <a name="per-thread-summary"></a>Her Iş parçacığı Özeti  
 Bu sekme, her iş parçacığının çalıştırma, engelleme, g/ç ve diğer durumlarda harcadığı toplam sürenin renk kodlu bir sütun görünümünü gösterir. Sütunlar alt kısımdaki etiketlidir. Zaman çizelgesi grafiğinde yakınlaştırma düzeyini ayarlarken, bu sekme otomatik olarak güncelleştirilir. Bazı yakınlaştırma düzeylerinde bazı iş parçacıkları görüntülenmeyebilir. Bu gerçekleştiğinde, üç nokta sağ tarafta görüntülenir. İstediğiniz iş parçacığı görünmezse, diğer iş parçacıklarını gizleyebilirsiniz. Daha fazla bilgi için bkz. [Iş parçacığı özet raporu başına](../profiling/per-thread-summary-report.md).  
  
#### <a name="disk-operations"></a>Disk Işlemleri  
 Bu sekme, geçerli işlem adına disk g/ç 'ye hangi işlemlerin ve iş parçacıklarının dahil olduğunu, dokundukları dosyaları (örneğin, yüklenen dll 'Leri), kaç bayt okunduğunu ve diğer bilgileri gösterir. Bu raporu, yürütme sırasında dosyalara erişirken harcanan süreyi değerlendirmek için, özellikle de işleminiz g/ç ile bağlantılı gibi durumlarda kullanabilirsiniz. Daha fazla bilgi için bkz. [disk Işlemleri raporu](../profiling/disk-operations-report-threads-view.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Eşzamanlılık Görselleştiricisi](../profiling/concurrency-visualizer.md)
