---
title: Uygulamalarınızdaki bellek kullanımını ölçme
description: Hata ayıklama tümleşik tanı aracıyla hata ayıklama yaparken bellek sızıntılarını ve verimsiz belleği bulun.
ms.custom: seodec18
ms.date: 04/25/2018
ms.topic: tutorial
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dc0d97b1e2b2e27ebc8ddb898795c1767155c1cb
ms.sourcegitcommit: ee12b14f306ad8f49b77b08d3a16d9f54426e7ca
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2020
ms.locfileid: "80256198"
---
# <a name="measure-memory-usage-in-visual-studio"></a>Visual Studio'da bellek kullanımını ölçün

Hata ayıklama tümleşik **Bellek Kullanımı** tanı aracıyla hata ayıklama yaparken bellek sızıntılarını ve verimsiz belleği bulun. Bellek Kullanımı aracı, nesne türlerinin bellek kullanım etkisini anlamanıza yardımcı olmak için yönetilen ve yerel bellek yığınının bir veya daha fazla *anlık görüntüsünü* almanızı sağlar. .NET, yerel veya karma mod (.NET ve yerel) uygulamalarının anlık görüntülerini toplayabilirsiniz.

Aşağıdaki grafikte **Tanılama Araçları** penceresi (Visual Studio 2015 Update 1 ve sonraki sürümlerde mevcuttur) gösterilmektedir:

![DiagnosticTools&#45;Güncelleme1](../profiling/media/diagnostictools-update1.png "DiagnosticTools-Update1")

**Bellek Kullanımı** aracında istediğiniz zaman bellek anlık görüntülerini toplayabiliyor olsanız da, uygulamanızın performans sorunlarını araştırırken nasıl yürütüldünüzü denetlemek için Visual Studio hata ayıklama aracını kullanabilirsiniz. Kesme noktaları ayarlama, adım atma, Tümehata ayıklama eylemleri ve diğer hata ayıklama eylemleri, performans araştırmalarınızı en alakalı kod yollarına odaklamanıza yardımcı olabilir. Uygulamanız çalışırken bu eylemleri gerçekleştirmek, sizi ilginizi çekemeyen koddaki gürültüyü ortadan kaldırabilir ve bir sorunu tanılamanız için gereken süreyi önemli ölçüde azaltabilir.

Hata ayıklamanın dışındaki bellek aracını da kullanabilirsiniz. [Hata ayıklama olmadan Bellek Kullanımı'na](../profiling/memory-usage-without-debugging2.md)bakın. Profil oluşturma araçlarını Windows 7 ve sonraki lerle bağlı hata ayıklama olmadan kullanabilirsiniz. Windows 8 ve daha sonra hata ayıklama **(Tanılama Araçları** penceresi) ile profil oluşturma araçları çalıştırmak için gereklidir.

> [!NOTE]
> **Özel Tahsis Desteği** Yerel bellek profilleyicisi, çalışma süresi boyunca yayılan ayırma [ETW](/windows-hardware/drivers/devtest/event-tracing-for-windows--etw-) olay verilerini toplayarak çalışır.  CRT ve Windows SDK'daki tahsisatörler, ayırma verilerinin yakalanması için kaynak düzeyinde açıklamalı olarak eklenmiştir. Kendi ayırıcılarınızı yazıyorsanız, işaretçiyi yeni ayrılan yığın belleğe döndüren işlevler, myMalloc için bu örnekte görüldüğü gibi [__declspec](/cpp/cpp/declspec)(ayırıcı) ile dekore edilebilir:
>
> `__declspec(allocator) void* myMalloc(size_t size)`

Bu öğreticide şunları yapacaksınız:

> [!div class="checklist"]
> * Belleğin anlık görüntülerini alma
> * Bellek kullanım verilerini analiz edin

## <a name="collect-memory-usage-data"></a>Bellek kullanım verilerini toplama

1. Visual Studio'da hata ayıklamak istediğiniz projeyi açın ve bellek kullanımını incelemeye başlamak istediğiniz noktada uygulamanızda bir kesme noktası ayarlayın.

    Bellek sorunundan şüphelendiğiniz bir alanınız varsa, bellek sorunu oluşmadan önce ilk kesme noktasını ayarlayın.

    > [!TIP]
    > Çünkü uygulamanız sık sık bellek ayırDığında ve ayırdığında ilginizi çeken bir işlemin bellek profilini yakalamak zor olabilir, tam noktayı bulmak için işlemin başlangıcında ve sonunda kesme noktaları ayarlamak (veya işlem boyunca adım) bellek değişti.

2. Çözümlemek istediğiniz işlevin veya kod bölgesinin sonunda (veya şüpheli bir bellek sorunu oluştuktan sonra) ikinci bir kesme noktası ayarlayın.

3. **Tanılama Araçları** penceresi, siz kapatmadığınız sürece otomatik olarak görüntülenir. Pencereyi yeniden açmak için **Hata Ayıklama** > **Windows** > **Show Tanılama Araçları'nı**tıklatın.

4. Araç çubuğundaki **Araçları Seç** ayarı ile **Bellek Kullanımını** seçin.

     ![Tanılama Araçlarını Göster](../profiling/media/diag-tools-select-tool-2.png "DiagToolsSelectTool")

5. **Hata Ayıklama '** nı Başlat ' ı tıklatın (veya araç çubuğunda **başlat** veya **F5).**

     Uygulama yüklemeyi bitirdiğinde, Tanılama Araçlarının Özet görünümü görüntülenir.

     ![Tanılama Araçları Özet Sekmesi](../profiling/media/diag-tools-summary-tab-2.png "DiagToolsSummaryTab")

     > [!NOTE]
     > Bellek verilerinin toplanması yerel veya karma modlu uygulamalarınızın hata ayıklama performansını etkileyebileceğinden, bellek anlık görüntüleri varsayılan olarak devre dışı bırakılır. Yerel veya karma modlu uygulamalarda anlık görüntüleri etkinleştirmek için hata ayıklama oturumu başlatın (Kısayol tuşu: **F5).** **Tanılama Araçları** penceresi göründüğünde, **Bellek Kullanımı** sekmesini seçin ve ardından **Yığın Profil Oluşturma'yı**seçin.
     >
     >  ![Anlık görüntüleri etkinleştirme](../profiling/media/dbgdiag_mem_mixedtoolbar_enablesnapshot.png "DBGDIAG_MEM_MixedToolbar_EnableSnapshot")
     >
     >  Durdur (Kısayol tuşu: **Shift**+**F5**) ve hata ayıklamayeniden başlatın.

6. Hata ayıklama oturumunuzun başında anlık görüntü almak için **Bellek Kullanımı** özeti araç çubuğunda anlık **görüntü al'ı** seçin. (Burada da bir kırılma noktası ayarlamak için yardımcı olabilir.)

    ![Anlık görüntü alma](../profiling/media/dbgdiag_mem_mixedtoolbar_takesnapshot.png "DBGDIAG_MEM_MixedToolbar_TakeSnapshot")

     > [!TIP]
     > Bellek karşılaştırmaları için bir temel oluşturmak için hata ayıklama oturumunuzun başında anlık görüntü almayı düşünün.

6. İlk kesme noktanızın vurulmasına neden olacak senaryoyu çalıştırın.

7. Hata ayıklama ilk kesme noktasında duraklatılmış olsa da, **Bellek Kullanımı** özeti araç çubuğunda anlık görüntü **al'ı** seçin.

8. Uygulamayı ikinci kesme noktanıza çalıştırmak için **F5** tuşuna basın.

9. Şimdi, başka bir fotoğraf çekin.

     Bu noktada, verileri çözümlemeye başlayabilirsiniz.

## <a name="analyze-memory-usage-data"></a>Bellek kullanım verilerini analiz edin
Bellek Kullanımı özet tablosu satırları hata ayıklama oturumu sırasında aldığınız anlık görüntüleri listeler ve daha ayrıntılı görünümlere bağlantılar sağlar.

![Bellek özet tablosu](../profiling/media/dbgdiag_mem_summarytable.png "DBGDIAG_MEM_SummaryTable")

 Sütunların adı, proje özelliklerinde seçtiğiniz hata ayıklama moduna bağlıdır: .NET, yerel veya karışık (hem .NET hem de yerel).

- **Nesneler (Diff)** ve **Ayırmalar (Diff) sütunları** anlık görüntü alındığında .NET ve yerel bellekteki nesnelerin sayısını görüntüler.

- **Yığın Boyutu (Diff)** sütunu .NET ve yerel yığınlarda bayt sayısını görüntüler

Birden çok anlık görüntü aldığınızda, özet tablosunun hücreleri satır anlık görüntüsü ile önceki anlık görüntü arasındaki değer değişikliğini içerir.

Bellek kullanımını çözümlemek için, ayrıntılı bir bellek kullanımı raporunu açan bağlantılardan birini tıklatın:

- Geçerli anlık görüntü ile önceki anlık görüntü arasındaki farkın ayrıntılarını görüntülemek için, okun solundaki değiştir bağlantısını![(Bellek Kullanımı Artırım)](../profiling/media/prof-tour-mem-usage-up-arrow.png "Bellek Kullanımı Nın Artması")seçin. Kırmızı ok bellek kullanımında bir artış gösterir ve bir azalma gösterir yeşil ok.

> [!TIP]
> Bellek sorunlarını daha hızlı tanımlamaya yardımcı olmak için, diff raporları genel sayıda en çok artan nesne türlerine göre sıralanır **(Nesneler (Diff)** sütununda değişiklik bağlantısını tıklatın) veya genel yığın boyutunda en çok artırılan nesne türlerine göre sıralanır **(Yığın Boyutu (Diff)** sütunundaki değişiklik bağlantısını tıklatın).

- Yalnızca seçili anlık görüntünün ayrıntılarını görüntülemek için değiştirilmeyen bağlantıyı tıklatın.

   Rapor ayrı bir pencerede görüntülenir.

### <a name="managed-types-reports"></a>Yönetilen türleri raporları
 Bellek Kullanımı özet tablosundaki **Nesneler (Diff)** veya **Ayırmalar (Diff)** hücresinin geçerli bağlantısını seçin.

 ![Hata ayıklama, Yollar'ı Köke &#45; tür raporu yönetti](../profiling/media/dbgdiag_mem_managedtypesreport_pathstoroot.png "DBGDIAG_MEM_ManagedTypesReport_PathsToRoot")

 Üst bölme, türe **(Kapsayıcı Boyut)** başvuran tüm nesnelerin boyutu da dahil olmak üzere anlık görüntüdeki türlerin sayısını ve boyutunu gösterir.

 Alt bölmedeki Kök lere **Giden Yollar** ağacı, üst bölmede seçilen türe başvuran nesneleri görüntüler. .NET çöp toplayıcısı, yalnızca yayımlandığı son türde bir nesnenin belleği temizler.

 **Başvurulan Nesneler** ağacı, üst bölmede seçilen türtarafından tutulan başvuruları görüntüler.

 ![Yönetilen başvurulan nesneler rapor görünümü](../profiling/media/dbgdiag_mem_managedtypesreport_referencedtypes.png "DBGDIAG_MEM_ManagedTypesReport_ReferencedTypes")

 Seçili tür örneklerini üst bölmede görüntülemek için ![Örnek simgesi simgesini](../profiling/media/dbgdiag_mem_instanceicon.png "DBGDIAG_MEM_InstanceIcon") seçin.

 ![Örnek görünümü](../profiling/media/dbgdiag_mem_managedtypesreport_instances.png "DBGDIAG_MEM_ManagedTypesReport_Instances")

 **Örnekler** görünümü, üst bölmedeki anlık görüntüde seçili nesnenin örneklerini görüntüler. **Kök ve** **Başvurulan Nesnelere** Giden Yollar bölmesi, seçili örneğe başvuran nesneleri ve seçili örnek başvurularının yaptığı türleri görüntüler. Hata ayıklama anlık görüntünün alındığı noktada durdurulduğunda, nesnenin değerlerini bir araç ucunda görüntülemek için **Değer** hücresinin üzerinde gezinebilirsiniz.

### <a name="native-type-reports"></a>Yerel tür raporları
 **Tanılama Araçları** penceresinin Bellek Kullanımı özet tablosundaki **Ayırmalar (Diff)** veya **Yığın Boyutu (Diff)** hücresinin geçerli bağlantısını seçin.

 ![Yerel Tür Görünümü](../profiling/media/dbgdiag_mem_native_typesview.png "DBGDIAG_MEM_Native_TypesView")

 **Tür görünümü,** anlık görüntüdeki türlerin sayısını ve boyutunu görüntüler.

- Anlık görüntüde seçili türdeki nesnelerle ilgili bilgileri görüntülemek için seçili türdeki örnekler![simgesini (Nesne Türü sütunundaki örnek simgesi)](../profiling/media/dbg_mma_instancesicon.png "DBG_MMA_InstancesIcon")seçin.

     **Örnekler** görünümü, seçili türün her örneğini görüntüler. Örnek seçmek, **Ayırma Çağrısı Yığını** bölmesinde örneğin oluşturulmasıyla sonuçlanan çağrı yığınını görüntüler.

     ![Örnek görünümü](../profiling/media/dbgdiag_mem_native_instances.png "DBGDIAG_MEM_Native_Instances")

- Seçili türe ait ayırma yığınını görmek için **Görünüm Modu** listesinde **Yığınlar Görünümü'nu** seçin.

     ![Yığınlar Görünümü](../profiling/media/dbgdiag_mem_native_stacksview.png "DBGDIAG_MEM_Native_StacksView")

### <a name="change-diff-reports"></a>Change (Diff) raporları

- **Tanılama Araçları** penceresindebellek **kullanımı** sekmesinin özet tablosunun hücresindeki değişiklik bağlantısını seçin.

   ![Diff&#41; raporu &#40;bir değişiklik seçin](../profiling/media/dbgdiag_mem_choosediffreport.png "DBGDIAG_MEM_ChooseDiffReport")

- Yönetilen veya yerel raporun **Karşılaştırma** listesinde bir anlık görüntü seçin.

   ![Karşılaştırma listesinden anlık görüntü seçin](../profiling/media/dbgdiag_mem_choosecompareto.png "DBGDIAG_MEM_ChooseCompareTo")

Değişiklik raporu, temel anlık görüntü değeri ile karşılaştırma anlık görüntüsü arasındaki farkı gösteren temel rapora sütun **((Diff)** ile işaretlenmiş) ekler. Yerel Yazı Görünümü diff raporu şu şekilde görünebilir:

![Yerel Türleri Diff Görünümü](../profiling/media/dbgdiag_mem_native_typesviewdiff.png "DBGDIAG_MEM_Native_TypesViewDiff")

## <a name="blogs-and-videos"></a>Bloglar ve videolar

[Hata Ayıklama sırasında CPU ve Bellek analiz](https://devblogs.microsoft.com/visualstudio/analyze-cpu-memory-while-debugging/)

[Visual C++ Blog: Visual C++ 2015'te Bellek Profilleme](https://devblogs.microsoft.com/cppblog/memory-profiling-in-visual-c-2015/)

## <a name="next-steps"></a>Sonraki adımlar

Bu eğitimde, bellek kullanım verilerini nasıl toplayıp analiz edeceğiz öğrendiniz. [Profil oluşturucuturunu](../profiling/profiling-feature-tour.md)zaten tamamladıysanız, uygulamalarınızdaki CPU kullanımını nasıl analiz ettiğinize hızlıca bir göz atmak isteyebilirsiniz.

> [!div class="nextstepaction"]
> [CPU kullanımını analiz edin](../profiling/beginners-guide-to-performance-profiling.md)
