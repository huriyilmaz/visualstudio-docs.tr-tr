---
title: 'Nasıl yapılır: profil oluşturucu komut satırını kullanarak bir .NET Framework hizmeti izleme ve bellek verileri toplama | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 2fa072fc-05fe-4420-99c0-51d2ea3ac4ce
caps.latest.revision: 29
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d76eb9882eaf51de031d886c15954df8d5180e25
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64803789"
---
# <a name="how-to-instrument-a-net-framework-service-and-collect-memory-data-by-using-the-profiler-command-line"></a>Nasıl yapılır: Profil Oluşturucu Komut Satırını Kullanarak .NET Framework Hizmetini İzleme ve Bellek Verileri Toplama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu konu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] , bir hizmeti işaretlemek ve bellek kullanım verilerini toplamak için profil oluşturma araçları komut satırı araçlarının nasıl kullanılacağını açıklar. Bellek ayırma verilerini toplayabilir veya hem bellek ayırma hem de nesne yaşam verileri toplayabilirsiniz.  

> [!NOTE]
> Windows 8 ve Windows Server 2012 ' deki gelişmiş güvenlik özellikleri, Visual Studio Profiler 'ın bu platformlarda verileri nasıl topladığı konusunda önemli değişiklikler gerektirdi. Windows Mağazası uygulamaları da yeni koleksiyon teknikleri gerektirir. Bkz. [Windows 8 ve Windows Server 2012 uygulamalarında performans araçları](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  

> [!NOTE]
> Hizmet, işletim sistemi başladığında başlayan bir hizmet gibi, bilgisayar başladıktan sonra yeniden başlatılamazsa, izleme yöntemiyle bir hizmetin profilini oluşturamazsınız.  
>   
> Profil Oluşturma Araçları komut satırı araçları, yükleme dizininin \Team Tools\Performance Tools alt dizininde bulunur [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] . 64 bit bilgisayarlarda, araçların her ikisi de 64 bit ve 32 bit sürümleri mevcuttur. Profil oluşturucu komut satırı araçlarını kullanmak için araçlar yolunu komut istemi penceresinin PATH ortam değişkenine eklemeniz ya da komutun kendisine eklemeniz gerekir. Daha fazla bilgi için bkz. [komut satırı araçlarının yolunu belirtme](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  

## <a name="starting-the-profiling-session"></a>Profil oluşturma oturumu başlatılıyor  
 Bir hizmetten performans verilerini toplamak için [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] [VSPerfCLREnv. cmd](../profiling/vsperfclrenv.md) aracını kullanarak, hizmet ikili dosyasının belgelenmiş bir kopyasını oluşturmak için uygun ortam değişkenlerini ve [VSInstr.exe](../profiling/vsinstr.md) aracını başlatın.  

 Profili oluşturmak üzere yapılandırmak için hizmeti barındıran bilgisayarın yeniden başlatılması gerekir. Hizmeti hizmet denetimi Yöneticisi 'nden de el ile başlatmanız gerekir. Ardından profil oluşturucuyu başlatıp [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] hizmeti başlatabilirsiniz.  

 Araçlı bileşen yürütüldüğünde, bellek verileri otomatik olarak bir veri dosyasına toplanır. Profil oluşturma oturumu sırasında veri toplamayı duraklatabilir ve devam ettirebilirsiniz.  

 Profil oluşturma oturumunu sonlandırmak için hizmeti kapatır ve profil oluşturucuyu açıkça kapatın. Çoğu durumda, bir oturumun sonunda profil oluşturma ortam değişkenlerini temizlemeniz önerilir.  

#### <a name="to-begin-profiling-a-net-framework-service"></a>.NET Framework bir hizmetin profilini oluşturmaya başlamak için  

1. Bir komut istemi penceresi açın.  

2. Service binary 'ın belgelenmiş bir sürümünü oluşturmak için **vsinstr** aracını kullanın.  

3. Özgün ikiliyi belgelenmiş sürümle değiştirmek için hizmet denetimi Yöneticisi 'ni kullanın. Hizmet başlatma türünün manuel olarak ayarlandığından emin olun.  

4. Profil oluşturma ortamı değişkenlerini başlatın. Şunu yazın:  

    **VSPerfCLREnv** {**/globaltracegc** &#124; **/globaltracegclife**}  

   - **/globaltracegc** ve **/globaltracegclife** bellek ayırma ve nesne yaşam süresi verilerinin toplanmasını etkinleştirir.  

       |Seçenek|Açıklama|  
       |------------|-----------------|  
       |**/globaltracegc**|Yalnızca bellek ayırma verilerini toplar.|  
       |**/globaltracegclife**|Bellek ayırma ve nesne yaşam süresi verilerini toplar.|  

5. Bilgisayarı yeniden başlatın.  

6. Bir komut istemi penceresi açın.  

7. Profil oluşturucuyu başlatın. Şunu yazın:  

    **VSPerfCmd**  [/Start](../profiling/start.md) **: Trace**  [/output](../profiling/output.md) **:** `OutputFile` [ `Options` ]  

   - **/Start: çekişme** seçeneği profil oluşturucuyu başlatır.  

   - /Start ile **/output:** `OutputFile` seçeneği gereklidir. **/start** `OutputFile` profil oluşturma verileri (. vsp) dosyasının adını ve konumunu belirtir.  

     Aşağıdaki seçeneklerden herhangi birini, **/Start: Sample** seçeneğiyle kullanabilirsiniz.  

   > [!NOTE]
   > **/User** ve **/CrossSession** seçenekleri genellikle hizmetler için gereklidir.  

   |                                 Seçenek                                  |                                                                                                                                                   Açıklama                                                                                                                                                    |
   |-------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   | [/User](../profiling/user-vsperfcmd.md) **:**[ `Domain` **\\** ]`UserName` |               ASP.NET çalışan işleminin sahibi olan hesabın etki alanını ve Kullanıcı adını belirtir. İşlem, oturum açmış kullanıcı dışında bir kullanıcı olarak çalışıyorsa, bu seçenek gereklidir. İşlem sahibi, Windows Görev Yöneticisi 'nin Işlemler sekmesinde Kullanıcı adı sütununda listelenir.               |
   |              [/CrossSession](../profiling/crosssession.md)              | Diğer oturum oturumlarda işlemlerin profilini oluşturmayı mümkün. ASP.NET uygulaması farklı bir oturumda çalışıyorsa, bu seçenek gereklidir. Oturum kimliği, Windows Görev Yöneticisi 'nin süreçler sekmesindeki oturum KIMLIĞI sütununda listelenir. **/CS** , **/CrossSession**için bir kısaltma olarak belirtilebilir. |
   |        [/WaitStart](../profiling/waitstart.md)[**:** `Interval` ]         |                                                 Profil oluşturucunun hata vermeden önce başlatılması için bekleyeceği saniye sayısını belirtir. `Interval`Belirtilmezse, profil oluşturucu süresiz olarak bekler. Varsayılan olarak, **/Start** hemen döndürür.                                                  |
   |          [/globaloff](../profiling/globalon-and-globaloff.md)           |                                                                             Veri toplama duraklatılmış şekilde profil oluşturucuyu başlatmak için, **/Start** komut satırına **/globaloff** seçeneğini ekleyin. Profil oluşturmayı sürdürmeye yönelik **/GlobalOn** kullanın.                                                                              |
   |           [/Counter](../profiling/counter.md) **:**`Config`            |                                                                           Yapılandırma içinde belirtilen işlemci performans sayacından bilgi toplar. Her profil oluşturma olayında toplanan verilere sayaç bilgileri eklenir.                                                                           |
   |    [/WINCOUNTER](../profiling/wincounter.md) **:**`WinCounterPath`     |                                                                                                                    Profil oluşturma sırasında toplanacak bir Windows performans sayacı belirtir.                                                                                                                     |
   |         [/AutoMark](../profiling/automark.md) **:**`Interval`          |                                                                                  Yalnızca **/WINCOUNTER** ile kullanın. Windows performans sayacı toplama olayları arasındaki milisaniye sayısını belirtir. Varsayılan değer 500 MS 'dir.                                                                                   |
   |       [/Events](../profiling/events-vsperfcmd.md) **:**`Config`        |                                                                                     Profil oluşturma sırasında toplanacak bir Windows için olay Izleme (ETW) olayı belirtir. ETW olayları ayrı bir (. etl) dosyasında toplanır.                                                                                     |

8. Gerekirse, hizmeti başlatın.  

9. Profil oluşturucuyu hizmete ekleyin. Şunu yazın:  

     **VSPerfCmd/Attach:** `PID`&#124;`ProcessName`  

    - Hizmetin işlem KIMLIĞINI veya işlem adını belirtin. Windows Görev Yöneticisi 'nde çalışan tüm işlemlerin işlem kimliklerini ve adlarını görüntüleyebilirsiniz.  

## <a name="controlling-data-collection"></a>Veri Toplama Denetimi  
 Hizmet çalışırken, verileri dosyaya yazmayı **VSPerfCmd.exe** seçeneklerle başlatıp durdurarak veri toplamayı kontrol edebilirsiniz. Veri toplamayı denetlemek, program yürütmesinin, uygulamayı başlatma veya kapatma gibi belirli bir bölümü için veri toplamanızı sağlar.  

#### <a name="to-start-and-stop-data-collection"></a>Veri toplamayı başlatmak ve durdurmak için  

- Aşağıdaki **VSPerfCmd** seçenek çiftleri veri toplamayı başlatır ve durdurur. Her seçeneği ayrı bir komut satırında belirtin. Veri toplamayı birden çok kez açıp kapatabilirsiniz.  

    |Seçenek|Açıklama|  
    |------------|-----------------|  
    |[/GlobalOn/globaloff](../profiling/globalon-and-globaloff.md)|Tüm süreçler için veri toplamayı başlatır (**/GlobalOn**) veya Durdur (**/globaloff**).|  
    |[/ProcessOn](../profiling/processon-and-processoff.md) **:** `PID` [/ProcessOff](../profiling/processon-and-processoff.md) **:**`PID`|İşlem KIMLIĞI () tarafından belirtilen işlem için (**/ProcessOn**) veya duraklar (**/ProcessOff**) veri toplamayı başlatır `PID` .|  
    |[/ThreadOn](../profiling/threadon-and-threadoff.md) **:** `TID` [/ThreadOff](../profiling/threadon-and-threadoff.md) **:**`TID`|İş parçacığı KIMLIĞI () tarafından belirtilen iş parçacığı için (**/ThreadOn**) veya Durdur (**/ThreadOff**) veri toplamayı başlatır `TID` .|  

## <a name="ending-the-profiling-session"></a>Profil oluşturma oturumu sonlandırılıyor  
 Profil oluşturma oturumunu sonlandırmak için, Araçlı bileşeni çalıştıran uygulamayı kapatın ve ardından **VSPerfCmd** [/Shutdown](../profiling/shutdown.md) seçeneğini başlatıp profil oluşturucuyu kapatın ve profil oluşturma veri dosyasını kapatın. **VSPerfCLREnv/globaloff** komutu profil oluşturma ortam değişkenlerini temizler.  

#### <a name="to-end-a-profiling-session"></a>Profil oluşturma oturumunu sonlandırmak için  

1. Hizmeti hizmet denetimi Yöneticisi 'nden durdurun.  

2. Profil oluşturucuyu kapatın. Şunu yazın:  

     **VSPerfCmd/shutdown**  

3. Tüm profil oluşturmayı tamamladığınızda, profil oluşturma ortam değişkenlerini temizleyin. Şunu yazın:  

     **VSPerfClrEnv/globaloff**  

     Belgelenmiş modülün değerini özgün ile değiştirin. Gerekirse, hizmetin başlangıç türünü yeniden yapılandırın.  

4. Bilgisayarı yeniden başlatın.  

## <a name="see-also"></a>Ayrıca Bkz.  
 [Profil oluşturma hizmetleri](../profiling/command-line-profiling-of-services.md)   
 [.NET bellek verileri görünümleri](../profiling/dotnet-memory-data-views.md)
