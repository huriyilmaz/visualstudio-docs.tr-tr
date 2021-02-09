---
title: Eşzamanlılık Görselleştiricicide iş parçacığı görünümü | Microsoft Docs
description: Iş parçacıkları görünümünde, bir yürütme kesimi sırasında hangi iş parçacıklarının kod yürüttüğünü belirleyebileceğinizi öğrenin.
ms.date: 11/04/2018
ms.topic: conceptual
f1_keywords:
- vs.performance.view.threadblocking
helpviewer_keywords:
- Concurrency Visualizer, Threads View (Parallel Performance)
ms.assetid: 2e441103-a266-407b-88c3-fb58716257a3
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 77655e2e040b6a14a5c82151dac451e8373ea674
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99876985"
---
# <a name="threads-view-in-the-concurrency-visualizer"></a>Eşzamanlılık görselleştiricisi içindeki iş parçacıkları görünümü

**Iş parçacıkları** görünümü Eşzamanlılık Görselleştiricisinin en ayrıntılı ve özellik açısından zengin görünümüdür. **İş** parçacıkları görünümünde, bir yürütme kesimi sırasında hangi iş parçacıklarının kod yürüttüğünü tanımlayabilir ve eşitleme, g/ç ya da başka nedenlerden dolayı iş parçacıklarının yürütülmesini veya engellenip engellenmeyeceğini analiz edebilirsiniz. **Iş parçacıkları** raporları da profil çağrısı-yığın ağacı yürütme ve engellemeyi kaldırma iş parçacıklarını görüntüler.

İş parçacıkları yürütülürken Eşzamanlılık Görselleştiricisi örnekleri toplar. Bir iş parçacığı yürütmeyi durdurduğu zaman görselleştiricisi, iş parçacığı için tüm işletim sistemi bağlam anahtarı olaylarını inceler. Bağlam anahtarları oluşabilir, nedeni:

- Eşitleme temel alınarak bir iş parçacığı engellenir.
- Bir iş parçacığının hisse süresi dolar.
- Bir iş parçacığı engelleyici g/ç isteği yapar.

Eşzamanlılık görselleştiricisi iş parçacığı ve bağlam anahtarı olaylarını kategorilere ayırır ve iyi bilinen engelleme API 'Leri için iş parçacıklarının çağrı yığınlarını arar. İş parçacığı kategorilerini, **Iş parçacıkları** görünümünde sol alt köşedeki etkin göstergede görüntüler. Çoğu durumda, bağlam anahtarı olaylarına karşılık gelen çağrı yığınlarını inceleyerek engelleyici bir olayın kök nedenini belirleyebilirsiniz.

Çağrı yığını eşleşmesi yoksa eşzamanlılık görselleştiricisi tarafından sağlanmış bekleme nedenini kullanır [!INCLUDE[TLA#tla_mswin](../code-quality/includes/tlasharptla_mswin_md.md)] . Ancak, [!INCLUDE[TLA#tla_mswin](../code-quality/includes/tlasharptla_mswin_md.md)] Kategori bir uygulama ayrıntısı temelinde olabilir ve Kullanıcı amacını yansıtmayabilir. Örneğin, [!INCLUDE[TLA#tla_mswin](../code-quality/includes/tlasharptla_mswin_md.md)] yerel bir ince okuyucu-yazıcı kilidinde, eşitleme yerine g/ç olarak engelleme bekleme nedenini raporlar.

**Iş parçacıkları** görünümü iş parçacıkları arasındaki bağımlılıkları da gösterir. Örneğin, bir eşitleme nesnesinde engellenmiş bir iş parçacığını belirlerseniz, engeli kaldırılmış iş parçacığını bulabilirsiniz. Engellemeyi kaldırma iş parçacığı için çağrı yığınını, diğerinin engellemesinin kaldırılması durumunda inceleyebilirsiniz.

**Iş parçacıkları** görünümünü şu şekilde kullanabilirsiniz:

- Uygulamanın kullanıcı arabiriminin (UI) belirli yürütme aşamaları sırasında yanıt vermemesine neden olan nedenleri belirler.
- Eşitleme, g/ç, sayfa hataları ve diğer olaylar üzerinde engellemenin ne kadar zaman harcadığını belirleme.
- Sistemde yürütülen diğer işlemlerden girişim derecesini bulur.
- Paralel yürütme için Yük Dengeleme sorunlarını belirler.
- Alt veya var olmayan ölçeklenebilirlik için nedenleri bulun. Örneğin, bir paralel uygulamanın performansı, daha fazla mantıksal çekirdek kullanılabilir olduğunda neden geliştirilemez.
- Paralelleştirme konusunda yardımcı olmak için uygulamadaki eşzamanlılık derecesini anlayın.
- Çalışan iş parçacıkları ve yürütmenin kritik yolları arasındaki bağımlılıkları belirler.

## <a name="use-threads-view"></a>Iş parçacığı görünümünü kullan

Eşzamanlılık Görselleştiricisi ' i başlatmak için   >  **eşzamanlılık görselleştirmesini** Çözümle ' yi seçin ve ardından **Yeni işlem başlatma** gibi bir seçenek belirleyin.

Eşzamanlılık görselleştiricisi uygulamayı başlatır ve **toplamayı durdur** seçeneğini seçinceye kadar bir izleme toplar. Görselleştiricisi daha sonra izlemeyi analiz eder ve sonuçları izleme raporu sayfasında görüntüler.

**Iş parçacıkları** görünümünü açmak için raporun sol üst kısmındaki **iş parçacıkları** sekmesini seçin.

![İş parçacıkları görünümü](../profiling/media/threadsviewnarrowing.png "İş parçacıkları görünümü")

Bir performans analizini başlatmak için zaman aralıklarını ve iş parçacıklarını seçin.

## <a name="timeline-analysis"></a>Zaman çizelgesi Analizi

**Iş parçacıkları** görünümünün üst bölümü bir zaman çizelgesi olur. Zaman çizelgesi, işlemdeki tüm iş parçacıklarının etkinliklerini ve ana bilgisayardaki tüm fiziksel disk cihazlarını gösterir. Ayrıca GPU etkinliklerini ve işaret olaylarını görüntüler.

Zaman çizelgesinde x ekseni zaman ve y ekseni üzerinde birçok kanala sahiptir:

- Sistemdeki her disk sürücüsü için iki g/ç kanalı, okuma için bir kanal ve yazma işlemleri için bir kanal.
- İşlemdeki her iş parçacığı için bir kanal.
- İzlemede işaret olayları varsa işaretçi kanalları. İşaretçi kanalları başlangıçta bu olayları oluşturan iş parçacığı kanalları altında görünür.
- GPU kanalları.

Başlangıçta, iş parçacıkları oluşturuldukları sırada sıralanır, bu nedenle ana uygulama iş parçacığı ilk olarak olur. İş parçacıklarını **yürütme** gibi başka bir ölçüte göre sıralamak için **sıralama ölçütü** açılır listesinde başka bir seçenek belirleyin.

Zaman çizelgesi renkleri, belirli bir zamanda bir iş parçacığının durumunu gösterir. Yeşil segmentler yürütülüyor, kırmızı kesimlerin eşitleme için engellenmesi, sarı kesimlerin daha önce olması ve mor kesimlerin cihaz g/ç 'ye bağlı olması.

Daha fazla ayrıntı görüntülemek için yakınlaştırabilir veya daha uzun bir zaman aralığını görüntülemek için yakınlaştırabilirsiniz. Kategoriler, başlangıç zamanları, gecikmeler ve çağrı yığını durumlarıyla ilgili ayrıntıları almak için, kesimleri ve grafikteki noktaları seçin.

Paralel bir döngüye veya eşzamanlı görevlere dahil olan iş parçacıkları arasındaki iş dengesini incelemek için zaman çizelgesini kullanın. Bir iş parçacığının tamamlaması daha uzun sürüyorsa, iş dengesiz olabilir. İş parçacıkları arasında daha eşit bir şekilde dağıtarak uygulamanızın performansını artırabilirsiniz.

Bir zaman noktasında yalnızca bir iş parçacığı yürütülerek, uygulama sistemde eşzamanlılık özelliğinden tam olarak yararlanmayabilir. Zaman çizelgesi grafiğini kullanarak iş parçacıkları arasındaki bağımlılıkları ve engelleme ve engellenen iş parçacıkları arasındaki zamana bağlı ilişkileri inceleyebilirsiniz. İş parçacıklarını yeniden düzenlemek için bir iş parçacığı seçin ve ardından araç çubuğunda yukarı veya aşağı simgesini seçin.

Çalışmaları gerçekleşmeyen veya tamamen engellenmiş olan iş parçacıklarını gizleyebilirsiniz, çünkü istatistikleri ilgisiz ve raporları günlüğe kaydedebilir. Kendi adlarını seçerek ve ardından **Seçilen iş parçacıklarını Gizle** ' yi seçerek ve araç çubuğundaki **Seçili iş parçacıkları dışındaki Tümünü Gizle** ' yi seçerek iş parçacıklarını gizleyin. Gizlenecek iş parçacıklarını belirlemek için, sol alttaki **Iş parçacığı başına Özet** bağlantısını seçin. **Iş parçacığı başına Özet** grafiğinde hiçbir etkinliği olmayan iş parçacıklarını gizleyebilirsiniz.

### <a name="thread-execution-details"></a>İş parçacığı yürütme ayrıntıları
Bir yürütme kesimi hakkında daha ayrıntılı bilgi almak için, zaman çizelgesinin yeşil segmentinde bir nokta seçin. Eşzamanlılık görselleştiricisi seçili noktanın üzerinde siyah bir giriş işareti görüntüler ve alt bölmenin **geçerli** sekmesinde çağrı yığınını gösterir. Yürütme segmentinde birden çok noktayı seçebilirsiniz.

>[!NOTE]
>Segmentin süresi bir milisaniyeye azsa, eşzamanlılık görselleştiricisi bir yürütme segmentinde seçimi çözemeyebilir.

Seçili zaman aralığındaki tüm gizli olmayan iş parçacıkları için bir yürütme profili almak üzere sol alt köşedeki göstergeyi **seçin.**

### <a name="thread-blocking-details"></a>İş parçacığı engelleme ayrıntıları
Bir iş parçacığında belirli bir bölge hakkında bilgi almak için, bir araç ipucunu göstermek üzere zaman çizelgesinde bu bölgenin üzerine gelin. Araç ipucunda kategori, başlangıç saati ve gecikme gibi bilgiler bulunur. Alt bölmenin **geçerli** sekmesinde çağrı yığınını bu noktada görüntülenecek bölgeyi seçin. Bölmesi aynı zamanda kategori, gecikme, API 'yi engelleme, varsa, bir tane varsa iş parçacığının engellemesini gösterir. Çağrı yığınını inceleyerek, iş parçacığı engelleme olaylarının temel nedenlerini belirleyebilirsiniz.

Bir yürütme yolunda birkaç engelleme olayı olabilir. Bu, kategoriyi engelleyerek ve sorun bölgelerini daha hızlı bir şekilde bulmak için soldaki göstergede bir engelleme kategorisi seçin.

### <a name="dependencies-between-threads"></a>İş parçacıkları arasındaki bağımlılıklar
Eşzamanlılık görselleştiricisi iş parçacıkları arasındaki bağımlılıkları gösterir, bu sayede engellenen bir iş parçacığının ne yapmaya çalıştığını ve hangi diğer iş parçacığının yürütmek için etkin olduğunu belirleyebilirsiniz.

Hangi iş parçacığının başka bir iş parçacığının engellemesini kaldırmasını belirlemek için, zaman çizelgesinde engelleme segmentini seçin. Eşzamanlılık görselleştiricisi engellemeyi kaldırma iş parçacığını belirleyebiliyorsanız, engellemeyi kaldırma iş parçacığı ve engelleme segmentini izleyen yürütme segmenti arasına bir çizgi çizer. İlgili çağrı yığınını görmek için alt bölmedeki **yığın engellemesini** Kaldır sekmesini seçin.

## <a name="profile-reports"></a>Profil raporları
Zaman çizelgesi grafiğinin altında, **profil raporu**, **geçerli** ve **yığın raporu kaldırma** sekmelerini içeren bir bölme bulunur. Zaman çizelgesi ve iş parçacıkları seçimlerini değiştirirken raporlar otomatik olarak güncelleştirir. Büyük izlemeler için, güncelleştirmeler hesaplanırken raporlar bölmesi geçici olarak kullanılamıyor olabilir.

### <a name="profile-report-tab"></a>Profil raporu sekmesi

**Profil raporunda** iki filtre vardır:

- Az zaman harcanması gereken çağrı ağacı girişlerini filtrelemek için alanındaki **gürültü azaltmada** yüzde 0 ile 99 arasında bir filtre değeri yazın. Varsayılan değer yüzde 2 ' dir.
- Yalnızca kodunuzun çağrı ağaçlarını görüntülemek için **yalnızca kendi kodum** onay kutusunu seçin. Tüm çağrı ağaçlarını görüntülemek için onay kutusunu temizleyin.

**Profil raporu** sekmesi, göstergedeki kategorilerin ve bağlantıların raporlarını gösterir. Bir raporu göstermek için sol taraftaki girişlerden birini seçin:

- **Yürütme** **Yürütme** raporu, uygulamanın yürütülürken harcadığı sürenin dökümünü gösterir.

  Yürütme zamanının harcadığı kod satırını bulmak için çağrı ağacını genişletin ve çağrı ağacı girişinin kısayol menüsünde **kaynağı görüntüle** veya **çağrı sitelerini görüntüle**' yi seçin. **Kaynağı görüntüle** yürütülen kod satırını konumlandırır. **Çağrı sitelerini görüntüle** , yürütülen satırı çağıran kod satırını konumlandırır. Yalnızca bir adet çağrı site satırı varsa, kodu vurgulanır. Çeşitli çağrı siteleri varsa, iletişim kutusunda istediğiniz birini seçin ve ardından **Kaynağa Git**' i seçin. En çok örnek olan çağrı sitesini, en son saati veya her ikisini de bulmak en iyi seçenektir. Daha fazla bilgi için bkz. [yürütme profili raporu](../profiling/execution-profile-report.md).

- **Eşitleme** **Eşitleme** raporu, her bir çağrı yığınının toplam engellenme süreleriyle birlikte, eşitleme bloklarından sorumlu çağrıları gösterir. Daha fazla bilgi için bkz. [eşitleme süresi](../profiling/synchronization-time.md).

- **g/ç** **G/ç** raporu, her bir çağrı yığınının toplam engellenme süreleriyle birlikte g/ç bloklarından sorumlu olan çağrıları gösterir. Daha fazla bilgi için bkz. [g/ç zamanı (Iş parçacıkları görünümü)](../profiling/i-o-time-threads-view.md).

- **Sleep** **Uyku** raporu, her bir çağrı yığınının toplam engellenme süreleriyle birlikte, uyku bloklarında sorumlu olan çağrıları gösterir. Daha fazla bilgi için bkz. [uyku süresi](../profiling/sleep-time.md).

- **Bellek yönetimi** **Bellek** yönetimi raporu, bellek yönetimi bloklarının gerçekleştiği, her bir çağrı yığınının toplam engellenme süreleriyle birlikte aramaları gösterir. Aşırı sayfalama veya atık toplama sorunları olan bölgeleri belirlemek için bu bilgileri kullanın.  Daha fazla bilgi için bkz. [bellek yönetimi zamanı](../profiling/memory-management-time.md).

- **Önalım** **Önalım** raporu, sistemdeki işlemlerin geçerli işlemi ve geçerli işlemde iş parçacıklarının değiştirildiği bireysel iş parçacıklarını gösterir. Bu bilgileri, önalım için en çok sorumlu olan işlem ve iş parçacıklarını belirlemek için kullanabilirsiniz. Daha fazla bilgi için bkz. [önalım Time](../profiling/preemption-time.md).

- **UI işleme** **UI işleme** raporu, her bir çağrı yığınının toplam engellenme SÜRELERIYLE birlikte UI işleme bloklarında sorumlu olan çağrıları gösterir. Daha fazla bilgi için bkz. [UI işleme süresi](../profiling/ui-processing-time.md).

- **Her Iş parçacığı Özeti** Seçili zaman aralığı için iş parçacıklarının durumunu gösteren bir grafik göstermek üzere **Iş parçacığı Özeti başına** ' yı seçin. Renk kodlu sütunlar, her iş parçacığının çalıştırma, engelleme, g/ç ve diğer durumlar için harcadığı toplam süreyi gösterir. İş parçacıkları alt kısımdaki etiketlidir. Zaman çizelgesi grafiğinde yakınlaştırma düzeyini ayarlarken bu grafik otomatik olarak güncelleştirilir.

  Bazı yakınlaştırma düzeylerinde bazı iş parçacıkları grafikte gösterilmeyebilir. Bu durumda, üç nokta (**...**) sağda görüntülenir. İstediğiniz iş parçacığı görünmezse, diğer iş parçacıklarını gizleyebilirsiniz. Daha fazla bilgi için bkz. [iş parçacığı özet raporu başına](../profiling/per-thread-summary-report.md).

- **Disk işlemleri** Geçerli işlem için disk g/ç 'ye dahil olan işlemleri ve iş parçacıklarını, dokundukları dosyaları (örneğin, yüklendikleri dll 'Ler), okudukları bayt sayısını ve diğer bilgileri göstermek için **disk işlemlerini** seçin. Bu raporu, yürütme sırasında dosyalara erişirken harcanan süreyi değerlendirmek için, özellikle de işleminiz g/ç ile bağlantılı gibi durumlarda kullanabilirsiniz. Daha fazla bilgi için bkz. [Disk işlemleri raporu](../profiling/disk-operations-report-threads-view.md).

### <a name="current-tab"></a>Geçerli sekme
Bu sekme, zaman çizelgesi grafiğindeki iş parçacığı kesimindeki seçili bir nokta için çağrı yığınını gösterir. Çağrı yığınları, yalnızca uygulamanızla ilgili etkinlikleri gösterecek şekilde kırpılır.

### <a name="unblocking-stack-tab"></a>Yığın sekmesinin engellemesini kaldırma
Bu sekme, seçilen iş parçacığının hangi iş parçacığının engellemesini ve engellemeyi kaldırma çağrı yığınını gösterir.

## <a name="see-also"></a>Ayrıca bkz.
- [Eşzamanlılık Görselleştiricisi](../profiling/concurrency-visualizer.md)
