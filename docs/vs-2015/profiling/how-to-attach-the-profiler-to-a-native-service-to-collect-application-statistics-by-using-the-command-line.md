---
title: 'Nasıl yapılır: komut satırını kullanarak uygulama Istatistikleri toplamak için bir yerel hizmete profil oluşturucu Iliştirme | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: f783817f-77a0-4eb8-985b-ec3b77eadc42
caps.latest.revision: 30
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2a2884229024cfc212c408b0d07e5b94a41737ac
ms.sourcegitcommit: fb8babf5cd72f1fc2f97ffe4ad7b62d91f325f61
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2020
ms.locfileid: "64779762"
---
# <a name="how-to-attach-the-profiler-to-a-native-service-to-collect-application-statistics-by-using-the-command-line"></a>Nasıl yapılır: Komut Satırını Kullanarak Uygulama İstatistikleri Toplamak için bir Yerel Hizmete Profil Oluşturucu Ekleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu konu, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] bir yerel hizmete profil oluşturucu eklemek ve örnekleme yöntemini kullanarak performans istatistikleri toplamak için profil oluşturma araçları komut satırı araçlarının nasıl kullanılacağını açıklar.  

> [!NOTE]
> Windows 8 ve Windows Server 2012 ' deki gelişmiş güvenlik özellikleri, Visual Studio Profiler 'ın bu platformlarda verileri nasıl topladığı konusunda önemli değişiklikler gerektirdi. Windows Mağazası uygulamaları da yeni koleksiyon teknikleri gerektirir. Bkz. [Windows 8 ve Windows Server 2012 uygulamalarında performans araçları](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  

> [!NOTE]
> Profil Oluşturma Araçları komut satırı araçları, yükleme dizininin \Team Tools\Performance Tools alt dizininde bulunur [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] . 64 bit bilgisayarlarda, araçların her ikisi de 64 bit ve 32 bit sürümleri mevcuttur. Profil oluşturucu komut satırı araçlarını kullanmak için araçlar yolunu komut istemi penceresinin PATH ortam değişkenine eklemeniz ya da komutun kendisine eklemeniz gerekir. Daha fazla bilgi için bkz. [komut satırı araçlarının yolunu belirtme](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  

 Profil Oluşturucu hizmete iliştirirken, veri toplamayı duraklatabilir ve devam ettirebilirsiniz.  

 Profil oluşturma oturumunu sonlandırmak için, profil oluşturucunun hizmetten ayrılması ve ve açıkça kapatılması gerekir.  

## <a name="starting-the-application-with-the-profiler"></a>Uygulamayı Profil Oluşturucu ile başlatma  
 Profil oluşturucuyu yerel bir hizmete iliştirmek için, **VSPerfCmd.exe** [/Start](../profiling/start.md) ve [/Attach](../profiling/attach.md) seçeneklerini kullanarak profil oluşturucuyu başlatabilir ve hedef uygulamaya iliştirebilirsiniz. **/Start** ve **/Attach** ve ilgili seçeneklerini tek bir komut satırında belirtebilirsiniz. Ayrıca, hedef uygulamanın başlangıcında veri toplamayı duraklatmak için [/globaloff](../profiling/globalon-and-globaloff.md) seçeneğini de ekleyebilirsiniz. Daha sonra, veri toplamaya başlamak için [/GlobalOn](../profiling/globalon-and-globaloff.md) kullanabilirsiniz.  

#### <a name="to-attach-the-profiler-to-a-native-service"></a>Profil oluşturucuyu yerel bir hizmete eklemek için  

1. Gerekirse, hizmeti başlatın.  

2. Bir komut istemi penceresi açın.  

3. Profil oluşturucuyu başlatın. Şunu yazın:  

    **VSPerfCmd/start: örnek**  [/output](../profiling/output.md) **:** `OutputFile` [ `Options` ]  

   - **/Start: örnek** seçeneği, profil oluşturucuyu başlatır.  

   - /Start ile **/output:** `OutputFile` seçeneği gereklidir. **/start** `OutputFile` profil oluşturma verileri (. vsp) dosyasının adını ve konumunu belirtir.  

     Aşağıdaki seçeneklerden herhangi birini, **/Start: Sample** seçeneğiyle kullanabilirsiniz.  

   > [!NOTE]
   > **/User** ve **/CrossSession** seçenekleri genellikle hizmetler için gereklidir.  

   |                                 Seçenek                                  |                                                                                                                                            Açıklama                                                                                                                                             |
   |-------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   | [/User](../profiling/user-vsperfcmd.md) **:**[ `Domain` **\\** ]`UserName` |        Profili oluşturulan işlemin sahibi olan hesabın etki alanını ve Kullanıcı adını belirtir. Bu seçenek yalnızca, işlem oturum açmış kullanıcı dışında bir kullanıcı olarak çalışıyorsa gereklidir. İşlem sahibi, Windows Görev Yöneticisi 'nin Işlemler sekmesinde Kullanıcı adı sütununda listelenir.         |
   |              [/CrossSession](../profiling/crosssession.md)              | Diğer oturumlardaki işlemlerin profilini oluşturmaya izin vermez. Uygulama farklı bir oturumda çalışıyorsa, bu seçenek gereklidir. Oturum kimliği, Windows Görev Yöneticisi 'nin süreçler sekmesindeki oturum KIMLIĞI sütununda listelenir. **/CS** , **/CrossSession**için bir kısaltma olarak belirtilebilir. |
   |    [/WINCOUNTER](../profiling/wincounter.md) **:**`WinCounterPath`     |                                                                                                             Profil oluşturma sırasında toplanacak bir Windows performans sayacı belirtir.                                                                                                              |
   |         [/AutoMark](../profiling/automark.md) **:**`Interval`          |                                                                           Yalnızca **/WINCOUNTER** ile kullanın. Windows performans sayacı toplama olayları arasındaki milisaniye sayısını belirtir. Varsayılan değer 500 MS 'dir.                                                                            |
   |       [/Events](../profiling/events-vsperfcmd.md) **:**`Config`        |                                                                              Profil oluşturma sırasında toplanacak bir Windows için olay Izleme (ETW) olayı belirtir. ETW olayları ayrı bir (. etl) dosyasında toplanır.                                                                              |

4. Profil oluşturucuyu hizmete ekleyin. Şunu yazın:  

    **VSPerfCmd/Attach:** `PID` [`Sample Event`]  

    `PID` hedef uygulamanın işlem KIMLIĞINI belirtir. Windows Görev Yöneticisi 'nde çalışan tüm işlemlerin işlem kimliklerini görüntüleyebilirsiniz.  

    Varsayılan olarak, performans verileri 10.000.000 her durdurulmayan işlemci saati döngüsünde örneklenir. Bu, yaklaşık olarak 1GH işlemcide her 10 saniyede bir. Saat çevrimi aralığını değiştirmek veya farklı bir örnekleme olayı belirtmek için aşağıdaki seçeneklerden birini belirtebilirsiniz.  

   |Örnek olay|Açıklama|  
   |------------------|-----------------|  
   |[/Timer](../profiling/timer.md) **:**`Interval`|Örnekleme aralığını, tarafından belirtilen durdurulmayan saat döngüsü sayısına dönüştürür `Interval` .|  
   |[/PF](../profiling/pf.md)[**:** `Interval` ]|Örnekleme olayını sayfa hatalarına dönüştürür. `Interval`Belirtilmişse, örnekler arasındaki sayfa hatalarının sayısını ayarlar. Varsayılan değer 10 ' dur.|  
   |[/sys](../profiling/sys-vsperfcmd.md) [**:** `Interval` ]|Örnekleme olayını, işlemden işletim sistemi çekirdeğine (syscalls) sistem çağrıları olarak değiştirir. `Interval`Belirtilmişse, örnekler arasındaki çağrı sayısını ayarlar. Varsayılan değer 10 ' dur.|  
   |[/Counter](../profiling/counter.md) **:**`Config`|Örnekleme olayını ve aralığını, ' de belirtilen işlemci performans sayacı ve aralığı olarak değiştirir `Config` .|  

## <a name="controlling-data-collection"></a>Veri Toplama Denetimi  
 Hedef uygulama çalışırken, verileri profil oluşturucu veri dosyasına yazmayı başlatmak ve durdurmak için **VSPerfCmd.exe** seçeneklerini kullanabilirsiniz. Veri toplamayı denetlemek, program yürütmesinin, uygulamayı başlatma veya kapatma gibi belirli bir bölümü için veri toplamanızı sağlar.  

#### <a name="to-start-and-stop-data-collection"></a>Veri toplamayı başlatmak ve durdurmak için  

- Aşağıdaki **VSPerfCmd** seçenek çiftleri veri toplamayı başlatır ve durdurur. Her seçeneği ayrı bir komut satırında belirtin. Veri toplamayı birden çok kez açıp kapatabilirsiniz.  

    |Seçenek|Açıklama|  
    |------------|-----------------|  
    |[/GlobalOn/globaloff](../profiling/globalon-and-globaloff.md)|Tüm süreçler için veri toplamayı başlatır (**/GlobalOn**) veya Durdur (**/globaloff**).|  
    |[/ProcessOn](../profiling/processon-and-processoff.md) **:** `PID` [/ProcessOff](../profiling/processon-and-processoff.md) **:**`PID`|İşlem KIMLIĞI () tarafından belirtilen işlem için (**/ProcessOn**) veya duraklar (**/ProcessOff**) veri toplamayı başlatır `PID` .|  
    |**/Attach:** { `PID`&#124;`ProcName` } [/detach](../profiling/detach.md)[: { `PID`&#124;`ProcName` }]|**/Attach** işlem kimliği veya işlem adı tarafından belirtilen işlem için veri toplamaya başlar. **/Detach** belirtilen işlem için ya da bir işlem belirtilmemişse tüm işlemler için veri toplamayı durduruyor.|  

## <a name="ending-the-profiling-session"></a>Profil oluşturma oturumu sonlandırılıyor  
 Profil oluşturma oturumunu sonlandırmak için, profil oluşturucunun hizmetten ayrılması ve açıkça kapatılması gerekir. Hizmeti durdurarak veya **VSPerfCmd/detach** seçeneğini çağırarak örnekleme yöntemiyle profili oluşturulan yerel hizmeti ayırabilirsiniz. Ardından, profil oluşturucuyu kapatmak ve profil oluşturma veri dosyasını kapatmak için **VSPerfCmd** [/Shutdown](../profiling/shutdown.md) seçeneğini çağırın.  

#### <a name="to-end-a-profiling-session"></a>Profil oluşturma oturumunu sonlandırmak için  

1. Profil oluşturucuyu hedef uygulamadan ayırmak için aşağıdakilerden birini yapın:  

    - Hizmeti durdurun.  

         -veya-  

    - **VSPerfCmd/detach** yazın  

2. Profil oluşturucuyu kapatın. Şunu yazın:  

     **VSPerfCmd/shutdown**  

## <a name="see-also"></a>Ayrıca Bkz.  
 [Profil oluşturma hizmetleri](../profiling/command-line-profiling-of-services.md)   
 [Örnekleme Yöntemi Veri Görünümleri](../profiling/profiler-sampling-method-data-views.md)
