---
title: Hata ayıklama olmadan bellek kullanımını analiz etme | Microsoft Dokümanlar
ms.custom: ''
ms.date: 11/15/2018
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: eaf853cd19a44af4cb8510fde11da95bfa7de5c1
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77578346"
---
# <a name="analyze-memory-usage-without-the-debugger"></a>Hata ayıklama olmadan bellek kullanımını analiz edin

**Bellek Kullanımı** aracı uygulamanızın bellek kullanımını izler. Aracı Visual Studio'da aktif olarak geliştirdiğiniz senaryoların gerçek zamanlı bellek etkilerini incelemek için kullanabilirsiniz. Uygulamanın bellek durumlarının ayrıntılı anlık görüntülerini alabilir ve bellek sorunlarının temel nedenlerini bulmak için anlık görüntüleri karşılaştırabilirsiniz.

**Bellek Kullanımı** aracı hata ayıklayıcı ile veya olmadan çalıştırabilirsiniz. Aşağıdaki yönergeler Visual Studio **Performans Profilleyicisinde**hata ayıklayıcısı olmadan **Bellek Kullanımı** aracının nasıl kullanılacağını gösterir.

## <a name="memory-usage-diagnostic-sessions"></a>Bellek Kullanımı tanılama oturumları

**Bellek Kullanımı tanılama oturumunu başlatmak için:**

1. Visual Studio'da bir C# Universal Windows (UWP) projesi açın.

1. Menü çubuğunda **Hata Ayıklama** > **Performans Profilcisi'ni**seçin.

1. **Bellek Kullanımı'nı**seçin ve ardından **Başlat'ı**seçin.

   ![Bellek Kullanımı tanılama oturumunu başlatın](../profiling/media/memuse_start_diagnosticssession.png "Bellek Kullanımı tanılama oturumunu başlatın")

### <a name="monitor-memory-use"></a>Bellek kullanımını izleme

Tanılama oturumu başlattığınızda, uygulamanız başlar ve **Tanılama Araçları** penceresi uygulamanızın bellek kullanımının bir zaman çizelgesi grafiğini görüntüler.

![Bellek Kullanımına genel bakış sayfası](../profiling/media/memuse__reportoverview.png "MEMUSE__ReportOverview")

Zaman çizelgesi grafiği, uygulama çalışırken bellek dalgalanmalarını gösterir. Grafikteki ani artışlar genellikle bazı kodların veri topladığını veya oluşturduğunu ve işlem yapıldığında bunu attığını gösterir. Büyük ani artışlar, optimize edebileceğiniz alanları gösterir. Daha fazla endişe geri döndürülmez bellek tüketiminde bir artış, çünkü verimsiz bellek kullanımı veya hatta bir bellek sızıntısı gösterebilir.

### <a name="take-snapshots-of-app-memory-states"></a>Uygulama bellek durumlarının anlık görüntülerini alma

Bir uygulama çok sayıda nesne kullanır ve çözümlemenizi tek bir senaryoya yoğunlaşmış olabilirsiniz. Veya, araştırmak için bellek sorunları bulabilirsiniz. Belirli anlarda bellek kullanımını yakalamak için tanılama oturumu sırasında anlık görüntü alabilirsiniz. Bir bellek sorunu görünmeden önce bir uygulamanın temel anlık görüntüsünü, sorunun ilk oluşumundan sonra başka bir anlık görüntü ve senaryoyu yineleyebilirseniz ek anlık görüntüler almak iyi bir fikirdir.

Anlık görüntü toplamak için, bellek verilerini yakalamak istediğinizde **anlık görüntü al'ı** seçin.

### <a name="close-the-diagnostic-session"></a><a name="BKMK_Close_a_monitoring_session"></a>Tanılama oturumunu kapatın

Bir izleme oturumunu rapor oluşturmadan durdurmak için tanılama penceresini kapatmanın yeterli. Toplamayı bitirdiğinizde veya anlık görüntü aldığınızda rapor oluşturmak için **Koleksiyonu Durdur'u**seçin.

![Toplamayı Durdur](../profiling/media/memuse__stopcollection.png "Toplamayı Durdur")

## <a name="memory-usage-reports"></a>Bellek Kullanım raporları

Veri toplamayı durdurduktan sonra, **Bellek Kullanımı** aracı uygulamayı durdurur ve **Bellek Kullanımına** genel bakış sayfasını görüntüler.

![Bellek Kullanımına genel bakış sayfası](../profiling/media/memuse__reportoverview1.png "Bellek Kullanımına genel bakış sayfası")

### <a name="memory-usage-snapshots"></a><a name="BKMK_Memory_Usage_snapshot_views"></a>Bellek Kullanımı anlık görüntüleri

**Anlık Görüntü** bölmelerinde sayılar, her anlık görüntü alındığında bellekteki baytları ve nesneleri ve anlık görüntü ile bir önceki arasındaki farkı gösterir.

Sayılar, yeni Visual Studio pencerelerinde ayrıntılı **Bellek Kullanımı** raporu görünümlerini açan bağlantılardır. [Anlık görüntü ayrıntıları raporu,](#snapshot-details-reports) türleri ve örnekleri bir anlık görüntüde gösterir. [Anlık görüntü farkı (diff) raporu,](#snapshot-difference-diff-reports) iki anlık görüntüdeki türleri ve örnekleri karşılaştırır.

  ![Anlık görüntü bağlantıları](../profiling/media/memuse__snapshotview_numbered.png "Anlık görüntü bağlantıları")

|||
|-|-|
|![1. Adım](../profiling/media/procguid_1.png "ProcGuid_1")|Anlık görüntü alındığında bellekteki toplam bayt sayısı.<br /><br /> Tür örneklerinin toplam boyutuna göre sıralanmış anlık görüntü ayrıntıları raporunu görüntülemek için bu bağlantıyı seçin.|
|![2. Adım](../profiling/media/procguid_2.png "ProcGuid_2")|Anlık görüntü alındığında bellekteki toplam nesne sayısı.<br /><br /> Türlerin örnek sayısına göre sıralanmış anlık görüntü ayrıntıları raporunu görüntülemek için bu bağlantıyı seçin.|
|![3. Adım](../profiling/media/procguid_3.png "ProcGuid_3")|Bu anlık görüntüdeki bellek nesnelerinin toplam boyutu ile önceki anlık görüntü arasındaki fark. <br /><br /> Pozitif sayı, bu anlık görüntünün bellek boyutunun bir öncekinden daha büyük, negatif sayının boyutun ise daha küçük olduğu anlamına gelir. **Temel,** anlık görüntünün tanılama oturumundaki ilk görüntü olduğu anlamına gelir. **Fark Yok,** fark Sıfır demektir.<br /><br /> Türlerin örneklerinin toplam boyutundaki farka göre sıralanmış anlık görüntü diff raporunu görüntülemek için bu bağlantıyı seçin.|
|![Adım 4](../profiling/media/procguid_4.png "ProcGuid_4")|Bu anlık görüntüdeki toplam bellek nesnesi sayısı ile önceki anlık görüntü arasındaki fark.<br /><br /> Türlerin örneklerinin toplam sayısındaki farka göre sıralanmış anlık görüntü diff raporunu görüntülemek için bu bağlantıyı seçin.|

## <a name="memory-usage-snapshot-reports"></a>Bellek Kullanımı anlık görüntüleri raporları

<a name="BKMK_Snapshot_report_trees"></a>**Bellek Kullanımına** genel bakış sayfasındaki anlık görüntü bağlantılarından birini seçtiğinizde, yeni bir sayfada anlık görüntü raporu açılır.

![Bellek Kullanımı anlık görüntü raporu](../profiling/media/memuse_snapshotreport_all.png "Bellek Kullanımı anlık görüntü raporu")

Anlık görüntü raporunda, Alt girişleri görüntülemek için **Nesne Türü** girişlerini genişletebilirsiniz. Örnek adları, Bellek Kullanımı aracı tarafından oluşturulan benzersiz adlardır.

Nesne **Türü** maviyse, kaynak koddaki nesneye gitmek için ayrı bir pencerede onu seçebilirsiniz.

Tanımlayamadığınız veya kodunuzda olan etkileşimini anlamadığınız türler büyük olasılıkla .NET Framework, işletim sistemi veya derleyici nesneleridir. **Bellek Kullanımı** aracı, nesnelerinizin sahiplik zincirlerine dahil olmaları durumunda bu nesneleri görüntüler.

Anlık görüntü raporunda:

- **Yönetilen Yığın** ağacı, rapordaki türleri ve örnekleri gösterir. Bir tür veya örnek seçildiğinde, seçili öğe **için Kök** ve **Başvurulan Nesnelere** Giden Yollar görüntülenir.

- **Köke Giden Yollar** ağacı, bir türe veya örne başvuran nesneler zincirini gösterir. .NET Framework çöp toplayıcısı, bir nesnenin belleği yalnızca tüm başvurular yayımlandığında temizler.

- **Başvurulan Türler** veya **Başvurulan Nesneler** ağacı, seçili tür veya örnek başvurulan nesneleri gösterir.

### <a name="report-tree-filters"></a><a name="BKMK_Report_tree_filters_"></a>Ağaç filtrelerini bildir

Uygulamalardaki birçok tür, uygulama geliştiricileri için çok ilginç değildir. Anlık görüntü raporu filtreleri, **yönetilen yığın** ve **Kök ağaçlarına giden yollarda** bu türlerin çoğunu gizleyebilir.

![Sıralama ve filtre leme seçenekleri](../profiling/media/memuse_sortandfilter.png "MEMUSE_SortAndFilter")

- <a name="BKMK_Filter"></a>Bir ağacı tür adına göre filtrelemek için **Filtre** kutusuna adı girin. Filtre büyük/küçük harf duyarlı değildir ve tür adının herhangi bir bölümünde belirtilen dizetanır.

- <a name="BKMK_Collapse_Small_Objects"></a>**Boyutu (Baytlar)** toplam belleğin yüzde 0,5'inden az olan türleri gizlemek için **Filtre** açılır yerinde **Küçük Nesneleri Daralt'ı** seçin.

- <a name="BKMK_Just_My_Code"></a>Dış kod tarafından oluşturulan çoğu örneği gizlemek için **Filtre** açılır bölümünde **Yalnızca Kodum'u** seçin. Dış türler işletim sistemine veya çerçeve bileşenlerine aittir veya derleyici tarafından oluşturulur.

## <a name="snapshot-details-reports"></a>Anlık görüntü ayrıntıları raporları

 Anlık görüntü ayrıntıları raporu, tanılama oturumundan bir anlık görüntü açıklar. Raporu açmak için anlık görüntü bölmesinde boyut veya nesne bağlantısını seçin.

 ![Anlık görüntü bölmesinde anlık görüntü raporuna bağlantılar](../profiling/media/memuse_snapshotview_snapshotdetailslinks.png "Anlık görüntü bölmesinde anlık görüntü raporuna bağlantılar")

Her iki bağlantı da aynı raporu açar. Tek fark **Yönetilen Yığın** ağacının başlangıç sırasıdır. Boyut bağlantısı raporu Kapsayıcı **Boyut (Baytlar)** sütununa göre sıralar. Nesneler bağlantısı raporu **Kont** sütununa göre sıralar. Rapor açıldıktan sonra sıralama sütununa veya sırasını değiştirebilirsiniz.

### <a name="managed-heap-tree-snapshot-details-reports"></a><a name="BKMK_Managed_Heap_tree__Snapshot_details_"></a>Yönetilen Yığın ağacı (Anlık görüntü ayrıntıları raporları)
 **Yönetilen Yığın** ağacı, bellekte tutulan nesne türlerini listeler. Boyutuna göre sıralanmış türün en büyük on örneğini görüntülemek için bir tür adını genişletin. Seçili öğe için Kök ve **Başvurulan Nesnelere** **Giden Yolları** görüntülemek için bir tür veya örnek seçin.

 ![Yönetilen Yığın ağacı](../profiling/media/memuse__snapshotdetails_managedheaptree.png "Yönetilen Yığın ağacı")

Anlık görüntü ayrıntıları raporunda yönetilen **yığın** ağacı aşağıdaki sütunlara sahiptir:

|||
|-|-|
|**Nesne Türü**|Tür veya nesne örneğinin adı.|
|**Sayısı**|Türünün nesne örneklerinin sayısı. **Sayma** her zaman bir örnek için 1'dir.|
|**Boyut (Bayt)**|Bir tür için, anlık görüntüdeki türün tüm örneklerinin boyutu, örneklerde bulunan nesnelerin boyutundan daha azdır.<br /><br /> Örneğin, nesnenin boyutu, örnekte bulunan nesnelerin boyutu daha az. |
|**Dahil Boyut (Bayt)**|İçerdiği nesnelerin boyutu da dahil olmak üzere, tür örneklerinin veya tek bir örneğin boyutuboyutu.|
|**Modül**|Nesneyi içeren modül.|

### <a name="paths-to-root-tree-snapshot-details-reports"></a><a name="BKMK_Paths_to_Root_tree__Snapshot_details_"></a>Kök ağacına giden yollar (Anlık görüntü ayrıntıları raporları)
**Köke Giden Yollar ağacı,** bir türe veya örne başvuran nesneler zincirini gösterir. .NET Framework çöp toplayıcısı, bir nesnenin belleği yalnızca tüm başvurular yayımlandığında temizler.

**Köke Giden Yollar** ağacındaki bir tür için, bu türe başvuru tutan nesne sayısı **Başvuru Sayısı** sütununda görüntülenir.

![Türler için Kök ağacına giden yollar](../profiling/media/memuse_snapshotdetails_type_pathstoroottree.png "Türler için Kök ağacına giden yollar")

### <a name="referenced-types-or-referenced-objects-tree-snapshot-details-reports"></a><a name="BKMK_Referenced_Objects_tree__Snapshot_details_"></a>Başvurulan Türler veya Başvurulan Nesneler ağacı (Anlık görüntü ayrıntıları raporları)
**Başvurulan Türler** veya **Başvurulan Nesneler** ağacı, seçili tür veya örnek başvurulan nesneleri gösterir.

![Örneğin başvurulan Nesneler ağacı](../profiling/media/memuse_snapshotdetails_referencedobjects_instance.png "Örneğin başvurulan Nesneler ağacı")

Anlık görüntü ayrıntıları raporunda **başvurulan türler** ağacı aşağıdaki sütunlara sahiptir. **Başvurulan Nesneler** ağacında Başvuru **Sayısı** sütunu yoktur.

|||
|-|-|
|**Nesne Türü** veya **Örneği**|Tür veya örneğin adı.|
|**Referans Sayısı**|Türleri için, tür nesne örneklerinin sayısı.|
|**Boyut (Bayt)**|Bir tür için, türün tüm örneklerinin boyutu, türünde bulunan nesnelerin boyutu daha az.<br /><br /> Örneğin, nesnenin boyutu, nesnenin içinde bulunan nesnelerin boyutu daha az.|
|**Dahil Boyut (Bayt)**|İçerdiği nesnelerin boyutu da dahil olmak üzere, tür örneklerinin veya örneğin boyutunun toplam boyutu.|
|**Modül**|Nesneyi içeren modül.|

## <a name="snapshot-difference-diff-reports"></a>Anlık görüntü farkı (diff) raporları

Anlık görüntü farkı (diff) raporu, birincil anlık görüntü ile önceki anlık görüntü arasındaki değişiklikleri gösterir. Diff raporunu açmak için anlık görüntü bölmesindeki fark bağlantılarından birini seçin.

Her iki bağlantı da aynı raporu açar. Tek fark, raporda yönetilen **yığın** ağacının başlangıç sırasıdır. Boyut bağlantısı raporu Kapsayıcı **Boyut Diff (Bayt)** sütununa göre sıralar. Nesneler bağlantısı raporu **Diff Sayısı** sütununa göre sıralar. Rapor açıldıktan sonra sıralama sütununa veya sırasını değiştirebilirsiniz.

 ![Anlık görüntü bölmesinde fark raporuna bağlantılar](../profiling/media/memuse_snapshotview_snapshotdifflinks.png "Anlık görüntü bölmesinde fark raporuna bağlantılar")

### <a name="managed-heap-tree-snapshot-diff-reports"></a><a name="BKMK_Managed_Heap_tree__Snapshot_diff_"></a>Yönetilen Yığın ağacı (Anlık görüntü diff raporları)

 **Yönetilen Yığın** ağacı, bellekte tutulan nesne türlerini listeler. Bir tür adını, boyutuna göre sıralanmış türün en büyük on örneğini görüntülemek için genişletebilirsiniz. Seçili öğe için Kök ve **Başvurulan Nesnelere** **Giden Yolları** görüntülemek için bir tür veya örnek seçin.

 ![Fark raporunda bir tür için yönetilen Yığın ağacı](../profiling/media/memuse_snapshotdiff_type_heap.png "Fark raporunda bir tür için yönetilen Yığın ağacı")

Anlık görüntü diff raporunda **Yönetilen Yığın** ağacı aşağıdaki sütunlara sahiptir:

|||
|-|-|
|**Nesne Türü**|Tür veya nesne örneğinin adı.|
|**Sayısı**|Birincil anlık görüntüdeki bir tür örneklerinin sayısı. **Sayma** her zaman bir örnek için 1'dir.|
|**Sayı Diff**|Bir tür için, birincil anlık görüntü ve önceki anlık görüntü arasındaki tür örneklerinin sayısı arasındaki fark. Alan bir örnek için boş.|
|**Boyut (Bayt)**|Birincil anlık görüntüdeki nesnelerin boyutu, nesnelerdeki nesnelerin boyutundan daha azdır. Bir tür için **Boyut (Bayt)** ve **Kapsayıcı Boyut (Baytlar),** tür örneklerinin boyutlarının toplamıdır.|
|**Toplam Boyut Diff (Bayt)**|Bir tür için, birincil anlık görüntü ve önceki anlık görüntü arasındaki tür örneklerinin toplam boyutundaki fark, örneklerdeki nesnelerin boyutu daha az. Alan bir örnek için boş.|
|**Dahil Boyut (Bayt)**|Nesnelerdeki nesnelerin boyutu da dahil olmak üzere birincil anlık görüntüdeki nesnelerin boyutu.|
|**Kapsamlı Boyut Diff (Bayt)**|Bir tür için, nesnelerdeki nesnelerin boyutu da dahil olmak üzere birincil anlık görüntü ve önceki anlık görüntü arasındaki tür tüm örneklerinin boyutundaki fark. Alan bir örnek için boş.|
|**Modül**|Nesneyi içeren modül.|

### <a name="paths-to-root-tree-snapshot-diff-reports"></a><a name="BKMK_Paths_to_Root_tree__Snapshot_diff_"></a>Kök ağacına giden yollar (Anlık görüntü diff raporları)

**Köke Giden Yollar ağacı,** bir türe veya örne başvuran nesneler zincirini gösterir. .NET Framework çöp toplayıcısı, bir nesnenin belleği yalnızca tüm başvurular yayımlandığında temizler.

**Köke Giden Yollar** ağacındaki bir tür için, bu türe başvuru tutan nesne sayısı **Başvuru Sayısı** sütununda görüntülenir. Önceki anlık görüntüden sayım farkı **Başvuru Diff** sütunundadır.

 ![Diff raporunda Kök ağacına Giden Yollar](../profiling/media/memuse_snapshotdiff_pathstoroot_instance_all.png "Diff raporunda Kök ağacına Giden Yollar")

### <a name="referenced-types-or-referenced-objects-tree-snapshot-diff-reports"></a><a name="BKMK_Referenced_Objects_tree__Snapshot_diff_"></a>Başvurulan Türler veya Başvurulan Nesneler ağacı (Anlık görüntü diff raporları)

**Başvurulan Türler** veya **Başvurulan Nesneler** ağacı, seçili tür veya örnek başvurulan nesneleri gösterir.

![Diff raporunda başvurulan türler](../profiling/media/memuse_snapshotdiff_referencedtypes.png "Diff raporunda başvurulan türler")

Anlık görüntü diff raporunda **Başvurulan Türler** ağacı aşağıdaki sütunlara sahiptir. **Başvurulan Nesneler** ağacı, **Örnek,** **Boyut (Bayt)**, **Kapsayıcı Boyut (Bayt)** ve **Modül** sütunları vardır.

|||
|-|-|
|**Nesne Türü** veya **Örneği**|Tür veya nesne örneğinin adı.|
|**Referans Sayısı**|Birincil anlık görüntüdeki bir tür örneklerinin sayısı.|
|**Referans Sayısı Diff**|Bir tür için, birincil anlık görüntü ve önceki anlık görüntü arasındaki tür örneklerinin sayısı arasındaki fark.|
|**Boyut (Bayt)**|Birincil anlık görüntüdeki nesnelerin boyutu, nesnelerdeki nesnelerin boyutundan daha azdır. Bir tür için **Boyut (Bayt)** ve **Kapsayıcı Boyut (Baytlar),** tür örneklerinin boyutlarının toplamıdır.|
|**Toplam Boyut Diff (Bayt)**|Bir tür için, birincil anlık görüntü ve önceki anlık görüntü arasındaki tür örneklerinin toplam boyutundaki fark, örneklerdeki nesnelerin boyutu daha az. |
|**Dahil Boyut (Bayt)**|Nesnelerdeki nesnelerin boyutu da dahil olmak üzere birincil anlık görüntüdeki nesnelerin boyutu.|
|**Kapsamlı Boyut Diff (Bayt)**|Bir tür için, nesnelerdeki nesnelerin boyutu da dahil olmak üzere birincil anlık görüntü ve önceki anlık görüntü arasındaki tür tüm örneklerinin boyutundaki fark.|
|**Modül**|Nesneyi içeren modül.|

## <a name="see-also"></a>Ayrıca bkz.
- [JavaScript bellek](../profiling/javascript-memory.md)
- [Visual Studio'da Profil Oluşturma](../profiling/index.yml)
- [Profil oluşturma araçlarına ilk bakış](../profiling/profiling-feature-tour.md)
- [C++, C#ve Visual Basic kullanarak UWP uygulamaları için en iyi performans uygulamaları](/previous-versions/windows/apps/hh750313\(v\=win.10\))
- [Visual Studio'daki yeni Bellek Kullanımı aracıyla bellek sorunlarını tanılama](https://devblogs.microsoft.com/devops/diagnosing-memory-issues-with-the-new-memory-usage-tool-in-visual-studio/)