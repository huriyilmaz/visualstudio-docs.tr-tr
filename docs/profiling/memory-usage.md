---
title: Uygulamalarınız için bellek kullanımını ölçme
description: Hata ayıklayıcısıyla tümleşik tanılama aracıyla hata ayıklarken bellek sızıntılarını ve verimsiz belleği bulun.
ms.custom: seodec18
ms.date: 04/25/2018
ms.topic: tutorial
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 801af259243a67b7c41d23abad501ba32b351406
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126626894"
---
# <a name="measure-memory-usage-in-visual-studio"></a>Visual Studio’da bellek kullanımını ölçme

Hata ayıklayıcısıyla tümleşik Bellek Kullanımı tanılama aracıyla hata ayıklarken bellek sızıntılarını ve **verimsiz belleği** bulun. Bellek Kullanımı aracı, nesne türlerinin  bellek kullanım etkisini anlamanıza yardımcı olmak için yönetilen ve yerel bellek yığınının bir veya daha fazla anlık görüntüsünü alasınız. Ayrıca, hata ayıklayıcı ekli olmadan veya çalışan bir uygulamayı hedefleerek bellek kullanımını analiz edin. Daha fazla bilgi için [bkz. Hata ayıklayıcı ile veya hata ayıklayıcı olmadan profil oluşturma araçlarını çalıştırma.](../profiling/running-profiling-tools-with-or-without-the-debugger.md)

Bellek Kullanımı aracında herhangi bir zamanda  bellek anlık görüntüleri toplayabilirsiniz, ancak performans sorunlarını incelerken Visual Studio yürütmeyi kontrol etmek için Visual Studio hata ayıklayıcısını kullanabilirsiniz. Kesme noktaları, adımlama, Hepsini Kır ve diğer hata ayıklayıcı eylemlerini ayarlama, performans araştırmalarınızı en alakalı kod yollarından odaklanmanıza yardımcı olabilir. Uygulama çalışırken bu eylemleri gerçekleştirmek, ilginizi olmayan kod kirliliğini ortadan kaldırabilir ve bir sorunu tanılamak için gereken zamanı önemli ölçüde azaltabilir.

> [!Important]
> hata ayıklayıcısı ile tümleşik Tanılama Araçları Visual Studio, ASP.NET, ASP.NET Core, yerel/C++ geliştirme ve karma mod (.NET ve yerel) uygulamaları dahil olmak üzere Visual Studio'de .NET geliştirmesi için de desteklemektedir. Windows 8 aracılarını hata ayıklayıcısıyla (profil oluşturma **penceresiyle)** çalıştırmak için Tanılama Araçları gerekir.

Bu öğreticide şunları yapacaksınız:

> [!div class="checklist"]
> * Belleğin anlık görüntülerini alma
> * Bellek kullanım verilerini analiz etme

Bellek **Kullanımı** size ihtiyacınız olan verileri vermezse, Performans Profili Oluşturucu profil [](../profiling/profiling-feature-tour.md#post_mortem) oluşturma araçları size yardımcı olacak farklı türlerde bilgiler sağlar. Çoğu durumda, cpu, işleme kullanıcı arabirimi veya ağ isteği süresi gibi bellek dışında bir şey, uygulama performans sorununa neden olabilir.

> [!NOTE]
> **Özel Tümleyici Desteği** Yerel bellek profili oluşturma, çalışma zamanında yayılan [ayırma ETW](/windows-hardware/drivers/devtest/event-tracing-for-windows--etw-) olay verilerini toplayarak çalışır.  CRT ve Windows SDK'sı'nda, ayırma verileri yakalanıp yakalanamaları için kaynak düzeyinde ek açıklama ek açıklama ek açıklamalarına sahip olan ayırmalar. Kendi ayırıcılarınızı yazıyorsanız, bu myMalloc örneğinde olduğu gibi, yeni [](/cpp/cpp/declspec)ayrılan yığın belleğine işaretçisi __declspec (ayırıcı) ile dekore edilmiş olabilir:
>
> `__declspec(allocator) void* myMalloc(size_t size)`

## <a name="collect-memory-usage-data"></a>Bellek kullanım verilerini toplama

1. Hata ayıklamak istediğiniz projeyi Visual Studio bellek kullanımını incelemeye başlamak istediğiniz noktada uygulamanıza bir kesme noktası ayarlayın.

    Bellek sorunundan şüphelenen bir alanınız varsa, bellek sorunu oluşmadan önce ilk kesme noktası'ı ayarlayın.

    > [!TIP]
    > Uygulamanız belleği sık sık ayırıyor ve ayırıyorsa, işlem başında ve sonunda kesme noktaları ayarlayan (veya işlem boyunca adımlayan) sizi ilgilendiren bir işlem bellek profilini yakalamak zor olabilir.

2. Analiz etmek istediğiniz işlevin veya kodun bölgesinde ikinci bir kesme noktası ayarlayın (veya şüpheli bir bellek sorunu ortaya çıktıktan sonra).

3. Siz **Tanılama Araçları** pencere otomatik olarak görüntülenir. Pencereyi yeniden getirmek için Hata Ayıkla'ya **tıklayın**  >  **Windows**  >  **Show Tanılama Araçları**.

4. Araç **çubuğundaKi** Araçları Seç **ayarıyla** Bellek Kullanımı'ı seçin.

     ![Tanılama Araçlarını Göster](../profiling/media/diag-tools-select-tool-2.png "DiagToolsSelectTool")

5. Hata **Ayıkla / Hata Ayıklamayı Başlat'a** tıklayın **(veya** araç çubuğunda Başlat'a veya **F5'e tıklayın.**

     Uygulamanın yüklenmesi tamam olduğunda Tanılama Araçları'nın Özet görünümü görüntülenir.

     ![Tanılama Araçları Özet Sekmesi](../profiling/media/diag-tools-summary-tab-2.png "DiagToolsSummaryTab")

     > [!NOTE]
     > Bellek verilerini toplamak, yerel veya karma mod uygulamalarınızı hata ayıklama performansını etkileyeneden bellek anlık görüntüleri varsayılan olarak devre dışı bırakılır. Yerel veya karma modlu uygulamalarda anlık görüntüleri etkinleştirmek için bir hata ayıklama oturumu başlatın (Kısayol tuşu: **F5**). Uygulama **Tanılama Araçları,** Bellek Kullanımı **sekmesini** ve ardından Yığın Profili **Oluşturma'yı seçin.**
     >
     >  ![Anlık görüntüleri etkinleştirme](../profiling/media/dbgdiag_mem_mixedtoolbar_enablesnapshot.png "DBGDIAG_MEM_MixedToolbar_EnableSnapshot")
     >
     >  Durdur (Kısayol tuşu: **Shift** + **F5**) ve hata ayıklamayı yeniden başlatın.

6. Hata ayıklama oturumunun başında anlık görüntü almak için Bellek Kullanımı **özet** araç çubuğunda Anlık görüntü **al'ı** seçin. (Burada da bir kesme noktası ayarlamaya yardımcı olabilir.)

    ![Anlık görüntü alma](../profiling/media/dbgdiag_mem_mixedtoolbar_takesnapshot.png "DBGDIAG_MEM_MixedToolbar_TakeSnapshot")

     > [!TIP]
     > Bellek karşılaştırmaları için bir temel oluşturmak üzere hata ayıklama oturumunun başında anlık görüntü alma düşünün.

6. İlk kesme noktanıza isabet etmek için senaryoyu çalıştırın.

7. Hata ayıklayıcı ilk kesme noktası sırasında duraklatılırken Bellek **Kullanımı** özet araç çubuğunda Anlık görüntü **al'ı** seçin.

8. Uygulamayı ikinci kesme noktanıza çalıştırmak için **F5** tuşuna basın.

9. Şimdi başka bir anlık görüntü alın.

     Bu noktada, verileri analiz etmek için başlayabilirsiniz.

## <a name="analyze-memory-usage-data"></a>Bellek kullanım verilerini analiz etme
Bellek Kullanımı özet tablosu satırları, hata ayıklama oturumu sırasında alınan anlık görüntüleri listeler ve daha ayrıntılı görünümlere bağlantılar sağlar.

![Bellek özeti tablosu](../profiling/media/dbgdiag_mem_summarytable.png "DBGDIAG_MEM_SummaryTable")

 Sütunların adı proje özelliklerinde seçtiğiniz hata ayıklama moduna bağlıdır: .NET, yerel veya karışık (hem .NET hem de yerel).

- Objects **(Diff)** ve **Allocations (Diff)** sütunları, anlık görüntü alınırken .NET'te ve yerel bellekte nesne sayısını görüntüler.

- Yığın **Boyutu (Fark)** sütunu, .NET ve yerel yığınlarda bayt sayısını görüntüler

Birden çok anlık görüntü alırken özet tablonun hücreleri satır anlık görüntüsü ile önceki anlık görüntü arasındaki değer değişikliğini içerir.

Bellek kullanımını analiz etmek için, bellek kullanımının ayrıntılı bir raporunu açan bağlantılardan birini tıklatın:

- Geçerli anlık görüntü ile önceki anlık görüntü arasındaki farkın ayrıntılarını görüntülemek için okun sol yanındaki değişiklik bağlantısını seçin (![Bellek Kullanımı Artışı](../profiling/media/prof-tour-mem-usage-up-arrow.png "Bellek Kullanımı Artışı")). Kırmızı ok, bellek kullanımında artış olduğunu ve azalmayı gösteren yeşil bir ok olduğunu gösterir.

> [!TIP]
> Bellek sorunlarını daha hızlı belirlemeye yardımcı olmak için fark raporları, genel sayı olarak en fazla artan nesne türlerine göre sıralanmış (Nesneler **(Fark)** sütunundaki değişiklik bağlantısına tıklayın) veya genel yığın boyutunda en yüksek olan (Yığın Boyutu **(Fark)** sütunundaki değişiklik bağlantısına tıklayın).

- Yalnızca seçili anlık görüntüyle ilgili ayrıntıları görüntülemek için, değişiklik olmayan bağlantıya tıklayın.

   Rapor ayrı bir pencerede görünür.

### <a name="managed-types-reports"></a>Yönetilen türler raporları
 Bellek Kullanımı özet tablosunda **bir Nesnelerin (Fark)** veya **Ayırmalar (Fark)** hücresi geçerli bağlantısını seçin.

 ![Hata ayıklayıcısı yönetilen &#45; Yolları](../profiling/media/dbgdiag_mem_managedtypesreport_pathstoroot.png "DBGDIAG_MEM_ManagedTypesReport_PathsToRoot")

 Üst bölmede, türü tarafından başvurulan tüm nesnelerin boyutu da dahil olmak üzere anlık görüntüdeki türlerin sayısı ve boyutu gösterilir (**Kapsayıcı Boyut).**

 Alt **bölmedeki Kök** ağacın Yolları, üst bölmede seçilen türe başvurulan nesneleri görüntüler. .NET çöp toplayıcısı, bir nesnenin belleğini yalnızca başvurulan son tür serbest bırakıldı olduğunda temizler.

 Başvurulan **Nesneler** ağacı, üst bölmede seçilen tür tarafından düzenlenen başvuruları görüntüler.

 ![Yönetilen başvurulan nesneler rapor görünümü](../profiling/media/dbgdiag_mem_managedtypesreport_referencedtypes.png "DBGDIAG_MEM_ManagedTypesReport_ReferencedTypes")

 Seçili bir türün örneklerini üst bölmede görüntülemek için Örnek ![simgesini](../profiling/media/dbgdiag_mem_instanceicon.png "DBGDIAG_MEM_InstanceIcon") seçin.

 ![Örnekler bölmesini ve Kök ve Başvurulan Nesneler Visual Studio gösteren, Bellek Kullanımı aracında Örnekler görünümünün ekran görüntüsü.](../profiling/media/dbgdiag_mem_managedtypesreport_instances.png "DBGDIAG_MEM_ManagedTypesReport_Instances")

 Örnekler **görünümü,** seçili nesnenin örneklerini üst bölmede anlık görüntüde görüntüler. Kök **ve Başvurulan Nesnelere** Giden Yollar **bölmesi,** seçilen örnekle ilgili nesneleri ve seçilen örneğin başvurulan türleri görüntüler. Hata ayıklayıcı anlık görüntü alınan noktada durdurulursa, bir araç ipucunda nesnenin değerlerini görüntülemek için **Değer** hücresi üzerine gelin.

### <a name="native-type-reports"></a>Yerel tür raporlar
 Uygulama penceresinin Bellek Kullanımı özet tablosunda bir **Ayırmalar (Fark)** veya Yığın Boyutu **(Fark)** **hücresi Tanılama Araçları** seçin.

 ![Yerel Tür Görünümü](../profiling/media/dbgdiag_mem_native_typesview.png "DBGDIAG_MEM_Native_TypesView")

 Türler **Görünümü** anlık görüntüde türlerin sayısını ve boyutunu görüntüler.

- Anlık görüntüde seçili![türün](../profiling/media/dbg_mma_instancesicon.png "DBG_MMA_InstancesIcon")nesneleriyle ilgili bilgileri görüntülemek için seçili türdeki örnekler simgesini (Nesne Türü sütunundaki örnek simgesi) seçin.

     Örnekler **görünümü** seçilen türün her örneğini görüntüler. Bir örnek seçerek, örneğin oluşturulmasıyla sonuçlandırılmış çağrı yığını Ayırma Çağrı Yığını **bölmesinde** görüntülenir.

     ![Örnekler bölmesini ve Ayırma Çağrı Yığını bölmesini Visual Studio Bellek Kullanımı aracında Örnekler görünümünün ekran görüntüsü.](../profiling/media/dbgdiag_mem_native_instances.png "DBGDIAG_MEM_Native_Instances")

- Seçilen **türe ilişkin** ayırma **yığınını görmek için** Görünüm Modu listesinde Yığınlar Görünümü'ne tıklayın.

     ![Yığınlar Görünümü](../profiling/media/dbgdiag_mem_native_stacksview.png "DBGDIAG_MEM_Native_StacksView")

### <a name="change-diff-reports"></a>Raporları değiştirme (Fark)

- Uygulama penceresinin Bellek Kullanımı sekmesinin özet tablosunda **yer** alan bir hücrede **değişiklik Tanılama Araçları** seçin.

   ![Raporu fark &#40;değişiklik&#41; seçin](../profiling/media/dbgdiag_mem_choosediffreport.png "DBGDIAG_MEM_ChooseDiffReport")

- Yönetilen veya yerel bir **raporun Karşılaştır** listesinden bir anlık görüntü seçin.

   ![Karşılaştır listesinden anlık görüntü seçme](../profiling/media/dbgdiag_mem_choosecompareto.png "DBGDIAG_MEM_ChooseCompareTo")

Değişiklik raporu, temel anlık görüntü değeri ile karşılaştırma anlık görüntüsü arasındaki farkı göstermek için temel rapora sütun **ekler (fark)** ile işaretlenir. Yerel Tür Görünümü fark raporu şöyle olabilir:

![Yerel Türler Fark Görünümü](../profiling/media/dbgdiag_mem_native_typesviewdiff.png "DBGDIAG_MEM_Native_TypesViewDiff")

## <a name="blogs-and-videos"></a>Bloglar ve videolar

[Hata Ayıklama Sırasında CPU ve Belleği Analiz Etme](https://devblogs.microsoft.com/visualstudio/analyze-cpu-memory-while-debugging/)

[Visual C++ Blogu: Visual C++ 2015'te Bellek Profili Oluşturma](https://devblogs.microsoft.com/cppblog/memory-profiling-in-visual-c-2015/)

## <a name="next-steps"></a>Sonraki adımlar

Bu öğreticide bellek kullanım verilerini toplamayı ve analiz etme hakkında bilgi edinebilirsiniz. Profil oluşturma [turlarını zaten tamamladıysanız](../profiling/profiling-feature-tour.md)uygulamalarınız için CPU kullanımını analiz etme hakkında hızlı bir bakış elde etmek iyi olabilir.

> [!div class="nextstepaction"]
> [CPU kullanımını analiz etme](../profiling/beginners-guide-to-performance-profiling.md)
