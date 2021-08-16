---
title: Profil işleyiciyi .NET tek başına uygulamasına ekleme; uygulama istatistiklerini al
description: Çalışan bir Visual Studio Profil Oluşturma Araçları (istemci) uygulamasına profil oluşturma eklemek ve istatistikleri almak için .NET Framework komut satırı araçlarını kullanmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: b62fcbc1-791f-474e-890a-a6c332e0c9ea
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: 41ff72d2e23126cf5f7bc7530f556f7c28ce53c0a6ebd4185f58e9dd16478228
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121396571"
---
# <a name="how-to-attach-the-profiler-to-a-net-framework-stand-alone-application-and-collect-application-statistics-by-using-the-command-line"></a>Nasıl yapılır: Komut satırını kullanarak profil oluşturucuyu tek başına bir .NET Framework uygulamasına ekleme ve uygulama istatistikleri toplama
Bu makalede, Profil Oluşturma Araçları komut satırı araçlarını kullanarak çalışan bir .NET Framework (istemci) uygulamasına profil oluşturma ve örnekleme yöntemini kullanarak performans istatistikleri toplama [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] açıklanmıştır.

> [!NOTE]
> Windows 8 ve Windows Server 2012'daki gelişmiş güvenlik özellikleri, Visual Studio profil oluşturmanın bu platformlarda veri toplaması sırasında önemli değişiklikler gerektirmektedir. UWP uygulamaları için yeni koleksiyon teknikleri de gerekir. Uygulama [ve uygulama Windows 8 performans Windows Server 2012 bakın.](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)
>
> Profil oluşturma araçlarının yolunu almak için [bkz. Komut satırı araçlarının yolunu belirtme.](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md) 64 bit bilgisayarlarda, araçların hem 64 bit hem de 32 bit sürümleri kullanılabilir. Profil oluşturma komut satırı araçlarını kullanmak için, araç yolunu Komut İstemi penceresinin PATH ortam değişkenine eklemeniz veya komutun kendisine eklemeniz gerekir.
>
> Profil oluşturma çalıştırması için katman etkileşim verileri eklemek için komut satırı profil oluşturma araçlarıyla belirli yordamlar gerekir. Bkz. [Katman etkileşim verilerini toplama.](../profiling/adding-tier-interaction-data-from-the-command-line.md)

 Bir uygulamanın performans verilerini .NET Framework, hedef uygulama başlatılmadan önce uygun ortam değişkenlerinin başlatılması gerekir. Profiler uygulamaya ekli olduğunda veri toplamayı duraklatabilir ve sürdürebilirsiniz.

 Profil oluşturma oturumunu sona ertmak için, profil oluşturmanın artık uygulamaya bağlı olması ve profilleyicinin açıkça kapatılamaması gerekir. Çoğu durumda, profil oluşturma oturumunun sonunda profil oluşturma ortam değişkenlerini temizlemenizi öneririz.

## <a name="attach-the-profiler"></a>Profilleyiciyi ekleme

#### <a name="to-attach-the-profiler-to-a-running-net-framework-application"></a>Profilleyiciyi çalışan bir uygulamanın .NET Framework için

1. Bir komut istemi penceresi açın.

2. Profil oluşturma ortam değişkenlerini başlatma. Şunu yazın:

    **VSPerfClrEnv /sampleon** [**/samplelineoff**]

   - **/samplelineoff seçeneği,** kaynak kod satırı numarası verilerini toplamayı devre dışı bırakıyor.

3. Profilleyiciyi başlatma. Şunu yazın:

    **VSPerfCmd /start:sample /output:** `OutputFile` [`Options`]

   - [/start](../profiling/start.md)**:sample** seçeneği profilleyiciyi başlatıyor.

   - [/output](../profiling/output.md)**: seçeneği** / start ile `OutputFile` **gereklidir.** `OutputFile` profil oluşturma verileri (.vsp) dosyasının adını ve konumunu belirtir.

     **/start:sample** seçeneğiyle aşağıdaki seçeneklerden herhangi birini kullanabilirsiniz.

   | Seçenek | Açıklama |
   | - | - |
   | [/user](../profiling/user-vsperfcmd.md) **:**[ `Domain` **\\** ]`UserName` | Profili yapılan işleme sahip olan hesabın isteğe bağlı etki alanını ve kullanıcı adını belirtir. Bu seçenek yalnızca profili yapılan uygulama oturum açmış kullanıcıdan farklı bir kullanıcı olarak başlatıldı ise gereklidir. |
   | [/crosssession](../profiling/crosssession.md) | Diğer oturum açma oturumlarında işlemlerin profil oluşturmasını sağlar. **/CS,** **/crosssession için bir kısaltma olarak belirtilebilir.** Uygulama farklı bir oturumda çalışıyorsa bu seçenek gereklidir. |
   | [/wincounter:](../profiling/wincounter.md) `WinCounterPath` | Profil oluşturma Windows bir performans sayacı belirtir. |
   | [/automark:](../profiling/automark.md) `Interval` | Yalnızca **/wincounter ile** kullanın. Performans sayacı toplama olayları arasındaki milisaniye Windows sayısını belirtir. Varsayılan değer 500 ms'tir. |
   | [/events](../profiling/events-vsperfcmd.md) **:**`Config` | Profil oluşturma sırasında toplanacak Windows (ETW) olayı için bir Olay İzleme belirtir. ETW olayları ayrı bir () içinde toplanır.*etl*) dosyasını seçin. |

4. Gerekirse, hedef uygulamayı tipik bir şekilde başlatabilirsiniz.

5. Profilleyiciyi hedef uygulamaya ekleme. Şunu yazın:

    **VSPerfCmd /attach:**{ `PID`&#124;} [ ] [ `ProcessName` `Sample Event` **/targetclr:** `Version` ]

   - `PID` hedef uygulamanın işlem kimliğini belirtir. `ProcessName` , işlem adını belirtir. belirttiğinizde ve aynı `ProcessName` adı içeren birden çok işlem çalışıyorsa, sonuçların tahmin edilemez olduğunu unutmayın. Görev Yöneticisi'nde çalışan tüm işlemlerin işlem kimliklerini Windows görüntüebilirsiniz.

   - [/targetclr:](../profiling/targetclr.md)  bir uygulamada birden fazla çalışma zamanı sürümü yüklendiğinde profili oluşturmak için ortak dil çalışma `Version` zamanının (CLR) sürümünü belirtir. İsteğe bağlı.

   - Varsayılan olarak, her 10.000.000 durdurulan işlemci saat döngüsü için performans verileri örnek alır. Bu, 1GH işlemcide 10 saniyede bir yaklaşık bir kezdir. Saat döngüsü aralığını değiştirmek veya farklı bir örnekleme olayı belirtmek için aşağıdaki seçeneklerden birini belirtebilirsiniz. [/targetclr:](../profiling/targetclr.md) bir uygulamada çalışma zamanının birden fazla sürümü yüklendiğinde profili oluşturmak `Version` için CLR sürümünü belirtir. İsteğe bağlı.

   |Örnek olay|Açıklama|
   |-|-|
   |[/timer](../profiling/timer.md) **:**`Interval`|Örnekleme aralığını tarafından belirtilen durdurulmamış saat döngülerinin sayısına `Interval` değiştirir.|
   |[/pf](../profiling/pf.md) [**:** `Interval` ]|Örnekleme olayında sayfa hatalarını değiştirir. `Interval`belirtilirse, örnekler arasındaki sayfa hatalarının sayısını ayarlar. Varsayılan değer 10'dır.|
   |[/sys](../profiling/sys-vsperfcmd.md) [**:** `Interval` ]|Örnekleme olayı, işlemden işletim sistemi çekirdeğine (syscalls) yapılan sistem çağrılarını değiştirir. `Interval`belirtilirse, örnekler arasındaki çağrı sayısını ayarlar. Varsayılan değer 10'dır.|
   |[/counter](../profiling/counter.md) **:**`Config`|Örnekleme olayı ve aralığını, içinde belirtilen işlemci performans sayacı ve aralığı olarak `Config` değiştirir.|

## <a name="control-data-collection"></a>Veri toplamayı denetleme
 Hedef uygulama çalıştıryken, profil oluşturma seçeneklerini kullanarak veri yazmayı başlatarak ve durdurarak veri *toplamayıVSPerfCmd.exe* yapabilirsiniz. Veri toplamayı denetlemek, uygulamayı başlatma veya kapatma gibi program yürütmenin belirli bir bölümü için veri toplamaya olanak sağlar.

#### <a name="to-start-and-stop-data-collection"></a>Veri toplamayı başlatmak ve durdurmak için

- Aşağıdaki seçenek çiftleri veri toplamayı başlat ve durdur. Her seçeneği ayrı bir komut satırı üzerinde belirtin. Veri toplamayı birden çok kez açabilirsiniz ve kapatabilirsiniz.

    |Seçenek|Açıklama|
    |------------|-----------------|
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Tüm işlemler **için veri toplamayı** başlatır ( /globalon ) veya durdurur (**/globaloff).**|
    |[/processon:](../profiling/processon-and-processoff.md)  `PID` [/processoff](../profiling/processon-and-processoff.md) **:**`PID`|tarafından belirtilen **işlem için** veri koleksiyonunu başlatır ( /processon ) veya durdurur (**/processoff** `PID` ).|
    |[/attach:](../profiling/attach.md) { `PID`&#124;`ProcName` } [/detach](../profiling/detach.md)[**:**{ `PID`&#124;`ProcName` }]|**/attach,** veya işlem adı (ProcName) tarafından belirtilen işlem `PID` için veri toplamaya başlar. **/detach,** belirtilen işlem için veya belirli bir işlem belirtilmezse tüm işlemler için veri toplamayı durdurur.|

## <a name="end-the-profiling-session"></a>Profil oluşturma oturumunu sona er
 Profil oluşturma oturumunu sona erdirmak için profil oluşturma işleminin tüm profili yapılan işlemlerden ayrılmaları ve profil oluşturma işleminin açıkça kapatılmış olması gerekir. Uygulamayı kapatarak veya **VSPerfCmd /detach** seçeneğini çağırarak, örnekleme yöntemini kullanarak profil profili yapılan bir uygulamanın profillerini ayırabilirsiniz. Ardından, profil oluşturma veri dosyasını kapatmak ve profil oluşturma verilerini kapatmak için **VSPerfCmd /shutdown** seçeneğini çağırabilirsiniz. **VSPerfClrEnv /off** komutu profil oluşturma ortam değişkenlerini temizler.

#### <a name="to-end-a-profiling-session"></a>Profil oluşturma oturumunu sona erdir

1. Profilleyiciyi hedef uygulamadan ayırmak için aşağıdaki adımlardan birini gerçekleştirin:

    - **VSPerfCmd /detach yazın**

         -veya-

    - Hedef uygulamayı kapatın.

2. Profil oluşturucuyu kapatın. Şunu yazın:

     **VSPerfCmd**  [/Shutdown](../profiling/shutdown.md)

3. Seçim Profil oluşturma ortamı değişkenlerini temizleyin. Şunu yazın:

     **VSPerfClrEnv/off**

## <a name="see-also"></a>Ayrıca bkz.
- [Tek başına uygulamalar profili](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Örnekleme yöntemi veri görünümleri](../profiling/profiler-sampling-method-data-views.md)
