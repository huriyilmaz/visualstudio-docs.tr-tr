---
title: Performans profil oluşturucusu 'nda bellek kullanımını analiz etme
description: uygulamanızın bellek kullanımını izlemek için Visual Studio performans Profiler 'daki hata ayıklayıcı olmadan bellek kullanımı aracını nasıl kullanacağınızı öğrenin.
ms.custom: ''
ms.date: 04/02/2020
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
ms.openlocfilehash: 61f0e4a2613a8ccf66c0f5205d730a38264d8e3c
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126626900"
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

   ![Bellek kullanımı Tanılama oturumu başlatma](../profiling/media/memuse_start_diagnosticssession.png "Bellek kullanımı Tanılama oturumu başlatma")

### <a name="monitor-memory-use"></a>Bellek kullanımını izleme

Bir Tanılama oturumu başlattığınızda, uygulamanız başlar ve **Tanılama araçları** penceresi, uygulamanızın bellek kullanımı için bir zaman çizelgesi grafiği görüntüler.

![Visual Studio performans Profiler 'daki Tanılama Araçları penceresinin ekran görüntüsü, uygulamanın bellek kullanımı için bir zaman çizelgesi grafiği gösterir.](../profiling/media/memuse__reportoverview.png "MEMUSE__ReportOverview")

Zaman çizelgesi grafiği, uygulamanın çalıştırıldığı şekilde bellek dalgalanmalarını gösterir. Grafikteki ani artışlar genellikle bazı kodların veri toplamasını veya oluşturmasını ve işlem tamamlandığında bu dosyayı atmaya işaret ediyor. Büyük ani artışlar, iyileştirebilecek olan bölgeleri gösterir. Daha fazla sorun, yetersiz bellek kullanımı veya hatta bellek sızıntısı belirtebileceğinden, döndürülmemiş bellek tüketimine sahiptir.

### <a name="take-snapshots-of-app-memory-states"></a>Uygulama belleği durumlarının anlık görüntülerini al

Bir uygulama çok sayıda nesne kullanır ve analizinizi bir senaryoya göre yoğunlaşmak isteyebilirsiniz. Ya da araştırmak için bellek sorunları bulabilirsiniz. Bellek kullanımını belirli bir süre içinde yakalamak için bir Tanılama oturumu sırasında anlık görüntü alabilirsiniz. Bir bellek sorunu görüntülenmeden önce bir uygulamanın temel anlık görüntüsünü almak ve bu senaryoyu tekrarlamanız durumunda sorunun ilk oluşumunda daha sonra başka bir anlık görüntü sağlamak iyi bir fikir olabilir.

Anlık görüntü toplamak için bellek verilerini yakalamak istediğinizde **anlık görüntü al** ' ı seçin.

### <a name="close-the-diagnostic-session"></a><a name="BKMK_Close_a_monitoring_session"></a> Tanılama oturumunu kapat

Bir rapor oluşturmadan izleme oturumunu durdurmak için, yalnızca tanılama penceresini kapatmanız yeterlidir. Anlık görüntü toplamayı bitirdiğinizde rapor oluşturmak için, **toplamayı durdur**' u seçin.

![Toplamayı durdur](../profiling/media/memuse__stopcollection.png "Toplamayı durdur")

## <a name="memory-usage-reports"></a>Bellek kullanım raporları

Veri toplamayı durdurduktan sonra, **bellek kullanımı** Aracı uygulamayı durdurur ve **bellek kullanımı** genel bakış sayfasını görüntüler.

![Visual Studio performans Profiler 'daki bellek kullanımı aracındaki, bellek kullanımı grafiği ve iki anlık görüntü bölmesi gösteren genel bakış sayfasının ekran görüntüsü.](../profiling/media/memuse__reportoverview1.png "Bellek kullanımına genel bakış sayfası")

### <a name="memory-usage-snapshots"></a><a name="BKMK_Memory_Usage_snapshot_views"></a> Bellek kullanımı anlık görüntüleri

**Anlık** görüntü bölmelerinde bulunan sayılar, her anlık görüntü alındığı sırada bellekteki baytları ve nesneleri ve anlık görüntü ile bir önceki arasındaki farkı gösterir.

numaralar, yeni Visual Studio windows 'da ayrıntılı **bellek kullanımı** rapor görünümlerini açan bağlantılardır. [Anlık görüntü ayrıntıları raporu](#snapshot-details-reports) , bir anlık görüntüdeki türleri ve örnekleri gösterir. [Anlık görüntü farkı (fark) raporu](#snapshot-difference-diff-reports) , iki anlık görüntüdeki türleri ve örnekleri karşılaştırır.

  ![Anlık görüntü görünümü bağlantıları](../profiling/media/memuse__snapshotview_numbered.png "Anlık görüntü görünümü bağlantıları")

|Görüntü|Description|
|-|-|
|![1. Adım](../profiling/media/procguid_1.png "ProcGuid_1")|Anlık görüntü çekilirken bellekteki toplam bayt sayısı.<br /><br /> Tür örneklerinin toplam boyutuna göre sıralanmış bir anlık görüntü ayrıntıları raporu göstermek için bu bağlantıyı seçin.|
|![2. Adım](../profiling/media/procguid_2.png "ProcGuid_2")|Anlık görüntü çekilirken bellekteki toplam nesne sayısı.<br /><br /> Bu bağlantıyı, türlerin örnek sayısına göre sıralanmış bir anlık görüntü ayrıntıları raporu göstermek için seçin.|
|![3. Adım](../profiling/media/procguid_3.png "ProcGuid_3")|Bu anlık görüntüdeki bellek nesnelerinin toplam boyutu ve önceki anlık görüntü arasındaki fark. <br /><br /> Pozitif bir sayı, bu anlık görüntünün bellek boyutunun öncekinden daha büyük olduğu anlamına gelir ve negatif bir sayı ise boyutun daha küçük olduğu anlamına gelir. **Taban çizgisi** , bir anlık görüntünün bir tanılama oturumunda ilki olduğu anlamına gelir. **Fark olmaması** , farkın sıfır olduğu anlamına gelir.<br /><br /> Bu bağlantıyı, türlerin örneklerinin toplam boyutundaki farka göre sıralanmış bir anlık görüntü fark raporu göstermek için seçin.|
|![4. adım](../profiling/media/procguid_4.png "ProcGuid_4")|Bu anlık görüntüdeki toplam bellek nesnesi sayısı ve önceki anlık görüntü arasındaki fark.<br /><br /> Bu bağlantıyı, türlerin örneklerinin toplam sayısıyla aradaki bir anlık görüntü fark raporu göstermek için seçin.|

## <a name="memory-usage-snapshot-reports"></a>Bellek kullanımı anlık görüntü raporları

<a name="BKMK_Snapshot_report_trees"></a>**Bellek kullanımı** Genel Bakış sayfasında anlık görüntü bağlantılarından birini seçtiğinizde, yeni sayfada bir anlık görüntü raporu açılır.

![Bellek kullanımı anlık görüntü raporu](../profiling/media/memuse_snapshotreport_all.png "Bellek kullanımı anlık görüntü raporu")

Anlık görüntü raporunda, **nesne türü** girdilerini genişleterek alt girdileri görüntüleyebilirsiniz. Örnek adları, bellek kullanımı aracı tarafından oluşturulan benzersiz kimliklerdir.

Bir **nesne türü** mavi ise, kaynak koddaki nesneye gitmek için, ayrı bir pencerede bunu seçebilirsiniz.

Kodunuzun içindeki katılımlarınızı belirleyemezseniz veya bu kodun, .NET, işletim sistemi ya da derleyici nesnelerinden oluşan türler olabilir. **Bellek kullanımı** Aracı, nesnelerinizin sahiplik zincirlerine dahil olmaları durumunda bu nesneleri görüntüler.

Anlık görüntü raporunda:

- **Yönetilen yığın** ağacı, rapordaki türleri ve örnekleri gösterir. Bir tür veya örnek seçildiğinde seçili öğe için kök ve **başvurulan nesne** ağaçlarına **yönelik yollar** görüntülenir.

- **Kök ağacına yönelik yollar** , bir türe veya örneğe başvuran nesne zincirini gösterir. .NET atık toplayıcısı, yalnızca tüm başvuruları serbest bırakıldığında bir nesne için belleği temizler.

- **Başvurulan türler** veya **başvurulan nesneler** ağacı, seçilen türün veya Örneğin başvurduğu nesneleri gösterir.

### <a name="report-tree-filters"></a><a name="BKMK_Report_tree_filters_"></a> Rapor ağacı filtreleri

Uygulamalarda birçok tür uygulama geliştiricilerine çok ilginç değildir. Anlık görüntü raporu filtreleri **yönetilen yığında** bu türlerin çoğunu ve kök ağaçlara **yolları** gizleyebilir.

![Sıralama ve filtreleme seçenekleri](../profiling/media/memuse_sortandfilter.png "MEMUSE_SortAndFilter")

- <a name="BKMK_Filter"></a> Bir ağacı tür adına göre filtrelemek için, **filtre** kutusuna adı girin. Filtre, büyük/küçük harfe duyarlı değildir ve tür adının herhangi bir bölümünde belirtilen dizeyi tanır.

- <a name="BKMK_Collapse_Small_Objects"></a>**Boyutu (bayt)** toplam belleğin yüzde 0,5 ' inden az olan türleri gizlemek için **filtre** açılan menüsünde **küçük nesneleri Daralt** ' ı seçin.

- <a name="BKMK_Just_My_Code"></a>Dış kod tarafından oluşturulan örneklerin çoğunu gizlemek için **filtre** açılan listesinde **yalnızca kendi kodum** seçin. Dış türler, işletim sistemi veya çerçeve bileşenlerine aittir veya derleyici tarafından oluşturulur.

## <a name="snapshot-details-reports"></a>Anlık görüntü ayrıntıları raporları

 Anlık görüntü ayrıntıları raporu, bir tanılama oturumundan bir anlık görüntüyü açıklar. Raporu açmak için bir anlık görüntü bölmesindeki boyut veya nesneler bağlantısını seçin.

 ![Anlık görüntü bölmesinde anlık görüntü raporuna bağlantılar](../profiling/media/memuse_snapshotview_snapshotdetailslinks.png "Anlık görüntü bölmesinde anlık görüntü raporuna bağlantılar")

Her iki bağlantı de aynı raporu açar. Tek fark, **yönetilen yığın** ağacının başlangıç sıralama sıraıdır. Boyut bağlantısı, raporu **kapsamlı boyut (bayt)** sütununa göre sıralar. Nesneler bağlantısı, raporu **say** sütununa göre sıralar. Sıralama sütununu veya sırayı rapor açıldıktan sonra değiştirebilirsiniz.

### <a name="managed-heap-tree-snapshot-details-reports"></a><a name="BKMK_Managed_Heap_tree__Snapshot_details_"></a> Yönetilen yığın ağacı (anlık görüntü ayrıntıları raporları)
 **Yönetilen yığın** ağacı bellekte tutulan nesne türlerini listeler. Türün en büyük on örneğini görüntülemek için bir tür adı genişletin, boyuta göre sıralanır. Seçili öğe için köke ve **başvurulan nesne** ağaçlarına **yönelik yolları** göstermek için bir tür veya örnek seçin.

 ![Yönetilen yığın ağacı](../profiling/media/memuse__snapshotdetails_managedheaptree.png "Yönetilen yığın ağacı")

Anlık görüntü ayrıntıları raporundaki **yönetilen yığın** ağacı aşağıdaki sütunlara sahiptir:

|Ad|Açıklama|
|-|-|
|**Nesne Türü**|Türün veya nesne örneğinin adı.|
|**Sayısı**|Türün nesne örneklerinin sayısı. **Bir**  örnek için sayı her zaman 1'dir.|
|**Boyut (Bayt)**|Bir tür için anlık görüntüdeki türün tüm örneklerinin boyutu, örneklerde yer alan nesnelerin boyutu kadardır.<br /><br /> Bir örnek için nesnenin boyutu, örnekte bulunan nesnelerin boyutu kadar küçük olur. |
|**Kapsayıcı Boyut (Bayt)**|Türün örneklerinin boyutu veya içerdiği nesnelerin boyutu da dahil olmak üzere tek bir örneğin boyutu.|
|**Modül**|nesnesini içeren modül.|

### <a name="paths-to-root-tree-snapshot-details-reports"></a><a name="BKMK_Paths_to_Root_tree__Snapshot_details_"></a> Kök ağacın yolları (Anlık görüntü ayrıntıları raporları)
Kök **ağacının Yolları,** bir türe veya örneke başvurulan nesnelerin zincirini gösterir. .NET çöp toplayıcısı, bir nesnenin belleğini yalnızca tüm başvurular serbest bırakıldıklarda temizler.

Kök ağacının **Yolları'na bir** tür için, başvurular içeren nesne sayısı Başvuru Sayısı **sütununda** görünür.

![Türler için Kök ağacın yolları](../profiling/media/memuse_snapshotdetails_type_pathstoroottree.png "Türler için kök ağacına yönelik yollar")

### <a name="referenced-types-or-referenced-objects-tree-snapshot-details-reports"></a><a name="BKMK_Referenced_Objects_tree__Snapshot_details_"></a> Başvurulan Türler veya Başvurulan Nesneler ağacı (Anlık görüntü ayrıntıları raporları)
Başvurulan **Türler** **veya Başvurulan Nesneler** ağacı, seçilen türün veya örneğin başvuran nesneleri gösterir.

![Örnekler için Başvurulan Nesneler ağacı](../profiling/media/memuse_snapshotdetails_referencedobjects_instance.png "Örnekler için başvurulan nesneler ağacı")

Anlık **görüntü ayrıntıları raporunda** Başvurulan Türler ağacı aşağıdaki sütunlara sahip olur. Başvurulan **Nesneler ağacında** Başvuru Sayısı **sütunu** yok.

|Ad|Açıklama|
|-|-|
|**Nesne Türü** veya **Örneği**|Türün veya örneğin adı.|
|**Başvuru Sayısı**|Türler için, türün nesne örneklerinin sayısı.|
|**Boyut (Bayt)**|Bir tür için, türün tüm örneklerinin boyutu, türün içerdiği nesnelerin boyutu kadardır.<br /><br /> Bir örnek için nesnenin boyutu, nesnesinde yer alan nesnelerin boyutu kadardır.|
|**Kapsayıcı Boyut (Bayt)**|Tür örneklerinin toplam boyutu veya içerdiği nesnelerin boyutu da dahil olmak üzere örneğin boyutu.|
|**Modül**|nesnesini içeren modül.|

## <a name="snapshot-difference-diff-reports"></a>Anlık görüntü farkı (fark) raporları

Anlık görüntü farkı (fark) raporu, birincil anlık görüntü ile önceki anlık görüntü arasındaki değişiklikleri gösterir. Fark raporunu açmak için anlık görüntü bölmesindeki fark bağlantılarından birini seçin.

Her iki bağlantı da aynı raporu açar. Tek fark, raporda Yönetilen Yığın **ağacının başlangıç** sıralama düzenidir. Boyut bağlantısı, raporu Kapsayıcı Boyut Fark **(Bayt) sütununa göre** sıralar. Nesneler bağlantısı, raporu Count **Diff sütununa göre** sıralar. Rapor açıldıktan sonra sıralama sütununu veya sıralamayı değiştirebilirsiniz.

 ![Anlık görüntü bölmesindeki fark raporunun bağlantıları](../profiling/media/memuse_snapshotview_snapshotdifflinks.png "Bir anlık görüntü bölmesindeki fark raporuna bağlantılar")

### <a name="managed-heap-tree-snapshot-diff-reports"></a><a name="BKMK_Managed_Heap_tree__Snapshot_diff_"></a> Yönetilen Yığın ağacı (Anlık görüntü fark raporları)

 Yönetilen **Yığın** ağacı, bellekte tutulan nesne türlerini listeler. Türün boyuta göre sıralanmış en büyük on örneğini görüntülemek için bir tür adını genişletabilirsiniz. Seçilen öğenin Kök ve **Başvurulan Nesneler ağaç** yollarını görüntülemek için **bir** tür veya örnek seçin.

 ![Fark raporu türü için Yönetilen Yığın ağacı](../profiling/media/memuse_snapshotdiff_type_heap.png "Fark raporundaki bir tür için yönetilen yığın ağacı")

Anlık **görüntü fark** raporuna sahip Yönetilen Yığın ağacı aşağıdaki sütunlara sahip:

|Ad|Açıklama|
|-|-|
|**Nesne Türü**|Türün veya nesne örneğinin adı.|
|**Sayısı**|Birincil anlık görüntüde bir türün örnek sayısı. **Bir** örnek için sayı her zaman 1'dir.|
|**Fark Sayısı**|Bir tür için, birincil anlık görüntü ile önceki anlık görüntü arasındaki türün örnek sayısı arasındaki fark. Alanı bir örnek için boştur.|
|**Boyut (Bayt)**|Birincil anlık görüntüdeki nesnelerin boyutu, nesnelerdeki nesnelerin boyutunun altındadır. Bir tür için **Boyut (Bayt)** ve **Kapsayıcı Boyut (Bayt)** tür örneklerinin boyutlarının toplamlarıdır.|
|**Toplam Boyut Fark (Bayt)**|Bir tür için, birincil anlık görüntü ile önceki anlık görüntü arasındaki tür örneklerinin toplam boyutu arasındaki fark, örneklerde nesnelerin boyutunun altındadır. Alanı bir örnek için boştur.|
|**Kapsayıcı Boyut (Bayt)**|Nesnelerdeki nesnelerin boyutu da dahil olmak üzere birincil anlık görüntüdeki nesnelerin boyutu.|
|**Kapsayıcı Boyut Farkları (Bayt)**|Bir tür için, nesnelerdeki nesnelerin boyutu da dahil olmak üzere birincil anlık görüntü ile önceki anlık görüntü arasındaki türün tüm örneklerinin boyutu arasındaki fark. Alanı bir örnek için boştur.|
|**Modül**|nesnesini içeren modül.|

### <a name="paths-to-root-tree-snapshot-diff-reports"></a><a name="BKMK_Paths_to_Root_tree__Snapshot_diff_"></a> Kök ağacın yolları (Anlık görüntü fark raporları)

Kök **ağacının Yolları,** bir türe veya örneke başvurulan nesnelerin zincirini gösterir. .NET çöp toplayıcısı, bir nesnenin belleğini yalnızca tüm başvurular serbest bırakıldıklarda temizler.

Kök ağacının **Yolları'na bir** tür için, başvurular içeren nesne sayısı Başvuru Sayısı **sütununda** görünür. Önceki anlık görüntüdeki sayı farkı Başvuru Farkı **sütunundadır.**

 ![Fark raporunda Kök ağacın yolları](../profiling/media/memuse_snapshotdiff_pathstoroot_instance_all.png "Fark raporundaki kök ağacına yönelik yollar")

### <a name="referenced-types-or-referenced-objects-tree-snapshot-diff-reports"></a><a name="BKMK_Referenced_Objects_tree__Snapshot_diff_"></a> Başvurulan Türler veya Başvurulan Nesneler ağacı (Anlık görüntü fark raporları)

Başvurulan **Türler** **veya Başvurulan Nesneler** ağacı, seçilen türün veya örneğin başvuran nesneleri gösterir.

![Fark raporunda Başvurulan Türler](../profiling/media/memuse_snapshotdiff_referencedtypes.png "Fark raporundaki başvurulan türler")

Bir **anlık görüntü fark** raporunda Başvurulan Türler ağacı aşağıdaki sütunlara sahip olur. Başvurulan **Nesneler ağacında** Örnek, **Boyut** **(Bayt)**, Kapsayıcı **Boyut (Bayt)** ve Modül **sütunları** bulunur.

|Ad|Açıklama|
|-|-|
|**Nesne Türü** veya **Örneği**|Türün veya nesne örneğinin adı.|
|**Başvuru Sayısı**|Birincil anlık görüntüde bir türün örnek sayısı.|
|**Başvuru Sayısı Fark**|Bir tür için, birincil anlık görüntü ile önceki anlık görüntü arasındaki türün örnek sayısı arasındaki fark.|
|**Boyut (Bayt)**|Birincil anlık görüntüdeki nesnelerin boyutu, nesnelerdeki nesnelerin boyutunun altındadır. Bir tür için **Boyut (Bayt)** ve **Kapsayıcı Boyut (Bayt)** tür örneklerinin boyutlarının toplamlarıdır.|
|**Toplam Boyut Fark (Bayt)**|Bir tür için, birincil anlık görüntü ile önceki anlık görüntü arasındaki tür örneklerinin toplam boyutu arasındaki fark, örneklerde nesnelerin boyutunun altındadır. |
|**Kapsayıcı Boyut (Bayt)**|Nesnelerdeki nesnelerin boyutu da dahil olmak üzere birincil anlık görüntüdeki nesnelerin boyutu.|
|**Kapsayıcı Boyut Farkları (Bayt)**|Bir tür için, nesne içindeki nesnelerin boyutu dahil olmak üzere birincil anlık görüntü ve önceki anlık görüntü arasındaki türün tüm örneklerinin boyutuyla aradaki fark.|
|**Modül**|Nesneyi içeren modül.|

## <a name="see-also"></a>Ayrıca bkz.
- [JavaScript belleği](../profiling/javascript-memory.md)
- [Visual Studio profil oluşturma](../profiling/index.yml)
- [Profil oluşturma araçlarına ilk bakış](../profiling/profiling-feature-tour.md)
- [C++, C# ve Visual Basic kullanarak UWP uygulamaları için en iyi performans uygulamaları](/previous-versions/windows/apps/hh750313\(v\=win.10\))
- [Visual Studio yeni bellek kullanımı aracı ile bellek sorunlarını tanılama](https://devblogs.microsoft.com/devops/diagnosing-memory-issues-with-the-new-memory-usage-tool-in-visual-studio/)