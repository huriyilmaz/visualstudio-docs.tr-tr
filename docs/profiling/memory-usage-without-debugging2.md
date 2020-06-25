---
title: Hata ayıklama olmadan bellek kullanımını analiz etme | Microsoft Docs
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 62ac71a3aa707958bd0c7f107185d141e339b2b7
ms.sourcegitcommit: 57d96de120e0574e506dfd80bb7adfbac73f96be
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85332142"
---
# <a name="analyze-memory-usage-without-the-debugger"></a>Hata ayıklayıcı olmadan bellek kullanımını analiz etme

**Bellek kullanımı** Aracı, uygulamanızın bellek kullanımını izler. Visual Studio 'da etkin bir şekilde geliştirmekte olduğunuz senaryoların gerçek zamanlı bellek efektlerini incelemek için aracını kullanabilirsiniz. Uygulamanın bellek durumlarının ayrıntılı anlık görüntülerini alabilir ve bellek sorunlarının ana nedenlerini bulmak için anlık görüntüleri karşılaştırabilirsiniz.

**Bellek kullanımı** Aracı, [hata ayıklayıcı ile veya olmadan](../profiling/running-profiling-tools-with-or-without-the-debugger.md)çalıştırılabilir. Bu makalede, Visual Studio **performans profil oluşturucusu**'nda hata ayıklayıcı olmadan **bellek kullanımı** aracının nasıl kullanılacağını göstereceğiz.

## <a name="memory-usage-diagnostic-sessions"></a>Bellek kullanımı tanılama oturumları

**Bir bellek kullanımı Tanılama oturumu başlatmak için:**

1. Visual Studio 'da bir proje açın.

   Bellek kullanımı aracı .NET, ASP.NET, Native veya karma mod (.NET ve yerel) uygulamalarını destekler.

1. Hata Ayıkla menüsünde, çözüm yapılandırmasını **yayınlama** olarak ayarlayın ve dağıtım hedefi olarak **yerel Windows hata ayıklayıcısı** 'Nı (veya **yerel makine**) seçin.

1. Menü çubuğunda, **Hata Ayıkla**  >  **performans profil oluşturucusu**' nu seçin.

1. **Kullanılabilir araçlar**' ın altında **bellek kullanımı**' nı seçin ve ardından **Başlat**' ı seçin.

   ![Bellek kullanımı Tanılama oturumu başlatma](../profiling/media/memuse_start_diagnosticssession.png "Bellek kullanımı Tanılama oturumu başlatma")

### <a name="monitor-memory-use"></a>Bellek kullanımını izleme

Bir Tanılama oturumu başlattığınızda, uygulamanız başlar ve **Tanılama araçları** penceresi, uygulamanızın bellek kullanımı için bir zaman çizelgesi grafiği görüntüler.

![Bellek kullanımına genel bakış sayfası](../profiling/media/memuse__reportoverview.png "MEMUSE__ReportOverview")

Zaman çizelgesi grafiği, uygulamanın çalıştırıldığı şekilde bellek dalgalanmalarını gösterir. Grafikteki ani artışlar genellikle bazı kodların veri toplamasını veya oluşturmasını ve işlem tamamlandığında bu dosyayı atmaya işaret ediyor. Büyük ani artışlar, iyileştirebilecek olan bölgeleri gösterir. Daha fazla sorun, yetersiz bellek kullanımı veya hatta bellek sızıntısı belirtebileceğinden, döndürülmemiş bellek tüketimine sahiptir.

### <a name="take-snapshots-of-app-memory-states"></a>Uygulama belleği durumlarının anlık görüntülerini al

Bir uygulama çok sayıda nesne kullanır ve analizinizi bir senaryoya göre yoğunlaşmak isteyebilirsiniz. Ya da araştırmak için bellek sorunları bulabilirsiniz. Bellek kullanımını belirli bir süre içinde yakalamak için bir Tanılama oturumu sırasında anlık görüntü alabilirsiniz. Bir bellek sorunu görüntülenmeden önce bir uygulamanın temel anlık görüntüsünü almak ve bu senaryoyu tekrarlamanız durumunda sorunun ilk oluşumunda daha sonra başka bir anlık görüntü sağlamak iyi bir fikir olabilir.

Anlık görüntü toplamak için bellek verilerini yakalamak istediğinizde **anlık görüntü al** ' ı seçin.

### <a name="close-the-diagnostic-session"></a><a name="BKMK_Close_a_monitoring_session"></a>Tanılama oturumunu kapat

Bir rapor oluşturmadan izleme oturumunu durdurmak için, yalnızca tanılama penceresini kapatmanız yeterlidir. Anlık görüntü toplamayı bitirdiğinizde rapor oluşturmak için, **toplamayı durdur**' u seçin.

![Toplamayı durdur](../profiling/media/memuse__stopcollection.png "Toplamayı durdur")

## <a name="memory-usage-reports"></a>Bellek kullanım raporları

Veri toplamayı durdurduktan sonra, **bellek kullanımı** Aracı uygulamayı durdurur ve **bellek kullanımı** genel bakış sayfasını görüntüler.

![Bellek kullanımına genel bakış sayfası](../profiling/media/memuse__reportoverview1.png "Bellek kullanımına genel bakış sayfası")

### <a name="memory-usage-snapshots"></a><a name="BKMK_Memory_Usage_snapshot_views"></a>Bellek kullanımı anlık görüntüleri

**Anlık** görüntü bölmelerinde bulunan sayılar, her anlık görüntü alındığı sırada bellekteki baytları ve nesneleri ve anlık görüntü ile bir önceki arasındaki farkı gösterir.

Numaralar, yeni Visual Studio Windows 'da ayrıntılı **bellek kullanımı** rapor görünümlerini açan bağlantılardır. [Anlık görüntü ayrıntıları raporu](#snapshot-details-reports) , bir anlık görüntüdeki türleri ve örnekleri gösterir. [Anlık görüntü farkı (fark) raporu](#snapshot-difference-diff-reports) , iki anlık görüntüdeki türleri ve örnekleri karşılaştırır.

  ![Anlık görüntü görünümü bağlantıları](../profiling/media/memuse__snapshotview_numbered.png "Anlık görüntü görünümü bağlantıları")

|||
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

### <a name="report-tree-filters"></a><a name="BKMK_Report_tree_filters_"></a>Rapor ağacı filtreleri

Uygulamalarda birçok tür uygulama geliştiricilerine çok ilginç değildir. Anlık görüntü raporu filtreleri **yönetilen yığında** bu türlerin çoğunu ve kök ağaçlara **yolları** gizleyebilir.

![Sıralama ve filtreleme seçenekleri](../profiling/media/memuse_sortandfilter.png "MEMUSE_SortAndFilter")

- <a name="BKMK_Filter"></a>Bir ağacı tür adına göre filtrelemek için, **filtre** kutusuna adı girin. Filtre, büyük/küçük harfe duyarlı değildir ve tür adının herhangi bir bölümünde belirtilen dizeyi tanır.

- <a name="BKMK_Collapse_Small_Objects"></a>**Boyutu (bayt)** toplam belleğin yüzde 0,5 ' inden az olan türleri gizlemek için **filtre** açılan menüsünde **küçük nesneleri Daralt** ' ı seçin.

- <a name="BKMK_Just_My_Code"></a>Dış kod tarafından oluşturulan örneklerin çoğunu gizlemek için **filtre** açılan listesinde **yalnızca kendi kodum** seçin. Dış türler, işletim sistemi veya çerçeve bileşenlerine aittir veya derleyici tarafından oluşturulur.

## <a name="snapshot-details-reports"></a>Anlık görüntü ayrıntıları raporları

 Anlık görüntü ayrıntıları raporu, bir tanılama oturumundan bir anlık görüntüyü açıklar. Raporu açmak için bir anlık görüntü bölmesindeki boyut veya nesneler bağlantısını seçin.

 ![Anlık görüntü bölmesinde anlık görüntü raporuna bağlantılar](../profiling/media/memuse_snapshotview_snapshotdetailslinks.png "Anlık görüntü bölmesinde anlık görüntü raporuna bağlantılar")

Her iki bağlantı de aynı raporu açar. Tek fark, **yönetilen yığın** ağacının başlangıç sıralama sıraıdır. Boyut bağlantısı, raporu **kapsamlı boyut (bayt)** sütununa göre sıralar. Nesneler bağlantısı, raporu **say** sütununa göre sıralar. Sıralama sütununu veya sırayı rapor açıldıktan sonra değiştirebilirsiniz.

### <a name="managed-heap-tree-snapshot-details-reports"></a><a name="BKMK_Managed_Heap_tree__Snapshot_details_"></a>Yönetilen yığın ağacı (anlık görüntü ayrıntıları raporları)
 **Yönetilen yığın** ağacı bellekte tutulan nesne türlerini listeler. Türün en büyük on örneğini görüntülemek için bir tür adı genişletin, boyuta göre sıralanır. Seçili öğe için köke ve **başvurulan nesne** ağaçlarına **yönelik yolları** göstermek için bir tür veya örnek seçin.

 ![Yönetilen yığın ağacı](../profiling/media/memuse__snapshotdetails_managedheaptree.png "Yönetilen yığın ağacı")

Anlık görüntü ayrıntıları raporundaki **yönetilen yığın** ağacı aşağıdaki sütunlara sahiptir:

|||
|-|-|
|**Nesne türü**|Tür veya nesne örneğinin adı.|
|**Biriktirme**|Türün nesne örneklerinin sayısı. Bir örnek için **sayı** her zaman 1 ' dir.|
|**Boyut (bayt)**|Bir tür için, anlık görüntüdeki türün tüm örneklerinin boyutu, örneklerde yer alan nesnelerin boyutu azalır.<br /><br /> Bir örnek için, nesnenin boyutu, örnekte yer alan nesnelerin boyutunu azaltır. |
|**Kapsamlı boyut (bayt)**|İçerilen nesnelerin boyutu dahil olmak üzere, türün örneklerinin boyutu veya tek bir örneğin boyutu.|
|**Modül**|Nesneyi içeren modül.|

### <a name="paths-to-root-tree-snapshot-details-reports"></a><a name="BKMK_Paths_to_Root_tree__Snapshot_details_"></a>Kök ağacına yönelik yollar (anlık görüntü ayrıntıları raporları)
**Kök ağacına yönelik yollar** , bir türe veya örneğe başvuran nesne zincirini gösterir. .NET atık toplayıcısı, yalnızca tüm başvuruları serbest bırakıldığında bir nesne için belleği temizler.

**Kök ağaç yollarındaki** bir tür Için, **başvuru sayısı** sütununda bu türe başvuru tutan nesne sayısı görüntülenir.

![Türler için kök ağacına yönelik yollar](../profiling/media/memuse_snapshotdetails_type_pathstoroottree.png "Türler için kök ağacına yönelik yollar")

### <a name="referenced-types-or-referenced-objects-tree-snapshot-details-reports"></a><a name="BKMK_Referenced_Objects_tree__Snapshot_details_"></a>Başvurulan türler veya başvurulan nesneler ağacı (anlık görüntü ayrıntıları raporları)
**Başvurulan türler** veya **başvurulan nesneler** ağacı, seçilen türün veya Örneğin başvurduğu nesneleri gösterir.

![Örnekler için başvurulan nesneler ağacı](../profiling/media/memuse_snapshotdetails_referencedobjects_instance.png "Örnekler için başvurulan nesneler ağacı")

Bir anlık görüntü ayrıntıları raporundaki **başvurulan türler** ağacı aşağıdaki sütunlara sahiptir. **Başvurulan bir nesne** ağacının **başvuru sayısı** sütunu yok.

|||
|-|-|
|**Nesne türü** veya **örneği**|Türün veya örneğin adı.|
|**Başvuru sayısı**|Türler için, türün nesne örneklerinin sayısı.|
|**Boyut (bayt)**|Bir tür için, türün tüm örneklerinin boyutu, türünde bulunan nesnelerin boyutu daha düşüktür.<br /><br /> Bir örnek için, nesnenin boyutu, nesne içindeki nesnelerin boyutu daha düşüktür.|
|**Kapsamlı boyut (bayt)**|İçerilen nesnelerin boyutu da dahil olmak üzere, türün örneklerinin toplam boyutu veya örneğin boyutu.|
|**Modül**|Nesneyi içeren modül.|

## <a name="snapshot-difference-diff-reports"></a>Anlık görüntü farkı (fark) raporları

Anlık görüntü farkı (fark) raporu, birincil anlık görüntü ve önceki anlık görüntü arasındaki değişiklikleri gösterir. Bir fark raporu açmak için, bir anlık görüntü bölmesindeki fark bağlantılarından birini seçin.

Her iki bağlantı de aynı raporu açar. Tek fark, rapordaki **yönetilen yığın** ağacının başlangıç sıralama sıraıdır. Boyut bağlantısı, raporu **kapsamlı boyut farkı (bayt)** sütunuyla sıralar. Nesneler bağlantısı, raporu **say farkı** sütununa göre sıralar. Sıralama sütununu veya sırayı rapor açıldıktan sonra değiştirebilirsiniz.

 ![Bir anlık görüntü bölmesindeki fark raporuna bağlantılar](../profiling/media/memuse_snapshotview_snapshotdifflinks.png "Bir anlık görüntü bölmesindeki fark raporuna bağlantılar")

### <a name="managed-heap-tree-snapshot-diff-reports"></a><a name="BKMK_Managed_Heap_tree__Snapshot_diff_"></a>Yönetilen yığın ağacı (anlık görüntü fark raporları)

 **Yönetilen yığın** ağacı bellekte tutulan nesne türlerini listeler. Türün en büyük on örneğini görüntülemek için bir tür adını genişletebilirsiniz, boyuta göre sıralanır. Seçili öğe için köke ve **başvurulan nesne** ağaçlarına **yönelik yolları** göstermek için bir tür veya örnek seçin.

 ![Fark raporundaki bir tür için yönetilen yığın ağacı](../profiling/media/memuse_snapshotdiff_type_heap.png "Fark raporundaki bir tür için yönetilen yığın ağacı")

Anlık görüntü farkı raporundaki **yönetilen yığın** ağacı aşağıdaki sütunlara sahiptir:

|||
|-|-|
|**Nesne türü**|Tür veya nesne örneğinin adı.|
|**Biriktirme**|Birincil anlık görüntüdeki bir türün örneklerinin sayısı. Bir örnek için **sayı** her zaman 1 ' dir.|
|**Sayı farkı**|Bir tür için, birincil anlık görüntü ve önceki anlık görüntü arasındaki türdeki örnek sayısı arasındaki fark. Alan, bir örnek için boştur.|
|**Boyut (bayt)**|Birincil anlık görüntüdeki nesnelerin boyutu, nesnelerdeki nesnelerin boyutu azalır. Bir tür için **Boyut (bayt)** ve **kapsamlı boyut (bayt)** , tür örneklerinin boyutlarının toplamıdır.|
|**Toplam boyut farkı (bayt)**|Bir tür için, birincil anlık görüntü ve önceki anlık görüntü arasındaki türdeki örneklerin toplam boyutunun, örneklerdeki nesnelerin boyutunu daha az olan farkı. Alan, bir örnek için boştur.|
|**Kapsamlı boyut (bayt)**|Nesnelerdeki nesnelerin boyutu da dahil olmak üzere, birincil anlık görüntüdeki nesnelerin boyutu.|
|**Kapsamlı boyut farkı (bayt)**|Bir tür için, nesne içindeki nesnelerin boyutu dahil olmak üzere birincil anlık görüntü ve önceki anlık görüntü arasındaki türün tüm örneklerinin boyutuyla aradaki fark. Alan, bir örnek için boştur.|
|**Modül**|Nesneyi içeren modül.|

### <a name="paths-to-root-tree-snapshot-diff-reports"></a><a name="BKMK_Paths_to_Root_tree__Snapshot_diff_"></a>Kök ağacına yönelik yollar (anlık görüntü fark raporları)

**Kök ağacına yönelik yollar** , bir türe veya örneğe başvuran nesne zincirini gösterir. .NET atık toplayıcısı, yalnızca tüm başvuruları serbest bırakıldığında bir nesne için belleği temizler.

**Kök ağaç yollarındaki** bir tür Için, **başvuru sayısı** sütununda bu türe başvuru tutan nesne sayısı görüntülenir. Önceki anlık görüntüdeki Count farkı, **başvuru farkı** sütununda bulunur.

 ![Fark raporundaki kök ağacına yönelik yollar](../profiling/media/memuse_snapshotdiff_pathstoroot_instance_all.png "Fark raporundaki kök ağacına yönelik yollar")

### <a name="referenced-types-or-referenced-objects-tree-snapshot-diff-reports"></a><a name="BKMK_Referenced_Objects_tree__Snapshot_diff_"></a>Başvurulan türler veya başvurulan nesneler ağacı (anlık görüntü fark raporları)

**Başvurulan türler** veya **başvurulan nesneler** ağacı, seçilen türün veya Örneğin başvurduğu nesneleri gösterir.

![Fark raporundaki başvurulan türler](../profiling/media/memuse_snapshotdiff_referencedtypes.png "Fark raporundaki başvurulan türler")

Bir anlık görüntü farkı raporundaki **başvurulan türler** ağacı aşağıdaki sütunlara sahiptir. **Başvurulan nesneler** ağacının **örneği**, **boyutu (bayt)**, **kapsamlı boyut (bayt)** ve **Modül** sütunları vardır.

|||
|-|-|
|**Nesne türü** veya **örneği**|Tür veya nesne örneğinin adı.|
|**Başvuru sayısı**|Birincil anlık görüntüdeki bir türün örneklerinin sayısı.|
|**Başvuru sayısı farkı**|Bir tür için, birincil anlık görüntü ve önceki anlık görüntü arasındaki türdeki örnek sayısı arasındaki fark.|
|**Boyut (bayt)**|Birincil anlık görüntüdeki nesnelerin boyutu, nesnelerdeki nesnelerin boyutu azalır. Bir tür için **Boyut (bayt)** ve **kapsamlı boyut (bayt)** , tür örneklerinin boyutlarının toplamıdır.|
|**Toplam boyut farkı (bayt)**|Bir tür için, birincil anlık görüntü ve önceki anlık görüntü arasındaki türdeki örneklerin toplam boyutunun, örneklerdeki nesnelerin boyutunu daha az olan farkı. |
|**Kapsamlı boyut (bayt)**|Nesnelerdeki nesnelerin boyutu da dahil olmak üzere, birincil anlık görüntüdeki nesnelerin boyutu.|
|**Kapsamlı boyut farkı (bayt)**|Bir tür için, nesne içindeki nesnelerin boyutu dahil olmak üzere birincil anlık görüntü ve önceki anlık görüntü arasındaki türün tüm örneklerinin boyutuyla aradaki fark.|
|**Modül**|Nesneyi içeren modül.|

## <a name="see-also"></a>Ayrıca bkz.
- [JavaScript belleği](../profiling/javascript-memory.md)
- [Visual Studio 'da profil oluşturma](../profiling/index.yml)
- [Profil oluşturma araçlarına ilk bakış](../profiling/profiling-feature-tour.md)
- [C++, C# ve Visual Basic kullanarak UWP uygulamaları için en iyi performans uygulamaları](/previous-versions/windows/apps/hh750313\(v\=win.10\))
- [Visual Studio 'da yeni bellek kullanımı aracı ile bellek sorunlarını tanılama](https://devblogs.microsoft.com/devops/diagnosing-memory-issues-with-the-new-memory-usage-tool-in-visual-studio/)