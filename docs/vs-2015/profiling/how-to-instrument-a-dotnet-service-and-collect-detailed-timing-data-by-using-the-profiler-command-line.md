---
title: 'Nasıl yapılır: profil oluşturucu komut satırını kullanarak bir .NET hizmetini izleme ve ayrıntılı zamanlama verileri toplama | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 9f73593a-69a7-41b7-a21c-81d3ab0eb8fe
caps.latest.revision: 32
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b438cac78aa863eab4f04e250ed768d54a2fbc4c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64824825"
---
# <a name="how-to-instrument-a-net-service-and-collect-detailed-timing-data-by-using-the-profiler-command-line"></a>Nasıl yapılır: Profil Oluşturucu Komut Satırını Kullanarak bir .NET Hizmetini İzleme ve Ayrıntılı Zamanlama Verileri Toplama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu konu [!INCLUDE[vsPreShort](../includes/vspreshort-md.md)] [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] , bir hizmeti işaretlemek ve ayrıntılı zamanlama verilerini toplamak için profil oluşturma araçları komut satırı araçlarının nasıl kullanılacağını açıklar.  

> [!NOTE]
> Hizmet, bilgisayar başladıktan sonra yalnızca işletim sistemi başladığında başlatılan bir hizmet gibi yeniden başlatılırsa, izleme yöntemiyle bir hizmetin profilini oluşturamazsınız.  
>   
> Profil Oluşturma Araçları komut satırı araçları, yükleme dizininin \Team Tools\Performance Tools alt dizininde bulunur [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] . 64 bit bilgisayarlarda, araçların her ikisi de 64 bit ve 32 bit sürümleri mevcuttur. Profil oluşturucu komut satırı araçlarını kullanmak için araçlar yolunu komut istemi penceresinin PATH ortam değişkenine eklemeniz ya da komutun kendisine eklemeniz gerekir. Daha fazla bilgi için bkz. [komut satırı araçlarının yolunu belirtme](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
>   
> Bir profil oluşturma çalıştırmasına katman etkileşim verileri eklemek, komut satırı profil oluşturma araçlarıyla belirli yordamlar gerektirir. Bkz. [Katman etkileşimi verilerini toplama](../profiling/adding-tier-interaction-data-from-the-command-line.md).  

 İzleme yöntemini kullanarak bir hizmetten ayrıntılı zamanlama verileri toplamak için [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] , bileşenin belgelenmiş bir sürümünü oluşturmak için [VSInstr.exe](../profiling/vsinstr.md) aracını kullanın. Sonra, hizmetin el ile başlatılacak şekilde yapılandırıldığından emin olmak için, Service 'in belgelenmiş olmayan sürümünü belgelenmiş sürümle değiştirirsiniz. Genel profil oluşturma ortamı değişkenlerini başlatmak için [VSPerfCLREnv. cmd](../profiling/vsperfclrenv.md) aracını kullanın ve ardından ana bilgisayarı yeniden başlatın. Ardından profil oluşturucuyu başlatın.  

 Hizmet başlatıldığında, zamanlama verileri bir veri dosyasına otomatik olarak toplanır. Profil oluşturma oturumu sırasında veri toplamayı duraklatabilir ve devam ettirebilirsiniz.  

 Profil oluşturma oturumunu sonlandırmak için, hizmeti devre dışı bırakın ve ardından profil oluşturucuyu açıkça kapatın. Çoğu durumda, bir oturumun sonunda profil oluşturma ortam değişkenlerini temizlemeniz önerilir.  

## <a name="starting-the-application-with-the-profiler"></a>Uygulamayı Profil Oluşturucu ile başlatma  

#### <a name="to-start-profiling-a-net-framework-service"></a>.NET Framework bir hizmet profilini oluşturmaya başlamak için  

1. Bir komut istemi penceresi açın.  

2. Service binary 'ın belgelenmiş bir sürümünü oluşturmak için **vsinstr** aracını kullanın.  

3. Özgün ikilisini belgelenmiş sürümle değiştirin. Windows hizmet denetimi Yöneticisi 'nde, hizmet başlatma türünün manuel olarak ayarlandığından emin olun.  

4. [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]Profil oluşturma ortamı değişkenlerini başlatın. Şunu yazın:  

    **VSPerfClrEnv/globaltraceon**  

5. Bilgisayarı yeniden başlatın.  

6. Bir komut istemi penceresi açın.  

7. Profil oluşturucuyu başlatın. Şunu yazın:  

    **VSPerfCmd/start: Trace/output:** `OutputFile` [`Options`]  

   - [/Start](../profiling/start.md)**: Trace** seçeneği profil oluşturucuyu başlatır.  

   - /Start ile [/output](../profiling/output.md)**:** `OutputFile` seçeneği gereklidir. **/start** `OutputFile` profil oluşturma verileri (. vsp) dosyasının adını ve konumunu belirtir.  

     Aşağıdaki seçeneklerden herhangi birini, **/Start: Trace** seçeneği ile kullanabilirsiniz.  

   > [!NOTE]
   > **/User** ve **/CrossSession** seçenekleri genellikle profil oluşturma hizmetleri için gereklidir.  

   |                                 Seçenek                                  |                                                                                                                                            Açıklama                                                                                                                                             |
   |-------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   | [/User](../profiling/user-vsperfcmd.md) **:**[ `Domain` **\\** ]`UserName` |        Profili oluşturulan işlemin sahibi olan hesabın etki alanını ve Kullanıcı adını belirtir. Bu seçenek yalnızca, işlem oturum açmış kullanıcı dışında bir kullanıcı olarak çalışıyorsa gereklidir. İşlem sahibi, Windows Görev Yöneticisi 'nin Işlemler sekmesinde Kullanıcı adı sütununda listelenir.         |
   |              [/CrossSession](../profiling/crosssession.md)              | Diğer oturumlardaki işlemlerin profilini oluşturmaya izin vermez. Uygulama farklı bir oturumda çalışıyorsa, bu seçenek gereklidir. Oturum kimliği, Windows Görev Yöneticisi 'nin süreçler sekmesindeki oturum KIMLIĞI sütununda listelenir. **/CS** , **/CrossSession**için bir kısaltma olarak belirtilebilir. |
   |        [/WaitStart](../profiling/waitstart.md)[**:** `Interval` ]         |                                          Profil oluşturucunun hata vermeden önce başlatılması için bekleyeceği saniye sayısını belirtir. `Interval`Belirtilmezse, profil oluşturucu süresiz olarak bekler. Varsayılan olarak, **/Start** hemen döndürür.                                           |
   |          [/globaloff](../profiling/globalon-and-globaloff.md)           |                                                                      Veri toplama duraklatılmış şekilde profil oluşturucuyu başlatmak için, **/Start** komut satırına **/globaloff** seçeneğini ekleyin. Profil oluşturmayı sürdürmeye yönelik **/GlobalOn** kullanın.                                                                       |
   |           [/Counter](../profiling/counter.md) **:**`Config`            |                                                                    Yapılandırma içinde belirtilen işlemci performans sayacından bilgi toplar. Her profil oluşturma olayında toplanan verilere sayaç bilgileri eklenir.                                                                    |
   |    [/WINCOUNTER](../profiling/wincounter.md) **:**`WinCounterPath`     |                                                                                                             Profil oluşturma sırasında toplanacak bir Windows performans sayacı belirtir.                                                                                                              |
   |         [/AutoMark](../profiling/automark.md) **:**`Interval`          |                                                                           Yalnızca **/WINCOUNTER** ile kullanın. Windows performans sayacı toplama olayları arasındaki milisaniye sayısını belirtir. Varsayılan değer 500 MS 'dir.                                                                            |
   |       [/Events](../profiling/events-vsperfcmd.md) **:**`Config`        |                                                                              Profil oluşturma sırasında toplanacak bir Windows için olay Izleme (ETW) olayı belirtir. ETW olayları ayrı bir (. etl) dosyasında toplanır.                                                                              |

8. Hizmeti Windows hizmet denetimi Yöneticisi ' nden başlatın.  

## <a name="controlling-data-collection"></a>Veri Toplama Denetimi  
 Hizmet çalışırken, verileri profil oluşturucu veri dosyasına yazmayı başlatmak ve durdurmak için **VSPerfCmd.exe** seçeneklerini kullanabilirsiniz. Veri toplamayı denetlemek, program yürütmenin belirli bir bölümü için, hizmeti başlatma veya kapatma gibi verileri toplamanızı sağlar.  

#### <a name="to-start-and-stop-data-collection"></a>Veri toplamayı başlatmak ve durdurmak için  

- Aşağıdaki **VSPerfCmd** seçenek çiftleri veri toplamayı başlatır ve durdurur. Her seçeneği ayrı bir komut satırında belirtin. Veri toplamayı birden çok kez açıp kapatabilirsiniz.  

    |Seçenek|Açıklama|  
    |------------|-----------------|  
    |[/GlobalOn/globaloff](../profiling/globalon-and-globaloff.md)|Tüm süreçler için veri toplamayı başlatır (**/GlobalOn**) veya Durdur (**/globaloff**).|  
    |[/ProcessOn](../profiling/processon-and-processoff.md) **:** `PID` [/ProcessOff](../profiling/processon-and-processoff.md) **:**`PID`|İşlem KIMLIĞI () tarafından belirtilen işlem için (**/ProcessOn**) veya duraklar (**/ProcessOff**) veri toplamayı başlatır `PID` .|  
    |[/ThreadOn](../profiling/threadon-and-threadoff.md) **:** `TID` [/ThreadOff](../profiling/threadon-and-threadoff.md) **:**`TID`|İş parçacığı KIMLIĞI () tarafından belirtilen iş parçacığı için (**/ThreadOn**) veya Durdur (**/ThreadOff**) veri toplamayı başlatır `TID` .|  

## <a name="ending-the-profiling-session"></a>Profil oluşturma oturumu sonlandırılıyor  
 Profil oluşturma oturumunu sonlandırmak için, Araçlı bileşeni çalıştıran hizmeti durdurun ve ardından **VSPerfCmd** [/Shutdown](../profiling/shutdown.md) seçeneğini çağırıp profil oluşturucuyu kapatın ve profil oluşturma veri dosyasını kapatın. **VSPerfCLREnv/globaloff** komutu profil oluşturma ortam değişkenlerini temizler.  

 Yeni ortam ayarlarının uygulanması için bilgisayarı yeniden başlatmanız gerekir.  

#### <a name="to-end-a-profiling-session"></a>Profil oluşturma oturumunu sonlandırmak için  

1. Hizmeti hizmet denetimi Yöneticisi 'nden durdurun.  

2. Profil oluşturucuyu kapatın. Şunu yazın:  

     **VSPerfCmd/shutdown**  

3. Tüm profil oluşturmayı tamamladığınızda, profil oluşturma ortam değişkenlerini temizleyin. Şunu yazın:  

     **VSPerfClrEnv/globaloff**  

4. Belgelenmiş modülün değerini özgün ile değiştirin. Gerekirse, hizmetin başlangıç türünü yeniden yapılandırın.  

5. Bilgisayarı yeniden başlatın.  

## <a name="see-also"></a>Ayrıca Bkz.  
 [Profil oluşturma hizmetleri](../profiling/command-line-profiling-of-services.md)   
 [İzleme Metodu Veri Görünümleri](../profiling/instrumentation-method-data-views.md)
