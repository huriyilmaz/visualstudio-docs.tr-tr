---
title: Bellek verileri toplamak için ASP.NET 'e profil oluşturucu iliştirme
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: d608f85a-41ae-4ca7-85e6-b96624dbc83c
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- aspnet
ms.openlocfilehash: 22a3f7d20b02839ae677b12e5ce8454e63358914
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/19/2020
ms.locfileid: "90807982"
---
# <a name="how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-memory-data-by-using-the-command-line"></a>Nasıl yapılır: komut satırını kullanarak bellek verileri toplamak için profil oluşturucuyu bir ASP.NET Web uygulamasına Iliştirme
Bu makalede [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , bir [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web uygulamasına Profiler eklemek ve .NET Framework bellek ayırmalarının sayısı ve boyutu hakkında veri toplamak için profil oluşturma araçları komut satırı araçlarının nasıl kullanılacağı açıklanır. Ayrıca, .NET Framework bellek nesnelerinin yaşam süresi hakkında veri toplayabilirsiniz.

> [!NOTE]
> Profil oluşturma araçlarının yolunu almak için, bkz. [komut satırı araçlarının yolunu belirtme](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). 64 bit bilgisayarlarda, araçların her ikisi de 64-bit ve 32 bit sürümleri mevcuttur. Profil oluşturucu komut satırı araçlarını kullanmak için araçlar yolunu komut Istemi penceresinin PATH ortam değişkenine eklemeniz ya da komutun kendisine eklemeniz gerekir.

 Bir Web uygulamasından performans verilerini toplamak için [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] , Web uygulamasını barındıran bilgisayarda uygun ortam değişkenlerini başlatmak üzere [VSPerfCLREnv. cmd](../profiling/vsperfclrenv.md) aracını kullanmanız gerekir [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] . Daha sonra, Web sunucusunu profil oluşturma için yapılandırmak üzere bilgisayarı yeniden başlatmanız gerekir.

 Daha sonra, [VSPerfCmd.exe](../profiling/vsperfcmd.md) [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web sitenizi barındıran çalışan işleme profil oluşturucuyu eklemek içinVSPerfCmd.exearacını kullanın. Profil Oluşturucu uygulamaya eklendiğinde, veri toplamayı duraklatabilir ve devam ettirebilirsiniz.

 Profil oluşturma oturumunu sonlandırmak için, profil oluşturucunun artık uygulamaya bağlı olmaması ve profil oluşturucunun açıkça kapatılması gerekir. Çoğu durumda, bir oturumun sonunda profil oluşturma ortam değişkenlerini temizlemeniz önerilir.

## <a name="attach-the-profiler"></a>Profil oluşturucuyu iliştirme

#### <a name="to-attach-the-profiler-to-an-aspnet-web-application"></a>Profil oluşturucuyu bir ASP.NET Web uygulamasına eklemek için

1. Bir komut istemi penceresi açın.

2. Profil oluşturma ortamı değişkenlerini başlatın. Şunu yazın:

    **VSPerfCLREnv** {**/globalsamplegc** &#124; **/globalsamplegclienfe**} [**/samplelineoff**]

   - **/Globalsamplegc** ve **/globalsamplegclife** seçenekleri toplanacak bellek verilerinin türünü belirtir.

        Aşağıdaki seçeneklerden bir ve yalnızca bir tanesini belirtin.

       |Seçenek|Açıklama|
       |------------|-----------------|
       |**/globalörneklec**|Bellek ayırma verilerinin toplanmasını etkinleştirir.|
       |**/globalsamplegclife**|Bellek ayırma verilerinin ve nesne yaşam süresi verilerinin toplanmasını etkinleştirir.|

   - **/Samplelineoff** seçeneği, toplanan verilerin belirli kaynak kodu satırlarına atanmasını devre dışı bırakır. Bu seçenek belirtilmişse, veriler işlev düzeyinde atanır.

3. Yeni ortam yapılandırmasını ayarlamak için bilgisayarı yeniden başlatın.

4. Bir komut istemi penceresi açın. Gerekirse, profil oluşturucu yolu çalıştırılmaları değişkenini ayarlayın.

5. Profil oluşturucuyu başlatın. Şunu yazın:

    **VSPerfCmd**  [/Start](../profiling/start.md) **: örnek**  [/output](../profiling/output.md) **:** `OutputFile` [ `Options` ]

   - **/Start: örnek** seçeneği, profil oluşturucuyu başlatır.

   - /Start ile **/output:** `OutputFile` seçeneği gereklidir. **/start** `OutputFile` profil oluşturma verileri (. vsp) dosyasının adını ve konumunu belirtir.

     Aşağıdaki seçeneklerden herhangi birini, **/Start: Sample** seçeneğiyle kullanabilirsiniz.

   > [!NOTE]
   > **/User** ve **/CrossSession** seçenekleri genellikle ASP.NET uygulamaları için gereklidir.

   | Seçenek | Açıklama |
   | - | - |
   | [/User](../profiling/user-vsperfcmd.md) **:**[ `Domain` **\\** ]`UserName` | ASP.NET çalışan işleminin sahibi olan hesabın etki alanını ve Kullanıcı adını belirtir. Bu seçenek, işlem oturum açan kullanıcıdan farklı bir kullanıcı olarak çalışıyorsa gereklidir. İşlem sahibi, Windows Görev Yöneticisi 'nin Işlemler sekmesinde Kullanıcı adı sütununda listelenir. |
   | [/CrossSession](../profiling/crosssession.md) | Diğer oturum oturumlarda işlemlerin profilini oluşturmayı mümkün. ASP.NET uygulaması farklı bir oturumda çalışıyorsa, bu seçenek gereklidir. Oturum tanımlayıcısı, Windows Görev Yöneticisi 'nin süreçler sekmesindeki oturum KIMLIĞI sütununda listelenir. **/CS** , **/CrossSession**için bir kısaltma olarak belirtilebilir. |
   | [/WaitStart](../profiling/waitstart.md) [**:** `Interval` ] | Profil oluşturucunun hata vermeden önce başlatılması için bekleyeceği saniye sayısını belirtir. `Interval`Belirtilmezse, profil oluşturucu süresiz olarak bekler. Varsayılan olarak, **/Start** hemen döndürür. |
   | [/WINCOUNTER](../profiling/wincounter.md) **:**`WinCounterPath` | Profil oluşturma sırasında toplanacak bir Windows performans sayacı belirtir. |
   | [/AutoMark](../profiling/automark.md) **:**`Interval` | Yalnızca **/WINCOUNTER** ile kullanın. Windows performans sayacı toplama olayları arasındaki milisaniye sayısını belirtir. Varsayılan değer 500 MS 'dir. |
   | [/Events](../profiling/events-vsperfcmd.md) **:**`Config` | Profil oluşturma sırasında toplanacak bir Windows için olay Izleme (ETW) olayı belirtir. ETW olayları ayrı bir (. etl) dosyasında toplanır. |

6. [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]Web uygulamasını normal şekilde başlatın.

7. Profil oluşturucuyu [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] çalışan işleme ekleyin. Şunu yazın:

    **VSPerfCmd**[/Attach](../profiling/attach.md) **:**{ `PID`&#124;`ProcName` } [[/targetclr](../profiling/targetclr.md)**:** `Version` ]  

   - İşlem KIMLIĞI, `(PID)` çalışan işlemin Işlem kimliğini veya işlem adını belirtir [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] . Windows Görev Yöneticisi 'nde çalışan tüm işlemlerin işlem kimliklerini görüntüleyebilirsiniz.

   - **/targetclr:** `Version` bir uygulamaya çalışma zamanının birden fazla sürümü yüklendiğinde profil için ortak dil çalışma zamanının (CLR) sürümünü belirtir.

## <a name="control-data-collection"></a>Veri toplamayı denetleme
 Uygulama çalışırken, **VSPerfCmd.exe** seçeneklerini kullanarak profil oluşturucu veri dosyasına veri yazmayı başlatıp durdurarak veri toplamayı kontrol edebilirsiniz. Veri toplamayı denetlemek, program yürütmesinin, uygulamayı başlatma veya kapatma gibi belirli bir bölümü için veri toplamanızı sağlar.

#### <a name="to-start-and-stop-data-collection"></a>Veri toplamayı başlatmak ve durdurmak için

- Aşağıdaki **VSPerfCmd** seçenek çiftleri veri toplamayı başlatır ve durdurur. Her seçeneği ayrı bir komut satırında belirtin. Veri toplamayı birden çok kez açıp kapatabilirsiniz.

    |Seçenek|Açıklama|
    |------------|-----------------|
    |[/GlobalOn/globaloff](../profiling/globalon-and-globaloff.md)|Tüm süreçler için veri toplamayı başlatır (**/GlobalOn**) veya Durdur (**/globaloff**).|
    |[/ProcessOn](../profiling/processon-and-processoff.md) **:** `PID` [/ProcessOff](../profiling/processon-and-processoff.md) **:**`PID`|Tarafından belirtilen işlem için veri toplamayı başlatır (**/ProcessOn**) veya Durdur (**/ProcessOff**) `PID` .|
    |**/Attach:**{ `PID`&#124;`ProcName` } [/Detach](../profiling/detach.md)[**:**{ `PID`&#124;: `ProcName` }]|**/Attach** işlem kimliği veya işlem adı tarafından belirtilen işlem için veri toplamaya başlar. **/Detach** belirtilen işlem veya belirli bir işlem belirtilmemişse tüm işlemler için veri toplamayı durduruyor.|

## <a name="end-the-profiling-session"></a>Profil oluşturma oturumunu Sonlandır
 Profil oluşturma oturumunu sonlandırmak için, profil oluşturucunun Web uygulamasından ayrılmalıdır. [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]Çalışan işlemini yeniden başlatarak veya **VSPerfCmd/detach** seçeneğini çağırarak örnekleme yöntemiyle profili oluşturulmuş bir uygulamadan veri toplamayı durdurabilirsiniz. Ardından, profil oluşturucuyu kapatmak ve profil oluşturma veri dosyasını kapatmak için **VSPerfCmd** [/Shutdown](../profiling/shutdown.md) seçeneğini çağırın. **VSPerfCLREnv/globaloff** komutu profil oluşturma ortam değişkenlerini temizler, ancak bilgisayar yeniden başlatılana kadar sistem yapılandırması sıfırlanmaz.

#### <a name="to-end-a-profiling-session"></a>Profil oluşturma oturumunu sonlandırmak için

1. Profil oluşturucuyu hedef uygulamadan ayırmak için aşağıdaki adımlardan birini gerçekleştirin:

   - **VSPerfCmd** [/Detach](../profiling/detach.md) yazın

      -veya-

   - [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]Çalışan işlemini kapatın. Şunu yazın:

     **IISReset/stop**

2. Profil oluşturucuyu kapatın. Şunu yazın:

    **VSPerfCmd/shutdown**

3. Seçim Profil oluşturma ortamı değişkenlerini temizleyin. Şunu yazın:

    **VSPerfCmd/globaloff**

4. Bilgisayarı yeniden başlatın. Gerekirse Internet Information Services (IIS) yeniden başlatın. Şunu yazın:

    **IISReset/Start**

## <a name="see-also"></a>Ayrıca bkz.
- [ASP.NET Web uygulamaları profili](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [.NET bellek verileri görünümleri](../profiling/dotnet-memory-data-views.md)
