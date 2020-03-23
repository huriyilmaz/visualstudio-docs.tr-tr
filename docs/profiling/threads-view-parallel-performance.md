---
title: Eşzamanlılık Görselleştiricisinde Iş Parçacığı görünümü | Microsoft Dokümanlar
ms.date: 11/04/2018
ms.topic: conceptual
f1_keywords:
- vs.performance.view.threadblocking
helpviewer_keywords:
- Concurrency Visualizer, Threads View (Parallel Performance)
ms.assetid: 2e441103-a266-407b-88c3-fb58716257a3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4382a21a68848a758f3d4cd37a8528722927691c
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "62973766"
---
# <a name="threads-view-in-the-concurrency-visualizer"></a>Eşzamanlılık Görselleştiricisinde Iş Parçacığı görünümü

**İş parçacıkları** görünümü, Eşzamanlılık Görselleştiricisi'ndeki en ayrıntılı ve zengin özelliklere sahip görünümdür. İş **Parçacıkları** görünümünde, bir yürütme kesimi sırasında hangi iş parçacıklarının kod yürütüldettiğini belirleyebilir ve iş parçacıklarının eşitleme, G/Ç veya diğer nedenlerden dolayı yürütülüp yürütülmediğini veya engellenemediğini çözümleyebilirsiniz. **İş parçacıkları,** arama yığını ağaç yürütme ve engellemeyi kaldırma iş parçacığı profillerini de raporlara göre görüntüle.

İş parçacıkları yürütülse de, Eşzamanlılık Görselleştiricisi örnekler toplar. Bir iş parçacığı yürütmeyi durdurduğunda, görselleştirici iş parçacığı için tüm işletim sistemi bağlam anahtarı olaylarını inceler. Bağlam anahtarları oluşabilir, çünkü:

- Bir iş parçacığı eşitleme ilkel engellenir.
- Bir iş parçacığının kuantum süresi doluyor.
- İş parçacığı engelleme G/Ç isteği yapar.

Eşzamanlı Visualizer iş parçacığı ve bağlam anahtarı olayları kategorilere ve iyi bilinen engelleme API'leri için iş parçacığı arama yığınları arar. İş parçacığı kategorilerini **iş parçacıkları** görünümünde sol alttaki etkin göstergede görüntüler. Çoğu durumda, bağlam anahtarı olaylarına karşılık gelen çağrı yığınlarını inceleyerek engelleme olayının temel nedenini tanımlayabilirsiniz.

Çağrı yığını eşleşmesi yoksa, Eşzamanlı Görselleştirici tarafından [!INCLUDE[TLA#tla_mswin](../code-quality/includes/tlasharptla_mswin_md.md)]sağlanan bekleme nedenini kullanır. Ancak, [!INCLUDE[TLA#tla_mswin](../code-quality/includes/tlasharptla_mswin_md.md)] kategori bir uygulama ayrıntısını temel alabilir ve kullanıcı amacını yansıtmayabilir. Örneğin, [!INCLUDE[TLA#tla_mswin](../code-quality/includes/tlasharptla_mswin_md.md)] Eşitleme yerine G/Ç olarak yerel ince okuyucu-yazar kilidini engellemenin bekleme nedenini raporlar.

**İş parçacıkları** görünümü de iş parçacıkları arasındaki bağımlılıkları gösterir. Örneğin, bir eşitleme nesnesi üzerinde engellenen bir iş parçacığı tanımlarsanız, onu kaldıran iş parçacığı bulabilirsiniz. Diğerinin engelini kaldıran noktada, engeli kaldırma iş parçacığı için çağrı yığınını inceleyebilirsiniz.

**İş Parçacıkları** görünümünü şu şekilde kullanabilirsiniz:

- Belirli yürütme aşamalarında bir uygulamanın kullanıcı arabiriminin (UI) yanıt vermeme nedenlerini belirleyin.
- Eşitleme, G/Ç, sayfa hataları ve diğer olayları engellemek için harcanan süreyi belirleyin.
- Sistemde çalıştırılabilen diğer işlemlerden kaynaklanan girişim derecesini keşfedin.
- Paralel yürütme için yük dengeleme sorunlarını tanımlayın.
- Optimal olmayan veya var olmayan ölçeklenebilirliğin nedenlerini bulun. Örneğin, daha fazla mantıksal çekirdek kullanılabilir olduğunda paralel bir uygulamanın performansı neden iyileşmez?
- Paralelleştirmeye yardımcı olmak için uygulamadaki eşzamanlılık derecesini anlayın.
- Alt iş parçacıkları ve kritik yürütme yolları arasındaki bağımlılıkları tanımlayın.

## <a name="use-threads-view"></a>İş Parçacıkları görünümünü kullanma

Eşzamanlılık Görselleştiricisini başlatmak için**EşzamanlıLık Görselleştiricisini** **Çözümle'yi** > seçin ve ardından **Yeni İşlembaşlat**gibi bir seçenek seçin.

Eşzamanlı Görselleştirici uygulamayı başlatır ve **Koleksiyonu Durdur'u**seçene kadar bir izleme toplar. Görselleştirici daha sonra izlemeyi analiz eder ve sonuçları izleme raporu sayfasında görüntüler.

İş **Parçacıkları** görünümünü açmak için raporda sol üstteki İş **Parçacıkları** sekmesini seçin.

![İş parçacıkları görünümü](../profiling/media/threadsviewnarrowing.png "İş parçacıkları görünümü")

Performans çözümlemesi başlatmak için zaman aralıklarını ve iş parçacıklarını seçin.

## <a name="timeline-analysis"></a>Zaman çizelgesi analizi

**İş parçacıkları** görünümünün üst kısmı bir zaman çizelgesidir. Zaman çizelgesi, işlemdeki tüm iş parçacıklarının ve ana bilgisayardaki tüm fiziksel disk aygıtlarının etkinliğini gösterir. Ayrıca GPU etkinliği ve işaretolayları görüntüler.

Zaman çizelgesinde, x ekseni zaman ve y ekseninde birkaç kanal vardır:

- Sistemdeki her disk sürücüsü için iki G/Ç kanalı, okumalar için bir kanal ve yazmak için bir kanal.
- İşlemdeki her iş parçacığı için bir kanal.
- İzde işaretleme olayları varsa işaretleyici kanalları. İşaretleyici kanalları başlangıçta bu olayları oluşturan iş parçacığı kanallarının altında görünür.
- GPU kanalları.

Başlangıçta, iş parçacıkları oluşturuldukları sıraya göre sıralanır, bu nedenle ana uygulama iş parçacığı önce. İş parçacıklarını **Yürütme**gibi başka bir ölçüte göre sıralamak için açılan alt ağ başına **sırala'da** başka bir seçenek seçin.

Zaman çizelgesi renkleri, belirli bir zamanda bir iş parçacığının durumunu gösterir. Yeşil segmentler yürütülür, kırmızı segmentler eşitleme için engellenir, sarı segmentler önlenir ve mor segmentler aygıt G/Ç'de devreye girer.

Daha fazla ayrıntı görüntülemek için yakınlaştırabilir veya daha uzun bir zaman aralığını görüntülemek için uzaklaştırabilirsiniz. Kategoriler, başlangıç saatleri, gecikmeler ve arama yığını durumları hakkında ayrıntılı bilgi almak için grafikteki segmentleri ve noktaları seçin.

Paralel döngüde veya eşzamanlı görevlerde yer alan iş parçacıkları arasındaki çalışma dengesini incelemek için zaman çizelgesini kullanın. Bir iş parçacığının tamamlanması diğerlerinden daha uzun sürüyorsa, iş dengesiz olabilir. İş parçacıklar arasında daha eşit bir şekilde dağıtarak uygulamanızın performansını artırabilirsiniz.

Bir anda yalnızca bir iş parçacığı yürütülüyorsa, uygulama sistemdeki eşzamanlılıktan tam olarak yararlanamayabilir. İş parçacıkları arasındaki bağımlılıkları ve engellenen ve engellenen iş parçacıkları arasındaki zamansal ilişkileri incelemek için zaman çizelgesi grafiğini kullanabilirsiniz. İş parçacıklarını yeniden düzenlemek için bir iş parçacığı seçin ve ardından araç çubuğundaki yukarı veya aşağı simgesini seçin.

İstatistikleri alakasız olduğundan ve raporları tıkadığından, iş yapmayan veya tamamen engellenen iş parçacıklarını gizleyebilirsiniz. Adlarını seçip ardından **seçili iş parçacıklarını gizle** veya araç çubuğundaki **seçili iş parçacıkları simgeleri dışında tümünü gizle'yi** seçerek iş parçacıklarını gizleyin. Gizleyecek iş parçacıklarını tanımlamak için sol alttaki **İş Parçacığı Özeti** bağlantısını seçin. İş Parçacığı **Özeti** grafiğinde etkinliği olmayan iş parçacıklarını gizleyebilirsiniz.

### <a name="thread-execution-details"></a>İş parçacığı yürütme ayrıntıları
Yürütme kesimi hakkında daha ayrıntılı bilgi almak için zaman çizelgesinin yeşil kesiminde bir nokta seçin. EşzamanlıLık Görselleştiricisi seçili noktanın üzerinde siyah bir basamak görüntüler ve çağrı yığınını alt bölmenin **Geçerli** sekmesinde gösterir. Yürütme segmentinde birden çok nokta seçebilirsiniz.

>[!NOTE]
>Eşpara Birimi Görselleştiricisi, kesimin süresi bir milisaniyeden azsa, yürütme segmentindeki bir seçimi çözemeyebilir.

Şu anda seçili zaman aralığındaki tüm gizli olmayan iş parçacıkları için yürütme profili almak için sol alttaki göstergede **Yürütme'yi** seçin.

### <a name="thread-blocking-details"></a>İş parçacığı engelleme ayrıntıları
İş parçacığındaki belirli bir bölge hakkında bilgi almak için, bir araç ipucunu görüntülemek için zaman çizelgesinde o bölgenin üzerine gidin. Araç ipucu, kategori, başlangıç saati ve gecikme gibi bilgilere sahiptir. Arama yığınını bu noktada, alt bölmenin **Geçerli** sekmesinde görüntülemek için bölgeyi seçin. Bölmede ayrıca kategori, gecikme, varsa API'yi engelleme ve varsa iş parçacığının engelini kaldırma da gösterilmektedir. Arama yığınını inceleyerek, iş parçacığı engelleme olaylarının altında yatan nedenleri belirleyebilirsiniz.

Yürütme yolunun birkaç engelleme olayı olabilir. Bunları kategoriyi engelleyerek incelemek ve sorunlu alanları daha hızlı bulmak için soldaki göstergede bir engelleme kategorisi seçin.

### <a name="dependencies-between-threads"></a>İş parçacıkları arasındaki bağımlılıklar
Eşzamanlılık Görselleştiricisi iş parçacıkları arasındaki bağımlılıkları gösterir, böylece engellenen bir iş parçacığının ne yapmaya çalıştığını ve diğer iş parçacığının yürütmeyi etkinleştirdi.

Hangi iş parçacığının başka bir iş parçacığının engelini kaldırttıklarını belirlemek için, zaman çizelgesindeki engelleme bölümünü seçin. Eşzamanlılık Görselleştiricisi engellemeyi kaldırma iş parçacığı belirleyebiliyorsa, engellemeyi kaldırma iş parçacığı ile engelleme kesimini izleyen yürütme kesimi arasında bir çizgi çizer. İlgili çağrı yığınını görmek için alt bölmedeki **Engeli Kaldırma Yığını** sekmesini seçin.

## <a name="profile-reports"></a>Profil raporları
Zaman çizelgesi grafiğinin altında **Profil Raporu**, **Geçerli**ve **Engeli Kaldırma Yığını** rapor sekmelerinin yer alan bir bölme bulunur. Zaman çizelgesi ve iş parçacığı seçimlerini değiştirindedikçe raporlar otomatik olarak güncellenir. Büyük izlemeler için, güncelleştirmeler hesaplanırken raporlar bölmesi geçici olarak kullanılamayabilir.

### <a name="profile-report-tab"></a>Profil Raporu sekmesi

**Profil Raporu'nun** iki filtresi vardır:

- Az zaman harcanan çağrı ağacı girişlerini filtrelemek için, **alandaki Gürültü azaltmada** yüzde 0 ile 99 arasında bir filtre değeri yazın. Varsayılan değer yüzde 2'dir.
- Yalnızca kodunuz için arama ağaçlarını görüntülemek için **Yalnızca Kodum** onay kutusunu seçin. Tüm arama ağaçlarını görüntülemek için onay kutusunu temizleyin.

**Profil Raporu** sekmesi, göstergedeki kategorilere ve bağlantılara ait raporları gösterir. Bir raporu görüntülemek için soldaki girişlerden birini seçin:

- **Yürütme** **Yürütme** raporu, uygulamanın yürütmede harcadığı sürenin dökümünü gösterir.

  Yürütme süresinin harcandıği kod satırını bulmak için arama ağacını genişletin ve çağrı ağacı girişi için kısayol menüsünde **Kaynak Görüntüle** veya **Arama Sitelerini Görüntüle'yi**seçin. **View Kaynak,** yürütülen kod satırını bulur. **Çağrı Sitelerini Görüntüle,** çalıştırılan satırı çağıran kod satırını bulur. Yalnızca bir arama sitesi satırı varsa, kodu vurgulanır. Birden çok arama sitesi varsa, iletişim kutusunda istediğinizi seçin ve ardından **kaynağa git'i**seçin. Çoğu örnek, en çok zaman veya her ikisine sahip arama sitesini bulmak genellikle en kullanışlıdır. Daha fazla bilgi için [Yürütme profil raporuna](../profiling/execution-profile-report.md)bakın.

- **Eşitleme** **Eşitleme** raporu, her çağrı yığınının toplam engelleme süreleri ile birlikte eşitleme bloklarından sorumlu çağrıları gösterir. Daha fazla bilgi için [Eşitleme süresine](../profiling/synchronization-time.md)bakın.

- **I/O** **G/Ç** raporu, her çağrı yığınının toplam engelleme süreleri ile birlikte G/Ç bloklarından sorumlu çağrıları gösterir. Daha fazla bilgi için [G/Ç saati (İş parçacığı görünümü)](../profiling/i-o-time-threads-view.md)konusuna bakın.

- **Uyku** **Uyku** raporu, her çağrı yığınının toplam engelleme süreleri ile birlikte uyku bloklarından sorumlu çağrıları gösterir. Daha fazla bilgi için [Uyku süresine](../profiling/sleep-time.md)bakın.

- **Bellek Yönetimi** **Bellek Yönetimi** raporu, bellek yönetimi bloklarının oluştuğu çağrıları ve her çağrı yığınının toplam engelleme sürelerini gösterir. Aşırı sayfalama veya çöp toplama sorunları olan alanları tanımlamak için bu bilgileri kullanın.  Daha fazla bilgi için [Bellek yönetimi süresine](../profiling/memory-management-time.md)bakın.

- **Preemption** **Preemption** raporu, sistemdeki işlemlerin geçerli işlemi önleyen yeri ve geçerli işlemdeki iş parçacıklarının yerini alan tek tek iş parçacıklarını gösterir. Bu bilgileri, önalımdan en çok sorumlu olan işlemleri ve iş parçacıklarını tanımlamak için kullanabilirsiniz. Daha fazla bilgi için [Preemption süresine](../profiling/preemption-time.md)bakın.

- **UI İşleme** **UI İşleme** raporu, her çağrı yığınının toplam engelleme süreleri ile birlikte UI işleme bloklarından sorumlu çağrıları gösterir. Daha fazla bilgi için [Kullanıcı Arabirimi işleme süresine](../profiling/ui-processing-time.md)bakın.

- **İş Parçacığı Başına Özeti** Şu anda seçili zaman aralığının iş parçacığı durumunu gösteren bir grafik görüntülemek için **İş Parçacığı Başına Özeti'ni** seçin. Renk kodlu sütunlar, her iş parçacığının çalıştır, engellenmiş, G/Ç ve diğer durumlarda harcanan toplam süreyi gösterir. İş parçacıkları alt kısmında etiketlenir. Zaman çizelgesi grafiğinde yakınlaştırma düzeyini ayarladığınızda, bu grafik otomatik olarak güncellenir.

  Bazı yakınlaştırma düzeylerinde, bazı iş parçacıkları grafikte görünmeyebilir. Bu durumda, elipsler (**...**) sağda görünür. İstediğiniz iş parçacığı görünmüyorsa, diğer iş parçacıklarını gizleyebilirsiniz. Daha fazla bilgi için iş [parçacığı başına özet raporuna](../profiling/per-thread-summary-report.md)bakın.

- **Disk İşlemleri** Geçerli işlem için disk G/Ç'de yer alan işlemleri ve iş parçacıklarını, dokundukları dosyaları (örneğin, yükledikleri DL'ler), kaç bayt okuduklarını ve diğer bilgileri göstermek için **Disk İşlemleri'ni** seçin. Bu raporu, yürütme sırasında dosyalara erişmek için harcanan zamanı, özellikle de işleminiz I/O bağlı gibi görünüyorsa değerlendirmek için kullanabilirsiniz. Daha fazla bilgi için [Bkz. Disk işlemleri raporu.](../profiling/disk-operations-report-threads-view.md)

### <a name="current-tab"></a>Geçerli sekme
Bu sekme, zaman çizelgesi grafiğinde iş parçacığı segmentinde seçili bir noktanın çağrı yığınını gösterir. Arama yığınları yalnızca uygulamanızla ilgili etkinliği göstermek için kırpılır.

### <a name="unblocking-stack-tab"></a>Yığın sekmesinin engelini kaldırma
Bu sekme, seçili iş parçacığının ve engellemeyi kaldırma çağrısı yığınının engelini kaldıran iş parçacığının olduğunu gösterir.

## <a name="see-also"></a>Ayrıca bkz.
- [Eşzamanlılık görselleştiricisi](../profiling/concurrency-visualizer.md)
