---
title: Performans profil oluşturucusu 'nda bellek kullanımını analiz etme
description: uygulamanızın bellek kullanımını izlemek için Visual Studio performans Profiler 'daki hata ayıklayıcı olmadan bellek kullanımı aracını nasıl kullanacağınızı öğrenin.
ms.custom: devdivchpfy22
ms.date: 01/27/2022
ms.topic: how-to
dev_langs:
  - CSharp
  - VB
  - FSharp
  - C++
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
  - multiple
---
# <a name="analyze-memory-usage-without-debugging-in-the-performance-profiler"></a>Performans Profiler 'da hata ayıklama olmadan bellek kullanımını analiz etme

**Bellek kullanımı** Aracı, uygulamanızın bellek kullanımını izler. Visual Studio, etkin olarak geliştirmekte olduğunuz senaryoların gerçek zamanlı bellek efektlerini incelemek için aracı kullanabilirsiniz. Uygulamanın bellek durumlarının ayrıntılı anlık görüntülerini alabilir ve bellek sorunlarının ana nedenlerini bulmak için anlık görüntüleri karşılaştırabilirsiniz. bellek kullanımı aracı .net, ASP.NET, C++ veya karma mod (.net ve yerel) uygulamalarında desteklenir.

Bellek kullanımı aracı, [hata ayıklayıcı ile veya olmadan](../profiling/running-profiling-tools-with-or-without-the-debugger.md)çalıştırılabilir. bu makalede, sürüm derlemeleri için önerilen Visual Studio **performans Profiler**'da hata ayıklayıcı olmadan bellek kullanımı aracının nasıl kullanılacağını göstereceğiz.

## <a name="memory-usage-diagnostic-sessions"></a>Bellek kullanımı tanılama oturumları

**Bir bellek kullanımı Tanılama oturumu başlatmak için:**

1. Visual Studio bir proje açın.

   bellek kullanımı aracı .net, ASP.NET, C++ veya karma mod (.net ve yerel) uygulamalarını destekler.

1. hata ayıkla menüsünde, çözüm yapılandırmasını **yayınlama** olarak ayarlayın ve dağıtım hedefi olarak **yerel Windows hata ayıklayıcı** (veya **yerel makine**) öğesini seçin.

1. Menü çubuğunda, **Hata Ayıkla**  >  **performans profil oluşturucusu**' nu seçin.

1. **Kullanılabilir araçlar**' ın altında **bellek kullanımı**' nı seçin ve ardından **Başlat**' ı seçin.

   ![Bellek kullanımı Tanılama oturumu başlatma](../profiling/media/memory-usage-start-diagnostics-session.png "Bellek Kullanımı tanılama oturumu başlatma")

### <a name="monitor-memory-use"></a>Bellek kullanımını izleme

Bir Tanılama oturumu başlattığınızda, uygulamanız başlar ve **Tanılama araçları** penceresi, uygulamanızın bellek kullanımı için bir zaman çizelgesi grafiği görüntüler.

::: moniker range="<=vs-2019"
![Visual Studio performans Profiler 'daki Tanılama Araçları penceresinin ekran görüntüsü, uygulamanın bellek kullanımı için bir zaman çizelgesi grafiği gösterir.](../profiling/media/memory-usage-report-overview.png "Bellek Raporuna Genel Bakış")
::: moniker-end

::: moniker range="vs-2022"
![Visual Studio performans Profiler 'daki Tanılama Araçları penceresinin ekran görüntüsü, uygulamanın bellek kullanımı için bir zaman çizelgesi grafiği gösterir.](../profiling/media/memory-usage-report-overview-vs-2022.png "Bellek Kullanımı Raporuna Genel Bakış")
::: moniker-end

Zaman çizelgesi grafiği, uygulamanın çalıştırıldığı şekilde bellek dalgalanmalarını gösterir. Grafikteki ani artışlar genellikle bazı kodların veri toplamasını veya oluşturmasını ve işlem tamamlandığında bu dosyayı atmaya işaret ediyor. Büyük ani artışlar, iyileştirebileceğinizi gösterir. Ana sorun, döndürülmüyor bir bellek tüketimine sahiptir. Bu, yetersiz bellek kullanımı veya bellek sızıntısı olduğunu gösterebilir.

### <a name="take-snapshots-of-app-memory-states"></a>Uygulama belleği durumlarının anlık görüntülerini al

Bir uygulama çok sayıda nesne kullanır ve analizinizi bir senaryoya göre yoğunlaşmak isteyebilirsiniz. Ya da araştırmak için bellek sorunları bulabilirsiniz. Bellek kullanımını belirli bir süre içinde yakalamak için bir Tanılama oturumu sırasında anlık görüntü alabilirsiniz. Bir bellek sorunu görüntülenmeden önce bir uygulamanın temel anlık görüntüsünü almak iyi olur. Sorunun ilk oluşumdan sonra başka bir anlık görüntü alabilir ve senaryoyu tekrarlamanız için ek anlık görüntüler gerçekleştirebilirsiniz.

Anlık görüntü toplamak için bellek verilerini yakalamak istediğinizde **anlık görüntü al** ' ı seçin.

### <a name="close-the-diagnostic-session"></a><a name="BKMK_Close_a_monitoring_session"></a> Tanılama oturumunu kapat

Bir rapor oluşturmadan izleme oturumunu durdurmak için, yalnızca tanılama penceresini kapatmanız yeterlidir. Anlık görüntü toplamayı bitirdiğinizde rapor oluşturmak için, **toplamayı durdur**' u seçin.

![Toplamayı durdur](../profiling/media/memory-usage-stop-collection.png "Koleksiyonu Durdurma")

## <a name="memory-usage-reports"></a>Bellek kullanım raporları

Veri toplamayı durdurduktan sonra, **bellek kullanımı** Aracı uygulamayı durdurur ve **bellek kullanımı** genel bakış sayfasını görüntüler.

::: moniker range="<=vs-2019"
![Visual Studio performans Profiler 'daki bellek kullanımı aracındaki, bellek kullanımı grafiği ve iki anlık görüntü bölmesi gösteren genel bakış sayfasının ekran görüntüsü.](../profiling/media/memory-usage-report-overview-1.png "Bellek Kullanımına genel bakış sayfası")
::: moniker-end

::: moniker range="vs-2022"
![Visual Studio performans Profiler 'daki bellek kullanımı aracındaki, bellek kullanımı grafiği ve iki anlık görüntü bölmesi gösteren genel bakış sayfasının ekran görüntüsü.](../profiling/media/memory-usage-report-overview-1-vs-2022.png "Bellek Kullanımına genel bakış sayfası")
::: moniker-end

### <a name="memory-usage-snapshots"></a><a name="BKMK_Memory_Usage_snapshot_views"></a> Bellek kullanımı anlık görüntüleri

**Anlık** görüntü bölmelerinde bulunan sayılar, her anlık görüntü çekilirken bellekteki nesneleri ve baytları ve anlık görüntü ile bir önceki arasındaki farkı gösterir.

numaralar, yeni Visual Studio windows 'da ayrıntılı **bellek kullanımı** rapor görünümlerini açan bağlantılardır. [Anlık görüntü ayrıntıları raporu](#snapshot-details-reports) , bir anlık görüntüdeki türleri ve örnekleri gösterir. [Anlık görüntü farkı (fark) raporu](#snapshot-difference-diff-reports) , iki anlık görüntüdeki türleri ve örnekleri karşılaştırır.

::: moniker range="<=vs-2019"
  ![Anlık görüntü görünümü bağlantıları](../profiling/media/memory-usage-snapshot-view-numbered.png "Anlık görüntü görünümü bağlantıları")

|Görüntü|Description|
|-|-|
|![1. Adım](../profiling/media/process-guide-1.png "İşlem Kılavuzu-1")|Anlık görüntü çekilirken bellekteki toplam bayt sayısı. Tür örneklerinin toplam boyutuna göre sıralanmış bir anlık görüntü ayrıntıları raporu göstermek için bu bağlantıyı seçin.|
|![2. Adım](../profiling/media/process-guide-2.png "İşlem Kılavuzu-2")|Anlık görüntü çekilirken bellekteki toplam nesne sayısı. Bu bağlantıyı, türlerin örnek sayısına göre sıralanmış bir anlık görüntü ayrıntıları raporu göstermek için seçin.|
|![3. Adım](../profiling/media/process-guide-3.png "İşlem Kılavuzu-3")|Bu anlık görüntüdeki bellek nesnelerinin toplam boyutu ve önceki anlık görüntü arasındaki fark. Pozitif bir sayı, bu anlık görüntünün bellek boyutunun öncekinden daha büyük olduğu anlamına gelir ve negatif bir sayı ise boyutun daha küçük olduğu anlamına gelir. **Taban çizgisi** , bir anlık görüntünün bir tanılama oturumunda ilki olduğu anlamına gelir. **Fark olmaması** , farkın sıfır olduğu anlamına gelir. Bu bağlantıyı, türlerin örneklerinin toplam boyutundaki farka göre sıralanmış bir anlık görüntü fark raporu göstermek için seçin.|
|![4. adım](../profiling/media/process-guide-4.png "İşlem Kılavuzu-4")|Bu anlık görüntüdeki toplam bellek nesnesi sayısı ve önceki anlık görüntü arasındaki fark. Anlık görüntü fark raporu göstermek için bu bağlantıyı seçin. Bu, türlerin örneklerinin toplam sayısı arasındaki farka göre sıralanır.|
::: moniker-end

::: moniker range="vs-2022"
  ![Anlık görüntü görünümü bağlantıları](../profiling/media/memory-usage-snapshot-view-numbered-vs-2022.png "Anlık görüntü görünümü bağlantıları")

|Görüntü|Description|
|-|-|
|![1. Adım](../profiling/media/process-guide-1.png "İşlem Kılavuzu-1")|Anlık görüntü çekilirken bellekteki toplam nesne sayısı. Bu bağlantıyı, türlerin örnek sayısına göre sıralanmış bir anlık görüntü ayrıntıları raporu göstermek için seçin.|
|![2. Adım](../profiling/media/process-guide-2.png "İşlem Kılavuzu-2")|Bu anlık görüntüdeki toplam bellek nesnesi sayısı ve önceki anlık görüntü arasındaki fark. Bu bağlantıyı, türlerin örneklerinin toplam sayısıyla aradaki bir anlık görüntü fark raporu göstermek için seçin.|
|![3. Adım](../profiling/media/process-guide-3.png "İşlem Kılavuzu-3")|Anlık görüntü çekilirken bellekteki toplam bayt sayısı. Tür örneklerinin toplam boyutuna göre sıralanmış bir anlık görüntü ayrıntıları raporu göstermek için bu bağlantıyı seçin.|
|![4. adım](../profiling/media/process-guide-4.png "İşlem Kılavuzu-4")|Bu anlık görüntüdeki bellek nesnelerinin toplam boyutu ve önceki anlık görüntü arasındaki fark. Pozitif bir sayı, bu anlık görüntünün bellek boyutunun öncekinden daha büyük olduğu anlamına gelir ve negatif bir sayı ise boyutun daha küçük olduğu anlamına gelir. **Taban çizgisi** , bir anlık görüntünün bir tanılama oturumunda ilki olduğu anlamına gelir. **Fark olmaması** , farkın sıfır olduğu anlamına gelir. Bu bağlantıyı, türlerin örneklerinin toplam boyutundaki farka göre sıralanmış bir anlık görüntü fark raporu göstermek için seçin.|
::: moniker-end

## <a name="memory-usage-snapshot-reports"></a>Bellek kullanımı anlık görüntü raporları

<a name="BKMK_Snapshot_report_trees"></a>**Bellek kullanımı** Genel Bakış sayfasında anlık görüntü bağlantılarından birini seçtiğinizde, yeni sayfada bir anlık görüntü raporu açılır.

::: moniker range="<=vs-2019"
![Bellek kullanımı anlık görüntü raporu](../profiling/media/memory-usage-snapshot-report-all.png "Bellek Kullanımı anlık görüntü raporu")
::: moniker-end

::: moniker range="vs-2022"
![Bellek kullanımı anlık görüntü raporu](../profiling/media/memory-usage-snapshot-report-all-vs-2022.png "Bellek Kullanımı anlık görüntü raporu")
::: moniker-end

Bir **nesne türü** mavi ise, kaynak koddaki nesneye gitmek için, ayrı bir pencerede bunu seçebilirsiniz.

Kodunuzun içindeki katılımlarınızı belirleyemezseniz veya bu kodun, .NET, işletim sistemi ya da derleyici nesnelerinden oluşan türler olabilir. **Bellek kullanımı** Aracı, nesnelerinizin sahiplik zincirlerine dahil olmaları durumunda bu nesneleri görüntüler.

Anlık görüntü raporunda:

- **Yönetilen bellek** ağacı, rapordaki türleri ve örnekleri gösterir. Bir tür veya örnek seçildiğinde seçili öğe için kök ve **başvurulan nesne** ağaçlarına **yönelik yollar** görüntülenir.

- **Kök ağacına yönelik yollar** , bir türe veya örneğe başvuran nesne zincirini gösterir. .NET atık toplayıcısı, yalnızca tüm başvuruları serbest bırakıldığında bir nesne için belleği temizler.

- **Başvurulan türler** veya **başvurulan nesneler** ağacı, seçilen türün veya Örneğin başvurduğu nesneleri gösterir.

### <a name="report-tree-filters"></a><a name="BKMK_Report_tree_filters_"></a> Rapor ağacı filtreleri

Uygulamalarda birçok tür uygulama geliştiricisi için gerekli değildir. Anlık görüntü raporu filtreleri, **yönetilen bellekte** ve kök ağaçlara **yönelik yollarda** bu türlerin çoğunu gizleyebilir.

::: moniker range="<=vs-2019"
![Sıralama ve filtreleme seçenekleri](../profiling/media/memory-usage-sort-and-filter.png "Bellek Kullanımı Sıralama ve Filtreleme")
::: moniker-end

::: moniker range="vs-2022"
![Sıralama ve filtreleme seçenekleri](../profiling/media/memory-usage-sort-and-filter-vs-2022.png "Bellek kullanımı sıralama ve filtreleme")
::: moniker-end

- <a name="BKMK_Filter"></a> Bir ağacı tür adına göre filtrelemek için Filtre kutusuna **adı** girin. Filtre büyük/büyük/büyük harfe duyarlı değildir ve tür adının herhangi bir bölümünde belirtilen dizeyi tanır.

- <a name="BKMK_Collapse_Small_Objects"></a>Boyut **(Bayt) toplam belleğin** yüzde 0,5'inden küçük olan türleri gizlemek için Filtre açılan listesinde Küçük Nesneleri Daralt'ı seçin. 

- <a name="BKMK_Just_My_Code"></a> Dış **Yalnızca kendi kodum** **oluşturulan örneklerin** çoğunu gizlemek için Filtre açılan listesinden Filtre'yi seçin. Dış türler işletim sistemi veya çerçeve bileşenlerine aittir veya derleyici tarafından oluşturulur.

## <a name="snapshot-details-reports"></a>Anlık görüntü ayrıntıları raporları

 Anlık görüntü ayrıntıları raporu, tanılama oturumundan bir anlık görüntüyü açıklar. Raporu açmak için anlık görüntü bölmesindeki boyut veya nesneler bağlantısını seçin.

::: moniker range="<=vs-2019"
 ![Anlık görüntü bölmesindeki anlık görüntü raporuna bağlantılar](../profiling/media/memory-usage-snapshot-view-snapshot-details-links.png "Anlık görüntü bölmesindeki anlık görüntü raporuna bağlantılar")
::: moniker-end

::: moniker range="vs-2022"
 ![Anlık görüntü bölmesindeki anlık görüntü raporuna bağlantılar](../profiling/media/memory-usage-snapshot-view-snapshot-details-links-vs-2022.png "Anlık görüntü bölmesindeki anlık görüntü raporuna bağlantılar")
::: moniker-end

Her iki bağlantı da aynı raporu açar. Tek fark Yönetilen Bellek ağacının başlangıç sıralama **düzenidir** . Boyut bağlantısı, raporu Kapsayıcı Boyut **(Bayt) sütununa göre** sıralar. Nesneler bağlantısı, raporu Sayı sütununa **göre** sıralar. Rapor açıldıktan sonra sıralama sütununu veya sıralamayı değiştirebilirsiniz.

### <a name="managed-memory-tree-snapshot-details-reports"></a><a name="BKMK_Managed_Memory_tree__Snapshot_details_"></a> Yönetilen Bellek ağacı (Anlık görüntü ayrıntıları raporları)

 Yönetilen **Bellek** ağacı, bellekte tutulan nesne türlerini listeler. Türün boyuta göre sıralanmış en büyük 10 örneğini görüntülemek için bir tür adını genişletin. Seçilen öğenin Kök ve **Başvurulan Nesneler ağaç** yollarını **görüntülemek için** bir tür veya örnek seçin.

::: moniker range="<=vs-2019"
 ![Yönetilen Yığın ağacı](../profiling/media/memory-usage-snapshot-details-managed-heap-tree.png "Yönetilen Yığın ağacı")
::: moniker-end

::: moniker range="vs-2022"
 ![Yönetilen Bellek ağacı](../profiling/media/memory-usage-snapshot-details-managed-heap-tree-vs-2022.png "Yönetilen Bellek ağacı")
::: moniker-end

Anlık **görüntü ayrıntıları** raporuna ilişkin Yönetilen Bellek ağacı aşağıdaki sütunlara sahip:

|Adı|Açıklama|
|-|-|
|**Nesne Türü**|Türün veya nesne örneğinin adı.|
|**Sayısı**|Türün nesne örneklerinin sayısı. **Bir**  örnek için sayı her zaman 1'dir.|
|**Boyut (Bayt)**|Bir tür için anlık görüntüdeki türün tüm örneklerinin boyutu, örneklerde yer alan nesnelerin boyutu kadardır. Bir örnek için nesnenin boyutu, örnekte yer alan nesnelerin boyutu kadardır. |
|**Kapsayıcı Boyut (Bayt)**|Tür örneklerinin boyutu veya içerdiği nesnelerin boyutu da dahil olmak üzere tek bir örneğin boyutu.|
|**Modül**|nesnesini içeren modül.|

### <a name="paths-to-root-tree-snapshot-details-reports"></a><a name="BKMK_Paths_to_Root_tree__Snapshot_details_"></a> Kök ağacın yolları (Anlık görüntü ayrıntıları raporları)

Kök **ağacının Yolları,** bir türe veya örneke başvurulan nesnelerin zincirini gösterir. .NET çöp toplayıcısı yalnızca tüm başvurular serbest bırakıldıklarda bir nesnenin belleğini temizler.

Kök ağacının **Yolları'na bir** tür için, başvurular içeren nesne sayısı Başvuru Sayısı **sütununda** görünür.

::: moniker range="<=vs-2019"
![Türler için Kök ağacın yolları](../profiling/media/memory-usage-snapshot-details-type-paths-to-root-tree.png "Türler için Kök ağacın yolları")
::: moniker-end

::: moniker range="vs-2022"
![Türler için Kök ağacın yolları](../profiling/media/memory-usage-snapshot-details-type-paths-to-root-tree-vs-2022.png "Türler için Kök ağacın yolları")
::: moniker-end

### <a name="referenced-types-or-referenced-objects-tree-snapshot-details-reports"></a><a name="BKMK_Referenced_Objects_tree__Snapshot_details_"></a> Başvurulan Türler veya Başvurulan Nesneler ağacı (Anlık görüntü ayrıntıları raporları)

**Başvurulan Türler** **veya Başvurulan Nesneler** ağacı, seçilen türün veya örneğin başvuran nesneleri gösterir.

::: moniker range="<=vs-2019"
![Örnekler için Başvurulan Nesneler ağacı](../profiling/media/memory-usage-snapshot-details-referenced-objects-instance.png "Örnekler için Başvurulan Nesneler ağacı")
::: moniker-end

::: moniker range="vs-2022"
![Örnekler için Başvurulan Nesneler ağacı](../profiling/media/memory-usage-snapshot-details-referenced-objects-instance-vs-2022.png "Örnekler için Başvurulan Nesneler ağacı")
::: moniker-end

Anlık **görüntü ayrıntıları raporunda** Başvurulan Türler ağacı aşağıdaki sütunlara sahip olur. **Başvurulan Nesneler** ağacında Başvuru Sayısı **sütunu** yok.

|Adı|Açıklama|
|-|-|
|**Nesne Türü** veya **Örneği**|Türün veya örneğin adı.|
|**Başvuru Sayısı**|Türler için, türün nesne örneklerinin sayısı.|
|**Boyut (Bayt)**|Bir tür için, türün tüm örneklerinin boyutu, türün içerdiği nesnelerin boyutu daha azdır. Bir örnek için nesnenin boyutu, nesnesinde yer alan nesnelerin boyutu kadardır.|
|**Kapsayıcı Boyut (Bayt)**|Tür örneklerinin toplam boyutu veya içerdiği nesnelerin boyutu da dahil olmak üzere örneğin boyutu.|
|**Modül**|nesnesini içeren modül.|

## <a name="snapshot-difference-diff-reports"></a>Anlık görüntü farkı (fark) raporları

Anlık görüntü farkı (fark) raporu, birincil anlık görüntü ile önceki anlık görüntü arasındaki değişiklikleri gösterir. Fark raporunu açmak için anlık görüntü bölmesindeki fark bağlantılarından birini seçin.

Her iki bağlantı da aynı raporu açar. Tek fark, raporda Yönetilen Bellek **ağacının başlangıç** sıralama düzenidir. Boyut bağlantısı, raporu Kapsayıcı Boyut Fark **(Bayt) sütununa göre** sıralar. Nesneler bağlantısı, raporu Count **Diff sütununa göre** sıralar. Rapor açıldıktan sonra sıralama sütununu veya sıralamayı değiştirebilirsiniz.

::: moniker range="<=vs-2019"
 ![Anlık görüntü bölmesindeki fark raporunun bağlantıları](../profiling/media/memory-usage-snapshot-view-snapshot-diff-links.png "Anlık görüntü bölmesindeki fark raporunun bağlantıları")
::: moniker-end

::: moniker range="vs-2022"
 ![Anlık görüntü bölmesindeki fark raporunun bağlantıları](../profiling/media/memory-usage-snapshot-view-snapshot-diff-links-vs-2022.png "Anlık görüntü bölmesindeki fark raporunun bağlantıları")
::: moniker-end

### <a name="managed-memory-tree-snapshot-diff-reports"></a><a name="BKMK_Managed_Memory_tree__Snapshot_diff_"></a> Yönetilen Bellek ağacı (Anlık görüntü fark raporları)

 Yönetilen **Bellek** ağacı, bellekte tutulan nesne türlerini listeler. Türün boyuta göre sıralanmış en büyük 10 örneğini görüntülemek için bir tür adını genişletabilirsiniz. Seçilen öğenin Kök ve **Başvurulan Nesneler ağaç** yollarını **görüntülemek için** bir tür veya örnek seçin.

::: moniker range="<=vs-2019"
 ![Fark raporu türü için Yönetilen Yığın ağacı](../profiling/media/memory-usage-snapshot-diff-type-heap.png "Fark raporu türü için Yönetilen Yığın ağacı")
::: moniker-end

::: moniker range="vs-2022"
 ![Fark raporu türü için Yönetilen Bellek ağacı](../profiling/media/memory-usage-snapshot-diff-type-heap-vs-2022.png "Fark raporu türü için Yönetilen Bellek ağacı")
::: moniker-end

Anlık **görüntü fark** raporuna sahip Yönetilen Bellek ağacı aşağıdaki sütunlara sahip:

|Adı|Açıklama|
|-|-|
|**Nesne Türü**|Türün veya nesne örneğinin adı.|
|**Sayısı**|Birincil anlık görüntüde bir türün örnek sayısı. **Bir** örnek için sayı her zaman 1'dir.|
|**Count Diff**|Bir tür için, birincil anlık görüntü ile önceki anlık görüntü arasındaki türün örnek sayısı arasındaki fark. Alanı bir örnek için boştur.|
|**Boyut (Bayt)**|Birincil anlık görüntüdeki nesnelerin boyutu, nesnelerdeki nesnelerin boyutunun altındadır. Bir tür için **Boyut (Bayt)** ve **Kapsayıcı Boyut (Bayt)** tür örneklerinin boyutlarının toplamlarıdır.|
|**Toplam Boyut Fark (Bayt)**|Bir tür için, birincil anlık görüntü ile önceki anlık görüntü arasındaki tür örneklerinin toplam boyutu arasındaki fark, örneklerde nesnelerin boyutunun altındadır. Alanı bir örnek için boştur.|
|**Kapsayıcı Boyut (Bayt)**|Nesnelerdeki nesnelerin boyutu da dahil olmak üzere birincil anlık görüntüdeki nesnelerin boyutu.|
|**Kapsayıcı Boyut Farkları (Bayt)**|Bir tür için, nesnelerdeki nesnelerin boyutu da dahil olmak üzere birincil anlık görüntü ile önceki anlık görüntü arasındaki türün tüm örneklerinin boyutu arasındaki fark. Alanı bir örnek için boştur.|
|**Modül**|nesnesini içeren modül.|

### <a name="paths-to-root-tree-snapshot-diff-reports"></a><a name="BKMK_Paths_to_Root_tree__Snapshot_diff_"></a> Kök ağacın yolları (Anlık görüntü fark raporları)

Kök **ağacının Yolları,** bir türe veya örneke başvurulan nesnelerin zincirini gösterir. .NET çöp toplayıcısı yalnızca tüm başvurular serbest bırakıldıklarda bir nesnenin belleğini temizler.

Kök ağacının **Yolları'na bir** tür için, başvurular içeren nesne sayısı Başvuru Sayısı **sütununda** görünür. Önceki anlık görüntüdeki sayı farkı Başvuru Farkı **sütunundadır** .

::: moniker range="<=vs-2019"
 ![Fark raporunda Kök ağacın yolları](../profiling/media/memory-usage-snapshot-diff-paths-to-root-instance-all.png "Fark raporunda Kök ağacın yolları")
::: moniker-end

::: moniker range="vs-2022"
 ![Fark raporunda Kök ağacın yolları](../profiling/media/memory-usage-snapshot-diff-paths-to-root-instance-all-vs-2022.png "Fark raporunda Kök ağacın yolları")
::: moniker-end

### <a name="referenced-types-or-referenced-objects-tree-snapshot-diff-reports"></a><a name="BKMK_Referenced_Objects_tree__Snapshot_diff_"></a> Başvurulan Türler veya Başvurulan Nesneler ağacı (Anlık görüntü fark raporları)

**Başvurulan Türler** **veya Başvurulan Nesneler** ağacı, seçilen türün veya örneğin başvuran nesneleri gösterir.

::: moniker range="<=vs-2019"
![Fark raporunda Başvurulan Türler](../profiling/media/memory-usage-snapshot-diff-referenced-types.png "Fark raporunda Başvurulan Türler")
::: moniker-end

::: moniker range="vs-2022"
![Fark raporunda Başvurulan Türler](../profiling/media/memory-usage-snapshot-diff-referenced-types-vs-2022.png "Fark raporunda Başvurulan Türler")
::: moniker-end

Bir **anlık görüntü fark** raporunda Başvurulan Türler ağacı aşağıdaki sütunlara sahip olur. **Başvurulan Nesneler ağacında** Örnek, **Boyut** **(Bayt)**, Kapsayıcı **Boyut (Bayt) ve** Modül **sütunları** bulunur.

|Adı|Açıklama|
|-|-|
|**Nesne Türü** veya **Örneği**|Türün veya nesne örneğinin adı.|
|**Başvuru Sayısı**|Birincil anlık görüntüde bir türün örnek sayısı.|
|**Başvuru Sayısı Fark**|Bir tür için, birincil anlık görüntü ile önceki anlık görüntü arasındaki türün örnek sayısı arasındaki fark.|
|**Boyut (Bayt)**|Birincil anlık görüntüdeki nesnelerin boyutu, nesnelerdeki nesnelerin boyutunun altındadır. Bir tür için **Boyut (Bayt)** ve **Kapsayıcı Boyut (Bayt)** tür örneklerinin boyutlarının toplamlarıdır.|
|**Toplam Boyut Fark (Bayt)**|Bir tür için, birincil anlık görüntü ile önceki anlık görüntü arasındaki tür örneklerinin toplam boyutu arasındaki fark, örneklerde nesnelerin boyutunun altındadır. |
|**Kapsayıcı Boyut (Bayt)**|Nesnelerdeki nesnelerin boyutu da dahil olmak üzere birincil anlık görüntüdeki nesnelerin boyutu.|
|**Kapsayıcı Boyut Farkları (Bayt)**|Bir tür için, nesnelerdeki nesnelerin boyutu da dahil olmak üzere birincil anlık görüntü ile önceki anlık görüntü arasındaki türün tüm örneklerinin boyutu arasındaki fark.|
|**Modül**|nesnesini içeren modül.|

## <a name="see-also"></a>Ayrıca bkz.

- [JavaScript belleği](../profiling/javascript-memory.md)
- [Visual Studio'da profil oluşturma](../profiling/index.yml)
- [Profil oluşturma araçlarına ilk bakış](../profiling/profiling-feature-tour.md)
- [C++, C# ve Visual Basic kullanan UWP uygulamaları için performansa yönelik en iyi Visual Basic](/previous-versions/windows/apps/hh750313\(v\=win.10\))
- [Visual Studio'de yeni Bellek Kullanımı aracıyla ilgili bellek Visual Studio](https://devblogs.microsoft.com/devops/diagnosing-memory-issues-with-the-new-memory-usage-tool-in-visual-studio/)
