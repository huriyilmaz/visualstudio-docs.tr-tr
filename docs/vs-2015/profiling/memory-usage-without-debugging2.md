---
title: Debugging2 olmadan bellek kullanımı | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 24238fc0-40b8-4079-8579-698211db9a26
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 37db8a095e8f7b420f14df29de30f265aee49bb6
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/10/2020
ms.locfileid: "75850815"
---
# <a name="memory-usage-without-debugging"></a>Hata Ayıklayıcı Olmadan Bellek Kullanımı
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**Bellek kullanımı** aracını hata ayıklama olmadan, aşağıdakileri yapmak için kullanabilirsiniz  
  
- Bir senaryo geliştirirken, Visual Studio 'da uygulamanızın bellek kullanımını doğrudan izleyin.  
  
- Uygulamanızın belleğinin durumunun ayrıntılı anlık görüntülerini oluşturun.  
  
- Bellek sorunlarının kök nedenini bulmak için anlık görüntüleri karşılaştırın.  
  
  Bu konu, Windows Universal XAML uygulamasını çözümlemek için bellek kullanımı aracının nasıl kullanılacağını açıklar. JavaScript ve HTML kullanan Windows Evrensel uygulamalarında bellek kullanımını çözümlemek istiyorsanız, bkz. [bellek kullanımını çözümleme (JavaScript)](https://msdn.microsoft.com/library/windows/apps/jj819176.aspx).  
  
## <a name="BKMK_Start_a_Memory_Usage_diagnostic_session"></a>Bellek kullanımı Tanılama oturumu başlatma  
  
1. Visual Studio C# 'da bir Evrensel Windows projesi açın.  
  
2. Menü çubuğunda **Hata Ayıkla/performans profili Oluşturucu...** seçeneğini belirleyin.  
  
3. **Bellek kullanımı** ' nı seçin ve ardından sayfanın alt kısmındaki **Başlat** düğmesini seçin.  
  
     ![Bellek kullanımı Tanılama oturumu başlatma](../profiling/media/memuse-start-diagnosticssession.png "MEMUSE_Start_DiagnosticsSession")  
  
## <a name="BKMK_Monitor_memory_use"></a>Bellek kullanımını izleme  
 Sorunları bulmak ve gidermek için kullanabileceğiniz ayrıntılı raporlar oluşturmak üzere **bellek kullanımı** aracını kullanabilseniz de, etkin olarak geliştirmekte olduğunuz bir senaryonun gerçek zamanlı bellek efektlerini incelemek için de kullanabilirsiniz.  
  
 Bir Tanılama oturumu başlattığınızda, uygulamanız başlar ve **Tanılama araçları** penceresi, uygulamanızın bellek kullanımı için bir zaman çizelgesi grafiği görüntüler.  
  
 ![Bellek kullanımına genel bakış sayfası](../profiling/media/memuse-reportoverview.png "MEMUSE__ReportOverview")  
  
 Zaman çizelgesi grafiğinde, çalışırken uygulamanızın belleğindeki dalgalanmalar gösterilir. Grafikteki ani artışlar genellikle bazı kodların veri toplamasını veya oluşturmasını ve işlem tamamlandığında bu dosyayı atmaya işaret ediyor. Büyük ani artışlar, iyileştirebilecek olan bölgeleri gösterir. Daha fazla sorun, yetersiz bellek kullanımını veya hatta Bellek sızıntısını gösterebilen, döndürülmemiş bir bellek tüketimine sahiptir.  
  
### <a name="BKMK_Close_a_monitoring_session"></a>İzleme oturumunu kapatma  
 ![Toplamayı durdur](../profiling/media/memuse-stopcollection.png "MEMUSE__StopCollection")  
  
 Bir rapor oluşturmadan izleme oturumunu durdurmak için, yalnızca tanılama penceresini kapatmanız yeterlidir. Bellek anlık görüntülerini aldığınızda bir rapor oluşturmak için **Durdur**' u seçin.  
  
## <a name="BKMK_Take_snapshots_to_analyze_the_memory_state_of_your_app"></a>Uygulamanızın bellek durumunun anlık görüntülerini alın  
 Araştırmak istediğiniz bir bellek sorunu keşfettiğiniz zaman, nesneleri belirli bir süre içinde yakalamak için Tanılama oturumu sırasında anlık görüntü alabilirsiniz. Bir uygulama çok sayıda nesne türü kullandığından, analizinizi bir senaryoya göre yoğunlaşmak isteyebilirsiniz. Ayrıca, bir bellek sorunu görüntülenmeden önce uygulamanın temel anlık görüntüsünü almak ve bu senaryoyu tekrarlamanız durumunda sorunun ilk oluşumdan sonra bir veya daha fazla ek anlık görüntü olması iyi bir fikir olabilir.  
  
 Anlık görüntü toplamak için yeni bir Tanılama oturumu başlatın. Bellek verilerini yakalamak istediğinizde **anlık görüntü al** ' ı seçin. Bir rapor oluşturmak için **Durdur**' u seçin.  
  
## <a name="BKMK_Memory_Usage_overview_page"></a>Bellek kullanımına genel bakış sayfası  
 Veri toplamayı durdurduktan sonra, bellek kullanımı aracı uygulamayı durdurur ve genel bakış raporunu görüntüler.  
  
 ![Bellek kullanımına genel bakış sayfası](../profiling/media/memuse-reportoverview.png "MEMUSE__ReportOverview")  
  
### <a name="BKMK_Memory_Usage_snapshot_views"></a>Bellek kullanımı anlık görüntü görünümleri  
 Yeni Visual Studio Windows 'da ayrıntılı raporlar açmak için anlık görüntü görünümlerini kullanırsınız. İki tür anlık görüntü görünümü vardır:  
  
- [Anlık görüntü ayrıntıları raporları](../profiling/memory-usage-without-debugging2.md#BKMK_Snapshot_details_reports) , bir anlık görüntüdeki türleri ve örnekleri gösterir.  
  
- [Anlık görüntü farkı (fark) raporlarında](../profiling/memory-usage-without-debugging2.md#BKMK_Snapshot_difference__diff__reports) , iki anlık görüntüdeki türler ve örnekler karşılaştırılır.  
  
  ![Anlık görüntü görünümü bağlantıları](../profiling/media/memuse-snapshotview-numbered.png "MEMUSE__SnapshotView_Numbered")  
  
  Anlık görüntü görünümünün resimdeki numaralandırılmış öğeler, bellek kullanımı rapor görünümlerini açan bağlantılardır.  
  
|||  
|-|-|  
|![1. Adım](../profiling/media/procguid-1.png "ProcGuid_1")|Bağlantı metni, anlık görüntü çekilirken bellekteki toplam bayt sayısını gösterir.<br /><br /> Tür örneklerinin toplam boyutuna göre sıralanmış bir anlık görüntü ayrıntıları raporu göstermek için bu bağlantıyı seçin.|  
|![2. Adım](../profiling/media/procguid-2.png "ProcGuid_2")|Bağlantı metni, anlık görüntü çekilirken bellekteki toplam nesne sayısını gösterir.<br /><br /> Türlerin örnek sayısına göre sıralanan bir anlık görüntü ayrıntıları raporunu göstermek için bu bağlantıyı seçin.|  
|![3. Adım](../profiling/media/procguid-3.png "ProcGuid_3")|Bağlantı metni, bu anlık görüntünün şu andaki toplam nesne boyutu ve önceki anlık görüntünün toplam boyutu arasındaki farkı gösterir.<br /><br /> Bu anlık görüntünün bellek boyutu öncekinden daha büyükse ve boyut daha küçükse negatif bir sayı olduğunda bağlantı metni pozitif bir sayıdır. Bağlantı metni **taban çizgisi** , bu anlık görüntünün tanılama oturumunda ilk olduğunu belirtir; **Fark** , farkın sıfır olduğunu gösterir.<br /><br /> Bu bağlantıyı, türlerin örneklerinin toplam boyutundaki farka göre sıralanmış bir anlık görüntü fark raporu göstermek için seçin.|  
|![4. Adım](../profiling/media/procguid-4.png "ProcGuid_4")|Bağlantı metni, bu anlık görüntüdeki toplam bellek nesnesi sayısı ve önceki anlık görüntüdeki nesne sayısı arasındaki farkı gösterir.<br /><br /> Türlerin toplam örnek sayısı içindeki farka göre sıralanan bir anlık görüntü fark raporu göstermek için bu bağlantıyı seçin.|  
  
## <a name="BKMK_Snapshot_reports"></a>Anlık görüntü raporları  
 ![Bellek kullanımı anlık görüntü raporu](../profiling/media/memuse-snapshotreport-all.png "MEMUSE_SnapshotReport_All")  
  
### <a name="BKMK_Snapshot_report_trees"></a>Anlık görüntü rapor ağaçları  
  
#### <a name="BKMK_Managed_Heap"></a>Yönetilen yığın  
 Yönetilen yığın ağacı [yönetilen yığın ağacı (anlık görüntü ayrıntıları)](../profiling/memory-usage-without-debugging2.md#BKMK_Managed_Heap_tree__Snapshot_details_) ve [yönetilen yığın ağacı (anlık görüntü farkı)](../profiling/memory-usage-without-debugging2.md#BKMK_Managed_Heap_tree__Snapshot_diff_) rapordaki türleri ve örnekleri gösterir. Bir tür veya örnek seçildiğinde seçili öğe için kök ve **başvurulan nesne** ağaçlarına **yönelik yollar** görüntülenir.  
  
#### <a name="BKMK_Paths_to_Root"></a>Köke yönelik yollar  
 [Kök ağacın (anlık görüntü ayrıntıları) yolları](../profiling/memory-usage-without-debugging2.md#BKMK_Paths_to_Root_tree__Snapshot_details_) ve [kök ağacın yolları (Snapshot diff)](../profiling/memory-usage-without-debugging2.md#BKMK_Paths_to_Root_tree__Snapshot_diff_) , türe veya örneğe başvuran nesne zincirini gösterir. Çöp toplayıcı .NET Framework, yalnızca tüm başvuruları serbest bırakıldığında bir nesne için belleği temizler.  
  
#### <a name="BKMK_Referenced_Objects"></a>Başvurulan nesneler  
 [Başvurulan nesneler ağacı (anlık görüntü ayrıntıları)](../profiling/memory-usage-without-debugging2.md#BKMK_Referenced_Objects_tree__Snapshot_details_) ve [başvurulan nesneler ağacı (Snapshot diff)](../profiling/memory-usage-without-debugging2.md#BKMK_Referenced_Objects_tree__Snapshot_diff_) , seçilen türün veya örnek başvurduğu nesneleri gösterir.  
  
### <a name="BKMK_Object_Type_and_Instance_fields"></a>Nesne türü ve örnek alanları  
 Bir **nesne türü** girdisinde alt girişler olduğunda, bunları göstermek için ok simgesini seçebilirsiniz. **Nesne türü** metninin rengi mavi ise, kaynak kodu dosyasındaki nesnesine gitmek için bunu seçebilirsiniz. Kaynak dosya ayrı bir pencerede açılır.  
  
 Örnek adları, bellek kullanımı aracı tarafından oluşturulan benzersiz kimliklerdir.  
  
 Kolayca belirleyemediğinizde bir tür fark ederseniz veya kodunuza nasıl dahil olduğunu bilmiyorsanız, büyük olasılıkla bir .NET Framework, işletim sistemi veya derleyicinin, ' nin sahiplik zincirlerine dahil olduğu için bellek kullanım aracının görüntülediği bir nesnedir. nesneleriniz.  
  
### <a name="BKMK_Report_tree_filters_"></a>Rapor ağacı filtreleri  
 Çoğu uygulama, çoğu uygulama geliştiricisi için çok ilginç olmayan çok sayıda tür içerir. **Bellek kullanımı** Aracı, **yönetilen yığında** bu türlerin çoğunu ve kök ağaçlara **yolları** gizlemek için kullanabileceğiniz iki filtre tanımlar. Ayrıca, bir ağacı tür adına göre filtreleyebilirsiniz.  
  
 ![Sıralama ve filtreleme seçenekleri](../profiling/media/memuse-sortandfilter.png "MEMUSE_SortAndFilter")  
  
#### <a name="BKMK_Filter"></a>Filtreyle  
 Ağaç ekranların belirtilen metni içeren türlerle kısıtlanmasını sağlamak için **filtre** kutusuna bir dize girin. Filtre, büyük/küçük harfe duyarlı değildir ve tür adlarının herhangi bir bölümünde belirtilen dizeyi tanır.  
  
#### <a name="BKMK_Collapse_Small_Objects"></a>Küçük nesneleri Daralt  
 Bu filtre uygulandığında, **boyutu (bayt)** , anlık görüntü belleğinin toplam boyutunun yüzde 0,5 ' inden daha düşük olan türler **yönetilen yığın** listesinde gizlenir.  
  
#### <a name="BKMK_Just_My_Code"></a>Yalnızca kendi kodum  
 **Yalnızca kendi kodum** filtresi, dış kod tarafından oluşturulan örneklerin çoğunu gizler. Dış türlerin, işletim sistemine veya çerçeve bileşenlerine aittir veya derleyici tarafından oluşturulur.  
  
## <a name="BKMK_Snapshot_details_reports"></a>Anlık görüntü ayrıntıları raporları  
 Bir tanılama oturumundan bir anlık görüntüye odaklanmak için bir anlık görüntü ayrıntıları raporu kullanırsınız. Bir ayrıntılar raporu açmak için, aşağıdaki resimde gösterildiği gibi bir anlık görüntü görünümündeki bağlantılardan birini seçin. Her iki bağlantı de aynı raporu açar; Tek fark, rapordaki **yönetilen yığın** ağacının başlangıç sıralama sıraıdır. Her iki durumda da, rapor açıldıktan sonra sıralama düzenini değiştirebilirsiniz.  
  
 ![Anlık görüntü görünümündeki anlık görüntü raporuna bağlantılar](../profiling/media/memuse-snapshotview-snapshotdetailslinks.png "MEMUSE_SnapshotView_SnapshotDetailsLinks")  
  
- **MB** bağlantısı, raporu **kapsamlı boyut (bayt)** sütununa göre sıralar.  
  
- **Nesneler** bağlantısı, raporu **say** sütununa göre sıralar.  
  
### <a name="BKMK_Managed_Heap_tree__Snapshot_details_"></a>Yönetilen yığın ağacı (anlık görüntü ayrıntıları)  
 **Yönetilen yığın** ağacı bellekte tutulan nesne türlerini listeler. Türün en büyük on örneğini görüntülemek için bir tür adını genişletebilirsiniz, boyuta göre sıralanır. Bir tür veya örnek seçildiğinde seçili öğe için kök ve **başvurulan nesne** ağaçlarına **yönelik yollar** görüntülenir.  
  
 ![Yönetilen yığın ağacı](../profiling/media/memuse-snapshotdetails-managedheaptree.png "MEMUSE__SnapshotDetails_ManagedHeapTree")  
  
|||  
|-|-|  
|**Nesne türü**|Tür veya nesne örneğinin adı.|  
|**Biriktirme**|Türün nesne örneklerinin sayısı. Bu sayı her zaman bir örnek için 1 ' dir.|  
|**Boyut (bayt)**|Bir tür için, örneklerin içerdiği nesnelerin boyutu hariç olmak üzere, bellek anlık görüntüsünde türün tüm örneklerinin boyutu.<br /><br /> Örnek için, örneğinde bulunan nesnelerin boyutunu dışlayarak nesnenin boyutunu yazın. larında.|  
|**Kapsamlı boyut (bayt)**|İçerilen nesnelerin boyutu da dahil olmak üzere, türünün örneklerinin boyutu veya tek bir örneğin boyutu.|  
  
### <a name="BKMK_Paths_to_Root_tree__Snapshot_details_"></a>Kök ağacına yönelik yollar (anlık görüntü ayrıntıları)  
 **Kök ağacına yönelik yollar** , türe veya örneğe başvuran nesne zincirini gösterir. Çöp toplayıcı .NET Framework, yalnızca tüm başvuruları serbest bırakıldığında bir nesne için belleği temizler.  
  
 ![Türler için kök ağacına yönelik yollar](../profiling/media/memuse-snapshotdetails-type-pathstoroottree.png "MEMUSE_SnapshotDetails_Type_PathsToRootTree")  
  
 **Kök ağaç yollarındaki** bir türü görüntülediğinizde, **başvuru sayısı** sütununda bu türe başvuruları tutan türlerin nesne sayısı görüntülenir. Bir örneği çözümlediğinizde sütun görünmez.  
  
### <a name="BKMK_Referenced_Objects_tree__Snapshot_details_"></a>Başvurulan nesneler ağacı (anlık görüntü ayrıntıları)  
 **Başvurulan nesneler** ağacı, seçilen türün veya Örneğin başvurduğu nesneleri gösterir.  
  
 ![Örnekler için başvurulan objeler ağacı](../profiling/media/memuse-snapshotdetails-referencedobjects-instance.png "MEMUSE_SnapshotDetails_ReferencedObjects_Instance")  
  
|||  
|-|-|  
|**Nesne türü/örneği**|Tür veya nesne örneğinin adı.|  
|**Boyut (bayt)**|Bir tür için, türün içindeki nesnelerin boyutu hariç olmak üzere, türünün tüm örneklerinin boyutu.<br /><br /> Bir örnek için, nesnesinin içindeki nesnelerin boyutu hariç nesnenin boyutu.|  
|**Kapsamlı boyut (bayt)**|İçerilen nesnelerin boyutu da dahil olmak üzere, türün örneklerinin toplam boyutu veya örnek boyutu.|  
  
## <a name="BKMK_Snapshot_difference__diff__reports"></a>Anlık görüntü farkı (fark) raporları  
 Anlık görüntü farkı (fark) raporu, birincil anlık görüntü ve hemen öncesinde alınmış anlık görüntü arasındaki değişiklikleri gösterir. Bir fark raporu açmak için, aşağıdaki resimde gösterildiği gibi bir anlık görüntü görünümündeki bağlantılardan birini seçin. Her iki bağlantı de aynı raporu açar; Tek fark, rapordaki **yönetilen yığın** ağacının başlangıç sıralama sıraıdır. Sıralama düzenini rapor açıldıktan sonra değiştirebilirsiniz.  
  
 ![Bir anlık görüntü görünümündeki fark raporunun bağlantıları](../profiling/media/memuse-snapshotview-snapshotdifflinks.png "MEMUSE_SnapshotView_SnapshotDiffLinks")  
  
- **MB** bağlantısı, raporu **kapsamlı boyut (bayt)** sütununa göre sıralar.  
  
- **Nesneler** bağlantısı, raporu **say** sütununa göre sıralar.  
  
### <a name="BKMK_Managed_Heap_tree__Snapshot_diff_"></a>Yönetilen yığın ağacı (anlık görüntü farkı)  
 **Yönetilen yığın** ağacı bellekte tutulan nesne türlerini listeler. Türün en büyük on örneğini görüntülemek için bir tür adını genişletebilirsiniz, boyuta göre sıralanır. Bir tür veya örnek seçildiğinde seçili öğe için kök ve **başvurulan nesne** ağaçlarına **yönelik yollar** görüntülenir.  
  
 ![Fark raporundaki bir tür için yönetilen yığın ağacı](../profiling/media/memuse-snapshotdiff-type-heap.png "MEMUSE_SnapshotDiff_Type_Heap")  
  
 **Sayı**, **Boyut (bayt)** ve **kapsamlı boyut (bayt)** sütunlarının resimde daraltıldığına dikkat edin.  
  
|||  
|-|-|  
|**Nesne türü**|Tür veya nesne örneğinin adı.|  
|**Biriktirme**|Birincil anlık görüntüdeki bir türün örneklerinin sayısı. Bir örnek için **sayı** her zaman 1 ' dir.|  
|**Sayı farkı**|Bir tür için, birincil anlık görüntü ve önceki anlık görüntü arasındaki türdeki örnek sayısı arasındaki fark. Alan, bir örnek için boştur.|  
|**Boyut (bayt)**|Nesneler içindeki nesnelerin boyutu hariç olmak üzere birincil anlık görüntüdeki nesnelerin boyutu. Bir tür için **Boyut (bayt)** ve **kapsamlı boyut (bayt)** , tür örneklerinin boyutlarının toplamıdır.|  
|**Toplam boyut farkı (bayt)**|Bir tür için, örneklerin içerdiği nesnelerin boyutu hariç olmak üzere birincil anlık görüntü ve önceki anlık görüntü arasındaki örneklerin toplam boyutunun farkı. Alan, bir örnek için boştur.|  
|**Kapsamlı boyut (bayt)**|Nesneler içindeki nesnelerin boyutu da dahil olmak üzere, birincil anlık görüntüdeki nesnelerin boyutu.|  
|**Kapsamlı boyut farkı (bayt)**|Bir tür için, birincil anlık görüntü ve önceki anlık görüntü arasındaki, nesnelerin içerdiği nesnelerin boyutu dahil olmak üzere, türün tüm örneklerinin boyutuyla aradaki fark. Alan, bir örnek için boştur.|  
  
### <a name="BKMK_Paths_to_Root_tree__Snapshot_diff_"></a>Kök ağacına yönelik yollar (anlık görüntü farkı)  
 **Kök ağacına yönelik yollar** , türe veya örneğe başvuran nesne zincirini gösterir. Çöp toplayıcı .NET Framework, yalnızca tüm başvuruları serbest bırakıldığında bir nesne için belleği temizler.  
  
 ![Fark görünümündeki örnekler için kök ağacına yönelik yollar](../profiling/media/memuse-snapshotdiff-pathstoroot-instance-all.png "MEMUSE_SnapshotDiff_PathsToRoot_Instance_All")  
  
### <a name="BKMK_Referenced_Objects_tree__Snapshot_diff_"></a>Başvurulan nesneler ağacı (anlık görüntü farkı)  
 **Başvurulan nesneler** ağacı, birincil türün veya Örneğin başvurduğu nesneleri gösterir.  
  
 ![Örnekler için başvurulan objeler ağacı](../profiling/media/memuse-snapshotdetails-referencedobjects-instance.png "MEMUSE_SnapshotDetails_ReferencedObjects_Instance")  
  
|||  
|-|-|  
|**Nesne türü/örneği**|Tür veya nesne örneğinin adı.|  
|**Boyut (bayt)**|Örnek için, örneğin, birincil anlık görüntüdeki nesnenin boyutu, örnekteki nesnelerin boyutu hariç.<br /><br /> Bir tür için, örnekte yer alan nesnelerin boyutu hariç olmak üzere birincil anlık görüntüdeki tür örneklerinin toplam boyutu.|  
|**Kapsamlı boyut (bayt)**|Nesneler içindeki nesnelerin boyutu da dahil olmak üzere, birincil anlık görüntüdeki nesnelerin boyutu.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [JavaScript bellek](../profiling/javascript-memory.md)   
 [Uygulama performansını analiz](https://msdn.microsoft.com/library/58acb30b-8428-41a6-b195-b0fdedb89575)   
 [Performans ve tanılama araçlarını çalıştırın](https://msdn.microsoft.com/library/788279d8-f56b-40a0-9bef-facc3dfba471)   
 [ C++, C#Ve Visual Basic kullanarak Windows Mağazası uygulamaları için en iyi performans uygulamaları](https://msdn.microsoft.com/library/windows/apps/hh750313.aspx)   
 [Visual Studio 'da yeni bellek kullanımı aracı ile bellek sorunlarını tanılama](https://blogs.msdn.com/b/visualstudioalm/archive/2014/04/02/diagnosing-memory-issues-with-the-new-memory-usage-tool-in-visual-studio.aspx)
