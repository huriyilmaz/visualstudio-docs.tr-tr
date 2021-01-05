---
title: Uygulamalarınızda bellek kullanımını ölçme
description: Hata ayıklayıcı ile tümleşik tanılama aracı ile hata ayıklarken bellek sızıntılarını ve verimsiz belleği bulun.
ms.custom: seodec18
ms.date: 04/25/2018
ms.topic: tutorial
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3d259c6fa69821d1fecd26944227bff86cc82104
ms.sourcegitcommit: 105e7b5a486262bc92939980383ceee068098a11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/30/2020
ms.locfileid: "97815860"
---
# <a name="measure-memory-usage-in-visual-studio"></a>Visual Studio’da bellek kullanımını ölçme

Hata ayıklayıcı ile tümleşik **bellek kullanımı** Tanılama aracı ile hata ayıklarken bellek sızıntılarını ve verimsiz belleği bulun. Bellek kullanımı aracı, nesne türlerinin bellek kullanımının etkisini anlamanıza yardımcı olmak için yönetilen ve yerel bellek yığınının bir veya daha fazla *anlık görüntüsünü* almanızı sağlar. Ayrıca, bir hata ayıklayıcı ekli veya çalışan bir uygulamayı hedefleyerek bellek kullanımını çözümleyebilirsiniz. Daha fazla bilgi için bkz. [hata ayıklayıcı ile veya olmayan profil oluşturma araçlarını çalıştırma](../profiling/running-profiling-tools-with-or-without-the-debugger.md).

Bellek **kullanım** aracında istediğiniz zaman bellek anlık görüntülerini toplayabilmenize karşın, performans sorunlarını araştırırken uygulamanızın nasıl yürütüldüğünü denetlemek Için Visual Studio hata ayıklayıcısını kullanabilirsiniz. Kesme noktaları, Adımlama, tümünü Böl ve diğer hata ayıklayıcı eylemlerinin ayarlanması, performans araştırmalarınızın en ilgili kod yollarına odaklanmasına yardımcı olabilir. Uygulamanız çalışırken bu eylemlerin gerçekleştirilmesi, sizi ilgilendiremeyen koddan paraziti ortadan kaldırabilir ve bir sorunu tanılamak için gereken süreyi önemli ölçüde azaltabilir.

> [!Important]
> Hata ayıklayıcı ile tümleşik tanılama araçları, Visual Studio 'da ASP.NET, ASP.NET Core, Native/C++ geliştirme ve karma mod (.NET ve yerel) uygulamaları dahil .NET geliştirmesi için desteklenir. Hata ayıklayıcı (**Tanılama araçları** penceresi) ile profil oluşturma araçlarını çalıştırmak için Windows 8 ve üzeri gereklidir.

Bu öğreticide şunları yapacaksınız:

> [!div class="checklist"]
> * Belleğin anlık görüntülerini al
> * Bellek kullanım verilerini analiz etme

**Bellek kullanımı** size ihtiyacınız olan verileri sağlamıyorsa, [performans Profiler](../profiling/profiling-feature-tour.md#post_mortem) 'daki diğer profil oluşturma araçları sizin için yararlı olabilecek farklı türde bilgiler sağlar. Çoğu durumda, uygulamanızın performans sorunu, CPU, işleme Kullanıcı arabirimi veya ağ isteği süresi gibi belleğinizin dışında bir şey olabilir.

> [!NOTE]
> **Özel ayırıcı desteği** Yerel bellek profili Oluşturucu çalışma zamanında yayılan ayırma [ETW](/windows-hardware/drivers/devtest/event-tracing-for-windows--etw-) olay verileri toplanarak çalışır.  CRT ve Windows SDK ayırıcıları, ayırma verilerinin yakalanabilmesi için kaynak düzeyinde açıklanmalıdır. Kendi ayırıcılarınızı yazıyorsanız, yeni ayrılan yığın belleğine bir işaretçi döndüren işlevler, myMalloc için bu örnekte görüldüğü gibi [__declspec](/cpp/cpp/declspec)(ayırıcı) ile birlikte kullanılabilir.
>
> `__declspec(allocator) void* myMalloc(size_t size)`

## <a name="collect-memory-usage-data"></a>Bellek kullanım verilerini topla

1. Visual Studio 'da hata ayıklamak istediğiniz projeyi açın ve uygulamanızda, bellek kullanımını incelemeyi başlatmak istediğiniz noktada bir kesme noktası ayarlayın.

    Bellek sorunuyla şüphelendiğiniz bir alana sahipseniz, ilk kesme noktasını bellek sorunu gerçekleşmeden önce ayarlayın.

    > [!TIP]
    > Uygulamanız sıklıkla bellek ayırdığında ve serbest bırakıldığı zaman sizi ilgilendiren bir işlemin bellek profilini yakalamak zor olabileceğinden, belleğin değiştiği kesin noktasını bulmak için işlemin başlangıcında ve sonunda kesme noktaları ayarlayın (veya işlem boyunca ilerleyin).

2. Çözümlemek istediğiniz işlevin veya kod bölgesinin sonunda (veya bir şüpheli bellek sorunu oluştuktan sonra) ikinci bir kesme noktası ayarlayın.

3. **Tanılama araçları** penceresi devre dışı bırakılmadığı takdirde otomatik olarak görünür. Pencereyi yeniden getirmek için, **Hata Ayıkla**  >  **Windows**  >  **Tanılama araçları göster**' e tıklayın.

4. Araç çubuğundaki **araçları seç** ayarıyla **bellek kullanımı** ' nı seçin.

     ![Tanılama araçlarını göster](../profiling/media/diag-tools-select-tool-2.png "Diagaraçları selecttool")

5. **Hata Ayıkla/hata ayıklamayı Başlat** (ya da araç çubuğundan **başla** ya da **F5**) seçeneğine tıklayın.

     Uygulamanın yüklenmesi bittiğinde, tanılama araçlarının Özet görünümü görüntülenir.

     ![Tanılama araçları Özet sekmesi](../profiling/media/diag-tools-summary-tab-2.png "DiagToolsSummaryTab")

     > [!NOTE]
     > Bellek verileri toplama, yerel veya Karma modlu uygulamalarınızın hata ayıklama performansını etkileyebileceğinden, bellek anlık görüntüleri varsayılan olarak devre dışıdır. Yerel veya karma moddaki uygulamalarda anlık görüntüleri etkinleştirmek için bir hata ayıklama oturumu başlatın (kısayol tuşu: **F5**). **Tanılama araçları** penceresi göründüğünde **bellek kullanımı** sekmesini seçin ve ardından **yığın profili oluşturma**' yı seçin.
     >
     >  ![Anlık görüntüleri etkinleştir](../profiling/media/dbgdiag_mem_mixedtoolbar_enablesnapshot.png "DBGDIAG_MEM_MixedToolbar_EnableSnapshot")
     >
     >  Durdur (kısayol tuşu: **SHIFT** + **F5**) ve hata ayıklamayı yeniden Başlat.

6. Hata ayıklama oturumunuzun başlangıcında bir anlık görüntü almak için **bellek kullanımı** Özeti araç çubuğundan **anlık görüntü al** ' ı seçin. (Burada bir kesme noktası ayarlamaya da yardımcı olabilir.)

    ![Anlık görüntü al](../profiling/media/dbgdiag_mem_mixedtoolbar_takesnapshot.png "DBGDIAG_MEM_MixedToolbar_TakeSnapshot")

     > [!TIP]
     > Bellek karşılaştırmaları için bir taban çizgisi oluşturmak üzere hata ayıklama oturumunuzun başlangıcında bir anlık görüntü almayı düşünün.

6. İlk kesme noktasının isabet çekmesine neden olacak senaryoyu çalıştırın.

7. Hata ayıklayıcı ilk kesme noktasında duraklatıldığında, **bellek kullanımı** Özeti araç çubuğundan **anlık görüntü al** ' ı seçin.

8. Uygulamanızı ikinci kesme noktasına çalıştırmak için **F5** tuşuna basın.

9. Şimdi başka bir anlık görüntü alın.

     Bu noktada, verileri çözümlemeye başlayabilirsiniz.

## <a name="analyze-memory-usage-data"></a>Bellek kullanım verilerini analiz etme
Bellek kullanımı Özet tablosunun satırları, hata ayıklama oturumu sırasında yaptığınız anlık görüntüleri listeler ve daha ayrıntılı görünümlere bağlantılar sağlar.

![Bellek Özet tablosu](../profiling/media/dbgdiag_mem_summarytable.png "DBGDIAG_MEM_SummaryTable")

 Sütunların adı, proje özelliklerinde seçtiğiniz hata ayıklama moduna bağlıdır: .NET, Native veya Mixed (hem .NET hem de native).

- **Nesneler (fark)** ve **ayırmalar (fark)** sütunları, anlık görüntü çekilirken .net ve yerel bellekteki nesne sayısını görüntüler.

- **Yığın boyutu (fark)** sütunu, .net ve yerel yığınlardaki bayt sayısını görüntüler

Birden çok anlık görüntü aldığınızda, Özet tablosunun hücreleri, satır anlık görüntüsü ve önceki anlık görüntü arasındaki değer değişikliğini içerir.

Bellek kullanımını analiz etmek için, ayrıntılı bellek kullanımı raporunu açan bağlantılardan birine tıklayın:

- Geçerli anlık görüntü ve önceki anlık görüntü arasındaki farkın ayrıntılarını görüntülemek için okun sol tarafında bulunan değişiklik bağlantısını seçin (![bellek kullanımı artışı](../profiling/media/prof-tour-mem-usage-up-arrow.png "Bellek kullanımı artışı")). Kırmızı ok, bellek kullanımının artışını ve bir azalma belirten yeşil oku gösterir.

> [!TIP]
> Bellek sorunlarını daha hızlı belirlemesine yardımcı olmak için, fark raporları genel olarak en çok (nesnelerde değişiklik bağlantısı **(diff)** sütununda) artan nesne türlerine göre sıralanır veya genel yığın boyutunun en çok artması ( **yığın boyutu (fark)** sütunundaki bağlantıyı değiştirin).

- Yalnızca seçili anlık görüntünün ayrıntılarını görüntülemek için, değişiklik olmayan bağlantısına tıklayın.

   Rapor ayrı bir pencerede görüntülenir.

### <a name="managed-types-reports"></a>Yönetilen türler raporları
 Bellek kullanımı Özet tablosunda bir **nesneler (fark)** veya **ayırmalar (fark)** hücresinin geçerli bağlantısını seçin.

 ![Hata ayıklayıcı yönetilen tür raporu &#45;, köke yönelik yollar](../profiling/media/dbgdiag_mem_managedtypesreport_pathstoroot.png "DBGDIAG_MEM_ManagedTypesReport_PathsToRoot")

 Üstteki bölmede, tür tarafından başvurulan tüm nesnelerin boyutu da dahil olmak üzere anlık görüntüdeki türlerin sayısı ve boyutu gösterilir (**kapsamlı boyut**).

 Alt bölmedeki **kök ağacın yolları** , üst bölmede seçilen türe başvuran nesneleri görüntüler. .NET atık toplayıcısı, yalnızca kendisine başvuran son tür serbest bırakıldığında bir nesne için belleği temizler.

 **Başvurulan nesneler** ağacı, üst bölmede seçilen tür tarafından tutulan başvuruları görüntüler.

 ![Yönetilen başvurulan nesneler rapor görünümü](../profiling/media/dbgdiag_mem_managedtypesreport_referencedtypes.png "DBGDIAG_MEM_ManagedTypesReport_ReferencedTypes")

 Sol bölmede seçilen bir türün örneklerini göstermek için ![örnek simgesi](../profiling/media/dbgdiag_mem_instanceicon.png "DBGDIAG_MEM_InstanceIcon") simgesini seçin.

 ![Visual Studio bellek kullanımı aracındaki örnekler görünümünün ekran görüntüsü, örnekler bölmesi ve kök ve başvurulan nesneler bölmesine yönelik yollar.](../profiling/media/dbgdiag_mem_managedtypesreport_instances.png "DBGDIAG_MEM_ManagedTypesReport_Instances")

 **Örnekler** görünümü, alt görüntüdeki seçili nesnenin örneklerini üst bölmede görüntüler. Kök ve **başvurulan nesneler** **için yollar** bölmesi, seçilen örneğe ve seçili Örneğin başvurduğu türlere başvuran nesneleri görüntüler. Hata ayıklayıcı anlık görüntünün alındığı noktada durdurulduğunda, bir araç ipucunda nesnenin değerlerini göstermek için **değer** hücresinin üzerine gelin.

### <a name="native-type-reports"></a>Yerel tür raporları
 **Tanılama araçları** penceresinin bellek kullanım Özeti tablosunda bir **ayırma (fark)** veya **yığın boyutu (fark)** hücresinin geçerli bağlantısını seçin.

 ![Yerel tür görünümü](../profiling/media/dbgdiag_mem_native_typesview.png "DBGDIAG_MEM_Native_TypesView")

 **Türler görünümü** anlık görüntüdeki türlerin sayısını ve boyutunu görüntüler.

- Seçilen bir türün nesneleri hakkındaki bilgileri göstermek için örnekler simgesini (![nesne türü sütunundaki örnek simgesi](../profiling/media/dbg_mma_instancesicon.png "DBG_MMA_InstancesIcon")) seçin.

     **Örnekler** görünümü seçili türün her örneğini görüntüler. Örnek seçildiğinde, **ayırma çağrı yığını** bölmesinde örneğin oluşturulmasına neden olan çağrı yığını görüntülenir.

     ![Visual Studio bellek kullanımı aracında örnekler bölmesinin ve ayırma çağrı yığını bölmesinin gösterildiği örnekler görünümünün ekran görüntüsü.](../profiling/media/dbgdiag_mem_native_instances.png "DBGDIAG_MEM_Native_Instances")

- Seçili türe ait ayırma yığınını görmek için, **görünüm modu** listesinde **yığınlar görünümü** ' ne tıklayın.

     ![Yığınlar görünümü](../profiling/media/dbgdiag_mem_native_stacksview.png "DBGDIAG_MEM_Native_StacksView")

### <a name="change-diff-reports"></a>Değişiklik (fark) raporları

- **Tanılama araçları** penceresindeki **bellek kullanımı** sekmesinin Özet tablosunun Özet tablosunun bir hücresinde bağlantıyı değiştir ' i seçin.

   ![Bir değişiklik &#40;fark&#41; raporu seçin](../profiling/media/dbgdiag_mem_choosediffreport.png "DBGDIAG_MEM_ChooseDiffReport")

- Yönetilen veya yerel raporun **Karşılaştırılacak** listesinde bir anlık görüntü seçin.

   ![Karşılaştırılacak listeden bir anlık görüntü seçin](../profiling/media/dbgdiag_mem_choosecompareto.png "DBGDIAG_MEM_ChooseCompareTo")

Değişiklik raporu, temel anlık görüntü değeri ve karşılaştırma anlık görüntüsü arasındaki farkı gösteren temel rapora sütunlar ( **(fark)** ile işaretlenir) ekler. Yerel bir tür görünümü fark raporu şöyle görünebilir:

![Yerel türler fark görünümü](../profiling/media/dbgdiag_mem_native_typesviewdiff.png "DBGDIAG_MEM_Native_TypesViewDiff")

## <a name="blogs-and-videos"></a>Blogların ve videoların

[Hata ayıklarken CPU ve belleği çözümleme](https://devblogs.microsoft.com/visualstudio/analyze-cpu-memory-while-debugging/)

[Visual C++ blog: Visual C++ 2015 ' de bellek profili oluşturma](https://devblogs.microsoft.com/cppblog/memory-profiling-in-visual-c-2015/)

## <a name="next-steps"></a>Sonraki adımlar

Bu öğreticide, bellek kullanım verilerini nasıl toplayacağınızı ve analiz edeceğinizi öğrendiniz. [Profil oluşturucunun turuna](../profiling/profiling-feature-tour.md)zaten tamamladıysanız, uygulamalarınızda CPU kullanımını çözümleme hakkında hızlı bir bakış almak isteyebilirsiniz.

> [!div class="nextstepaction"]
> [CPU kullanımını çözümle](../profiling/beginners-guide-to-performance-profiling.md)
