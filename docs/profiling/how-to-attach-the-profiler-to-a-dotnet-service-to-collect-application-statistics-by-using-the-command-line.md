---
title: Uygulama istatistikleri toplamak için .NET hizmetine profil oluşturma ekleme
description: Profil Visual Studio Profil Oluşturma Araçları hizmetine eklemek ve örnekleme yöntemini kullanarak performans istatistikleri .NET Framework komut satırı araçlarını kullanın.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: a0046c47-26c8-4bec-96a0-81da05e5104a
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- dotnet
ms.openlocfilehash: 92b5e24100e43a6a03352c49111226298160521b
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112385480"
---
# <a name="how-to-attach-the-profiler-to-a-net-service-to-collect-application-statistics-by-using-the-command-line"></a>Nasıl yapılanlar: Komut satırı kullanarak uygulama istatistikleri toplamak için bir .NET hizmetine profil oluşturma ekleme
Bu makalede, Profil Oluşturma Araçları hizmetine profil .NET Framework ve örnekleme yöntemini kullanarak performans istatistikleri toplamak için .NET Framework komut satırı [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] araçlarının nasıl kullanımı açıklanmıştır.

> [!NOTE]
> Windows 8 ve Windows Server 2012'de gelişmiş güvenlik özellikleri, Visual Studio profilleyicinin bu platformlarda veri toplama şeklinde önemli değişiklikler gerektirmektedir. UWP uygulamaları için yeni koleksiyon teknikleri de gerekir. Bkz. Windows 8 [ve Windows Server 2012 uygulamalarında Performans Araçları.](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)
>
> Profil oluşturma araçlarının yolunu almak için [bkz. Komut satırı araçlarının yolunu belirtme.](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md) 64 bit bilgisayarlarda, araçların hem 64 bit hem de 32 bit sürümleri kullanılabilir. Profil oluşturma komut satırı araçlarını kullanmak için, araç yolunu Komut İstemi penceresinin PATH ortam değişkenine eklemeniz veya komutun kendisine eklemeniz gerekir.
>
> Profil oluşturma çalıştırması için katman etkileşim verileri eklemek, komut satırı profil oluşturma araçlarıyla belirli yordamlar gerektirir. Bkz. [Katman etkileşim verilerini toplama.](../profiling/adding-tier-interaction-data-from-the-command-line.md)

 Bir hizmetten performans .NET Framework toplamak için [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) aracını kullanarak uygun ortam değişkenlerini başlatmanız gerekir. Ardından hizmeti barındıran bilgisayarı yeniden başlatmanız ve bu bilgisayarı profil oluşturma için yapılandırmanız gerekir. Ardından profilleyiciyi hizmet sürecine iliştirebilirsiniz. Profiler hizmete ekli olduğunda veri toplamayı duraklatabilir ve sürdürebilirsiniz.

 Profil oluşturma oturumunu sonlandırmak için, profil oluşturucunun hizmetten ayrılması ve ve açıkça kapatılması gerekir. Çoğu durumda, bir oturumun sonunda profil oluşturma ortam değişkenlerini temizlemenizi öneririz.

## <a name="attach-the-profiler"></a>Profilleyiciyi ekleme

#### <a name="to-attach-the-profiler-to-a-net-framework-service"></a>Profilleyiciyi bir .NET Framework eklemek için

1. Hizmeti yükleyin.

2. Bir komut istemi penceresi açın.

3. Profil oluşturma ortam değişkenlerini başlatma. Şunu yazın:

    **VSPerfClrEnv /globalsampleon** [**/samplelineoff**]

   - **/globalsampleon örneklemeyi** sağlar.

   - **/samplelineoff,** toplanan verilerin belirli kaynak kod satırlarına atamasını devre dışı bırakıyor. Bu seçenek belirtilirse, veriler yalnızca işlevlere atanır.

4. Bilgisayarı yeniden başlatın.

5. Bir komut istemi penceresi açın.

6. Profilleyiciyi başlatma. Şunu yazın:

    **VSPerfCmd**  [/start](../profiling/start.md) **:sample**  [/output](../profiling/output.md) **:** [ `OutputFile` `Options` ]

   - **/start:sample** seçeneği profilleyiciyi başlatıyor.

   - **/output:** `OutputFile` seçeneği / **start ile gereklidir.** `OutputFile` profil oluşturma verileri (.vsp) dosyasının adını ve konumunu belirtir.

     **/start:sample** seçeneğiyle aşağıdaki seçeneklerden herhangi birini kullanabilirsiniz.

   > [!NOTE]
   > **/user ve** **/crosssession** seçenekleri genellikle hizmetler için gereklidir.

   | Seçenek | Açıklama |
   | - | - |
   | [/user](../profiling/user-vsperfcmd.md) **:**[ `Domain` **\\** ]`UserName` | Profili yapılan işleme sahip olan hesabın etki alanını ve kullanıcı adını belirtir. Bu seçenek yalnızca işlem oturum açmış kullanıcıdan farklı bir kullanıcı olarak çalışıyorsa gereklidir. İşlem sahibi, Windows Görev Yöneticisi'nin İşlemler sekmesindeki Kullanıcı Adı sütununda listelenir. |
   | [/crosssession](../profiling/crosssession.md) | Diğer oturumlarda işlemlerin profilinin oluşturmayı sağlar. Hizmet farklı bir oturumda çalışıyorsa bu seçenek gereklidir. Oturum kimliği, Windows Görev Yöneticisi'nin İşlemler sekmesindeki Oturum Kimliği sütununda listelenir. **/CS,** **/crosssession için bir kısaltma olarak belirtilebilir.** |
   | [/wincounter:](../profiling/wincounter.md) `WinCounterPath` | Profil oluşturma sırasında toplanacak Windows performans sayacını belirtir. |
   | [/automark:](../profiling/automark.md) `Interval` | Yalnızca **/wincounter ile** kullanın. Windows performans sayacı toplama olayları arasındaki milisaniye sayısını belirtir. Varsayılan değer 500 ms'tir. |
   | [/events](../profiling/events-vsperfcmd.md) **:**`Config` | Profil oluşturma Windows için Olay İzleme bir olay (ETW) toplanacak bir olay belirtir. ETW olayları ayrı bir (.etl) dosyasında toplanır. |

7. Gerekirse hizmeti başlatabilirsiniz.

8. Profiler'i hizmete ekleme. Şunu yazın:

    **VSPerfCmd**[/attach:](../profiling/attach.md)  {&#124;} [ ] `PID` [ `ProcName` `Sample Event` [/targetclr](../profiling/targetclr.md)**:** `Version` ]  

   - Hizmetin işlem kimliğini ( `PID` ) veya işlem adını (ProcName) belirtin. Windows Görev Yöneticisi'nde işlem kimliklerini ve çalışan tüm işlemlerin adlarını görüntüebilirsiniz.

     Varsayılan olarak, her 10.000.000 durdurulan işlemci saat döngüsü için performans verileri örnek alır. Bu, 1GH işlemcide saniye başına yaklaşık 100 örnektir. Saat döngüsü aralığını değiştirmek veya farklı bir örnekleme olayı belirtmek için aşağıdaki seçeneklerden birini belirtebilirsiniz.

   |Örnek Olay|Açıklama|
   |------------------|-----------------|
   |[/timer](../profiling/timer.md) **:**`Interval`|Örnekleme aralığını tarafından belirtilen durdurulmamış saat döngülerinin sayısına `Interval` değiştirir.|
   |[/pf](../profiling/pf.md)[**:** `Interval` ]|Örnekleme olayında sayfa hatalarını değiştirir. `Interval`belirtilirse, örnekler arasındaki sayfa hatalarının sayısını ayarlar. Varsayılan değer 10'dır.|
   |[/sys](../profiling/sys-vsperfcmd.md)[ `:``Interval` ]|Örnekleme olayı, işlemden işletim sistemi çekirdeğine (syscalls) yapılan sistem çağrılarını değiştirir. `Interval`belirtilirse, örnekler arasındaki çağrı sayısını ayarlar. Varsayılan değer 10'dır.|
   |[/counter](../profiling/counter.md) **:**`Config`|Örnekleme olayı ve aralığını, içinde belirtilen işlemci performans sayacı ve aralığı olarak `Config` değiştirir.|

   - **targetclr:** `Version` , bir uygulamada birden fazla çalışma zamanı sürümü yüklendiğinde profili oluşturmak için ortak dil çalışma zamanının (CLR) sürümünü belirtir. İsteğe bağlı.

## <a name="control-data-collection"></a>Veri toplamayı denetleme
 Hizmet çalışmaya devam ediyorsa, profil *VSPerfCmd.exe* veri dosyasına veri yazmayı başlatmak ve durdurmak içinVSPerfCmd.exeseçeneklerini kullanabilirsiniz. Veri toplamayı denetlemek, uygulamayı başlatma veya kapatma gibi program yürütmenin belirli bir bölümü için veri toplamaya olanak sağlar.

#### <a name="to-start-and-stop-data-collection"></a>Veri toplamayı başlatmak ve durdurmak için

- Aşağıdaki **VSPerfCmd seçenekleri çiftleri** veri toplamayı başlatacak ve durduracak. Her seçeneği ayrı bir komut satırı üzerinde belirtin. Veri toplamayı birden çok kez açabilirsiniz ve kapatabilirsiniz.

    |Seçenek|Açıklama|
    |------------|-----------------|
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Tüm işlemler **için veri toplamayı** başlatır ( /globalon ) veya durdurur (**/globaloff).**|
    |[/processon:](../profiling/processon-and-processoff.md)  `PID` [/processoff](../profiling/processon-and-processoff.md) **:**`PID`|İşlem kimliği ( ) tarafından belirtilen işlem için veri toplamayı (**/processon**) veya durdurur ( `PID` ).|
    |**/attach:**{ `PID`&#124;`ProcName` } [/detach](../profiling/detach.md)[:{ `PID`&#124;`ProcName` }]|**/attach,** işlem kimliği veya işlem adı tarafından belirtilen işlem için veri toplamaya başlar. **/detach,** belirtilen işlem için veya belirli bir işlem belirtilmezse tüm işlemler için veri toplamayı durdurur.|

## <a name="end-the-profiling-session"></a>Profil oluşturma oturumunu sona er
 Profil oluşturma oturumunu sona erdirmak için profil oluşturma işleminin tüm profili yapılan işlemlerden ayrılmaları ve profil oluşturma işleminin açıkça kapatılmış olması gerekir. Uygulamayı kapatarak veya **VSPerfCmd /detach** seçeneğini çağırarak örnekleme yöntemiyle profili profili yapılan bir uygulamadan ayırabilirsiniz. Ardından, profil oluşturma veri dosyasını kapatmak ve profil oluşturma verilerini kapatmak için **VSPerfCmd /shutdown** seçeneğini çağırabilirsiniz.

 **VSPerfClrEnv /globaloff** komutu profil oluşturma ortam değişkenlerini temizler, ancak bilgisayar yeniden başlatana kadar sistem yapılandırması sıfırlanmaz.

#### <a name="to-end-a-profiling-session"></a>Profil oluşturma oturumunu sona erdirecek

1. Profilleyiciyi hedef uygulamadan ayırmak için aşağıdakilerden birini yapın:

    - Hizmeti durdurun.

         -veya-

    - **VSPerfCmd /detach yazın**

2. Profilleyiciyi kapatın. Şunu yazın:

     **VSPerfCmd /shutdown**

3. (İsteğe bağlı) Profil oluşturma ortam değişkenlerini temizleme. Şunu yazın:

     **VSPerfClrEnv /globaloff**

4. Bilgisayarı yeniden başlatın.

## <a name="see-also"></a>Ayrıca bkz.
- [Profil hizmetleri](../profiling/command-line-profiling-of-services.md)
- [Örnekleme yöntemi veri görünümleri](../profiling/profiler-sampling-method-data-views.md)
