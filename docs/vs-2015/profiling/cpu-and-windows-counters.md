---
title: CPU ve Windows sayaçları | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.property.counters
helpviewer_keywords:
- Windows counters in Profiling Tools
- CPU counters in Profiling Tools
ms.assetid: d2c45c6a-f975-45ab-b8a5-4768ddd518fb
caps.latest.revision: 33
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: eceadf1b1bf82876a20027a9d29c8336e381d18d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64808659"
---
# <a name="cpu-and-windows-counters"></a>CPU ve Windows Sayaçları
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio Profiler, işletim sistemi (Windows sayaçları) tarafından oluşturulan performans verilerini ve işlemci birimi (CPU sayaçları) tarafından oluşturulan performans verilerini toplamanıza olanak sağlar.  
  
 **Gereksinimler**  
  
- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
> [!NOTE]
> Windows 8 ve Windows Server 2012 ' deki gelişmiş güvenlik özellikleri, Visual Studio Profiler 'ın bu platformlarda verileri nasıl topladığı konusunda önemli değişiklikler gerektirdi. Windows Mağazası uygulamaları da yeni koleksiyon teknikleri gerektirir. Bkz. [Windows 8 ve Windows Server 2012 uygulamalarında performans araçları](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
## <a name="windows-counters"></a>Windows sayaçları  
 Windows sayaçları, işletim sisteminin veya bir uygulamanın, bir hizmetin veya bir sürücünün performansı hakkında bilgi sağlayan Windows Tanılama altyapısının bir parçasıdır. Windows sayaçları, geçerli bilgisayarın yapılandırmasına bağlıdır ve diğer bilgisayarlarda kullanılamayabilir. Windows performans sayaçları, profil oluşturma işaretleri olarak veri dosyalarında toplanır ve bu sayede görünümleri ve raporları filtrelemek için kullanılabilir.  
  
## <a name="cpu-counters"></a>CPU sayaçları  
 CPU sayaçları, donanım ile ilgili olayların sayısını depolayan bilgisayarın CPU özelliğidir.  İzleme profili oluşturma yöntemini kullanarak CPU sayacı verileri topladığınızda, veriler işlevler ve modüller için verilere eklenir. İzleme yöntemini kullanarak birden çok CPU sayacı toplayabilirsiniz. Örnekleme yöntemini kullandığınızda, örneklendiği olay olarak kullanılacak bir sayaç seçersiniz.  
  
 Performans sayaçları, CPU 'ya özeldir. Bir CPU 'nun farklı modelleri ve sürümleri, aynı performans sayacını etkinleştirmek için önemli ölçüde farklı yapılandırma ayarlarına sahip olabilir. [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] Profil Oluşturucu taşınabilir olayları belirli işlemcilerin bazı yaygın performans sayaçlarını ayırır ve genel performans olaylarını toplamanıza veya örneklemenizi sağlar.  
  
 Profil oluşturucuyu kullandığınızda belirli bir olayı saymak istiyorsanız, örneğin L2 önbellek isabetsizliği, bu olay göndericisinin çevresinde bir performans oturumu oluşturabilirsiniz. Bunu L2 önbelleğiyle herhangi bir CPU 'da yapabilirsiniz. Performans oturumu, değişiklik yapılmadan platformdan platforma taşınabilir.  
  
 Visual Studio Profiler, belirli bir platform için belirli olayları desteklemeye devam eder. Örneğin, bir Pentium 4 platformunda bir geliştirici Netpatlaması mimarisine özgü olan olayları saymak isteyebilir. Bu olay taşınabilir değildir, ancak belirli bir platformda belirli bir performans oturumu için geliştirici tarafından kullanılabilir.  
  
## <a name="portable-and-platform-events"></a>Taşınabilir ve platform olayları  
 Taşınabilir olaylar, belirli bir işlemciye özgü olmayan bir CPU sayaçları grubudur. Diğer tüm CPU sayaçlarına platform olayları denir ve çeşitli platformlarda desteklenmeyebilir.  
  
 Hem taşınabilir hem de platform olaylarının sayaçları ' de tanımlanmıştır. Sayaçlarıyla ilgili belirli değerlerin sağlandığı XML dosyaları. Farklı CPU 'lar için birden çok dosya vardır, çünkü Örneğin, Intel ve AMD CPU 'Lar için veriler farklıdır. [!INCLUDE[vs_orcas_long](../includes/vs-orcas-long-md.md)]Profiler bu bilgileri, hem taşınabilir hem de platform için uygun sayaçları, performans ölçümü için kullanıcıya sunmak üzere kullanır.  
  
### <a name="portable-events"></a>Taşınabilir olaylar  
 Taşınabilir olaylar aşağıdaki olayları içerir:  
  
 **Genel Olaylar**  
  
|Olay Adı|Olay Açıklaması|  
|----------------|-----------------------|  
|Yönergeler kullanımdan kaldırıldı|Olay tamamlanana kadar yürütülen yönergelerin sayısını belirtir.|  
|Durdurulmayan döngüler|Yalnızca işlemcinin durdurulmadığını belirtir (örneğin, g/ç bekleniyor).|  
  
 **Ön uç olayları**  
  
|Olay Adı|Olay Açıklaması|  
|----------------|-----------------------|  
|ILB Isabetsizliği|Bir isabetsizlik ile sonuçlanan yönerge çevirisi arama arabelleği aramalarının sayısını belirtir.|  
  
 **Dal olayları**  
  
|Olay Adı|Olay Açıklaması|  
|----------------|-----------------------|  
|Dallar kullanımdan kaldırıldı|Olay tamamlanana kadar yürütülen dal yönergelerinin sayısını belirtir.|  
|Yanlış tahmin edilen dallar|İşlemcinin hatalı bir yolu tahmin ettiğinden oluşan, yanlış tahmin edilen dalları gösterir. Yanlış tahmin edilen dallar, işlemcinin tüm işleri atıp doğru bir yolda yeniden başlaması gerektiğinden performansı etkiler.|  
  
 **Bellek olayları:**  
  
|Olay Adı|Olay Açıklaması|  
|----------------|-----------------------|  
|L2 önbellek okuma Isabetsizliği|İkinci düzey önbellek okuma isabetsizlik sayısını belirtir.|  
|L2 önbellek okuma başvuruları|İkinci düzey önbellek okuma başvurularının sayısını belirtir. Yükleme isabetsizliği ve sahiplik (RFO) isabetsizliği ve isabetler için okuma içerir.|  
  
## <a name="viewing-available-counters"></a>Kullanılabilir sayaçları görüntüleme  
 Visual Studio IDE 'deki kullanılabilir CPU sayaçlarını bir komut Istemi penceresinde listeleyebilirsiniz.  
  
### <a name="visual-studio-ui"></a>Visual Studio Kullanıcı arabirimi  
 Visual Studio IDE 'deki bir bilgisayardaki kullanılabilir sayaçları listelemek için Performans Gezgini bir profiler performans oturumunun açık olması gerekir.  
  
##### <a name="to-view-a-list-of-a-list-of-all-cpu-counters-that-are-supported-on-the-current-platform"></a>Geçerli platformda desteklenen tüm CPU sayaçlarının listesini görüntülemek için  
  
1. Performans Gezgini, performans oturumuna sağ tıklayın ve ardından **Özellikler**' e tıklayın.  
  
2. Şunlardan birini yapın:  
  
   - **Örnekleme**' ye tıklayın ve ardından **örnek** olay listesinden **performans sayacı** ' nı seçin. CPU sayaçları **kullanılabilir performans sayaçlarında**listelenir.  
  
      **Göz önünde** Önceki örnekleme yapılandırmasına geri dönmek için **iptal** 'e tıklayın.  
  
     -veya-  
  
   - **CPU sayaçlarını**seçin ve ardından **CPU sayaçlarını topla**' yı seçin. CPU sayaçları **kullanılabilir sayaçlara**göre listelenmiştir.  
  
      **Göz önünde** Önceki sayaç koleksiyonu yapılandırmasına dönmek için **iptal** 'e tıklayın.  
  
##### <a name="to-view-a-list-of-a-list-of-window-counters-that-are-supported-on-the-current-platform"></a>Geçerli platformda desteklenen pencere sayaçlarının listesinin bir listesini görüntülemek için  
  
1. Performans Gezgini, performans oturumuna sağ tıklayın ve ardından **Özellikler**' e tıklayın.  
  
2. **Windows sayaçları**' na tıklayın.  
  
3. **Windows sayaçlarını topla**' yı seçin.  
  
4. **Sayaç kategorisi** listesinden bir sayaç grubu seçin. Grubun Windows sayacı liste kutusunda görüntülenir.  
  
     **Note:** Önceki sayaç koleksiyonu yapılandırmasına dönmek için **iptal** 'e tıklayın.  
  
### <a name="command-line"></a>Komut Satırı  
 [VSPerfCmd](../profiling/vsperfcmd.md) komut satırı aracını kullanarak bir BILGISAYARDAKI kullanılabilir CPU sayaçlarını komut satırından listeleyebilirsiniz.  
  
##### <a name="to-list-of-cpu-counters-that-are-supported-on-the-current-platform"></a>Geçerli platformda desteklenen CPU sayaçlarının listesi  
  
1. Bir komut istemi penceresi açın.  
  
2. Tür  
  
     **\<Visual Studio Performance Tools Directory>\VSPerfCmd/QueryCounters**  
  
     burada, **\<Visual Studio Performance Tools Directory>** Visual Studio yüklemenizin performans araçları dizininin yoludur, genellikle  
  
     C:\Program Files\Microsoft Visual Studio 10.0 \ Team Tools\performans araçları  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Tahmin](../profiling/overviews-performance-tools.md)   
 [Nasıl yapılır: örnekleme olaylarını seçme](../profiling/how-to-choose-sampling-events.md)   
 [Nasıl yapılır: CPU sayacı verilerini toplama](../profiling/how-to-collect-cpu-counter-data.md)   
 [Nasıl yapılır: Windows sayaç verileri toplama](../profiling/how-to-collect-windows-counter-data.md)
