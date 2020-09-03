---
title: Bellek kullanımı | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: bbb58d6c-3362-4ca3-8e87-64b2d4415bf6
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0feabad8dfa3b086c9ed5a1a58e231719774f9cc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "74298366"
---
# <a name="memory-usage"></a>Bellek Kullanımı
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Hata ayıklayıcı ile tümleşik **bellek kullanımı** Tanılama aracı ile hata ayıklarken bellek sızıntılarını ve verimsiz belleği bulun. Bellek kullanımı aracı, yönetilen ve yerel bellek yığınının bir veya daha fazla *anlık görüntüsünü* almanızı sağlar. .NET, yerel veya karma mod (.NET ve yerel) uygulamalarının anlık görüntülerini toplayabilirsiniz.  
  
- Nesne türlerinin bellek kullanımı üzerindeki göreli etkisini anlamak ve uygulamanızda belleği verimsiz kullanan kodu bulmak için tek bir anlık görüntüyü anailz edebilirsiniz.  
  
- Ayrıca, kodunuzun içindeki ve zaman içinde artış için bellek kullanımına neden olan bölümleri bulmak için bir uygulamanın iki anlık görüntüsünü de karşılaştırabilirsiniz (fark edebilirsiniz).  
  
  Aşağıdaki grafikte, Visual Studio 2015 güncelleştirme 1 ' deki **Tanılama araçları** penceresi gösterilmektedir:  
  
  ![DiagnosticTools&#45;güncelleştirme 1](../profiling/media/diagnostictools-update1.png "DiagnosticTools-güncelleştirme 1")  
  
  Bellek **kullanım** aracında istediğiniz zaman bellek anlık görüntülerini toplayabilmenize karşın, performans sorunlarını araştırırken uygulamanızın nasıl yürütüldüğünü denetlemek Için Visual Studio hata ayıklayıcısını kullanabilirsiniz. Kesme noktaları, Adımlama, tümünü Böl ve diğer hata ayıklayıcı eylemlerinin ayarlanması, performans araştırmalarınızın en ilgili kod yollarına odaklanmasına yardımcı olabilir. Uygulamanız çalışırken bu eylemlerin gerçekleştirilmesi, sizi ilgilenmeyen koddan paraziti ortadan kaldırır ve bir sorunu tanılamak için gereken süreyi önemli ölçüde azaltabilir.  
  
  Bellek aracını hata ayıklayıcı dışında da kullanabilirsiniz. [Hata ayıklama olmadan bellek kullanımını](https://msdn.microsoft.com/library/8883bc5f-df86-4f84-aa2b-a21150f499b0)görün.  
  
> [!NOTE]
> **Özel ayırıcı desteği** Yerel bellek Oluşturucu, çalışma zamanı sırasında tarafından yayılan ayırma [ETW](https://msdn.microsoft.com/library/windows/desktop/bb968803\(v=vs.85\).aspx) olay verileri toplanarak işe yarar.  CRT ve Windows SDK ayırıcıları, ayırma verilerinin yakalanabilmesi için kaynak düzeyinde açıklanmalıdır.  Kendi ayırıcılarınızı yazıyorsanız, yeni ayrılan yığın belleğine yönelik bir işaretçi döndüren işlevlerden farklı olarak, myMalloc için bu örnekte görüldüğü gibi [__declspec](https://msdn.microsoft.com/library/832db681-e8e1-41ca-b78c-cd9d265cdb87)(ayırıcı) ile birlikte kullanılabilir.  
>   
> `__declspec(allocator) void* myMalloc(size_t size)`  
  
## <a name="analyze-memory-use-with-the-debugger"></a>Hata ayıklayıcı ile bellek kullanımını analiz etme  
  
> [!NOTE]
> Bellek verileri toplama, yerel veya Karma modlu uygulamalarınızın hata ayıklama performansını etkileyebileceğinden, bellek anlık görüntüleri varsayılan olarak devre dışıdır. Anlık görüntülerin yerel veya karma mod uygulamaları etkinleştirmek için bir hata ayıklama oturumu başlatın (kısayol tuşu: **F5**). **Tanılama araçları** penceresi göründüğünde, bellek kullanımı sekmesini seçin ve ardından **anlık görüntüleri etkinleştir**' i seçin.  
>   
> ![Anlık görüntüleri etkinleştir](../profiling/media/dbgdiag-mem-mixedtoolbar-enablesnapshot.png "DBGDIAG_MEM_MixedToolbar_EnableSnapshot")  
>   
> Durdur (kısayol tuşu: **SHIFT + F5**) ve hata ayıklamayı yeniden Başlat.  
  
 Bellek durumunu yakalamak istediğinizde, **bellek kullanımı** Özeti araç çubuğundan **anlık görüntü al** ' ı seçin.  
  
 ![Anlık görüntü al](../profiling/media/dbgdiag-mem-mixedtoolbar-takesnapshot.png "DBGDIAG_MEM_MixedToolbar_TakeSnapshot")  
  
> [!TIP]
> - Bellek karşılaştırmaları için bir taban çizgisi oluşturmak üzere hata ayıklama oturumunuzun başlangıcında bir anlık görüntü almayı düşünün.  
>   - Uygulamanız sıklıkla bellek ayırdığında ve serbest bırakıldığı zaman sizi ilgilendiren bir işlemin bellek profilini yakalamak zor olabileceğinden, işlemin başında ve sonunda kesme noktaları ayarlayın veya belleğin değiştiği kesin noktasını bulmak için işlemi adım adım yapın.  
  
## <a name="viewing-memory-snapshot-details"></a>Bellek anlık görüntüsü ayrıntılarını görüntüleme  
 Bellek kullanımı Özet tablosunun satırları, hata ayıklama oturumu sırasında yaptığınız anlık görüntüleri listeler.  
  
 Satır sütunları, proje özelliklerinde seçtiğiniz hata ayıklama moduna bağlıdır: .NET, Native veya Mixed (hem .NET hem de native).  
  
- **Yönetilen nesne**ve **Yerel ayırmalar** sütunları, anlık görüntü çekilirken .net ve yerel bellekteki nesne sayısını görüntüler.  
  
- **Yönetilen yığın boyutu** ve **yerel yığın boyutu** sütunları, .net ve yerel yığınlardaki bayt sayısını görüntüler  
  
- Birden çok anlık görüntü aldığınızda, Özet tablosunun hücreleri, satır anlık görüntüsü ve önceki anlık görüntü arasındaki değer değişikliğini içerir.  
  
   ![Bellek Özet Tablo hücresi](../profiling/media/dbgdiag-mem-summarytablecell.png "DBGDIAG_MEM_SummaryTableCell")  
  
  **Ayrıntı raporunu görüntülemek için:**  
  
- Yalnızca seçili anlık görüntünün ayrıntılarını görüntülemek için geçerli bağlantıyı seçin.  
  
- Geçerli anlık görüntü ve önceki anlık görüntü arasındaki farkın ayrıntılarını görüntülemek için Değiştir bağlantısını seçin.  
  
  Rapor ayrı bir pencerede görüntülenir.  
  
## <a name="memory-usage-details-reports"></a>Bellek kullanım ayrıntıları raporları  
  
### <a name="managed-types-reports"></a>Yönetilen türler raporları  
 **Yönetilen nesnelerin** geçerli bağlantısını veya bellek kullanımı Özet tablosunda **yönetilen yığın boyutu** hücresini seçin.  
  
 ![Hata ayıklayıcı yönetilen tür raporu &#45;, köke yönelik yollar](../profiling/media/dbgdiag-mem-managedtypesreport-pathstoroot.png "DBGDIAG_MEM_ManagedTypesReport_PathsToRoot")  
  
 Üstteki bölmede, tür tarafından başvurulan tüm nesnelerin boyutu da dahil olmak üzere anlık görüntüdeki türlerin sayısı ve boyutu gösterilir (**kapsamlı boyut**).  
  
 Alt bölmedeki **kök ağacın yolları** , üst bölmede seçilen türe başvuran nesneleri görüntüler. .NET Framework çöp toplayıcı, yalnızca kendisine başvuran son tür serbest bırakıldığında bir nesne için belleği temizler.  
  
 **Başvurulan türler** ağacı, üst bölmede seçilen tür tarafından tutulan başvuruları görüntüler.  
  
 ![Yönetilen eferenced Types rapor görünümü](../profiling/media/dbgdiag-mem-managedtypesreport-referencedtypes.png "DBGDIAG_MEM_ManagedTypesReport_ReferencedTypes")  
  
 Sol bölmede seçilen bir türün örneklerini göstermek için ![örnek simgesi](../profiling/media/dbgdiag-mem-instanceicon.png "DBGDIAG_MEM_InstanceIcon") simgesini seçin.  
  
 ![Örnek görünümü](../profiling/media/dbgdiag-mem-managedtypesreport-instances.png "DBGDIAG_MEM_ManagedTypesReport_Instances")  
  
 **Örnekler** görünümü, alt görüntüdeki seçili nesnenin örneklerini üst bölmede görüntüler. Kök ve başvurulan nesneler bölmesine yönelik yollar seçili örneğe ve seçili Örneğin başvurduğu türlere başvuran nesneleri görüntüler. Hata ayıklayıcı anlık görüntünün alındığı noktada durdurulduğunda, bir araç ipucunda nesnenin değerlerini göstermek için değer hücresinin üzerine gelin.  
  
### <a name="native-type-reports"></a>Yerel tür raporları  
 **Tanılama araçları** penceresinin bellek kullanımı Özet tablosunda **Yerel ayırmaların** veya **yerel yığın boyutu** hücresinin geçerli bağlantısını seçin.  
  
 ![Yerel tür görünümü](../profiling/media/dbgdiag-mem-native-typesview.png "DBGDIAG_MEM_Native_TypesView")  
  
 **Türler görünümü** anlık görüntüdeki türlerin sayısını ve boyutunu görüntüler.  
  
- Seçilen bir türün nesneleri hakkındaki bilgileri göstermek için örnekler simgesini (![nesne türü sütunundaki örnek simgesi](../misc/media/dbg-mma-instancesicon.png "DBG_MMA_InstancesIcon")) seçin.  
  
     **Örnekler** görünümü seçili türün her örneğini görüntüler. Örnek seçildiğinde, **ayırma çağrı yığını** bölmesinde örneğin oluşturulmasına neden olan çağrı yığını görüntülenir.  
  
     ![Örnek görünümü](../profiling/media/dbgdiag-mem-native-instances.png "DBGDIAG_MEM_Native_Instances")  
  
- Seçili türe ait ayırma yığınını görmek için, **görünüm modu** listesinde **yığınlar görünümü** ' ne tıklayın.  
  
     ![Yığınlar görünümü](../profiling/media/dbgdiag-mem-native-stacksview.png "DBGDIAG_MEM_Native_StacksView")  
  
### <a name="change-diff-reports"></a>Değişiklik (fark) raporları  
  
- **Tanılama araçları** penceresindeki **bellek kullanımı** sekmesinin Özet tablosunun Özet tablosunun bir hücresinde bağlantıyı değiştir ' i seçin.  
  
   ![Değişiklik &#40;DIF&#41;f raporu seçin](../profiling/media/dbgdiag-mem-choosediffreport.png "DBGDIAG_MEM_ChooseDiffReport")  
  
- Yönetilen veya yerel raporun **Karşılaştırılacak** listesinde bir anlık görüntü seçin.  
  
   ![Karşılaştırılacak listeden bir anlık görüntü seçin](../profiling/media/dbgdiag-mem-choosecompareto.png "DBGDIAG_MEM_ChooseCompareTo")  
  
  Değişiklik raporu, temel anlık görüntü değeri ve karşılaştırma anlık görüntüsü arasındaki farkı gösteren temel rapora sütunlar ( **(fark)** ile işaretlenir) ekler. Yerel bir tür görünümü fark raporu şöyle görünebilir:  
  
  ![Yerel türler fark veiw](../profiling/media/dbgdiag-mem-native-typesviewdiff.png "DBGDIAG_MEM_Native_TypesViewDiff")  
  
## <a name="blogs-and-videos"></a>Blogların ve videoların  
 [Visual Studio 2015 Tanılama Araçları hata ayıklayıcı penceresi](https://devblogs.microsoft.com/devops/diagnostic-tools-debugger-window-in-visual-studio-2015/)  
  
 [Blog: Visual Studio 2015 ' de hata ayıklarken bellek kullanımı aracı](https://devblogs.microsoft.com/devops/memory-usage-tool-while-debugging-in-visual-studio-2015/)  
  
 [Visual C++ blog: VS2015 Preview 'da yerel bellek tanılama](https://devblogs.microsoft.com/cppblog/native-memory-diagnostics-in-vs2015-preview/)  
  
 [Visual C++ blog: Visual Studio için yerel Bellek Tanılama Araçları 2015 CTP](https://devblogs.microsoft.com/cppblog/native-memory-diagnostic-tools-for-visual-studio-14-ctp/)
