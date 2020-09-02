---
title: 'Nasıl yapılır: komut satırını kullanarak bellek verileri toplamak için bir .NET hizmetine profil oluşturucu Iliştirme | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: aeac39af-ad99-479f-aa36-4104356ca512
caps.latest.revision: 33
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9a1601b855cfc895aa01c6b72cbbe36b59980bd5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64812822"
---
# <a name="how-to-attach-the-profiler-to-a-net-service-to-collect-memory-data-by-using-the-command-line"></a>Nasıl yapılır: Komut Satırını Kullanarak Bellek Verileri Toplamak için bir .NET Hizmetine Profil Oluşturucu Ekleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu konuda [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , bir hizmete profil oluşturucu eklemek [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] ve bellek verileri toplamak için profil oluşturma araçları komut satırı araçlarının nasıl kullanılacağı açıklanmaktadır. Bellek ayırmalarının sayısı ve boyutu hakkında veri toplayabilir ve ayrıca, bellek nesnelerinin yaşam süresi hakkında veri toplayabilirsiniz.  

> [!NOTE]
> Windows 8 ve Windows Server 2012 ' deki gelişmiş güvenlik özellikleri, Visual Studio Profiler 'ın bu platformlarda verileri nasıl topladığı konusunda önemli değişiklikler gerektirdi. Windows Mağazası uygulamaları da yeni koleksiyon teknikleri gerektirir. Bkz. [Windows 8 ve Windows Server 2012 uygulamalarında performans araçları](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  

> [!NOTE]
> Profil Oluşturma Araçları komut satırı araçları, yükleme dizininin \Team Tools\Performance Tools alt dizininde bulunur [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] . 64 bit bilgisayarlarda, araçların her ikisi de 64 bit ve 32 bit sürümleri mevcuttur. Profil oluşturucu komut satırı araçlarını kullanmak için araçlar yolunu komut istemi penceresinin PATH ortam değişkenine eklemeniz ya da komutun kendisine eklemeniz gerekir. Daha fazla bilgi için bkz. [komut satırı araçlarının yolunu belirtme](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  

 Bir hizmetten bellek verileri toplamak için [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] [VSPerfCLREnv. cmd](../profiling/vsperfclrenv.md) aracını kullanarak hizmeti barındıran bilgisayardaki uygun ortam değişkenlerini başlatın. Bilgisayarın, profil oluşturma için yapılandırılmak üzere yeniden başlatılması gerekir.  

 Ardından, profil oluşturucuyu hizmet işlemine iliştirmek için [VSPerfCmd](../profiling/vsperfcmd.md) aracını kullanın. Profil Oluşturucu hizmete iliştirirken, veri toplamayı duraklatabilir ve devam ettirebilirsiniz.  

 Profil oluşturma oturumunu sonlandırmak için, profil oluşturucunun hizmetten ayrılması ve ve açıkça kapatılması gerekir. Çoğu durumda, bir oturumun sonunda profil oluşturma ortam değişkenlerini temizlemeniz önerilir.  

## <a name="attaching-the-profiler"></a>Profil oluşturucuyu iliştirme  

#### <a name="to-attach-the-profiler-to-a-net-framework-service"></a>Profil oluşturucuyu bir .NET Framework hizmetine eklemek için  

1. Gerekirse, hizmeti yükler.  

2. Bir komut istemi penceresi açın.  

3. Profil oluşturma ortamı değişkenlerini başlatın. Şunu yazın:  

    **VSPerfCLREnv** {**/globalsamplegc/globalsamplegclienfe**} [**/samplelineoff**]  

   - **/Globalsamplegclife** ve **/globalsamplegclife** seçenekleri toplanacak bellek verilerinin türünü belirtir. Aşağıdaki seçeneklerden bir ve yalnızca bir tanesini belirtin.  

     **/globalörneklec**  
     Bellek ayırma verilerinin toplanmasını etkinleştirir.  

     **/globalsamplegclife**  
     Bellek ayırma verilerinin ve nesne yaşam süresi verilerinin toplanmasını etkinleştirir.  

   - **/Samplelineoff** seçeneği, kaynak kodu satır numarası verileri koleksiyonunu devre dışı bırakır.  

4. Yeni ortam yapılandırmasını ayarlamak için bilgisayarı yeniden başlatın.  

5. Gerekirse, hizmeti başlatın.  

6. Bir komut istemi penceresi açın. Gerekirse, profil oluşturucu yolunu PATH ortam değişkenine ekleyin.  

7. Profil oluşturucuyu başlatın. Şunu yazın:  

    **VSPerfCmd**  [/Start](../profiling/start.md) **: örnek**  [/output](../profiling/output.md) **:** `OutputFile` [ `Options` ]  

   - **/Start: örnek** seçeneği, profil oluşturucuyu başlatır.  

   - /Start ile **/output:** `OutputFile` seçeneği gereklidir. **/start** `OutputFile` profil oluşturma verileri (. vsp) dosyasının adını ve konumunu belirtir.  

     Aşağıdaki seçeneklerden birini veya daha fazlasını **/Start: Sample** seçeneğiyle kullanabilirsiniz.  

   > [!NOTE]
   > **/User** ve **/CrossSession** seçenekleri genellikle hizmetler için gereklidir.  

   |                                 Seçenek                                  |                                                                                                                                                   Açıklama                                                                                                                                                    |
   |-------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
   | [/User](../profiling/user-vsperfcmd.md) **:**[ `Domain` **\\** ]`UserName` |                      İşlemin sahibi olan hesabının etki alanını ve kullanıcı adını belirtir. İşlem, oturum açmış kullanıcı dışında bir kullanıcı olarak çalışıyorsa, bu seçenek gereklidir. İşlem sahibi, Windows Görev Yöneticisi 'nin Işlemler sekmesinde Kullanıcı adı sütununda listelenir.                       |
   |              [/CrossSession](../profiling/crosssession.md)              | Diğer oturum oturumlarda işlemlerin profilini oluşturmayı mümkün. ASP.NET uygulaması farklı bir oturumda çalışıyorsa, bu seçenek gereklidir. Oturum kimliği, Windows Görev Yöneticisi 'nin süreçler sekmesindeki oturum KIMLIĞI sütununda listelenir. **/CS** , **/CrossSession**için bir kısaltma olarak belirtilebilir. |
   | [/User](../profiling/user-vsperfcmd.md) **:**[ `Domain` **\\** ]`UserName` |                                                    Hizmetin altında çalıştığı oturum açma hesabının kullanıcı adını ve isteğe bağlı etki alanını belirtir. Oturum açma hesabın, Windows Hizmet Denetimi Yöneticisi'nde hizmetin Farklı Oturum Aç sütununda listelenir.                                                     |
   |          [/CrossSession&#124;CS](../profiling/crosssession.md)          |                                                                                                                             Diğer oturum oturumlarda işlemlerin profilini oluşturmayı mümkün.                                                                                                                              |
   |    [/WINCOUNTER](../profiling/wincounter.md) **:**`WinCounterPath`     |                                                                                                                    Profil oluşturma sırasında toplanacak bir Windows performans sayacı belirtir.                                                                                                                     |
   |         [/AutoMark](../profiling/automark.md) **:**`Interval`          |                                                                                  Yalnızca **/WINCOUNTER** ile kullanın. Windows performans sayacı toplama olayları arasındaki milisaniye sayısını belirtir. Varsayılan değer 500 MS 'dir.                                                                                   |
   |       [/Events](../profiling/events-vsperfcmd.md) **:**`Config`        |                                                                                     Profil oluşturma sırasında toplanacak bir Windows için olay Izleme (ETW) olayı belirtir. ETW olayları ayrı bir (. etl) dosyasında toplanır.                                                                                     |

8. Profil oluşturucuyu hizmete ekleyin. Şunu yazın:  

    **VSPerfCmd**[/Attach](../profiling/attach.md) **:**{ `PID`&#124;`ProcName` } [[/targetclr](../profiling/targetclr.md)**:** `Version` ]    

   - İşlem kimliğini veya hizmetin işlem adını belirtin. Windows Görev Yöneticisi 'nde çalışan tüm işlemlerin işlem kimliklerini ve adlarını görüntüleyebilirsiniz.  

   - **targetclr:** `Version` bir uygulamaya çalışma zamanının birden fazla sürümü yüklendiğinde profil için ortak dil çalışma zamanının (CLR) sürümünü belirtir. İsteğe bağlı.  

## <a name="controlling-data-collection"></a>Veri Toplama Denetimi  
 Hizmet çalışırken, verileri Profiler veri dosyasına yazmayı durdurmak ve başlatmak için **VSPerfCmd.exe** seçeneklerini kullanabilirsiniz. Veri toplamanın denetlenmesi, program yürütmenin, uygulamanın başlatılması veya kapatılması gibi özel bir bölümü için veri toplamanızı sağlar.  

#### <a name="to-start-and-stop-data-collection"></a>Veri toplamayı başlatmak ve durdurmak için  

- Aşağıdaki **VSPerfCmd** seçenek çiftleri veri toplamayı başlatır ve durdurur. Her seçeneği ayrı bir komut satırında belirtin. Veri toplamayı birden çok kez açıp kapatabilirsiniz.  

    |Seçenek|Açıklama|  
    |------------|-----------------|  
    |[/GlobalOn/globaloff](../profiling/globalon-and-globaloff.md)|Tüm süreçler için veri toplamayı başlatır (**/GlobalOn**) veya Durdur (**/globaloff**).|  
    |[/ProcessOn](../profiling/processon-and-processoff.md) **:** `PID` [/ProcessOff](../profiling/processon-and-processoff.md) **:**`PID`|İşlem KIMLIĞI () tarafından belirtilen işlem için (**/ProcessOn**) veya duraklar (**/ProcessOff**) veri toplamayı başlatır `PID` .|  
    |**/Attach:**{ `PID`&#124;`ProcName` } [/detach](../profiling/detach.md)[: { `PID`&#124;`ProcName` }]|**/Attach** işlem kimliği veya işlem adı tarafından belirtilen işlem için veri toplamaya başlar. **/Detach** belirtilen işlem için veya belirli bir işlem belirtilmemişse tüm işlemler için veri toplamayı durduruyor.|  

## <a name="ending-the-profiling-session"></a>Profil oluşturma oturumu sonlandırılıyor  
 Profil oluşturma oturumunu sonlandırmak için, profil oluşturucunun veri toplamamalıdır. Hizmeti durdurarak veya **VSPerfCmd/detach** seçeneğini çağırarak, örnekleme yöntemiyle profili oluşturulmuş bir uygulamadan veri toplamayı durdurabilirsiniz. Ardından, profil oluşturucuyu kapatmak ve profil oluşturma veri dosyasını kapatmak için **VSPerfCmd** [/Shutdown](../profiling/shutdown.md) seçeneğini çağırın. **VSPerfCLREnv/globaloff** komutu profil oluşturma ortam değişkenlerini temizler, ancak bilgisayar yeniden başlatılana kadar sistem yapılandırması sıfırlanmaz.  

#### <a name="to-end-a-profiling-session"></a>Profil oluşturma oturumunu sonlandırmak için  

1. Profil oluşturucuyu hedef uygulamadan ayırmak için aşağıdakilerden birini yapın:  

    - Hizmeti durdurun.  

         -veya-  

    - **VSPerfCmd/detach** yazın  

2. Profil oluşturucuyu kapatın. Şunu yazın:  

     **VSPerfCmd/shutdown**  

3. Seçim Profil oluşturma ortamı değişkenlerini temizleyin. Şunu yazın:  

     **VSPerfClrEnv/globaloff**  

4. Bilgisayarı yeniden başlatın.  

## <a name="see-also"></a>Ayrıca Bkz.  
 [Profil oluşturma hizmetleri](../profiling/command-line-profiling-of-services.md)   
 [.NET bellek verileri görünümleri](../profiling/dotnet-memory-data-views.md)
