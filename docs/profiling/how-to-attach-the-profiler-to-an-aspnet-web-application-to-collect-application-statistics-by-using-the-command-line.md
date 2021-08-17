---
title: uygulama istatistiklerini almak için ASP.NET profil oluşturucu iliştirme
description: profil oluşturucuyu bir ASP.NET Web uygulamasına eklemek ve örnekleme yöntemini kullanarak performans istatistiklerini almak için Visual Studio Profil Oluşturma Araçları komut satırı araçlarını kullanın.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 3725ddbe-ce91-4469-991e-8c5ed048c618
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- aspnet
ms.openlocfilehash: 76272c69b636da2bb104a28049f2dd31c88f9527
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122033700"
---
# <a name="how-to-attach-the-profiler-to-an-aspnet-web-application-to-collect-application-statistics-by-using-the-command-line"></a>nasıl yapılır: komut satırını kullanarak uygulama istatistikleri toplamak için profil oluşturucuyu bir ASP.NET web uygulamasına iliştirme
bu makalede [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , bir ASP.NET Web uygulamasına profiler eklemek ve örnekleme yöntemini kullanarak performans istatistikleri toplamak için Profil Oluşturma Araçları komut satırı araçlarının nasıl kullanılacağı açıklanır.

> [!NOTE]
> Windows 8 ve Windows Server 2012 gelişmiş güvenlik özellikleri Visual Studio profiler 'ın bu platformlarda verileri topladıkları şekilde gerekli önemli değişikliklere sahiptir. UWP uygulamaları için de yeni koleksiyon teknikleri gerekir. bkz. [Windows 8 ve Windows Server 2012 uygulamalarda performans araçları](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).
>
> Bir profil oluşturma çalıştırmasına katman etkileşim verileri eklemek, komut satırı profil oluşturma araçlarıyla belirli yordamlar gerektirir. Bkz. [Katman etkileşimi verilerini toplama](../profiling/adding-tier-interaction-data-from-the-command-line.md).
>
> Profil oluşturma araçlarının yolunu almak için, bkz. [komut satırı araçlarının yolunu belirtme](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). 64 bit bilgisayarlarda, araçların her ikisi de 64-bit ve 32 bit sürümleri mevcuttur. Profil oluşturucu komut satırı araçlarını kullanmak için araçlar yolunu komut Istemi penceresinin PATH ortam değişkenine eklemeniz ya da komutun kendisine eklemeniz gerekir.

 ASP.NET web uygulamasından performans verilerini toplamak için, uygun ortam değişkenleri başlatılmalıdır ve web sunucusunu profil oluşturma için yapılandırmak üzere ASP.NET web uygulamasını barındıran bilgisayarın yeniden başlatılması gerekir.

 ardından, profil oluşturucuyu Web sitenizi barındıran ASP.NET çalışan işleme ekleyebilirsiniz. Profil Oluşturucu uygulamaya eklendiğinde, veri toplamayı duraklatabilir ve devam ettirebilirsiniz.

 Profil oluşturma oturumunu sonlandırmak için, profil oluşturucunun profili oluşturulmuş uygulamadan ayrılması ve profil oluşturucunun açıkça kapatılması gerekir. Çoğu durumda, bir oturumun sonunda profil oluşturma ortam değişkenlerini temizlemeniz önerilir.

## <a name="start-the-profiler-and-attach-to-an-aspnet-web-application"></a>profil oluşturucuyu başlatma ve bir ASP.NET web uygulamasına iliştirme

#### <a name="to-attach-the-profiler-to-an-aspnet-web-application"></a>profil oluşturucuyu bir ASP.NET Web uygulamasına eklemek için

1. Bir komut istemi penceresi açın.

2. Profil oluşturma ortamı değişkenlerini başlatın. Şunu yazın:

    **VSPerfCLREnv/globalsampleon** [**/samplelineoff**]

   - **/globalsampleon** , örneklemesi sunar.

   - **/samplelineoff** toplanan verilerin belirli kaynak kodu satırlarına atanmasını devre dışı bırakır. Bu seçenek belirtildiğinde, veriler yalnızca işlevlere atanır.

3. Bilgisayarı yeniden başlatın.

4. Profil oluşturucuyu başlatın. Tür:**VSPerfCmd** [/Start](../profiling/start.md)**: örnek** [/output](../profiling/output.md)**:** `OutputFile` [ `Options` ]

   - **/Start: örnek** seçeneği, profil oluşturucuyu başlatır.

   - /Start ile **/output:** `OutputFile` seçeneği gereklidir.  `OutputFile` profil oluşturma verileri (. vsp) dosyasının adını ve konumunu belirtir.

     Aşağıdaki seçeneklerden herhangi birini, **/Start: Sample** seçeneğiyle kullanabilirsiniz.

   > [!NOTE]
   > **/user** ve **/crosssession** seçenekleri genellikle ASP.NET uygulamalar için gereklidir.

   | Seçenek | Açıklama |
   | - | - |
   | [/User](../profiling/user-vsperfcmd.md) **:**[ `Domain` **\\** ]`UserName` | ASP.NET çalışan işleminin sahibi olan hesabın etki alanını ve kullanıcı adını belirtir. Bu seçenek, işlem oturum açan kullanıcıdan farklı bir kullanıcı olarak çalışıyorsa gereklidir. işlem sahibi, Windows görev yöneticisi 'nin **işlemler** sekmesinde **kullanıcı adı** sütununda listelenir. |
   | [/CrossSession](../profiling/crosssession.md) | Diğer oturum oturumlarda işlemlerin profilini oluşturmayı mümkün. ASP.NET uygulaması farklı bir oturumda çalışıyorsa, bu seçenek gereklidir. oturum tanımlayıcısı, Windows görev yöneticisi 'nin süreçler sekmesindeki oturum kimliği sütununda listelenir. **/CS** , **/CrossSession** için bir kısaltma olarak belirtilebilir. |
   | [/WINCOUNTER](../profiling/wincounter.md) **:**`WinCounterPath` | profil oluşturma sırasında toplanacak bir Windows performans sayacı belirtir. |
   | [/AutoMark](../profiling/automark.md) **:**`Interval` | Yalnızca **/WINCOUNTER** ile kullanın. Windows performans sayacı toplama olayları arasındaki milisaniye sayısını belirtir. Varsayılan değer 500 MS 'dir. |
   | [/Events](../profiling/events-vsperfcmd.md) **:**`Config` | profil oluşturma sırasında toplanacak Windows (ETW) olayı için bir olay izleme olayı belirtir. ETW olayları ayrı bir (. etl) dosyasında toplanır. |

5. ASP.NET Web uygulamasını normal şekilde başlatın.

6. profil oluşturucuyu ASP.NET çalışan işlemine iliştirin. Tür:**VSPerfCmd** [/Attach](../profiling/attach.md)**:**{ `PID`&#124;`ProcName` } [ `Sample Event` ] [[/targetclr](../profiling/targetclr.md)**:** `Version` ]

   - `PID`ASP.NET çalışan işleminin işlem kimliğini belirtir; `ProcName`çalışan işlemin adını belirtir. Windows görev yöneticisi 'nde çalışan tüm işlemlerin işlem kimliklerini ve adlarını görüntüleyebilirsiniz.

   - Varsayılan olarak, performans verileri 10.000.000 her durdurulmayan işlemci saati döngüsünde örneklenir. Bu, 1 GH işlemcide saniyede yaklaşık 100 kez olur. Saat çevrimi aralığını değiştirmek veya farklı bir örnekleme olayı belirtmek için aşağıdaki **VSPerfCmd** seçeneklerinden birini belirtebilirsiniz.

   |Örnek olay|Açıklama|
   |------------------|-----------------|
   |[/Timer](../profiling/timer.md) **:**`Interval`|Örnekleme aralığını, tarafından belirtilen durdurulmayan saat döngüsü sayısına dönüştürür `Interval` .|
   |[/PF](../profiling/pf.md)[**:** `Interval` ]|Örnekleme olayını sayfa hatalarına dönüştürür. `Interval`Belirtilmişse, örnekler arasındaki sayfa hatalarının sayısını ayarlar. Varsayılan değer 10 ' dur.|
   |[/sys](../profiling/sys-vsperfcmd.md)[ `:``Interval` ]|Örnekleme olayını, işlemden işletim sistemi çekirdeğine (syscalls) sistem çağrıları olarak değiştirir. `Interval`Belirtilmişse, örnekler arasındaki çağrı sayısını ayarlar. Varsayılan değer 10 ' dur.|
   |[/Counter](../profiling/counter.md) **:**`Config`|Örnekleme olayını ve aralığını, ' de belirtilen işlemci performans sayacı ve aralığı olarak değiştirir `Config` .|
   |[/targetclr](../profiling/targetclr.md) **:**`Version`|Bir uygulamaya çalışma zamanının birden fazla sürümü yüklendiğinde profil için ortak dil çalışma zamanının (CLR) sürümünü belirtir.|

   - **targetclr:** `Version` bir uygulamaya çalışma zamanının birden fazla sürümü yüklendiği zaman profil için CLR sürümünü belirtir. İsteğe bağlı.

## <a name="control-data-collection"></a>Veri toplamayı denetleme
 Uygulama çalışırken, *VSPerfCmd.exe* seçeneklerini kullanarak verileri dosyaya yazmayı başlatıp durdurarak veri toplamayı kontrol edebilirsiniz. Veri toplamayı denetlemek, program yürütmesinin, uygulamayı başlatma veya kapatma gibi belirli bir bölümü için veri toplamanızı sağlar.

#### <a name="to-start-and-stop-data-collection"></a>Veri toplamayı başlatmak ve durdurmak için

- Aşağıdaki **VSPerfCmd** seçenek çiftleri veri toplamayı başlatır ve durdurur. Her seçeneği ayrı bir komut satırında belirtin. Veri toplamayı birden çok kez açıp kapatabilirsiniz.

    |Seçenek|Açıklama|
    |------------|-----------------|
    |[/GlobalOn/globaloff](../profiling/globalon-and-globaloff.md)|Tüm süreçler için veri toplamayı başlatır (**/GlobalOn**) veya Durdur (**/globaloff**).|
    |[/ProcessOn](../profiling/processon-and-processoff.md) **:** `PID` **/ProcessOff:**`PID`|Tarafından belirtilen işlem için veri toplamayı başlatır (**/ProcessOn**) veya duraklar (**/ProcessOff**) `PID` .|
    |[/Attach](../profiling/attach.md) **:**{ `PID`&#124;`ProcName` } [/Detach](../profiling/detach.md)[**:**{ `PID`&#124;`ProcName` }]|**/Attach** , `PID` veya Işlem adı (ProcName) tarafından belirtilen işlem için veri toplamaya başlar. **/Detach** belirtilen işlem veya belirli bir işlem belirtilmemişse tüm işlemler için veri toplamayı durduruyor.|

## <a name="end-the-profiling-session"></a>Profil oluşturma oturumunu Sonlandır
 bir profil oluşturma oturumunu sonlandırmak için [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] Web uygulamasını kapatın ve ardından Internet Information Services (ııs) **ıısreset** komutunu kullanarak [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] çalışan işlemini kapatın. Profiler 'ı devre dışı bırakmak ve profil oluşturma veri dosyasını kapatmak için **VSPerfCmd** [/Shutdown](../profiling/shutdown.md) seçeneğini çağırın.

 **VSPerfCLREnv/globaloff** komutu profil oluşturma ortam değişkenlerini temizler. Yeni ortam ayarlarının uygulanması için bilgisayarı yeniden başlatmanız gerekir.

 **VSPerfCLREnv/globaloff** komutu profil oluşturma ortam değişkenlerini temizler, ancak bilgisayar yeniden başlatılana kadar sistem yapılandırması sıfırlanmaz.

#### <a name="to-end-a-profiling-session"></a>Profil oluşturma oturumunu sonlandırmak için

1. Profil oluşturucuyu hedef uygulamadan ayırmak için aşağıdakilerden birini yapın:

   - **VSPerfCmd/detach** yazın

      -veya-

   - [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]Çalışan işlemini kapatın.

2. Profil oluşturucuyu kapatın. Tür:**VSPerfCmd** [/Shutdown](../profiling/shutdown.md)

3. Seçim Profil oluşturma ortamı değişkenlerini temizleyin. Şunu yazın:

    **VSPerfCmd/globaloff**

4. Bilgisayarı yeniden başlatın.

## <a name="see-also"></a>Ayrıca bkz.
- [web uygulamalarının profilini ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Örnekleme yöntemi veri görünümleri](../profiling/profiler-sampling-method-data-views.md)
