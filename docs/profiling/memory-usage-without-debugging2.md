---
title: Bellek kullanımını analiz Performans Profili Oluşturucu
description: Uygulamanın bellek kullanımını izlemek için bellek kullanımı aracını Visual Studio Performans Profili Oluşturucu hata ayıklayıcısı olmadan kullanmayı öğrenin.
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
ms.openlocfilehash: f57c8a77872d38400bb45e0d8c9136869b8eefa714c01ea4c3b0a2f4aadb578c
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121442436"
---
# <a name="analyze-memory-usage-without-debugging-in-the-performance-profiler"></a>Bellek kullanımını hata ayıklama olmadan analiz Performans Profili Oluşturucu

Bellek **Kullanımı aracı,** uygulamanın bellek kullanımını izler. Bu aracı kullanarak etkin bir şekilde geliştirmeniz gereken senaryoların gerçek zamanlı bellek etkilerini Visual Studio. Uygulamanın bellek durumlarının ayrıntılı anlık görüntülerini alıp anlık görüntüleri karşılaştırarak bellek sorunlarının kök nedenlerini bulabilirsiniz. Bellek Kullanımı aracı .NET, ASP.NET, C++ veya karma mod (.NET ve yerel) uygulamalarda de destekler.

Bellek Kullanımı aracı hata [ayıklayıcı ile veya hata ayıklayıcı olmadan çalışmasına neden olabilir.](../profiling/running-profiling-tools-with-or-without-the-debugger.md) Bu makalede, sürüm derlemeleri için önerilen bellek kullanımı aracının Visual Studio **Performans Profili Oluşturucu** aracında hata ayıklayıcı olmadan nasıl kullanabileceğiniz açıklanmıştır.

## <a name="memory-usage-diagnostic-sessions"></a>Bellek Kullanımı tanılama oturumları

**Bellek Kullanımı tanılama oturumu başlatmak için:**

1. Bir projeyi Visual Studio.

   Bellek Kullanımı aracı .NET, ASP.NET, C++ veya karma mod (.NET ve yerel) uygulamalarını destekler.

1. Hata Ayıkla menüsünde çözüm yapılandırmasını  Yayınla olarak ayarlayın ve dağıtım hedefi **Windows** Hata Ayıklayıcısı (veya **Yerel** Makine) seçeneğini belirleyin.

1. Menü çubuğunda Hata **ayıkla'Performans Profili Oluşturucu.**  >  

1. Kullanılabilir **Araçlar'ın** altında Bellek **Kullanımı'ı ve** ardından Başlat'ı **seçin.**

   ![Bellek Kullanımı tanılama oturumu başlatma](../profiling/media/memuse_start_diagnosticssession.png "Bellek Kullanımı tanılama oturumu başlatma")

### <a name="monitor-memory-use"></a>Bellek kullanımını izleme

Bir tanılama oturumu başlatıldığında, uygulama başlatılır ve **Tanılama Araçları** zaman çizelgesi grafiğini gösterir.

![Uygulamanın bellek Tanılama Araçları zaman çizelgesi grafiğini Visual Studio Performans Profili Oluşturucu ekran görüntüsü.](../profiling/media/memuse__reportoverview.png "MEMUSE__ReportOverview")

Zaman çizelgesi grafiği, uygulama çalıştırıla birlikte bellek dalgalanmalarını gösterir. Grafikte ani artışlar genellikle bazı kodun veri topladığı veya oluşturduklarını ve ardından işleme bittiğinde atılırken olduğunu gösterir. Büyük ani artışlar, en iyi duruma getirmenizi mümkün olan alanları gösteriyor. Daha da önemli olan, döndürülecek bellek tüketiminde bir artıştır çünkü verimsiz bellek kullanımına, hatta bir bellek sızıntısına işaret ediyor olabilir.

### <a name="take-snapshots-of-app-memory-states"></a>Uygulama bellek durumunun anlık görüntülerini alma

Uygulama çok sayıda nesne kullanır ve analizinizi tek bir senaryoya yoğunlaştırabilirsiniz. Veya araştırılacak bellek sorunları bulabilirsiniz. Belirli anlarda bellek kullanımını yakalamak için tanılama oturumu sırasında anlık görüntüler atabilirsiniz. Bellek sorunu oluşmadan önce bir uygulamanın temel anlık görüntüsünü, sorunun ilk ortaya çıkmasının ardından başka bir anlık görüntü ve senaryoyu tekrarlamanız gerekirse ek anlık görüntüler almak iyi bir fikirdir.

Anlık görüntüleri toplamak için bellek **verilerini yakalamak** istediğiniz zaman Anlık görüntü al'ı seçin.

### <a name="close-the-diagnostic-session"></a><a name="BKMK_Close_a_monitoring_session"></a> Tanılama oturumunu kapatma

Rapor oluşturmadan izleme oturumunu durdurmak için tanılama penceresini kapatmanız gerekir. Toplamayı tamamlayan veya anlık görüntü alan bir rapor oluşturmak için Koleksiyonu **Durdur'a seçin.**

![Koleksiyonu Durdurma](../profiling/media/memuse__stopcollection.png "Koleksiyonu Durdurma")

## <a name="memory-usage-reports"></a>Bellek Kullanımı raporları

Veri toplamayı durduran Bellek **Kullanımı aracı** uygulamayı durdurur ve Bellek Kullanımına **genel bakış** sayfasını görüntüler.

![Bellek kullanım grafiğini ve iki anlık görüntü bölmesini gösteren, Visual Studio Performans Profili Oluşturucu Kullanım aracında genel bakış sayfasının ekran görüntüsü.](../profiling/media/memuse__reportoverview1.png "Bellek Kullanımına genel bakış sayfası")

### <a name="memory-usage-snapshots"></a><a name="BKMK_Memory_Usage_snapshot_views"></a> Bellek Kullanımı anlık görüntüleri

Anlık Görüntü **bölmesindeki** sayılar, her anlık görüntü alınırken bellekte yer alan baytları ve nesneleri ve anlık görüntü ile önceki arasındaki farkı gösterir.

Sayılar, ayrıntılı Bellek Kullanımı rapor **görünümlerini** yeni bellek kullanımı pencerelerde Visual Studio bağlantılardır. Anlık [görüntü ayrıntıları raporu,](#snapshot-details-reports) bir anlık görüntüde türleri ve örnekleri gösterir. Anlık [görüntü farkı (fark) raporu,](#snapshot-difference-diff-reports) iki anlık görüntüde yer alan türleri ve örnekleri karşılar.

  ![Anlık görüntü görünümü bağlantıları](../profiling/media/memuse__snapshotview_numbered.png "Anlık görüntü görünümü bağlantıları")

|Görüntü|Açıklama|
|-|-|
|![1. Adım](../profiling/media/procguid_1.png "ProcGuid_1")|Anlık görüntü alınırken bellekte toplam bayt sayısı.<br /><br /> Tür örneklerinin toplam boyutuna göre sıralanmış bir anlık görüntü ayrıntıları raporu görüntülemek için bu bağlantıyı seçin.|
|![2. Adım](../profiling/media/procguid_2.png "ProcGuid_2")|Anlık görüntü alınırken bellekte yer alan nesnelerin toplam sayısı.<br /><br /> Türlerin örnek sayısına göre sıralanmış bir anlık görüntü ayrıntıları raporu görüntülemek için bu bağlantıyı seçin.|
|![3. Adım](../profiling/media/procguid_3.png "ProcGuid_3")|Bu anlık görüntüdeki bellek nesnelerinin toplam boyutu ile önceki anlık görüntü arasındaki fark. <br /><br /> Pozitif sayı, bu anlık görüntüde bellek boyutunun öncekinden büyük, negatif bir sayı ise boyutun daha küçük olduğu anlamına gelir. **Temel,** anlık görüntü bir tanılama oturumunda ilk kez olduğu anlamına gelir. **Fark Yok,** farkın sıfır olduğu anlamına gelir.<br /><br /> Türlerin toplam örnek boyutu arasındaki farka göre sıralanmış bir anlık görüntü fark raporu görüntülemek için bu bağlantıyı seçin.|
|![4. Adım](../profiling/media/procguid_4.png "ProcGuid_4")|Bu anlık görüntüdeki toplam bellek nesnesi sayısı ile önceki anlık görüntü arasındaki fark.<br /><br /> Türlerin toplam örnek sayısı arasındaki farka göre sıralanmış bir anlık görüntü fark raporu görüntülemek için bu bağlantıyı seçin.|

## <a name="memory-usage-snapshot-reports"></a>Bellek Kullanımı anlık görüntü raporları

<a name="BKMK_Snapshot_report_trees"></a> Bellek Kullanımına genel bakış sayfasındaki anlık görüntü bağlantılarından **birini** seçerek anlık görüntü raporu yeni bir sayfada açılır.

![Bellek Kullanımı anlık görüntü raporu](../profiling/media/memuse_snapshotreport_all.png "Bellek Kullanımı anlık görüntü raporu")

Anlık görüntü raporunda Nesne Türü **girişlerini genişletebilirsiniz** ve alt girişleri görüntüleyeceksiniz. Örnek adları, Bellek Kullanımı aracı tarafından oluşturulan benzersiz kimliklerdir.

Nesne **Türü mavi** ise, kaynak kodda nesneye gitmek için ayrı bir pencerede bunu seçin.

Belirleye olmadığınız veya kodunuzla kimlerin dahil olduğunu anlamanız zor olan türler büyük olasılıkla .NET, işletim sistemi veya derleyici nesneleridir. Bellek **Kullanımı** aracı, nesnelerinizin sahiplik zincirlerine dahilse bu nesneleri görüntüler.

Anlık görüntü raporunda:

- Yönetilen **Yığın** ağacı, rapora türleri ve örnekleri gösterir. Bir tür veya örnek seçildiğinde, seçilen **öğe için Kök** ve **Başvurulan Nesnelere** giden yollar görüntülenir.

- Kök **ağacının Yolları,** bir türe veya örneke başvurulan nesnelerin zincirini gösterir. .NET çöp toplayıcısı yalnızca tüm başvurular serbest bırakıldıklarda bir nesnenin belleğini temizler.

- Başvurulan **Türler** **veya Başvurulan Nesneler** ağacı, seçilen türün veya örneğin başvuran nesneleri gösterir.

### <a name="report-tree-filters"></a><a name="BKMK_Report_tree_filters_"></a> Rapor ağacı filtreleri

Uygulamalarda birçok tür, uygulama geliştiricileri için pek ilgi çekici bir şey değil. Anlık görüntü raporu filtreleri, Bu türlerin çoğunu Yönetilen Yığında **ve** Kök ağaç **yollarında gizler.**

![Sıralama ve filtreleme seçenekleri](../profiling/media/memuse_sortandfilter.png "MEMUSE_SortAndFilter")

- <a name="BKMK_Filter"></a> Bir ağacı tür adına göre filtrelemek için Filtre kutusuna **adı** girin. Filtre büyük/büyük/büyük harfe duyarlı değildir ve tür adının herhangi bir bölümünde belirtilen dizeyi tanır.

- <a name="BKMK_Collapse_Small_Objects"></a>Boyut  **(Bayt)** **toplam belleğin** yüzde 0,5'inden küçük olan türleri gizlemek için Filtre açılan listesinde Küçük Nesneleri Daralt'ı seçin.

- <a name="BKMK_Just_My_Code"></a> Dış **Yalnızca kendi kodum** oluşturulan **örneklerin** çoğunu gizlemek için Filtre açılan listesinden Filtre'yi seçin. Dış türler işletim sistemi veya çerçeve bileşenlerine aittir veya derleyici tarafından oluşturulur.

## <a name="snapshot-details-reports"></a>Anlık görüntü ayrıntıları raporları

 Anlık görüntü ayrıntıları raporu, tanılama oturumundan bir anlık görüntüyü açıklar. Raporu açmak için anlık görüntü bölmesindeki boyut veya nesneler bağlantısını seçin.

 ![Anlık görüntü bölmesindeki anlık görüntü raporuna bağlantılar](../profiling/media/memuse_snapshotview_snapshotdetailslinks.png "Anlık görüntü bölmesindeki anlık görüntü raporuna bağlantılar")

Her iki bağlantı da aynı raporu açar. Tek fark Yönetilen Yığın ağacının başlangıç sıralama **düzenidir.** Boyut bağlantısı, raporu Kapsayıcı Boyut **(Bayt) sütununa göre** sıralar. Nesneler bağlantısı, raporu Sayı sütununa **göre** sıralar. Rapor açıldıktan sonra sıralama sütununu veya sıralamayı değiştirebilirsiniz.

### <a name="managed-heap-tree-snapshot-details-reports"></a><a name="BKMK_Managed_Heap_tree__Snapshot_details_"></a> Yönetilen Yığın ağacı (Anlık görüntü ayrıntıları raporları)
 Yönetilen **Yığın** ağacı, bellekte tutulan nesne türlerini listeler. Türün boyuta göre sıralanmış en büyük on örneğini görüntülemek için bir tür adını genişletin. Seçilen öğenin Kök ve **Başvurulan Nesneler ağaç** yollarını görüntülemek **için** bir tür veya örnek seçin.

 ![Yönetilen Yığın ağacı](../profiling/media/memuse__snapshotdetails_managedheaptree.png "Yönetilen Yığın ağacı")

Anlık **görüntü ayrıntıları** raporuna ilişkin Yönetilen Yığın ağacı aşağıdaki sütunlara sahip:

|Ad|Açıklama|
|-|-|
|**Nesne Türü**|Türün veya nesne örneğinin adı.|
|**Sayısı**|Türün nesne örneklerinin sayısı. **Bir**  örnek için sayı her zaman 1'dir.|
|**Boyut (Bayt)**|Bir tür için anlık görüntüdeki türün tüm örneklerinin boyutu, örneklerde yer alan nesnelerin boyutu kadardır.<br /><br /> Bir örnek için nesnenin boyutu, örnekte yer alan nesnelerin boyutu kadardır. |
|**Kapsayıcı Boyut (Bayt)**|Tür örneklerinin boyutu veya içerdiği nesnelerin boyutu da dahil olmak üzere tek bir örneğin boyutu.|
|**Modül**|nesnesini içeren modül.|

### <a name="paths-to-root-tree-snapshot-details-reports"></a><a name="BKMK_Paths_to_Root_tree__Snapshot_details_"></a> Kök ağacın yolları (Anlık görüntü ayrıntıları raporları)
Kök **ağacının Yolları,** bir türe veya örneke başvurulan nesnelerin zincirini gösterir. .NET çöp toplayıcısı yalnızca tüm başvurular serbest bırakıldıklarda bir nesnenin belleğini temizler.

Kök ağacının **Yolları'na bir** tür için, başvurular içeren nesne sayısı Başvuru Sayısı **sütununda** görünür.

![Türler için Kök ağacın yolları](../profiling/media/memuse_snapshotdetails_type_pathstoroottree.png "Türler için Kök ağacın yolları")

### <a name="referenced-types-or-referenced-objects-tree-snapshot-details-reports"></a><a name="BKMK_Referenced_Objects_tree__Snapshot_details_"></a> Başvurulan Türler veya Başvurulan Nesneler ağacı (Anlık görüntü ayrıntıları raporları)
Başvurulan **Türler** **veya Başvurulan Nesneler** ağacı, seçilen türün veya örneğin başvuran nesneleri gösterir.

![Örnekler için Başvurulan Nesneler ağacı](../profiling/media/memuse_snapshotdetails_referencedobjects_instance.png "Örnekler için Başvurulan Nesneler ağacı")

Anlık **görüntü ayrıntıları raporunda** Başvurulan Türler ağacı aşağıdaki sütunlara sahip olur. Başvurulan **Nesneler ağacında** Başvuru Sayısı **sütunu** yok.

|Ad|Açıklama|
|-|-|
|**Nesne Türü** veya **Örneği**|Türün veya örneğin adı.|
|**Başvuru Sayısı**|Türler için, türün nesne örneklerinin sayısı.|
|**Boyut (Bayt)**|Bir tür için, türün tüm örneklerinin boyutu, türün içerdiği nesnelerin boyutu daha azdır.<br /><br /> Bir örnek için nesnenin boyutu, nesnesinde yer alan nesnelerin boyutu kadardır.|
|**Kapsayıcı Boyut (Bayt)**|Tür örneklerinin toplam boyutu veya içerdiği nesnelerin boyutu da dahil olmak üzere örneğin boyutu.|
|**Modül**|nesnesini içeren modül.|

## <a name="snapshot-difference-diff-reports"></a>Anlık görüntü farkı (fark) raporları

Anlık görüntü farkı (fark) raporu, birincil anlık görüntü ile önceki anlık görüntü arasındaki değişiklikleri gösterir. Fark raporunu açmak için anlık görüntü bölmesindeki fark bağlantılarından birini seçin.

Her iki bağlantı da aynı raporu açar. Tek fark, raporda Yönetilen Yığın **ağacının başlangıç** sıralama düzenidir. Boyut bağlantısı, raporu Kapsayıcı Boyut Fark **(Bayt) sütununa göre** sıralar. Nesneler bağlantısı, raporu Count **Diff sütununa göre** sıralar. Rapor açıldıktan sonra sıralama sütununu veya sıralamayı değiştirebilirsiniz.

 ![Anlık görüntü bölmesindeki fark raporunun bağlantıları](../profiling/media/memuse_snapshotview_snapshotdifflinks.png "Anlık görüntü bölmesindeki fark raporunun bağlantıları")

### <a name="managed-heap-tree-snapshot-diff-reports"></a><a name="BKMK_Managed_Heap_tree__Snapshot_diff_"></a> Yönetilen Yığın ağacı (Anlık görüntü fark raporları)

 Yönetilen **Yığın** ağacı, bellekte tutulan nesne türlerini listeler. Türün boyuta göre sıralanmış en büyük on örneğini görüntülemek için bir tür adını genişletabilirsiniz. Seçilen öğenin Kök ve **Başvurulan Nesneler ağaç** yollarını görüntülemek **için** bir tür veya örnek seçin.

 ![Fark raporu türü için Yönetilen Yığın ağacı](../profiling/media/memuse_snapshotdiff_type_heap.png "Fark raporu türü için Yönetilen Yığın ağacı")

Anlık **görüntü fark** raporunda Yönetilen Yığın ağacı aşağıdaki sütunlara sahip:

|Ad|Açıklama|
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

Kök ağacının **Yolları'na bir** tür için, başvurular içeren nesne sayısı Başvuru Sayısı **sütununda** görünür. Önceki anlık görüntüdeki sayı farkı Başvuru Farkı **sütunundadır.**

 ![Fark raporunda Kök ağacın yolları](../profiling/media/memuse_snapshotdiff_pathstoroot_instance_all.png "Fark raporunda Kök ağacın yolları")

### <a name="referenced-types-or-referenced-objects-tree-snapshot-diff-reports"></a><a name="BKMK_Referenced_Objects_tree__Snapshot_diff_"></a> Başvurulan Türler veya Başvurulan Nesneler ağacı (Anlık görüntü fark raporları)

Başvurulan **Türler** **veya Başvurulan Nesneler** ağacı, seçilen türün veya örneğin başvuran nesneleri gösterir.

![Fark raporunda Başvurulan Türler](../profiling/media/memuse_snapshotdiff_referencedtypes.png "Fark raporunda Başvurulan Türler")

Bir **anlık görüntü fark** raporunda Başvurulan Türler ağacı aşağıdaki sütunlara sahip olur. Başvurulan **Nesneler ağacında** Örnek, **Boyut** **(Bayt)**, Kapsayıcı **Boyut (Bayt)** ve Modül **sütunları** bulunur.

|Ad|Açıklama|
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
- [Visual Studio'de profil oluşturma](../profiling/index.yml)
- [Profil oluşturma araçlarına ilk bakış](../profiling/profiling-feature-tour.md)
- [C++, C# ve Visual Basic kullanan UWP uygulamaları için performansa yönelik en iyi Visual Basic](/previous-versions/windows/apps/hh750313\(v\=win.10\))
- [Visual Studio'de yeni Bellek Kullanımı aracıyla ilgili bellek sorunlarını tanılama](https://devblogs.microsoft.com/devops/diagnosing-memory-issues-with-the-new-memory-usage-tool-in-visual-studio/)