---
title: 'Nasıl yapılır: komut satırını kullanarak eşzamanlılık verileri toplamak için bir yerel hizmete profil oluşturucu Iliştirme | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 283a1ee1-b43e-4daf-95ae-1311925a42a8
caps.latest.revision: 27
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ab6e56d6b2d9a953b5549d59ea85049be8cc0306
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64787662"
---
# <a name="how-to-attach-the-profiler-to-a-native-service-to-collect-concurrency-data-by-using-the-command-line"></a>Nasıl yapılır: Komut Satırını Kullanarak Eşzamanlılık Verileri Toplamak için Yerel bir Hizmete Profil Oluşturucu Ekleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu konu, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] bir yerel (C/C++) hizmetine profil oluşturucu eklemek ve örnekleme yöntemini kullanarak işlem ve iş parçacığı eşzamanlılık verilerini toplamak için profil oluşturma araçları komut satırı araçlarının nasıl kullanılacağını açıklar.  

> [!NOTE]
> Windows 8 ve Windows Server 2012 ' deki gelişmiş güvenlik özellikleri, Visual Studio Profiler 'ın bu platformlarda verileri nasıl topladığı konusunda önemli değişiklikler gerektirdi. Windows Mağazası uygulamaları da yeni koleksiyon teknikleri gerektirir. Bkz. [Windows 8 ve Windows Server 2012 uygulamalarında performans araçları](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  

> [!NOTE]
> Profil Oluşturma Araçlarının komut satırı araçları, Visual Studio yükleme dizini altındaki \Team Tools\Performance Tools alt dizininde yer alır. 64 bit bilgisayarlarda, araçların her ikisi de 64-bit ve 32 bit sürümleri mevcuttur. Profil oluşturucuyu bir komut isteminde kullanmak için, araçlar yolunu **komut istemi** penceresinin PATH ortam değişkenine veya komutun içine eklemeniz gerekir. Daha fazla bilgi için bkz. [komut satırı araçlarının yolunu belirtme](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  

 Profil Oluşturucu hizmete iliştirirken, veri toplamayı duraklatabilir ve devam ettirebilirsiniz. Profil oluşturma oturumunu sonlandırmak için, profil oluşturucunun artık hizmete bağlı olmaması ve profil oluşturucunun açıkça kapatılması gerekir.  

## <a name="attaching-the-profiler"></a>Profil oluşturucuyu iliştirme  
 Profil oluşturucuyu yerel bir hizmete eklemek için **VSPerfCmd/start** ve **/Attach** seçeneklerini kullanarak profil oluşturucuyu başlatabilir ve hedef uygulamaya iliştirebilirsiniz. **/Start** ve **/Attach** ve ilgili seçeneklerini tek bir komut satırında belirtebilirsiniz. Ayrıca, hedef uygulamanın başlangıcında veri toplamayı duraklatmak için **/globaloff** seçeneğini de ekleyebilirsiniz. Ardından, veri toplamaya başlamak için **/GlobalOn** kullanın.  

#### <a name="to-attach-the-profiler-to-a-native-service"></a>Profil oluşturucuyu yerel bir hizmete eklemek için  

1. Hizmet çalışmıyorsa, hizmeti başlatın.  

2. Komut istemine aşağıdakileri yazarak profil oluşturucuyu başlatın:  

    [VSPerfCmd](../profiling/vsperfcmd.md) **/Start: eşzamanlılık/çıkış:** `OutputFile` [ `Options` ]  

   - /Start ile [/output](../profiling/output.md)**:** `OutputFile` seçeneği gereklidir. **/start** `OutputFile` profil oluşturma verileri (. vsp) dosyasının adını ve konumunu belirtir.  

     Aşağıdaki tabloda, **/Start** seçeneği ile herhangi bir seçeneği kullanabilirsiniz.  

   > [!NOTE]
   > Çoğu hizmet **/User** ve **/CrossSession** seçeneğini gerektirir.  

   |                               Seçenek                               |                                                                     Açıklama                                                                      |
   |--------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------|
   | [/User](../profiling/user-vsperfcmd.md) **:**[ `Domain\` ]`UserName` |                           Profil oluşturucuya erişim verilecek hesabın isteğe bağlı etki alanını ve Kullanıcı adını belirtir.                           |
   |           [/CrossSession](../profiling/crosssession.md)            |                                               Diğer oturum oturumlarda işlemlerin profilini oluşturmayı mümkün.                                                |
   |  [/WINCOUNTER](../profiling/wincounter.md) **:**`WinCounterPath`  |                                      Profil oluşturma sırasında toplanacak bir Windows performans sayacı belirtir.                                       |
   |       [/AutoMark](../profiling/automark.md) **:**`Interval`       | Yalnızca **/WINCOUNTER** ile kullanın. Windows performans sayacı toplama olayları arasındaki milisaniye sayısını belirtir. Varsayılan değer 500'dür. |
   |     [/Events](../profiling/events-vsperfcmd.md) **:**`Config`     |       Profil oluşturma sırasında toplanacak bir Windows için olay Izleme (ETW) olayı belirtir. ETW olayları ayrı bir (. etl) dosyasında toplanır.       |

3. Komut istemine aşağıdaki komutu yazarak profil oluşturucuyu hizmete ekleyin:  

    **VSPerfCmd/Attach:**`PID`  

    `PID` hedef uygulamanın işlem KIMLIĞINI veya işlem adını belirtir. Windows Görev Yöneticisi 'nde çalışan tüm işlemlerin işlem kimliklerini görüntüleyebilirsiniz.  

## <a name="controlling-data-collection"></a>Veri Toplama Denetimi  
 Hedef uygulama çalışırken, VSPerfCmd.exe seçenekleriyle dosyaya yazmayı başlatıp durdurarak veri toplamayı kontrol edebilirsiniz. Veri toplamayı denetleyerek, program yürütmesinin, uygulamanın başlatılması veya kapatılması gibi belirli bir bölümü için veri toplayabilirsiniz.  

#### <a name="to-start-and-stop-data-collection"></a>Veri toplamayı başlatmak ve durdurmak için  

- Aşağıdaki tabloda bulunan seçenek çiftleri veri toplamayı başlatır ve durdurur. Her seçeneği ayrı bir komut satırında belirtin. Veri toplamayı birden çok kez açıp kapatabilirsiniz.  

    |Seçenek|Açıklama|  
    |------------|-----------------|  
    |[/GlobalOn/globaloff](../profiling/globalon-and-globaloff.md)|Tüm süreçler için veri toplamayı başlatır (**/GlobalOn**) veya Durdur (**/globaloff**).|  
    |[/ProcessOn](../profiling/processon-and-processoff.md) **:** `PID` [/ProcessOff](../profiling/processon-and-processoff.md) **:**`PID`|İşlem KIMLIĞI () tarafından belirttiği işlem için (**/ProcessOn**) veya duraklar (**/ProcessOff**) veri toplamayı başlatır `PID` .|  
    |[/Attach](../profiling/attach.md) **:**{ `PID`&#124;`ProcName` } [/Detach](../profiling/detach.md)[**:**{ `PID`&#124;`ProcName` }]|**/Attach** işlem kimliği ( `PID` ) veya Işlem adı (*ProcName*) tarafından belirttiği işlem için veri toplamaya başlar. **/Detach** belirtilen işlem için veya hiçbir işlem belirtilmemişse tüm işlemler için veri toplamayı durduruyor.|  

## <a name="ending-the-profiling-session"></a>Profil oluşturma oturumu sonlandırılıyor  
 Profil oluşturma oturumunu sonlandırmak için, profil oluşturucunun veri toplamamalıdır. Hizmeti durdurarak veya **VSPerfCmd/detach** seçeneğini çağırarak eşzamanlılık yöntemiyle profili oluşturulan bir yerel hizmetten veri toplamayı durdurabilirsiniz. Ardından, profil oluşturucuyu kapatmak ve profil oluşturma veri dosyasını kapatmak için **VSPerfCmd/shutdown** seçeneğini çağırın.  

#### <a name="to-end-a-profiling-session"></a>Profil oluşturma oturumunu sonlandırmak için  

1. Hizmeti durdurarak veya bir komut isteminde aşağıdaki komutu yazarak profil oluşturucuyu hedef uygulamadan ayırın:  

     **VSPerfCmd/detach** yazın  

2. Komut istemine aşağıdaki komutu yazarak profil oluşturucuyu kapatın:  

     **VSPerfCmd**  [/Shutdown](../profiling/shutdown.md)
