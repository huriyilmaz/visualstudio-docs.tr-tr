---
title: .NET tek başına uygulamasına profil oluşturucu ekleyin; Uygulama istatistiklerini al
description: Profil oluşturucuyu çalışan bir .NET Framework tek başına (istemci) uygulamasına eklemek ve istatistikleri almak için Visual Studio Profil Oluşturma Araçları komut satırı araçlarını kullanmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: b62fcbc1-791f-474e-890a-a6c332e0c9ea
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: 899a74894e34b43f87a7f45b4c4c90fff60088a1
ms.sourcegitcommit: 589d96700208bf22c8da9e26a1d2041fbf39b8f9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/26/2021
ms.locfileid: "98801141"
---
# <a name="how-to-attach-the-profiler-to-a-net-framework-stand-alone-application-and-collect-application-statistics-by-using-the-command-line"></a>Nasıl yapılır: Komut satırını kullanarak profil oluşturucuyu tek başına bir .NET Framework uygulamasına ekleme ve uygulama istatistikleri toplama
Bu makalede [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , profil oluşturucuyu çalışan bir .NET Framework tek başına (istemci) uygulamasına eklemek ve örnekleme yöntemini kullanarak performans istatistikleri toplamak için profil oluşturma araçları komut satırı araçlarının nasıl kullanılacağı açıklanır.

> [!NOTE]
> Windows 8 ve Windows Server 2012 ' deki gelişmiş güvenlik özellikleri, Visual Studio Profiler 'ın bu platformlarda verileri nasıl topladığı konusunda önemli değişiklikler gerektirdi. UWP uygulamaları için de yeni koleksiyon teknikleri gerekir. Bkz. [Windows 8 ve Windows Server 2012 uygulamalarında performans araçları](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).
>
> Profil oluşturma araçlarının yolunu almak için, bkz. [komut satırı araçlarının yolunu belirtme](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md). 64 bit bilgisayarlarda, araçların her ikisi de 64-bit ve 32 bit sürümleri mevcuttur. Profil oluşturucu komut satırı araçlarını kullanmak için araçlar yolunu komut Istemi penceresinin PATH ortam değişkenine eklemeniz ya da komutun kendisine eklemeniz gerekir.
>
> Bir profil oluşturma çalıştırmasına katman etkileşim verileri eklemek, komut satırı profil oluşturma araçlarıyla belirli yordamlar gerektirir. Bkz. [Katman etkileşimi verilerini toplama](../profiling/adding-tier-interaction-data-from-the-command-line.md).

 .NET Framework uygulamasından performans verilerini toplamak için, hedef uygulama başlamadan önce uygun ortam değişkenlerinin başlatılması gerekir. Profil Oluşturucu uygulamaya eklendiğinde, veri toplamayı duraklatabilir ve devam ettirebilirsiniz.

 Profil oluşturma oturumunu sonlandırmak için, profil oluşturucunun artık uygulamaya bağlı olmaması ve profil oluşturucunun açıkça kapatılması gerekir. Çoğu durumda, profil oluşturma oturumunun sonundaki profil oluşturma ortamı değişkenlerini temizlemeniz önerilir.

## <a name="attach-the-profiler"></a>Profil oluşturucuyu iliştirme

#### <a name="to-attach-the-profiler-to-a-running-net-framework-application"></a>Profil oluşturucuyu çalışan bir .NET Framework uygulamasına eklemek için

1. Bir komut istemi penceresi açın.

2. Profil oluşturma ortamı değişkenlerini başlatın. Şunu yazın:

    **VSPerfClrEnv/sampleon** [**/samplelineoff**]

   - **/Samplelineoff** seçeneği, kaynak kodu satır numarası verileri koleksiyonunu devre dışı bırakır.

3. Profil oluşturucuyu başlatın. Şunu yazın:

    **VSPerfCmd/start: örnek/çıktı:** `OutputFile` [`Options`]

   - [/Start](../profiling/start.md)**: örnek** seçeneği, profil oluşturucuyu başlatır.

   - /Start ile [/output](../profiling/output.md)**:** `OutputFile` seçeneği gereklidir.  `OutputFile` profil oluşturma verileri (. vsp) dosyasının adını ve konumunu belirtir.

     Aşağıdaki seçeneklerden herhangi birini, **/Start: Sample** seçeneğiyle kullanabilirsiniz.

   | Seçenek | Açıklama |
   | - | - |
   | [/User](../profiling/user-vsperfcmd.md) **:**[ `Domain` **\\** ]`UserName` | Profili oluşturulan işlemin sahibi olan hesabın isteğe bağlı etki alanını ve Kullanıcı adını belirtir. Bu seçenek yalnızca profili oluşturulmuş uygulamanın oturum açmış kullanıcı dışında bir kullanıcı olarak başlatılması durumunda gereklidir. |
   | [/CrossSession](../profiling/crosssession.md) | Diğer oturum oturumlarda işlemlerin profilini oluşturmayı mümkün. **/CS** , **/CrossSession** için bir kısaltma olarak belirtilebilir. Uygulama farklı bir oturumda çalışıyorsa, bu seçenek gereklidir. |
   | [/WINCOUNTER](../profiling/wincounter.md) **:**`WinCounterPath` | Profil oluşturma sırasında toplanacak bir Windows performans sayacı belirtir. |
   | [/AutoMark](../profiling/automark.md) **:**`Interval` | Yalnızca **/WINCOUNTER** ile kullanın. Windows performans sayacı toplama olayları arasındaki milisaniye sayısını belirtir. Varsayılan değer 500 MS 'dir. |
   | [/Events](../profiling/events-vsperfcmd.md) **:**`Config` | Profil oluşturma sırasında toplanacak bir Windows için olay Izleme (ETW) olayı belirtir. ETW olayları ayrı bir (.*ETL*) dosyası. |

4. Gerekirse, hedef uygulamayı normal şekilde başlatın.

5. Profil oluşturucuyu hedef uygulamaya ekleyin. Şunu yazın:

    **VSPerfCmd/Attach:**{ `PID`&#124;`ProcessName` } [ `Sample Event` ] [**/targetclr:** `Version` ]

   - `PID` hedef uygulamanın işlem KIMLIĞINI belirtir. `ProcessName` işlemin adını belirtir. ' İ belirtirseniz `ProcessName` ve aynı ada sahip birden çok işlem çalışıyorsa, sonuçların tahmin edilemez olduğunu unutmayın. Windows Görev Yöneticisi 'nde çalışan tüm işlemlerin işlem kimliklerini görüntüleyebilirsiniz.

   - [/targetclr](../profiling/targetclr.md) **:** `Version` bir uygulamaya çalışma zamanının birden fazla sürümü yüklendiğinde profil için ortak dil çalışma zamanının (CLR) sürümünü belirtir. İsteğe bağlı.

   - Varsayılan olarak, performans verileri 10.000.000 her durdurulmayan işlemci saati döngüsünde örneklenir. Bu, yaklaşık bir adet 1 GH işlemcide her 10 saniyede bir kez olur. Saat çevrimi aralığını değiştirmek veya farklı bir örnekleme olayı belirtmek için aşağıdaki seçeneklerden birini belirtebilirsiniz. [/targetclr](../profiling/targetclr.md)**:** `Version` bir uygulamaya çalışma zamanının birden fazla sürümü yüklendiğinde, profil için CLR sürümünü belirtir. İsteğe bağlı.

   |Örnek olay|Description|
   |-|-|
   |[/Timer](../profiling/timer.md) **:**`Interval`|Örnekleme aralığını, tarafından belirtilen durdurulmayan saat döngüsü sayısına dönüştürür `Interval` .|
   |[/PF](../profiling/pf.md) [**:** `Interval` ]|Örnekleme olayını sayfa hatalarına dönüştürür. `Interval`Belirtilmişse, örnekler arasındaki sayfa hatalarının sayısını ayarlar. Varsayılan değer 10 ' dur.|
   |[/sys](../profiling/sys-vsperfcmd.md) [**:** `Interval` ]|Örnekleme olayını, işlemden işletim sistemi çekirdeğine (syscalls) sistem çağrıları olarak değiştirir. `Interval`Belirtilmişse, örnekler arasındaki çağrı sayısını ayarlar. Varsayılan değer 10 ' dur.|
   |[/Counter](../profiling/counter.md) **:**`Config`|Örnekleme olayını ve aralığını, ' de belirtilen işlemci performans sayacı ve aralığı olarak değiştirir `Config` .|

## <a name="control-data-collection"></a>Veri toplamayı denetleme
 Hedef uygulama çalışırken, *VSPerfCmd.exe* seçeneklerini kullanarak profil oluşturucu veri dosyasına veri yazmayı başlatıp durdurarak veri toplamayı kontrol edebilirsiniz. Veri toplamayı denetlemek, program yürütmesinin, uygulamayı başlatma veya kapatma gibi belirli bir bölümü için veri toplamanızı sağlar.

#### <a name="to-start-and-stop-data-collection"></a>Veri toplamayı başlatmak ve durdurmak için

- Aşağıdaki seçenek çiftleri veri toplamayı başlatır ve durdurur. Her seçeneği ayrı bir komut satırında belirtin. Veri toplamayı birden çok kez açıp kapatabilirsiniz.

    |Seçenek|Açıklama|
    |------------|-----------------|
    |[/GlobalOn/globaloff](../profiling/globalon-and-globaloff.md)|Tüm süreçler için veri toplamayı başlatır (**/GlobalOn**) veya Durdur (**/globaloff**).|
    |[/ProcessOn](../profiling/processon-and-processoff.md) **:** `PID` [/ProcessOff](../profiling/processon-and-processoff.md) **:**`PID`|Tarafından belirtilen işlem için veri toplamayı başlatır (**/ProcessOn**) veya duraklar (**/ProcessOff**) `PID` .|
    |[/Attach](../profiling/attach.md) **:**{ `PID`&#124;`ProcName` } [/Detach](../profiling/detach.md)[**:**{ `PID`&#124;`ProcName` }]|**/Attach** , `PID` veya Işlem adı (ProcName) tarafından belirtilen işlem için veri toplamaya başlar. **/Detach** belirtilen işlem veya belirli bir işlem belirtilmemişse tüm işlemler için veri toplamayı durduruyor.|

## <a name="end-the-profiling-session"></a>Profil oluşturma oturumunu Sonlandır
 Profil oluşturma oturumunu sonlandırmak için, profil oluşturucunun profili oluşturulmuş tüm işlemlerden ayrılması ve profil oluşturucunun açıkça kapatılması gerekir. Profil oluşturucuyu, uygulamayı kapatarak veya **VSPerfCmd/detach** seçeneğini çağırarak örnekleme yöntemini kullanarak profili oluşturulmuş bir uygulamadan ayırabilirsiniz. Ardından, profil oluşturucuyu kapatmak ve profil oluşturma veri dosyasını kapatmak için **VSPerfCmd/shutdown** seçeneğini çağırın. **VSPerfCLREnv/off** komutu profil oluşturma ortam değişkenlerini temizler.

#### <a name="to-end-a-profiling-session"></a>Profil oluşturma oturumunu sonlandırmak için

1. Profil oluşturucuyu hedef uygulamadan ayırmak için aşağıdaki adımlardan birini gerçekleştirin:

    - **VSPerfCmd/detach** yazın

         -veya-

    - Hedef uygulamayı kapatın.

2. Profil oluşturucuyu kapatın. Şunu yazın:

     **VSPerfCmd**  [/Shutdown](../profiling/shutdown.md)

3. Seçim Profil oluşturma ortamı değişkenlerini temizleyin. Şunu yazın:

     **VSPerfClrEnv/off**

## <a name="see-also"></a>Ayrıca bkz.
- [Tek başına uygulamalar profili](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Örnekleme yöntemi veri görünümleri](../profiling/profiler-sampling-method-data-views.md)
