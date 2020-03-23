---
title: CPU ve Windows Sayaçları | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.property.counters
helpviewer_keywords:
- Windows counters in Profiling Tools
- CPU counters in Profiling Tools
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 9accd3d0ab5ff1f7a3084d5973cace08e66396b9
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779556"
---
# <a name="cpu-and-windows-counters"></a>CPU ve Windows sayaçları

Visual Studio Profiler, işletim sistemi (Windows sayaçları) tarafından oluşturulan performans verilerini ve işlemci birimi (CPU sayaçları) tarafından oluşturulan performans verilerini toplamanızı sağlar.

> [!NOTE]
> Windows 8 ve Windows Server 2012'deki gelişmiş güvenlik özellikleri, Visual Studio profil oluşturucusu bu platformlarda veri toplama şeklinde önemli değişiklikler gerektiriyordu. UWP uygulamaları da yeni toplama teknikleri gerektirir. [Windows 8 ve Windows Server 2012 uygulamalarında Performans Araçları'na](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)bakın.

## <a name="windows-counters"></a>Windows sayaçları

Windows sayaçları, işletim sisteminin veya uygulamanın, hizmetin veya sürücünün performansı hakkında bilgi sağlayan Windows tanı altyapısının bir parçasıdır. Windows sayaçları geçerli bilgisayarın yapılandırması bağlıdır ve diğer bilgisayarlarda kullanılamayabilir. Windows performans sayaçları profil oluşturma işaretleri olarak profil oluşturma veri dosyaları toplanır, daha sonra görünümleri ve raporları filtrelemek için kullanılabilir.

## <a name="cpu-counters"></a>CPU sayaçları

CPU sayaçları, bilgisayarın işlemcisinin donanımla ilgili olayların sayısını depolayan bir özelliğidir. Enstrümantasyon profiloluşturma yöntemini kullanarak CPU karşı verilerini topladığınızda, veriler işlevler ve modüller için verilere eklenir. Enstrümantasyon yöntemini kullanarak birden çok CPU sayacı toplayabilirsiniz. Örnekleme yöntemini kullandığınızda, örneklenecek olay olarak kullanmak üzere bir sayaç seçersiniz.

Performans sayaçları CPU'ya özgür. Cpu'nun farklı modelleri ve sürümleri, aynı performans sayacını etkinleştirmek için önemli ölçüde farklı yapılandırma ayarlarına sahip olabilir. [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)]Profiler taşınabilir olaylar, bazı yaygın performans sayaçlarını belirli işlemcilerden ayırır ve genel performans olaylarını toplamanızı veya örneklemenizi sağlar.

Profil oluşturucuyu kullandığınızda belirli bir olayı saymak istiyorsanız, örneğin, L2 önbelleği kaçırırsa, bu olay gönderenin etrafında bir performans oturumu oluşturabilirsiniz. Bunu, L2 önbelleği yle herhangi bir CPU'da yapabilirsiniz. Performans oturumu değişiklik yapılmadan platformdan platforma taşınabilir.

Visual Studio profiloluşturucubelirli bir platform için belirli olayları desteklemeye devam ediyor. Örneğin, Pentium 4 platformundaki bir geliştirici NetBurst mimarisine özgü olayları saymak isteyebilir. Bu olay taşınabilir değildir, ancak belirli bir platformda belirli bir performans oturumu için geliştirici tarafından kullanılabilir.

## <a name="portable-and-platform-events"></a>Taşınabilir ve platform etkinlikleri

Taşınabilir olaylar, belirli bir işlemciye özgü olmayan bir CPU sayacı grubudur. Diğer tüm CPU sayaçları platform olayları olarak adlandırılır ve çeşitli platformlarda desteklenmeyebilir.

 Hem taşınabilir hem de platform olayları için sayaçlar . *sayaçlarla* ilgili belirli değerlerin sağlandığı xml dosyaları. Örneğin Intel ve AMD CPU'ları için veriler farklı olduğundan, farklı CPU'lar için birden çok dosya vardır. Profiler bu [!INCLUDE[vs_orcas_long](../debugger/includes/vs_orcas_long_md.md)] bilgileri, performans ölçümü için kullanıcıya hem taşınabilir hem de platformlu uygun sayaçları sunmak için kullanır.

### <a name="portable-events"></a>Taşınabilir olaylar

Taşınabilir olaylar aşağıdaki olayları içerir:

**Genel Olaylar**

|Olay Adı|Olay Açıklaması|
|----------------|-----------------------|
|Talimatlar Emekli|Olay tamamlanana kadar yürütülen yönergelerin sayısını gösterir.|
|Durdurulmayan Döngüler|Yalnızca işlemcinin durdurulan döngüleri gösterir, örneğin G/Ç'yi beklerken.|

**Ön Uç Etkinlikleri**

|Olay Adı|Olay Açıklaması|
|----------------|-----------------------|
|ITLB Özlüyor|Kullanım Çevirisi Görünüm kenara Arabellek aramalarının sayısını gösterir ve bu da kaçırılmayla sonuçlanır.|

**Şube Etkinlikleri**

|Olay Adı|Olay Açıklaması|
|----------------|-----------------------|
|Şubeler Emekli|Olay tamamlanana kadar yürütülen şube yönergelerinin sayısını gösterir.|
|Yanlış tahmin edilen Dallar|İşlemci yanlış bir yol öngördüğü için hatalı tahmin edilen dalları gösterir. Hatalı tahmin edilen dallar performansı etkiler, çünkü işlemcinin yapılan tüm işleri atması ve doğru yolda yeniden başlaması gerekir.|

**Bellek Olayları:**

|Olay Adı|Olay Açıklaması|
|----------------|-----------------------|
|L2 Önbellek Okuma Misses|İkinci düzey önbellek okuma sayısını gösterir.|
|L2 Önbellek Okuma Başvuruları|İkinci düzey önbellek okuma başvurularının sayısını gösterir. Bu yük misses içerir ve mülkiyet (RFO) özlüyor ve isabet için okuyun.|

## <a name="view-available-counters"></a>Kullanılabilir sayaçları görüntüleme

Visual Studio IDE'deki kullanılabilir CPU sayaçlarını Komut İstemi penceresinde listeleyebilirsiniz.

### <a name="visual-studio-ui"></a>Görsel Stüdyo UI

Visual Studio IDE'deki bir bilgisayardaki kullanılabilir sayaçları listelemek için Performance Explorer'da açık bir profil oluşturucu performans oturumunuz olması gerekir.

#### <a name="to-view-a-list-of-a-list-of-all-cpu-counters-that-are-supported-on-the-current-platform"></a>Geçerli platformda desteklenen tüm CPU sayaçlarının listesini görüntülemek için

1. Performans Gezgini'nde performans oturumuna sağ tıklayın ve ardından **Özellikler'i**tıklatın.

2. Aşağıdakilerden birini yapın:

   - **Örnekle'yi**tıklatın ve ardından **Örnek** olay listesinden **Performans sayacını** seçin. CPU sayaçları Kullanılabilir **performans sayaçlarında**listelenir.

      **Not** Önceki örnekleme yapılandırmasına dönmek için **İptal'i** tıklatın.

     -veya-

   - **CPU Sayaçları'nı**seçin ve ardından **CPU Sayaçlarını Topla'yı**seçin. CPU sayaçları Kullanılabilir **sayaçlarda**listelenir.

      **Not** Önceki sayaç koleksiyonu yapılandırmasına dönmek için **İptal'i** tıklatın.

#### <a name="to-view-a-list-of-a-list-of-window-counters-that-are-supported-on-the-current-platform"></a>Geçerli platformda desteklenen Pencere sayaçlarının listesini görüntülemek için

1. Performans Gezgini'nde performans oturumuna sağ tıklayın ve ardından **Özellikler'i**tıklatın.

2. **Windows Sayaçları'nı**tıklatın.

3. **Windows Sayaçlarını Topla'yı**seçin.

4. Sayaç **Kategorisi** listesinden bir sayaç grubu seçin. Grubun Windows sayacı liste kutusunda görüntülenir.

     **Not:** Önceki sayaç koleksiyonu yapılandırmasına dönmek için **İptal'i** tıklatın.

### <a name="command-line"></a>Komut satırı

[VSPerfCmd](../profiling/vsperfcmd.md) komut satırı aracını kullanarak, bilgisayarda bulunan CPU sayaçlarını komut satırından listeleyebilirsiniz.

#### <a name="to-list-of-cpu-counters-that-are-supported-on-the-current-platform"></a>Geçerli platformda desteklenen CPU sayaçları listesi için

1. Bir komut istemi penceresi açın.

2. Tür

     **\<Visual Studio Performans Araçları Dizin>\VSPerfCmd /querycounters**

     * \<Visual Studio Performans Araçları Dizin>* Visual Studio yüklemenizin Performans Araçları dizinine giden yoldur. Performans araçlarına giden yolu almak için [bkz.](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)

## <a name="see-also"></a>Ayrıca bkz.

[Genel Bakış](../profiling/overviews-performance-tools.md)[Lar Nasıl Seçilir: Örnekleme olaylarını](../profiling/how-to-choose-sampling-events.md)
seçme[nasıl: CPU karşı veri](../profiling/how-to-collect-cpu-counter-data.md)
toplama[Nasıl: Windows karşı veri toplama](../profiling/how-to-collect-windows-counter-data.md) 

